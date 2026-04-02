---
name: crm-tasks
description: Create, manage, and track CRM Tasks in SuperAGI Sales — including task creation, editing, activity logging (notes, emails, calls, meetings), filtering, view management, and association with contacts, leads, companies, and deals.
platform: [linux, macos, windows]
---

# SuperAGI CRM — CRM Tasks

## Related Skills

| Skill | Relationship |
|-------|-------------|
| `crm-records` | Tasks are associated with Contacts, Leads, Companies, and Deals via the Object Hierarchy panel. Use `crm-records` to look up or create those records. |
| `crm-lists` | Bulk selecting records inside a List → "Add CRM Task" creates tasks for those records in bulk. Use `crm-lists` to manage the list of records first. |
| `sequences` | Tasks of type "Manual Phone Call Task", "Manual Email Task", etc. in Sequences surface as CRM Tasks. Use `crm-tasks` to action them. |
| `workflows` | The Workflow "Create Task" node automatically creates CRM Tasks. Use `workflows` to automate task creation based on CRM events. |
| `crm` | CLI-based access to the `crm_tasks` object type — use for bulk task queries, updates, or automation scripts. |

---

CRM Tasks is the task management module inside SuperAGI CRM. It lets you create and assign tasks, track their status and priority, log activities (notes, emails, calls, meetings), and associate tasks with CRM records (Contacts, Leads, Companies, Deals). Tasks move through a lifecycle: **Todo → In Progress → Done**.

## Sidebar Navigation

In the left sidebar, click **CRM** to expand the CRM section. Then click **CRM Tasks**:
- **CRM Tasks** → `https://sales.superagi.com/tasks`

---

## 1. Task List Page

**URL:** `https://sales.superagi.com/tasks`
**Purpose:** View, search, filter, and manage all CRM tasks across the team.

### Page Layout

**Top tab bar (predefined views):**
- **All Tasks** (default, active on load) — shows all tasks across all users
- **My Tasks** — tasks assigned to the logged-in user only
- **Due Today** — tasks whose due date is today
- **Overdue** — tasks that are past their due date
- **Upcoming** — tasks due in the future
- **Untitled View** — a user-created custom view
- **Everyone** — tasks visible across all team members
- **+ icon** (circle with plus, after the last tab) — click to add a new view. Shows a dropdown with two options: **Table** and **Board**

**Top-right action bar (left to right):**
- **Search by title** — text input field to search tasks by their title
- **Play Tasks** — grey button, launches a focused one-task-at-a-time mode
- **Add CRM Task** — black primary button, opens the Add CRM Task side panel

**Task table columns (default visible, left to right):**
- **Checkbox** — for bulk selecting tasks
- **Title** — the task name (clickable → opens task detail page)
- **Description** — task description text (shows `--` if no description was entered)
- **Created By** — avatar circle with initials + full name of the creator
- **Status** — shows a **Mark as Done** quick-action button per row
- **+ icon** (column header) — click to add a new custom column to the table
- **⋮** (kebab icon, far right of each row) — per-row action menu

**Top-left:**
- **+ Filters** button — opens the filter property panel

**Top-right three-dot menu (⋮ at the very top-right of the page, above the table):**
Clicking this opens a panel for the current view with:
- **Layout** — shows current layout as **Table** with arrow to change
- **Permissions** — shows **Private** with arrow to change
- **Property Visibility** — click to manage which columns are visible
- **Export CSV** — click to download all task data as a CSV file
- **Done** button — closes this panel

**Bottom pagination bar:**
- Displays: `1–10 of [total count]`
- Navigation: left arrow (`‹`), page number buttons (1, 2, 3, 4, 5), right arrow (`›`)
- **Per page dropdown** (bottom-right) — click to change results per page. Options: **10**, **20**, **50**, **100**. Default is **10**.

---

## 2. Add CRM Task Modal

**Trigger:** Click the **Add CRM Task** black button (top-right of task list page).
**Behavior:** A side panel slides in from the right side of the screen. Title of the panel: **"Add CRM Task"**. Has an **×** close icon at the top-right of the panel.

### Fields in the Modal (top to bottom)

