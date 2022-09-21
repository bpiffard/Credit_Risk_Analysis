# Credit_Risk_Analysis
## Overview
The pourpose of this analysis was to test differene machine learning methods ability to predict credit risk, thatis predict the status of a loan based on a selection of other variables. The credit_risk_resampling.ipynb file tests how different resampling methods affect the success fo a logistice regression on credit risk prediction. 
- **Oversampling methods used**: Naive Random Oversampling (imbalanced-learn's RandomOverSampler), and Synthetic Minority Oversampling Technique (SMOTE) oversampling (imbalanced-learn's SMOTE)
- **Undersampling methods used**: K-Means Clustering (imbalanced-learn's ClusterCentroids)
- **Combination Sampling methods used**: SMOTE with Edited Nearest Neighbor (SMOTE-ENN) (imbalanced-learn's SMOTEENN)

The credit_risk_ensemble.ipnyb file tests two ensemble learning methods: random forests (imbalanced learn's BalancedRandomForestClassifier) and a boostrap aggregation (imbalanced learn's EasyEnsembleClassifier)

## Results
### Model 1: Logistic Regression with Naive Random Oversampling
- Balanced accuracy score: 0.59
- Confusion matrix: ![Confusion matrix for random oversampler]()
- Imbalanced classification report: ![imbalanced classification report for random oversampler]()

*Analysis*: The overall accuracy of this model is rather mediocre, at 0.59. The precision score is great for low-risk predictions, but abysmal for high-risk predicitons. This means that very few of the profiles the algorithm predicted as high-risk were actually high-risk while the opposite was true for the low-risk examples. The recall scores are bit more similar bewtween the two classifications. The algorithm caught a little over half of the high-risk cases were detected, and the low-risk cases were detected only mariginally better. The F-1 score for high-risk cases reflect the awful rate of precision. The F-1 score for the low-risk examples was decent.

### Model 2: Logistic Regression with SMOTE
- Balanced accuracy score: 0.62
- Confusion matrix: ![Confusion matrix for SMOTE]()
- Imbalanced classification report: ![imbalanced classification report for SMOTE]()

*Analysis*: The balanced accuracy score is about the same as the first model. The only real difference in this model is a slightly higher recall score for the low-risk cases. This model did not better when it came to predicting high-risk cases.

### Model 3: Logistic Regression with K-Means Clustering Undersampling
- Balanced accuracy score: 0.51
- Confusion matrix: ![Confusion matrix for cluster]()
- Imbalanced classification report: ![imbalanced classification report for cluster]()

*Analysis*: This model performed the worst overall. The biggest, and only real, difference between this model and the ones above is that the recall score for low-risk loans took a rather large hit. The model did not change in it's ability to predict high-risk loans at all. 

### Model 4: Logistic Regression with SMOTE-ENN
- Balanced accuracy score: 0.63
- Confusion matrix: ![Confusion matrix for SMOTE-ENN]()
- Imbalanced classification report: ![imbalanced classification report for SMOTE-ENN]()

*Analysis*: The balanced accuracy of this model is comparable to the SMOTE model, however this model's recall score for the high-risk loans were appreciably better than any of the other logistic regression models. The recall score for low-risk loans, however, were worse. The precision scores didn't change at all. I would say that if detecting high-risk loans were the goal, and I do believe it is, that this model is the best choice among the logistic regression models.

### Model 5: Random Forests
- Balanced accuracy score: 0.83
- Confusion matrix: ![Confusion matrix for random forests]()
- Imbalanced classification report: ![imbalanced classification report for random forests]()

*Analysis*: Clearly the ensemble learning methods did a lot better. The balanced accuracy score is impressive. The precision score for high-risk loans are not, though it was three times as good as any of the logistic regression models. Of course, that just means going from 0.01 to 0.03. The recall scores, though, are quite encouraging. The model did a lot better in detecting low-risk loans than high risks, but did well in both cases, overall.

### Model 6: Bootstrap Aggregation
- Balanced accuracy score: 0.93
- Confusion matrix: ![Confusion matrix for easyensemble]()
- Imbalanced classification report: ![imbalanced classification report for easyensemble]()

*Analysis*: This model is definitely a case of save the best for last. The balanced accurtacy score is *very* impressive. The precision scores were not really that different than any of tyhe other models, but it would be rather surprising if they changed dramatically atr this point anyway. The recall scores are about as good as I could hope them to be. It was able to detect most of the high-risk cases and low-risk cases alike. 

## Summary
Overall, the bootstrap ensemble model performed the best, and I would recommend its use. Although many of the loans that the model predicted as high-risk aren't actaully high-risk (low precision score), it did quite well in detecting most of the high-risk cases. It is more important that the high-risk cases be caught, rather than the model being able to be accurate about it's high-risk predictions. In this dataset, there are a very low number of high-risk loans compared to the overall number. The cases labelled as high-risk may be looked over by a loan officer to make an accurate determination as to the actual risk of the loan, while those predicted to be low-risk can be confidently approved (high precision score). This is how I would picture this model being used. 
