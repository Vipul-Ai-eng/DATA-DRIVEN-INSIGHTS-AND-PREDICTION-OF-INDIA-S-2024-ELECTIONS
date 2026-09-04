# Data-Driven Insights and Prediction of India's 2024 Elections

A machine learning project that digs into constituency-level data from India's 2024 Lok Sabha elections to understand what actually drives a candidate's win or loss, and to build a model that can predict the outcome based on measurable, pre-election factors like assets, criminal history, education, and past electoral performance.

The idea started from a simple question - how much of an election result can be explained by numbers alone, without touching sentiment, campaigning, or last-minute politics? Turns out, quite a lot.

---

## What this project does

- Scrapes and compiles constituency and candidate-level data for the 2024 elections
- Cleans and preprocesses the raw data into a model-ready format
- Runs exploratory data analysis to surface patterns in candidate demographics, financial disclosures, and electoral history
- Engineers features from raw fields (assets, liabilities, education, criminal cases, past win/loss records, etc.)
- Trains a Random Forest classifier to predict win/loss outcomes at the candidate level
- Tunes hyperparameters to squeeze out generalization performance rather than just training accuracy
- Visualizes the whole pipeline — 16 plots covering distributions, correlations, feature importance, and model diagnostics

---

## Results

| Metric | Score |
|---|---|
| Accuracy | 94.69% |
| ROC-AUC | 99.69% |

The high ROC-AUC alongside strong accuracy suggests the model isn't just memorizing the majority class — it's genuinely separating winners from losers across a wide probability threshold range. Feature importance analysis (inside the notebook) breaks down exactly which candidate attributes carry the most predictive weight.

---

## Repository structure

```
.
├── DATA-DRIVEN INSIGHTS AND PREDICTION OF INDIA'S 2024 ELECTIONS.ipynb   # Main analysis + modeling notebook
├── data preprocessing.ipynb                                              # Cleaning & preprocessing pipeline
├── web scrapping.ipynb                                                   # Data collection notebook
├── Election data.csv                                                     # Compiled dataset
├── Data-Driven Insights and Prediction of india's 2024 Election.pptx     # Presentation summary of findings
└── LICENSE                                                                # MIT License
```

**Suggested reading order:** `web scrapping.ipynb` → `data preprocessing.ipynb` → main analysis notebook. The main notebook is where the EDA, feature engineering, model training, tuning, and evaluation all come together.

---

## Methodology

**1. Data collection**
Candidate and constituency-level data was scraped and compiled into `Election data.csv`, covering fields like candidate assets, liabilities, education, criminal cases, party affiliation, and prior electoral history.

**2. Preprocessing**
Raw fields (often messy — inconsistent formatting, missing values, text-encoded numbers) were cleaned and standardized so they could actually be fed into a model.

**3. Exploratory Data Analysis**
Before modeling anything, the data was explored to check distributions, spot outliers, and look for obvious correlations between candidate attributes and election outcomes.

**4. Feature engineering**
Raw columns were transformed into features that a tree-based model could use meaningfully — this is usually where most of the real performance gain comes from, more than the model choice itself.

**5. Modeling**
A Random Forest classifier was chosen over simpler baselines because the relationships between features (like assets vs. criminal cases vs. incumbency) are non-linear and interact with each other — something a linear model would miss.

**6. Hyperparameter tuning**
Parameters like tree depth, number of estimators, and split criteria were tuned to balance bias and variance, rather than just chasing training accuracy.

**7. Evaluation**
Performance was validated using accuracy and ROC-AUC, with visual diagnostics (confusion matrix, ROC curve, feature importances) to confirm the model wasn't overfitting.

---

## Tech stack

- **Python 3**
- **Pandas / NumPy** — data wrangling
- **Matplotlib / Seaborn** — visualization
- **Scikit-learn** — Random Forest, model evaluation, hyperparameter tuning
- **Jupyter Notebook** — development environment

---

## Getting started

Clone the repo:

```bash
git clone https://github.com/Vipul-Ai-eng/DATA-DRIVEN-INSIGHTS-AND-PREDICTION-OF-INDIA-S-2024-ELECTIONS.git
cd DATA-DRIVEN-INSIGHTS-AND-PREDICTION-OF-INDIA-S-2024-ELECTIONS
```

Install the usual data science stack:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
```

Then run the notebooks in order — scraping/preprocessing first if you want to regenerate `Election data.csv` from scratch, or skip straight to the main notebook if you just want to explore the analysis and model using the provided CSV.

---

## Why this matters

Election prediction is usually approached through polling and sentiment analysis, which is noisy and expensive to collect. This project takes a different angle — using publicly disclosed, verifiable candidate data (assets, criminal record, education, past performance) that's available well before polling day. It's not meant to replace psephology, but it shows how much signal is already sitting in data that candidates are legally required to disclose.

---

## Future scope

- Extend the dataset across multiple election cycles to test temporal robustness
- Add state-level and regional features to capture local political dynamics
- Compare Random Forest against gradient boosting methods (XGBoost/LightGBM)
- Build a lightweight dashboard for interactive exploration of predictions

---

## License

This project is licensed under the MIT License — see the [LICENSE](./LICENSE) file for details.

## Author

**Vipul Bohra**
GitHub: [@Vipul-Ai-eng](https://github.com/Vipul-Ai-eng)
