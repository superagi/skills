# skills

A collection of reusable **Agent Skills** for SuperAGI platform.

## Skills

### Prospecting & Outreach
- [`prospect/`](./prospect/) — find leads and companies, enrich data, track buying signals
- [`cold-outreach/`](./cold-outreach/) — AI SDR campaigns: list page, replies, analytics
- [`cold-outreach/setup/`](./cold-outreach/setup/) — workspace, app install, mailbox and LinkedIn setup
- [`cold-outreach/find-new-leads/`](./cold-outreach/find-new-leads/) — 5-step "Find New Leads" campaign wizard
- [`sequences/`](./sequences/) — manual multi-channel outreach sequences

### CRM
- [`crm/`](./crm/) — CRM CLI operations (bulk, scripting, API access)
- [`crm/records/`](./crm/records/) — CRUD for Contacts, Leads, Companies, and Deals (web UI)
- [`crm/lists/`](./crm/lists/) — create, manage, filter, and export CRM Lists
- [`crm/tasks/`](./crm/tasks/) — create and manage CRM Tasks, log calls/meetings/notes

### Automation
- [`workflows/`](./workflows/) — visual automation builder: 30+ node types, triggers, canvas, lifecycle
- [`process-design/`](./process-design/) — simplified process flows for CRM data collection and routing
- [`forms/`](./forms/) — form definitions, versioning, runtime, and submissions

### Navigation & Settings
- [`navigation/`](./navigation/) — screen/sidebar navigation
- [`settings/`](./settings/) — settings + configuration guidance
- [`chats/`](./chats/) — chat-based workflows via CLI

## Skill Relationships

Skills are interconnected — agents can traverse between them as needed:

```
prospect ──────→ crm/records ←──── crm/lists ←──── sequences
                     ↑                               ↑
                  crm/tasks                    cold-outreach
                     ↑                               ↑
                  workflows ←─── forms ─→ process-design
```

Each skill's **Related Skills** section lists exactly which other skills to navigate to for connected operations.

## Repo layout

Each skill folder contains a `SKILL.md` with usage instructions, workflows, and gotchas.
