# Final Capstone Project

# Part 4: Tableau Executive Dashboard & Data Storytelling

## Business Problem Summary

A retail leadership team needs an executive dashboard to monitor sales performance, profitability, customer segments, category performance, shipping performance, discount impact, and return patterns across their 2024–2025 operations. The dashboard must support active decision-making — not just reporting — by surfacing risks and opportunities from 4,200 orders and Rs 21.70 Crore in sales across four regions, three categories, and three customer segments.

---

## Dataset Description

| Attribute | Value |
|---|---|
| File | `dashboard_sales_data.xlsx` |
| Total rows | 4,200 orders |
| Columns | 20 |
| Date range | January 2024 – December 2025 (24 months) |
| Regions | North, South, East, West |
| Categories | Furniture, Office Supplies, Technology |
| Sub-categories | 12 (Accessories, Art, Binders, Bookcases, Chairs, Copiers, Furnishings, Labels, Machines, Paper, Phones, Storage, Tables) |
| Customer Segments | Consumer, Corporate, Home Office |
| Ship Modes | Same Day, First Class, Second Class, Standard Class |
| Campaign Channels | Organic, Social, Referral, Paid, Email |

### Key Business Metrics (Full Dataset)

| Metric | Value |
|---|---|
| Total Sales | Rs 21,70,17,651.92 |
| Total Profit | Rs 3,33,06,312.84 |
| Overall Profit Margin | 15.35% |
| Total Orders | 4,200 |
| Unique Customers | Approx. 4,200 (one order per customer_id in this dataset) |
| Overall Return Rate | 4.55% (191 returns) |
| Average Order Value | Rs 51,670.87 |
| Average Delivery Days | 3.88 days across all modes |

---

## Tableau Workbook Description

**File:** `tableau/executive_dashboard.twbx`

The packaged workbook contains the source dataset embedded within the file and requires no external data connection to open. It was built entirely in Tableau Desktop and saved as a Packaged Workbook (.twbx).

### Workbook Contents

| Component | Count | Details |
|---|---|---|
| Worksheets | 11 | 4 KPI sheets + 7 analytical chart sheets |
| Dashboards | 1 | Executive Dashboard combining all 11 sheets |
| Calculated fields | 8 | All required fields present |
| Filters on dashboard | 1 interactive (Region) + Dashboard action filter | |
| Dashboard actions | 1 | Filter action from Regional Performance to all sheets |

---

## Calculated Fields Created

| Field | Formula | Business Purpose |
|---|---|---|
| **Profit Margin** | `[profit] / [sales]` | Core profitability KPI displayed in KPI card and colour encodings |
| **Cost** | `[sales] - [profit]` | Cost structure analysis |
| **Average Order Value** | `SUM([sales]) / COUNTD([order_id])` | Revenue quality per transaction |
| **Return Rate** | `SUM([return_flag]) / COUNT([order_id])` | Guardrail metric — return risk monitoring |
| **Shipping Delay Bucket** | IF [delivery_days]=0 THEN "Same Day" ELSEIF [delivery_days]=1 THEN "1 Day" ELSEIF [delivery_days]<=3 THEN "2-3 Days" ELSEIF [delivery_days]<=7 THEN "4-7 Days" ELSE "8+ Days" END | Groups delivery speed into business-meaningful tiers |
| **Discount Band** | IF [discount]=0 THEN "0%" ELSEIF [discount]<=0.10 THEN "1-10%" ELSEIF [discount]<=0.20 THEN "11-20%" ELSEIF [discount]<=0.30 THEN "21-30%" ELSEIF [discount]<=0.50 THEN "31-50%" ELSE ">50%" END | Segments discount levels for profit impact analysis |
| **Is Returned** | IF [return_flag]=1 THEN "Returned" ELSE "Not Returned" END | Human-readable return dimension |
| **Profit Status** | IF [profit]>0 THEN "Profitable" ELSE "Loss" END | Loss detection flag per order |

---

## Dashboard Components

### KPI Cards (4 sheets — top row of dashboard)

| KPI Sheet | Metric Displayed | Value |
|---|---|---|
| KPI Sales | Total Sales | Rs 21,70,17,651.92 |
| KPI Profit | Total Profit | Rs 3,33,06,313 |
| KPI – Profit Margin | Profit Margin % | 15.35% (note: displayed as 55,118.9% due to aggregation — fix by changing to AVG or using SUM/SUM formula) |
| KPI – Return Rate | Return Rate % | 4.55% |

### Chart Sheets (7 sheets — body of dashboard)

| Sheet Name | Chart Type | Primary Question Answered |
|---|---|---|
| Sales Trend | Dual-axis line chart | How are sales and profit trending month by month? |
| Regional Performance | Horizontal bar, colour by profit | Which regions lead in sales and are they all profitable? |
| Category Profitability | Stacked bar by sub-category + avg reference line | Which categories and sub-categories drive profit? |
| Customer Segment View | Bar chart, colour by profit | How do the three segments compare on sales and margin? |
| Shipping Performance | Horizontal bar by delay bucket, colour by ship mode | Which ship modes are fastest and what are typical delays? |
| Discount vs Profit | Scatter plot, colour by category, size by sales, trend lines | Where does discounting destroy profit? |
| Return Analysis | Stacked bar, colour by customer segment | Which categories and segments have the most returns? |

