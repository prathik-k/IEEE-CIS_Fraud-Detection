---
layout: page
title: Data Preprocessing
subtitle: Data Feature Engineering, Data Warehousing, Data Cleaning
---

<p style="text-align: justify;">
The preprocessing step is especially critical for this project, since the data is heavily skewed in favor of one class (genuine transactions). Extracting the most useful features and generating new ones would require elimination of redundant columns and combining some of them. This section provides an overview of our data preprocessing for the training transaction and ID datasets and feature engineering procedures.  
</p>

**1. Dataframe Size Reduction**  
<p style="text-align: justify;">
&nbsp;&nbsp;This step is essential to post-process the Pandas dataframe after reading in from the initial train and test datasets. Essentially, the procedure is performed to convert the implicit datatypes assigned by Pandas (typically the highest - bit category for the respective datatype, such as int64 and float64) to the datatype with the lowest possible memory burden. The range of numerical values for each column is considered, and a datatype with int or float precision (as required) is assigned so that the largest number in the column may be stored. This procedure drastically reduces memory requirements of all the dataframes (by ~50-60%).
</p>

**2. Noise Removal**  
<p style="text-align: justify;">
&nbsp;&nbsp; It is important to remove the noise data from the columns as a lot of outliers may affect our final prediction model. For this, we scan all the columns and remove a columns if it has more than 90% of data missing. We also replace all infinity values with -1 in numerical columns and 'missing' in categorical columns. 

Another example of this is Cards columns. Figure 1 shows that data. We have columns Card1 to Card6 columns that are defined as categorical, but columns Card1, Card3, Card5 have numeric values. We remove the data points that don't occur frequently.
</p>

![Img](/assets/img/card-data.png)

<center>Figure 1: Card data is a mixture of Numerical and Categorical data</center>

**3. Feature Enginnering**  
<p style="text-align: justify;">
&nbsp;&nbsp; We need to parse some of the categorical features and create one or features from them. For e.g, the 'id_30' column has operating system information. We parse the column for words such as 'Mac', 'iOS' etc and create an new column. Similarly the 'DeviceInfo' (Figure 2) column has string values that contain device name and version. We parse them for values like 'SAMSUNG', 'MOTO' etc and create two new feature for device name and version. Similarly, we parse for browser name, version, screen width, height etc.

For emails we parse sender and receiver emails and bin them into domain name like google and suffix like 'org'
</p>

![Img](/assets/img/DeviceInfo-distribution.png)

<center>Figure 2: The DeviceInfo column and its distribution</center>
