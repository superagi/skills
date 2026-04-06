---
name: marketing-email-campaign
description: Create and launch Email marketing campaigns in SuperAGI — covers app installation, campaign creation, recipient selection, content types (Drag-N-Drop, Plain Text, Custom HTML), personalization, and launch options
platform: [linux, macos]
---

# SuperAGI Marketing — Email Campaign

Email Campaigns allow users to send bulk emails to selected recipient lists with customizable content using templates, plain text, or HTML.

**Sidebar path:** Marketing → Campaign  
**URL:** `https://sales.superagi.com/marketing/campaigns`

## Related Skills

| Skill | Relationship |
|-------|-------------|
| `crm/lists.md` | Recipient lists for email campaigns are CRM Lists. Use `crm/lists.md` to create and manage the contact/lead lists used as campaign recipients. |
| `crm/records.md` | Individual contacts and leads in CRM are the recipients. Use `crm/records.md` to view or manage the records inside those lists. |
| `marketing/whatsapp-campaign.md` | Alternative bulk messaging channel in the same Marketing → Campaign module. Use this skill for email blasts; use `marketing/whatsapp-campaign.md` for WhatsApp blasts. |
| `cold-outreach/SKILL.md` | Alternative multi-step email outreach. Use `cold-outreach/SKILL.md` for AI-driven personalized sequences; use this skill for one-shot bulk email campaigns. |
| `sequences` | Sequences support multi-step drip email flows. Use this skill for bulk one-time blasts; use `sequences` for multi-step drip flows. |
| `workflows` | The Email workflow node and Marketing Email node can send emails as part of automations. Use `workflows` to trigger emails based on CRM events instead of manual campaign launches. |
| `settings` | Sender email accounts (`/settings#email_campaign_settings`) and sender domains must be verified in Settings before they appear in the Sender Email Account dropdown. |
| `ai-analytics` | Email campaign metrics (open rates, click rates, reply rates) are available as analytics data sources in AI Analytics dashboards. |

---

## Step 1 — Install Campaign App

Before creating an Email campaign, the Campaign app must be installed.

1. Log in to SuperAGI — you are redirected to the Dashboard
2. In the left sidebar, scroll down to the bottom and click **"Add Apps"**
3. You are redirected to the **Apps Store**
4. Scroll to the **Marketing** section
5. Locate **Campaign**
6. If the button shows **"Install"** — click it to install
7. If the button shows **"Open"** — it is already installed, skip
8. Click **"Back to SuperAGI"** (top of Apps Store page) to return to the Dashboard

---

## Step 2 — Navigate to Campaign Module

1. From the Dashboard, look at the left sidebar
2. Click **Marketing**
3. Click **Campaign**
4. You land on the **Campaign Listing Page** (`/marketing/campaigns`) showing Sent and Draft campaigns

---

## Step 3 — Create a New Campaign

1. On the Campaign Listing Page, click **"Create Campaign"** (top-right corner)
2. You are redirected to the **Select a Campaign Channel** page

---

## Step 4 — Select Email Channel

Three channel options are displayed:
- **Email** (1st option)
- SMS
- WhatsApp

1. Click **Email**
2. Click **"Create Campaign"**
3. You are redirected to the Email Campaign Configuration page

---

## Step 5 — Configure the Campaign (Left Section)

### Recipients

1. Under **Recipients**, click the input box
2. Type a list name to search (e.g., `"temp_list"`)
3. Select the matching list from the dropdown suggestions

> Only existing CRM Lists appear in the dropdown. Create the list first via `crm/lists.md` if it does not exist.

### Subject Line

1. Under the **Email Message** section, enter the subject line in the **Subject** field

#### Add Personalization to Subject

1. Click the **Personalization** button next to the subject field
2. Select a variable from the dropdown (e.g., **First Name**)
3. The variable token is inserted into the subject line (e.g., `{{contact.firstname}}`)

### Preview Text (Optional)

- Enter preview text in the **Preview Text** field
- This is the snippet shown below the subject line in email clients

### Sender Details

**Sender Name:**
- Enter the sender name that recipients will see

**Sender Email Account:**
1. Click the **"Select Email"** dropdown
2. Choose a registered sender email from the list

> Only email accounts verified in Settings → Email Campaign Settings (`/settings#email_campaign_settings`) appear here.

**Reply-To:**
- If the reply-to address is the same as the sender: check **"Use sender email as reply-to address"**
- If different: enter the reply-to email address in the input field

---

