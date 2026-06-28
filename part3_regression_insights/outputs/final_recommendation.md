# Final Recommendation
**For**: Retail Leadership Team  
**From**: Business Analyst  
**Subject**: What is really driving monthly sales across our stores?

---

## The Short Answer

After analysing 320 store-month records using regression analysis, three factors stand out as the most strongly associated with higher monthly sales:

1. **Footfall** — how many customers walk through the door
2. **Inventory availability** — whether the products customers want are actually in stock
3. **Customer rating** — how satisfied customers are with their experience

Marketing spend also matters, but has a smaller effect once you account for everything else. Discounting, surprisingly, does not appear to significantly improve sales.

---

## Which Factors Should Leadership Focus On?

### 1. Footfall — The Biggest Driver
Our model shows that every additional 1,000 monthly visitors is associated with roughly £33,650 more in monthly sales. This is by far the strongest relationship in the data.

**What this means for action**: Any strategy that brings more people through the door — better location marketing, events, partnerships with nearby businesses, or improved signage — is likely to have the highest return on investment.

### 2. Inventory Availability — Often Overlooked
Each 1% improvement in stock availability is associated with about £3,061 more in monthly sales. A store improving from 85% to 95% availability could expect roughly £30,000 more in monthly sales, everything else being equal.

**What this means for action**: Reviewing supply chain performance, reducing stockouts on high-demand products, and improving warehouse replenishment cycles could deliver significant sales improvement at relatively low cost.

### 3. Customer Rating — Quality Matters
A 1-point improvement in customer rating (on a 5-point scale) is associated with about £12,825 more in monthly sales. Stores rated 4.5 vs 3.5 could expect roughly £12,825 more per month.

**What this means for action**: Staff training, store cleanliness, and checkout efficiency improvements that lift customer satisfaction scores have a measurable sales payoff.

### 4. Regional Differences Are Real
South and West stores outperform East stores by approximately £18,000–£19,000 per month even after accounting for footfall, marketing, and other factors. This suggests there are structural or market differences between regions that are worth understanding — possibly stronger local demand, less competition, or better store positioning.

### 5. Residential Stores Underperform Malls
Residential store types sell about £29,394 less per month than Mall stores on average, even with similar footfall and marketing. This may reflect lower average basket sizes, different product mix needs, or weaker impulse purchasing behaviour in residential areas.

---

## Which Variables Should NOT Be Over-Interpreted?

### Discounting (avg_discount_pct)
The model shows discounts have a negative association with sales (higher discounts = lower sales), but this result is **not statistically significant** — meaning it could just be noise in the data. Do not use this model to conclude that discounting hurts sales. The relationship is unclear and needs more investigation.

### Airport Stores vs Malls
The model shows Airport stores perform similarly to Mall stores, but this variable is also not statistically significant. We cannot draw strong conclusions about airport vs mall performance from this dataset alone.

---

## Recommended Business Actions

| Priority | Action | Why |
|---|---|---|
| High | Investigate what drives footfall in top-performing stores and replicate | Footfall explains 73.6% of sales variation on its own |
| High | Audit inventory availability across all stores — target 90%+ | 1% improvement = ~£3,000 more sales per month |
| Medium | Launch customer experience improvement programme | 1-point rating increase = ~£12,825 more sales per month |
| Medium | Review East region store strategy — they underperform South and West | £18,000–£19,000 monthly gap vs other regions |
| Low | Investigate Residential store format — consider product mix changes | £29,394 monthly underperformance vs Mall stores |
| Ongoing | Visit West High Street stores showing large negative residuals | STR-1017 and STR-1014 significantly underperform predictions |

---

## Why Regression Shows Association But Not Causation

This is an important limitation. Regression tells us that footfall and sales tend to move together, or that stores with better inventory tend to have higher sales. But it cannot tell us for certain that one causes the other.

For example:
- High footfall stores might also happen to be in better locations with better product ranges — the location itself might be the real cause of both the footfall and the sales
- Customer ratings might be high because a store is already doing well financially and can afford better staff — not the other way around
- We are missing variables like local competition density, store age, and product range quality that could explain some of the relationships we see

To establish causation, you would need a controlled experiment — for example, deliberately increasing marketing spend in randomly selected stores while holding everything else constant, and measuring the result.

---

## Risks and Limitations

1. The dataset covers only 4 months (January–April 2025) — seasonal patterns beyond this window are unknown
2. 6 missing competitor_distance values and 8 missing customer_rating values were filled with median values — this introduces minor inaccuracy
3. The model explains 83.5% of sales variation, but 16.5% remains unexplained — there are factors we are not measuring
4. West High Street stores show systematic under-prediction — there may be a regional factor specific to this combination not captured in the data
5. Regression assumes a straight-line relationship between variables — if the true relationship is curved (e.g., sales plateau after a certain footfall level), the model will be less accurate at extremes
