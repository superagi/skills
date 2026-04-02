---
name: workflows
description: Create and manage visual trigger-based automation workflows in SuperAGI Sales — covers editor layout, lifecycle, all 30+ node types, triggers, canvas controls, list page, publishing, and key behaviors
platform: [linux, macos]
---

# SuperAGI Workflows (Automations)

Workflows (also called Automations) is SuperAGI's visual automation builder. Users design trigger-based, multi-step workflows using a drag-and-drop canvas. Workflows automate sales, marketing, and CRM operations by connecting triggers to a chain of actions, conditions, and delays.

**URL:** `/workflows` (list page) | `/workflows/:id` (editor)

## Related Skills

| Skill | Relationship |
|-------|-------------|
| `process-design` | Process Design is a simplified version of Workflows focused on CRM data collection. Use `process-design` for internal form-based processes; use `workflows` for full sales/marketing automation. |
| `forms` | The Form node in Workflows uses the Forms service. Use `forms` to create, version, and publish forms before embedding them in a workflow. |
| `crm/records.md` | Workflow nodes (Create Entity, Update Entity) create and update CRM records (leads, contacts, companies, deals). Use `crm/records.md` to understand the fields and structure. |
| `crm/lists.md` | The "Add to List" and "Remove from List" workflow nodes manage CRM list membership. Use `crm/lists.md` to understand list structure. |
| `crm/tasks.md` | The "Create Task" workflow node creates CRM Tasks. Use `crm/tasks.md` to view and action those tasks. |
| `sequences` | The "Add to Sequence" / "Remove from Sequence" workflow nodes enroll contacts in sequences. Use `sequences` to build those sequences. |
| `cold-outreach` | Cold Outreach trigger events (`form_submitted`, `email_replied`) can be used as workflow triggers. Use `cold-outreach` to manage the campaigns. |
| `prospect` | The "Prospect Leads" and "Prospect Companies" workflow nodes use the same filters as the Prospect module. Use `prospect` to understand filter options. |

---

## Editor Layout (3-Panel)

| Panel | Content |
|-------|---------|
| **Left — Steps Tab** | Collapsible node categories with draggable node types |
| **Center — Canvas** | ReactFlow canvas for visual workflow design |
| **Right — Configuration** | Node-specific configuration form (or "No Node Selected" message) |

### Left Panel Tabs
- **Steps** (always visible) — Node palette organized by category
- **Analytics** (non-DRAFT only) — Execution metrics, success/failure counts, timeline, node-level data

### Navbar
- Left: Automation name with pencil icon for inline editing
- Right: Status action buttons (Launch / Pause / Resume / Exit)

---

## Automation Lifecycle

```
DRAFT → ACTIVE → PAUSED → ACTIVE (cycle)
```

| Status | Available Actions |
|--------|-------------------|
| **DRAFT** | Launch Automation, Exit |
| **ACTIVE** | Pause, Exit |
| **PAUSED** | Resume, Exit |

### Status Transition Rules
- Launch requires a configured trigger node + at least one connected action node
- Launch button is **disabled** when no trigger node exists on canvas
- Pausing stops new executions; in-flight executions may complete
- Resuming re-enables trigger event acceptance

---

## Trigger Types

Only **one** trigger node is allowed per workflow. After adding one, trigger options in the Steps panel become disabled.

| Trigger Type | Configuration Fields |
|-------------|---------------------|
| **Event-Based** (`When an event occurs`) | Event type dropdown (created, updated, added to list, etc.), Entity type selector (leads/contacts/companies) |
| **Schedule-Based** (`Based on a schedule`) | Frequency selector (Daily/Weekly/Monthly), Time picker, Day-of-week/date picker |
| **Webhook** | Auto-generated webhook URL (read-only), Auth type, HTTP method, Test endpoint button, Field mapping |
| **Manual** (`When triggered manually`) | Object type selector for on-demand execution |

### Supported Trigger Events

- **Object lifecycle:** `created`, `updated`
- **Email channel:** `email_clicked`, `email_sent`, `email_bounced`, `email_opened`, `email_replied`
- **WhatsApp:** `whatsapp_sent`, `whatsapp_replied`, `whatsapp_opened`
- **Forms:** `form_submitted`, `routing_form_submitted`
- **Lists:** `added_to_list`, `removed_from_list`
- **Process Flow:** `process_flow:create_lead_clicked`, `process_flow:create_deal_clicked`

---

## Node Types (30+)

### Engage

| Node | Description |
|------|-------------|
| **Email** | Send email with template, subject, body, from address, personalization |
| **WhatsApp** | Send WhatsApp message via template |
| **Add to Sequence** | Add contact to an outreach sequence |
| **Remove from Sequence** | Remove contact from a sequence |
| **Marketing Email** | Marketing campaign email with audience targeting |
| **Voice Agent** | Voice agent call (dev/staging only) |

### CRM

| Node | Description |
|------|-------------|
| **Create Entity** | Create lead/contact/company with dynamic field mappings |
| **Update Entity** | Update entity fields (read-only fields excluded) |
| **Create Task** | Create task with title, description, due date, assignee, priority |
| **Add to List** | Add entity to a static CRM list |
| **Rotate Entity Owner** | Round-robin owner assignment |
| **Add Note** | Add text note to entity with personalization |

### Agents (AI)

