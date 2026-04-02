---
name: crm-records
description: Create, edit, delete, and search Contacts, Leads, Companies, and Deals in SuperAGI CRM web UI
platform: [linux, macos]
---

# SuperAGI CRM — Contacts, Leads, Companies & Deals

This skill covers CRUD operations on the four primary CRM record types via the SuperAGI Sales web UI. Each module follows the same pattern: list page → Add button → form → detail page.

## Sidebar Navigation

Click **CRM** in the left sidebar to expand it:
- **Contacts** → `https://sales.superagi.com/crm/contacts`
- **Leads** → `https://sales.superagi.com/crm/leads`
- **Companies** → `https://sales.superagi.com/crm/companies`
- **Deals** → `https://sales.superagi.com/crm/deals`

---

## 1. Contacts

**URL:** `https://sales.superagi.com/crm/contacts`

### Page Layout

- **Search bar** — visible at the top; searches by First Name, Last Name, and Email only
- **Add Contact** button (top-right) — opens the Add Contact form
- **Contacts table** — all contact records in rows; each row has a **⋮ (three-dot)** menu on hover

### Add Contact Form — All Fields

| Field | Required | Notes |
|-------|----------|-------|
| **First Name** | Yes | Free text, e.g., `"Suhani"` |
| **Last Name** | Yes | Free text, e.g., `"Das"` |
| **Email** | No | e.g., `"suhani.das@gmail.com"` |
| **Phone Number** | No | e.g., `"9876543210"` |
| **Current Company** | No | Dropdown — if company doesn't exist, type the name and click **Add** to create it; if it exists, select from dropdown |
| **Address** | No | Street address |
| **City** | No | e.g., `"Bangalore"` |
| **State** | No | e.g., `"Karnataka"` |
| **Country** | No | Dropdown — select from list, e.g., `"India"` |
| **Zipcode** | No | e.g., `"560001"` |
| **Current Role** | No | Job title, e.g., `"QA Analyst"` |
| **Owner** | No | Dropdown — pre-filled with logged-in user; change if needed |
| **Contact Status** | No | Dropdown — options include: **New**, **In-Progress** |
| **LinkedIn URL** | No | e.g., `"https://linkedin.com/in/suhani-das"` |
| **Description** | No | Free text, e.g., `"Interested in CRM demo"` |
| **Tags** | No | Type a tag name and press Enter to create new; or select existing from dropdown |
| **Lists** | No | Select existing list from dropdown; or click **Create New List**, enter a name, and click **Create List** |

**Submit button:** **Add Contact** (bottom of form)

### Workflow: Create a Contact

1. Navigate to `https://sales.superagi.com/crm/contacts`
2. Click **Add Contact** button (top-right)
3. The Add Contact form opens
4. Enter **First Name** and **Last Name** (required)
5. Fill in Email, Phone Number, and other fields as needed
6. For **Current Company**: type the company name — if it does not exist, click **Add** to create and select it; if it exists, select from the dropdown
7. Scroll down to fill in Address, City, State, Country, Zipcode, Current Role
8. Verify **Owner** is correct or select from dropdown
9. Select **Contact Status** from dropdown (e.g., New)
10. Add **Tags** by typing a name and pressing Enter (new) or selecting from dropdown (existing)
11. Add **Lists** by selecting an existing list or clicking **Create New List** → enter name → **Create List**
12. Click **Add Contact** — contact is created and you are redirected to the contact details page

### Workflow: Edit a Contact

1. Navigate to `https://sales.superagi.com/crm/contacts`
2. Locate the contact row in the table
3. Click the **⋮** menu on the right of the row
4. Click **Edit** — the Edit Contact drawer opens with all existing values pre-filled
5. Update any fields as needed (same fields as the Add form)
6. Click **Update** — changes are saved and the updated contact appears in the listing

### Workflow: Delete a Contact

1. Navigate to `https://sales.superagi.com/crm/contacts`
2. Locate the contact row in the table
3. Click the **⋮** menu on the right of the row
4. Click **Delete**
5. A confirmation pop-up appears with **Cancel** and **Delete** buttons
6. Click **Delete** — the contact is permanently removed
7. Refresh the page to confirm the deleted contact is no longer visible

### Workflow: Search Contacts

