---
name: crm-lists
description: Create, manage, filter, save views, export, and delete CRM Lists for Contacts, Companies, and Leads in SuperAGI CRM
platform: [linux, macos]
---

# SuperAGI CRM — Lists

## Related Skills

| Skill | Relationship |
|-------|-------------|
| `crm-records` | Records (Contacts, Leads, Companies) are the items inside a list. Use `crm-records` to create/edit/delete the records that populate lists. |
| `crm-tasks` | Bulk selecting records inside a list allows you to click "Add CRM Task" — creates tasks for those records. Navigate to `crm-tasks` to view/manage those tasks. |
| `sequences` | Bulk select records in a list → "Add to Sequence" to enroll them in outreach. Use `sequences` skill to build and manage those sequences. |
| `cold-outreach-find-new-leads` | Saved lists can be used in Cold Outreach via "Select a list" campaign type. Use `cold-outreach-find-new-leads` to configure that campaign. |
| `prospect` | In Prospect Leads, the "Target Company Domains → Select a list" filter references saved company lists. Use `crm-lists` to create those company lists first. |
| `workflows` | Workflow nodes (Add to List, Remove from List) automatically manage list membership. Use `workflows` skill to set up those automations. |

---

Lists is how you organise and segment your CRM records — Contacts, Companies, or Leads — into named, reusable groups. You create a list, add records to it, apply filters to narrow down the data, save filtered views for quick access, and export or delete lists as needed. Lists sit inside the CRM module and act as the primary way to segment and target your records for outreach or analysis.

## Sidebar Navigation

Click **CRM** in the left sidebar to expand it. Sub-sections visible:
- **Contacts** → `https://sales.superagi.com/crm/contacts`
- **Leads** → `https://sales.superagi.com/crm/leads`
- **Companies** → `https://sales.superagi.com/crm/companies`
- **Deals** → `https://sales.superagi.com/crm/deals`
- **Customers** → `https://sales.superagi.com/crm/customers`
- **Lists** → `https://sales.superagi.com/crm/lists`

Click **Lists** to land on the main Lists page.

---

## 1. Lists Page (Main View)

**URL:** `https://sales.superagi.com/crm/lists`
**Purpose:** View all lists in your workspace, filter them, search by name, and create new ones.

### Page Layout

**Tab bar (top):** Shows all list views as tabs. Default tabs are:
- **Private Lists** — lists only you can see
- **Shared Lists** — lists accessible to the whole team
- **Contact Lists** — lists filtered to Contact object type
- **Company Lists** — lists filtered to Company object type
- **Lead Lists** — lists filtered to Lead object type
- **Custom view tabs** — any saved views appear here (e.g., "test", "testir")
- **+ icon** — click to create a new saved view (always the last item in the tab bar)

**Top-right controls:**
- **Search lists** — text input, filters list names live as you type (no Enter needed)
- **Create List** button — opens the Create List modal (always visible, top-right corner)

**Column filter bar (below tabs):** Five dropdown filters to narrow what appears in the table:
- **Object ▾** — filter by Contact / Company / Lead
- **Created By ▾** — filter by the team member who created the list
- **Privacy ▾** — filter by access type
- **Created Date ▾** — filter by when the list was created
- **Last Activity ▾** — filter by most recent activity date

When a column filter is active, it shows as a chip (e.g., `Object : Contact`) with a **Reset** button appearing at the top-right of the filter bar to clear all active filters.

**Table columns:**

| Column | Description |
|--------|-------------|
| **List Name** | Name of the list — click to open list detail view |
| **Object** | Type of records in the list: Contact, Company, or Lead |
| **Size** | Number of records currently in the list |
| **Created by** | Avatar + name of the team member who created the list |
| **Last updated** | Timestamp of the most recent change |
| **⋮ (three-dot menu)** | Per-row action — reveals inline **Delete** option on hover |

**Pagination (bottom):** Page numbers `← 1  2 →` with a **20 per page ▾** dropdown to change page size.

---

## 2. Create List Modal

Triggered by clicking the **Create List** button on the Lists page (top-right corner).

### Modal Layout

The modal slides in from the right side of the screen. It contains:

