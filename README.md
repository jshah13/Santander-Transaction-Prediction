# Santander Customer Transaction Prediction
This competition is run by Banco Santander, a global bank, who are looking to look for new ways to help their customers understand their financial health and identify which products and services might help them achieve their goals. This is all part of their mission to help people and businesses prosper.

With this competition, they are looking to predict, based on a number of features, which customers will make a specific transaction in the future, regardless of the amount transacted.

## Conclusion
We have trained the data using several models and use the Gaussian Naive Bayes model since as shown below, this provides the best performance (albeit with a large standard deviation). One possible way to improve performance further is through the use of neural networks, since the amount of data here is large.

![image](https://user-images.githubusercontent.com/45533954/92143920-da240280-ee0d-11ea-91cc-20a0277e143c.png)

## Problem and Data Exploration
The data provided comes from two files: train.csv, test.csv. The training set has 200,000 rows of data and 200 columns. The test set aslo has 200,000 rows and 199 columns, where the missing column is the target variable.

Each row represents one customer transaction and each column is a feature. We are not given any details on the individual features and so cannot use any sort of heuristic analysis or intuition to solve this problem.

## Objective
As described above, Santander's mission is to help people and businesses prosper. Therefore the major questions they aim to find the answer to the questions: is the customer satisfied? Will a customer buy this product? Can a customer pay this loan? These are the most common questions that are asked by many businesses and financial intermediaries. Therefore, in this competition we hope to predict whether a particular customer would have completed a transaction based on some arbitrary, unknown variables.

## Metric
Ultimately, we want to build a model that can predict the target value accurately and the measure we will use to quantify this is the area under the ROC curve. The Receiving Operating Characteristic (ROC) curve is a graphical plot that illustrates the diagnostic ability of a binary classifier system by plotting the true positive rate (TPR) against the false positive rate (FPR) at various threshold setting. $$TPR = \frac{TP}{TP + FN}$$

![image]("http://www.sciweavers.org/tex2img.php?eq=%24%24TPR%20%3D%20%5Cfrac%7BTP%7D%7BTP%20%2B%20FN%7D%24%24&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0")

$$FPR = \frac{FP}{TN + FP}$$
The closer the area under the curve is to 1, the better the model is, while as it approaches 0, this signifies a poorer model. When the AUC is 0.5, this means the model ahs no class separation whatsoever i.e. it is similar to flipping a coin and therefore no better than random choice.