1. Navigate to `https://sales.superagi.com/crm/contacts`
2. Click the **Search bar** at the top
3. Type a First Name, Last Name, or Email — matching contacts appear as you type
4. Search does **not** work for Phone Number, Company, or other fields — only First Name, Last Name, and Email are searchable

---

## 2. Leads

**URL:** `https://sales.superagi.com/crm/leads`

### Page Layout

- **Search bar** — visible at the top; searches by First Name, Last Name, and Email only
- **Add Lead** button (top-right) — opens the Add Lead form
- **Leads table** — all lead records in rows; each row has a **⋮ (three-dot)** menu on hover

### Add Lead Form — All Fields

| Field | Required | Notes |
|-------|----------|-------|
| **First Name** | Yes | Free text, e.g., `"Rahul"` |
| **Last Name** | Yes | Free text, e.g., `"Sharma"` |
| **Email** | No | e.g., `"rahul.sharma@gmail.com"` |
| **Phone Number** | No | e.g., `"9876543210"` |
| **Company** | No | Dropdown — type name and click **Add** if new; select from dropdown if existing |
| **Address** | No | Street address |
| **City** | No | e.g., `"Bangalore"` |
| **State** | No | e.g., `"Karnataka"` |
| **Country** | No | Dropdown |
| **Zipcode** | No | e.g., `"560025"` |
| **Current Role** | No | Job title |
| **Owner** | No | Dropdown — pre-filled with logged-in user |
| **Lead Status** | No | Dropdown — options include: **New**, **Contacted**, **Qualified** |
| **LinkedIn URL** | No | e.g., `"https://linkedin.com/in/rahul-sharma"` |
| **Description** | No | Free text |
| **Tags** | No | Type and press Enter to create; select from dropdown if existing |
| **Lists** | No | Select existing list or click **Create New List** → enter name → **Create List** |

**Submit button:** **Add Lead** (bottom of form)

### Workflow: Create a Lead

1. Navigate to `https://sales.superagi.com/crm/leads`
2. Click **Add Lead** button (top-right)
3. The Add Lead form opens
4. Enter **First Name** and **Last Name** (required)
5. Fill in Email, Phone Number, Company, and other fields as needed
6. For **Company**: type the company name — click **Add** if it doesn't exist; select from dropdown if it does
7. Scroll down to fill in Address, City, State, Country, Zipcode, Current Role
8. Select **Lead Status** from dropdown (e.g., New)
9. Add **Tags** and **Lists** as needed
10. Click **Add Lead** — lead is created and you are redirected to the lead details page

### Workflow: Edit a Lead

1. Navigate to `https://sales.superagi.com/crm/leads`
2. Locate the lead row in the table
3. Click the **⋮** menu on the right of the row
4. Click **Edit** — the Edit Lead drawer opens with all existing values pre-filled
5. Update any fields as needed
6. Click **Update** — changes are saved

### Workflow: Delete a Lead

1. Navigate to `https://sales.superagi.com/crm/leads`
2. Locate the lead row in the table
3. Click the **⋮** menu → Click **Delete**
4. Confirmation pop-up appears — click **Delete**
5. Lead is permanently removed

### Workflow: Search Leads

1. Navigate to `https://sales.superagi.com/crm/leads`
2. Click the **Search bar** at the top
3. Type a First Name, Last Name, or Email
4. Search does **not** work for Company, Phone Number, or other fields

---

## 3. Companies

**URL:** `https://sales.superagi.com/crm/companies`

### Page Layout

- **Search bar** — visible at the top; searches by Company Name only
- **Add Company** button (top-right) — opens the Add Company form
- **Companies table** — all company records in rows; each row has a **⋮ (three-dot)** menu on hover

### Add Company Form — All Fields

| Field | Required | Notes |
|-------|----------|-------|
| **Name** | Yes | Company name, e.g., `"ABC Pvt Ltd"` |
| **Owner** | No | Dropdown — pre-filled with logged-in user |
| **Industry** | No | Dropdown — e.g., Accounting, Agriculture |
| **Country** | No | Dropdown — e.g., India |
| **Website** | No | e.g., `"https://abc.com"` |
| **Description** | No | Free text, e.g., `"Leading software company"` |
| **LinkedIn URL** | No | e.g., `"https://linkedin.com/company/abc"` |
| **Company Size** | No | Dropdown — e.g., `"51-200 employees"` |
| **Annual Revenue** | No | Numeric, e.g., `"5000000"` |
| **City** | No | e.g., `"Bangalore"` |
| **State** | No | e.g., `"Karnataka"` |
| **Zipcode** | No | e.g., `"560001"` |
| **Tags** | No | Type and press Enter to create; select from dropdown if existing |
| **Lists** | No | Select existing list or click **Create New List** → enter name → **Create List** |