**List Name field** *(mandatory)*
- Text input with placeholder `"Enter list name"`
- The **Create** button remains **disabled** until this field has a value
- Leaving it empty and clicking Create shows a validation error

**Object selector** *(choose one)*
- Three mutually exclusive options displayed as cards:
  - **Contacts** — Create a list of contacts *(selected by default)*
  - **Companies** — Create a list of companies
  - **Leads** — Create a list of leads
- The selected option shows a checkmark (✓) and highlighted border

**Who can access this list** *(choose one)*
- **Anyone from the team** *(selected by default)* — everybody in your workspace can access this list
- **Private** — only you and people you invite can access this list
  - When **Private** is selected, a **Members who can access** section appears below with a user picker dropdown showing team members to add individually

**Action buttons (bottom of modal):**
- **Cancel** — closes the modal without saving anything; any entered data is lost
- **Create** — creates the list and adds it to the Lists page; disabled until List Name is filled

### Workflow: Create a List

1. Navigate to `https://sales.superagi.com/crm/lists`
2. Click the **Create List** button (top-right corner)
3. The Create List modal slides in from the right
4. Type a name in the **List Name** field (e.g., `"Test_List_01"`)
5. Select an **Object** — click Contacts, Companies, or Leads card
6. Select **Who can access this list** — click "Anyone from the team" or "Private"
7. If "Private" selected: click the member picker and select users to grant access
8. Click **Create** — the modal closes and the new list appears in the Lists table
9. If you want to abort: click **Cancel** — modal closes, nothing is saved

---

## 3. List Detail View

Triggered by clicking any **List Name** in the Lists table.

**URL:** `https://sales.superagi.com/crm/lists/{list_id}`

### Page Layout

**Top bar:**
- **← back arrow** — returns to the Lists page
- **List name** (editable) — click the **pencil icon** next to the name to rename inline
- **More Options ▾** button (top-right) — whole-list actions dropdown
- **Add Leads / Add Contacts / Add Companies** button (top-right, label changes based on object type)

**More Options dropdown** contains:
- **Create Cold Outreach Campaign** — starts a campaign using this list
- **Add to Sequence** — adds all list records to an outreach sequence
- **Manage Access** — update who can see and use this list
- **Export List** — exports all records to your email as a file
- **Delete List** — permanently removes the list from the system

**View tabs (below top bar):**
- **All Lists** — default view showing all records in the list
- **Custom view tabs** — any saved views for this list (e.g., "Untitled View", "test")
- **+ icon** — create a new saved view for this list
- **⋮ (three-dot)** next to "All Lists" — additional view options

**Search bar (top-right of view):** `"Search leads / contacts / companies"` — live search within the list records.

**+ Filters bar:** Click to add filters that narrow the records shown in the table.

**Records table columns (for a Leads list):**

| Column | Description |
|--------|-------------|
| **Checkbox** | Select individual records for bulk actions |
| **Name** | Avatar + full name of the record |
| **Email** | Email address |
| **Phone Number** | Contact phone |
| **Current Company** | Company the lead is associated with |
| **Actions** | Quick action icons: email, call, sequence, assign owner |
| **Lead Location** | Geographic location |
| **Company HQ Location** | Company headquarters location |

**Pagination (bottom):** `← 1  2  3  4  5 →` with **20 per page ▾** dropdown.

---

## 4. Add Records to a List

Click the **Add Leads / Add Contacts / Add Companies** button (top-right of List Detail view). A panel slides in from the right with three tabs:

### Tab 1 — Create New
- Form to create a brand new record directly into this list
- Fill in the record's details and submit

### Tab 2 — Upload New
- Drag-and-drop area or **Click to upload** button
- Accepts **.csv files only**
- Upload a CSV of records to bulk-import into this list

### Tab 3 — Add Existing
- **Search leads** text input — search existing CRM records
- Checkbox list of matching records (shows name + email)
- Select one or more records using checkboxes
- Click **Add Leads** button (bottom-right of panel) to add selected records to the list
- Click **Cancel** to close without adding

---

## 5. Filters (Inside a List)

Filters narrow which records are shown inside an open list. They do not permanently remove records — they only affect the current view.

### How to Add a Filter

