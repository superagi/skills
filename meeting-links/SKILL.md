---
name: meeting-links
description: Create and manage meeting agents, handle booking flows, view meeting logs, and use AI notetaker features in SuperAGI Sales Meeting Links
platform: [linux, macos]
---

# SuperAGI Sales — Meeting Links

Meeting Links is how you create shareable booking pages (called "Meeting Agents") that let external people schedule meetings with you or your team. Each agent has its own public URL. Once a meeting is booked, it appears in Meeting Logs where you can view recordings, AI summaries, transcripts, and manage meeting details. This is the scheduling and meeting management hub of SuperAGI Sales.

## Sidebar Navigation

In the left sidebar, scroll down and click **"Meeting Links"** to expand it. Two sub-sections appear:
- **Meeting Agents** — `https://sales.superagi.com/meeting_agent`
- **Meeting Logs** — `https://sales.superagi.com/meeting_log`

## Related Skills

| Skill | Relationship |
|-------|-------------|
| `crm/records.md` | Meeting Logs Associations panel links meetings to Contacts, Leads, Companies, and Deals. Use `crm/records.md` to view or manage those records. |
| `crm/tasks.md` | AI Notetaker auto-creates Tasks from meeting content — visible in the Tasks tab on the meeting detail page. Use `crm/tasks.md` to action those tasks. |
| `workflows` | Meeting bookings and calendar events can trigger workflow automations. Use `workflows` to automate follow-up actions after a meeting is booked or completed. |
| `sequences` | After a meeting, leads can be enrolled into follow-up outreach sequences. Use `sequences` to build those flows. |
| `cold-outreach` | Meeting Agent booking links can be used as CTA links in Cold Outreach campaign emails. Use `cold-outreach` to configure CTA links in campaign step content. |

---

## 1. Meeting Agents

**URL:** `https://sales.superagi.com/meeting_agent`  
**Purpose:** Create and manage meeting booking agents — each agent generates a public booking page with a unique URL that external people can use to schedule meetings with you.

### Pre-Condition: Calendar Must Be Connected

Before any Meeting Agents functionality is available, a calendar must be connected. If no calendar is connected, the page shows an empty state screen with:
- A calendar icon in the center
- Heading: **"Connect Your Calendar"**
- Message: *"Please connect your google or outlook calendar to create & manage your calendar within SuperAGI"*
- Button: **"Connect Your Google Calendar"** (black button with Google icon)
- Button: **"Connect Your Outlook Calendar"** (black button with Outlook icon)
- No agent list or "Create Agent" button is visible

**To connect Google Calendar:**
1. Click the **"Connect Your Google Calendar"** button
2. A Google OAuth popup opens in the browser
3. Complete the Google authorization and grant required permissions
4. Return to the Meeting Agents page — the list view now loads

**To connect Outlook Calendar:**
1. Click the **"Connect Your Outlook Calendar"** button
2. A Microsoft OAuth popup opens
3. Complete Microsoft authorization and grant required permissions
4. Return to the Meeting Agents page — the list view now loads

---

### Page Layout (After Calendar Connected)

Once a calendar is connected, the Meeting Agents page shows:

**Top bar:**
- **Search bar** on the left — placeholder text: `"Search agents"` — filters the agent list in real time as you type
- **"Create Agent"** button on the top right (black button)

**Agent list table** with 5 columns:

| Column | Description |
|--------|-------------|
| **Agent Name** | Name of the meeting agent (bold text) |
| **Type** | Meeting type — e.g., "One-on-One" or "Round Robin" |
| **Participants** | Host name (e.g., "Raju k") |
| **Duration** | Meeting duration — e.g., "15min", "30min" |
| **Booking** | Number of bookings made via this agent (numeric count) |

**Per-row action icons** (appear on the right side of each row, 4 icons + 1 menu):
- **Preview icon** (external link icon) — opens the public booking page in a new tab
- **Embed code icon** (`<>` brackets icon) — shows the embed snippet/code for this agent
- **Copy link icon** (clipboard icon) — copies the booking URL to clipboard
- **Three-dot menu (`...`)** — reveals two options:
  - **Edit** — opens the agent creation panel pre-populated with existing data
  - **Delete** — removes the agent permanently

