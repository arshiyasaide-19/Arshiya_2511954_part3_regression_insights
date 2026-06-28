# Model Comparison

Think of regression like trying to guess a store's monthly sales. Each model is a different "guess strategy" — some use just one clue, others use many.

---

## Model 1 — Simple Regression: Marketing Spend

**Question it answers**: Does spending more on marketing lead to higher sales?

**Variables**: marketing_spend → monthly_sales

**Equation**:
```
monthly_sales = 560,777 + 2.13 × marketing_spend
```

**What this means in plain English**:
- Every extra £1 spent on marketing is associated with about £2.13 more in monthly sales
- If a store spent £0 on marketing, the model predicts £560,777 in sales (theoretical baseline)

| Metric | Value | Plain English |
|---|---|---|
| R-Squared | 16.7% | Marketing spend explains about 1 in 6 sales differences between stores |
| P-Value | < 0.001 | This result is statistically reliable |
| Significant? | Yes | Marketing spend does matter |

**Limitation**: Marketing spend alone misses 83.3% of what drives sales differences. It's a useful clue, but not the full picture.

---

## Model 2 — Simple Regression: Footfall

**Question it answers**: Does having more customers walk into the store lead to higher sales?

**Variables**: footfall → monthly_sales

**Equation**:
```
monthly_sales = 446,411 + 35.68 × footfall
```

**What this means in plain English**:
- Every additional customer who walks into the store is associated with about £35.68 more in monthly sales
- This is a much stronger relationship than marketing spend

| Metric | Value | Plain English |
|---|---|---|
| R-Squared | 73.6% | Footfall alone explains nearly 3 out of 4 sales differences between stores |
| P-Value | < 0.001 | Highly statistically reliable |
| Significant? | Yes — strongly | Footfall is the most powerful single driver of sales |

**Limitation**: Even though footfall explains a lot, 26.4% of sales variation is still unexplained. Store type, region, marketing, and stock levels also matter.

---

## Model 3 — Multiple Regression: Full Model (Recommended)

**Question it answers**: When we look at all major factors together, which ones actually drive sales?

**Variables**: footfall + marketing_spend + inventory_availability_pct + avg_discount_pct + customer_rating + holiday_flag + region dummies + store type dummies → monthly_sales

**Equation**:
```
monthly_sales = 77,386
  + 33.65 × footfall
  + 1.19  × marketing_spend
  + 3,061 × inventory_availability_pct
  - 47,751 × avg_discount_pct
  + 12,825 × customer_rating
  + 13,859 × holiday_flag
  + 6,367  × region_North
  + 18,883 × region_South
  + 19,281 × region_West
  + 12,217 × store_type_Airport
  - 11,016 × store_type_High Street
  - 29,394 × store_type_Residential
```
(Reference categories: region = East, store_type = Mall)

| Metric | Value | Plain English |
|---|---|---|
| R-Squared | 83.5% | This model explains 83.5% of why sales differ across stores — very strong |
| Adjusted R-Squared | 83.1% | Still strong even after adjusting for the number of variables used |

### Which variables are statistically significant in Model 3?

| Variable | Significant? | Direction |
|---|---|---|
| footfall | Yes ✓ | More footfall = more sales |
| marketing_spend | Yes ✓ | More marketing = more sales |
| inventory_availability_pct | Yes ✓ | Better stock = more sales |
| customer_rating | Yes ✓ | Higher rating = more sales |
| holiday_flag | Yes ✓ | Holiday months = more sales |
| region_South vs East | Yes ✓ | South stores outsell East stores |
| region_West vs East | Yes ✓ | West stores outsell East stores |
| store_type_Residential vs Mall | Yes ✓ | Residential stores sell less than Malls |
| avg_discount_pct | No | Discounting does not significantly improve sales |
| region_North vs East | No | North and East perform similarly |
| store_type_Airport vs Mall | No | Airport and Mall perform similarly |
| store_type_High Street vs Mall | No | High Street and Mall perform similarly |

---

## Head-to-Head Comparison

| | Model 1 | Model 2 | Model 3 |
|---|---|---|---|
| Variables used | 1 | 1 | 13 |
| R-Squared | 16.7% | 73.6% | 83.5% |
| Easy to explain? | Very easy | Very easy | Moderate |
| Useful for decisions? | Limited | Good start | Best |
| Recommended? | No | As reference | Yes |

---

## Final Choice: Model 3

Model 3 is the recommended model because it gives leadership the most complete and accurate picture of what drives monthly sales. It is not perfect — 16.5% of sales variation is still unexplained — but it is far more useful than looking at any single factor in isolation.