| Node | Description |
|------|-------------|
| **Research Contact** | AI-driven contact research |
| **Research Company** | AI-driven company research |
| **Research Lead** | AI-driven lead research |
| **Qualification Agent** | AI qualification scoring |
| **AI Agent** | Generic custom AI agent action |

### Prospect

| Node | Description |
|------|-------------|
| **Prospect Leads** | Search/filter criteria for lead prospecting |
| **Prospect Companies** | Search/filter criteria for company prospecting |

### Operation

| Node | Description |
|------|-------------|
| **Agent Action** | Custom agent action |
| **Time Delay** | Wait X duration / until specific date/time/day |
| **If/Else** | Binary condition with True/False paths, AND/OR logic, property/operator/value builder |
| **Conditional Branch** | Multi-path branching with multiple condition paths |
| **Restart Workflow** | Restart execution from beginning |

### Internal

| Node | Description |
|------|-------------|
| **Email Notification** | Internal email alert to recipients |
| **Slack Notification** | Slack channel notification |

### Interaction

| Node | Description |
|------|-------------|
| **Form** | Form submission node — integrates with Forms Service; supports `wait_for_submit` to pause flow until form is submitted |

---

## Canvas Controls

| Control | Function |
|---------|----------|
| **Zoom In/Out** | Adjust canvas magnification |
| **Reset View** | Return to default zoom and center |
| **Auto-Layout** | Rearrange scattered nodes into organized layout |
| **Lock/Unlock** | Toggle node movement on canvas |
| **Pan** | Click-drag on empty area to navigate |
| **Scroll Zoom** | Mouse wheel to zoom |

---

## Automation List Page

**URL:** `/workflows`

### Table Columns

| Column | Description |
|--------|-------------|
| **Workflow Name** | Clickable — navigates to editor |
| **Status** | DRAFT / ACTIVE / PAUSED badge |
| **Created By** | User name or email |
| **Created At** | Formatted datetime |
| **Last Updated** | Formatted datetime |
| **Actions** | Three-dot dropdown menu |

### Actions Dropdown (per row)

- **Edit Name** — opens modal with pre-populated name
- **Clone** — duplicates automation and navigates to clone editor
- **Delete** — removes automation from list
- **Start Workflow** — (DRAFT only) changes status to ACTIVE

### Search
- 300ms debounced text search filtering by automation name
- Resets pagination to page 1
- Shows empty state for no results

### Pagination
- 20 items per page (default)
- Next/Previous navigation controls

---

## Workflow: Create an Automation

1. Navigate to `/workflows`
2. Click **Create Automation** button
3. Modal opens with name input (pre-filled "Untitled")
4. Enter a name — **Save** button is disabled when name is empty
5. Click **Save** — redirects to editor at `/workflows/:id`
6. Editor loads with auto-created trigger node on canvas
7. Configure the trigger node in the right panel
8. Drag additional nodes from the left panel onto the canvas
9. Connect nodes by drawing edges between them
10. Configure each node in the right panel
11. Click **Launch Automation** (top-right) when ready

---

## Publishing Workflow

Editing a published (ACTIVE) workflow creates a draft version automatically:
- **Blue banner** appears: "This workflow has unpublished changes" with **Publish** and **Discard** buttons
- **Publish** — promotes draft to live version; workflow resumes with new config
- **Discard** — reverts canvas to last published state; draft changes are lost

---

## Key Behaviors

### Node Configuration
- **Auto-save:** Changes save on field blur/change events — no manual save button needed
- **Personalization:** Text fields include dropdown for dynamic variables (`{{contact.name}}`, `{{contact.company}}`, etc.)
- **Right panel scrollable** for long configuration forms

### Error Messages
- Launch failure: `"Failed to launch automation. Please try again."`
- Pause failure: `"[AutomationType] was not paused successfully!"`
- Name update failure: `"Automation was not updated successfully!"`
- Buttons re-enable after error; no partial state changes

---

## Key Gotchas

1. **Only one trigger node per workflow** — once a trigger is added, all trigger options in the left panel are disabled. To change the trigger type, delete the existing trigger node first.

2. **Launch is blocked without trigger + action** — the Launch button stays disabled until there is at least one configured trigger node AND at least one connected action node.

3. **Editing an ACTIVE workflow creates a draft** — changes are not live until you click **Publish** in the blue banner. Working on the canvas does not affect the running workflow until published.

4. **Discard is irreversible** — clicking Discard in the banner permanently deletes all unpublished canvas changes and restores the last published state.

5. **Analytics tab only visible for non-DRAFT workflows** — the Analytics tab in the left panel does not appear for DRAFT status automations.

6. **Auto-Layout reorganizes all nodes** — clicking Auto-Layout rearranges every node on the canvas. Use it when the layout is messy, but note it may reposition nodes you have deliberately placed.

7. **Form node requires Forms Service integration** — the Form node (`Interaction` category) only works if a form is configured in the Forms module. Set `form_id`, `form_name`, and `wait_for_submit` in the node config.

8. **Schedule trigger requires time + frequency** — the Schedule-Based trigger needs both a frequency (Daily/Weekly/Monthly) and a specific time. Missing either prevents launch.

9. **Webhook URL is auto-generated and read-only** — you cannot set a custom webhook URL. Copy the generated URL and configure it in the external system.

10. **Clone navigates immediately to the clone's editor** — clicking Clone on a workflow opens the cloned workflow in the editor automatically. The original remains unchanged.
