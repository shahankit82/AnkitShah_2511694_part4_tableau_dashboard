# Chart Selection Justification — Executive Dashboard

## Design Principles Applied

This dashboard was built around four core visualisation principles:
1. **Answer one question per chart** — no chart does double duty
2. **Encode the most important dimension with position** (x/y axis), not colour
3. **Use colour sparingly and meaningfully** — only for categorical grouping or conditional status (green/amber/red)
4. **Remove chart junk** — no 3D effects, no gridlines on clean charts, no unnecessary legends

---

## Chart 1: Monthly Sales & Profit Trend

**Question answered:** How are sales and profit changing month-over-month over 2024–2025?

**Chart type chosen:** Dual-line chart with area fill

**Why this type:**
- Time-series data with two related measures (sales, profit) is the canonical use case for line charts
- The area fill emphasises volume magnitude while the line shows trend direction
- Lines allow direct comparison of two series on the same axis without the visual clutter of grouped bars

**Field encoding:**
- X-axis: Order Date (truncated to Month)
- Y-axis: SUM(Sales) and SUM(Profit) — dual axis
- Colour: Fixed (Blue for Sales, Green for Profit) — colour used to distinguish series, not encode data

**Design principle applied:** Pre-attentive processing — the eye naturally follows lines, making trend visible without reading axis values

**Mistake avoided:** Did NOT use a bar chart for this time series (bars emphasise individual period magnitude over trend; harder to see direction of change across 24 months)

---

## Chart 2: Sales & Profit by Region

**Question answered:** Which regions generate the most sales and profit — and does the relative share differ?

**Chart type chosen:** Horizontal bar chart (sorted by sales)

**Why this type:**
- Categorical comparison (4 regions) with a single measure is the textbook bar chart use case
- Horizontal orientation allows long region names to display without rotation
- Sorting from highest to lowest makes rank immediately apparent without reading labels

**Field encoding:**
- Y-axis: Region (dimension)
- X-axis: SUM(Sales) — primary bar
- Overlapping bar: SUM(Profit) — shows profit in the same space
- Colour: Consistent (Blue = Sales, Green = Profit)

**Design principle applied:** Gestalt proximity — placing sales and profit bars side-by-side for each region allows immediate within-region comparison

**Mistake avoided:** Did NOT use a pie chart for regional share — pie charts are unreliable for comparing more than 3 slices and cannot show absolute values alongside proportions

---

## Chart 3: Profit Margin by Category

**Question answered:** Which categories are delivering acceptable margins, and which are underperforming?

**Chart type chosen:** Single bar chart with conditional colour (green/amber/red)

**Why this type:**
- Only 3 categories — a bar chart is clearest for small-cardinality comparisons
- Conditional colour (green if margin >15%, amber if >5%, red if below) encodes the status signal without requiring the reader to interpret the axis

**Field encoding:**
- X-axis: Category (dimension)
- Y-axis: AVG(Profit Margin) as percentage
- Colour: Calculated field "Margin Status" driving green/amber/red
- Reference line: Company-wide average margin (dashed line)

**Design principle applied:** Colour as a pre-attentive signal — Furniture's orange/amber bar immediately draws the eye before the reader processes the value

