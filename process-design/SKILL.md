---
name: process-design
description: Create and manage Process Flows in SuperAGI — a simplified workflow builder for CRM data collection, routing, and internal process management using forms, conditional branches, and notifications
platform: [linux, macos]
---

# SuperAGI Process Design (Process Flows)

Process Design (Process Flows) is a simplified variant of the Workflows/Automations system, focused on CRM data collection, routing, and internal process management. It uses the same editor canvas but with a reduced set of node types tailored for structured business processes.

**URL:** `/process-flows` (list page) | `/process-flows/:id` (editor)

> **See also:** `workflows/SKILL.md` for the full Automations system. `forms/SKILL.md` for the Forms service that powers Form nodes.

---

## How Process Design Differs from Workflows

| Aspect | Workflows (Automations) | Process Design (Process Flows) |
|--------|------------------------|-------------------------------|
| **Scope** | Full sales/marketing automation | CRM data collection & routing |
| **Node Types** | 30+ types across 8 categories | Limited subset (triggers, forms, conditionals, notifications) |
| **Triggers** | Event, Schedule, Webhook, Manual | Trigger, Manual Trigger (simplified) |
| **Analytics** | Full execution metrics and node-level data | Not available |
| **AI Agents** | Research, Qualification, AI Agent nodes | Not included |
| **Engagement** | Email, WhatsApp, Sequences, Voice | Not included |
| **Prospecting** | Prospect Leads/Companies nodes | Not included |
| **Use Case** | Automated multi-channel outreach & CRM ops | Internal process workflows, data capture, routing |

---

## Supported Node Types

### Triggers

| Node | Description |
|------|-------------|
| **Trigger** | Event-based trigger for process flow events |
| **Manual Trigger** | On-demand execution trigger |

**Process-specific trigger events:**
- `process_flow:create_lead_clicked` — triggered when a user clicks to create a lead within a process flow
- `process_flow:create_deal_clicked` — triggered when a user clicks to create a deal within a process flow

### Interaction

| Node | Description |
|------|-------------|
| **Form** | Display a form for data collection; supports `wait_for_submit` to pause the flow until the form is submitted |

### Operation

| Node | Description |
|------|-------------|
| **Conditional Branch** | Multi-path routing based on conditions (property/operator/value) |

### Internal

| Node | Description |
|------|-------------|
| **Email Notification** | Send internal email alerts |
| **Slack Notification** | Send Slack channel notifications |

---

## Editor Layout

The Process Flow editor uses the same 3-panel layout as the Workflows editor:

| Panel | Content |
|-------|---------|
| **Left — Steps** | Reduced set of draggable node types |
| **Center — Canvas** | ReactFlow canvas for visual design |
| **Right — Configuration** | Node configuration form |

### Key Differences from Workflows Editor
- **No Analytics tab** in the left panel (even for active process flows)
- **Fewer node categories** in the Steps panel
- Uses `ProcessFlowService` for API calls instead of `AutomationService`

---

## Lifecycle

```
DRAFT → ACTIVE → PAUSED → ACTIVE (cycle)
```

- **Launch** — activates the process flow
- **Pause** — stops accepting new triggers
- **Resume** — re-enables trigger acceptance

---

## Form Node Configuration

When adding a **Form** node to a process flow:

| Field | Description |
|-------|-------------|
| `form_id` | References a specific form definition from the Forms module |
| `form_name` | Display name shown on the canvas node |
| `wait_for_submit` | When **enabled**, the flow pauses at this node until the form is submitted |

**Runtime behavior:** When a process flow reaches a Form node, it opens the form for the user, collects data, and proceeds upon submission.

---

## Typical Use Cases

### 1. Lead Qualification Process
```
Manual Trigger → Form (qualification questions) → Conditional Branch (score-based routing) → Notifications
```

### 2. Deal Approval Workflow
```
Trigger (deal created) → Form (approval checklist) → Conditional Branch (approved/rejected) → Email Notification
```

### 3. Data Collection Pipeline
```
Manual Trigger → Form 1 → Form 2 → Form 3 → CRM entity creation → Slack Notification
```

### 4. Routing & Assignment
```
Trigger event → Conditional Branch (on entity attributes) → Different notification channels based on criteria
```

---

## Workflow: Create a Process Flow

1. Navigate to `/process-flows`
2. Click **Create Process Flow** button
3. Enter a name for the process flow
4. Click **Save/Create** — redirects to editor at `/process-flows/:id`
5. Drag a **Trigger** or **Manual Trigger** node onto the canvas
6. Connect a **Form** node for data collection (set `form_id`, `form_name`, enable `wait_for_submit` if needed)
7. Add a **Conditional Branch** node if routing is needed
8. Add **Email Notification** or **Slack Notification** nodes at the end of each path
9. Connect all nodes with edges
10. Click **Launch** to activate

---

## Key Gotchas

1. **No Analytics tab** — unlike Workflows, Process Design has no analytics view even after the flow is active. Use the Workflows Analytics tab for execution metrics if you need them.

2. **Form node requires a published form** — the `form_id` field in the Form node must reference a form that exists in the Forms module and has at least one published version. Unpublished or deleted forms will cause runtime errors.

3. **`wait_for_submit` pauses the entire flow** — when this flag is ON, the process flow will not advance to the next node until the form is submitted. If a user never submits the form, the flow remains paused indefinitely at that node.

4. **Conditional Branch requires complete conditions** — each branch path must have a fully configured condition (property + operator + value). Incomplete conditions prevent launch.

5. **Same lifecycle as Workflows** — DRAFT → ACTIVE → PAUSED → ACTIVE. Launch requires at least one trigger node and one connected action node.

6. **Process-flow-specific trigger events** — the events `process_flow:create_lead_clicked` and `process_flow:create_deal_clicked` are only available in Process Design, not in the Workflows trigger event list.