| Field | Type | Required | Default | Exact Options / Notes |
|---|---|---|---|---|
| Parent CRM Task | Dropdown | No | Empty | Placeholder: "Select CRM Task". Links this task as a child of an existing task |
| Title | Text input | **Yes** | Empty | Placeholder: "Enter Title". Marked with `*`. Clicking **Add CRM Task** without a title shows a validation error |
| Description | Textarea | No | Empty | Placeholder: "Enter Description". Multi-line free text. Resizable. |
| Status | Dropdown | No | **Todo** | Exact options: **Todo**, **In Progress**, **Done** |
| Assigned To | Dropdown | No | Logged-in user | Lists all team members. Has a clear (×) icon to remove selection |
| Priority | Dropdown | No | **Medium** | Exact options: **Low**, **Medium**, **High** |
| Task Type | Dropdown | No | Empty | Placeholder: "Select Task Type". Exact options: **Phone Call**, **Email**, **Task**, **Meeting**, **LinkedIn InMail**, **LinkedIn Invite**, **LinkedIn Message**, **Whatsapp Message**, **Send Letter/Quote**, **OTHER** |
| Due Date | Date picker | No | Empty | Calendar UI with month/year navigation. Has a **Today** shortcut button at the bottom of the calendar. Format shown: MM/DD/YYYY |
| Due Time | Dropdown | No | 12:00 PM | Time slots in **15-minute intervals**. Starts from 6:45 AM. Default shown: 12:00 PM |
| Email Reminder | Dropdown | No | Empty | Placeholder: "Select Email Reminder". Exact options: **No Reminder**, **At task due time**, **30 mins before**, **1 hour before**, **1 day before**, **2 days before**, **1 week before**, **2 weeks before** |
| Associated Contact | Dropdown | No | Empty | Placeholder: "Select Associated Contact". Lists CRM contacts by name |
| Associated Lead | Dropdown | No | Empty | Placeholder: "Select Associated Lead". Lists CRM leads by name |
| Associated Company | Dropdown | No | Empty | Placeholder: "Select Associated Company". Lists CRM companies |
| Associated Deal | Dropdown | No | Empty | Placeholder: "Select Associated Deal". Lists CRM deals |

**Modal action buttons (bottom-right):**
- **Cancel** — closes the modal without saving anything
- **Add CRM Task** (black button) — validates and saves the task

### Workflow: Create a Task (Minimal)

1. Navigate to `https://sales.superagi.com/tasks`
2. Click **Add CRM Task** button (top-right)
3. The **Add CRM Task** side panel opens from the right
4. Enter a value in the **Title** field (only mandatory field)
5. Click **Add CRM Task** button
6. Task is created with defaults: Status = Todo, Priority = Medium, Assigned To = logged-in user
7. New task appears immediately at the top of the task list

### Workflow: Create a Task (Full — All Fields)

1. Navigate to `https://sales.superagi.com/tasks`
2. Click **Add CRM Task**
3. Optionally select a **Parent CRM Task** from dropdown
4. Enter **Title** (mandatory)
5. Enter **Description**
6. Set **Status** — Todo / In Progress / Done
7. Set **Assigned To** — select a team member
8. Set **Priority** — Low / Medium / High
9. Set **Task Type** — select from the 10 options
10. Set **Due Date** — pick from calendar or click Today
11. Set **Due Time** — select a 15-minute slot
12. Set **Email Reminder** — select timing option
13. Set **Associated Contact / Lead / Company / Deal** — select from CRM records
14. Click **Add CRM Task**
15. Task appears in the list with all saved values

### Workflow: Create a Child Task (Parent-Child Linking)

1. Open Add CRM Task modal
2. Click **Parent CRM Task** dropdown (first field at the top)
3. Search and select an existing task from the dropdown
4. Fill in the Title and other fields
5. Click **Add CRM Task**
6. Task is saved as a child of the selected parent task

---

## 3. Task List Actions

### Mark as Done (Quick Action from List)

Each task row has a **Mark as Done** button visible in the Status column area.

1. Find the task row in the list
2. Click **Mark as Done** button on that row
3. Task status updates to **Done** immediately — no page reload needed

### Row Kebab Menu (⋮)

Click the **⋮** (three-dot) icon at the far right of any task row. A dropdown appears with exactly three options:

| Option | What it does |
|---|---|
| **Edit** | Opens the task detail page (same as clicking the title) |
| **Delete** | Deletes the task permanently. Confirm if a confirmation dialog appears. |
| **Create follow up task** | Opens the Add CRM Task modal with the current task pre-filled as the Parent CRM Task |

### Workflow: Delete a Task

1. Click **⋮** on the task row
2. Click **Delete**
3. Confirm deletion if prompted
4. Task is permanently removed from the list

### Workflow: Create a Follow-Up Task

1. Click **⋮** on the task you want to follow up on
2. Click **Create follow up task**
3. Add CRM Task modal opens — Parent CRM Task is already pre-filled with the current task
4. Enter the Title and any other fields for the follow-up
5. Click **Add CRM Task** to save

---

## 4. Search and Filters

### Search by Title

1. Click the **Search by title** text input (top-right area, left of Play Tasks button)
2. Type a full or partial task title
3. Task list filters in real-time as you type
4. To clear: delete the text in the input — full list restores

### Filters

Click **+ Filters** button (top-left, below the tab bar) to open the filter panel.

**All filterable properties:**

| Property | Available Operators |
|---|---|
| Title | is equal to, is not equal to, contains, does not contain, starts with, ends with, is empty, is not empty |
| Description | is equal to, is not equal to, contains, does not contain, starts with, ends with, is empty, is not empty |
| Created By | is, is not, is empty, is not empty |
| Status | is, is not, is empty, is not empty |
| Assigned To | is, is not, is empty, is not empty |
| Created At | Today, Yesterday, Last 3 days, Last 7 days, Last 30 days, This month, Last month |
| Priority | is, is not, is empty, is not empty |
| Updated At | Today, Yesterday, Last 3 days, Last 7 days, Last 30 days, This month, Last month |
| Task Type | is, is not, is empty, is not empty |
| Due Date | Today, Yesterday, Last 3 days, Last 7 days, Last 30 days, This month, Last month |
| Last Modified By | is, is not, is empty, is not empty |
| Due Time | is equal to, is not equal to, contains, does not contain |
| Email Reminder | is, is not, is empty, is not empty |
| Boolean | is true, is false |

### Workflow: Apply a Single Filter

1. Click **+ Filters**
2. Filter panel opens with **Search Property** input
3. Click a property from the list (e.g., **Status**)
4. An operator dropdown appears — select an operator (e.g., **is**)
5. Select or enter a value (e.g., **Todo**)
6. Task list updates automatically to show matching tasks
7. To remove the filter: click the **trash icon** on the active filter pill

### Workflow: Apply Multiple Filters (AND Logic)

1. Apply the first filter (e.g., Status = Todo)
2. Click **+ Filters** again
3. Select the second property (e.g., Priority = High)
4. Both filters are now active — list shows only tasks matching ALL conditions (AND logic)

---

## 5. View Management

### Add a New View

1. Click the **+** (circle plus icon) after the last tab in the tab bar
2. A small dropdown appears with label **"Add a new view"** and two options:
   - **Table** — standard row/column list view
   - **Board** — kanban-style board view
3. Click the desired view type
4. New view tab is created and becomes active

### View Settings Panel

Click the **⋮** (three-dot icon) at the top-right of the page to open the view settings panel:

- **Layout** — shows current as **Table** with arrow to change
- **Permissions** — shows **Private** with arrow to change
- **Property Visibility** — click to open column show/hide panel
- **Export CSV** — click to download all task data in CSV format
- **Done** — closes this settings panel

### Property Visibility

1. Click **⋮** (top-right of page) → view settings panel opens
2. Click **Property Visibility**
3. Panel shows a list of all available columns with a **Search columns** input at top
4. Available columns: **Title**, **Description**, **Created By**, **Status**, **Created At**, **Assigned To**, **Priority**, **Updated At**
5. Each column has:
   - A **drag handle** on the left — drag to reorder columns
   - An **eye icon** on the right — click to toggle visibility
6. Changes apply to the table in real-time
7. Click **Done** to close

### Export CSV

1. Click **⋮** (top-right of page)
2. Click **Export CSV**
3. A CSV file containing the current view's task data downloads to the browser

---

## 6. Task Detail Page

**Trigger:** Click on any task **Title** in the task list.
**URL pattern:** `https://sales.superagi.com/crm/crm_tasks/[task-uuid]`