**Pagination** (bottom of page):
- Left arrow `<` and right arrow `>` for page navigation
- Page number displayed (e.g., "1")
- Pagination dropdown on the right showing **"20 per page"** by default — click to change to **50 per page** or **100 per page**

---

### Workflow: Search Agents

1. Navigate to `https://sales.superagi.com/meeting_agent`
2. Click the **"Search agents"** input bar at the top
3. Type the agent name — the list filters in real time showing only matching agents
4. To clear, delete the text from the input — the full list reappears
5. If no agent matches, the list shows empty / no results

---

### Workflow: Create a One-on-One Meeting Agent

**Step 1 — Open the Create Agent modal:**
1. Navigate to `https://sales.superagi.com/meeting_agent`
2. Click the **"Create Agent"** button (top right, black button)
3. A modal dialog appears titled **"Choose a meeting agent type"** with two options:
   - **One-on-One** — *"Create a personal meeting agent for individual scheduling"* (person icon) — selected by default with a checkmark
   - **Round Robin** — *"Create a team-based meeting agent that rotates between team members"* (rotation icon)
4. Click **"One-on-One"** to select it (a checkmark appears on the option)
5. Click the **"Continue"** button (black button, bottom right of modal)

**Step 2 — Fill in the Create New Meeting Agent panel:**

A right-side panel slides in titled **"Create New Meeting Agent"** with subtitle **"One-on-One"**. There is an **X** button at the top right to close the panel without saving.

Fill in the following fields by scrolling down the panel:

**Agent Name (required):**
- Click the **"Enter Name"** text input field
- Type the agent name (maximum 50 characters — counter shows `"0/50 characters"` updating as you type)
- If left empty and you try to create, validation triggers

**Available durations:**
- A dropdown showing **"30min"** by default
- Click the dropdown to see all options: 15min, 30min, 45min, 60min, 90min, 120min, 150min, 180min
- Click the desired duration to select it

**Allow booker to select duration:**
- A toggle switch (off by default)
- Click to toggle ON — allows the person booking to choose their preferred duration

**Select Theme:**
- A dropdown showing **"Light"** by default
- Click the dropdown to see theme options (e.g., Light, Dark)

**Custom brand color:**
- A checkbox (unchecked by default)
- Click to check — reveals a color picker to set a custom brand color

**Availability (scroll down to see this section):**
- Shows days of the week with checkboxes and time range dropdowns
- **Default state:** Monday to Friday are checked (enabled) with 9:00am – 5:00pm
- Sunday and Saturday are unchecked — shows "Not available"
- For each enabled day:
  - **Start time dropdown** (e.g., "9:00am") — click to change
  - **End time dropdown** (e.g., "5:00pm") — click to change
  - **X button** — removes that time slot for that day
  - **+ button** — adds an additional time slot for that day
- To enable a day: click its checkbox
- To disable a day: uncheck its checkbox — it reverts to "Not available"

**Timezone:**
- Shows current timezone (e.g., "Asia/Kolkata") — auto-detected
- Click to change if needed

**Description (scroll down):**
- A rich text editor with formatting toolbar: **B** (Bold), *I* (Italic), **U** (Underline), ordered list, unordered list
- Maximum 400 characters — counter shows `"0/400 characters"` at the bottom

**Location:**
- A dropdown showing **"Google Meet"** by default with Google Meet icon
- Click the dropdown to see all options:
  - **Google Meet** (Google Meet icon)
  - **Zoom** (Zoom icon)
  - **MS Teams** (Teams icon)
  - **Super Meet** (SuperAGI icon)

**Advanced Settings (scroll down):**
- Click **"Advanced Settings"** to expand the section (accordion/collapsible)
- Three toggle switches appear:
  - **Limit future bookings** — *"Limit how far in the future this event can be booked"*
  - **Buffer time** — *"Add time before and after booked meeting"*
  - **Minimum notice** — *"Set the minimum amount of notice that is required"*

