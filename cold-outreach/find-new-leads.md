---
name: cold-outreach-find-new-leads
description: Step-by-step guide to create a Cold Outreach campaign using the "Find New Leads" flow in SuperAGI Sales — covers all 5 wizard steps including ICP filters, value prop setup, sender configuration, outreach approval, and automation
platform: [linux, macos]
---

# Cold Outreach — Create Campaign: Find New Leads

## Related Skills

| Skill | Relationship |
|-------|-------------|
| `cold-outreach-setup` | Must be completed first — workspace, app install, mailbox connection are prerequisites for this wizard. |
| `cold-outreach` | After launching, use `cold-outreach` to monitor campaign status, view replies, check analytics, and manage the campaign. |
| `crm-records` | Leads found and enriched by this campaign land in CRM as Lead records. Use `crm-records` to view, edit, or act on them. |
| `crm-lists` | The "Select a list" campaign type (not covered here) uses CRM Lists as the lead source. Use `crm-lists` to create and manage those lists. |
| `sequences` | Cold Outreach is AI-driven and volume-oriented. For manual, step-by-step multi-channel outreach, use `sequences` instead. |
| `prospect` | ICP filters in Step 1 mirror the filters in Prospect Leads. Use `prospect` skill to understand available filter options. |

---

This flow creates a new campaign where SuperAGI's AI SDR automatically finds and prospects new leads matching your ICP (Ideal Customer Profile).

**Direct URL:** `https://sales.superagi.com/cold-outreach`
**Sidebar path:** Engage → Cold Outreach → Create Campaign → Find New Leads

> **Prerequisites:** At least one mailbox must be connected (Settings → Personal Mailboxes). See `cold-outreach/setup/SKILL.md` for first-time setup.

---

## How to Start

1. Navigate to `https://sales.superagi.com/cold-outreach`
2. Click the **Create Campaign** button (top-right corner of the Campaigns tab)
3. In the modal that appears, select **Find New Leads**
4. Click the **Create** button (bottom-right of the modal)
5. You are taken into the campaign wizard — the campaign is titled **"Untitled campaign"** by default
6. Click the **pencil icon** next to the title to rename it

The campaign wizard has 5 steps shown in the left stepper:
1. **Create ICP**
2. **Define Value Prop**
3. **Sender Details**
4. **Approve Outreach**
5. **Automate**

---

## Step 1 — Create ICP (Ideal Customer Profile)

**Purpose:** Define filters that determine which leads SuperAGI will find and prospect.

**Page layout:** The center panel shows all available ICP filter fields. The right panel shows **Preview Leads** with a live estimate count.

Click the **+** icon next to any field to expand and add values:

| Filter Field | Description |
|---|---|
| **Lead Name** | Filter by specific lead names |
| **Job Title** | Target specific job titles (e.g., CEO, VP of Sales) |
| **Department** | Filter by department (e.g., Engineering, Marketing) |
| **Seniority** | Target by seniority level (e.g., Director, C-Level) |
| **HQ Location** | Filter by company headquarters location |
| **Lead Location** | Filter by where the lead is physically located |
| **Industry** | Target specific industries |
| **Technologies** | Filter companies using specific tech stack tools |
| **Revenue Range** | Filter by company annual revenue range |
| **Employee Range** | Filter by company size (number of employees) |
| **Target Company Domains** | Specify exact company domains to target |
| **Company Keywords** | Keywords that describe the target company |
| **Funding Stage** | Filter by funding round (e.g., Series A, Seed) |
| **Founded Year** | Filter by company founding year |

> **Tip:** The **Preview Leads** panel on the right updates the lead estimate count as you add or change filters. Use it to validate your ICP before proceeding.

7. Once ICP filters are set, click **Continue** (top-right) to proceed to Step 2

---

## Step 2 — Define Value Prop

**Purpose:** Define what SuperAGI's AI will use to write personalized outreach emails on your behalf.

There are two ways to fill this step:

### Option A — Use a Saved Value Prop Template

8. Click the **Value Prop Template** dropdown (first field at the top)
9. If templates exist, select one — it auto-fills all fields below
10. If no templates exist, click **Manage Value Prop Templates** in the dropdown → redirects to **Settings → Manage Value Prop Templates** (see workflow below to create one)

### Option B — Fill Fields Directly (via Company Website)

