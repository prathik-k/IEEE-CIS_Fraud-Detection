---
layout: page
title: Dataset Overview
subtitle: Dataset description
---
<p style="text-align: justify;">
According to Consumer Sentinel Network Data Book 2019 from the Federal Trade Commission, credit card theft is one of the most common consequences of identity theft. In addition to negatively impacting consumers, merchants lost $9.5 billion in fraudulent transactions in 2019, with the sixth highest number of bad transactions reported in Georgia. Unsurprisingly, minimizing the cost of fraudulent transactions is critical, and several security companies have released public datasets to enable the development of effective fraud detection models. For this project, we will be using the IEEE-CIS Fraud detection dataset published by Vesta Corporation on Kaggle. Prior models on similar datasets have utilized rule induction and decision tree methods to identify fraudulent transactions. We plan to assess several of these techniques, and also attempt different methods of feature engineering/data reduction. </p>

**1. Dataset Description**  
<p style="text-align: justify;">
There are two separate categories of data in the data: the id and transaction datasets. The ID dataset consists of identification information (such as the device on which the purchase was made, Operating System used, etc.), while the transaction dataset consists of the information directly tied to the transaction (such as the type of credit card used, billing address, transaction amount, etc.). Each of these additionally have train and test versions respectively. An interesting aspect to this dataset is the presence of certain abstract engineered features. A detailed overview of the features found in each table is shown below:

Table 1: Overview of the ID dataset

Feature(s) Name | Categorical or Numeric? | Description
------------ | -------------
Content from cell 1 | Content from cell 2 | C3
Content in the first column | Content in the second column | C4


Table 2: Overview of the Transaction dataset

Feature(s) Name | Categorical/String/Numeric? (C/S/N) | Description
------------ | ------------- | -------------
TransactionDT | N | Timedelta of transaction from a certain instant
TransactionAMT | N | Amount of transaction
ProductCD | C | Product code of transaction
card1 - card6 | C | Provide information about the type of card used for the transaction
addr1-2 | S | Addresses of buyer and receiver
P_, R_ | S | email addresses of buyer and receiver
C1-C14 | N | Additional metadata for the card information
D1-D15 | N | Datetime metadata
M1-M9 | C | Match features (such as the name on card, etc.)
Vxx | N | Vesta engineered features - unknown/undisclosed implication of each column
