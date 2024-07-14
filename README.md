
# HeavyMachineryAuction

Welcome to the Heavy Machinery Auction Price Estimator competition! 

This is a [Kaggle](https://www.kaggle.com/competitions/ds-17-basic-ml-regression-predict-machine-price) competition which is a part of an ongoing certification as a data scientist at BIU.  
This README provides an overview of the logic implemented in the `HeavyMachineryAuction.ipynb` notebook.

## Objective
The objective of this notebook is to develop a basic ML model that accurately estimates the final sale price of heavy machinery based on historical auction data.

## Data
The dataset used for this project is in CSV format. It contains historical auction data for various types of heavy machinery and construction equipment.
There is a separate verification dataset (as well in CSV format) which is being used for Sale Prices predictions and final submission on Kaggle competition.

## Logic
The `HeavyMachineryAuction.ipynb` notebook implements the following logic:

1. Data Preprocessing: The notebook starts by loading all datasets,  
reducing some features, creating some new features, scaling some features , dropping duplications (not on verification dataset).

2. It then splits an original dataset into the train and test data, and from here going forward - works on all 3 datasets performing necessary preprocessing steps on every one - such as handling missing values, encoding categorical variables, and scaling numerical features. The common approach - all the manipuations on data is being done (transform) on each of the 3 above datasets , but only train dataset used to fit a model.  

3. Hyperparameters  detection - this code is commented , please uncomment to run (its lengthy! Thus, prior to run be sure you have required cpus number or change tuning function code to adjust accordingly)

4. Model Training: The notebook uses random forest regression machine learning algorithm, to train a model on the preprocessed data. The model is trained using a train portion of the dataset and being evaluated on a test portion of it. 

5. Model Evaluation: The notebook evaluates the trained model's performance using various metrics such as mean squared error (MSE), root mean squared error (RMSE), and R-squared.

6. Predictions: Finally, the notebook uses the trained model to make predictions on new, unseen data (validation dataset). The predicted auction sale prices are saved in a CSV file for further submission to the Kaggle competition , where analysis and evaluation takes place and score for competition is given (RMSE on predicted vs a target data available upon kaggle submission process)


## List of data mnipulations and technics used

    For numerical features:
    - Mean imputer
    - Scaler

    For categorical features:
    - Mode imputer
    - Label encoding

    Feature engineering:
    - Manipulations on salesdate derivates (datetime)
    - Introduction of Age feature
    - Handling outliers in YearMade
    - Overall Features Reduction

    Hyperparameter Optimization: 
    - Finding the best set of hyperparameters for a model with sklearn GridSearchCV

    Takeaway:
    - Choose rigth features; use correlation matrixes and heatmaps to decide. 
    I feel like there are still redundant columns in the model
    - Introduce powerfull features and clean features that not contributing 
    - Split datasets early to prevent data mixing on transform (overfitting)
    - Decide how to clean and enchance data
    - After separating , fit on train ,then transform on everything. Prevents data mixing and overfitting
    - See how it reflected in feature importances of a regressor  - if it close?
    - Model validity
    - Use whatever helps - hyperparameters tuning , so on
    - Learn visualtization methods
    - Learn about target encoding
    - Analyze significant columns - split to particular values and check for corelations to other signifcant things

    Competition winner's tips:
    - Use target encoding on columns - maybe classical label encoding technic is not good enougth as it does not reflect possible relations between the values (product size: huge,largee,small - may affect the price) on columns where a lot of nans (post possibly the column is not relavant for the target, or if a few nans - maybe missing data)
    - Random forest can't interpolate or predict inflation (sales in valid are from 2012, in train - from 2011). so target may have a factor (percent of inflation) f.e. valid_price = train_price_prediction * 1.035 

## Conclusion
The `HeavyMachineryAuction.ipynb` notebook provides a basic ML model for estimating the auction sale prices of heavy machinery. By following the logic described above, you can understand and replicate the steps taken in the notebook to develop your own price estimation model.

Please refer to the notebook for detailed code implementation and further instructions.

