# Business Insights — Executive Sales Dashboard (2024–2025)

## Calculated Fields Created

| Field | Formula | Purpose |
|---|---|---|
| **Profit Margin** | `[profit] / [sales]` | Core profitability KPI |
| **Cost** | `[sales] - [profit]` | Enables cost trend analysis |
| **Average Order Value** | `[sales] / COUNTD([order_id])` | Measures per-order revenue quality |
| **Return Rate** | `SUM([return_flag]) / COUNT([order_id])` | Guardrail metric for product quality |
| **Shipping Delay Bucket** | IF delivery_days=0 → "Same Day", ≤1 → "1 Day", ≤3 → "2-3 Days", ≤7 → "4-7 Days", ELSE "8+ Days" | Groups delivery speed for analysis |
| **Discount Band** | IF discount=0 → "0%", ≤10% → "1-10%", ≤20% → "11-20%", ≤30% → "21-30%", ≤50% → "31-50%", ELSE ">50%" | Enables discount-vs-profit segmentation |
| **Is Returned** | IF return_flag=1 → "Returned" ELSE "Not Returned" | Readable flag for return analysis |
| **Profit Status** | IF profit>0 → "Profitable" ELSE "Loss" | Quick classification for loss detection |

---

## Business Insights

### 1. SALES TREND — Seasonality Pattern with Aug Dip
**Observation:** Monthly sales show a recurring low point in August (Rs 6.3M in Aug 2024, Rs 10.9M in Aug 2025 — a notable recovery year-on-year). January and September-October are consistently strong months.

**Data evidence:** Aug 2024 = Rs 6.3M (lowest month across 2 years); Sep 2024 = Rs 10.5M (bouncing back +66% in one month).

**Business interpretation:** The August dip likely reflects a seasonal slowdown (post-festival lull or academic year transition). The strong Sep-Oct recovery suggests a pre-Diwali/festive stocking pattern.

**Recommended action:** Pre-position inventory and marketing campaigns in July to minimise the August revenue gap. Run an early-access promotion in late July to pull-forward August purchases.

---

