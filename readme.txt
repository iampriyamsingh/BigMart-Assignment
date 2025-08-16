README
Project: BigMart Sales Prediction - Model Comparison
This project focuses on the final stage of a machine learning pipeline: comparing and selecting the best model to predict sales for a BigMart outlet. It uses cross-validation to rigorously evaluate different regression models and then generates a final submission file with the best-performing model's predictions.

Files Required
Before running the script, ensure the following files are in the same directory:

preprocessed_train_simplified.csv: The training features dataset.

preprocessed_train_target_simplified.csv: The target sales variable for training.

preprocessed_test_simplified.csv: The test features dataset.

test_AbJTz2l.csv: The original test file, needed to create the final submission file.

How to Run the Code
To execute the script, simply run it from your terminal or a Python environment:

python Comparing_Models.py

The script will automatically load the necessary data, train and evaluate the models, and save the final prediction file.

What the Code Does
Data Loading and Preparation: The script loads the preprocessed training and test data. It also performs a final check for any missing values, filling them with zero to prevent errors during model training.

Target Variable Transformation: The Item_Outlet_Sales target variable is right-skewed, which can negatively impact some models. To address this, the script applies a log-transformation (np.log1p), making the distribution more suitable for a linear-based model.

Model Evaluation with Cross-Validation: The core of this script is its systematic comparison of six different regression models:

Linear Regression

Ridge Regression

Lasso Regression

Random Forest Regressor

Gradient Boosting Regressor

XGBoost Regressor

It uses a 5-fold cross-validation approach to evaluate each model's performance on the training data. The primary metric used is the Root Mean Squared Error (RMSE), which provides a measure of the average difference between the predicted and actual sales values.

Best Model Selection: After evaluating all models, the script identifies the one with the lowest average cross-validation RMSE as the best-performing model.

Final Training and Prediction: The best model is then trained on the entire training dataset to maximize its learning. This fully trained model is used to generate predictions on the unseen test data. The predictions are then inverse-transformed back to the original sales scale.

Submission File Generation: Finally, the script creates a CSV file named submission_tuned_v4.csv. This file contains the Item_Identifier, Outlet_Identifier, and the final predicted Item_Outlet_Sales in the required format for submission.