### Page Layout — Three Panels

**Left panel — Property Group:**
- **← Back** link at the top-left — returns to CRM Tasks list
- Task **title** as a heading
- **Note** button — quick shortcut to open Add New Note panel
- All task fields listed below, all **inline editable**:
  - Title (mandatory)
  - Description
  - Status
  - Assigned To
  - Priority
  - Task Type
  - Due Date
  - Due Time
  - Email Reminder

**Center panel — Activity/Tabs area:**
Tabs from left to right:
- **Activity** (default active tab)
- **Notes**
- **Emails**
- **Calls**
- **Meetings**

> Note: Calls and Meetings tabs may appear twice in the tab bar — use the first occurrence of each.

**Right panel — Object Hierarchy:**
- Header: **"Object Hierarchy"**
- **[Task Name]** with **"Current"** badge — the task itself
- **Contacts** section — with **+ Add** button
- **Leads** section — with **+ Add** button
- **Companies** section — with **+ Add** button
- **Deals** section — with **+ Add** button
- Each section shows linked records or **"No results found!"** empty state

---

## 7. Activity Tab

**Purpose:** A read-only, auto-generated log of every change made to the task.

**Location:** Center panel → **Activity** tab (default active when task detail opens)

**Filter controls (top of activity feed):**
- **Activity type** dropdown — filter by type (note added, field changed, etc.)
- **Updated by** dropdown — filter by the team member who made the change
- **Updated date** dropdown — filter by when the change happened

**Each activity entry shows:**
- Bold label of what changed: e.g., `"Note added"` or `"Due Time"`
- Full change description: `"[Field] updated from [old value] to [new value] by [user]"`
- Timestamp: e.g., `Mar 27, 2026 · 11:42am`

**What is automatically logged:**
- Any field value change (Status, Priority, Due Date, Due Time, Task Type, Assigned To, Email Reminder, etc.)
- Notes added
- Emails sent
- Calls logged
- Meetings logged

**Important:** You cannot manually add entries to the Activity tab. It is auto-generated only.

---

## 8. Notes Tab

**Purpose:** Add freeform notes to a task with rich text formatting and optional file attachments.

**Location:** Center panel → **Notes** tab

### Add New Note Panel

Clicking **Add Note** button (top-right of notes area) or the **Note** quick-action button on the left panel opens a side panel from the right titled **"Add New Note"** with:

- **Rich text editor toolbar:** Normal (style dropdown), Bold, Italic, Underline, Link, Blockquote, Numbered list, Bullet list, Align, Image, Clear formatting
- **Note body input** — placeholder: `"Enter note details"` — click and type
- **Attach files** link (bottom-right, with paperclip icon)
- **Add Note** button (bottom-right, black) — disabled until content is entered
- **×** close icon — closes without saving

### Workflow: Add a Note

1. Open task detail page
2. Click the **Notes** tab in the center panel
3. Click **Add Note** button (top-right of notes area)
4. **Add New Note** side panel opens from the right
5. Click in the note body area and type your note content
6. Optionally apply formatting using the toolbar
7. Optionally click **Attach files** to attach a file
8. Click **Add Note** (black button, bottom-right)
9. Success toast: **"Note added successfully"** (green checkmark)
10. Note appears in the Notes tab list with author name and timestamp
11. Activity tab auto-logs: `"Note added by [user]"` with the note content

---

## 9. Emails Tab

**Purpose:** Compose and send emails directly from the task context. Requires a connected email account (Gmail or Outlook).

**Location:** Center panel → **Emails** tab

### Compose Email Panel

Opens a side panel from the right titled **"Compose Email"** with:

**Banner (shown when no email account is connected):**
- Text: **"Connect Your Email"** — "Please connect your email account to send & receive emails within SuperAGI"
- **Connect Gmail** button
- **Connect Outlook** button

**Email form fields:**
- **From:** — sender email address (auto-filled once account is connected)
- **To:** — recipient email address input. Also has **CC** and **BCC** toggle links
- **Subject:** — subject line text input. Has a `{ }` personalization icon on the right
- **Message body** — rich text editor. Placeholder: `"Enter Message"`
- **Bottom bar options:** **Insert** | **Email Template** | **Personalize**
- **Send Email** button (bottom-right)

