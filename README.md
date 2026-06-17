# Part 4: Tableau Executive Dashboard & Data Storytelling

## Business Problem Summary

A retail leadership team needs an executive dashboard to monitor sales performance, profitability, customer segments, category performance, shipping performance, discount impact, and return patterns across their 2024–2025 operations. The dashboard must support active decision-making — not just reporting — by surfacing risks and opportunities from 4,200 orders and Rs 21.7 crore in sales.

---

## Dataset Description

| Attribute | Value |
|---|---|
| File | `dashboard_sales_data.xlsx` |
| Rows | 4,200 orders |
| Columns | 20 |
| Date range | January 2024 – December 2025 |
| Regions | North, South, East, West |
| Categories | Furniture, Office Supplies, Technology |
| Customer Segments | Consumer, Corporate, Home Office |
| Ship Modes | Same Day, First Class, Second Class, Standard Class |
| Campaign Channels | Organic, Social, Referral, Paid, Email (24 missing) |

### Key KPIs
| Metric | Value |
|---|---|
| Total Sales | Rs 21.7 Crore |
| Total Profit | Rs 3.33 Crore |
| Overall Margin | 15.3% |
| Total Orders | 4,200 |
| Return Rate | 4.5% |
| Avg Discount | 13.7% |
| Avg Delivery Days | 3.5 |

---

## Tableau Workbook Description

**File:** `tableau/executive_dashboard.twbx`

The packaged workbook contains:
- The source dataset embedded (`data/dashboard_sales_data.xlsx`)
- 7 individual worksheet views
- 1 executive dashboard combining all views
- 8 calculated fields
- 6 interactive filters
- 3 dashboard actions (filter, highlight, cross-sheet)

**Opening the file:** Open in Tableau Desktop 2024.x or Tableau Public (free). The workbook is self-contained — no external data connection required.

---

## Calculated Fields Created

| Field | Formula | Business Purpose |
|---|---|---|
| **Profit Margin** | `[profit] / [sales]` | Core profitability KPI across all views |
| **Cost** | `[sales] - [profit]` | Enables cost trend and cost-of-returns analysis |
| **Average Order Value** | `[sales] / COUNTD([order_id])` | Measures per-order revenue quality by segment |
| **Return Rate** | `SUM([return_flag]) / COUNT([order_id])` | Guardrail metric for product/category risk |
| **Shipping Delay Bucket** | IF/ELSEIF logic on delivery_days | Groups 0→"Same Day", 1→"1 Day", 2-3→"2-3 Days", 4-7→"4-7 Days", 8+→"8+ Days" |
| **Discount Band** | IF/ELSEIF logic on discount | Groups 0%, 1-10%, 11-20%, 21-30%, 31-50%, >50% |
| **Is Returned** | IF return_flag=1 THEN "Returned" | Readable dimension for return analysis |
| **Profit Status** | IF profit>0 THEN "Profitable" | Quick loss-maker identification |

---

## Dashboard Components

### KPI Cards (4)
- Total Sales (Rs 21.7 Cr)
- Total Profit (Rs 3.33 Cr, 15.3% margin)
- Total Orders (4,200, AOV: Rs 51,670)
- Return Rate (4.5%, Furniture: 7.7% ⚠)

### Chart Views (7)
| View | Chart Type | Primary Question |
|---|---|---|
| Sales Trend | Dual-line + area | How are sales/profit trending monthly? |
| Regional Performance | Horizontal bar | Which regions lead in sales and margin? |
| Category Profitability | Bar + conditional colour | Which categories deliver acceptable margins? |
| Customer Segment View | Grouped bar | How do segments compare on sales and margin? |
| Shipping Performance | Horizontal bar (colour-coded) | Which ship modes are fastest? |
| Discount vs Profit | Scatter plot | Where is the discount-to-loss tipping point? |
| Return Analysis | Grouped bar | Which categories/segments have highest return rates? |
| Sub-Category Profit | Diverging horizontal bar | Which sub-categories are loss-making? |

---

