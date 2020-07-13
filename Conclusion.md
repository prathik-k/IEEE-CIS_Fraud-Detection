---
layout: page
title: Conclusion
subtitle: Review what we've done
---

<p style="text-align: justify;">
Overall, we achieved good performance with our tree-based models. Unsurprisingly, the SMOTE - Logistic Regression pipeline appears to yield the worst performance for this task. We attribute this larger error to the following potential sources:
  <ul>
    <li>The oversampling procedure was accompanied by undersampling - this meant throwing away useful data, and consequently less real data points for the model to learn from.
     <li> Logistic regression performs optimally on datasets with fully independent features. Naturally, as evidenced by the unsupervised learning (with the correlation based clustering and PCA), we see that full independence between features in the dataset has not been achieved. This drastically reduced the predictive capability of the model.
     <li> Assuming the specific functional form (as constrained by the governing equation of logistic regression) may not always provide an optimal solution, as was seen in this case.
   </ul>
</p>