**Mistake avoided:** Did NOT use a line chart (categories are not ordered dimensions — a line would imply a trend between Furniture → Office Supplies → Technology that doesn't exist)

---

## Chart 4: Discount vs Profit (Scatter Plot)

**Question answered:** Is there a visible relationship between discount level and profitability — and where is the loss threshold?

**Chart type chosen:** Scatter plot with colour by Discount Band

**Why this type:**
- A scatter plot is the only chart type that can reveal correlation between two continuous variables simultaneously
- Individual order points show the true distribution of outcomes (not just averages)
- Colour by Discount Band adds a third dimension without adding another axis

**Field encoding:**
- X-axis: Discount (continuous, 0–50%)
- Y-axis: Profit (continuous)
- Colour: Discount Band (calculated field)
- Shape: Category (to show if the pattern differs by product type)
- Reference line: Profit = 0 (horizontal line marking loss boundary)

**Design principle applied:** Visual hierarchy — the zero-profit reference line is the most important element, drawn first; all scatter points are read relative to it

**Mistake avoided:** Did NOT aggregate to averages only — showing individual order scatter reveals the variance (some 30% discount orders are still profitable; it's the average that crosses zero, not every order)

---

## Chart 5: Avg Delivery Days by Ship Mode

**Question answered:** Which shipping modes deliver faster, and how much speed difference is there?

**Chart type chosen:** Horizontal bar chart with colour coding (green/amber/red by speed)

**Why this type:**
- 4 ship modes comparing a single measure (average delivery days)
- Horizontal layout reads naturally as "speed" — shorter bar = faster
- Colour coding (green for ≤2 days, amber 2-4, red >4) adds status signal without text

**Field encoding:**
- Y-axis: Ship Mode (dimension)
- X-axis: AVG(Delivery Days)
- Colour: Calculated speed status

**Design principle applied:** Spatial metaphor — shorter bar = faster delivery is intuitively understood

**Mistake avoided:** Did NOT use a pie chart or donut chart — delivery speed is a quantitative measure, not a proportion; pie charts only work for parts-of-a-whole

---

## Chart 6: Return Rate by Category & Segment

**Question answered:** Which category-segment combinations have the highest return rates, and does return behaviour differ by who is buying?

**Chart type chosen:** Grouped bar chart (Category on X, bars grouped by Segment)

**Why this type:**
- Two categorical dimensions (category × segment) with one measure (return rate)
- Grouped bars allow within-category cross-segment comparison and cross-category level comparison simultaneously
- A heatmap would work but bar heights make magnitude comparison easier for a leadership audience

**Field encoding:**
- X-axis: Category
- Y-axis: Return Rate %
- Colour: Customer Segment (3 colours, one per segment)
- Reference line: Company-wide average return rate

**Design principle applied:** Comparison clarity — bars side by side within a group are easier to compare than bars in separate chart panels

**Mistake avoided:** Did NOT use stacked bars — stacked bars cannot show within-segment return rates clearly (the stacking combines what we want to compare)

---

## Chart 7: Sub-Category Profit (Horizontal Bar, Sorted)

**Question answered:** Which specific sub-categories are profitable and which are loss-making?

**Chart type chosen:** Horizontal diverging bar chart (sorted by profit, green/red colouring)

**Why this type:**
- 13 sub-categories is too many for a vertical bar chart (label overlap)
- Horizontal layout accommodates sub-category name labels cleanly
- Diverging from the zero-line makes profitable vs loss-making sub-categories immediately separable
- Sorting by profit level puts the biggest problems at the top (or bottom) visually

**Field encoding:**
- Y-axis: Sub-Category (sorted by profit ascending — worst at top)
- X-axis: SUM(Profit) — diverging from 0
- Colour: Green if profit >0, Red if profit <0

**Design principle applied:** Pre-attentive colour separation — red bars requiring attention appear before the reader processes the sub-category names

**Mistake avoided:** Did NOT use alphabetical sorting — sorting alphabetically would bury the most important insight (which sub-categories lose money) among a visual equal distribution of bars

---

## Dashboard Layout Decisions

### KPI Cards (Top Row)
Placed at the top as the first thing leadership reads — Total Sales, Total Profit, Total Orders, Return Rate. Each KPI uses a single bold number, a secondary context metric, and a colour-coded card background. No chart is needed — single-number KPIs are their own visual.

### Trend Charts (Second Row — Wide)
Sales trend and regional performance are given the most horizontal space because they are the primary strategic questions: "How are we performing over time?" and "Where are we winning geographically?"

### Analytical Charts (Third/Fourth Row)
Category, Discount, Shipping, and Returns are placed in the lower panels as operational/diagnostic charts — read after the strategic overview establishes context.

### Filter Placement
Six filters (Region, Category, Segment, Ship Mode, Campaign Channel, Date Range) placed in the header bar so they are always visible and do not consume dashboard chart space. Interactive filters apply to all sheets simultaneously via a filter action.

### Color Palette
- **Blue (#1E3A5F, #1565C0)**: Sales and primary measures
- **Green (#2E7D32)**: Profit and positive outcomes
- **Red (#C62828)**: Losses, high return rates, risks
- **Amber (#F9A825)**: Warning/watch items
- **Consistent across all charts** — the same colour always means the same thing throughout the dashboard

### Avoided Mistakes
- No 3D charts of any type
- No pie charts for comparisons
- No dual-axis chart that makes the axes confusing (only used where both measures share the same conceptual scale)
- No chart with >7 series (cognitive overload)
- No axis truncation (all bars start at zero to avoid distortion)