### 2. REGIONAL PERFORMANCE — South Leads but East Has Best Margin
**Observation:** South region has the highest absolute sales (Rs 64.7M) but East region has the highest profit margin (15.6% vs West's 15.1%).

**Data evidence:**
- South: Rs 64.7M sales, Rs 10.0M profit (15.4% margin)
- East: Rs 48.9M sales, Rs 7.6M profit (15.6% margin)
- West: Rs 48.9M sales, Rs 7.4M profit (15.1% margin — lowest)

**Business interpretation:** South is the volume engine; East is the efficiency leader. West underperforms on margin despite similar sales to East — suggesting higher discounting or cost structure in the West.

**Recommended action:** Investigate West region's discount practices and cost structure. Apply East's pricing discipline to West. Replicate South's volume-driving tactics (campaign mix, product focus) in underperforming regions.

---

### 3. CATEGORY PROFITABILITY — Furniture is a Margin Drain
**Observation:** Technology generates 70.9% of total sales (Rs 153.9M) at an 18.2% margin. Furniture contributes 23.8% of sales but only 6.9% margin — far below the 15.3% company average.

**Data evidence:**
- Technology: 18.2% margin | Rs 28.0M profit
- Office Supplies: 14.9% margin | Rs 1.7M profit
- Furniture: 6.9% margin | Rs 3.6M profit

**Business interpretation:** Furniture is volume-meaningful but profit-destructive relative to its share. Tables and Bookcases (sub-categories) likely drag this down further.

**Recommended action:** Conduct a sub-category profitability audit for Furniture. Consider reducing discounts on Furniture, renegotiating supplier costs, or deprioritising high-volume/low-margin Furniture SKUs in favour of Technology accessories.

---

### 4. DISCOUNT IMPACT — Orders Above 30% Discount Are Loss-Making
**Observation:** Average profit per order inverts to negative (Rs -1,601) when discounts exceed 30%. The tipping point is clearly between the 21-30% band (Rs 3,181 avg profit) and 31-50% band (loss territory).

**Data evidence:**
- 0% discount → avg profit Rs 13,203
- 1-10% → Rs 10,011
- 11-20% → Rs 6,336
- 21-30% → Rs 3,181
- 31-50% → Rs -1,602 (loss)

**Business interpretation:** The company's discounting strategy is destroying value at the high end. Each percentage point above 30% discount is accelerating losses.

**Recommended action:** Implement a hard cap on discounts at 25% without regional/category manager approval. Automate a Tableau alert that flags any order with discount >25% for daily review. Specifically investigate which customers or sales reps are applying 30%+ discounts.

---

### 5. SHIPPING PERFORMANCE — Standard Class Dominates but Slowest
**Observation:** Standard Class accounts for the majority of orders (Rs 122.8M sales) but averages 4.7 delivery days. Same Day shipping (Rs 14.6M, avg 0.4 days) has the fastest delivery but lowest volume.

**Data evidence:**
- Same Day: 0.4 days avg | Rs 14.6M sales
- First Class: 1.8 days | Rs 31.9M
- Second Class: 2.7 days | Rs 47.7M
- Standard Class: 4.7 days | Rs 122.8M

**Business interpretation:** The majority of orders are on the slowest mode. This may be customer-driven (cost preference) or default selection. There's a risk that slow delivery is contributing to lower customer ratings.

**Recommended action:** Analyse the correlation between delivery_days and customer_rating. If faster delivery correlates with higher ratings (and lower returns), consider subsidising First Class upgrades for high-value Technology orders. Test "free First Class" promotion for orders above Rs 50,000.

---

### 6. RETURN RATE — Furniture Returns Are Disproportionately High
**Observation:** Furniture has a 7.7% return rate vs Technology's 3.0% and Office Supplies' 3.7% — more than 2.5× the Technology rate.

**Data evidence:**
- Furniture: 7.7% return rate
- Office Supplies: 3.7%
- Technology: 3.0%
- Company average: 4.5%

**Business interpretation:** Furniture returns create double-cost impact: lost revenue AND reverse logistics. At 7.7%, roughly 1 in 13 Furniture orders is returned. Combined with Furniture's already-low 6.9% margin, this makes Furniture the most concerning category.

**Recommended action:** Improve Furniture product descriptions and dimension specifications online (a common driver of furniture returns). Add a "measure before you buy" prompt for large Furniture items. Review Furniture return reasons — if the majority are "not as described," update product content urgently.

---

### 7. CUSTOMER SEGMENT — Home Office Leads in Sales and Margin
**Observation:** Home Office segment achieves the highest sales (Rs 74.5M) and the highest margin (15.5%), making it the most valuable segment by both dimensions.

**Data evidence:**
- Home Office: Rs 74.5M sales, 15.5% margin
- Consumer: Rs 71.9M, 15.3% margin
- Corporate: Rs 70.6M, 15.2% margin

**Business interpretation:** Despite the three segments being broadly similar in scale, Home Office's slight margin advantage suggests lower discounting and higher-value product mix. The Corporate segment, typically assumed to be the most valuable, is the weakest of the three.

**Recommended action:** Investigate why Corporate margin lags. It may reflect bulk discounting arrangements or higher service costs. Consider introducing tiered pricing for Corporate that preserves volume while improving margin per order.

---

### 8. CAMPAIGN CHANNEL — Referral Delivers Best Margin; Paid Needs Review
**Observation:** Referral channel customers show the highest profit margin, while Paid channel (paid advertising) has lower margin quality — suggesting acquisition cost or discount usage is higher for paid-traffic customers.

**Data evidence:** Referral and Organic channels show margin >15.5%; Paid channel customers exhibit lower average order profit and higher discount usage patterns.

**Business interpretation:** Referral customers likely have higher intent and lower price sensitivity, leading to better-quality orders. Paid channel may be attracting discount-hunters.

**Recommended action:** Invest in referral programme mechanics (incentivised sharing, loyalty bonuses for referring new customers). Restructure Paid channel campaign targeting to focus on high-margin product categories (Technology) rather than broad acquisition.

---

## Summary of Key Risks and Opportunities

| Area | Finding | Risk/Opportunity |
|---|---|---|
| Furniture | 6.9% margin + 7.7% return rate | HIGH RISK — two-sided margin destruction |
| Discounting >30% | Negative average profit | HIGH RISK — needs policy cap |
| Technology | 18.2% margin, 70.9% sales share | HIGH OPPORTUNITY — protect and grow |
| South Region | Highest volume | OPPORTUNITY — extract lessons for other regions |
| Home Office Segment | Best margin | OPPORTUNITY — design segment-specific campaigns |
| August Dip | Recurring low month | RISK — plan seasonal promotions |
| Standard Class delivery | 4.7-day avg | RISK if correlated with low ratings |
