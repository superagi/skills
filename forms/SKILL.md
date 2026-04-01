---
name: forms
description: Create, version, publish, and submit Forms in SuperAGI — covers form lifecycle, versioning, schema attributes, runtime modes, submission lifecycle, search, and integration with Workflows and Process Design
platform: [linux, macos]
---

# SuperAGI Forms

Forms is a standalone service in SuperAGI that manages form definitions, versioning, runtime rendering, and submissions. Forms are used for data collection within CRM processes, workflow automation, and standalone data capture scenarios. They integrate with both the Workflows (Automations) and Process Design (Process Flows) systems.

**URL:** `/forms` (standalone) | Embedded in workflow/process flow editors via Form nodes

**Authentication:** All API endpoints require the `X-Workspace-Id` header.
**Base API URL:** `/api`

---

## Form Lifecycle

```
DRAFT → PUBLISHED → ARCHIVED
```

| Status | Description |
|--------|-------------|
| **DRAFT** | Form is being designed, not available for use |
| **PUBLISHED** | Form is active and available for submissions |
| **ARCHIVED** | Form is retired and inactive |

---

## Versioning

Forms support full versioning — only one version can be published at a time.

### Version Operations

| Operation | Endpoint |
|-----------|----------|
| Create version | `POST /api/forms/{id}/versions` (body: `schema_json`, `rules_json`) |
| Edit version | `PUT /api/forms/{id}/versions/{version_id}` |
| Publish version | `POST /api/forms/{id}/versions/{version_id}/publish` |
| Get published version | `GET /api/forms/{id}/versions/published` |

### Version Structure

```json
{
  "id": 1,
  "form_id": 123,
  "version": 1,
  "is_published": false,
  "runtime_hash": "abc123",
  "schema_json": { "fields": [...] },
  "rules_json": { "rules": [...] },
  "created_at": "2024-01-15T10:30:00Z",
  "published_at": null
}
```

- **`schema_json`** — defines form fields and layout
- **`rules_json`** — defines validation and conditional logic rules
- **`runtime_hash`** — enables cache invalidation for form bundles
- Only one version can be `is_published: true` at a time

---

## Form Schema & Attributes

Each field in `schema_json` has:

| Property | Type | Description |
|----------|------|-------------|
| `id` | string | Unique field identifier |
| `slug` | string | URL-friendly field name |
| `name` | string | Display label |
| `type` | string | Field type (text, email, phone, select, etc.) |
| `required` | boolean | Whether field is mandatory |
| `options` | array | Dropdown/select options |
| `config` | object | Additional field configuration |
| `order` | integer | Display order |
| `is_system` | boolean | Whether it's a system-managed field |

### Schema Retrieval

```
GET /api/forms/key/{form_key}/schema
```
Returns form attributes — used by the Views service.

---

## Forms CRUD

| Operation | Endpoint |
|-----------|----------|
| Create form | `POST /api/forms` |
| List forms | `GET /api/forms` |
| Get by ID | `GET /api/forms/{id}` |
| Get by key | `GET /api/forms/key/{form_key}` |
| Update form | `PUT /api/forms/{id}` |
| Delete form | `DELETE /api/forms/{id}` |

---

## Runtime

The runtime system handles live form rendering.

### Open Form for Runtime

```
POST /api/forms/runtime/open
```

**Request:**
```json
{
  "form_key": "my-form",
  "entity_type": "lead",
  "entity_id": "123",
  "context": {
    "mode": "CREATE",
    "prefill_from_entity": true
  }
}
```

**Response includes:**
- Form metadata (id, key, name, version, runtime_hash)
- Bundle (schema + rules for rendering)
- Prefill data (from linked entity if `prefill_from_entity: true`)

### Runtime Modes

| Mode | Behavior |
|------|----------|
| **CREATE** | Empty form for new data entry |
| **EDIT** | Pre-filled form allowing modifications |
| **VIEW** | Read-only display of submitted data |

### Runtime Metadata (Lightweight)

```
GET /api/forms/runtime-meta?formKey=...
```
Lightweight metadata used by the Process Flow Service.

---

## Submissions

### Submission Lifecycle

```
DRAFT → SUBMITTED → APPROVED / REJECTED
```

| Status | Description |
|--------|-------------|
| **DRAFT** | Partially filled, auto-saved |
| **SUBMITTED** | Completed and submitted |
| **APPROVED** | Reviewed and approved |
| **REJECTED** | Reviewed and rejected |

