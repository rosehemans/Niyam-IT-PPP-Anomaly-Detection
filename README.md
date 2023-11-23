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
| **DateApproved**                  | excluded         | date              | date when the loan was approved                                            |
| **SBAOfficeCode**                 | excluded         | categorical       | SBA Origination Office Code                                                |
| **ProcessingMethod**              | input         | categorical       | Loan Delivery Method (PPP for first draw; PPS for second draw)             |
| **BorrowerName**                  | excluded         | text              | Name of the borrower                                                       |
| **BorrowerAddress**               | excluded         | text              | Street address of the borrower                                             |
| **BorrowerCity**                  | input         | categorical       | City of the borrower                                                        |
| **BorrowerState**                 | input         | categorical       | State of the borrower                                                       |
| **BorrowerZip**                   | excluded         | categorical       | Zip code of the borrower                                                   |
| **LoanStatusDate**                | excluded         | date              | Date indicating the loan status                                            |
| **LoanStatus**                    | input         | categorical       | Description of loan status                                                 |
| **Term**                          | input         | int               | Loan Maturity in Months                                                    |
| **SBAGuarantyPercentage**         | excluded         | float             | Percentage of SBA Guaranty                                                 |
| **InitialApprovalAmount**         | input         | float             | Loan Approval Amount (at origination)                                      |
| **CurrentApprovalAmount**         | input         | float             | Loan Approval Amount (current)                                             |
| **UndisbursedAmount**             | excluded         | float             | Amount not yet disbursed                                                   |
| **FranchiseName**                 | excluded         | categorical       | Name of the franchise                                                      |
| **ServicingLenderLocationID**     | input         | categorical       | Lender Location ID                                                         |
| **ServicingLenderName**           | excluded         | categorical       | Name of the servicing lender                                               |
| **ServicingLenderAddress**        | excluded         | text              | Street address of the servicing lender                                     |
| **ServicingLenderCity**           | input         | categorical       | City of the servicing lender                                               |
| **ServicingLenderState**          | input         | categorical       | State of the servicing lender                                              |
| **ServicingLenderZip**            | excluded         | categorical       | Zip code of the servicing lender                                           |
| **RuralUrbanIndicator**           | input         | categorical       | Indicator for rural or urban                                               |
| **HubzoneIndicator**              | input         | categorical       | Indicator for Hubzone (Y/N)                                                |
| **LMIIndicator**                  | input         | categorical       | Indicator for Low to Moderate Income (Y/N)                                 |
| **ProjectCity**                   | input         | categorical       | City of the project                                                        |
| **ProjectCountyName**             | excluded         | categorical       | County Name of the project                                                 |
| **ProjectState**                  | input         | categorical       | State of the project                                                       |
| **ProjectZip**                    | excluded         | categorical       | Zip code of the project                                                    |
| **CD**                            | input         | categorical       | Project Congressional District                                              |
| **NAICSCode**                     | excluded         | categorical       | NAICS 6 digit code                                                         |
| **Race**                          | excluded         | categorical       | Borrower Race Description                                                  |
| **Ethnicity**                     | excluded         | categorical       | Borrower Ethnicity Description                                             |
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
| **Gender**                        | excluded         | categorical       | Gender Indicator                                                           |
| **Veteran**                       | excluded         | categorical       | Veteran Indicator                                                          |
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
| **Forgiven**                      | input        | categorical       | Categorical indicator if the loan is forgiven                              |
| **non_forgiven_loan_portion**     | input        | float             | Portion of the loan not forgiven                                           |
| **ApprovalDifference**            | input        | float             | Difference between initial and current approval amount                     |
| **ApprovalDifference_per_employee** | input     | float             | Approval difference per employee                                           |
| **InitialApprovalAmount_per_employee** | input  | float             | Initial approval amount per employee                                       |
| **CurrentApprovalAmount_per_employee** | input  | float             | Current approval amount per employee                                       |
| **UTILITIES_PROCEED_per_employee** | input       | float             | Utilities proceeds per employee                                            |
| **PAYROLL_PROCEED_per_employee**  | input       | float             | Payroll proceeds per employee                                              |
| **MORTGAGE_INTEREST_PROCEED_per_employee** | input | float      | Mortgage interest proceeds per employee                                   |
| **RENT_PROCEED_per_employee**     | input        | float             | Rent proceeds per employee                                                 |
| **REFINANCE_EIDL_PROCEED_per_employee** | input | float           | EIDL refinance proceeds per employee                                       |
| **HEALTH_CARE_PROCEED_per_employee** | input   | float             | Healthcare proceeds per employee                                           |
| **DEBT_INTEREST_PROCEED_per_employee** | input | float           | Debt interest proceeds per employee                                        |
| **ForgivenessAmount_per_employee** | input       | float             | Forgiveness amount per employee                                            |
| **Prior PPP count**               | input         | int               | Count of previous PPP loans                                                |
| **Prior PPS count**               | input         | int               | Count of previous PPS loans                                                |
| **expected_UTILITIES_PROCEED**    | input        | float             | Expected utilities proceeds                                                |
| **expected_PAYROLL_PROCEED**      | input        | float             | Expected payroll proceeds                                                  |
| **expected_MORTGAGE_INTEREST_PROCEED** | input | float           | Expected mortgage interest proceeds                                        |
| **expected_RENT_PROCEED**         | input        | float             | Expected rent proceeds                                                     |
| **expected_REFINANCE_EIDL_PROCEED** | input      | float             | Expected EIDL refinance proceeds                                           |
| **expected_HEALTH_CARE_PROCEED**  | input        | float             | Expected healthcare proceeds                                               |
| **expected_DEBT_INTEREST_PROCEED** | input      | float             | Expected debt interest proceeds                                            |
| **expected_ForgivenessAmount**    | input        | float             | Expected forgiveness amount                                                |
| **expected_ApprovalDifference**   | input        | float             | Expected approval difference                                               |
| **expected_InitialApprovalAmount** | input       | float             | Expected initial approval amount                                            |
| **expected_CurrentApprovalAmount** | input       | float             | Expected current approval amount                                           |
| **deviant_JR**                    | input         | float             | Deviant value for jobs reported                                                      |
| **deviant_JR_risk_score**         | input        | float             | Risk score for deviant jobs reported                                                  |
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
| **deviant_UTILITIES_PROCEED_risk_score** | input | float           | Risk score for deviant utilities proceeds                                  |
| **deviant_PAYROLL_PROCEED_risk_score** | input   | float           | Risk score for deviant payroll proceeds                                    |
| **deviant_MORTGAGE_INTEREST_PROCEED_risk_score** | input | float   | Risk score for deviant mortgage interest proceeds                          |
| **deviant_RENT_PROCEED_risk_score** | input     | float           | Risk score for deviant rent proceeds                                       |
| **deviant_REFINANCE_EIDL_PROCEED_risk_score** | input | float      | Risk score for deviant EIDL refinance proceeds                             |
| **deviant_HEALTH_CARE_PROCEED_risk_score** | input  | float           | Risk score for deviant healthcare proceeds                                 |
| **deviant_DEBT_INTEREST_PROCEED_risk_score** | input | float        | Risk score for deviant debt interest proceeds                              |
| **deviant_ForgivenessAmount_risk_score** | input | float           | Risk score for deviant forgiveness amount                                  |
| **deviant_ApprovalDifference_risk_score** | input | float          | Risk score for deviant approval difference                                 |
| **deviant_InitialApprovalAmount_risk_score** | input | float        | Risk score for deviant initial approval amount                             |
| **deviant_CurrentApprovalAmount_risk_score** | input | float        | Risk score for deviant current approval amount                             |
| **average_risk_score**            | output        | float             | Average risk score                                                         |



