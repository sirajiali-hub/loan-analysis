# Loan Default Prediction

**In one line:** Predicting which loan applicants are likely not to repay, so a bank can check risky loans before approving them.

## The question
When a bank lends to someone who does not repay, it loses money. Can past loan data help spot risky applicants early?

## What I did
1. Used a public dataset of 255,347 loans, where 11.6% (about 1 in 9) were not repaid.
2. Looked at which borrowers default most, for example by income, age, job type and loan size compared with income.
3. Trained two models to give each applicant a default risk score.
4. Measured the models the way banks do (ROC AUC and KS statistic).
5. Looked at where to set the cut off, trading caught defaults against good customers turned away.

## What I found
* **Biggest warning signs:** younger age, high interest rate, a large loan compared with income, and short time in a job.
* **Loan size against income:** borrowers in the top quarter defaulted at 18.7%, against 8.0% in the bottom quarter.
* **Model quality:** ROC AUC of 0.76 and KS of 0.39, which banks treat as acceptable to good for consumer lending.
* **At the standard cut off:** the model catches about 7 in 10 defaults while still approving about two thirds of applicants.

## Why it matters
A model like this can act as a second check behind the loan officer, so staff spend review time on the riskiest applications.

## Limitations
* The data is a public practice dataset, not real Kenyan bank data.
* Training and testing were not split by date, which a real bank would do.
* Real models also use credit bureau and M-Pesa data, which this does not have.

## Files
* `credit_risk_loan_default_analysis_model.ipynb`: the full analysis

## How to run
1. Run `pip install pandas numpy scikit-learn matplotlib seaborn scipy`
2. Open the notebook and run all cells from the top.

**Tools:** Python, scikit-learn
