---
layout: page
title: Supervised Learning
subtitle: LightGBM, Random Forest, XGBoost
---

<p style="text-align: justify;">
For this project, we attempted a variety of supervised classification methods that are well suited to binary classification problems with severe class imbalance. In this section, we describe some background theory, our approaches and results obtained from this step.
</p>

<p style="text-align: justify;">
  <b>1. Logistic Model</b>
</p>

<p style="text-align: justify;">
  <b>2. Random Forest Classification</b>
</p>
Random forest is a classical tree-based ensemble learning method that constructs multiple individual decision trees in order to evaluate a class assignment of a data point.
<p style="text-align: justify;">
  <b>3. XGBoost Classifier</b>
</p>

<p style="text-align: justify;">
  <b>4. LightGBM Classifier</b>
LightGBM is a gradient boosting tree based supervised learning method. Gradient boosting is a machine learning technique for regression and classification problems, which produces a prediction model in the form of an ensemble of weak prediction models, typically decision trees. LightGBM uses histogram-based algorithms, which bucket continuous feature (attribute) values into discrete bins. This speeds up training and reduces memory usage. Advantages of histogram-based algorithms include the following:
<ul>
<li>Reduced cost at each split</li>
<li>Reduce memory usage</li>
<li>Reduce communication cost for parallel learning</li>
</ul>
</p>

<p style="text-align: justify;">
  <b>Approach and Results</b>
</p>
 We attempted these supervised learning methods on two cases of data - 1. the preprocessed data following the previous steps, and 2. PCA implmeneted to this preprocessed data. Moreover, the SMOTE oversampled data was used for the logistic regression case to obtain a more balanced training set.. After training each model, we let the model produce prediction of the test data and recorded their score through kaggle submission. The hyper-parameters were manually and lightly tuned to obtain moderate test scores. Followig table shows the results.
 
Table 1: Result from each model

<table style="width:100%">
  <tr>
    <th>Model(s) Name</th>
    <th>Hyper-parameters</th>
    <th>Prediction Score</th>
    <th>Prediction Score with PCA</th>

  </tr>
  <tr>
    <td>Logistic Regression</td>
    <td> - </td>
    <td>0.81</td>
    <td> - </td>
  </tr>
  <tr>
    <td>Random Forest Classification</td>
    <td> - </td>
    <td>0.893633</td>
    <td>0.893633</td>
  </tr>
  <tr>
    <td>XGBoost Classifier</td>
    <td> - </td>
    <td>0.928964</td>
    <td>0.921232</td>
  </tr>
  <tr>
    <td>LightGBM Classifier</td>
    <td> - </td>
    <td>0.926462</td>
    <td>0.921232</td>
  </tr>
</table>
