
# Wisconsin Mortgage PD Model
Overview

This project develops a Probability of Default (PD) model for Wisconsin mortgage loans originated between 2020 and 2022 using traditional credit risk modeling techniques. The analysis predicts whether a loan will default within 12 months of origination, evaluates model stability over time, and demonstrates how model outputs can support risk-based lending decisions.

# Business Objective

The goal is to estimate 12-month default risk for mortgage loans and assess whether the model remains reliable under changing borrower conditions. The project also shows how calibrated PDs can be translated into approval cutoffs and portfolio risk trade-offs.

# Data Source
- Freddie Mac Single-Family Loan-Level Dataset  
- Scope: Wisconsin mortgage originations from 2020 to 2022  
Inputs:  
- Origination data: borrower and loan characteristics  
- Performance data: monthly loan outcomes

# Methodology

The project follows a traditional credit risk modeling workflow:

- Constructed a 12-month default target from monthly performance records  
- Filtered and aggregated large loan-level performance files  
- Applied Weight of Evidence (WOE) transformation and Information Value (IV) screening  
- Built a logistic regression PD model
- Evaluated performance using AUC, KS, lift, and Brier Score  
- Assessed population drift using PSI  
- Applied intercept-only recalibration to correct probability bias  
- Built a decision strategy using calibrated PD cutoffs

# Key Results
Train AUC: 0.817  
Validation AUC: 0.824  
OOT AUC: 0.808  
KS: 0.514  
PSI: 0.33  

The model showed strong and stable discriminatory power across datasets. Population drift caused overestimation of default probabilities in the OOT sample, but intercept recalibration improved probability alignment without affecting model ranking.

# Decision Strategy
Calibrated PDs were used to evaluate the trade-off between approval rate and default risk.

Recommended cutoff: 0.005 – 0.008
Achieves strong balance between:
approval volume
risk reduction


# Next Steps
- Ongoing model monitoring on new OOT samples  
- Periodic recalibration  
- Stress testing under adverse borrower conditions  
- Extension to machine learning models such as Random Forest and XGBoost  
