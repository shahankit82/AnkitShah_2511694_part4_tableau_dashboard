# Chart Selection Justification — Executive Dashboard

## Design Principles Applied

Every chart in this dashboard was selected to answer a specific business question. The guiding principles were:

1. **One question per chart** — no chart tries to do two things at once
2. **Position encodes the most important dimension** — the most critical measure sits on the longest axis
3. **Colour encodes a second meaningful dimension** — not decoration, always data-driven
4. **Sort order reveals the answer** — bars are sorted so the takeaway is visible without reading labels
5. **Remove chart junk** — no 3D effects, no unnecessary gridlines, no decorative elements

---

## Chart 1: Sales Trend — Monthly Sales & Profit Trend (Line Chart)

**Screenshot reference:** sales_trend_view.png

**Business question answered:** How are total sales and profit changing month by month across 2024–2025?

**Why a line chart:**
Time-series data with a continuous date axis is the definitive use case for line charts. Lines allow the eye to follow the direction of change across 24 monthly data points — something bars cannot do as effectively at this granularity. The dual-axis approach (Sales on right axis, Profit on left) allows both measures to be read independently on their own scales.

**Field encodings used:**
- X-axis (Columns): Month of Order Date (continuous, truncated to month)
- Y-axis (Rows): Measure Values (SUM of Sales and SUM of Profit combined via Measure Names)
- Colour: Measure Names (blue = Profit, orange = Sales) — visible in the legend shown on the chart
- Filter: Region (dropdown filter visible on the right side showing All, East, North, South, West)

**Design principle applied:** The Region filter on this sheet allows leadership to see the trend for any individual region by selecting it — transforming a portfolio-level view into a regional diagnostic tool.

**Mistake avoided:** Did NOT use a bar chart for monthly time series. Bars emphasise individual period magnitude; lines emphasise trend direction. With 24 months of data, a bar chart would create 48 bars (24 × 2 measures) that would be unreadable. The line chart keeps it clean.

**What the chart reveals:** A clear seasonal dip in August (both years), strong September recovery, and broadly stable monthly sales between Rs 70–110 lakhs. Profit (blue line) tracks closely with sales, confirming no major margin shifts over time.

---

## Chart 2: Regional Performance (Horizontal Bar Chart, Colour-Encoded by Profit)

**Screenshot reference:** regional_performance_view.png

**Business question answered:** Which regions generate the most sales, and are they all profitable?

**Why a horizontal bar chart:**
Four regions comparing a single measure (sales) is the textbook bar chart use case. Horizontal layout is preferred here because it allows region names to display without rotation, and the bars read naturally left-to-right as "more sales = longer bar." Sorting by sales descending (South → North → East/West) makes rank immediately visible without reading the labels.

**Field encodings used:**
- Y-axis (Rows): Region (sorted by sales descending)
- X-axis (Columns): SUM(Sales) — the primary comparison metric
- Colour: SUM(Profit) — using a diverging red-to-green colour scale visible in the legend (198,512 to 425,271 range shown)
- Labels: Sales value shown at the end of each bar

**Design principle applied:** Colour is doing a second job here — it answers "is this region profitable?" without adding another axis or chart. The red-to-green scale means a regional manager can see both volume rank AND profit health in a single glance. All bars show green shades, confirming every region is profitable.

**Mistake avoided:** Did NOT use a pie chart for regional sales share. Pie charts cannot show absolute values alongside proportions, cannot be sorted, and are unreliable for comparing more than 3 slices. A horizontal bar chart shows all of this more clearly.

**What the chart reveals:** South leads at Rs 3.02M (scaled), North second at Rs 2.19M, East and West broadly equal around Rs 1.65M. All regions are in profit (all green). West is slightly lighter green than East, flagging its marginally lower profit despite similar sales — this is visible directly from the colour encoding.

---

## Chart 3: Category Profitability (Stacked Bar Chart with Sub-Category Colour and Average Reference Line)

**Screenshot reference:** category_profitability_view.png

**Business question answered:** How much profit does each category generate, and which sub-categories within each category drive or drag the total?

**Why a stacked bar chart:**
This chart answers two questions simultaneously: (1) which category has the highest total profit? and (2) within each category, which sub-categories contribute most? A stacked bar encodes both category total (bar height) and sub-category composition (stacked segments by colour) in one view.