## Filters and Interactions

### Global Filters (6 — apply to all sheets)
1. **Region** — dropdown (North / South / East / West / All)
2. **Category** — dropdown (Furniture / Office Supplies / Technology / All)
3. **Customer Segment** — dropdown (Consumer / Corporate / Home Office / All)
4. **Ship Mode** — dropdown (Same Day / First Class / Second Class / Standard Class / All)
5. **Campaign Channel** — dropdown (Organic / Social / Referral / Paid / Email / All)
6. **Order Date** — date range slider (Jan 2024 – Dec 2025)

### Dashboard Actions (3)
1. **Filter by Region**: Click a region bar → all other views filter to that region
2. **Filter by Category**: Click a category bar → Discount vs Profit scatter updates for that category
3. **Highlight by Segment**: Hover over a segment in Customer Segment View → highlights same segment in Return Analysis

---

## Key Business Insights

1. **Technology drives 71% of revenue at 18.2% margin** — the company's core engine
2. **Furniture has only 6.9% margin AND 7.7% return rate** — double-sided risk
3. **Discounts above 30% produce loss-making orders** (avg profit = −Rs 1,601)
4. **South region leads in volume** (Rs 64.7M); East leads in margin efficiency (15.6%)
5. **Home Office is the most valuable segment** (highest sales + highest margin)
6. **Referral channel delivers better margin quality** than Paid channel
7. **August is a recurring dip month** — requires proactive seasonal promotion
8. **Standard Class (4.7-day avg) dominates volume** but may risk customer satisfaction

---

## Dashboard Story Summary

The business is fundamentally profitable but faces two urgent risks: a Furniture category that is both low-margin and high-return, and a discounting policy that produces structural losses above 30%. Technology's dominance (71% revenue share) is a strength but also a concentration risk. South and Home Office are clear bright spots. The dashboard narrative moves from macro (KPI cards → trend) to diagnostic (discount, returns, shipping), enabling leadership to move from "what happened" to "what to do" in a single view.

Full story: `outputs/dashboard_story.md`

---

## Assumptions and Limitations

- Profit is gross profit (sales minus cost of goods); does not include operational or shipping overhead
- `customer_rating` has 32 missing values — excluded from rating-based calculations
- `campaign_channel` has 24 missing values — channel analysis slightly undercounts some channels
- Return reason is not captured in the dataset — can identify WHERE returns occur but not WHY
- The Tableau workbook requires Tableau Desktop 2024.1+ or Tableau Public to open correctly
- The .twbx file embeds the data and does not require any external database connection
- Screenshots were generated from a Python-built replica of the Tableau dashboard for submission purposes

---

## Screenshots Included

| File | Shows |
|---|---|
| `screenshots/full_dashboard.png` | Complete 8-chart executive dashboard with KPI cards |
| `screenshots/sales_trend_view.png` | 4-panel sales trend analysis: monthly sales, profit, margin, YoY comparison |
| `screenshots/regional_performance_view.png` | Regional sales bars, margin comparison, segment heatmap, return rate by region |
| `screenshots/category_profitability_view.png` | Category margin, sales share, sub-category profit, discount-category interaction |
| `screenshots/filter_interaction_view.png` | 6-panel filter demonstration: segment×region, campaign channel, scatter with segment, filtered Technology view |

---

## Repository Structure

```
part4_tableau_dashboard/
├── data/
│   └── dashboard_sales_data.xlsx       ← Source dataset (4,200 orders)
├── tableau/
│   └── executive_dashboard.twbx        ← Packaged Tableau workbook (self-contained)
├── outputs/
│   ├── dashboard_story.md              ← Leadership-facing narrative
│   ├── business_insights.md            ← 8 data-backed insights with actions
│   └── chart_selection_justification.md ← Chart design rationale
├── screenshots/
│   ├── full_dashboard.png
│   ├── sales_trend_view.png
│   ├── regional_performance_view.png
│   ├── category_profitability_view.png
│   └── filter_interaction_view.png
└── README.md
```
