# Newyork-City-Taxi-Demand-Prediction

* This is a small project to present the time-series analysis of public demand for Taxis in the Newyork City during various timezones of the day. We have taken this data from Newyork City Taxi & Limousine Commission. 
* We have evaluated various big data management and parallel computing aspects to handle large volumes of data and analysed the geo spatial data in New York city to identify various regions based on the customer demand patterns using Dask Library & Folium library.
* Given a location and time, we have to predict the number of pickups in the next ten minutes to help drivers serve the customers well and make a good living for themselves.

# Features in the dataset:

#### Field Name : Description

#### VendorID : A code indicating the TPEP provider that provided the record.

    * Creative Mobile Technologies
    * VeriFone Inc.
#### tpep_pickup_datetime : The date and time when the meter was engaged.
#### tpep_dropoff_datetime : The date and time when the meter was disengaged.
#### Passenger_count : The number of passengers in the vehicle. This is a driver-entered value.
#### Trip_distance : The elapsed trip distance in miles reported by the taximeter.
#### Pickup_longitude : Longitude where the meter was engaged.
#### Pickup_latitude : Latitude where the meter was engaged.
#### RateCodeID : The final rate code in effect at the end of the trip.
    * Standard rate 
    * JFK
    * Newark
    * Nassau or Westchester
    * Negotiated fare 
    * Group ride
#### Store_and_fwd_flag :  This flag indicates whether the trip record was held in vehicle memory before sending to the vendor, aka “store and forward,” because the vehicle did not have a connection to the server.
	* Y= store and forward trip
	* N= not a store and forward trip
#### Dropoff_longitude : Longitude where the meter was disengaged.
#### Dropoff_ latitude : Latitude where the meter was disengaged.
#### Payment_type : A numeric code signifying how the passenger paid for the trip.
	* Credit card
    * Cash
    * No charge
    * Dispute
    * Unknown
    * Voided trip
#### Fare_amount : The time-and-distance fare calculated by the meter.
#### Extra : Miscellaneous extras and surcharges. Currently, this only includes. the $0.50 and $1 rush hour and overnight charges.
#### MTA_tax
    * 0.50 MTA tax that is automatically triggered based on the metered rate in use.
    * Improvement_surcharge
    * 0.30 improvement surcharge assessed trips at the flag drop. the improvement surcharge began being levied in 2015
#### Tip amount : This field is automatically populated for credit card tips.Cash tips are not included.
#### Tolls_amount : Total amount of all tolls paid in trip.
#### Total_amount : The total amount charged to passengers. Does not include cash tips.

## Information on taxis:

# Yellow Taxi: Yellow Medallion Taxicabs</h5>
* These are the famous NYC yellow taxis that provide transportation exclusively through street-hails. The number of taxicabs is limited by a finite number of medallions issued by the TLC. You access this mode of transportation by standing in the street and hailing an available taxi with your hand. The pickups are not pre-arranged.</p>

# For Hire Vehicles (FHVs) 
* FHV transportation is accessed by a pre-arrangement with a dispatcher or limo company. These FHVs are not permitted to pick up passengers via street hails, as those rides are not considered pre-arranged. 

# Green Taxi: Street Hail Livery (SHL) 
* The SHL program will allow livery vehicle owners to license and outfit their vehicles with green borough taxi branding, meters, credit card machines, and ultimately the right to accept street hails in addition to pre-arranged rides. 

# Note:
In the given notebook we are considering only the yellow taxis for the time period between Jan - Mar 2015 & Jan - Mar 2016


# Performance metrics
* Mean Absolute percentage error
* Mean Squared error

# Exploratory Data Analysis
* We implemeted Exploratory Data Analysis of all the given features to get a fundamental understanding of the data and we identified close to 3% of the data points as outliers.
* We categorized the 24 hours time into 10 minute interval timebins to make our time series analysis easier. So we got 144 timebins a day.
* We identified 30 Clusters in the Newyork City using K-means clustering and marked them as regions so that depending on the current location, a driver can travel to the nearest high demand region so that he could get more number of pickups.
* These are the 30 clusters identified in the NYC:
![NYC Clusters](https://user-images.githubusercontent.com/42597977/139604929-26a59a03-5930-48dc-be2d-760b3b07ec01.png)



# Modelling
* We have implemented variety of models ranging from simple baseline models using averages to complex Machine LEarning Models
* These are the models implemetned:
# Simple Moving Averages:
* Simple Moving Averages using Ratio Values -  Rt=(Rt−1+Rt−2+Rt−3....Rt−n)/n
# Weighted Moving Averages
* Weighted Moving Averages using Ratio Values -  Rt=(N∗Rt−1+(N−1)∗Rt−2+(N−2)∗Rt−3....1∗Rt−n)/(N∗(N+1)/2)
# Exponential Weighted Moving Averages(Exponential Decaying Average)
* R′t=α∗Rt−1+(1−α)∗R′t−1
# Linear Regression
# Random Forest Regression
# XG-Boost Regression

# Results:
| Model | MAP Error |
| --- | --- |
| Simple Moving Average | 0.124 |
| Exponential DecayingAverage | 0.119 |
| Linear Regression | 0.145 |
| Random Forest Regression | 0.120 |
| XG-Boost Regression | 0.117 |



Conlusion
* Among all the models, Exponential Weighted Averages and XG-Boost Regression gave us the lowest mean absolute percentage error