**Step 3 — Create the agent:**
1. After filling all required fields, scroll down to the bottom of the panel
2. Click the **"Create Agent"** button (black button, bottom right of panel)
3. The panel closes and the new agent appears in the agents list table

**To close without saving:**
- Click the **X** button at the top right of the panel — no changes are saved

---

### Workflow: Create a Round Robin Meeting Agent

**Step 1 — Open the Create Agent modal:**
1. Navigate to `https://sales.superagi.com/meeting_agent`
2. Click the **"Create Agent"** button (top right)
3. Modal appears — click **"Round Robin"** option to select it
4. Click **"Continue"**

**Step 2 — Fill in the Round Robin panel:**

The right-side panel slides in titled **"Create New Meeting Agent"** with subtitle **"Round Robin"**.

Round Robin has all the same fields as One-on-One PLUS these additional fields:

**Select Team (Round Robin exclusive):**
- A dropdown showing placeholder `"Select team"`
- Click to open the dropdown and select a team
- The team determines which members are available for rotation

**Distribution (Round Robin exclusive):**
- A dropdown showing **"Flexible"** by default
- Click to change distribution method

**Set Weight (Round Robin exclusive):**
- A toggle switch (off by default)
- Click to toggle ON — allows setting weight/priority for team member rotation

> Round Robin does NOT have individual team member email entry in the panel — team members are managed via the "Select Team" dropdown.

**Step 3 — Create the agent:**
1. Fill all required fields (Agent Name is mandatory)
2. Click **"Create Agent"** button at the bottom right
3. Agent appears in the list — bookings rotate between team members

---

### Workflow: Edit an Existing Agent

1. Navigate to `https://sales.superagi.com/meeting_agent`
2. Find the agent row in the list
3. Click the **three-dot menu (`...`)** on the right side of that row
4. A small dropdown appears with **"Edit"** and **"Delete"** options
5. Click **"Edit"**
6. The same creation panel opens — now pre-populated with existing agent data
7. Make the required changes
8. Click **"Create Agent"** button at the bottom to save changes

---

### Workflow: Delete an Agent

1. Navigate to `https://sales.superagi.com/meeting_agent`
2. Find the agent row in the list
3. Click the **three-dot menu (`...`)** on the right side of that row
4. Click **"Delete"**
5. The agent is removed from the list permanently
6. Note: Meeting log entries for this agent are NOT deleted — they remain in Meeting Logs

---

### Workflow: Preview Booking Page

1. Navigate to `https://sales.superagi.com/meeting_agent`
2. Find the agent row
3. Click the **preview icon** (external link icon — first icon in the row actions)
4. The public booking page opens in a new browser tab at URL format: `meetings.superagi.com/{agent-slug}`

---

### Workflow: Get Embed Code

1. Navigate to `https://sales.superagi.com/meeting_agent`
2. Find the agent row
3. Click the **embed code icon** (`<>` brackets — second icon in the row actions)
4. A popup appears showing the HTML embed snippet for this agent
5. Copy the code to embed the booking page on an external website

---

### Workflow: Copy Booking Link

1. Navigate to `https://sales.superagi.com/meeting_agent`
2. Find the agent row
3. Click the **copy link icon** (clipboard — third icon in the row actions)
4. The booking URL is copied to clipboard silently

---

## 2. Booking Flow (External Booking Page)

**URL format:** `https://meetings.superagi.com/{agent-slug}` (e.g., `meetings.superagi.com/Raju-k/30min-20`)  
**Purpose:** This is the public-facing page that external people (bookers) use to schedule a meeting. No login required to access this page.

### Page Layout — Step 1: Select Date & Time

The booking page has two sections side by side:

**Left panel (agent info):**
- Host avatar/initials (circle with initials)
- Host organization name (above agent name)
- Agent name (large, bold heading)
- **"Hosted by [Name]"** with a person icon
- **Meeting duration** (e.g., "30 min") with a clock icon

