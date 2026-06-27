# Part 3: Regression-Based Business Insights & Model Interpretation

## Business Problem Summary
The leadership team of a retail chain wants to understand what is driving monthly sales performance across stores. They are considering actions like increasing marketing spend, improving stock availability, changing discounting strategy, and reallocating staff. This analysis uses regression to identify which factors are most strongly associated with monthly sales.

---

## Dataset Description
- **File**: `data/business_regression_data.xlsx`
- **Rows**: 320 records (80 stores × 4 months)
- **Columns**: 14 fields

| Column | Type | Role |
|---|---|---|
| store_id | Text | Identifier — not used in regression |
| month | Date | Time reference — not used directly |
| region | Categorical | Converted to dummy variables |
| store_type | Categorical | Converted to dummy variables |
| marketing_spend | Numeric | Independent variable |
| footfall | Numeric | Independent variable (strongest driver) |
| avg_discount_pct | Numeric | Independent variable |
| staff_count | Numeric | Available but not included — low correlation |
| inventory_availability_pct | Numeric | Independent variable |
| competitor_distance_km | Numeric | 6 missing values — filled with median |
| holiday_flag | Binary (0/1) | Independent variable |
| customer_rating | Numeric | 8 missing values — filled with median |
| monthly_sales | Numeric | **Dependent variable (Y) — what we predict** |
| monthly_profit | Numeric | Outcome variable — not used as predictor |

---

## Regression Approach

Three models were built:

1. **Simple Regression 1** — marketing_spend → monthly_sales
2. **Simple Regression 2** — footfall → monthly_sales  
3. **Multiple Regression** — all 6 numeric variables + 6 dummy variables → monthly_sales

Each model was evaluated on R-Squared, coefficient significance (p-value), and business usefulness.

---

## Dummy Variable Approach

Two categorical variables were converted to dummy variables:

**Region** (reference category: East)
- region_North, region_South, region_West

**Store Type** (reference category: Mall)
- store_type_Airport, store_type_High Street, store_type_Residential

The reference category is the baseline. All other categories are compared against it.

---

## Model Comparison Summary

| Model | Variables | R-Squared | Recommended? |
|---|---|---|---|
| Simple — Marketing Spend | 1 variable | 16.7% | No |
| Simple — Footfall | 1 variable | 73.6% | Reference only |
| Multiple — Full Model | 13 variables | 83.5% | Yes ✓ |

---

## Final Model Selected

**Multiple Regression (Model 3)** — R-Squared = 83.5%

**Significant variables**: footfall, marketing_spend, inventory_availability_pct, customer_rating, holiday_flag, region_South, region_West, store_type_Residential

---

## Business Recommendation (Summary)

The three most actionable findings are:
1. **Footfall** is the strongest driver — strategies that bring more visitors have the highest ROI
2. **Inventory availability** has a large and significant effect — stockouts are costing sales
3. **Customer rating** matters — a 1-star improvement is worth ~£12,825 per month

Discounting does not appear to significantly drive sales in this model. East region stores and Residential store types underperform vs benchmarks and warrant review.

See `outputs/final_recommendation.md` for the full business recommendation.

---

## Assumptions and Limitations
1. Missing values (6 competitor_distance, 8 customer_rating) filled with median — minor impact
2. Dataset covers only 4 months — seasonal patterns beyond this window unknown
3. Regression shows association, not causation — controlled experiments needed to confirm
4. 16.5% of sales variation is still unexplained — unmeasured factors exist
5. Model assumes linear relationships — non-linear effects are not captured

---

## Screenshots Included

| File | Shows |
|---|---|
| `screenshots/simple_regression_output.png` | Scatter plots for both simple regression models |
| `screenshots/multiple_regression_output.png` | Multiple regression coefficient table |
| `screenshots/residuals_preview.png` | Residual scatter plot and top over/under-performers |
| `screenshots/model_comparison_preview.png` | Side-by-side model comparison table |
