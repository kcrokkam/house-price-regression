# House Price Prediction | Linear Regression

An end-to-end machine learning project predicting residential property prices using the King County housing dataset.

## Project Overview

The objective is to investigate how property characteristics and location influence house prices and develop an interpretable regression model that generalizes to unseen properties.

The project explores feature selection, exploratory data analysis, regression diagnostics, regularization, categorical encoding, and model evaluation.

## Dataset

- **Dataset:** King County House Sales
- **Observations:** 21,613 property-sale records
- **Target:** Sale price (`price`)
- **Features:** Living area, bedrooms, bathrooms, construction grade, condition, view, waterfront access, construction year, and ZIP code

The dataset is stored in `Data/kc_house_data.csv`.

**Source:** [House Sales in King County, USA — Kaggle](https://www.kaggle.com/datasets/harlfoxem/housesalesprediction)

**Dataset License:** CC0 — Public Domain

## Methodology

1. Explored property prices and relationships between predictor variables.
2. Established simple and multiple Linear Regression baselines.
3. Examined residuals, correlated features, and training versus test errors.
4. Experimented with Ridge (L2) and Lasso (L1) regularization.
5. Expanded the feature set to include property quality and characteristics.
6. Used one-hot encoding to represent ZIP codes as categorical variables.
7. Compared candidate models on validation data.
8. Selected ordinary Linear Regression and evaluated it on a reserved test set.

Property IDs were grouped during splitting to prevent sales of the same property from appearing across training, validation, and test datasets.

## Results

### Validation performance

| Model | MAE | R² |
|---|---:|---:|
| Linear Regression — 4 features | $167,256.63 | 0.5382 |
| Linear Regression — 8 features | $140,637.23 | 0.6567 |
| Linear Regression — 8 features + ZIP code | $97,198.34 | 0.8271 |

Adding ZIP code reduced validation MAE by approximately **30.9%** compared with the eight-feature model.

### Final test performance

| Metric | Result |
|---|---:|
| Mean Absolute Error (MAE) | $97,467.15 |
| Root Mean Squared Error (RMSE) | $165,088.18 |
| R² | 0.8049 |

The final model used Linear Regression with one-hot-encoded ZIP codes, refitted on the combined training and validation observations.

## Key Findings

- Location information substantially improved predictive performance.
- Property size alone was insufficient to explain house-price differences.
- Ridge regularization provided minimal improvement over ordinary Linear Regression in the tested configurations.
- Lasso demonstrated automatic feature selection by shrinking some coefficients to zero.
- Residual analysis revealed greater variability in prediction errors for higher-priced properties.

## Technologies

Python, Pandas, NumPy, Matplotlib, Scikit-learn, and Jupyter Notebook.

## Repository Structure

```text
house-price-regression/
├── Data/
│   └── kc_house_data.csv
├── regression.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

## Limitations

- Prediction errors remain substantial for some properties, especially at higher price ranges.
- ZIP codes provide geographic information but do not capture all location-specific differences.
- The dataset was explored repeatedly during the learning process, so final test performance should be interpreted as an educational benchmark rather than an entirely independent external evaluation.
- This project demonstrates regression modeling techniques and is not a production property-appraisal system.

## Learning Outcomes

This project demonstrates practical understanding of Linear Regression, feature engineering, regularization, residual diagnostics, model validation, and the tradeoffs between predictive accuracy, complexity, and interpretability.