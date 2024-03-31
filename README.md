# Loan_Dataset_Analysis
# DPDzeroData analyst assignment - 2024

This assignment is designed to give you a flavour for the kind of data analysis a typical data analyst does at DPDzero. Data analysts here us leverage **Jupyter notebooks** heavily to do their tasks and you are expected to use the **same tool** to do the given task.

## **Dataset**

DPDzero is a data driven organisation where most decisions are taken based on data analyst recommendations. Here is a typical data set (it is anonymised) that a data analyst may look at. 

[Data_Analyst_Assignment_Dataset.csv](https://prod-files-secure.s3.us-west-2.amazonaws.com/0fb337c8-6186-4010-911c-38ba2e525070/7e55b4b1-5878-4d1c-9dce-75419c39c4c5/Data_Analyst_Assignment_Dataset.csv)

The dataset contains Loan data for various borrowers in a loan portfolio

The columns are as follows

| Column Name | Description |
| --- | --- |
| Amount Pending | This is the EMI amount pending. |
| State | The borrower’s state. |
| Tenure | Total tenure of the borrower. |
| Interest Rate | Interest rate of the loan. |
| City | The city of the borrower. |
| Bounce String | This is a string that explain’s customer’s bounce behaviour since the disbursal of the loan - bounce means that the customer did not end up making the payment
• S or H- No bounce in that month
• B or L - Bounce in that month
• FEMI - first EMI - no known behaviour
• Last character denotes the last month - first character denotes the first month on book - for example SSB means that customer was on book for 4 months and he has bounced the in the last month |
| Disbursed Amount | The total disbursed amount of the loan. |
| Loan Number | The unique identifier for the loan. |

We recommend that you explore the data before you go to the next section of assignment.

## Derive values from the raw data

When a data analyst gets data from the lender at DPDzero, a lot of information should be derived and data set needs to be enhanced. As part of this assignment, derive the following values

### Calculate the risk labels for all the borrowers.

| Unknown risk | New customers |
| --- | --- |
| Low risk | Customers who have not bounced in the last 6 months
 |
| Medium Risk  | These are customers who have bounced at less than twice in the last 6 months - The bounce should not have occurred in the last month
 |
| High risk  | every other customer |

### label all customers based on where they are in their tenure

| Early tenure | Customers who are in the book for 3 months |
| --- | --- |
| Late tenure | Customers who are 3 months away from closing the loan |
| Mid tenure | Everyone else |

<aside>
🤔 Hint: Read the delinquency string description above

</aside>

### Segment borrowers based on ticket size

Distribute the data into 3 cohorts based on ticket size. This is to be done such that sum of amount pending in each cohort should be approximately equal. Apply the following labels on each borrower based on this logic:

```
1. Low ticket size
2. Medium ticket size
3. High ticket size
```

## Give channel spend recommendations

At DPDzero, we employ various channels to communicate with the borrowers so that we can get the repayment done - Different channels have different costs & various degrees of effectiveness.

You are allowed to spend 3 kinds of resources to reduce the overall bounce

1. Whatsapp bot: This is the cheapest medium - it will cost 5 rupees per borrower 
2. Voice bot: This is the mid-cost - it will cost 10 rupees per borrower
3. Human calling: This is the costliest option - it will cost 50 rupees per borrower

Whatsapp bot will work well in the following scenarios

1. Customers with great repayment behavior
2. Customers with first EMIs
3. Customers who have low EMIs

Voice bot will work well in the following scenarios 

1. Customer who know Hindi or English - Metropolitan areas have high probability of english speakers & english speakers have typically lower interest rates
2. Customers who have had low bounce behaviour
3. Customers with low or medium sized EMIs

Human calling will work on all scenarios but is the costliest option and you need to use this channel only where absolutely necessary

Your job is to segment the borrowers into these 3 channels of spend category and minimise the overall spend while maximise on time repayment.