**Field encodings used:**
- X-axis (Columns): Category (3 bars: Technology, Furniture, Office Supplies)
- Y-axis (Rows): SUM(Profit) — the primary business measure
- Colour: Sub-Category (12 colours, one per sub-category — visible in the legend: Accessories, Art, Binders, Bookcases, Chairs, Copiers, Labels, Machines, Paper, Phones, Storage, Tables)
- Labels: Profit values shown inside major segments (102,105 / 58,386 / 25,988 / 11,622 visible)
- Reference line: Average profit across categories (horizontal line labelled "Average" at ~80K)

**Design principle applied:** The Average reference line is critical — it allows a viewer to instantly see that Furniture and Office Supplies sit below the average, while Technology towers above it. Without this line, the visual gap between Technology and the others might be dismissed as "Technology is just bigger." With the line, it becomes clear that the other two categories are sub-average performers.

**Mistake avoided:** Did NOT use a pie chart for profit share. A pie would show Technology's dominance but hide the sub-category breakdown entirely. The stacked bar preserves both levels of information.

**What the chart reveals:** Technology profit (Rs 1.02 Cr from Accessories alone, Rs 58K from Phones visible) completely dominates. Furniture's segments are small and colourless relative to Technology. The reference line confirms both Furniture and Office Supplies are below-average profit contributors.

---

## Chart 4: Customer Segment View (Bar Chart, Colour-Encoded by Profit)

**Business question answered:** Which customer segment generates the most sales, and do margins differ across segments?

**Why a bar chart with colour encoding:**
Three customer segments comparing sales is a standard bar chart. The colour encoding (profit) adds a second question — "which segment is more profitable?" — without needing a second chart or a dual axis.

**Field encodings used:**
- X-axis (Columns): Customer Segment (Consumer, Corporate, Home Office)
- Y-axis (Rows): SUM(Sales)
- Colour: SUM(Profit) — diverging scale, darker = higher profit
- Labels: Sales value shown above each bar (373,104 / 565,366 / 646,889 visible in the dashboard)

**Design principle applied:** Colour as a profit signal means a viewer can answer "who makes us more money per sale?" just by looking at bar shade. No second chart, no table needed.

**What the chart reveals:** Home Office leads slightly (Rs 7.45 Cr), Consumer and Corporate close behind. All three are profitable (no red colours). Home Office has marginally stronger profit colour intensity, consistent with its 15.51% margin vs Corporate's 15.18%.

---

## Chart 5: Shipping Performance (Horizontal Bar, Colour by Ship Mode)

**Business question answered:** How does average delivery time vary by shipping mode, and which modes cause the longest delays?

**Why a horizontal bar chart:**
Ship modes (Same Day, First Class, Second Class, Standard Class, and the Shipping Delay Bucket groups) comparing average delivery days is a straightforward categorical comparison. Horizontal layout allows mode names to display cleanly without rotation.

**Field encodings used:**
- Y-axis (Rows): Shipping Delay Bucket (calculated field — groups delivery days into Same Day, 1 Day, 2–3 Days, 4–7 Days, 8+ Days)
- X-axis (Columns): AVG(Delivery Days)
- Colour: Ship Mode (First Class, Same Day, Second Class, Standard Class — four colours)
- Labels: Delivery day values shown at bar ends (0.000, 3.000, 2.000, 2.500, 5.833, 5.000, 8.133, 4.000 visible)

**Design principle applied:** Using the Shipping Delay Bucket calculated field as the Y-axis groups modes into meaningful service tiers rather than showing raw mode names. This makes the business interpretation (Same Day = fastest, 8+ Days = slowest) immediately obvious to a non-technical leadership audience.

**Mistake avoided:** Did NOT use a pie chart or donut to show delivery day distribution. Delivery speed is a quantitative measure — it has a natural order (faster is better) that pie charts cannot convey.

**What the chart reveals:** The "8+ Days" bucket shows values up to 8.133 days average. "Same Day" shows 0.000 (sub-day delivery). The colour coding reveals which ship mode dominates each delay bucket — Standard Class is concentrated in the longer delay categories.

---

## Chart 6: Discount vs Profit (Scatter Plot, Colour by Category, Size by Sales)

