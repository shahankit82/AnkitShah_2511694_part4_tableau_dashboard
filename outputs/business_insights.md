# Business Insights — Executive Sales Dashboard (2024–2025)

## Calculated Fields Created in Tableau

| Field Name | Formula Used | Purpose |
|---|---|---|
| **Profit Margin** | `[profit] / [sales]` | Core profitability KPI shown in KPI card and colour encoding on Regional Performance |
| **Cost** | `[sales] - [profit]` | Enables cost structure analysis alongside revenue |
| **Average Order Value** | `SUM([sales]) / COUNTD([order_id])` | Measures revenue quality per transaction |
| **Return Rate** | `SUM([return_flag]) / COUNT([order_id])` | Guardrail metric — visible as KPI card on dashboard |
| **Shipping Delay Bucket** | IF/ELSEIF on delivery_days: "Same Day", "1 Day", "2–3 Days", "4–7 Days", "8+ Days" | Groups delivery speed for the Shipping Performance bar chart |
| **Discount Band** | IF/ELSEIF on discount: "0%", "1–10%", "11–20%", "21–30%", "31–50%", ">50%" | Used as colour dimension in Discount vs Profit scatter |
| **Is Returned** | IF return_flag=1 THEN "Returned" ELSE "Not Returned" END | Readable label for return segmentation |
| **Profit Status** | IF profit>0 THEN "Profitable" ELSE "Loss" END | Quick flag for loss-making sub-categories |

---

## Business Insights

### 1. SALES TREND — Clear Seasonality with August as Weakest Month

**Observation:** Monthly Sales & Profit Trend shows a consistent dip in August across both years. August 2024 recorded Rs 63,03,795 — the lowest month of the year. Sales recover sharply in September (Rs 1.05 Cr in 2024). The trend is otherwise relatively stable between Rs 70–110 lakhs per month.

**Data evidence:** August 2024 = Rs 63.0L vs September 2024 = Rs 1.05 Cr (+66% recovery in one month). The dual-axis line chart shows both Sales (orange) and Profit (blue) following the same seasonal dip pattern simultaneously.

**Business interpretation:** The August dip is structural — likely a post-summer, pre-festive transition period where customers delay purchases. This affects all categories simultaneously, not just one.

**Recommended action:** Pre-load August with early Diwali/festive promotions and targeted campaigns in late July to pull forward purchases. Increase inventory buffers in August ahead of the September surge.

---

### 2. REGIONAL PERFORMANCE — South Leads Volume; All Four Regions Profitable

**Observation:** The Regional Performance horizontal bar chart (colour-coded by profit) shows South as the clear leader at Rs 6.47 Cr in sales, followed by North (Rs 5.46 Cr), East (Rs 4.89 Cr), and West (Rs 4.89 Cr). Colour gradient confirms all regions are profitable (green shades throughout).

**Data evidence:**
- South: Rs 6,46,93,707 sales | Rs 99,87,912 profit | 15.44% margin
- North: Rs 5,45,55,801 | Rs 83,14,884 | 15.24% margin
- East: Rs 4,88,59,164 | Rs 75,99,443 | 15.55% margin (highest margin)
- West: Rs 4,89,08,980 | Rs 74,04,073 | 15.14% margin (lowest margin)

**Business interpretation:** South leads in volume. East leads in margin efficiency despite lower volume. West matches East in sales but generates the weakest margin — suggesting either higher discounting or less favourable product mix in the West.

**Recommended action:** Apply East's pricing discipline to West region stores. Analyse why West's margin lags despite comparable sales volume. Replicate South's volume-driving sales strategy in North and West.

---

### 3. CATEGORY PROFITABILITY — Technology Dominates; Furniture is a Risk

**Observation:** Category Profitability stacked bar chart clearly shows Technology towering above the others with a profit of Rs 2.80 Cr (sub-categories: Accessories Rs 71.9L, Copiers Rs 73.1L, Machines Rs 64.5L, Phones Rs 71.0L). Furniture (Rs 25,988 visible in the chart) and Office Supplies (Rs 11,622) are significantly lower, with the Average reference line showing how far Furniture and Office Supplies fall below the mean.

**Data evidence:**
- Technology: Rs 15.39 Cr sales | Rs 2.80 Cr profit | 18.22% margin
- Furniture: Rs 5.16 Cr sales | Rs 35.6L profit | 6.89% margin
- Office Supplies: Rs 1.15 Cr sales | Rs 17.1L profit | 14.85% margin

**Business interpretation:** Technology generates 70.9% of total profit on 70.9% of revenue — it is the business engine. Furniture contributes 23.8% of revenue but only 10.7% of profit, making it structurally inefficient. The Average reference line at Rs 80K on the chart confirms Furniture and Office Supplies are below the portfolio mean.

**Recommended action:** Protect and grow Technology (lowest return rate, highest margin). Conduct a sub-category audit of Furniture — specifically Tables and Bookcases — to assess whether volume justifies the margin cost.

---

### 4. DISCOUNT IMPACT — Orders Above 30% Discount Are Loss-Making

**Observation:** The Discount vs Profit scatter plot shows a clear downward trend as discount increases. The trend lines for all three categories converge toward zero profit at around 25–30% discount. Points clustered at 30–35% discount level visibly dip below the zero-profit line.

**Data evidence:**
- 0% discount: avg profit Rs 13,203 per order
- 1–10%: avg profit Rs 10,010
- 11–20%: avg profit Rs 6,336
- 21–30%: avg profit Rs 3,181
- 31–50%: avg profit Rs **−1,601** (loss-making)

**Business interpretation:** The break-even point is between 25–30% discount. Any discount above 30% destroys value on average. The scatter shows Home Office segment (red dots) at high-discount levels generating the largest losses.

