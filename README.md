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

## Key Learnings

- **Simpler models can match complex ones** — Logistic Regression matched 
  Random Forest and XGBoost on this dataset, reinforcing that model 
  complexity should be justified by performance.
- **Feature engineering matters more than model choice** — the cleaning 
  and engineering work in the EDA stage (region consolidation, SIC missing 
  flag, officer turnover rate) had more impact on performance than 
  switching between models
- **API data is messy** — region labels like `Co Antrim`, `Co. Antrim` 
  and `County Antrim` all mean the same thing but required significant 
  cleaning before being useful
- **SHAP over built-in importance** — built-in feature importance scores 
  don't show direction or individual prediction contributions; SHAP is 
  more rigorous and more useful for explaining model decisions
- **Sampling strategy affects everything** — deliberately balancing 
  classes produces a cleaner modelling problem but creates a distribution 
  mismatch with the real world that would need addressing before deployment
- **Security from the start** — storing API keys in `.env` files rather 
  than notebooks prevents accidental exposure when pushing to GitHub