10. Leave the Value Prop Template dropdown empty
11. Enter your **Company Website** URL and click **Generate Template** — SuperAGI auto-fills the fields below using your website content
12. Review and edit all fields:

| Field | Required | Description |
|---|---|---|
| **Company Website** | No | Your company URL — used for auto-generation |
| **Company Name** | Yes | Your company name |
| **What are you selling** | Yes | Description of your product/service |
| **Pain Points** | No | Pain points your product addresses — click **+ Add** for each additional point |
| **Value Propositions** | No | Your product's key value props — click **+ Add** for each |
| **Proof Points** | No | Stats, case studies, testimonials — click **+ Add** for each |
| **Personality** | No | Tone of outreach: Friendly, Professional, etc. (default: Friendly) |
| **Outreach Language** | No | Language for emails (default: American English) |
| **Train Cold Outreach for Emails** | No | Provide sample emails to train the AI writing style |
| **Give Instructions to Cold Outreach** | No | Additional instructions for the AI — click **+ Add** for multiple |
| **Call to Action (toggle)** | No | Enable/disable a CTA button in the email |
| **CTA Button Text** | If CTA on | Label on the CTA button (e.g., `"Call Us Today"`) |
| **CTA Link Type** | If CTA on | Type of CTA link (e.g., Meeting Agent Link) |
| **CTA Link** | If CTA on | The actual URL for the CTA |

13. Once all fields are filled, click **Continue** (top-right) to proceed to Step 3

---

### Workflow: Create a Value Prop Template (in Settings)

Use this if you need to create a reusable template before selecting it in the campaign wizard.

1. From the left sidebar, go to **Settings → Manage Value Prop Templates**
   - OR click **Manage Value Prop Templates** from the Value Prop Template dropdown in the wizard
2. Click **Create**
3. A **"Create Value Prop Template"** modal appears
4. Fill in the following fields:

| Field | Required | Description |
|---|---|---|
| **Template Name** | Yes | A name to identify this template |
| **Company Website** | No | Enter your URL and click **Generate Template** to auto-fill fields |
| **Company Name** | Yes | Your company name |
| **What are you selling** | Yes | Describe your product/service in detail |
| **Pain Points** | No | Add one or more pain points — click **+ Add** for each |
| **Value Propositions** | No | Add your key value propositions — click **+ Add** for each |
| **Proof Points** | No | Add proof points like case studies or stats — click **+ Add** for each |
| **Personality** | No | Select tone: Friendly, Professional, etc. (default: Friendly) |

5. Scroll down in the modal to fill all fields
6. Click **Create Template** to save
7. Return to the campaign wizard — the new template now appears in the Value Prop Template dropdown
8. Select it from the dropdown to auto-fill all value prop fields

---

## Step 3 — Sender Details

**Purpose:** Configure which email account will send outreach emails.

### Mailbox Rotation (Toggle)
- **Off (default):** A single email account is used for sending
- **On:** SuperAGI dynamically rotates across multiple selected mailboxes to improve email deliverability
- Connect more mailboxes via **Settings → Personal Mailboxes** (link shown under the toggle)

### Select Sender Email Account

14. Click the **Select email account** dropdown
15. A picker appears showing all connected email accounts — search or scroll to find yours
16. Click an account to select it
17. To add a new mailbox, click **+ Connect New Email Account** at the bottom of the dropdown

### Display Name (shown after account is selected)

Once an email account is selected, choose how your name appears in the email body:
- **Use Name** — enter a custom display name (e.g., `"Nikhil"`)
- **Use Signature** — use an email signature instead of a plain name

18. Click **Continue** (top-right) to proceed to Step 4

---

## Step 4 — Approve Outreach

**Purpose:** Preview the AI-generated outreach email sequence and approve before sending.

> **Banner at the top reads:** "This is a sample outreach thread. When sending out, each outreach is personalized."

### Template Toggle
- **AI Personalized (toggle ON — recommended):** SuperAGI generates a fully personalized multi-step sequence based on your ICP and Value Prop
- **Template (toggle OFF):** Uses a pre-built fixed email template instead of AI personalization

### Outreach Steps Shown

**Email Outreach (first email):**
- Subject line (editable)
- Email body with dynamic variables like `{{contact.firstname}}` and `{{contact.company}}`
- **Regenerate** button — regenerates this step only
- **Delete icon** — removes this step

