# Santander Customer Transaction Prediction
This competition is run by Banco Santander, a global bank, who are looking to look for new ways to help their customers understand their financial health and identify which products and services might help them achieve their goals. This is all part of their mission to help people and businesses prosper.

With this competition, they are looking to predict, based on a number of features, which customers will make a specific transaction in the future, regardless of the amount transacted.

## Problem and Data Exploration
The data provided comes from two files: train.csv, test.csv. The training set has 200,000 rows of data and 200 columns. The test set aslo has 200,000 rows and 199 columns, where the missing column is the target variable.

Each row represents one customer transaction and each column is a feature. We are not given any details on the individual features and so cannot use any sort of heuristic analysis or intuition to solve this problem.

The data has a large imbalance since 90% of all training examples have a target value of 0 (no transaction); it would therefore be simpler to estimate the target to be 0 at all times. However, one way to fix this is to oversample the training data. This duplicates the points from the less prevalent group i.e. where target = 1 (transaction completed) until the total instances of this target is the same as when target = 0. This should make it easier for algorithms to learn from these instances.

We try the more 'state-of-the-art' SMOTE (_Synthetic Minority Oversampling TEchnique_) to once again oversample the minority group. This method consists of synthesising elements for the minority class based on those that already exist. It works by randomly picking a point from the minority class and computing the k-nearest neighbours for this point. The synthetic points are added between the chosen point and its neighbors.

## Objective
As described above, Santander's mission is to help people and businesses prosper. Therefore the major questions they aim to find the answer to the questions: is the customer satisfied? Will a customer buy this product? Can a customer pay this loan? These are the most common questions that are asked by many businesses and financial intermediaries. Therefore, in this competition we hope to predict whether a particular customer would have completed a transaction based on some arbitrary, unknown variables.

## Metric
Ultimately, we want to build a model that can predict the target value accurately and the measure we will use to quantify this is the area under the ROC curve. The Receiving Operating Characteristic (ROC) curve is a graphical plot that illustrates the diagnostic ability of a binary classifier system by plotting the true positive rate (TPR) against the false positive rate (FPR) at various threshold setting.

![render](https://user-images.githubusercontent.com/45533954/92144562-caf18480-ee0e-11ea-86a2-15ae676a5557.png)

![render (1)](https://user-images.githubusercontent.com/45533954/92144619-df358180-ee0e-11ea-9469-fe6933df0a4a.png)

The closer the area under the curve is to 1, the better the model is, while as it approaches 0, this signifies a poorer model. When the AUC is 0.5, this means the model ahs no class separation whatsoever i.e. it is similar to flipping a coin and therefore no better than random choice.

## Conclusion
We have trained the data using several models and use the Gaussian Naive Bayes model since as shown below, this provides the best performance (albeit with a large standard deviation). One possible way to improve performance further is through the use of neural networks, since the amount of data here is large. This led to a test score of 0.899% which at the time ranked in the top 25% of submissions.

![image](https://user-images.githubusercontent.com/45533954/92143920-da240280-ee0d-11ea-91cc-20a0277e143c.png)
