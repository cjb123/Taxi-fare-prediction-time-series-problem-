<h1> New York City Taxi Fare Prediction </h1>

<b> problem Link : </b> <href> https://www.kaggle.com/c/new-york-city-taxi-fare-prediction/</href>

<b>Problem Description:</b> This problem has been taken from kaggle.We are tasked with predicting the fare amount (inclusive of tolls) for a taxi ride in New York City given the pickup and dropoff locations. While we can get a basic estimate based on just the distance between the two points, this will result in an RMSE of $5-$8, depending on the model used. Our challenge is to do better than this using Machine Learning techniques!

<b>Evaluation Metric</b> : The evaluation metric for this competition is the root mean-squared error or RMSE. RMSE measures the difference between the predictions of a model, and the corresponding ground truth. A large RMSE is equivalent to a large average error, so smaller values of RMSE are better. One nice property of RMSE is that the error is given in the units being measured, so you can tell very directly how incorrect the model might be on unseen data.

RMSE is given as below:

<div>$$ RMSE = \sqrt{\frac{1}{n} \sum^{n}_{i=1} (\hat{y}_i - y_i)^2} $$ </div><br>
where $y_i$ is the ith observation and $\hat{y}_i$ is the prediction  for that observation

<b>My Approach:</b>
<b> Data Exploration </b>
1. Collected the 1st 5000000 datapoints from the train dataset(as total size of data is very large)
2. Done basic understanding of data, like what variables are present, their datatypes,basic statistics of the variables.Found out that there are negative fare amounts in the data sample,maximum fare amount and maximum passenger count is too high
3. Checked for missing values and found out dropoff latitude and logitude variables had missing values <br>

<b> Data Cleaning and Feature extraction </b>
1. Missing values instances are removed from data sample.
2. Pickup datetime values are converted to python date-time object.
3. New features were extracted: year,moth,day of trips(other features from the combination of these features), log_fare,trip distance(haversine distance),fare per kilometer.
3. Outliers were detected(fare amount ,passenger count,map coordinates that occur very rare and those located outside newyork city ,trip distance) and were removed
4. After removing outliers , found out that only 4.6% of the data samples were lost which is a reasonable amount.<br>

<b> Data Visualisation from cleaned data </b>
1. Distribution of various numerical features.
2. Yearly count of total trips, total fare amount, total trip distance and total no of passengers
3. Monthly, weekly,daily(hourly) trend in trips.
4. Correlation matrix of trip count, passenger count,fare amount,trip distance
5. Scatterplot of fare amount vs trip distance.Found out that there were some trips with very low trip distance but very high fare amount.Removed those.

6. Compared mean fare amount and mean trip distance with passenger count.
7. Scatterplots of Fare per kilometer vs trip distance.
8. Trips to and from Airports of newyork(Jfk and LaGuardia) and compared it with trips not to and from the airports
9. How Fare varies with hour of the day


<b> Time series analysis and forecating of total fare amount per month for years 2009 to 2015</b>
1. Used log transform to smooth the variation in data.
2. Visualised and Modeled the trend , seasonality and noise from the time series data.
3. Used Arima models for forecating the total fares in months after June 2015.

<b> ML Models </b> <br>
1. Split the data sample into train and validation set using first 80% in train set and the last 20% as validation set.
2. Used various models(Linear regression , Random Forest Regression, light GBM boosting) to train the dataset and was evaluated using validation dataset. Evaluation metric used was Root mean Squared Error(RMSE) and also calculated explained variance score(EVS)

<b> Conclusions: </b>
RMSE for:<br>
<b> Linear regression </b> : RMSE = 4.08 , EVS = 0.84<br>
<b> Random Forest Regression </b> : RMSE = 3.94   EVS = 0.87<br>

<b> Boosting(light GBM) </b> : RMSE = 3.8 EVS = 0.88