### Workflow: Send an Email from a Task

1. Open task detail page
2. Click the **Emails** tab
3. Click the compose/send email action to open the **Compose Email** panel
4. If **"Connect Your Email"** banner appears: click **Connect Gmail** or **Connect Outlook** and complete the OAuth flow
5. Fill in the **To** field with recipient email address
6. Fill in the **Subject** line
7. Type the **Message body**
8. Click **Send Email**
9. Email is sent and logged in the Emails tab with timestamp

---

## 10. Calls Tab

**Purpose:** Log a phone call activity on the task with full call details.

**Location:** Center panel → **Calls** tab

### Log Call Panel

Clicking the log call action opens a side panel titled **"Log Call"** from the right with:

| Field | Default | Notes |
|---|---|---|
| Contact/Lead Number | Empty | Recipient's phone number (country flag dropdown) |
| User number | Empty | Caller's phone number (country flag dropdown) |
| Team member | Logged-in user | Select which team member made the call |
| Direction | Empty | Options: Inbound, Outbound |
| Status | Empty | Call outcome status |
| Disposition | Empty | Call outcome/disposition |
| Duration | Empty | Enter call duration in **minutes** |
| Date | Today's date | Format: YYYY-MM-DD |
| Time | Current time | 12-hour format |
| Description | Empty | Rich text editor — placeholder: `"Describe the call..."` |

**Action button:** **Log Activity** (black button, bottom-right)

### Workflow: Log a Call

1. Open task detail page
2. Click the **Calls** tab in the center panel
3. Click the log call action to open the **Log Call** panel
4. Enter **Contact/Lead Number** (select country flag + enter number)
5. Enter **User number** (your phone number)
6. Select **Team member**, **Direction**, **Status**, **Disposition**
7. Enter **Duration** in minutes
8. Verify **Date** and **Time** (both default to now)
9. Enter a **description** of the call
10. Click **Log Activity**
11. Call appears in the Calls tab; Activity tab auto-logs the entry

---

## 11. Meetings Tab

**Purpose:** Log a meeting activity on the task with attendees, outcome, and timing.

**Location:** Center panel → **Meetings** tab

### Log Meeting Panel

Clicking the log meeting action opens a side panel titled **"Log Meeting"** with:

| Field | Default | Notes |
|---|---|---|
| Attendees | Empty | Select attendees from team members or contacts |
| Outcome | Empty | Meeting outcome |
| Disposition | Empty | Meeting disposition |
| Date | Today's date | Format: YYYY-MM-DD |
| Start Time | Current time | Start time of meeting |
| End Time | ~1 hr after start | End time of meeting |
| Description | Empty | Rich text editor — placeholder: `"Describe the meeting..."` |
| Attach files | — | Paperclip icon, bottom-right |

**Action button:** **Log Activity** (black button, bottom-right)

### Workflow: Log a Meeting

1. Open task detail page
2. Click the **Meetings** tab in the center panel
3. Click the log meeting action to open the **Log Meeting** panel
4. Select **Attendees**, **Outcome**, **Disposition**
5. Set **Date**, **Start Time**, **End Time**
6. Enter a **description** of the meeting
7. Optionally click **Attach files** to upload a file
8. Click **Log Activity**
9. Meeting appears in the Meetings tab; Activity tab auto-logs the entry

---

## 12. Object Hierarchy — Associations

**Purpose:** Link a task to existing or new CRM records — Contacts, Leads, Companies, and Deals — from the right panel of the task detail page.

**Location:** Right panel of the task detail page under **"Object Hierarchy"**

### Workflow: Add an Existing Lead

1. Open task detail page
2. In the right panel, click **+ Add** next to **Leads**
3. **Add Leads** panel opens from the right with two tabs:
   - **Create New** — to create a brand-new lead and link it
   - **Add Existing** — to search and select from existing CRM leads
4. Click **Add Existing** tab
5. Type to search for a lead name
6. Check the checkbox(es) next to the lead(s) you want to associate
7. Click **Add Existing Leads** (black button, bottom-right)
8. Selected leads now appear under Leads in Object Hierarchy

### Workflow: Create and Link a New Company

