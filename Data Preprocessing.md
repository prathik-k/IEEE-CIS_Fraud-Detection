---
layout: page
title: Data Preprocessing
subtitle: Data Feature Engineering, Data Warehousing, Data Cleaning
---

The preprocessing step is especially critical for this project, since the data is heavily skewed in favor of one class (genuine transactions). Extracting the most useful features and generating new ones would require elimination of redundant columns and combining some of them. This section provides an overview of our data preprocessing for the training transaction and ID datasets and feature engineering procedures.  

**1. Dataframe Size Reduction **  
<div style="text-align: justify">
   This step is essential to post-process the Pandas dataframe after reading in from the initial train and test datasets. Essentially, the procedure is performed to convert the implicit datatypes assigned by Pandas (typically the highest - bit category for the respective datatype, such as int64 and float64) to the datatype with the lowest possible memory burden. The range of numerical values for each column is considered, and a datatype with int or float precision (as required) is assigned so that the largest number in the column may be stored. This procedure drastically reduces memory requirements of all the dataframes (by ~50-60%).</div>

