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
  <br>
Our preliminary Exploratory Data Analysis (EDA) indicated a potential way of clustering columns in the transaction dataset by matching the row with missing information (NaN). It appeared that certain columns contained uniform amounts of missing data; these rows were further found to be matching amongst all the columns within the same data cluster. The results of this clustering (based on number of NaNs found in the column) is shown in Fig. 1.
</p>

![Img](/assets/img/piechart_V_corr_red.JPG)

Fig. 1. Distribution of NaN values in the transaction dataset.

<p style="text-align: justify;">
  After grouping the columns together in this way, a correlation analysis on the groups of features was performed, and for each group, the columns were organized into subgroups such that all columns in each subgroup had a correlation >0.8 with each other. Further, a single representative column (the one with the largest variance) was chosen as representative from this subgroup. A sample correlation plot for one of the groupings is shown in Fig. 2. This analysis is similar to the work of Chris Deotte [1] 
</p>

![Img](/assets/img/V12-V34_sample_corrplot.jpg)

Fig. 2.Correlation heat map for the features V12 to V34 (One of the groups)

<p style="text-align: justify;">
<b>2. Principal Component Analysis of the V columns</b>
  <br>
  The V components form the majority of the features in the transaction data. As such, applying a suitable dimensionality reduction scheme to capture the variance in the V columns is a good step in reducing model complexity, overfitting and interpretability. PCA is a suitable dimensionality reduction technique that provides an orthogonal linear transformation of the features to project the high-dimensional data onto a set of uncorrelated axes (called principle components). The transformed data are ordered in decreasing order of variance captured, so that the subset of selected features maximize the variance in the representation. 
  </p>
<p style="text-align: justify;">
  We decided to apply PCA to only individual groups of features (such as the D features, V features, etc.) independently, instead of the entire dataset as a whole. This is because the different classes of features could be either categorical or numeric (i.e. different types of data) and also had very different scales. Moreover, only the PCA on the V data appeared to be useful in reducing dimensionality while maintaining a similar level of performance; when applied to the other categories of features, the performance of the model drastically worsened. Fig. 3. Shows the scree plot of the PCA on the V columns. As can be seen, the first few components do not account for much of the variance (in fact, ~50 components are needed to capture 99% of the variance in the V columns). This is in line with expectations for a complicated dataset as in this case; as such, plotting the first 3 PCs did not yield much separation between the classes of data (genuine and fraudulent transactions).
</p>

![Img](/assets/img/V_pca.jpg)

Fig. 3. Scree plot of PCA on V.


<p style="text-align: justify;">

<b>3. SMOTE Oversampling of the dataset to overcome imbalance</b>
<br>
Since most of the supervised learning methods we used were tree-based, they performed well on the classification task in spite of the huge discrepancy in quantity of data for the genuine and fraudulent categories. However, we attempted to compare our methods with another form of classification (logistic regression) to ascertain the effectiveness of alternative methods. To prepare the data for this, we decided to use SMOTE (Synthetic Minority Oversampling TEchnique) followed by random undersampling of the genuine data. SMOTE draws a line between random points (that are amongst k-Nearest Neighbors of each other) in the minority class in the high dimensinal space, and artificially synthesizes data points along this line. After applying SMOTE to the minority class to achieve a class ratio of 0.2, we used random undersampling on the genuine data to reduce the number of datapoints to the original number. We recognize that this undersampling could involve discarding some useful data points; however, it was necessary to make the dataset less unwieldy and run the logistic regression in a computationally efficient way. Fig. 4. illustrates the SMOTE procedure for a lower-dimensional case; the same concept may be extended to the higher dimensional case.
</p>

![Img](/assets/img/SMOTE_sample.jpg)

Fig. 4. SMOTE on a low-dimensional dataset. [2]

<b>References</b>
<br>
[1] https://www.kaggle.com/cdeotte/eda-for-columns-v-and-id
[2] https://rikunert.com/SMOTE_explained
