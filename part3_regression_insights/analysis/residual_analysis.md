# Residual Analysis

## What is a Residual?

A residual is simply the gap between what actually happened and what our model predicted.

```
Residual = Actual Sales − Predicted Sales
```

- **Positive residual** → The store sold MORE than the model expected. Something good happened that our model didn't fully capture.
- **Negative residual** → The store sold LESS than the model expected. Something dragged sales down that our model didn't fully capture.
- **Residual close to zero** → The model predicted this store's sales very accurately.

---

## Top 5 Stores That Outperformed Predictions (Positive Residuals)

These stores sold significantly more than our model expected:

| Store ID | Region | Store Type | Actual Sales | Predicted Sales | Residual |
|---|---|---|---|---|---|
| STR-1028 | East | Mall | £713,611 | £599,810 | +£113,801 |
| STR-1073 | East | Residential | £813,317 | £717,037 | +£96,279 |
| STR-1069 | West | High Street | £686,738 | £593,783 | +£92,955 |
| STR-1050 | North | Residential | £735,787 | £643,121 | +£92,665 |
| STR-1030 | West | Residential | £820,519 | £729,914 | +£90,605 |

**What this might mean in business terms**:
- These stores may have a particularly strong local customer base or loyal repeat shoppers not captured in the data
- They could have had a successful local event, promotion, or seasonal spike that the model doesn't know about
- Strong store management or staff quality might be contributing — something we cannot measure with the current data
- These stores are worth visiting or interviewing to understand what they are doing differently

---

## Top 5 Stores That Underperformed Predictions (Negative Residuals)

These stores sold significantly less than our model expected:

| Store ID | Region | Store Type | Actual Sales | Predicted Sales | Residual |
|---|---|---|---|---|---|
| STR-1017 | West | High Street | £685,379 | £857,239 | -£171,860 |
| STR-1023 | South | Mall | £627,172 | £770,047 | -£142,875 |
| STR-1012 | West | Residential | £595,468 | £714,025 | -£118,558 |
| STR-1007 | West | Mall | £800,452 | £909,725 | -£109,274 |
| STR-1014 | West | High Street | £463,534 | £563,050 | -£99,515 |

**What this might mean in business terms**:
- These stores have good footfall and marketing investment on paper, but the sales are not converting — there may be a product mix issue or staff performance issue
- STR-1017 and STR-1014 are both West High Street stores — this pattern of underperformance in that combination is worth investigating specifically
- External factors like nearby competitor openings, local infrastructure changes (roadworks, closures), or poor product availability on key days could be responsible
- These stores are candidates for a business review or store visit

---

## Is the Model Over-Predicting or Under-Predicting Certain Store Types?

Looking at where the largest residuals cluster:

- **West High Street stores** appear disproportionately in the negative residuals list — the model consistently over-predicts their sales. This suggests High Street stores in the West region may face challenges (stronger local competition, lower foot traffic quality) that the model does not fully capture.
- **East and North stores** appear in the positive residuals — the model tends to under-predict their performance, suggesting there may be positive local factors in those regions not captured in the data.
- **Residential stores** appear in both lists — some over-perform, some under-perform — suggesting this store type has the most variability and is hardest to predict.

---

## Summary

| Observation | Business Implication |
|---|---|
| Model explains 83.5% of sales variation | Good — but 16.5% is still unexplained |
| Largest positive residuals are in East and North | Investigate these stores for best practices to replicate |
| Largest negative residuals are mostly in West | Investigate operational issues, competition, or product problems |
| West High Street stores consistently underperform model predictions | May need a dedicated West High Street strategy review |