### Submit a Form

```
POST /api/forms/submissions
```
```json
{
  "formKey": "my-form",
  "entityType": "lead",
  "entityId": "123",
  "action": "submit",
  "values": {
    "email": "user@example.com",
    "name": "John Doe"
  }
}
```

### Save Draft (Auto-Save)

```
PUT /api/forms/submissions/draft
```
Saves partial form data without submitting. Enables auto-save functionality — users don't lose partially filled data.

### Check Submission Status

```
GET /api/forms/submissions/status?formKey=...&entityType=...&entityId=...
```
Returns whether a submission already exists for the given form + entity combination.

### List Submissions

```
GET /api/forms/submissions
```

### Get Submission by ID

```
GET /api/forms/submissions/{id}
```

Each submission includes a `history` array tracking all actions (submitted, approved, rejected) with actor details and timestamps.

---

## Search

### Full Search

```
GET /api/forms/search?q=...&filters=...&sorts=...&page=1&page_size=20
```
- Powered by OpenSearch
- Supports JSON-encoded filter and sort criteria

### Name Search

```
GET /api/forms/search/name?q=...&page=1&page_size=10
```
Searches by form name or `form_key`.

### Reindex

```
POST /api/forms/reindex
```
Rebuilds the OpenSearch index for all workspace forms. Use when search results are stale or missing.

---

## Integration with Workflows

Forms integrate into Workflows through the **Form Node** (category: Interaction):

| Config Field | Description |
|---|---|
| `form_id` | Selected form reference |
| `form_name` | Display name on the canvas |
| `wait_for_submit` | When ON, pauses workflow execution until the form is submitted |

**Trigger events available in Workflows:**
- `form_submitted` — fires when any form is submitted
- `routing_form_submitted` — fires for routing form submissions

---

## Integration with Process Design

Forms are central to Process Flows:
1. **Form nodes** are a primary node type in process flows
2. Process flows use `GET /api/forms/runtime-meta` for lightweight metadata
3. The `wait_for_submit` flag creates step-by-step data collection pipelines

---

## Error Response Format

### Validation Error (400)
```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Validation failed"
  },
  "validationErrors": [
    {
      "field": "email",
      "code": "REQUIRED",
      "message": "Email is required"
    }
  ]
}
```

### Not Found (404)
```json
{
  "success": false,
  "error": "resource not found"
}
```

### Internal Error (500)
```json
{
  "success": false,
  "error": "internal server error"
}
```

---

## API Surface Summary

| Category | Count | Key Endpoints |
|----------|-------|---------------|
| Forms CRUD | 6 | Create, List, Get by ID, Get by Key, Update, Delete |
| Forms Search | 3 | Search with filters, Search by name, Reindex |
| Form Versions | 6 | Create, List, Get, Get published, Update, Publish |
| Runtime | 3 | Open form, Runtime metadata, Schema/attributes |
| Submissions | 5 | Submit, List, Get by ID, Save draft, Check status |
| Health | 2 | Basic health, Health with OpenTelemetry |

---

## Key Design Decisions & Gotchas

1. **Workspace isolation** — all forms are scoped to a workspace via `X-Workspace-Id` header. Every API call must include this header.

2. **Only one published version at a time** — publishing a new version automatically unpublishes the previous one. Use `GET /api/forms/{id}/versions/published` to always get the current live version.

3. **Draft auto-save** — use `PUT /api/forms/submissions/draft` to persist partial form data. Users can return to a partially filled form without losing data.

4. **Check submission status before opening** — use `GET /api/forms/submissions/status` to determine if the form has already been submitted for a given entity. Use this to decide whether to open in CREATE vs EDIT vs VIEW mode.

5. **runtime_hash for caching** — when the form bundle is cached client-side, compare `runtime_hash` to detect when the form has changed and the cache should be invalidated.

6. **`rules_json` controls conditional logic** — field visibility rules, validation conditions, and branching logic are all in `rules_json`, not `schema_json`. To change when a field appears or is required, update `rules_json`.

7. **Entity binding** — forms are linked to CRM entity types (`lead`, `contact`, `company`, `deal`). Pass the correct `entity_type` and `entity_id` when opening a form in EDIT or VIEW mode.

8. **Reindex after bulk changes** — if forms are created or modified in bulk (e.g., via migration), run `POST /api/forms/reindex` to ensure search results are up to date.
