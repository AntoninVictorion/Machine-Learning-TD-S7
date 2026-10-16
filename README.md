# Lab 5 – Machine Learning Challenge: Air Quality Prediction

EFREI – Lab 5 (Malika Charrad)

## Goal

Predict air quality from pollutant sub-indexes, using the `global_air_pollution.xlsx` dataset (23,463 rows × 12 columns):

- **Regression**: predict the numeric `AQI Value`.
- **Classification**: predict the `AQI Category` (Good, Moderate, Unhealthy for Sensitive Groups, Unhealthy, Very Unhealthy, Hazardous).

## Project structure

The notebook is organized in the same order as the assignment:

1. **Part 1 – Preprocessing**: data understanding, cleaning, encoding, feature selection, train/test split, normalization.
2. **Part 2 – Regression**: Linear Regression, Decision Tree Regressor, Random Forest Regressor.
3. **Part 3 – Classification**: Logistic Regression, Decision Tree, Random Forest, Perceptron, MLP Classifier.
4. **Conclusion**: comparison of all models, strengths and limitations, effect of complexity, recommendations.

## Setup

- Python environment: conda environment `ml_tp`
- Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `openpyxl`

```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl
```

Place `global_air_pollution.xlsx` in the same folder as the notebook, then run all cells from top to bottom.

## Main choices

- **Features (4)**: `CO AQI Value`, `Ozone AQI Value`, `NO2 AQI Value`, `PM2.5 AQI Value`.
- `AQI Value` is excluded from the classification features (data leakage: the category is derived from it).
- **Missing values**: only in `Country` and `City`, replaced by `"Unknown"` (these columns are not used as predictors).
- **Outliers**: kept, since they are real measurements of very polluted cities and are needed to learn the rare classes.
- **Target encoding**: ordinal, following severity (Good = 0 … Hazardous = 5).
- **Split**: 80/20, stratified on `AQI Category`, `random_state=42`.
- **Normalization**: `StandardScaler` fitted on the train set only. Used for Linear/Logistic Regression, Perceptron and MLP. Trees and forests use the original values.

## Main results (test set)

| Task | Best model | Results |
|---|---|---|
| Regression | Random Forest | R² = 0.998, RMSE = 2.58, MAE = 0.22 |
| Classification | Decision Tree / Random Forest | Accuracy ≈ 0.999, macro-F1 ≈ 0.99 |

Other findings:

- Tree-based models clearly beat linear models: the AQI is the maximum of the sub-indexes and the categories follow fixed thresholds (50, 100, 150, ...).
- The Perceptron is the worst model (macro-F1 = 0.46); the MLP with two hidden layers reaches macro-F1 = 0.97.
- No harmful overfitting: the limiting factor was bias, not variance.
- Weak points: AQI > 300 and the rare classes `Very Unhealthy` and `Hazardous`.

## Limitations

- The target is almost a deterministic function of the input sub-indexes, so these scores do not represent real air quality forecasting.
- Only one split and one random seed were tested (no cross-validation).
- Some inconsistencies between values and categories were observed in the data but not corrected.