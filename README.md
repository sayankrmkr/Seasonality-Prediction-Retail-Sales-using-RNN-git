
# Seasonality Prediction Retail Sales using RNN

Info about this data set: https://fred.stlouisfed.org/series/IPN31152N

Units: Index 2012=100, Not Seasonally Adjusted

Frequency: Monthly

The industrial production (IP) index measures the real output of all relevant establishments located in the United States, regardless of their ownership, but not those located in U.S. territories.

NAICS = 31152

Source Code: IP.N31152.N

Suggested Citation: Board of Governors of the Federal Reserve System (US), Industrial Production: Nondurable Goods: Ice cream and frozen dessert [IPN31152N], retrieved from FRED, Federal Reserve Bank of St. Louis; https://fred.stlouisfed.org/series/IPN31152N, November 16, 2019.

## Data Preparation
* Read in the data set "Frozen_Dessert_Production.csv" from the Data folder. 

* Set the date to a datetime index columns
#### Train Test Split
* Split the data into a train/test split where the test set is the last 24 months of data.
* Use a MinMaxScaler to scale the train and test sets into scaled versions.
#### Time Series Generator 
* Create a TimeSeriesGenerator object based off the scaled_train data. The batch length is up to you, but at a minimum it should be at least 18 to capture a full year seasonality.


## Model Creation
* Create a Keras Sequential Model with as many LSTM units you want and a final Dense Layer.  
* Create a generator for the scaled test/validation set. NOTE: Double check that your batch length makes sense for the size of the test set  
* Create an EarlyStopping callback based on val_loss. Validation generator is also used.
* Fit the model to the generator, let the EarlyStopping dictate the amount of epochs, so feel free to set the parameter high.
 
## Evaluation
* Forecast predictions for your test data range (the last 12 months of the entire dataset). Remember to inverse your scaling transformations. Your final result should be a DataFrame with two columns, the true test values and the predictions. 

## Retrain and Forecatsing

* Forecast for the next 12 months based upon previous trends and historical dataset.
