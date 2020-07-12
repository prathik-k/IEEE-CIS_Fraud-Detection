---
layout: page
title: Unsupervised Learning
subtitle: PCA, SMOTE
---

<p style="text-align: justify;">
The unsupervised learning section for this project is an extension of the data preprocessing step. Given the extremely high dimension of the input data (~370 columns) and the large class imbalance, the unsupervised techniques of dimensionality reduction/data rebalancing appears essential. Three major techniques were investigated for this section - reduction based on correlation analysis, PCA and SMOTE oversampling (for the logistic regression section). The largest collection of features in the transaction dataset is the set of Vesta engineered Vxx features; as such, our dimensionality reduction efforts were focused predominantly on this set of data.
</p>

<p style="text-align: justify;">
  <b>1. Reduction of the number of components in transaction data with correlation metrics</b>
  <b>Method</b>
  Our preliminary EDA indicated a potential way of clustering columns in the transaction dataset by matching the row with missing information (NaN). It appeared that certain columns contained uniform amounts of missing data; these rows were further found to be matching amongst all the columns within the same data cluster. The results of this clustering (based on number of NaNs found in the column) is shown in Fig. 1.
  
  

</p>


