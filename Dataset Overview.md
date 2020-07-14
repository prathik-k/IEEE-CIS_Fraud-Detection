---
layout: page
title: Dataset Overview
subtitle: Dataset description
---




<p style="text-align: justify;">
 <b>Dataset Description </b> 
 <br>
There are two separate categories of data in the data: the id and transaction datasets. The ID dataset consists of identification information (such as the device on which the purchase was made, Operating System used, etc.), while the transaction dataset consists of the information directly tied to the transaction (such as the type of credit card used, billing address, transaction amount, etc.). Each of these additionally have train and test versions respectively. An interesting aspect to this dataset is the presence of certain abstract engineered features. A detailed overview of the features found in each table is shown below:
</p>


<table style="width:100%">
  <tr>
    <th>Feature(s) Name</th>
    <th>Categorical/String/Numeric? (C/S/N)</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>DeviceType</td>
    <td>C</td>
    <td>Type of device used for transaction</td>
  </tr>
  <tr>
    <td>DeviceInfo</td>
    <td>C</td>
    <td>Additional metadata about device</td>
  </tr>
  <tr>
    <td>id12-id38</td>
    <td>C & N</td>
    <td>Identifying features of buyer/seller (IP,browser, etc.)</td>
  </tr>
</table>

<center>Table 1: Overview of the ID dataset</center><br>


<table style="width:100%">
  <tr>
    <th>Feature(s) Name</th>
    <th>Categorical/String/Numeric? (C/S/N)</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>TransactionDT</td>
    <td>N</td>
    <td>Timedelta of transaction from a certain instant</td>
  </tr>
  <tr>
    <td>TransactionAMT</td>
    <td>N</td>
    <td>Amount of transaction</td>
  </tr>
  <tr>
    <td>ProductCD</td>
    <td>C</td>
    <td>Product code of transaction</td>
  </tr>
  <tr>
    <td>card1 - card6</td>
    <td>C</td>
    <td>Provide information about the type of card used for the transaction</td>
  </tr>
  <tr>
    <td>addr1-2</td>
    <td>S</td>
    <td>Addresses of buyer and receiver</td>
  </tr>  
  <tr>
    <td>P_, R_</td>
    <td>S</td>
    <td>email addresses of buyer and receiver</td>
  </tr>
  <tr>
    <td>C1-C14</td>
    <td>N</td>
    <td>Additional metadata for the card information</td>
  </tr>
  <tr>
    <td>D1-D15</td>
    <td>N</td>
    <td>Datetime metadata</td>
  </tr>
  <tr>
    <td>M1-M9</td>
    <td>C</td>
    <td>Match features (such as the name on card, etc.)</td>
  </tr>
  <tr>
    <td>Vxx</td>
    <td>N</td>
    <td>Vesta engineered features - unknown/undisclosed implication of each column</td>
  </tr>
  <tr>
    <td>isFraud</td>
    <td>C</td>
    <td>Whether the transaction is genuine or fraudulent not (0 or 1) - Only present in training dataset</td>
  </tr>
  
</table>

<center>Table 2: Overview of the Transaction dataset</center>

<p style="text-align: justify;">
 <b>Class Imbalance</b>
 <br>
 As with typical credit card transaction data, the number of genuine transactions far outnumbers the fraudulent transaction rate (majority of which are performed by a few bad actors). In this dataset, we observe that only about 3.5% of the training data is classified as fraudulent (shown in Fig. 1.).


</p>

![Img](/assets/img/isfraud.png)

<center>
Figure 1. Disparity between fraudulent and genuine data
</center>

<p style="text-align: justify;">
<b>Objective</b> 
 <br>
The objective of the problem is to predict a probability for a transaction in the test dataset of being fraudulent (a value between 0 or 1). The submission is evaluated in terms of area under the ROC curve between the predicted value and observed target.
</p>