1. Open task detail page
2. In the right panel, click **+ Add** next to **Companies**
3. **Add Companies** panel opens — defaults to **Create New** tab
4. Fill in: **Name**, **Owner**, **Industry**, **Country**, **Website**, **Description**, **LinkedIn URL**
5. Click **Add Companies** (black button, bottom-right)
6. New company is created in CRM Companies AND linked to this task

---

## 13. Inline Editing — Task Detail Page

All task property fields on the left panel are directly editable without opening any modal. Changes auto-save.

### How Inline Editing Works

1. Open task detail page (click task title from list)
2. In the **Property Group** (left panel), click any field value
3. The field becomes interactive:
   - **Dropdowns** (Status, Priority, Task Type, Email Reminder, Assigned To): dropdown opens immediately
   - **Text fields** (Title, Description): text input becomes active for typing
   - **Date fields** (Due Date): calendar picker opens
   - **Time fields** (Due Time): time slot dropdown opens
4. Select or type the new value
5. Click outside the field or press Enter to confirm
6. Value saves immediately — no save button needed
7. **Activity tab** auto-logs: `"[Field name] updated from [old value] to [new value] by [username]"`

---

## Key Gotchas from the UI

1. **Title is the ONLY mandatory field** — all other fields have defaults or are optional. Status defaults to **Todo**, Priority defaults to **Medium**, Assigned To defaults to the logged-in user.

2. **Exact Task Type values** — the dropdown options are: **Phone Call** (not "Call"), **Email**, **Task**, **Meeting**, **LinkedIn InMail**, **LinkedIn Invite**, **LinkedIn Message**, **Whatsapp Message**, **Send Letter/Quote**, **OTHER**. Do not use abbreviated names.

3. **Due Time starts at 6:45 AM** — the earliest available time slot in the Due Time dropdown is 6:45 AM, not 12:00 AM. Default shown is 12:00 PM.

4. **Email Reminder options are fixed** — the 8 exact options are: No Reminder, At task due time, 30 mins before, 1 hour before, 1 day before, 2 days before, 1 week before, 2 weeks before.

5. **Email Reminder without Due Date** — if you select a reminder but do not set a Due Date, the reminder may not trigger. Always set Due Date + Due Time when using Email Reminder.

6. **Duplicate Calls and Meetings tabs** — the task detail center panel may show Calls and Meetings tabs twice. Use the first occurrence of each.

7. **Connect Email before sending** — the Emails tab shows a **"Connect Your Email"** banner with **Connect Gmail** and **Connect Outlook** buttons when no account is linked. Emails cannot be sent without completing this setup.

8. **Activity tab is read-only** — you cannot manually create Activity entries. All entries are auto-generated. To log something manually, use Notes, Calls, or Meetings tabs.

9. **Note button on left panel = shortcut** — the **Note** button on the left panel opens the same **Add New Note** panel as clicking Notes tab → Add Note button.

10. **Add Leads has multi-select** — in the Object Hierarchy "+ Add" panel for Leads, the "Add Existing" tab allows selecting multiple leads via checkboxes before clicking "Add Existing Leads".

11. **Add Companies defaults to Create New** — unlike Leads where "Add Existing" is available immediately, for Companies the panel opens on "Create New" showing the full company creation form.

12. **Multiple filters use AND logic** — when two or more filters are active, the list shows only tasks that match ALL conditions simultaneously.

13. **Property Visibility columns** — the exact 8 columns that can be shown/hidden are: **Title**, **Description**, **Created By**, **Status**, **Created At**, **Assigned To**, **Priority**, **Updated At**.

14. **Per-page options** — the pagination dropdown has exactly 4 options: **10** (default), **20**, **50**, **100**.

15. **View types** — clicking + in the tab bar offers exactly two view types: **Table** and **Board**.

16. **"Create follow up task"** in the row kebab menu — pre-fills the Parent CRM Task field in the Add CRM Task modal with the current task, making it easy to create a linked child task.

17. **Log Activity button** — both the **Log Call** and **Log Meeting** panels use the same button label: **"Log Activity"** (not "Log Call" or "Log Meeting"). Always click **Log Activity** to save.

18. **Play Tasks button** — the **Play Tasks** grey button launches a focused, one-task-at-a-time mode. It is separate from the standard list view.