**Follow Up Email (subsequent steps):**
- **Wait for** field — number + unit (e.g., `"2 Days"`) to configure delay before the follow-up is sent
- Editable email body, Regenerate, and Delete per step

**Actions Available:**
- **Regenerate All** (top-right) — regenerates the entire outreach sequence at once
- Edit subject lines and email body text directly in the fields
- **+ Add Step** — adds new outreach steps (Email or LinkedIn types)

19. Once satisfied with the outreach sequence, click **Continue** (top-right) to proceed to Step 5

---

## Step 5 — Automate

**Purpose:** Configure campaign scheduling, automation mode, and sending options before launch.

### Daily Leads Quota
- Shows the current quota (default: **30 leads/day**)
- Click the **pencil icon** next to the number to edit it
- A note below shows approximate maximum emails per day based on the quota

### Automation Mode

| Mode | Description |
|---|---|
| **Manual** | Your approval will be required before sending emails |
| **Autopilot** | SuperAGI will send out all the emails by itself automatically |

### Exclusion Options

| Toggle | Default | Description |
|---|---|---|
| **Exclude people from lists** | Off | Exclude leads that are part of specific lists |
| **Exclude people already added in SuperAGI** | **On** | Prevents re-contacting leads already in your SuperAGI CRM |

### Advanced Filters (expandable section)

| Field | Default | Description |
|---|---|---|
| **Timezone** | — | Select timezone for sending (e.g., `"Asia/Kolkata"`) |
| **Active Days** | Mon–Fri | Choose which days of the week emails are sent |
| **Start Time** | 9:30am | Time to start sending emails |
| **End Time** | 5:30pm | Time to stop sending emails |

### Additional Toggles

| Toggle | Description |
|---|---|
| **Add unsubscribe link to Campaign** | Adds an unsubscribe link to the bottom of each email |
| **Limit leads per company** | Restricts the number of leads enriched from a single company |
| **Send to CC and BCC emails** | Enables CC and BCC email addresses to be included in campaign emails |

20. Once all automation settings are configured, click **Launch Campaign** (top-right) to activate the campaign

---

## Campaign Wizard — Step Summary

| Step | Page Name | Key Action |
|---|---|---|
| 1 | Create ICP | Set lead filters → check Preview Leads estimate → Continue |
| 2 | Define Value Prop | Select/create template OR fill manually → Continue |
| 3 | Sender Details | Select email account + set display name → Continue |
| 4 | Approve Outreach | Review AI-generated emails → edit if needed → Continue |
| 5 | Automate | Set quota, mode, schedule → **Launch Campaign** |

---

## Key Gotchas

1. **Preview Leads updates in real-time** — as you add or change ICP filters, the estimate in the right panel updates immediately. If it shows 0, your filters are too narrow — broaden them before continuing.

2. **Generate Template overwrites fields** — clicking **Generate Template** on the Company Website field will overwrite any manually entered Value Prop fields. Enter your website URL and generate first, then edit the pre-filled values.

3. **Pain Points, Value Props, and Proof Points each require a separate "+ Add" click** — each item in these multi-value fields is added one at a time. Do not try to enter multiple items in a single input.

4. **CTA fields only appear when the Call to Action toggle is ON** — if you need a CTA button in the email, enable the toggle first; the CTA Button Text, CTA Link Type, and CTA Link fields are hidden until it is turned on.

5. **Mailbox must be checked before display name is editable** — in Sender Details, the display name combobox and Edit button for a mailbox are disabled until you check (select) that mailbox.

6. **Wizard steps are clickable — not sequential-only** — the step labels in the left stepper (Create ICP, Define Value Prop, etc.) are clickable, allowing you to jump to any step directly without going in order.

7. **"Continue" becomes "Launch Campaign" on Step 5** — Step 5 does not have a Continue button. The final button is labeled **Launch Campaign**. Clicking it immediately activates the campaign.

8. **Exclude people already added in SuperAGI is ON by default** — this prevents re-contacting existing CRM leads. If you intentionally want to reach existing leads, you must manually turn this toggle off.

9. **Daily Leads Quota math** — the quota (e.g., 30 leads/day) × number of outreach steps = approximate maximum emails per day. The wizard shows this calculated estimate below the quota field.

10. **Value Prop Template can be reused across campaigns** — templates created in Settings → Manage Value Prop Templates are available in all campaigns. Create one template and reuse it rather than re-entering fields each time.