---

## Filters and Interactions

### Interactive Filter
- **Region filter** — applied on Sales Trend sheet, accessible from dashboard. Allows filtering to individual regions (All / East / North / South / West).

### Dashboard Action
- **Filter by Region action** — clicking any bar in the Regional Performance chart filters all other charts on the dashboard to show only that region's data. Clicking the same bar again or pressing Escape clears the filter and returns all charts to full view.

### How to Use the Dashboard
1. Start with the KPI cards for a headline summary
2. Review Sales Trend for the time dimension
3. Click a region bar in Regional Performance to filter everything to that region
4. Check Category Profitability and Discount vs Profit to understand margin drivers
5. Check Return Analysis and Shipping Performance for operational risks
6. Clear the region filter (Escape) to return to full view

---

## Key Business Insights

### What is performing well
1. **Technology drives the business** — Rs 2.80 Cr profit at 18.22% margin, lowest return rate (3.03%), four strong sub-categories
2. **South leads in volume** — Rs 6.47 Cr in sales, profitable at 15.44% margin
3. **All four regions are profitable** — Regional Performance chart shows no red (loss) colouring anywhere
4. **Three balanced segments** — Home Office (Rs 7.45 Cr), Consumer (Rs 7.19 Cr), Corporate (Rs 7.06 Cr) — no single-segment concentration risk

### What needs attention
5. **Furniture double risk** — 6.89% margin AND 7.67% return rate — worst category on both dimensions simultaneously
6. **Discounts above 30% are loss-making** — average profit per order = Rs −1,601 at 31–50% band
7. **August is a predictable dip** — visible in both 2024 and 2025 on the Sales Trend chart
8. **West margin lags East** — same sales volume (Rs 4.89 Cr each) but West margin (15.14%) trails East (15.55%)

---

## Dashboard Story Summary

The retail business is fundamentally healthy — profitable across all regions, balanced across segments, and powered by a strong Technology category. But two structural issues are visible in the dashboard and demand leadership action before the next planning cycle.

First, Furniture is destroying value from both ends: low margins (6.89%) and high returns (7.67%), particularly from Home Office customers. Second, the discounting practice produces loss-making orders above 30% discount — the Discount vs Profit scatter chart shows trend lines clearly crossing zero at that threshold.

The recommended actions in priority order: (1) cap discounts at 25% without GM approval, (2) fix the Profit Margin KPI card formula, (3) audit Furniture sub-categories for margin viability, (4) plan proactively for August's recurring dip.

Full narrative: `outputs/dashboard_story.md`

---

## Assumptions and Limitations

- Profit is gross profit (sales minus cost of goods) — does not include shipping costs, return handling, or operational overheads. Actual net margin would be lower than 15.35%.
- Return reason is not captured in the dataset — returns are flagged (1/0) but the reason (damaged, wrong item, changed mind) is unknown.
- The Profit Margin KPI card currently displays 55,118.9% instead of 15.35% due to a Tableau aggregation issue (SUM of row-level margins rather than total profit/total sales). The correct value is 15.35%. Fix: change formula to `{SUM([profit])/SUM([sales])}` or change aggregation to AVG.
- Campaign channel has some missing values — channel-level analysis may slightly undercount some channels.
- 24 months of data provides good trend visibility but is insufficient for formal seasonality modelling or forecasting.
- The dashboard filter action was built using Regional Performance as the source — clicking bars in other charts does not trigger cross-filtering (this would require additional filter actions).

---

## Screenshots Included

| File | What It Shows |
|---|---|
| `screenshots/full_dashboard.png` | Complete Executive Dashboard — all 11 sheets, 4 KPI cards, title, 7 chart views, layout |
| `screenshots/sales_trend_view.png` | Monthly Sales & Profit Trend dual-axis line chart with Region filter and Measure Names legend |
| `screenshots/regional_performance_view.png` | Regional Performance horizontal bar chart sorted by sales, colour-encoded by profit |
| `screenshots/category_profitability_view.png` | Category Profitability stacked bar by sub-category with average reference line |
| `screenshots/filter_interaction_view.png` | Executive Dashboard with East region selected via filter action — all charts filtered simultaneously |

---

## Repository Structure

```
part4_tableau_dashboard/
├── data/
│   └── dashboard_sales_data.xlsx          ← Source dataset (4,200 orders, 20 columns)
├── tableau/
│   └── executive_dashboard.twbx           ← Packaged Tableau workbook (self-contained)
├── outputs/
│   ├── dashboard_story.md                 ← Leadership-facing narrative
│   ├── business_insights.md               ← 8 data-backed insights with evidence and actions
│   └── chart_selection_justification.md   ← Chart design rationale for all 7 views
├── screenshots/
│   ├── full_dashboard.png                 ← Complete dashboard view
│   ├── sales_trend_view.png               ← Sales Trend sheet
│   ├── regional_performance_view.png      ← Regional Performance sheet
│   ├── category_profitability_view.png    ← Category Profitability sheet
│   └── filter_interaction_view.png        ← Dashboard with filter action active
└── README.md
```
