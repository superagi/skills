---
name: ai-analytics
description: Create and manage AI Analytics spaces, dashboards, charts, and calculated fields in SuperAGI — covers space creation, dashboard types (AI-generated/manual/SQL), template library, chart builder with 12 chart types, and export
platform: [linux, macos]
---

# SuperAGI AI Analytics

AI Analytics is SuperAGI's reporting and visualization module. Users create **Spaces** to organize **Dashboards**, which contain charts built from CRM and sales data. Dashboards can be generated with AI, built manually via a chart builder, or created with SQL.

**Sidebar path:** Analytics  
**URL:** `https://sales.superagi.com/analytics`

## Related Skills

| Skill | Relationship |
|-------|-------------|
| `crm/records.md` | Analytics charts are built from CRM entity data (leads, contacts, companies, deals). Use `crm/records.md` to understand the fields and structure of the underlying data. |
| `crm/lists.md` | CRM lists can be used as data sources for analytics dashboards. Use `crm/lists.md` to understand list structure. |
| `crm/tasks.md` | Task data (call logs, meetings, notes) is available as an analytics data source. |
| `workflows` | Workflow execution events and metrics can be referenced in analytics dashboards. |
| `forms` | Form submission data can be analyzed via the SQL dashboard type. |

---

## Overview

The Analytics module is organized into three levels:

```
Analytics (sidebar)
  └── Spaces (containers for dashboards)
        └── Dashboards (collections of charts)
              └── Charts (individual visualizations)
```

**Page layout:** Left sidebar lists all Spaces. Clicking a Space reveals its Dashboards. The main panel shows the selected dashboard with its charts in a grid.

---

## Sidebar Navigation

- The left sidebar lists all **Spaces** the user has access to.
- Each Space expands to show its Dashboards.
- A **+ New Space** button at the top or bottom creates a new space.
- Hovering over a Space reveals action icons (edit, delete).

---

## Step 1 — Create a Space

A Space is a container for organizing related dashboards.

1. Click **+ New Space** in the left sidebar (or the create button on the Analytics landing page)
2. A modal appears with:
   - **Space Name** — text input (required)
   - **Visibility** — three options:
     - **Public** — visible to all users in the workspace
     - **Shared** — visible to specific users/teams you select
     - **Private** — visible only to you
3. Enter a name and select visibility
4. Click **Create** — the space appears in the left sidebar

### Space Visibility Rules

| Visibility | Who Can See |
|------------|------------|
| Public | All workspace members |
| Shared | Only explicitly invited members |
| Private | Only the creator |

---

## Step 2 — Space Actions

When hovering over a Space in the sidebar:

- **Edit icon** — opens a modal to rename the space or change visibility
- **Delete icon** — permanently deletes the space and ALL dashboards inside it

> Deleting a space is irreversible. All dashboards and charts inside are permanently removed.

---

## Step 3 — Create a Dashboard

1. Click on a Space in the sidebar to open it
2. Click **+ New Dashboard** (or **Create Dashboard** button on the space page)
3. A modal appears asking you to choose a dashboard type:
   - **Generate with AI** — AI creates a dashboard based on a text prompt
   - **Create manually** — blank canvas; add charts one by one using the chart builder
   - **Create with SQL** — write a SQL query to define the dataset; results shown as a table or chart
4. Enter a dashboard name
5. Select the type and click **Create**

---

## Dashboard Types

### Generate with AI
- User provides a natural language prompt (e.g., "Show me pipeline by stage for this quarter")
- AI generates multiple charts automatically and lays them out on the dashboard
- Charts can be individually edited or deleted after generation

### Create Manually
- Blank dashboard
- Click **+ Add Chart** to open the Chart Builder
- Build each chart individually by selecting object, metrics, grouping, and chart type

### Create with SQL
- Provides a SQL editor
- Write a query against the SuperAGI data schema
- Results are displayed as a table
- Can be converted to a chart type

---

## Dashboard Preview (Viewing)

When viewing a dashboard:
- Charts are displayed in a **grid layout**
- Each chart has a title, the visualization, and a three-dot **more_icon** menu
- The more_icon per chart provides: **Edit**, **Duplicate**, **Delete**, **Export as CSV**
- **Filter bar** at the top applies date range and dimension filters across all charts on the dashboard
- **Edit Dashboard** button (top-right) enables drag-and-drop repositioning and resizing of chart tiles

---

## Export Dashboard as CSV

To export chart data:

1. Hover over a chart tile on the dashboard
2. Click the three-dot **more_icon** on the chart
3. Select **Export as CSV**
4. A CSV file with the chart's underlying data downloads immediately

> Only individual chart data can be exported as CSV, not the full dashboard at once.

---

## Template Report Library

The Template Library provides 24 pre-built report templates organized into 5 categories.

**Access:** Click **+ Add Chart** → **From Template** (or a Template Library button on the dashboard)

### Template Categories

