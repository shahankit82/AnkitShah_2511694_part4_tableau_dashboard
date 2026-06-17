# Dashboard Story — Executive Sales Overview (2024–2025)
## Written for Leadership Audience

---

## Executive Summary

Across 4,200 orders and Rs 21.7 crore in sales over 2024–2025, the retail business is fundamentally healthy — but two areas require immediate leadership attention: **Furniture's eroding profitability** and **a broken discounting discipline** that is producing loss-making orders at the high end of the discount scale.

Technology is the business's engine, delivering 71% of revenue at an 18.2% margin. The South region leads in volume. Home Office customers are the most valuable segment. These strengths should be protected and amplified.

---

## What Is Performing Well

### Technology Is the Profit Powerhouse
Technology generates Rs 28.0 million in annual profit on Rs 153.9 million in sales — an 18.2% margin that is well above the 15.3% company average. Sub-categories like Copiers and Accessories drive this. This is the category to double down on: it has high customer demand, strong margin, and relatively low return rates (3.0%).

**Story link:** The Discount vs Profit chart confirms Technology orders maintain profitability even at moderate discount levels (10-20%), unlike Furniture, which crosses into loss territory at much lower discounts.

### South Region is the Volume Champion
South generates Rs 64.7 million in sales — 29.8% of the company's total — and its profitability (15.4% margin) is above the West region benchmark. Leadership's South-region strategy is working. The question is: what is South doing that other regions are not?

**Story link:** The Regional Performance view shows South leading in absolute sales. The segment heatmap reveals that South's strength cuts across all three customer segments — Home Office, Consumer, and Corporate — which is a structural advantage, not a one-segment dependency.

### Home Office is the Hidden Star
Despite being a segment that might intuitively seem smaller, Home Office customers generate the highest revenue (Rs 74.5M) and the best margin (15.5%). These customers appear to be buying high-value Technology and Office Supplies without heavy discounting.

---

## What Is Underperforming

### Furniture: Double Jeopardy (Low Margin + High Returns)
Furniture tells a two-part underperformance story. First, its profit margin of 6.9% is barely half the company average. Second, it carries a 7.7% return rate — the highest of any category, and nearly 2.5× the Technology return rate. Every Furniture return is doubly costly: the order was already low-margin, and the return creates reverse logistics cost on top.

**Story link:** The Category Profitability view (orange bar) makes the margin gap immediately visible. The Return Analysis chart reinforces this — Furniture's return bar is consistently the tallest across all segments and regions.

### The 30%+ Discount Problem
The Discount vs Profit scatter plot tells a clear story: once discounts exceed 30%, average profit per order becomes negative (Rs -1,601). This is not a marginal effect — it is a structural profitability destruction. Somewhere in the business, high-value orders are being approved at 31-50% discounts, producing losses that offset the gains from well-priced orders elsewhere.

**Story link:** The Discount Band chart shows the inflection point clearly at the 31-50% band. When the Category filter is applied to Furniture, the loss zone appears at even lower discount thresholds — 21-30% for Furniture already produces thin margins.

### West Region Leaves Margin on the Table
While West matches East in absolute sales (Rs 48.9M each), West's margin is the weakest of all four regions (15.1% vs East's 15.6%). Over Rs 217 million in total sales, even a 0.5 percentage point margin gap is material. West's underperformance may reflect heavier discounting, a less favourable product mix, or higher operational costs.

---

## What Risks Are Visible

### 1. Discounting Without a Floor
Orders with 30%+ discounts exist in the data — these are structurally loss-making. Without a policy control, individual sales decisions are eroding company profitability order by order.

### 2. Furniture's Margin-Return Spiral
If Furniture's return rate is driven by product quality or expectation mismatches, the problem will worsen as volume grows. A 7.7% return rate at 6.9% margin means the effective margin on Furniture, after return costs, may be close to zero or negative.

### 3. August Revenue Dip — Unprepared
The August dip is visible in both 2024 (Rs 6.3M, the lowest month of the year) and, while August 2025 recovered (Rs 10.9M), the pattern is real. Without a counter-seasonal strategy, August will underperform again.

### 4. Standard Class Delivery Dominating — Possible Rating Impact
The majority of orders ship via Standard Class (4.7-day average). If slower delivery is correlated with lower customer ratings or higher return rates, there is a hidden cost accumulating in the Standard Class decision.

---

## What Opportunities Are Visible

### 1. Grow Technology Further — Low Return, High Margin
Technology is already 71% of revenue and growing. Its 3.0% return rate is excellent. Accelerating Technology sales through targeted campaigns (especially via the Referral channel, which shows strong margin quality) is the clearest growth lever.

### 2. South-Region Playbook for Other Regions
South's success across all segments is reproducible. Leadership should commission a qualitative review of South's pricing, product mix, and campaign approach and translate those learnings into North and West regional plans.

### 3. Home Office Segment — Design Exclusive Campaigns
Home Office customers are the most valuable but probably receive generic marketing. A segment-specific campaign (bundled Technology + Office Supplies offers, subscription-style replenishment for supplies) could increase both AOV and loyalty.

### 4. Referral Channel — Underinvested
Referral delivers strong margin quality. Yet it likely receives a small fraction of marketing budget vs Paid channels. Formalising a referral programme (customer incentives for introducing new buyers) could replicate the organic quality of referral at scale.

---

## Recommended Business Actions

| Priority | Action | Metric to Watch |
|---|---|---|
| 1 — Immediate | Cap discounts at 25% without GM approval | % orders >25% discount |
| 2 — Immediate | Audit Furniture sub-categories for margin viability | Furniture profit margin by sub-cat |
| 3 — Short-term | Pre-plan August promotional campaign for next year | August sales vs prior year |
| 4 — Short-term | Investigate West region discounting practices | West margin vs East margin |
| 5 — Medium-term | Launch Home Office segment-specific campaign | Home Office AOV & order count |
| 6 — Medium-term | Formalise referral programme | Referral channel revenue share |
| 7 — Ongoing | Monitor delivery_days vs customer_rating correlation | Rating by ship mode |

---

## Limitations of This Dashboard

1. **No cost breakdown**: The dashboard cannot separate product cost from operational cost (shipping, returns handling). "Profit" here is gross profit only.
2. **No time-series forecasting**: The trend views show historical patterns but do not predict future performance. A separate forecasting model would be needed.
3. **Customer rating has 32 missing values**: Rating-based insights should be treated as directional rather than precise.
4. **Campaign channel has 24 missing values**: Channel attribution for those 24 orders is unknown; channel-level conclusions may slightly understate some channels.
5. **No customer lifetime value**: The dashboard is order-level. A customer who places 10 small orders looks the same as one placing 10 large ones in aggregate metrics.
6. **Return reason not captured**: The dataset flags returns (return_flag=1) but doesn't specify why. "Not as described," "damaged in transit," and "changed mind" require different business responses.

---

## Suggested Next Analysis

1. **Furniture Sub-Category Deep Dive**: Which specific sub-categories (Tables, Bookcases, Chairs?) are the primary margin drains?
2. **Delivery Days vs Customer Rating Regression**: Is Standard Class speed statistically correlated with lower ratings?
3. **Discount Approval Audit**: Which regions, segments, and product categories have the highest proportion of 25%+ discount orders?
4. **Customer Cohort Analysis**: What is the repeat purchase rate by segment and channel? Are Referral customers more loyal?
5. **State-Level Profitability Map**: Within South region, which states drive the volume — and do any states show signs of margin weakness?