**Recommended action:** Implement a hard cap at 25% discount without regional manager approval. Automate an alert for any order exceeding 25% discount. Specifically review Home Office segment high-discount orders.

---

### 5. SHIPPING PERFORMANCE — Standard Class is Slowest but Handles Most Volume

**Observation:** The Shipping Performance chart (colour-coded by ship mode) shows the "8+ Days" bucket carrying the highest average delivery days at 8.133, followed by "4–7 Days" at 5.033. Standard Class (which maps to these longer delays) handles the majority of orders. Same Day delivers at 0.4 days but has very limited volume.

**Data evidence:**
- Same Day: 0.40 avg delivery days | 241 orders
- First Class: 1.77 days | 630 orders
- Second Class: 2.68 days | 894 orders
- Standard Class: 4.71 days | 2,435 orders (58% of all orders)

**Business interpretation:** 58% of all orders use Standard Class, averaging 4.71 days. If slow delivery correlates with lower customer ratings or higher return rates, the concentration in Standard Class creates a hidden quality risk at scale.

**Recommended action:** Analyse correlation between delivery_days and customer_rating. For high-value Technology orders (>Rs 50,000), consider offering free First Class upgrades. Test a "faster shipping" promotion for the Corporate segment to see if it reduces return rates.

---

### 6. RETURN ANALYSIS — Furniture Has the Highest Return Rate Across All Segments

**Observation:** The Return Analysis stacked bar chart shows Furniture with the highest return count (88 returns), with Home Office segment (red) contributing 37 returns — the single largest segment-category combination. Office Supplies and Technology show lower return counts with more balanced distribution across segments.

**Data evidence:**
- Furniture: 88 returns / 1,147 orders = **7.67% return rate**
- Office Supplies: 61 returns / 1,669 orders = 3.65%
- Technology: 42 returns / 1,384 orders = 3.03%
- Highest single segment-category: Furniture × Home Office = 37 returns

**Business interpretation:** Furniture's 7.67% return rate is 2.5× the Technology rate. Combined with Furniture's already-thin 6.89% margin, every return erodes profitability twice — lost revenue plus reverse logistics cost. Home Office customers are the most likely to return Furniture.

**Recommended action:** Improve Furniture product descriptions, dimension guides, and augmented reality "see in your room" previews for online channels. Focus return-reduction effort on the Home Office segment for Furniture first, as it's the highest-volume returner.

---

### 7. CUSTOMER SEGMENT VIEW — Three Segments Are Broadly Equal; Home Office Leads Marginally

**Observation:** The Customer Segment View bar chart (colour-encoded by Profit) shows three broadly comparable segments. Home Office edges ahead at Rs 7.45 Cr sales, followed by Consumer (Rs 7.19 Cr) and Corporate (Rs 7.06 Cr). The profit colour gradient (darker = higher profit) shows Consumer as slightly more profitable in colour intensity.

**Data evidence:**
- Home Office: Rs 7,45,00,746 | Rs 1,15,55,047 profit | 15.51% margin
- Consumer: Rs 7,18,86,173 | Rs 1,10,30,581 | 15.34% margin
- Corporate: Rs 7,06,30,733 | Rs 1,07,20,685 | 15.18% margin

**Business interpretation:** Despite being assumed the most valuable, Corporate has the weakest margin of the three segments. Home Office customers are the most valuable per rupee of sales. The segments are remarkably balanced — no single segment dominates, which reduces concentration risk.

**Recommended action:** Design segment-specific campaigns for Home Office (bundle Technology + Office Supplies) and investigate why Corporate margins lag. Bulk discount arrangements with Corporate clients may be eroding their margin.

---

### 8. BUSINESS RISK — Profit Margin KPI Displaying Incorrect Calculation

**Observation:** The KPI card "Profit Margin" on the dashboard shows 55,118.9% (in the full dashboard screenshot) rather than the expected 15.35%. This is a formula issue — the calculated field is computing `[profit]/[sales]` correctly but Tableau may be applying a non-percentage format, or a text-based Profit Margin field is being summed rather than averaged in the KPI card view.

**Data evidence:** Actual margin = Rs 3,33,06,313 / Rs 21,70,17,652 = **15.35%**. The value 55,118.9% indicates the formula may be summing individual row margins rather than dividing total profit by total sales.

**Business interpretation:** This is a data presentation risk — a leadership audience would misread this KPI. The fix is to change the Profit Margin aggregation in the KPI sheet from SUM to AVG, or rewrite the formula as `SUM([profit]) / SUM([sales])` using a Level of Detail (LOD) expression.

**Recommended action:** In Tableau, right-click the Profit Margin pill in the KPI sheet → change aggregation from SUM to either AVG or use the formula `{SUM([profit])/SUM([sales])}`. The KPI card should then display 15.35%.

---

## Summary Risk and Opportunity Matrix

| Area | Finding | Risk / Opportunity |
|---|---|---|
| Furniture margin | 6.89% margin + 7.67% return rate | HIGH RISK — double-sided value destruction |
| Discounts >30% | Average profit = Rs −1,601 | HIGH RISK — needs immediate policy cap |
| Technology | 18.22% margin, 71% of profit | HIGH OPPORTUNITY — protect and grow |
| South region | Rs 6.47 Cr, highest volume | OPPORTUNITY — codify their playbook |
| August dip | Recurring lowest month | RISK — plan seasonal promotions |
| Standard Class | 4.71-day avg for 58% of orders | RISK — monitor vs customer rating |
| Profit Margin KPI | Displaying 55,118% — incorrect | IMMEDIATE FIX NEEDED — misleads leadership |