**Submit button:** **Add Company** (bottom of form)

### Workflow: Create a Company

1. Navigate to `https://sales.superagi.com/crm/companies`
2. Click **Add Company** button (top-right)
3. The Add Company form opens
4. Enter **Name** (required)
5. Select **Owner** (pre-filled with logged-in user), **Industry**, **Country**
6. Fill in Website, Description, LinkedIn URL, Company Size, Annual Revenue
7. Fill in City, State, Zipcode
8. Add **Tags** and **Lists** as needed
9. Click **Add Company** — company is created and you are redirected to the company details page

### Workflow: Edit a Company

1. Navigate to `https://sales.superagi.com/crm/companies`
2. Locate the company row in the table
3. Click the **⋮** menu → Click **Edit** — the Edit Company drawer opens with all values pre-filled
4. Update any fields as needed
5. Click **Update** — changes are saved

### Workflow: Delete a Company

1. Navigate to `https://sales.superagi.com/crm/companies`
2. Locate the company row in the table
3. Click the **⋮** menu → Click **Delete**
4. Confirmation pop-up appears — click **Delete**
5. Company is permanently removed

### Workflow: Search Companies

1. Navigate to `https://sales.superagi.com/crm/companies`
2. Click the **Search bar** at the top
3. Type a company **Name** — matching companies appear as you type
4. Search works **only for Name** — Website, City, Industry, and other fields are not searchable

---

## 4. Deals

**URL:** `https://sales.superagi.com/crm/deals`

### Page Layout

- **Search bar** — visible at the top; searches by Deal Title only
- **Add Deal** button (top-right) — opens the Add Deal form
- **Deals table** — all deal records in rows; each row has a **⋮ (three-dot)** menu on hover

### Add Deal Form — All Fields

| Field | Required | Notes |
|-------|----------|-------|
| **Title** | Yes | Deal name, e.g., `"Website Development Deal"` |
| **Expected Close Date** | No | Date picker, e.g., `"30 March 2026"` |
| **Deal Owner** | No | Dropdown — pre-filled with logged-in user |
| **Amount** | No | Numeric, e.g., `"150000"` |
| **Priority** | No | Dropdown — **High**, **Medium**, **Low** |
| **Deal Type** | No | Dropdown — **New**, **Existing** |
| **Description** | No | Free text |
| **Pipeline** | **Yes** | Dropdown — mandatory. e.g., `"Sales Pipeline"` |
| **Pipeline Stage** | No | Dropdown — options depend on selected Pipeline (e.g., Qualification, Proposal, Negotiation) |
| **Tags** | No | Type and press Enter to create; select from dropdown if existing |
| **Associated Company** | No | Dropdown — search and select an existing company |
| **Associated Contact** | No | Dropdown — search and select an existing contact |
| **Associated Lead** | No | Dropdown — search and select an existing lead |

**Submit button:** **Add Deal** (bottom of form)

### Workflow: Create a Deal

1. Navigate to `https://sales.superagi.com/crm/deals`
2. Click **Add Deal** button (top-right)
3. The Add Deal form opens
4. Enter **Title** (required)
5. Set Expected Close Date, Deal Owner, Amount, Priority, Deal Type, Description
6. Select **Pipeline** (mandatory — must be selected before Pipeline Stage becomes available)
7. Scroll down and select **Pipeline Stage** based on the selected pipeline
8. Add **Tags**, **Associated Company**, **Associated Contact**, **Associated Lead** as needed
9. Click **Add Deal** — deal is created and you are redirected to the deal details page

### Workflow: Edit a Deal

1. Navigate to `https://sales.superagi.com/crm/deals`
2. Locate the deal row in the table
3. Click the **⋮** menu → Click **Edit** — the Edit Deal drawer opens with all values pre-filled
4. Update any fields as needed (Pipeline Stage options change if you change Pipeline)
5. Click **Update** — changes are saved

### Workflow: Delete a Deal

1. Navigate to `https://sales.superagi.com/crm/deals`
2. Locate the deal row in the table
3. Click the **⋮** menu → Click **Delete**
4. Confirmation pop-up appears — click **Delete**
5. Deal is permanently removed