**Right panel (calendar):**
- Heading: **"Select Date & Time"**
- Month navigation: left arrow `<` and right arrow `>` to navigate months, current month/year displayed (e.g., "MAR 2026")
- Calendar grid showing SUN | MON | TUE | WED | THU | FRI | SAT
- **Past dates** are greyed out and not clickable
- **Available dates** are shown in black/dark text and are clickable
- **Today's date** is highlighted with a dark circle
- **Timezone selector** at the bottom — shows current timezone (e.g., "Asia/Kolkata, UTC +5:30") with a globe icon and dropdown arrow — click to change timezone

**Selecting a date:**
1. Click on an available (non-greyed) date in the calendar
2. The selected date highlights with a filled dark circle
3. A time slot panel appears on the right side showing available times for that day (e.g., "Friday, March 27")
4. Time slots appear as a scrollable list: 9:00am, 9:30am, 10:00am, 10:30am... (in intervals based on agent duration)
5. Scroll down within the time slot list to see more times
6. Click a time slot to select it — it highlights with a dark/black background
7. Once a time slot is selected, a **"Proceed to Next"** black button appears at the bottom of the time slot panel
8. Click **"Proceed to Next"** to go to Step 2

---

### Page Layout — Step 2: Provide Your Details

After clicking "Proceed to Next", the page transitions to the booking form:

**Left panel (booking summary):**
- Back arrow `<` with **"Back"** text — click to return to Step 1 (date/time selection)
- Host avatar/initials
- Organization name
- Agent name (large, bold)
- **"Hosted by [Name]"** with person icon
- **Selected date and time** (e.g., "Friday 27, March 2026, 3:30pm") with calendar icon
- **Duration** (e.g., "30 min") with clock icon
- **Timezone** (e.g., "Asia/Kolkata, UTC +5:30") with globe icon

**Right panel (booking form):**
- Heading: **"Provide your details"**
- **Your name\*** — required text input field
- **Email\*** — required text input field (must be valid email format)
- **"Add Guests"** button (with people icon) — click to add additional guest email addresses
- **Short note** — optional textarea for a message to the host
- **"Book Meeting"** button (black, full width) — submits the booking

**Validation:**
- If "Your name" is empty and "Book Meeting" is clicked — validation error shown on the name field
- If "Email" is empty and "Book Meeting" is clicked — validation error shown on the email field
- If email format is invalid (e.g., missing @) — validation error shown

**Booking costs 25 credits** — if insufficient credits, an error is shown and booking is blocked.

**After successful booking:**
- A confirmation page appears showing:
  - Meeting confirmation details (agent name, host, date, time, duration, timezone)
  - Option to **download .ics file** to add to local calendar
  - **"Add to Google Calendar"** button
  - **"Add to Outlook Calendar"** button
- A confirmation email is sent to the booker's email address

---

## 3. Reschedule & Cancel Flow

After a meeting is booked, the confirmation email contains reschedule and cancel links.

### Reschedule
1. Click the reschedule link in the confirmation email
2. Redirected to the booking page Step 1 (date/time selection) — same flow as initial booking
3. Select a new date and time
4. Proceed through to Step 2 and confirm
5. **No additional credits are charged** for rescheduling
6. The meeting log updates to reflect the new time

### Cancel
1. Click the cancel link in the confirmation email
2. Redirected to a **"Meeting Cancelled"** page confirming cancellation
3. **No credit refund** is issued for cancelled meetings
4. The meeting moves to the **"Cancelled"** tab in Meeting Logs
5. The Booking count for the agent does NOT change after cancellation

---

## 4. Meeting Logs

**URL:** `https://sales.superagi.com/meeting_log`  
**Purpose:** View all meetings — both those booked via Meeting Agents and calendar events synced from Google/Outlook. Manage recordings, AI summaries, dispositions, tags, and associations.

### Page Layout

**Top tabs (meeting status filter):**
- **All meetings** (default tab, shows all meetings regardless of status) — click the `...` next to it to see more tab options
- **Cancelled** — shows only cancelled meetings
- Additional status tabs can be pinned

