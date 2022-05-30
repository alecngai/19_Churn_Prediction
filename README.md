# 19_Churn_Prediction

What Is Churn Rate? The churn rate, also known as the rate of attrition or customer churn, is the rate at which customers stop doing business with an entity. It is most commonly expressed as the percentage of service subscribers who discontinue their subscriptions within a given time period.

## The data set includes information about:

- Customers who left within the last month – the column is called Churn
- Services that each customer has signed up for – phone, multiple lines, internet, online security, online backup, device protection, tech support, and streaming TV and movies
- Customer account information – how long they’ve been a customer, contract, payment method, paperless billing, monthly charges, and total charges
- Demographic info about customers – gender, age range, and if they have partners and dependents

![Overview1](https://raw.githubusercontent.com/alecngai/19_Churn_Prediction/main/Resources/Images/Overview1.jpg)

## Data Cleaning 

![Null](https://raw.githubusercontent.com/alecngai/19_Churn_Prediction/main/Resources/Images/Null1.png)

Initially, we can see that Total Charges is an Object, so I converted it to a numeric value, in doing so we can see that we have 11 null values, this is because these 11 customers did not use the service for longer than a month, and the calculation 
for Total charges is Tenure * Monthly Charge, so these 11 customers have Null due to their Tenure being zero. I decided to remove these customers as they will skew the data since we do not have much data on how our service affected these customers. 

![Churn](https://raw.githubusercontent.com/alecngai/19_Churn_Prediction/main/Resources/Images/Churn_Rates.png)   

Here is a visable graph showing the relation to each feature to Churn. Allowing us to further our feature selection to reduce uneeded features. 

![Churn2](https://raw.githubusercontent.com/alecngai/19_Churn_Prediction/main/Resources/Images/Churn_Relation.png)

After exploring the features, I have decided not to use the following features because they add little or no informative power to the model:

- Customer ID
- Gender
- PhoneService
- Contract
- TotalCharges
- MultipleLines

The final list of features which we will use are: 
Discontinous:
- SeniorCitizen 
- Partner 
- Dependents
- InternetService
- OnlineSecurity
- OnlineBackup
- DeviceProtection
- TechSupport
- StreamingTV
- StreamingMovies
- PaperlessBilling
- PaymentMethod

Continuous: 
- Tenure
- MonthlyCharges

For the continous features, we used MinMAxScaler to scale the values and fit transformed them to better fit the metrics of the model.  We also dropped first if the feature was binary to downsize the input for the model. 

