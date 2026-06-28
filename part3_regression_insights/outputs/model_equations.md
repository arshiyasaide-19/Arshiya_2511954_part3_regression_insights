# Model Equations

## How to Read a Regression Equation

A regression equation is just a recipe. It takes what we know about a store (how many visitors it gets, how much it spends on marketing, etc.) and uses that to estimate what its monthly sales should be.

```
monthly_sales = starting_point + (factor1 × value1) + (factor2 × value2) + ...
```

The number next to each factor (called the **coefficient**) tells you: "if this factor goes up by 1, how much does sales change?"

---

## Simple Regression Equation 1 — Marketing Spend

```
monthly_sales = 560,777 + 2.13 × marketing_spend
```

**Coefficients explained**:
- **560,777** (intercept): The theoretical baseline — predicted sales if marketing spend were zero. Not realistic on its own, just the starting point of the math.
- **2.13** (marketing_spend coefficient): For every £1 extra spent on marketing, monthly sales go up by about £2.13. So spending £10,000 more on marketing is associated with roughly £21,300 more in sales.

**R-Squared: 16.7%** — Marketing spend alone explains about 1 in 6 sales differences between stores.

---

## Simple Regression Equation 2 — Footfall

```
monthly_sales = 446,411 + 35.68 × footfall
```

**Coefficients explained**:
- **446,411** (intercept): Theoretical baseline sales with zero footfall.
- **35.68** (footfall coefficient): Every additional customer visiting the store is associated with about £35.68 more in monthly sales. A store with 1,000 more monthly visitors than another would be expected to sell around £35,680 more.

**R-Squared: 73.6%** — Footfall alone explains nearly 3 out of 4 sales differences. This is the strongest single factor.

---

## Multiple Regression Equation — Full Model (Recommended)

```
monthly_sales =
    77,386                              (baseline)
  + 33.65  × footfall
  +  1.19  × marketing_spend
  + 3,061  × inventory_availability_pct
  - 47,751 × avg_discount_pct
  + 12,825 × customer_rating
  + 13,859 × holiday_flag
  +  6,367 × region_North
  + 18,883 × region_South
  + 19,281 × region_West
  + 12,217 × store_type_Airport
  - 11,016 × store_type_High Street
  - 29,394 × store_type_Residential
```

---

## What Each Coefficient Means

| Variable | Coefficient | Plain English |
|---|---|---|
| footfall | +33.65 | Each extra visitor = +£33.65 in sales |
| marketing_spend | +1.19 | Each extra £1 marketing = +£1.19 in sales |
| inventory_availability_pct | +3,061 | Each 1% better stock availability = +£3,061 in sales |
| avg_discount_pct | -47,751 | Each 1 unit increase in discount = -£47,751 in sales (not statistically significant — don't over-interpret) |
| customer_rating | +12,825 | Each 1-star improvement in rating = +£12,825 in sales |
| holiday_flag | +13,859 | Holiday months bring in ~£13,859 more than non-holiday months |

---

## Dummy Variable Explanation

Some of our data is categorical — meaning it's a label, not a number (like "North", "South", "Mall", "Airport"). Regression needs numbers, so we convert these into 0/1 columns called **dummy variables**.

**How it works**:
- We pick one category as the "reference" (the baseline to compare against)
- We create a separate 0/1 column for every other category
- A value of 1 means "yes, this store is this type"; 0 means "no"

### Region Dummy Variables

| Column | Meaning | Reference Category |
|---|---|---|
| region_North | 1 = North store, 0 = not | East (baseline) |
| region_South | 1 = South store, 0 = not | East (baseline) |
| region_West | 1 = West store, 0 = not | East (baseline) |

**Reference category: East region**

So when we say "region_South coefficient = +18,883", it means: "South stores sell about £18,883 more per month than East stores, everything else being equal."

### Store Type Dummy Variables

| Column | Meaning | Reference Category |
|---|---|---|
| store_type_Airport | 1 = Airport store, 0 = not | Mall (baseline) |
| store_type_High Street | 1 = High Street store, 0 = not | Mall (baseline) |
| store_type_Residential | 1 = Residential store, 0 = not | Mall (baseline) |

**Reference category: Mall store type**

So "store_type_Residential coefficient = -29,394" means: "Residential stores sell about £29,394 less per month than Mall stores, everything else being equal."

---

## Final Model Selected

**Model 3 — Multiple Regression** is the selected final model.

**Why**:
1. It has the highest R-Squared (83.5%) — it explains the most sales variation
2. It uses all available meaningful factors, not just one
3. It separates the effect of each variable while holding others constant — giving more reliable insights
4. It correctly handles categorical variables like region and store type through dummy variables

**Key limitation**: A higher R-Squared does not mean the model is perfect. 16.5% of sales variation is still unexplained, and the model shows association — not proven cause and effect.
