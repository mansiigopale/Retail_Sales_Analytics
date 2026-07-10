# Retail Sales Analytics — Project Review Business Problem



Sales across the business looked healthy overall, but profit performance was inconsistent.
I set out to analyze the underlying transaction data to find out where — and why —
profitability was breaking down, using Python for cleaning and exploratory analysis, SQL
for structured business-question analysis, and Power BI for an interactive dashboard.



## Headline Numbers

* Total Sales: **$2.30M**
* Total Profit: **$286,397**
* Overall Profit Margin: **12.47%**
* Total Orders: **9,994**



## Key Finding 1: Sales are balanced across categories, but profit is not

Total Sales are nearly even across all three categories — Furniture ($252.61K, 34.82%),
Technology ($251.99K, 34.74%), and Office Supplies ($220.85K, 30.44%). On revenue alone,
all three categories appear to be performing similarly.

Profit tells a completely different story. Of the $286,397 total profit:

* Technology: $145,454.95 (50.8%)
* Office Supplies: $122,490.80 (42.8%)
* Furniture: $18,451.27 (only 6.4%)



Furniture generates roughly a third of total sales but contributes only a fraction of the
profit — a gap that a sales-only view would have completely missed.

**Key Takeaway:**

* "Sales were almost perfectly split three ways across categories, but profit wasn't even close — Furniture generated about a third of total sales but only 6% of total profit.
* That gap is exactly the kind of insight a sales dashboard alone would hide, and it's what led me to dig into Furniture's Sub-Categories specifically."



## Key Finding 2: Tables and Bookcases are the only Sub-Categories losing money

Breaking Furniture down further, I found that across all 17 Sub-Categories in the dataset,
Tables and Bookcases are the only two operating at a net loss. Every other Sub-Category —
Copiers, Phones, Accessories, Paper, Binders, Chairs, Storage, Appliances, Furnishings,
Envelopes, Art, Labels, Machines, Fasteners, and Supplies — is profitable, with Copiers the
strongest individual contributor.

This finding explains Finding 1 directly: Furniture's weak profit isn't a category-wide
issue, it's concentrated in two specific Sub-Categories.

**Key Takeaway:**

* "Once I saw Furniture's profit was disproportionately low, I broke it down by Sub-Category and found Tables and Bookcases were the only two losing money in the entire dataset.
* That turned a vague 'Furniture underperforms' observation into a specific, actionable finding."



## Key Finding 3: Discounting is the likely driver of those losses

Looking at average profit by discount band, profit stays positive under No Discount and Low
Discount (0–20%), softens in the Medium band (20–40%), and turns sharply negative in the
High band (40%+). This pattern lines up with Finding 2 — Tables and Bookcases are plausibly
being discounted aggressively enough to erase their margin entirely.

**Key Takeaway:**

* "The discount-band analysis showed average profit declining steadily as discount increased, and turning clearly negative at the highest discount levels. 
* Combined with the Sub-Category finding, my conclusion was that Tables and Bookcases were likely being discounted more heavily than their margins could support — a concrete, testable
recommendation rather than just a surface-level observation."



## Key Finding 4: A small number of states drive most of the profit

California and New York are by far the strongest profit contributors, each generating
roughly double the profit of the next-highest state, Washington. Profit then tapers off
steadily through Michigan, Virginia, Indiana, Georgia, and the remaining states, each
contributing comparatively modest amounts.

**Key Takeaway:**

* "Profit wasn't evenly spread across states — California and New York alone accounted for a disproportionately large share, roughly double the third-place state. That kind of concentration is useful for a business deciding where to focus regional resources."



## Key Finding 5: Consumer segment drives the largest share of profit

By Segment, Consumer contributes $134,119.21 (46.83%) of total profit, ahead of Corporate
($91,979.13, 32.12%) and Home Office ($60,298.68, 21.05%). Consumer isn't just the largest
segment by volume — it's the clear leader on profit contribution as well, while Home Office
lags noticeably behind the other two.

**Key Takeaway:**

* "Consumer was both the largest segment and the most profitable by a clear margin, which makes it the segment most worth protecting, while Home Office's comparatively weak 

&#x20;   contribution is worth investigating further."



## Key Finding 6: West region leads on both sales and profit

Among the four regions, West shows the highest total sales and total profit, followed by
East, with Central and South comparatively lower on both measures — indicating regional
performance tracks fairly consistently between revenue and profitability, unlike the
category-level split seen in Finding 1.



## Recommendations

1. **Review discount policy for Tables and Bookcases specifically** — these are the only
Sub-Categories operating at a loss, and the discount-band pattern points to aggressive
discounting as a likely cause.
2. **Investigate Furniture's weak profit performance despite strong sales** — since it's
driven almost entirely by two Sub-Categories, a targeted fix should be more effective
than a category-wide change.
3. **Prioritize California and New York in regional planning**, given their outsized share
of total profit relative to every other state.
4. **Protect and grow the Consumer segment**, the strongest profit contributor, while
reviewing why Home Office underperforms relative to Consumer and Corporate.



## Tools \& Methodology

* **Python (Pandas, NumPy, Matplotlib, Seaborn):** cleaned the dataset (removed duplicates,
converted Postal Code to a text identifier) and engineered features including Profit
Margin % and Discount Band, then conducted exploratory analysis to surface the patterns
above.
* **SQL (SQLite):** solved 15+ business questions using GROUP BY, CASE WHEN, HAVING, window
functions, and CTEs to analyze profitability by Category, Sub-Category, State, and Region.
* **Power BI:** built an interactive dashboard with KPI cards, a Category × Segment profit
matrix, and Region/State/Discount Band visuals, using DAX measures for Total Sales, Total
Profit, Profit Margin %, and Average Profit, with slicers for Region, Category, and
Segment.