| Category | Templates |
|----------|-----------|
| **Sales Performance** | Pipeline by Stage, Revenue by Rep, Win Rate by Quarter, Deal Velocity, Quota Attainment |
| **Lead Management** | Lead Source Analysis, Lead Conversion Rate, Leads by Status, New Leads Over Time |
| **Activity Tracking** | Calls Logged, Emails Sent, Meetings Booked, Task Completion Rate |
| **Campaign Analytics** | Email Open Rate, Click-Through Rate, Reply Rate by Campaign, Leads Generated by Campaign |
| **CRM Overview** | Contact Growth, Company Distribution, Deal Distribution by Owner, Monthly Revenue Trend |

> The exact 24 templates span these categories. Template names are searchable in the library.

### Using a Template

1. Open the Template Library
2. Browse or search for a template by name
3. Click the template card to preview it
4. Click **Add to Dashboard** — the chart is added to the current dashboard with default configuration
5. Click the chart's edit icon to customize filters, date ranges, or grouping

---

## Chart Builder

The Chart Builder is a **3-panel layout** for creating individual charts.

**Access:** Click **+ Add Chart** → **Create Manually** on any dashboard

### Panel Layout

| Panel | Content |
|-------|---------|
| **Left** | Configuration — Primary Object, filters, values/metrics, group by, chart type selector |
| **Center** | Live chart preview — updates as configuration changes |
| **Right** | Chart-type-specific settings (axes, colors, labels, thresholds) |

### Configuration Fields

#### Primary Object
The entity type the chart is built on. Options:
- **Leads**
- **Contacts**
- **Companies**
- **Deals**
- **Tasks**
- **Activities** (calls, meetings, notes)
- **Campaigns**
- **Sequences**

#### Filters
Add conditions to narrow the data:
1. Click **+ Add Filter**
2. Select a property (e.g., "Status", "Owner", "Created Date")
3. Select an operator (equals, contains, is before, is after, is empty, etc.)
4. Enter a value
5. Multiple filters use AND logic by default; OR logic can be toggled

#### Values (Metrics)
The measure(s) to display:
- **Count** — count of records
- **Sum** — sum of a numeric field (e.g., Deal Value)
- **Average** — average of a numeric field
- **Min / Max** — minimum or maximum value
- Multiple values can be added for multi-series charts

#### Group By
Dimension to segment data:
- Select a property field (e.g., "Stage", "Owner", "Created Month")
- For time fields: group by Day, Week, Month, Quarter, Year
- Second group by available for pivot tables and scatter charts

---

## Chart Types (12)

| Chart Type | Best For |
|------------|----------|
| **Bar Chart** | Comparing values across categories |
| **Horizontal Bar** | Same as bar but horizontal — better for long labels |
| **Line Chart** | Trends over time |
| **Area Chart** | Trends over time with filled area (volume emphasis) |
| **Pie Chart** | Part-to-whole composition (< 7 slices recommended) |
| **Donut Chart** | Same as pie with center metric display |
| **Scatter Chart** | Correlation between two numeric variables |
| **Bubble Chart** | Correlation with a third variable shown as bubble size |
| **Gauge Chart** | Single metric against a target/threshold |
| **Table** | Tabular data with sorting and column control |
| **Pivot Table** | Cross-tabulation with row/column grouping |
| **Funnel Chart** | Stage-by-stage conversion visualization |

---

## Chart-Specific Configuration

The right panel shows different settings depending on the selected chart type:

| Chart Type | Right Panel Sections |
|------------|---------------------|
| Table | Columns, Sort, Pagination |
| Gauge | Min Value, Max Value, Threshold, Color Bands |
| Area Chart | X-Axis, Y-Axis, Fill Opacity, Stacking |
| Pivot Table | Row Groups, Column Groups, Values, Aggregation |
| Funnel | Stage Field, Value Field, Color |
| Scatter/Bubble | X-Axis Field, Y-Axis Field, Bubble Size Field (Bubble only), Color By |

### Table Chart
- **Columns** — select which fields appear as columns; drag to reorder
- **Sort** — default sort column and direction (ascending/descending)
- **Pagination** — rows per page (10/25/50/100)
- **Column Width** — auto or fixed pixel width per column

### Gauge Chart
- **Min Value** — lower bound of the gauge (default: 0)
- **Max Value** — upper bound of the gauge (required — set to your target)
- **Threshold** — value at which color changes (e.g., 80% of target)
- **Color Bands** — configure color zones (red/yellow/green ranges)

### Area Chart
- **X-Axis** — time or category field
- **Y-Axis** — numeric metric
- **Fill Opacity** — transparency of the filled area (0–100%)
- **Stacking** — stack multiple series for cumulative view

### Pivot Table
- **Row Groups** — fields that become row headers
- **Column Groups** — fields that become column headers
- **Values** — metrics displayed in cells
- **Aggregation** — Sum / Count / Average per cell

### Funnel Chart
- **Stage Field** — the categorical field defining each funnel stage
- **Value Field** — the numeric metric (count or sum)
- **Color** — single color or automatic gradient