* **Source of training data**:
* Small Business Administration (https://data.sba.gov/dataset/ppp-foia),
* Data.gov (https://catalog.data.gov/dataset/small-business-administration-sba-size-standards-table)
  
* **Number of rows in training data**:
  * Training rows: 965,548
 
### Model details
* **Columns used as inputs in the final model**: 'ProcessingMethod', 'LoanStatus', 'Term',
                  'InitialApprovalAmount', 'CurrentApprovalAmount', 'ForgivenessAmount', 
                  'RuralUrbanIndicator', 'HubzoneIndicator', 'LMIIndicator',
                  'BusinessAgeDescription', 'CD', 'JobsReported', 'NonProfit',
                  'BusinessType', 'NAICS Industry Description', 'Size standards in number of employees',
                  'UTILITIES_PROCEED', 'PAYROLL_PROCEED', 'MORTGAGE_INTEREST_PROCEED',
                  'RENT_PROCEED', 'REFINANCE_EIDL_PROCEED', 'HEALTH_CARE_PROCEED', 'DEBT_INTEREST_PROCEED',
                  'non_forgiven_loan_portion','ApprovalDifference', 'ApprovalDifference_per_employee',
                  'InitialApprovalAmount_per_employee', 'CurrentApprovalAmount_per_employee',
                  'UTILITIES_PROCEED_per_employee', 'PAYROLL_PROCEED_per_employee', 'MORTGAGE_INTEREST_PROCEED_per_employee',
                  'RENT_PROCEED_per_employee', 'REFINANCE_EIDL_PROCEED_per_employee', 'HEALTH_CARE_PROCEED_per_employee',
                  'DEBT_INTEREST_PROCEED_per_employee', 'ForgivenessAmount_per_employee',
                  'BorrowerCity', 'BorrowerState', 'ServicingLenderCity', 'ServicingLenderState',
                  'ServicingLenderLocationID', 'ProjectCity', 'ProjectState',
                  'OriginatingLenderLocationID', 'OriginatingLender', 'OriginatingLenderCity', 'OriginatingLenderState',
                  'deviant_JR', 'deviant_UTILITIES_PROCEED', 'deviant_PAYROLL_PROCEED', 'deviant_MORTGAGE_INTEREST_PROCEED',
                  'deviant_RENT_PROCEED', 'deviant_REFINANCE_EIDL_PROCEED', 'deviant_HEALTH_CARE_PROCEED',
                  'deviant_DEBT_INTEREST_PROCEED', 'deviant_ForgivenessAmount', 'deviant_ApprovalDifference',
                  'deviant_InitialApprovalAmount', 'deviant_CurrentApprovalAmount'
  
  * **Type of model**: Unsupervised Average Weighted Ensemble Anomaly Detection
  
  * **Model Composition**:
  * The ensemble model comprises three components:

1. Isolation Forest
    * **Software used to implement the model**: Python, scikit-learn
    * **Version of the modeling software**: (ADD AT END)
    * **Hyperparameters or other settings of model**:
```
IsolationForest(n_estimators=50, max_samples = auto, contamination = 0.01, max_features = 1.0, bootstrap = False, n_jobs = None, random_state=12345, verbose = 0, warm_start = False)
```

2. Isolation Forest
    * **Software used to implement the model**: Python, H2O
    * **Version of the modeling software**: (ADD AT END)
    * **Hyperparameters or other settings of model**:
```
hyper_params = {
    'ntrees':list(range(20, 140, 20)),
    'max_depth':list(range(2, 30, 2)),
    'sample_rate':[s/float(10) for s in range(1, 11)],
    'col_sample_rate_per_tree' : [s/float(10) for s in range(1, 11)]}

search_criteria = {
    "strategy": "RandomDiscrete",
    "max_models": 50,
    "seed": 100,
    'max_runtime_secs':3600}

# Set up grid search
grid = H2OGridSearch(
    model=H2OIsolationForestEstimator,
    grid_id='iso_grid1',
    hyper_params=hyper_params,
    search_criteria=search_criteria
)
```
```
train, test = ppp_model.split_frame(ratios = [0.70])
grid.train(x=anomaly_inputs, training_frame=train)
```
```
#selected model: iso_grid1_model_31
isolationForest(ntrees = 40.0, max_depth = 24.0, sample_rate = 0.9, col_sample_rate_per_tree = 1.0)
```

3. Average risk score
    * **Software used to implement the model**: Python
    * **Version of the modeling software**: (ADD AT END)
    * **Calculation of average risk score**: Using industry size standards, we calculated standard 'expected' figures for 'per employee' data for UTILITIES_PROCEED, PAYROLL_PROCEED, MORTGAGE_INTEREST_PROCEED, REFINANCE_EIDL_PROCEED, HEALTH_CARE_PROCEED, DEBT_INTEREST_PROCEED, InitialApprovalAmount, CurrentApprovalAmount, ApprovalDifference, and ForgivenessAmount. We then calculated 'deviant' figures by calculating the difference between actual and 'expected' figures for each loan. Risk scores for each figure were calculated by percentile rank among all loans. The final average risk score is a simple arithmetic mean of risk scores:
  
```
# Calculate Average Risk Score
clean['average_risk_score'] = clean[['deviant_UTILITIES_PROCEED_risk_score',
            'deviant_PAYROLL_PROCEED_risk_score',
            'deviant_MORTGAGE_INTEREST_PROCEED_risk_score',
            'deviant_RENT_PROCEED_risk_score',
            'deviant_REFINANCE_EIDL_PROCEED_risk_score',
            'deviant_HEALTH_CARE_PROCEED_risk_score',
            'deviant_DEBT_INTEREST_PROCEED_risk_score',
            'deviant_ForgivenessAmount_risk_score',
            'deviant_ApprovalDifference_risk_score',
            'deviant_InitialApprovalAmount_risk_score',
            'deviant_CurrentApprovalAmount_risk_score']].mean(axis=1)
```     
 
* **Columns as outputs of models**:
* 












