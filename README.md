# Niyam-IT-PPP-Anomaly-Detection

### Basic Information

* **Person or organization developing model**: Niyam IT; Rohit Bollineni (rbollineni@niyamit.com), GWU MSBA; Rose Hemans (rose.hemans@gwu.edu), Bagya Maduwanthi Widanagamage (bmwidanagamage@gwu.edu), Kaixuan (Kevin) Han (kaixuan.han@gwu.edu), Pavneet Singh (pavneet@gwu.edu)
  
* **Model date**: Nov, 2023
* **Model version**: 1.0
* **License**: MIT
* **Model implementation code**: (ADD AT END)

### Intended Use
* **Primary intended uses**: This model is an example of an end-to-end anomaly detection modeling process that is intended to be used as a guide for current and future anomaly detection models.
* **Primary intended users**: Niyam IT, Patrick Hall, and students in the GW MSBA DNSC 6317 class.
* **Out-of-scope use cases**: Any use beyond an educational example is out-of-scope.

* ### Training Data

* Data dictionary: 

| Name                              | Modeling Role | Measurement Level | Description                                                               |
| --------------------------------- | ------------- | ----------------- | ------------------------------------------------------------------------- |
| **LoanNumber**                    | ID            | int               | unique row identifier                                                      |
| **DateApproved**                  | input         | date              | date when the loan was approved                                            |
| **SBAOfficeCode**                 | input         | categorical       | SBA Origination Office Code                                                |
| **ProcessingMethod**              | input         | categorical       | Loan Delivery Method (PPP for first draw; PPS for second draw)             |
| **BorrowerName**                  | input         | text              | Name of the borrower                                                       |
| **BorrowerAddress**               | input         | text              | Street address of the borrower                                             |
| **BorrowerCity**                  | input         | categorical       | City of the borrower                                                        |
| **BorrowerState**                 | input         | categorical       | State of the borrower                                                       |
| **BorrowerZip**                   | input         | categorical       | Zip code of the borrower                                                   |
| **LoanStatusDate**                | input         | date              | Date indicating the loan status                                            |
| **LoanStatus**                    | input         | categorical       | Description of loan status                                                 |
| **Term**                          | input         | int               | Loan Maturity in Months                                                    |
| **SBAGuarantyPercentage**         | input         | float             | Percentage of SBA Guaranty                                                 |
| **InitialApprovalAmount**         | input         | float             | Loan Approval Amount (at origination)                                      |
| **CurrentApprovalAmount**         | input         | float             | Loan Approval Amount (current)                                             |
| **UndisbursedAmount**             | input         | float             | Amount not yet disbursed                                                   |
| **FranchiseName**                 | input         | categorical       | Name of the franchise                                                      |
| **ServicingLenderLocationID**     | input         | categorical       | Lender Location ID                                                         |
| **ServicingLenderName**           | input         | categorical       | Name of the servicing lender                                               |
| **ServicingLenderAddress**        | input         | text              | Street address of the servicing lender                                     |
| **ServicingLenderCity**           | input         | categorical       | City of the servicing lender                                               |
| **ServicingLenderState**          | input         | categorical       | State of the servicing lender                                              |
| **ServicingLenderZip**            | input         | categorical       | Zip code of the servicing lender                                           |
| **RuralUrbanIndicator**           | input         | categorical       | Indicator for rural or urban                                               |
| **HubzoneIndicator**              | input         | categorical       | Indicator for Hubzone (Y/N)                                                |
| **LMIIndicator**                  | input         | categorical       | Indicator for Low to Moderate Income (Y/N)                                 |
| **ProjectCity**                   | input         | categorical       | City of the project                                                        |
| **ProjectCountyName**             | input         | categorical       | County Name of the project                                                 |
| **ProjectState**                  | input         | categorical       | State of the project                                                       |
| **ProjectZip**                    | input         | categorical       | Zip code of the project                                                    |
| **CD**                            | input         | categorical       | Project Congressional District                                              |
| **NAICSCode**                     | input         | categorical       | NAICS 6 digit code                                                         |
| **Race**                          | input         | categorical       | Borrower Race Description                                                  |
| **Ethnicity**                     | input         | categorical       | Borrower Ethnicity Description                                             |
| **UTILITIES_PROCEED**             | input         | float             | Proceeds for utilities                                                     |
| **PAYROLL_PROCEED**               | input         | float             | Proceeds for payroll                                                       |
| **MORTGAGE_INTEREST_PROCEED**     | input         | float             | Proceeds for mortgage interest                                             |
| **RENT_PROCEED**                  | input         | float             | Proceeds for rent                                                          |
| **REFINANCE_EIDL_PROCEED**        | input         | float             | Proceeds for EIDL refinance                                                |
| **DEBT_INTEREST_PROCEED**         | input         | float             | Proceeds for debt interest                                                 |
| **BusinessType**                  | input         | categorical       | Description of business type                                               |
| **OriginatingLenderLocationID**   | input         | categorical       | Originating Lender ID                                                      |
| **OriginatingLender**             | input         | categorical       | Name of the originating lender                                             |
| **OriginatingLenderCity**         | input         | categorical       | City of the originating lender                                             |
| **OriginatingLenderState**        | input         | categorical       | State of the originating lender                                            |
| **Gender**                        | input         | categorical       | Gender Indicator                                                           |
| **Veteran**                       | input         | categorical       | Veteran Indicator                                                          |
| **NonProfit**                     | input         | categorical       | 'Yes' if Business Type = Non-Profit Organization or Non-Profit Childcare Center or 501(c) Non Profit |
| **UTILITIES_PROCEED_purpose**     | input         | categorical       | Purpose of utilities proceeds                                              |
| **PAYROLL_PROCEED_purpose**       | input         | categorical       | Purpose of payroll proceeds                                                |
| **MORTGAGE_INTEREST_PROCEED_purpose** | input    | categorical       | Purpose of mortgage interest proceeds                                      |
| **RENT_PROCEED_purpose**          | input         | categorical       | Purpose of rent proceeds                                                   |
| **REFINANCE_EIDL_PROCEED_purpose**| input        | categorical       | Purpose of EIDL refinance proceeds                                         |
| **HEALTH_CARE_PROCEED_purpose**   | input         | categorical       | Purpose of healthcare proceeds                                             |
| **DEBT_INTEREST_PROCEED_purpose** | input         | categorical       | Purpose of debt interest proceeds                                          |
| **NAICS Industry Description**    | input         | categorical       | Description of NAICS industry                                              |
| **Size standards in number of employees** | input | categorical  | Size standards in number of employees                                      |
| **Forgiven**                      | output        | categorical       | Categorical indicator if the loan is forgiven                              |
| **non_forgiven_loan_portion**     | output        | float             | Portion of the loan not forgiven                                           |
| **ApprovalDifference**            | output        | float             | Difference between initial and current approval amount                     |
| **ApprovalDifference_per_employee** | output     | float             | Approval difference per employee                                           |
| **InitialApprovalAmount_per_employee** | output  | float             | Initial approval amount per employee                                       |
| **CurrentApprovalAmount_per_employee** | output  | float             | Current approval amount per employee                                       |
| **UTILITIES_PROCEED_per_employee** | output       | float             | Utilities proceeds per employee                                            |
| **PAYROLL_PROCEED_per_employee**  | output       | float             | Payroll proceeds per employee                                              |
| **MORTGAGE_INTEREST_PROCEED_per_employee** | output | float      | Mortgage interest proceeds per employee                                   |
| **RENT_PROCEED_per_employee**     | output        | float             | Rent proceeds per employee                                                 |
| **REFINANCE_EIDL_PROCEED_per_employee** | output | float           | EIDL refinance proceeds per employee                                       |
| **HEALTH_CARE_PROCEED_per_employee** | output   | float             | Healthcare proceeds per employee                                           |
| **DEBT_INTEREST_PROCEED_per_employee** | output | float           | Debt interest proceeds per employee                                        |
| **ForgivenessAmount_per_employee** | output       | float             | Forgiveness amount per employee                                            |
| **Prior PPP count**               | input         | int               | Count of previous PPP loans                                                |
| **Prior PPS count**               | input         | int               | Count of previous PPS loans                                                |
| **expected_UTILITIES_PROCEED**    | output        | float             | Expected utilities proceeds                                                |
| **expected_PAYROLL_PROCEED**      | output        | float             | Expected payroll proceeds                                                  |
| **expected_MORTGAGE_INTEREST_PROCEED** | output | float           | Expected mortgage interest proceeds                                        |
| **expected_RENT_PROCEED**         | output        | float             | Expected rent proceeds                                                     |
| **expected_REFINANCE_EIDL_PROCEED** | output      | float             | Expected EIDL refinance proceeds                                           |
| **expected_HEALTH_CARE_PROCEED**  | output        | float             | Expected healthcare proceeds                                               |
| **expected_DEBT_INTEREST_PROCEED** | output      | float             | Expected debt interest proceeds                                            |
| **expected_ForgivenessAmount**    | output        | float             | Expected forgiveness amount                                                |
| **expected_ApprovalDifference**   | output        | float             | Expected approval difference                                               |
| **expected_InitialApprovalAmount** | output       | float             | Expected initial approval amount                                            |
| **expected_CurrentApprovalAmount** | output       | float             | Expected current approval amount                                           |
| **deviant_JR**                    | input         | float             | Deviant value for JR                                                       |
| **deviant_JR_risk_score**         | output        | float             | Risk score for deviant JR                                                  |
| **deviant_UTILITIES_PROCEED**     | input         | float             | Deviant value for utilities proceeds                                       |
| **deviant_PAYROLL_PROCEED**       | input         | float             | Deviant value for payroll proceeds                                         |
| **deviant_MORTGAGE_INTEREST_PROCEED** | input   | float             | Deviant value for mortgage interest proceeds                               |
| **deviant_RENT_PROCEED**          | input         | float             | Deviant value for rent proceeds                                            |
| **deviant_HEALTH_CARE_PROCEED**   | input         | float             | Deviant value for healthcare proceeds                                      |
| **deviant_DEBT_INTEREST_PROCEED** | input         | float             | Deviant value for debt interest proceeds                                   |
| **deviant_ForgivenessAmount**     | input         | float             | Deviant value for forgiveness amount                                       |
| **deviant_ApprovalDifference**    | input         | float             | Deviant value for approval difference                                      |
| **deviant_InitialApprovalAmount** | input         | float             | Deviant value for initial approval amount                                  |
| **deviant_CurrentApprovalAmount** | input         | float             | Deviant value for current approval amount                                  |
| **deviant_UTILITIES_PROCEED_risk_score** | output | float           | Risk score for deviant utilities proceeds                                  |
| **deviant_PAYROLL_PROCEED_risk_score** | output   | float           | Risk score for deviant payroll proceeds                                    |
| **deviant_MORTGAGE_INTEREST_PROCEED_risk_score** | output | float   | Risk score for deviant mortgage interest proceeds                          |
| **deviant_RENT_PROCEED_risk_score** | output     | float           | Risk score for deviant rent proceeds                                       |
| **deviant_REFINANCE_EIDL_PROCEED_risk_score** | output | float      | Risk score for deviant EIDL refinance proceeds                             |
| **deviant_HEALTH_CARE_PROCEED_risk_score** | output  | float           | Risk score for deviant healthcare proceeds                                 |
| **deviant_DEBT_INTEREST_PROCEED_risk_score** | output | float        | Risk score for deviant debt interest proceeds                              |
| **deviant_ForgivenessAmount_risk_score** | output | float           | Risk score for deviant forgiveness amount                                  |
| **deviant_ApprovalDifference_risk_score** | output | float          | Risk score for deviant approval difference                                 |
| **deviant_InitialApprovalAmount_risk_score** | output | float        | Risk score for deviant initial approval amount                             |
| **deviant_CurrentApprovalAmount_risk_score** | output | float        | Risk score for deviant current approval amount                             |
| **average_risk_score**            | output        | float             | Average risk score                                                         |

* **Source of training data**: Small Business Administration (https://data.sba.gov/dataset/ppp-foia), Data.gov (https://catalog.data.gov/dataset/small-business-administration-sba-size-standards-table)
* **Number of rows in training data**:
  * Training rows: 965,548
