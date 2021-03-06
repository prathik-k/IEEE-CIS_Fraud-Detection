---
layout: page
title: Supervised Learning
subtitle: Logistic Model, LightGBM, Random Forest, XGBoost
---
<style TYPE="text/css">
code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}
</style>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
    displayAlign: "center",
    tex2jax: {
        inlineMath: [['$','$'], ['\\(','\\)']],
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'] // removed 'code' entry
    }
});
MathJax.Hub.Queue(function() {
    var all = MathJax.Hub.getAllJax(), i;
    for(i = 0; i < all.length; i += 1) {
        all[i].SourceElement().parentNode.className += ' has-jax';
    }
});
</script>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-AMS_HTML-full"></script>



<p style="text-align: justify;">
For this project, we attempted a variety of supervised classification methods that are well suited to binary classification problems with severe class imbalance. In this section, we describe some background theory, our approaches and results obtained from this step. The Scikit-Learn implementation was used for logistic regression and random forest classification, while XGBoost and LightGBM have full-support Python libraries.
</p>

<p style="text-align: justify;">
  <b>1. Logistic Model</b>
Logistic regression is a binary classification algorithm that is used to model the probability of a data point belonging to a class. The equation for logistic regression that models this probability is given by: <br>
$$p(X) = \frac{e^{\beta_{0}+\beta_{1}X}}{1+e^{\beta_{0}+\beta_{1}X}}$$

where $\beta_{0}$ and $\beta_{1}$ are constants that need to be computed [1]. This function is also referred to as the sigmoid function - a sample plot of the sigmoid function is shown in Fig. 1. In this project, the standard logistic regression model was used along with SMOTE oversampling which is described in the previous section.
</p>
![Img](/assets/img/sigmoid.png) 
<br>
<center>Fig. 1. The sigmoid curve. Note that the classification procedure yields a probability between 0 and 1.</center>
<p style="text-align: justify;">
  <b>2. Random Forest Classification</b>
</p>
Random forest is a classical tree-based ensemble learning method that constructs multiple individual decision trees in order to evaluate a class assignment of a data point. The prediction is made at the end of the multiple trees, by majority voting of their results. As in traditional decision trees, an information criterion is used to make splits in a tree. In our implementation, we used the Gini impurity criterion. A critical difference between Random Forest and the traditional decision tree algorithm is that only certain features are made available to each particular tree while determining split locations (which differentiates it from Bagging) and that each tree has access to only a random subset of data. This regularizes against overfitting, which is a common problem for decision tree methods. The important hyperparameters of the random forest models are shown in the table below:
<table style="width:100%">
  <tr>
    <th>Parameter Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Max depth:</td>
    <td>The maximum depth of each individual tree</td>
  </tr>
  <tr>
    <td>num_estimators</td>
    <td>The number of trees in the random forest</td>
  </tr>
  <tr>
    <td>max_features</td>
    <td>The maximum number of selected features that each tree can utilize</td>
  </tr>
</table>
<center>Table 1: Random Forest classifier hyper-parameters</center>
<p style="text-align: justify;">
  <b>3. XGBoost Classifier</b>
</p>
XGBoost is a tree-based ensemble learning framework that implements gradient boosting method. Gradient boosting is a machine learning technique for regression and classification problems, which produces a prediction model in the form of an ensemble of weak prediction models, typically decision trees. Following are the features that XGBoost differ from other tree-boosting algorithms[2]:
<ul>
<li>novel tree learning algorithm that handles sparse data</li>
<li>weighted quantile sketch procedure for approximate tree learning</li>
<li>out-of-core computation to effectively process data</li>
</ul>

Also, among the hyper-parameters XGBoost uses[3], we considered the following parameters to train our model.
<table style="width:100%">
  <tr>
    <th>Parameter Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>objective</td>
    <td>'binary:logistic' was chosed to handle this classification problem</td>
  </tr>
  <tr>
    <td>max_depth</td>
    <td>Maximum depth of a tree, which controls complexity and overfitting</td>
  </tr>
  <tr>
    <td>subsample</td>
    <td>Subsample ratio of the training instance, occuring once in every boosting iteration</td>
  </tr>
  <tr>
    <td>colsample_bytree</td>
    <td>Subsample ratio of columns when constructing each tree</td>
  </tr>
  <tr>
    <td>tree_method</td>
    <td>Tree construction algorithm. We used 'hist', a faster histogram optimized approximate greedy algorithm. </td>
  </tr>
  <tr>
    <td>metric</td>
    <td>Cost penalty for a prediction. We chose the area under the curve metric</td>
  </tr>
