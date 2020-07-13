---
layout: page
title: Conclusion
subtitle: Discussion and Future steps
---

<p style="text-align: justify;">
  <b>1. Comparison of Model Performances </b>
  <br>
Overall, we achieved good performance with our tree-based models. Out of the three tree-based models (XGBoost, LightGBM and Random Forest), the XGBoost and LightGBM models yielded the best performance with an optimal parameter set, and slightly outperformed the Random Forest classifier. Although XGBoost performs marginally better, we are inclined to suggest LightGBM as the best model of choice for this applications due to its significantly shorter traning time. Unsurprisingly, the SMOTE - Logistic Regression pipeline does not perform as well as the other tree-based methods we have implemented. We attribute this larger error to the following potential sources:
  <ul>
    <li>The oversampling procedure was accompanied by undersampling - this meant throwing away useful data, and consequently less real data points for the model to learn from.
     <li> Logistic regression performs optimally on datasets with fully independent features. Naturally, as evidenced by the unsupervised learning (with the correlation based clustering and PCA), we see that full independence between features in the dataset has not been achieved. This drastically reduced the predictive capability of the model.
     <li> Assuming the specific functional form (as constrained by the governing equation of logistic regression) may not always provide an optimal solution, as was seen in this case.
   </ul>

<b>2. Deployment of Model </b>
  <br>
  The overall utility of such a model to predict credit card fraud would be to predict the probability of a transaction being fraudulent in an online setting. There are two main characteristics the model would need to have to be well-suited for this purpose:
  <ul>
    <li>Being lightweight - our LightGBM model is fairly lightweight (with a stored size of 2.75 Mb). This alows for easy deployment of our model on a server. </li>
    <li>Providing fast results. Typical fraud detection models have to detect fraud within microseconds (by assigning a probability of belonging to either class). Our LightGBM model also excels at this; the prediction on the test dataset is performed in under 25 microseconds. </li>
  </ul>
  As such, we believe our model is fairly well suited for the application of credit card fraud detection. Moreover, after submitting our best result (the LightGBM model) to the Kaggle, we obtained an AUC-ROC of 0.92 - this would place us in the top 100 performances in the contest if it were still running.
</p>      