## Step 6 — Choose Content Type (Right Section)

Three content types are available — only one can be used per campaign:

### Option A: Drag-N-Drop Editor

1. Click **Drag-N-Drop Editor**
2. A template picker appears:
   - Select an **existing template** to use as a base, OR
   - Click **"Build from Scratch"** to start with a blank canvas
3. The drag-and-drop editor opens with an element palette on the left

**Available elements:**
| Element | Description |
|---------|-------------|
| Columns | Multi-column layout containers |
| Button | Clickable CTA button |
| Divider | Horizontal separator line |
| Heading | Section heading text |
| Paragraph | Body text block |
| Image | Image upload or URL |
| Video | Embedded video |
| Social | Social media icon links |
| Menu | Navigation menu |
| HTML | Raw HTML block |
| Table | Data table |
| Timer | Countdown timer |

**To add an element:**
1. Drag the element from the palette onto the canvas
2. Click the element on the canvas to select it
3. Configure it in the right panel (e.g., upload image, enter text, set link URL)
4. Repeat for additional elements

4. When done, click **"Save & Continue"**

### Option B: Plain Text

1. Click **Plain Text**
2. Enter content in the plain text editor
3. Add personalization tokens if needed (click Personalization button)
4. Click **"Save & Continue"**

### Option C: Custom HTML

1. Click **Custom HTML**
2. Write or paste your HTML code in the editor
3. A live preview renders on the right side of the editor
4. Add personalization tokens if needed
5. Click **"Save & Continue"**

> **"Save & Continue" is mandatory** before the Launch Campaign button becomes active. Do not skip this step.

---

## Step 7 — Launch Campaign

1. Click **"Launch Campaign"** (top-right corner)
2. A popup appears with two sending options:

### Option 1: Send Now

1. Select **Send Now**
2. Click **"Send Campaign"**
3. The campaign sends immediately

### Option 2: Schedule

1. Select **Schedule**
2. Choose the **date**, **time**, and **timezone** for delivery
3. Click **"Schedule Campaign"**
4. The campaign is queued and sends at the specified time

> The campaign is **NOT sent** when you click "Launch Campaign" — it is only sent after you click **"Send Campaign"** or **"Schedule Campaign"** in the popup.

---

## End-to-End Workflow Summary

```
1. INSTALL     → Apps Store → Install Campaign app
2. NAVIGATE    → Dashboard → Marketing → Campaign
3. CREATE      → Click "Create Campaign" → Select Email channel
4. RECIPIENTS  → Select CRM list from dropdown
5. SUBJECT     → Enter subject line → add personalization if needed
6. SENDER      → Set sender name + email + reply-to
7. CONTENT     → Choose Drag-N-Drop / Plain Text / Custom HTML → build content
8. SAVE        → Click "Save & Continue" (mandatory)
9. LAUNCH      → Click "Launch Campaign" → Send Now or Schedule → confirm
```

---

## Key Gotchas

1. **Install vs Open button:** "Install" means the app is not yet installed; "Open" means it is already installed. Do not click "Install" on an already-installed app.

2. **Recipient list must exist first:** The recipient dropdown only shows existing CRM Lists. If the list is not there, navigate to `crm/lists.md` to create it before returning here.

3. **Only verified sender emails appear:** The Sender Email Account dropdown is empty if no sender email has been verified in Settings → Email Campaign Settings. Verify the sender domain and email first.

4. **Only one content type per campaign:** You cannot mix Drag-N-Drop, Plain Text, and Custom HTML in the same campaign. Choose one type and stick with it.

5. **"Save & Continue" is mandatory:** Clicking "Launch Campaign" without first clicking "Save & Continue" in the content editor will not proceed — the campaign content must be saved first.

6. **Campaign is not sent until final confirmation:** Clicking "Launch Campaign" only opens the send options popup. The actual send happens only after selecting Send Now or Schedule and clicking the confirmation button.

7. **Schedule requires timezone selection:** When scheduling, always select the correct timezone. An incorrect timezone will deliver the campaign at the wrong time.

8. **Personalization works in subject and content:** The Personalization button is available in both the subject line field and within the content editors. Use it in both places for fully personalized campaigns.

9. **"Back to SuperAGI" after app install:** After installing apps in the Apps Store, use the "Back to SuperAGI" button at the top — do not use the browser back button.

10. **Preview text is optional but recommended:** Preview text is shown as the email snippet in recipients' inboxes. Leaving it blank may result in the email client pulling random text from the email body as the preview.