**Business question answered:** Is there a relationship between discount level and profitability — and where does profit turn negative?

**Why a scatter plot:**
A scatter plot is the only chart type that can show the relationship between two continuous variables (discount and profit) simultaneously across individual order-level data points. Each dot is one order. The downward trend is visible from the scatter distribution, and trend lines make it explicit.

**Field encodings used:**
- X-axis (Columns): AVG(Discount) — the independent variable
- Y-axis (Rows): SUM(Profit) — the outcome variable
- Colour: Category (Technology, Furniture, Office Supplies — three colours)
- Size: SUM(Sales) — larger circles = higher value orders
- Tooltip: Customer Segment — hovering reveals which segment placed the order
- Trend lines: Added per category (three coloured lines showing direction of relationship)

**Design principle applied:** The trend lines are the most important design decision here. Without them, the scatter might look like random noise to a business audience. With three per-category trend lines, the downward direction (more discount = less profit) is unmistakable, and the point where each line crosses zero on the Y-axis reveals the break-even discount level for each category.

**Mistake avoided:** Did NOT aggregate to a bar chart by discount band. Aggregation would hide the order-level variance — some 30% discount orders are still profitable (visible as dots above zero), while others at 20% are losses. The scatter preserves this nuance.

**What the chart reveals:** All three trend lines slope downward as discount increases. The lines converge at zero profit around 0.25–0.30 on the X-axis. Points above 0.30 cluster below zero — visually confirming that 30%+ discounts systematically produce losses.

---

## Chart 7: Return Analysis (Stacked Bar Chart, Colour by Customer Segment)

**Business question answered:** Which product categories have the most returns, and which customer segments are driving them?

**Why a stacked bar chart by segment:**
Returns analysis needs two dimensions: category (where returns happen) and segment (who is returning). A stacked bar answers both simultaneously — bar height shows total returns per category, and stack composition shows segment breakdown within each category.

**Field encodings used:**
- X-axis (Columns): Category (Technology, Furniture, Office Supplies)
- Y-axis (Rows): SUM(Return Flag) — count of returned orders
- Colour: Customer Segment (Consumer, Corporate, Home Office — three colours visible in legend)
- Labels: Return counts shown inside each segment stack (26, 25, 37 for Furniture segments visible)

**Design principle applied:** Sorting categories by total return count (Furniture first, then Office Supplies, then Technology) puts the most problematic category at the front — matching the principle that the most important information should be leftmost.

**Mistake avoided:** Did NOT use a rate (%) chart here — used raw counts. While rate would be needed for comparing categories of different sizes (Furniture has 1,147 orders, Technology has 1,384), the stacked count chart at this stage shows the absolute scale of the return problem in Furniture, which is the most actionable insight for leadership.

**What the chart reveals:** Furniture has 88 returns — the most of any category. Home Office (red) contributes 37 Furniture returns — the single largest segment-category combination. Technology has the fewest returns (42) despite having the second-highest order count.

---

## Dashboard Layout Decisions

**KPI Cards (top row):** Total Sales, Total Profit, Profit Margin, and Return Rate are placed first because they are the summary metrics leadership reads before any chart. They establish context ("this is a Rs 21.7 Cr business with 15.35% margins") before the analytical charts explain the detail.

**Top chart row (Sales Trend + Regional Performance):** These two answer the "what and where" strategic questions — time trend and geography. They are given the most horizontal space as the primary strategic views.

**Bottom chart row (Category Profitability, Customer Segment, Shipping Performance, Discount vs Profit, Return Analysis):** These are operational and diagnostic charts — read after the strategic overview provides context. They answer "why" and "what should we do."

**Colour palette consistency:**
- Profit encoded as colour: always uses the same red-green diverging palette (red = low/negative, green = high/positive)
- Segment colour: Consumer (blue), Corporate (orange), Home Office (red) — consistent across Customer Segment View and Return Analysis
- Category colour: consistent sub-category palette across Category Profitability
- This consistency means once a viewer learns the colour key on one chart, it applies to others — reducing cognitive load

**Filter placement:** Region filter is displayed on the Sales Trend sheet and is accessible from the dashboard. The dashboard filter action (clicking a region in Regional Performance filters all other charts) provides the interactive layer without cluttering the canvas with multiple filter controls.
