# Boosting_Project_Using_CensusData

In this project, we will be using a dataset containing census information from UCI’s Machine Learning Repository.

By using this census data with boosting algorithms, we will try to predict whether or not a person makes more than $50,000.

Let’s get started!

Datasets
The original data set is available at the UCI Machine Learning Repository: https://archive.ics.uci.edu/ml/datasets/census+income


# Explore and prepare the data

1.
Take a look at the distribution of the target column, income. What percentage of samples have incomes greater than 50k and less than or equal to 50k?



2.
We have identified a set of features to explore. The features are stored in a variable raw_feature_cols. Take a look at the datatypes of these columns. Are they what you expected based on the data dictionary provided in the description?



# Preparing the features

3.
Create a features dataframe X with the features listed in the stored variable raw_feature_cols. Since the columns workclass, sex, and race are all low cardinality categorical variables, we will convert them to dummy variables using pd.get_dummies().

Set the parameter drop_first = True in pd.get_dummies(). This drops the first categorical instance in each of the categorical variable columns because it is redundant. Make sure you understand why we do not have to worry about dropping the redundant variable before moving on.

Note: pd.get_dummies() is clever enough that it will only create dummy variables for the categorical columns. It will not create dummy variables for the int64 columns.

Take a look at the first 5 rows of the features dataframe by using the .head(n=5) method.



4.
Convert the target variable to a binary value and store it in a variable y. Set it to 0 when income <= 50K and 1 when income > 50K.


# Build and Train the AdaBoost and Gradient Boosted Trees Classifiers

5.
Perform a train-test split. Create the base estimator for the AdaBoost classifier in the form a decision stump using DecisionTreeClassifier() and store it in a variable named decision_stump.



6.
Create an instance of AdaBoostClassifier() and store it in a variable ada_classifier. Keep most of the parameters set as their default value, except the base_estimator parameter which should be set to decision_stump.


7.
Create an instance of GradientBoostingClassifier() and store it in a variable grad_classifier. Keep all the parameters set as their default value.


8.
Fit each of the instantiated models on the training data. Calculate and store the predictions on the test data in separate variables y_pred_ada and y_pred_grad. Print the accuracy and f1 score for the predictions from each model.


# Explore Hyperparameters
9.
For AdaBoost the default n_estimators is 50 and for Gradient Boosting it is 100. We’ve created a new list n_estimators_list = [10, 30, 50, 70, 90] to search from and determine the value of this parameter that gives us the most performant model. Use GridSearchCV with AdaBoost to fit the data and search this parameter space.


10.
Calculate the mean_test_score for each of these fits and store it as a list, ada_scores_list. Plot it against n_estimators_list to pick the best value for n_estimators.
