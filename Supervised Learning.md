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
The standard logistic regression model was used along with SMOTE oversampling which is described in the previous senction.
</p>

<p style="text-align: justify;">
  <b>2. Random Forest Classification</b>
</p>
Random forest is a classical tree-based ensemble learning method that constructs multiple individual decision trees in order to evaluate a class assignment of a data point. The prediction is made at the end of the multiple trees, by majority voting their results.
</p>

<p style="text-align: justify;">
  <b>3. XGBoost Classifier</b>
</p>
XGBoost is a tree-based ensemble learning framework that implements gradient boosting method. Gradient boosting is a machine learning technique for regression and classification problems, which produces a prediction model in the form of an ensemble of weak prediction models, typically decision trees. Following are the features that XGBoost differ from other tree-boosting algorithms[1]:
<ul>
<li>novel tree learning algorithm that handles sparse data</li>
<li>weighted quantile sketch procedure for approximate tree learning</li>
<li>out-of-core computation to effectively process data</li>
</ul>
</p>

<p style="text-align: justify;">
  <b>4. LightGBM Classifier</b>
</p>
LightGBM is another gradient boosting tree based supervised learning method. LightGBM uses histogram-based algorithms, which bucket continuous feature (attribute) values into discrete bins. This speeds up training and reduces memory usage, even compared to XGBoost. Advantages of histogram-based algorithms include the following:
<ul>
<li>Reduced cost at each split</li>
<li>Reduce memory usage</li>
<li>Reduce communication cost for parallel learning</li>
</ul>
</p>

<p style="text-align: justify;">
  <b>Approach and Results</b>
</p>
 We attempted these supervised learning methods on two cases of data - 1) the preprocessed data following the previous steps, and 2) PCA implmeneted to this preprocessed data. Moreover, the SMOTE oversampled data was used for the logistic regression case to obtain a more balanced training set.. After training each model, we let the model produce prediction of the test data and recorded their score through kaggle submission. The hyper-parameters were manually and lightly tuned to obtain moderate test scores. Followig table shows the results.
 
Table 1: Result from each model

<table style="width:100%">
  <tr>
    <th>Model(s) Name</th>
    <th>Prediction Score</th>
    <th>Prediction Score with PCA</th>
    <th>Hyper-parameters</th>
  </tr>
  <tr>
    <td>Logistic Regression</td>
    <td>0.81</td>
    <td> - </td>
    <td>(SMOTE) sampling_strategy=0.05</td>
  </tr>
  <tr>
    <td>Random Forest Classification</td>
    <td>0.893633</td>
    <td>0.893633</td>
    <td> - </td>
  </tr>
  <tr>
    <td>XGBoost Classifier</td>
    <td>0.928964</td>
    <td>0.921232</td>
    <td>n_estimators=250,
        max_depth=15,
        learning_rate=0.05,
        subsample=0.9,
        colsample_bytree=0.9,
        tree_method = 'hist'</td>
  </tr>
  <tr>
    <td>LightGBM Classifier</td>
    <td>0.928964</td>
    <td>0.921232</td>
    <td>max_bin = 63,
    num_leaves = 255,
    num_iterations = 500,
    learning_rate = 0.01,
    tree_learner = 'serial',
    min_data_in_leaf = 1,
    min_sum_hessian_in_leaf = 100,
    sparse_threshold=1.0</td>
  </tr>
</table>

<p style="text-align: justify;">
  <b>AUC-ROC curves</b>
</p>

![Img](/assets/img/Logistic_Regression.png)
![Img](/assets/img/LightGBM.png)
![Img](/assets/img/LightGBM_with_PCA.png)
![Img](/assets/img/XGBoost.png)
![Img](/assets/img/XGBoost_with_PCA.png)


<b>References</b>
<br>

[1] Tianqi Chen and Carlos Guestrin. Xgboost: A scalable tree boosting system. In Proceedings of the 22Nd ACM SIGKDD International
Conference on Knowledge Discovery and Data Mining, pages 785–794. ACM, 2016.