1. Open a list (click its name from the Lists page)
2. Click **+ Filters** in the filter bar below the view tabs
3. A **Search Property** dropdown appears — scroll or type to find a field
4. Click a property to select it as the filter field

### Available Filter Properties

**Text-based fields:**

| Property | Description |
|----------|-------------|
| **First Name** | Lead or contact first name |
| **Last Name** | Lead or contact last name |
| **Email** | Email address field |
| **Phone Number** | Phone number field |
| **Current Company** | Company the record is associated with |
| **Address** | Street address |
| **City** | City field |
| **State** | State field |
| **Country** | Country field |
| **Zipcode** | Postal code |
| **Current Role** | Job role or title |
| **LinkedIn URL** | LinkedIn profile URL |
| **Description** | Notes or description field |

**Dropdown / Relational fields:**

| Property | Description |
|----------|-------------|
| **Owner** | Who owns the record in CRM |
| **Lead Status** | Current status of the lead |
| **Lead Source** | Where the lead came from |
| **Tags** | Tags applied to records |
| **Multiselect** | Custom multi-select fields |
| **Link** | URL-type custom fields |
| **sync** | Sync status field |

**Date-based fields:**

| Property | Description |
|----------|-------------|
| **Created At** | When the record was created |
| **Updated At** | When the record was last modified |
| **Last Activity** | Most recent activity timestamp |
| **Last Modified By** | Who last changed the record |

### Filter Conditions

**For text fields**, the condition dropdown offers:

| Condition | Behaviour |
|-----------|-----------|
| **is equal to** | Exact match only |
| **is not equal to** | Excludes exact match |
| **contains** | Partial match anywhere in the value |
| **does not contain** | Excludes partial match |
| **starts with** | Value begins with the input |
| **ends with** | Value ends with the input |
| **is empty** | Field has no value (no input needed) |
| **is not empty** | Field has any value (no input needed) |

**For dropdown/relational fields**, the condition dropdown offers:

| Condition | Behaviour |
|-----------|-----------|
| **is** | Matches selected value(s) from a searchable list |
| **is not** | Excludes selected value(s) |
| **is empty** | Field has no value |
| **is not empty** | Field has any value |

**For date fields**, the options are:
- **Today**
- **Last 7 days**
- **Last 30 days**

### Multiple Filters

- Click **+ Filters** again after the first filter is applied to add a second filter
- All active filters work with **AND logic** — a record must match every active filter to appear
- Each active filter appears as a chip above the table showing the field name and condition
- Click the **delete icon (×)** on a filter chip to remove that individual filter
- To clear all filters at once, click the **Reset** button (appears top-right when filters are active)

### Workflow: Apply a Text Filter

1. Open a list from the Lists page
2. Click **+ Filters**
3. In the Search Property dropdown, click **First Name**
4. The filter chip appears: `First Name | is equal to ▾`
5. Click the condition dropdown (`is equal to`) to change the condition if needed
6. Type a value in the input field (e.g., `"John"`)
7. Table updates instantly to show only matching records
8. To remove: click the × icon on the filter chip

### Workflow: Apply a Dropdown Filter

1. Open a list and click **+ Filters**
2. Select a dropdown property (e.g., **Current Company**)
3. Filter chip shows: `Current Company | is ▾`
4. Click the condition dropdown to choose is / is not / is empty / is not empty
5. A searchable value list appears — type to search, click to select company names
6. Table updates instantly to show only records matching the selected companies

---

## 6. Save View

A **View** saves the current filter configuration as a named tab so you can return to it without re-applying filters each time. Views appear in the tab bar both on the Lists page and inside List Detail.

### How to Create a View (from Lists Page)

1. On the Lists page, apply any column filters you want to save (Object, Created By, Privacy, etc.)
2. Click the **+ icon** at the end of the tab bar
3. A panel opens on the right with:
   - **View Name** text field — enter a name for the view (e.g., `"Contact Lists Only"`)
   - **Who can access this view** — three radio options:
     - **Everyone** *(default)* — everybody in your workspace can see this view tab
     - **Specific to team members** — only selected users/teams can access
     - **Private to me** — only you can see this view tab