**Top right:**
- **Search bar** — placeholder: `"Search meeting logs"` — searches by meeting name
- **"Add Notetaker"** button (black button, top right) — manually add AI notetaker to any meeting

**Filter bar** (below tabs):
- **"+ Filters"** button — click to open the filter property selector
- **"Reset"** button (appears when filters are active) — clears all active filters
- Active filters appear as chips/pills next to the "+ Filters" button showing the filter name with a dropdown arrow

**Meeting list table** with columns:

| Column | Description |
|--------|-------------|
| **Meeting Name** | Name of the meeting (e.g., "Raju - Raju and Raju k") |
| **Source** | Where the meeting came from (e.g., "Google Meet", agent name like "Nothing_1") |
| **Type** | Meeting type — "Calendar Event" or "One-on-one" |
| **Location** | Platform icon + name (e.g., Google Meet icon + "Google Meet", MS Teams icon + "MS Teams") |
| **Status** | Meeting status — e.g., "Past", "Upcoming", "Cancelled" |
| **Disposition** | Sales disposition label (empty by default, set from detail page) |

**Pagination** (bottom):
- Page navigation arrows `<` `>`
- Page numbers (e.g., 1, 2, 3, 4)
- **"20 per page"** dropdown — click to change

---

### Workflow: Filter Meeting Logs

1. Navigate to `https://sales.superagi.com/meeting_log`
2. Click **"+ Filters"** button
3. A filter property dropdown panel appears on the left with a **"Search Property"** input at top
4. Available filter properties (scroll to see all):
   - **Date** — filter by date range
   - **Status** — filter by meeting status
   - **Meeting Agent** — filter by which agent the meeting was booked through
   - **Host Email** — filter by host's email address
   - **Tags** — filter by tags assigned to meetings
   - **Disposition** — filter by disposition label
   - **Meeting Link** — filter by meeting link
   - **AI Notetaker** — filter by AI notetaker presence
   - **Synced From Calendar** — filter by calendar sync source
5. Click a filter property to select it — the filter chip appears in the filter bar
6. Click the filter chip to open its value dropdown and select values:

   **Date filter options:** Today | This Week | This Month | All Time | Custom date range

   **Status filter options:** Upcoming | Cancelled | Past

   **Meeting Agent filter:** Opens a searchable dropdown — type to search, click to select an agent name

   **Host Email filter:** Opens a searchable dropdown showing available host emails — click to select

7. Multiple filters can be active simultaneously — they stack as chips in the filter bar
8. To remove a filter: click the filter chip and deselect, or click **"Reset"** to clear all filters

---

### Workflow: Search Meeting Logs

1. Navigate to `https://sales.superagi.com/meeting_log`
2. Click the **"Search meeting logs"** search bar (top right)
3. Type the meeting name or keyword
4. The list filters in real time

---

### Workflow: View Meeting Log Detail

1. Navigate to `https://sales.superagi.com/meeting_log`
2. Click on any meeting row in the list
3. Navigates to the meeting detail page at URL: `https://sales.superagi.com/meeting_log/{meeting_id}?source=meeting_log`

**Meeting Detail Page Layout:**

**Left panel (meeting info):**
- **Back** arrow — click to return to Meeting Logs list
- **Meeting name** (large heading, e.g., "Raju - Raju and Raju k")
- **Date and time** (e.g., "26 Mar 2026, 4:30pm - 5:00pm (Asia/Kolkata)")
- **"Generate AI Email"** button (with lightning bolt icon) — generates an AI-drafted email about this meeting
- **Source** — where the meeting came from (e.g., "Google Meet")
- **Location** — platform with icon + external link icon + copy icon
- **Attendees** — list of attendees with avatars
- **No. of Guests** — numeric count
- **Disposition** — dropdown showing "Select Disposition" — click to select a disposition label
- **Tags** — field showing "Select Tags" — click to add tags
- **Last Activity** — timestamp of last activity
- **Created Date** — timestamp of creation