### Scatter / Bubble Chart
- **X-Axis Field** — first numeric dimension
- **Y-Axis Field** — second numeric dimension
- **Bubble Size Field** — (Bubble chart only) third numeric dimension controlling dot size
- **Color By** — categorical field for dot coloring
- **Show Labels** — toggle to display record names on each point

---

## Add Calculated Fields

Calculated fields let you create derived metrics using formulas.

**Access:** In the Chart Builder left panel, click **+ Add Calculated Field** (available in the Values section)

### Properties Tab

Pre-built calculated field types:

| Field | Description |
|-------|-------------|
| **ID** | Count of unique record IDs |
| **Duration** | Time between two date fields (e.g., Created Date → Close Date) |

### Functions Tab

Build custom formulas using four function categories:

#### CONDITIONAL
- `IF(condition, true_value, false_value)` — conditional logic
- `CASE(field, value1, result1, ...)` — multi-branch condition

#### COMPARISON
- `EQUALS(a, b)` — returns true/false
- `GREATER_THAN(a, b)`, `LESS_THAN(a, b)`
- `BETWEEN(value, min, max)`

#### LOGICAL
- `AND(condition1, condition2)` — both must be true
- `OR(condition1, condition2)` — either must be true
- `NOT(condition)` — inverts boolean

#### ARITHMETIC
- `ADD(a, b)`, `SUBTRACT(a, b)`, `MULTIPLY(a, b)`, `DIVIDE(a, b)`
- `ROUND(value, decimals)` — round to N decimal places
- `ABS(value)` — absolute value

### Using a Calculated Field
1. Click **+ Add Calculated Field** in the Values section
2. Select **Properties** tab for pre-built types OR **Functions** tab for custom formulas
3. Select the function or property type
4. Configure the required inputs (field selectors, constants)
5. Enter a **Field Name** (this label appears in the chart)
6. Click **Save** — the calculated field appears as a selectable value in the chart

---

## End-to-End Workflow

```
1. CREATE SPACE   → Analytics → + New Space → name + visibility → Create
2. CREATE DASHBOARD → click Space → + New Dashboard → choose type → name → Create
3. ADD CHART      → + Add Chart → From Template (quick) OR Create Manually (custom)
4. CONFIGURE      → select Primary Object → add Filters → set Values → Group By
5. CHOOSE TYPE    → select chart type → configure type-specific settings
6. CALCULATED     → + Add Calculated Field → pick function → configure → Save
7. PREVIEW        → center panel shows live preview
8. SAVE CHART     → click Save — chart appears on dashboard
9. EXPORT         → three-dot menu on chart → Export as CSV
```

---

## Agent Behavior Instructions

- **To find an existing dashboard:** Navigate to Analytics in sidebar → click the Space → click the Dashboard name
- **To add a chart:** Open the dashboard → click **+ Add Chart** → choose Create Manually or From Template
- **To use a template:** Click **+ Add Chart** → From Template → search template name → click template → Add to Dashboard
- **To configure a chart metric:** In chart builder left panel, find Values section → click **+ Add Value** → select field and aggregation
- **To filter chart data:** In chart builder left panel, click **+ Add Filter** → select property → set operator and value
- **To export chart data:** Hover chart tile → three-dot icon → Export as CSV

---

## Key Gotchas

1. **Spaces must exist before dashboards** — you cannot create a dashboard without first selecting or creating a Space. There is no global "Create Dashboard" button; it only appears inside a Space.

2. **Deleting a Space deletes all dashboards inside** — there is no move operation. If you need to reorganize, recreate dashboards in the target space first, then delete the old space.

3. **AI-generated dashboards still need review** — AI-generated charts use default date ranges and may not match the user's intent. Always review and edit generated charts.

4. **SQL dashboards require knowledge of schema** — the SQL editor does not provide schema hints. The user must know the table/field names in the SuperAGI data model.

5. **Gauge chart requires Max Value** — a Gauge chart without a Max Value will not render correctly. Always set the target value as the Max.

6. **Pie/Donut charts break with too many segments** — more than 7 distinct values results in an "Other" category. Use Bar charts for high-cardinality dimensions.

7. **Calculated fields are per-chart** — a calculated field defined in one chart is not reusable across other charts. You must recreate it in each chart where it is needed.

8. **Filters use AND logic by default** — multiple filters narrow the dataset cumulatively. To use OR logic, toggle the filter connector between conditions.

9. **Group by time field requires selecting granularity** — when grouping by a date field (e.g., Created Date), you must also select the granularity (Day/Week/Month/Quarter/Year). Missing this results in one data point per unique timestamp.

10. **Export CSV is per-chart only** — there is no "export all charts" or "export full dashboard" as a single file. Each chart must be exported individually.

11. **Bubble chart requires three numeric fields** — X-Axis, Y-Axis, and Bubble Size must all be numeric. Selecting a non-numeric field for any of these prevents the chart from rendering.

12. **Pivot table performance** — pivot tables with high-cardinality row AND column groups can be slow to load. Limit to <50 distinct values per axis for best performance.