</table>
<center>Table 2: XGBoost hyper-parameters</center>


<p style="text-align: justify;">
  <b>4. LightGBM Classifier</b>
</p>
LightGBM is another gradient boosting tree based supervised learning method. LightGBM uses histogram-based algorithms, which bucket continuous feature (attribute) values into discrete bins. This speeds up training and reduces memory usage, even compared to XGBoost. Advantages of histogram-based algorithms include the following:
<ul>
<li>Reduced cost at each split</li>
<li>Reduce memory usage</li>
<li>Reduce communication cost for parallel learning</li>
</ul>
LightGBM supports various hyper-parameters [4]. Table 2 lists some of the important ones and the values we used:
<table style="width:100%">
  <tr>
    <th>Parameter Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>num_leaves</td>
    <td>Number of leaves in the full tree</td>
  </tr>
  <tr>
    <td>objective</td>
    <td>We chose Binary as this is a classification problem</td>
  </tr>
  <tr>
    <td>max_depth</td>
    <td>Max depth of the tree. Used to control overfitting</td>
  </tr>
  <tr>
    <td>min_child_samples</td>
    <td>Minimum number of data points needed in a child (leaf) node. This is a very important parameter to prevent overfitting.</td>
  </tr>
  <tr>
    <td>boosting_type</td>
    <td>We chose gradient boosting</td>
  </tr>
  <tr>
    <td>subsample_freq</td>
    <td>This specifies that bagging should be performed after every k iterations</td>
  </tr>
  <tr>
    <td>metric</td>
    <td>Cost penalty for a prediction. We chose the area under the curve metric</td>
  </tr>
</table>
<center>Table 2: LightGBM hyper-parameters</center>

<p style="text-align: justify;">
  <b>Approach and Results</b>
</p>
 We attempted these supervised learning methods on two cases of data - 1) the preprocessed data following the previous steps, and 2) PCA implemented to this preprocessed data. Moreover, the SMOTE oversampled data was used for the logistic regression case to obtain a more balanced training set. After training each model, we generated model prediction and evaluated its performance by submitting it on Kaggle. The hyper-parameters were manually and lightly tuned with grid search and 5-fold cross validation to obtain moderate test scores. To plot the ROC curves, a hard train-validation split was performed on to yield an 80-20 split. Table 2 shows the final results after we evaluated the models when trained on the complete set of training data.
 
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
    <td> n_estimators=200,
      max_depth=15,
      max_features=25,
      criterion='gini'      
    </td>
  </tr>
  <tr>
    <td>XGBoost Classifier</td>
    <td>0.928550</td>
    <td>0.917584</td>
    <td>n_estimators=250,
        max_depth=15,
        learning_rate=0.05,
        subsample=0.9,
        colsample_bytree=0.9,
        tree_method = 'hist'</td>
  </tr>
  <tr>
    <td>LightGBM Classifier</td>
    <td>0.925995</td>
    <td>0.922701</td>
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

<center>Table 3: Result from each model</center>

<p style="text-align: justify;">
  <b>AUC-ROC curves</b>
</p>

![Img](/assets/img/Logistic_Regression.png)
![Img](/assets/img/LightGBM.png)
![Img](/assets/img/LightGBM_with_PCA.png)
![Img](/assets/img/XGBoost.png)
![Img](/assets/img/XGBoost_with_PCA.png)
![Img](/assets/img/RandomForest.jpg)
![Img](/assets/img/RandomForest_with_pca.jpg)

<p style="text-align: justify;">
<b>References</b>
<br>

[1] http://stat.cmu.edu/~cshalizi/uADA/12/lectures/ch12.pdf <br>

[2] Tianqi Chen and Carlos Guestrin. Xgboost: A scalable tree boosting system. In Proceedings of the 22Nd ACM SIGKDD International
Conference on Knowledge Discovery and Data Mining, pages 785–794. ACM, 2016. <br>
[3]  XGBoost Docs, https://xgboost.readthedocs.io/en/latest/parameter.html<br>
[4]  LightGBM Docs, URL: https://lightgbm.readthedocs.io/en/latest/Parameters.html
</p>
