# Credit Risk Modeling in Python

## Outline:

1. Exploring and Preparing Loan Data
2. Logistic Regression for Defaults
3. Gradient Boosted Trees Using XGBoost
4. Model Evaluation and Implementation


## Exploring and Preparing Loan Data

- Credit Risk: possibility that someone who has borrowed money will nost repay it
- Default: fails to repay loan
- Probability of Default(PD)

- Expected loss: amount firm loses because of a loan Default
    - PD
    - Exposure at default (EAD) amount outstanding at the time of default
    - Loss Given Default (LGD) 

    `expected_loss = PD*EAD*LGD`

- Two Primary types of data used
    - application data eg. interest rate, grade, amount
    - behavioral data eg. employment length, income, historical default

Data columns include a mix of the two. 

-  Exploring with cross tables 
```Python
pd.crosstab(cr_load['person_hope_ownership'], cr_load['loan_status'], values = cr_loan['loan_int_rate'], aggfunc = 'mean').round(2)
```
grouped by loan status and home ownership and average int rate is calculated

### snippets

```Python
# Look at the distribution of loan amounts with a histogram
n, bins, patches = plt.hist(x=cr_loan['loan_amnt'], bins='auto', color='blue',alpha=0.7, rwidth=0.85)
plt.xlabel("Loan Amount")
plt.show()

# Create a cross table of home ownership, loan status, and average percent income
print(pd.crosstab(cr_loan['person_home_ownership'], cr_loan['loan_status'],
              values=cr_loan['loan_percent_income'], aggfunc='mean'))

```