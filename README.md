# Caravan-Insurance-Challenge
Identify potential purchasers of caravan insurance policies

## Problem setting & dataset
### Problem setting
Given the customer and sales information, the task is to identify customers that could be interested in a caravan insurance and especially why.

### Dataset
The dataset of the competition can be downloaded from the [Kaggle website](https://www.kaggle.com/datasets/uciml/caravan-insurance-challenge). 
The dataset contains 5822 observations with 85 features and a target variable (information of whether a customer has (1) or does not have (0) a caravan insurance policy). Each observation corresponds to a postal code. A test set contains 4000 observations without the information on the caravan insurance policy.

## Models
All models were trained using the nested cross validation procedure with hyperparameter tuning.
### Decision Tree classifier
AUC (Area under the curve): 0.7466 \
with the averaged hyper parameters: {'criterion': 'gini', 'max_depth': 3}
### Random Forest classifier
AUC: 0.7560 \
with the averaged hyper parameters: {'criterion': 'log_loss', 'max_depth': 5, 'n_estimators': 325}

## Feature selection
Motivation for the feature selection:  
1. Prevent overfitting 
2. Explainable models 
3. Variance reduction 

Eliminate features which importance is smaller than a given threshold. The threshold here is the mean value of importance of all features.

**Top 10 most important features:**
- 47 PPERSAUT Contribution car policies 
- 68 APERSAUT Number of car policies 
- 59 PBRAND Contribution fire policies 
- 1 MOSTYPE Customer Subtype see L0 
- 37 MINKM30 Income < 30.000 
- 18 MOPLLAAG Lower level education 
- 42 MINKGEM Average income 
- 22 MBERMIDD Middle management 
- 43 MKOOPKLA Purchasing power class 
- 10 MRELGE Married 

### Re-train the Random Forest classifier with the useful features only
AUC of the Random Forest classifier with 26 most important features: 0.7669 (vs. 0.7560 of Random Forest with all features) 

with the averaged hyper parameters: {'criterion': 'log_loss', 'max_depth': 5, 'n_estimators': 775} 

