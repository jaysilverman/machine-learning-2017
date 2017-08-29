# Water Pump Failure

This project contains the Jupyter notebooks which I used to participate in the Drivendata Water Pump Failure competition (https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table). The dataset for this competition is moderately large with 40 features and 59400 examples in the training dataset. This project was my attempt to use Python and Scikit-Learn (http://scikit-learn.org) to predict which water pumps in Tanzania will fail or require repair. 

There are a number of problems one has to overcome in this competition:

* Some categorical features have thousands of unique values - If one creates a dummy variable for each unique value in these features you wind up with over 7000 columns. The fitting time and memory requirements for some classification models increase dramatically when the number of features is very large (e.g. Bagging, MLP, Gradient Boosting). So you have to decide whether to drop features, standardize feature values (e.g. use one standard value instead of five variations of the same value for the name of an organization), consolidate feature values (e.g. use top 20 and put the rest into an 'other' category), use dimensionality reduction (e.g. PCA), pay for additional computing resources, and even forgo using a specific classifier.  

* Several features have missing values - For this dataset I thought the best approach was to impute missing values based on a combination of geographic information, mean, median, and most common value. For example to impute construction year I used the median construction year for the ward where the water pump was located. If this wasn't possible I used the median construction year using the next highest geographic feature (lga, district, region, and basin).  

* Uncertainty whether values are missing or actual values - Some of the features appear to use a value for a missing value which could actually be an actual value. As an example the GPS height feature has the value 0 on almost 30000 records. By analyzing the dataset one can easily see that every water pump in 4 regions have 0 for GPS height. I decided to treat features with these types of values as missing values. 

This project contains two Jupyter notebooks. The Water Pump Failure Analysis notebook contains some of the data analysis I performed with the training and test datasets. The Water Pump Failure Model notebook contains the functionality to cleanup the dataset, impute features, drop features, normalize features, fit/predict, cross validate, identify optimal hyperparameters, and generate a submission file. 

At the time of my best submission my score (0.8124) was ranked 449 out of more than 3600 competitors.