### Workflow: Search Deals

1. Navigate to `https://sales.superagi.com/crm/deals`
2. Click the **Search bar** at the top
3. Type a deal **Title** — matching deals appear as you type
4. Search works **only for Title** — Amount, Company, and other fields are not searchable

---

## Related Skills

| Skill | Relationship |
|-------|-------------|
| `crm-lists` | Records can be added to Lists from the add form (Lists field) or via bulk actions. Use `crm-lists` to create and manage those lists. |
| `crm-tasks` | CRM Tasks can be associated with any Contact, Lead, Company, or Deal. Navigate to `crm-tasks` to create or view tasks linked to a record. |
| `crm` | CLI-based skill for the same record types — use for bulk operations, scripting, or API-level access to leads, contacts, companies, deals. |
| `prospect` | Prospects found via Prospect Leads/Companies are saved into CRM as Leads or Companies using "Add to Leads" / "Add to Companies". |
| `sequences` | Leads and Contacts can be added to outreach Sequences directly from the record list or from bulk actions inside a List. |
| `cold-outreach-find-new-leads` | Cold Outreach campaigns target CRM entity types (leads, contacts). Enriched prospects land in CRM as Lead records. |
| `workflows` | Workflow nodes (Create Entity, Update Entity) create and update these CRM record types automatically. |

---

## Common Patterns Across All Four Modules

| Action | How |
|--------|-----|
| **Open add form** | Click the **Add [Record]** button (top-right of the listing page) |
| **Edit a record** | Hover the row → click **⋮** menu → click **Edit** |
| **Delete a record** | Hover the row → click **⋮** menu → click **Delete** → confirm in pop-up |
| **Search** | Click the Search bar at the top; each module only searches specific fields (see per-module notes) |
| **Create new company inline** | In Contact/Lead forms, type company name in the Company field and click **Add** |
| **Create new list inline** | In any form's Lists field, click **Create New List** → enter name → **Create List** |
| **Create new tag inline** | In any form's Tags field, type a tag name and press **Enter** |

---

## Key Gotchas from the UI

1. **Pipeline is mandatory for Deals** — the Add Deal form requires a Pipeline to be selected. Pipeline Stage is dependent on which Pipeline you select — you must select Pipeline first, then Pipeline Stage options populate.

2. **Company field in Contacts/Leads creates on the fly** — if the company you type does not exist in CRM, you must click the **Add** button that appears next to the typed name. Simply typing and moving on will NOT create the company — you must click Add.

3. **Tags require pressing Enter** — typing a new tag name and clicking elsewhere does NOT save the tag. You must press **Enter** after typing a new tag name to create and add it.

4. **Lists field: "Create New List" is separate from "select existing"** — if no list exists yet, click **Create New List** inside the dropdown. If a list already exists, scroll and click it in the dropdown. These are two separate actions.

5. **⋮ menu only appears on hover** — the three-dot row action menu is not permanently visible. You must hover over the row first to see it.

6. **Delete confirmation is required** — all four modules show a confirmation pop-up with **Cancel** and **Delete** buttons before permanently deleting a record. You must click **Delete** in the pop-up, not just the initial menu option.

7. **Search scope is narrow per module:**
   - Contacts: First Name, Last Name, Email only
   - Leads: First Name, Last Name, Email only
   - Companies: Name only
   - Deals: Title only
   Searching by phone number, company name (on lead/contact), amount, or industry will return no results.

8. **Owner pre-fills with logged-in user** — all four modules pre-fill the Owner field with the currently logged-in user. Change it explicitly if assigning to someone else.

9. **Edit drawer shows "Update" not "Save"** — the submit button in all edit forms is labeled **Update**, not "Save" or "Submit".

10. **After create, you are redirected to detail page** — clicking Add Contact / Add Lead / Add Company / Add Deal navigates you to the newly created record's detail page, not back to the listing. Use the **← Back** button to return to the listing.

11. **Contact Status vs Lead Status** — Contacts use **Contact Status** while Leads use **Lead Status**. The field names are different; do not confuse them.

12. **Deal Type options are exactly two** — **New** and **Existing**. There are no other options.

13. **Annual Revenue for Companies is numeric** — enter a plain number (e.g., `5000000`), not a formatted string. Formatting may be applied by the UI after entry.