**Center panel (tabs):**
- **Activity** tab (default) — shows activity timeline with filters: Activity type, Updated by, Updated date
- **Tasks** tab — shows auto-created tasks from AI analysis of the meeting
- **Recording** tab — shows meeting recording and transcript
- **Meeting Summary** tab — shows AI-generated meeting summary and outcome
- **Email** tab — shows email history related to this meeting

**Right panel (Associations):**
- **Associations** tab and **Comments** tab
- Under Associations:
  - **Contacts** — "+ Add" button to link contacts
  - **Leads** — "+ Add" button to link leads
  - **Companies** — "+ Add" button to link companies
  - **Deals** — "+ Add" button to link deals
  - **Customers** — "+ Add" button to link customers
  - **Forms** — linked forms

---

### Workflow: Recording Tab

1. Open a meeting detail page
2. Click the **"Recording"** tab in the center panel
3. The Recording section shows:
   - **Video player** — embedded video with play/pause, mute, fullscreen, settings controls and a timeline scrubber
   - **Talktime tab** — shows per-participant talktime percentage with a progress bar (e.g., "Sanskriti Sahu — 75.7% Talktime")
   - **Transcript tab** — click "Transcript" to switch from Talktime to the searchable transcript of the meeting

> Recording tab only shows content if an AI Notetaker was present in the meeting. If no notetaker was present, the tab shows an empty state.

---

### Workflow: Meeting Summary Tab

1. Open a meeting detail page
2. Click the **"Meeting Summary"** tab
3. Shows AI-generated summary of what was discussed in the meeting
4. If participants discussed any action items, the AI auto-creates tasks visible in the **Tasks** tab

---

### Workflow: Add Disposition to a Meeting

1. Open a meeting detail page
2. In the left panel, find the **"Disposition"** field showing "Select Disposition"
3. Click the "Select Disposition" dropdown
4. Select a disposition label from the options
5. The selection saves automatically

---

### Workflow: Add Tags to a Meeting

1. Open a meeting detail page
2. In the left panel, find the **"Tags"** field showing "Select Tags"
3. Click "Select Tags"
4. Type or select tags from the dropdown
5. Tags are saved automatically

---

### Workflow: Add Associations (Contacts/Leads/Companies/Deals)

1. Open a meeting detail page
2. In the right panel under **"Associations"** tab
3. Click **"+ Add"** next to the desired association type (Contacts, Leads, Companies, Deals, Customers, or Forms)
4. A search/select dialog opens — search and select the record to link
5. The association is saved and shown under that section

---

### Workflow: Generate AI Email

1. Open a meeting detail page
2. Click the **"Generate AI Email"** button (lightning bolt icon, top of left panel)
3. An AI-drafted email is generated based on the meeting content
4. Review and use the email from the Email tab

---

## 5. Add Notetaker (Manual)

The AI Notetaker can be manually added to any meeting from the Meeting Logs page.

### Workflow: Add Notetaker from Meeting Logs

1. Navigate to `https://sales.superagi.com/meeting_log`
2. Click the **"Add Notetaker"** button (black button, top right)
3. A modal dialog appears titled **"Add Notetaker to your meeting"** with an X button to close
4. Fill in the modal fields:

   **Platform** (required):
   - Click the **"Select platform"** dropdown
   - Options available: Google Meet, Zoom, MS Teams
   - Click to select the platform

   **Meeting URL** (required):
   - Click the **"Enter meeting URL"** text input
   - Paste or type the full meeting URL
   - If left empty and Add is clicked — validation error triggers
   - If invalid URL format — validation error triggers

5. Click **"Add"** button (black button, bottom right of modal) to submit
6. Click **"Cancel"** button to close the modal without adding

---

## End-to-End Flow

