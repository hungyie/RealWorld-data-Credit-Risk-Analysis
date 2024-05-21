# RealWorld-data-Credit-Risk-Analysis

This is a dataset for a take-home assessment of a finance company named Moneylion. The main goal of the notebook is to enhance the company's ability to identify loans at risk of default by creating a model that complements existing screening systems and reduces potential losses.

## Important Preparation

As per our objective, our model aim to serve as a complementary to the current screening system. We will narrow down our focus to loans that **have been funded**. From here, we will further dive in and hopefully to provide a more indepth analysis.

Refering to the data dictionary, the "Return Item" under loanStatus column seems to be a good fit for our target variable as it indicate a missed payment due to insufficient funds. But we are also curious with other loanStatus like "External/Internal collection". Does it really indicates timely repayment? Due to the absence of additional information, we've decided to stick with "Return Item" as our primary target variable for now. Further insights could be gained with more detailed data on these other categories.

## Data Understanding
We received a zipfile which contains 3 dataframe (loan, payment, clarity underwriting variavles). Below is a summarization for these 3 dataframe  
"loan.csv" : Our key dataframe   
"payment.csv" : Consist payment info that comes after loan approval. Since our model's goal is to act as a secondary safety measure prior to loan approval, this dataset will be excluded to avoid information leakage.  
"clarity_underwriting_variables.csv" : This dataset encompasses variables retrieved from clarity, aiding in the underwriting process of loans. In simpler terms, it involves assessing the risk associated with a loan by evaluating various factors (columns) to determine the probability of the borrower repaying the loan. Upon reviewing the dataset, it appears that the "clearFraudScore" serves as a summarizing score derived from all other columns in the dataset. We assume that all other columns are well represented by this particular column. Consequently, we may consider dropping all other columns to streamline our dataset and reduce dimensionality.  

## EDA
In this section, we will categorize the dataset into three types: Categorical, Datetime, and Numerical data. We will process each data type separately, create new features where applicable, and provide business insights to the company.

We frist start from categorical columns:  
![Categorical Feature](Money_Lion_Images/1.png)  
Finding: 

- Semi-monthly and monthly repayment schedules have nearly twice the likelihood of loan default compared to biweekly and weekly repayments. This is likely because weekly payments involve smaller amounts each time. As a business strategy, the company should consider promoting more frequent repayment schedules to reduce the risk of loan defaults.
- We observed that lead costs between 25 and 50 are associated with the highest default risk. Upon further investigation, we found that these leads are categorized as "lead" in the lead type column. MoneyLion is advised to reduce the approval rate for this category to mitigate risk.
- The history of paid-off loans does not significantly impact the associated default risk.
- Many states have a loan default rate of 10% or higher. It is recommended that the company reduce loan approvals in these states, with particular attention to Virginia (VA), which has a 20% default rate.
- Our dataset shows a significant class imbalance, which we will address in the modeling section.

