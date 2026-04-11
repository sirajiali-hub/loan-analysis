# Credit Risk Modeling: Loan Default Prediction

A machine learning-based credit risk model that predicts loan defaults and translates predictions into actionable financial impact estimates for portfolio risk management.

---

## Business Problem

Loan defaults are one of the largest sources of financial loss for banks and microfinance institutions. Under IFRS 9, lenders must estimate Expected Credit Loss (ECL) and set aside provisions — meaning bad loans hurt the balance sheet even before they officially default.

This project builds a probability of default (PD) model that serves as a second-line risk filter in the loan approval process. The model scores each application and flags high-risk borrowers for enhanced due diligence, helping credit teams make faster, data-driven decisions.

## Key Results

| Metric | Value |
|--------|-------|
| Best Model | Logistic Regression (selected for interpretability and regulatory alignment) |
| ROC-AUC | 0.762 |
| Default Detection Rate | ~70% at optimized threshold (0.20) |
| Estimated Annual Loss Prevention | KES 490M per KES 10B portfolio |

## What Makes This Different

This is not a typical train-predict-accuracy project. The analysis includes:

- **Threshold optimization** — instead of using sklearn's default 0.50 cutoff, the model evaluates multiple thresholds based on the cost asymmetry between missed defaults (expensive) and false flags (cheap)
- **Financial impact quantification** — model performance is translated into KES figures that a credit committee can act on
- **Banking-standard metrics** — ROC-AUC, KS Statistic, and segment-level default rate analysis alongside standard classification metrics
- **Feature importance with business interpretation** — explaining *why* loan-to-income ratio and employment stability drive defaults, not just that they do

## Project Structure

```
credit-risk-loan-default/
│
├── credit_risk_loan_default_analysis.ipynb   # Main analysis notebook
├── Loan_default.csv                          # Dataset (255K loans, 18 features)
├── README.md
│
└── outputs/                                  # Generated charts
    ├── 01_default_distribution.png
    ├── 02_segment_default_rates.png
    ├── 03_continuous_risk_analysis.png
    ├── 04_correlation_matrix.png
    ├── 05_roc_comparison.png
    ├── 06_ks_statistic.png
    ├── 07_feature_importance.png
    ├── 08_threshold_optimization.png
    └── 09_confusion_matrix_comparison.png
```

## Dataset

255,347 historical loan records with 18 features covering borrower demographics, financial profile, and loan characteristics.

| Feature | Description |
|---------|-------------|
| Age, Income, Education | Borrower demographics |
| CreditScore, NumCreditLines, DTIRatio | Credit profile |
| LoanAmount, InterestRate, LoanTerm | Loan terms |
| MonthsEmployed, EmploymentType | Employment stability |
| LoanPurpose, HasMortgage, HasCoSigner | Loan context |
| Default | Target variable (11.6% default rate) |

**Engineered feature:** `LoanToIncome` — loan amount divided by annual income, capturing affordability risk.

## Methodology

**Models evaluated:**

| Model | Role | Why |
|-------|------|-----|
| Logistic Regression | Final model | Interpretable, auditable, regulators understand it, industry standard for credit scoring |
| Random Forest | Challenger model | Captures non-linear interactions, used for comparison and ongoing monitoring |

Both models use `class_weight='balanced'` to handle the 88:12 class imbalance, penalizing missed defaults more heavily during training.

**Evaluation approach:**
The project prioritizes recall (catching defaults) over accuracy, since misclassifying a defaulter as low-risk results in direct financial loss. Threshold optimization finds the probability cutoff that balances default detection against approval rate based on the bank's risk appetite.

## Top Risk Drivers

1. **Borrower Age** — younger borrowers show less financial stability
2. **Interest Rate** — higher rates correlate with riskier profiles and create repayment burden
3. **Loan-to-Income Ratio** — core affordability metric; high LTI signals stretched finances
4. **Months Employed** — job stability directly impacts repayment consistency
5. **Income** — absolute repayment capacity

## How to Run

```bash
# Clone the repository
git clone https://github.com/sirajiali-hub/loan-analysis.git
cd loan-analysis

# Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn scipy

# Open the notebook
jupyter notebook credit_risk_loan_default_analysis.ipynb
```

Requires Python 3.8+ and Jupyter Notebook.

## Limitations

- Dataset has uniform feature distributions suggesting synthetic generation — real-world data would be messier
- Uses random train/test split; production models require time-based validation
- Does not incorporate CRB (Credit Reference Bureau) or alternative data (M-Pesa transactions)
- Static model — production deployment would need drift monitoring (PSI) and periodic retraining

## Future Enhancements

- Build a Weight of Evidence (WOE) scorecard for direct integration into loan origination systems
- Incorporate M-Pesa transaction patterns as alternative credit signals
- Add Sharia-compliant risk assessment for Islamic banking products
- Implement reject inference to account for selection bias in approved-only data

## Tools

Python, pandas, NumPy, scikit-learn, matplotlib, seaborn, SciPy

---

*Built by Siraji Ali — combining data science and financial analysis for credit risk applications in the East African market.*
