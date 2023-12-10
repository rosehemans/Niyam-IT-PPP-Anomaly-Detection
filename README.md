# Paycheck Protection Program Loan Anomaly Detection Model Card

![Dashboard](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/e3fdcdb14695db02831f3d8ed8dc847eb047c0d9/Graphs/ppp_dashboard_update.jpeg)

[Google Drive Datasets Folder](https://drive.google.com/drive/folders/157Bi_PxtXq2lqmx0nTDuS71tw_9YnW7K?usp=drive_link)

## Table of Contents

* **Data Introduction**:
  * [Basic Information](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/tree/main#basic-information)
  * [Intended Use](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/tree/main#intended-use)
  * [Training Data](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/tree/main#training-data)
* **Model Details**
  * [Scikit-Learn Library Isolation Forest Model](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/main/README.md#1-isolation-forest-skl-if)
  * [H2O Library Isolation Forest Model](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/main/README.md#2-isolation-forest-h2o-if)
  * [Pandas Average Risk Score Model](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/main/README.md#3-average-risk-score-avr)
* **Exploratory Data Analysis**:
  * [General Exploratory Data Analysis](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/tree/main#general-exploratory-data-analysis)
  * [AVR Model Exploratory Data Analysis](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/tree/main#avr-model-exploratory-data-analysis)
  * [scikit-learn Isolation Forest Model Exploratory Data Analysis](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/tree/main#scikit-learn-isolation-forest-model-exploratory-data-analysis)
  * [H2O IF Model Exploratory Data Analysis](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/tree/main#h2o-if-model-exploratory-data-analysis)
  * [Final Blended Model Exploratory Data Analysis](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/tree/main#final-blended-model-exploratory-data-analysis)
* **Considerations and Next Steps**:
  * [Ethical Considerations](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/tree/main#ethical-considerations)
  * [Risk Considerations](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/tree/main#risk-considerations)
  * [Potential Next Steps](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/tree/main#potential-next-steps)

* **[Author Contributions](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/tree/main#author-contributions)**

# Basic Information

* **Person or organization developing model**:
  * **GWU MSBA**;
    * Rose Hemans (rose.hemans@gwu.edu)
    * Bagya Maduwanthi Widanagamage (bmwidanagamage@gwu.edu)
    * Kaixuan (Kevin) Han (kaixuan.han@gwu.edu)
    * Pavneet Singh (pavneet@gwu.edu)
  * **Niyam IT**;
    * Rohit Bollineni (rbollineni@niyamit.com)
  
* **Model date**: Nov, 2023
* **Model version**: 1.0
* **License**: MIT
* **Model implementation code**: [Notebooks](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/tree/f0f8f76f8ee1f1cf1c5cef435f4998fd6106d796/Notebooks)

# Intended Use
* **Primary intended uses**: This model is an example of an end-to-end anomaly detection modeling process that is intended to be used as a guide for current and future anomaly detection models.
* **Primary intended users**: Niyam IT, Patrick Hall, and students in the GW MSBA DNSC 6317 class.
* **Out-of-scope use cases**: Any use beyond an educational example is out-of-scope.

# Training Data

**Data dictionary**: 

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




* **Data Source**:
  * [Small Business Administration](https://data.sba.gov/dataset/ppp-foia)
  * [Data.gov](https://catalog.data.gov/dataset/small-business-administration-sba-size-standards-table)
  * [GWU MSBA Feature Engineering](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/841f9ca989efd7cc9056ed7caedf0ee516d02641/Notebooks/(2)%20PPP%20Additional%20Feature%20Engineering.ipynb)
  
* **Number of rows in training data**:
  * Training rows: 965,548
 
 #### PPP Overview Dashboard

![PPP Dashboard 2](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/273c9b50786cf91e2c3a3605e94b6c74ac1efc7c/Graphs/ppp_dashboard_2.jpeg)
  
# Model details
* **Columns used as inputs in the final model**: 'ProcessingMethod', 'LoanStatus', 'Term',
                  'InitialApprovalAmount', 'CurrentApprovalAmount', 'ForgivenessAmount', 
                  'RuralUrbanIndicator', 'HubzoneIndicator', 'LMIIndicator',
                  'BusinessAgeDescription', 'CD', 'JobsReported', 'NonProfit',
                  'BusinessType', 'NAICS Industry Description', 'Size standards in number of employees',
                  'UTILITIES_PROCEED', 'PAYROLL_PROCEED', 'MORTGAGE_INTEREST_PROCEED',
                  'RENT_PROCEED', 'REFINANCE_EIDL_PROCEED', 'HEALTH_CARE_PROCEED', 'DEBT_INTEREST_PROCEED',
                  'non_forgiven_loan_portion', 'ApprovalDifference', 'ApprovalDifference_per_employee',
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
  
## Model Composition and Methodology:
The ensemble model comprises three components:

### 1. Isolation Forest (SKL IF)
   * **Software used to implement the model**: Python, scikit-learn
   * **Version of the modeling software**: Python 3.9.12, scikit-learn 1.0.2
   * **Hyperparameters or other settings of model**:
 
```
IsolationForest(n_estimators=50, max_samples = auto, contamination = 0.01, max_features = 1.0, bootstrap = False, n_jobs = None, random_state=12345, verbose = 0, warm_start = False)
```

* **The scikit-learn Isolation Forest model is an unsupervised machine learning algorithm used for anomaly detection, isolating anomalies by constructing random decision trees and identifying instances that require fewer partitions to isolate:**
  
  * Rare and distant points are anomalies.
  * Isolation Forest uses random trees to isolate anomalies.
  * Randomly selects features and split values for tree construction.
  * Anomalies closer to tree roots need fewer partitions.
  * Shorter average path lengths across trees flag anomalies.

* **Advantages**:
  * Scalability
  * Robust to outliers
  * Minimal hyperparameters
  * Extensive documentation and online support
  * User friendly

* **Disadvantages**:
  * Struggles with dense data
  * Difficulty handling multimodal data
  * Random sensitivity
  
### 2. Isolation Forest (H2O IF)

   * **Software used to implement the model**: Python, H2O
   * **Version of the modeling software**: Python 3.9.12, H2O 3.44.0.1
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
isolationForest(ntrees = 40.0, max_depth = 24.0, sample_rate = 0.9, col_sample_rate_per_tree = 1.0)
```

* **Advantages**:
  * Leverages distributed computing and parallelization
  * Automated hyperparameter optimization (AutoML)
  * Integration with H2O's framework and ecosystem

* **Disadvantages**:
  * Complexity and steeper learning curve
  * Limited documentation and community support available

### Quantitative Analysis

**Isolation Forest (H2O)**

| Anomaly Score | Normalized Anomaly Score |
| ------------- | ------------------------ |
| 22.913 | 0.006|

| Number of Trees | Number of Internal Trees | Model Size in Bytes | Min Depth | Max Depth | Min Leaves | Max Leaves | Mean Leaves |
| --------------- | ------------------------ | ------------------- | --------- | --------- | ---------- | ---------- | ----------- |
| 40.0 | 40.0 | 9,689,439.0 | 24.0 | 24.0 | 24.0 | 7030.0 | 34,088.0 | 19,211.75 |

### 3. Average Risk Score (AVR)
   * **Software used to implement the model**: Python, pandas
   * **Version of the modeling software**: Python 3.9.12
   * **Calculation of average risk score**:
     * Using industry size standards, we calculated standard 'expected' figures for 'per employee' data for UTILITIES_PROCEED, PAYROLL_PROCEED, MORTGAGE_INTEREST_PROCEED, REFINANCE_EIDL_PROCEED, HEALTH_CARE_PROCEED, DEBT_INTEREST_PROCEED, InitialApprovalAmount, CurrentApprovalAmount, ApprovalDifference, and ForgivenessAmount.
     * We then calculated 'deviant' figures by calculating the difference between actual and 'expected' figures for each loan.
     * Risk scores for each figure were calculated by percentile rank among all loans.
     * The final average risk score is a simple arithmetic mean of risk scores:

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
 
**Columns as outputs of blended model**: 'final_anomaly_score', 'final_blended_anomaly_indicator'

# General Exploratory Data Analysis

#### Correlation Heatmap

Initial and Current Approval Amount were both highly correlated with ForgivenessAmount, indicating both in a statistical sense the higher the approval amount, the higher the forgiveness amount but logically of the loans that were forgiven, it would seem that they were mostly, if not completely forgiven, rather than just partially.

Initial and Current Approval Amount were both highly correlated with PAYROLL_PROCEED, indicating that most loans were used to process Payroll rather than utilities, mortgage interest, rent, EIDL refinancing, healthcare, or debt interest. Ranked by correlation: payroll, rent, healthcare, mortgage interest, debt interest, EIDL refinance.

Initial and Current Approval amount were highly correlated with JobsReported, indicating that the SBA and lenders generally approved higher loan amounts for businesses that reported more jobs.

![Correlation Heatmap](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/ee4f7b246230f672a385bee2b54b08c403ef758f/Graphs/ppp_eda_corr.png)


#### Initial and Current Approval Amount Scatter Plot

The lower the initial and current approval amount, the more likely loans will center around the line of best fit. The distribution of residuals is not constant as initial and current approval amounts rise as we can see points more sporadically plotted further from the line of best fit.

![Init/Current Approval Scatter](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/ee4f7b246230f672a385bee2b54b08c403ef758f/Graphs/ppp_eda_intial_current_scatter.png)


#### Applications by Industry

Full service restaurants by far accounted for the most number of loan applications. Professional offices like Offices of Physicians, Offices of Lawyers, Offices of Dentists were also particularly prevalent for industries where loan applications were high.

![Loan Apps by Industry](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/raw/d106ed5d65b20b7452d978c242dae2fdc14b9097/ppp_eda_industries_count.png)

#### Applications by Loan Draw

Roughly 70% of all applications were for First Draw PPP loans, with the remainder representing Second Draw PPS loans. Officially, only those who have fewer than 300 employees, have previously received a First Draw PPP loan or can demonstrate at least a 25% reduction in gross receipts between comparable quarters in 2019 and 2020 were eligible for Second Draw PPP loans.

![Draw Plot](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/raw/796f17f3202385c02922176d58d13288f9a8c37a/ppp_eda_draw_plot.png)


#### Loan Term by Draw

In general, we can say that Second Draw PPS loans on average had a higher loan term than that of First Draw PPP loans. The mean loan term for PPP loans was 24.5 months while for PPS loans it was 52 months.

![Loan Term Histogram](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/ee4f7b246230f672a385bee2b54b08c403ef758f/Graphs/ppp_eda_term_draw.png)


#### Loans by State

In accordance with population size, California, Texas, New York, and Florida were the top 4 states for the number of applications.

![States](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/ee4f7b246230f672a385bee2b54b08c403ef758f/Graphs/ppp_eda_state.png)


#### Current Loan Amount Per Employee by Jobs Reported

We can start to analyze outliers here by observing very large loan amounts borrowed for companies with very low numbers of jobs reported. Many companies reporting less than 10 employees can be seen to have borrowed excessively large loan amounts.

![Current PE by JR](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/ee4f7b246230f672a385bee2b54b08c403ef758f/Graphs/ppp_eda_loan_amount_emp.png)


# AVR Model Exploratory Data Analysis

After calculating the average risk score for each loan, we have prepared the following EDA:

#### Distribution of Average Risk Scores

The mean average risk score for all loans was 0.228 and the threshold for the top 1.5% of risk scores was 0.545. Below are some other notable thresholds:

* Threshold for the top 10% of risk scores: 0.394
* Threshold for the top 5% of risk scores: 0.442
* Threshold for the top 1% of risk scores: 0.586

![Average Risk Score Histogram](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/ee4f7b246230f672a385bee2b54b08c403ef758f/Graphs/ppp_avr_score_hist.png)


### Correlation of Numerical Features with Average Risk Score

The deviant amounts for Forgiveness Amount, Initial Approval Amount, Current Approval Amount were most highly correlated with average risk score despite all deviant risk scores being equally weighted in the Average Risk Score calculation (i.e., actual amount - expected amount based on industry size standards).

![Correlation of AVR with Numerical Features](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/478a2058ff90bbc2195f3939f56858435c0b5460/Graphs/ppp_avr_corrRED.png)


# scikit-learn Isolation Forest Model Exploratory Data Analysis

#### Distribution of SKL IF Anomaly Scores

The mean for anomaly scores from the sklearn Isolation Forest model was 0.0156. The model outputted 1.01% of the dataset as suspected anomalies.

![sklearn Score Histogram](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/ee4f7b246230f672a385bee2b54b08c403ef758f/Graphs/ppp_skl_score_hist.png)


#### Feature Importance for SKL IF

PAYROLL_PROCEED_per_empoyee, Size standards in number of employees, ForgivenessAmount, and JobsReported were the most important features in this model. BorrowerState closely led and was noted for further EDA at the end of the final model.

![sklearn Feature Importance](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/0fa990e139670c543cc9016fea873dc8b2696d67/Graphs/ppp_sklearn_feature_importanceRED.png)


#### Surrogate Model

We ran a surrogate model to provide a simplified interpretable model that mimics the predictions of our more complex and computationally expensive Isolation Forest model. This surrogate model is an Isolation Forest model with just one tree and the following parameters:

```
global_surrogate_dt = H2OIsolationForestEstimator(model_id = model_id,
                                               ntrees = 1, max_depth = 3,
                                               sample_rate = 1, mtries = 2, seed=12345)
global_surrogate_dt.train(training_frame = train, x = anomaly_inputs, y = "anomaly")
```

**Model Summary**:

| Number of Trees | Number of Internal Trees | Model Size in Bytes | Min Depth | Max Depth | Min Leaves | Max Leaves | Mean Leaves |
| --------------- | ------------------------ | ------------------- | --------- | --------- | ---------- | ---------- | ----------- |
| 1.0 | 1.0 | 133.0 | 3.0 | 3.0 | 3.0 | 6.0 | 6.0 | 6.0 |

*Since the surrogate isolation forest model has just one decision tree, we have named it a decision tree but we would like to note that the model is still used in the context of anomaly detection and not classification since this is an unsupervised learning task.*

Here we can interpret the rules of the tree where UTILITIES_PROCEED_per_employee, deviant_ApprovalDifference, ServicingLenderCity, JobsReported, HEALTH_CARE_PROCEED and deviant_JR (jobs reported) were some of the most important features for splitting.

![Surrogate Model](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/ee4f7b246230f672a385bee2b54b08c403ef758f/Graphs/ppp_sklearn_surrogate_dt.png)


# H2O IF Model Exploratory Data Analysis

#### Distribution of H2O IF Anomaly Scores

The mean anomaly score for this model was 0.005, with the top 2.6% of scores being assigned as suspected anomalies by the model. The score threshold for these top 2.6% suspected anomalies was 0.036.

![H2O IF Anomaly Scores Histogram](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/ee4f7b246230f672a385bee2b54b08c403ef758f/Graphs/ppp_h2o_score_hist.png)


#### Correlation of Numerical Features with H2O IF Model Anomaly Scores

InitialApprovalAmount (0.42), CurrentApprovalAmount (0.42), PAYROLL_PROCEED (0.37), and ForgivenessAmount (0.37) were top for strong positive correlation with the anomaly risk score for this model.

![H2O IF Anomaly Score Correlations](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/0fa990e139670c543cc9016fea873dc8b2696d67/Graphs/ppp_h20_if_corrRED.png)


#### Geographical Analysis of Suspected Anomalies from H2O IF Model

The 'Top 10 States by Anomaly Percentage per State' graph at the bottom shows Wyoming (13.9%), Alaska (12.8%), Alabama (5.9%), and Wisconsin (5.0%) were the top 4 known states where suspected anomalous loans occurred the most. 

The top two graphs show clearly just how different the top 10 states for suspected anomalous loans per 100,000 people are compared to top states for normal loans. Wyoming (51 anomalous loans per 100k) and Alaska (46 anomalous loans per 100k) had the highest absolute number of suspected anomalous loans adjusted for state population size.

In comparison, DC (641 normal loans and 14 anomalous loans per 100k), North Dakota (402 normal loans and 12 anomalous loans per 100k), and Massachusetts (361 normal loans and 8 anomalous loans per 100k) were the top states for number of normal loans adjusted for state population size, whilst still exhibiting low anomalous loan rates.

![Geo Analysis H20](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/0fa990e139670c543cc9016fea873dc8b2696d67/Graphs/ppp_h2o_geoRED.png)


#### Industry Analysis of Suspected Anomalies from H2O IF Model

New Car Dealers (2.03%), Full-Service Restaurants (1.67%), Couriers and Express Delivery Services (1.65%), and Limited Full Service Restaurants (1.41%) were top 3 known industries for suspected anomalous loans. Almost 8% of all suspected anomalous loans either did not report a valid NAICS code on their application or NAICS code data was missing in the SBA data collection process.

![H2O Industry Analysis](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/0fa990e139670c543cc9016fea873dc8b2696d67/Graphs/ppp_h2o_industriesRED.png)


![H2O Industries Word Cloud](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/ee4f7b246230f672a385bee2b54b08c403ef758f/Graphs/ppp_h2o_industries_wc.png)

# Final Blended Model Exploratory Data Analysis

#### Distribution of Final Risk Scores

The vast majority of loans had a risk score between 0.0 and 0.2. The mean risk score was 0.13 and the histogram below displays right skew as expected. The top 1.5% of loans had a risk score threshold of 0.328.

![Final Risk Score Histogram](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/ee4f7b246230f672a385bee2b54b08c403ef758f/Graphs/ppp_final_score_hist.png)


#### Jaccard Heatmap of Final Model Components (AVR, H2O IF, SKL IF)

* The two machine learning models (H20 IF and SKL IF) had the highest intersection of unique loans with a Jaccard Similarity Coefficient (JSC) of 0.3279.

* The AVR model had a JSC of 0.1653 with the SKL IF model.

![Jaccard Heatmap](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/0fa990e139670c543cc9016fea873dc8b2696d67/Graphs/ppp_jaccardRED.png)

### Tableau Dashboard for Blended Anomalies 

* After combining scores from various models, a total of 14,484 anomalous loan applications were identified out of approximately one million applications.

* Analysis reveals 14,053 anomalous loans processed via the PPP method, compared to only 431 through the PPS method, indicating a higher prevalence of anomalies in the PPP method.

* The map visualization shows normalized anomalies of loans per state, adjusted for population. States with darker shades have a higher ratio of anomalies relative to their population.

* The bubble chart highlights the number of loan applications by industry. Larger bubbles indicate more applications and darker bubbles show a higher number of anomalies within an industry.

* The bar graph details the top anomalous lenders, with percentages atop each bar showing the proportion of anomalous loans to total loans lent by each lender.
  
![Dashboard 1](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/main/Graphs/D1.png)



* The top-right graph on the next dashboard indicates increasing percentages of anomalous data as employee group size increases, with larger companies more likely to have anomalous loan applications.

* The bottom-left graph presents a stacked bar chart comparing anomalous and non-anomalous loan applications for veterans and non-veterans, showing no anomalies in the veterans' category and the highest proportion in the non-stated category.

* Box plot illustrates the distribution of current approval amounts by jobs reported, with anomalous loan applications (orange dots) mostly appearing as outliers, suggesting these loans have atypical approval amounts.
  

![Dashboard 2](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/main/Graphs/D2_1.png)


# Ethical Considerations

* **Racial and Demographic Bias**: Excluding explicit demographic information doesn't eliminate the risk of encoding bias. Anomaly detection models can be trained on proxies of correlated features where racial of demographic bias is still perpetuate. 
* **Ambiguity in Validation**: In unsupervised anomaly detection, the absence of labeled data identifying actual anomalies or fraud makes it challenging to validate the model's predictions accurately. We encourage analysis and decisions to be made based on differences of trends in features between suspected anomalies and suspected normal loans. This paired with significant domain knowledge of fraud detection for loans of this type will mitigate this ethical concern.
* **Transparency and Complexity**: Blended machine learning models can be highly complex. The incorporation of three algorithms makes interpretability difficult. To the best of our ability, we have provided as transparent and interpretable of a model card as possible.


# Risk Considerations
* **False Positives and False Negatives**: Even without labels, anomaly detection models may incorrectly label normal instances as anomalies (false positives) or fail to identify actual anomalies (false negatives).
* **Model Robustness and Generalization**: This model may perform well on this PPP dataset, but might fail to generalize to a new loan program dataset.
* **Data Quality**: The dataset included many missing values, some of which were identified as missing from the original loan applications. However, some missing values may be the result of poor data collection practices from the data sources provided. There is little evidence of how to identify the difference.

These risks can be mitigated by applying decision-making paired only with extensive domain knowledge of fraud detection.


# Potential Next Steps
* Run a cost-benefit analysis of formally investigating anomalous loans
* Formally investigate the 2642 loans identified as suspected anomalies by all three model components
* Adjust additional hyperparameter settings
* Employ generative modelling to augment the training set and address data imbalance, improving existing anomaly detection modeling
* Consult with domain expert improve fraud feature engineering


# Author Contributions
* RH served as the primary contributor for the model card
* KH and PS contributed equally for the SKL IF notebook
* BW served as the primary contributor for the H2O IF notebook
* RH served as the primary contributor for the AVR model notebook
* PS, KH, BW, and RH contributed equally to EDA across all notebooks
* PS, KH, and BW contributed equally to the EDA dashboards using Tableau



