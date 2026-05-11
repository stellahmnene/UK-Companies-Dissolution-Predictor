# UK-Companies-Dissolution-Predictor" 

An end-to-end data science project predicting whether a UK company will 
dissolve using structural and behavioural features collected from the 
Companies House Public Data API.

## Results

| Model | CV AUC | Test AUC | Test Accuracy |
|---|---|---|---|
| Logistic Regression | 0.980 | 0.974 | 95.6% |
| Random Forest | 0.981 | 0.961 | 95.6% |
| XGBoost | 0.981 | 0.961 | 93.1% |

**Key finding:** A linear model matched ensemble performance, suggesting 
the relationship between company structure and dissolution is largely 
linear and interpretable.

## Project Structure

| Notebook | Description |
|---|---|
| `ch_pipeline.ipynb` | Data collection from Companies House API across 5 endpoints |
| `ch_eda.ipynb` | Exploratory analysis, feature engineering and cleaning |
| `ch_modelling.ipynb` | Model training, evaluation and SHAP explainability |


## Features Engineered

- Officer count and turnover rate
- Filing frequency and history
- Financial charge count and satisfaction rate
- Ownership complexity (PSC structure)
- Company age, type and industry sector
- Geographic region
- SIC code missing flag


## Setup

1. Clone the repository
2. Install dependencies:
```bash
pip install requests pandas scikit-learn xgboost shap matplotlib seaborn python-dotenv
```
3. Get a free API key from the [Companies House Developer Portal](https://developer.company-information.service.gov.uk)
4. Create a `.env` file in the project folder:
5. 5. Run notebooks in order:
   - `ch_pipeline.ipynb` — collect data
   - `ch_eda.ipynb` — explore and clean
   - `ch_modelling.ipynb` — model and explain

> **Note:** The dataset CSV files are included so you can run the EDA 
> and modelling notebooks without needing an API key.


## Tech Stack
Python, pandas, scikit-learn, XGBoost, SHAP, matplotlib, seaborn, REST APIs

## Data Source
[Companies House Public Data API](https://developer-specs.company-information.service.gov.uk/companies-house-public-data-api/reference)

## Status
Work in progress — awaiting survival analysis and API deployment.