4. If **Specific to team members** is selected:
   - An **Add Users & Teams** button appears
   - Clicking it reveals a dropdown with two tabs: **Users** and **Teams**
   - Search and check individual members to grant access
5. Click **Done** — the view is saved and a new tab appears in the tab bar

### How Views Work

- Clicking a saved view tab filters the Lists table to show only lists matching that view's configuration
- The active view tab is highlighted
- Saved views persist after browser refresh — they are stored server-side, not in the browser
- To delete a view: click the **×** icon on the view tab (appears on hover)
- Switching between view tabs changes which lists appear in the table instantly

### Workflow: Switch Between Views

1. From the Lists page, observe the view tabs in the tab bar
2. Click any tab (e.g., "Contact Lists", "Lead Lists", or a custom tab like "test")
3. The table re-loads showing only lists that belong to that view's filter
4. Click another tab to switch — the filter updates instantly, no page reload needed
5. Filters applied within a view are remembered when you switch away and return

---

## 7. Bulk Actions (Inside a List)

When you select one or more records in a list's detail view, a **bulk action toolbar** appears above the table.

### How to Select Records

- Click individual **checkboxes** on the left of each row
- Click the **master checkbox** in the column header to open a selection dropdown:
  - **Select this Page** — selects all records visible on the current page
  - **Select all (N)** — selects every record in the list across all pages
  - **Unselect All** — deselects everything

The toolbar shows **"N selected ▾"** when records are selected.

### Bulk Action Buttons

| Button | Action |
|--------|--------|
| **Add to List ▾** | Add selected records to an existing list (search by name) or create a new list inline (enter name + optional "Mark as private list" checkbox + Create) |
| **Remove from list** | Remove selected records from the current list (records still exist in CRM) |
| **Add to Sequence ▾** | Add selected records to an outreach sequence |
| **Assign Owner ▾** | Opens owner picker — search team members and click **Assign** |
| **Add CRM Task** | Create a CRM task linked to selected records |
| **Add Note** | Add a note to selected records |
| **More ▾** | Additional actions dropdown (see below) |

### More ▾ Dropdown Options

| Option | Description |
|--------|-------------|
| **Enrich Email** | Runs email enrichment on selected records |
| **Enrich Phone Number** | Runs phone number enrichment on selected records |
| **Run Market Research** | Runs AI market research on selected records |
| **Export** | Opens the Export Leads modal to export selected records to email |

### Per-Row Action Icons

Each record row has quick action icons in the **Actions** column (visible without selecting):
- **Email icon** — send an email to this record
- **Call icon** — call this record
- **Sequence icon** — add to a sequence
- **Person icon** — assign an owner

---

## 8. Export

There are two ways to export records from a list. Both send the exported file to your registered email address — the file is **not downloaded directly to the browser**.

### Way 1 — Export Selected Records (Bulk)

1. Open a list from the Lists page
2. Select records using checkboxes
3. In the bulk action toolbar, click **More ▾**
4. Click **Export**
5. The **Export Leads** modal appears:
   - Shows message: `"N leads will be exported to your email"`
   - **Email ID** field — pre-filled with your registered email (editable)
6. Click **Export** — the file is sent to the email address shown

### Way 2 — Export Entire List (More Options)

1. Open a list from the Lists page
2. Click **More Options ▾** (top-right of list detail view)
3. Click **Export List**
4. The same **Export Leads** modal appears with your email pre-filled
5. Click **Export** — all records in the list are sent to your email

---

## 9. Delete

There are two ways to delete a list.

### Way 1 — Delete from Lists Page (Row-level)

1. On the Lists page, hover over any list row
2. Click the **⋮ (three-dot)** icon that appears on the right of the row
3. Click **Delete**
4. The list is removed immediately

### Way 2 — Delete from List Detail (More Options)

1. Open a list by clicking its name
2. Click **More Options ▾** (top-right)
3. Click **Delete List**
4. Confirm the deletion when prompted
5. The list is permanently removed from the system and no longer appears in the Lists table

---

## 10. Manage Access

Update who can see or use an existing list after it has been created.

### Workflow: Update List Access

1. Open a list from the Lists page
2. Click **More Options ▾** (top-right)
3. Click **Manage Access**
4. The access settings panel opens — change between:
   - **Anyone from the team**
   - **Private** (with member picker to add/remove specific users)
