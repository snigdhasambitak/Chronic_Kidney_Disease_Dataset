# Chronic_Kidney_Disease_Dataset

## Problem Statement

* Identify the factors causing chronic kidney disease
* Build a model that can help to determine if a patient is suffering from the chronic disease or not
* Provided data set : Chronic Kidney Disease dataset
  * Data Set Characteristics: Multivariate
  * Number of Instances: 400
  * Attribute Characteristics: Real
  * Number of Attributes: 25
  * Associated Tasks: Classification
  * Missing values: Yes


## Data Definition and Understanding

* This is a multi variate dataset with 25 attributes(24 + class)
* Excluding class there are 13 Nominal attributes and 11 Numeric attributes
* There are missing values represented with “?”
* The range of numeric attributes varies.
  * Example wbcc is in thousands, bgr is in hundreds and sg is in single digits. This demands scaling.
* At the face value, there are multiple attributes that appear to be correlated.
  * Example hemoglobin, rbc count, Sugar , blood glucose levels and Diabetes mellitus. Which demands for a correlation analysis

## Pre-Processing Techniques

* Update missing values with mean for numeric attributes and most frequent value for nominal variables
* Encode the labels for the nominal attribute values
* Perform correlation analysis and see if attributes can be dropped based on the threshold (0.9), where 0.9 means that the attributes are highly correlated with each other.
* Scale and transform the data, in order to fit the model perfectly without causing any skewness in the model we build.

 <!-- Heat Map for Correlation b/w different Attributes

  Histograms to show the distributions after Data preprocessing
  We employed Standard Scaler provided by sklearn library

 Box plot for numerical columns in the dataset -->

## Algorithm Selection

4 algorithms were considered for model evaluation and following are the design considerations

* Decision Tree Classifier
  * Good for categorical output, can handle high dimension data and domainknowledge may not be necessary
  * May produce complex tree as there are many numerical attributes
* Gaussian Naive Bayes Classifier
  * Efficient and fast
  * But can be less reliable when there are dependencies between the attributes.
* Gradient Boosting Classifier
  * Depends on number of trees, depth and learning rate. But performs fairly well in terms of accuracy.
* SVM Classifier
  * Can model non-linear decision boundaries
  * Pretty robust against overfitting in an high dimensional space
* Random Forest Classifier
  * It is an ensemble learning method, composed of multiple decision trees. By averaging out the impact of several decision trees, random forests tend to improve prediction
  * Random forests tend to shine in scenarios where a model has a large number of features that individually have weak predicative power but much stronger power collectively

Although the above classifiers are intuitively expected to work well for the pre- processed data, we went ahead to evaluate the model based on the metrics.


## Observations

* Accuracy was found to be higher for Gradient Boosting classifier and SVM (RBF kernel)
* Decision tree classifier was found to do better (accuracy increased from 96.6 to 97.5) when attributes were dropped based on correlation threshold 0.8. (attribute pcv being dropped if threshold is 0.8 or 0.85)
* The trends are similar for different training-test data divide (75-25, 80-20, 70-30). SVM did better for the pre-processing techniques used.
* Using Random Forest model we can see from the output that there was a slight improvement in the results. Our roc_auc score improved from .999 to .997. The downside is that our number of false positives increased slightly (but false negatives declined)


Conclusion: We would like to conclude by saying that for the given dataset analysis, we found SVM to be best method for building a predictive model.