```
1. CONNECT CALENDAR  → Connect Google or Outlook calendar (one-time setup)
2. CREATE AGENT      → Create One-on-One or Round Robin meeting agent
3. SHARE LINK        → Copy booking URL or embed code and share with prospects
4. BOOKER SELECTS    → Booker opens public page → picks date/time → fills details → clicks Book Meeting
5. MEETING BOOKED    → 25 credits deducted, confirmation email sent, meeting appears in Meeting Logs
6. MEETING HAPPENS   → AI Notetaker auto-joins (if configured) and records
7. POST MEETING      → View Recording, Transcript, Talktime, AI Summary, Auto-Tasks in Meeting Logs
8. MANAGE            → Set Disposition, add Tags, link Contacts/Leads/Companies/Deals, generate AI Email
9. RESCHEDULE/CANCEL → Via links in confirmation email — no extra credits for reschedule, no refund for cancel
```

---

## Key Gotchas

1. **Calendar must be connected first:** No Meeting Agents functionality is available without a connected Google or Outlook calendar. Always check for the "Connect Your Calendar" screen first — if it appears, calendar connection is required before proceeding.

2. **Agent Name limit is 50 characters:** The name field shows a live counter (e.g., "0/50 characters"). Input will stop accepting characters at the limit.

3. **Description limit is 400 characters:** The description rich text editor has a 400-character limit shown as `"0/400 characters"` below the editor.

4. **Scroll down in the Create Agent panel:** The panel is long. After filling Agent Name and Available Durations at the top, you must scroll down to see: Availability days/times, Timezone, Description, Location, and Advanced Settings.

5. **Advanced Settings is collapsed by default:** Click the "Advanced Settings" accordion header to expand and see Limit future bookings, Buffer time, and Minimum notice toggles.

6. **Booking costs 25 credits:** Each meeting booking deducts 25 credits from the account. Round Robin bookings also cost 25 credits. If credits are insufficient, booking is blocked with an error.

7. **Rescheduling does not cost extra credits:** Credits are only charged on initial booking. Rescheduling and re-booking the same slot is free.

8. **Cancellation does not refund credits:** Once a meeting is cancelled, the 25 credits are not returned.

9. **Booking count does not change on cancellation:** The "Booking" column count in the agent list reflects total bookings made — it does not decrease when a meeting is cancelled.

10. **Past dates are not selectable on booking page:** The calendar on the public booking page greys out all past dates. Only present and future available dates can be clicked.

11. **Time slots appear only after selecting a date:** On the booking page Step 1, the time slot list is hidden until a date is clicked. After clicking a date, scroll within the time slot panel if needed to find the desired time.

12. **"Proceed to Next" appears only after selecting a time slot:** On the booking page, the "Proceed to Next" button only appears after both a date AND a time slot are selected.

13. **Row action icons vs three-dot menu:** There are 3 quick-action icons per row (Preview, Embed, Copy Link) and a separate three-dot menu (`...`) that contains Edit and Delete. They are different — do not confuse the copy icon with the three-dot menu.

14. **Meeting Logs tab default:** The default tab is "All meetings" which shows all meetings. To see only cancelled meetings, click the "Cancelled" tab. To filter by status (Upcoming/Past/Cancelled), use the "+ Filters" > Status filter.

15. **Recording tab is empty without AI Notetaker:** If no AI Notetaker joined the meeting, the Recording tab will show an empty state with no video, transcript, or talktime data.

16. **Meeting Log detail URL pattern:** Each meeting log has a unique ID in the URL: `https://sales.superagi.com/meeting_log/{id}?source=meeting_log`. Navigate back using the "Back" arrow in the detail page — do not use the browser back button.

17. **Filters in Meeting Logs persist as chips:** Once a filter is applied, it shows as a chip/pill in the filter bar. To remove it, click the chip and deselect, or click "Reset" to clear all active filters at once.

18. **Round Robin uses Select Team — not individual emails:** Unlike manual team member addition, Round Robin agents use the "Select Team" dropdown to assign a team. The rotation happens automatically across team members.

19. **Booking page is publicly accessible:** The meeting agent booking page (`meetings.superagi.com/...`) does not require the booker to log into SuperAGI — it is fully public and accessible to anyone with the link.

20. **Embed code renders on external pages:** The embed snippet obtained via the `<>` icon can be placed on any external website to render the booking calendar inline.
