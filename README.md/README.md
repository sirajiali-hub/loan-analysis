# Credit Risk Classification: Loan Default Prediction

## Project Overview
This project applies machine learning to predict loan default risk.
It is designed to support credit risk teams in making safer,
data-driven lending decisions.

## Business Problem
Loan defaults lead to financial losses for banks and fintech companies.
The goal of this project is to identify high-risk borrowers before loan
approval using a classification model.

## Stakeholders
- Credit risk teams
- Lending and underwriting departments

## Data
The dataset contains historical loan applicant information including
financial, demographic, and loan-related features.
The target variable indicates whether a borrower defaulted.

## Modeling Approach
An iterative modeling approach was used:
- Logistic Regression (baseline model)
- Decision Tree
- Random Forest (final model)

Data preprocessing was handled using scikit-learn pipelines, including
feature scaling and categorical encoding.

## Evaluation
Because this is a credit risk problem, accuracy alone is insufficient.
Evaluation focused on:
- Recall for default cases
- Confusion matrix
- ROC-AUC score

The Random Forest model was selected as the final model due to its strong
performance in identifying high-risk borrowers.

## Business Impact
The model can help:
- Reduce non-performing loans
- Improve risk management
- Support data-driven loan approval decisions

## Limitations
- Historical data may not reflect current economic conditions
- Some borrower risk factors may not be captured
- Model should be used as a decision-support tool

## Repository Structure
