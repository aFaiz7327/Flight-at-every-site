# Flight-at-every-site
Created a tool that predicts flight prices to assist customers in finding the greatest deals when purchasing airline tickets. Engineered elements such as Departure Time and Date of Journey were included to quantify and make the data more comprehensible. GridsearchCV was used to optimise several regression models in order to find the best one.

**Codes and Resources Used**

Python Version: 3.8.5
Packages: pandas, numpy, sklearn, matplotlib, seaborn
For Web Framework Requirements: pip install -r requirements.txt
Dataset: https://www.kaggle.com/nikhilmittal/flight-fare-prediction-mh
Flask Productionization: https://towardsdatascience.com/productionize-a-machine-learning-model-with-flask-and-heroku-8201260503d2

**Problem Statement**
Flight ticket costs may be difficult to predict; we may see one price today, but if we check the price of the same flight tomorrow, it will be a different tale. We've all heard passengers complain about how unpredictable aeroplane ticket costs are. As data scientists, we will demonstrate that everything can be predicted given the correct data. You will see rates for flight tickets for numerous airlines and between various places during the months of March and June 2019. 10683 records in the training set

**Size of test set: 2671 records**
FEATURES: Airline: The name of the airline.
Date_of_Journey: The date of the journey
Source: The source from which the service begins.
Destination: The destination where the service ends.
Route: The route taken by the flight to reach the destination.
Dep_Time: The time when the journey starts from the source.
Arrival_Time: Time of arrival at the destination.
Duration: Total duration of the flight.
Total_Stops: Total stops between the source and destination.
Additional_Info: Additional information about the flight
Price: The price of the ticket

**Cleaning the Data**
I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

Made Columns for Day and Month out of Date of Journey
Calculated the total flight duration
Removed the null values
Removed the outliers

**Model Building**
First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 30%.

I tried forteen different models and evaluated them using Root Mean Squared Error. I chose RMSE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.

**Different models I tried:**

LinearRegression : 2779.0455708889144
ElasticNet : 3379.6819876610443
Lasso : 2759.449381312224
Ridge : 2710.8476127741037
DecisionTreeRegressor : 2017.530360334335
RandomForestRegressor : 1662.7359733973055
SVR : 4246.460099935076
AdaBoostRegressor : 3135.985374101527
GradientBoostingRegressor : 1904.7364927923986
ExtraTreeRegressor : 2432.1393735590073
HuberRegressor : 3108.870789540331
BayesianRidge : 2773.275561516677
ExtraTreeRegressor, RandomForestRegressor and GradientBoostingRegressor gave the lowest RMSE so I chose these model and performed hyper parameter tuning



USing hyperparameter tuning on GradientBoostingRegressor further increased the accuracy.

Model Accuracy
GradientBoostingRegressor :

MAE: 959.8979539240587
MSE: 2705023.0432436923
RMSE: 1644.6954256772565
Productionization
In this step, I finalized the model by using Characterised parameter you can predict the price of flight