5. Save the updated access settings

---

## The Lists Workflow — End to End

How Lists connects to the rest of SuperAGI CRM:

```
1. NAVIGATE    → CRM > Lists in the left sidebar
2. CREATE      → Click "Create List" → name it, pick object type, set access → Create
3. ADD RECORDS → Open list → "Add Leads/Contacts/Companies" → Create New / Upload CSV / Add Existing
4. FILTER      → Click "+ Filters" → pick property → pick condition → enter value → table updates
5. SAVE VIEW   → Click + → name the view → set access → Done (view saved as a tab)
6. BULK ACT    → Select records → Add to List / Assign Owner / Add to Sequence / Export
7. EXPORT      → More Options → Export List → confirm email → file sent to inbox
8. DELETE      → More Options → Delete List → confirm
```

**Key connections:**
- **Lists → Sequences:** Use "Add to Sequence" from bulk toolbar to push list records into automated outreach
- **Lists → Cold Outreach:** Use "Create Cold Outreach Campaign" from More Options to target the whole list
- **Lists → Prospect Leads:** Saved lists can be selected as a "Target Company Domains" source in Prospect Leads filters
- **Lists → Data Enrichment:** Use "Enrich Email" / "Enrich Phone Number" from More ▾ to enrich selected records in bulk

---

## Key Gotchas from the UI

1. **Create button is disabled until List Name is filled:** The Create button in the Create List modal stays greyed out until at least one character is typed in the List Name field. Clicking it while disabled does nothing.

2. **Private access reveals a member picker:** Selecting "Private" in the Create List modal immediately shows a "Members who can access" section with a user dropdown. If you switch back to "Anyone from the team", the member picker disappears.

3. **Filters are AND logic only:** All active filters must be satisfied simultaneously. There is no OR toggle between different filter fields — a record must match every filter to appear in results.

4. **is empty / is not empty need no value input:** When you select these conditions for any filter, the value input field disappears — no typing needed, just selecting the condition is enough to apply the filter.

5. **Removing a filter resets results immediately:** Clicking the × icon on a filter chip removes it instantly and the table re-fetches without that condition — no confirm step.

6. **Export goes to email, not browser download:** Clicking Export does not trigger a file download in the browser. The export file is sent to the email address shown in the Export modal. Make sure the email shown is correct before clicking Export.

7. **Delete from the Lists page row is instant:** Using the ⋮ → Delete on a row from the main Lists page removes the list immediately without a confirmation prompt. Delete from inside the list (More Options → Delete List) shows a confirmation step.

8. **View tabs persist after browser refresh:** Saved views are stored server-side. Refreshing the page, closing the tab, or logging out and back in will not lose your saved views — they always appear in the tab bar.

9. **Switching view tabs changes the filter instantly:** Clicking between view tabs on the Lists page does not trigger a page reload — the table data updates immediately to match the selected view's filter configuration.

10. **List Name supports duplicates (behavior TBD):** The system may allow two lists with the same name without showing an error.

11. **Upload New accepts CSV only:** The "Upload New" tab in the Add Leads panel accepts only `.csv` files. Other formats (xlsx, txt) are not supported and will be rejected.

12. **Search on the Lists page searches list names only:** The search bar (top-right of Lists page) matches on List Name only — it does not search by Object type, Creator, or any other column.

13. **Search and column filters work simultaneously:** The search bar and the Object/Privacy/Created By/Created Date/Last Activity filter dropdowns can all be active at the same time. Records must match all active criteria to appear.

14. **Add to List from bulk toolbar can create a new list inline:** When you click "Add to List ▾" in the bulk toolbar, you can search for an existing list OR click "+ Create New List" to create one on the spot — just type a name, optionally check "Mark as private list", and click Create.

15. **Pagination persists through filters:** When a filter is active and you navigate to page 2 or beyond, the filter remains applied — you will not lose your filter state by changing pages.

16. **Large dataset performance:** When a list contains a very large number of records, the table should still load without UI breaking, freezing, or layout shifts. If the UI shows a blank table or a spinner that never resolves on large datasets, that is a bug.
