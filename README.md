# skills

A collection of reusable **Agent Skills** for SuperAGI platform.

## Skills

### Prospecting & Outreach
- [`prospect/`](./prospect/) — find leads and companies, enrich data, track buying signals
- [`cold-outreach/`](./cold-outreach/) — AI SDR campaigns: list page, replies, analytics
  - [`cold-outreach/setup.md`](./cold-outreach/setup.md) — workspace, app install, mailbox and LinkedIn setup
  - [`cold-outreach/find-new-leads.md`](./cold-outreach/find-new-leads.md) — 5-step "Find New Leads" campaign wizard
- [`sequences/`](./sequences/) — manual multi-channel outreach sequences

### CRM
- [`crm/`](./crm/) — CRM CLI operations (bulk, scripting, API access)
  - [`crm/records.md`](./crm/records.md) — CRUD for Contacts, Leads, Companies, and Deals (web UI)
  - [`crm/lists.md`](./crm/lists.md) — create, manage, filter, and export CRM Lists
  - [`crm/tasks.md`](./crm/tasks.md) — create and manage CRM Tasks, log calls/meetings/notes

### Marketing
- [`marketing/`](./marketing/) — marketing campaigns
  - [`marketing/whatsapp-campaign.md`](./marketing/whatsapp-campaign.md) — create and launch WhatsApp bulk campaigns
  - [`marketing/email-campaign.md`](./marketing/email-campaign.md) — create and launch Email bulk campaigns (Drag-N-Drop, Plain Text, Custom HTML)

### Automation
- [`workflows/`](./workflows/) — visual automation builder: 30+ node types, triggers, canvas, lifecycle
- [`process-design/`](./process-design/) — simplified process flows for CRM data collection and routing
- [`forms/`](./forms/) — form definitions, versioning, runtime, and submissions

### Meetings
- [`meeting-links/`](./meeting-links/) — create meeting agents (One-on-One/Round Robin), booking flow, reschedule/cancel, meeting logs, AI notetaker, recordings, and transcripts

### Analytics
- [`ai-analytics/`](./ai-analytics/) — AI Analytics: spaces, dashboards, chart builder, 12 chart types, template library, calculated fields, and CSV export

### Navigation & Settings
- [`navigation/`](./navigation/) — screen/sidebar navigation
- [`settings/`](./settings/) — settings + configuration guidance
- [`chats/`](./chats/) — chat-based workflows via CLI

## Skill Relationships

Skills are interconnected — agents traverse between them using each skill's **Related Skills** table:

```
prospect ──→ crm/records.md ←── crm/lists.md ←── sequences
                  ↑                                    ↑
             crm/tasks.md                       cold-outreach
                  ↑                                    ↑
             workflows ←─── forms ──→ process-design
                  ↑
             ai-analytics ←── crm/records.md
```

## Repo layout

Each skill folder contains a `SKILL.md` (main skill) and optional `.md` files for sub-topics (e.g. `crm/lists.md`, `cold-outreach/setup.md`). All files in a folder communicate via **Related Skills** tables.
