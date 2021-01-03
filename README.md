# King County Housing Market: Regression Analysis
A Project for Flatiron School

![Seattle](images/seattle.jpeg)

### Business Case

A new real estate development company based in Washington hired our team to build a model that will help them estimate housing prices for various areas in King County, WA. Our client is looking to develop homes in areas that are most profitable, as they are looking to raise their capital. 

Our exploration and analysis were guided by the following questions:

* Which areas of King County should a housing development company build properties in? 

* What features should these properties have to sell at high prices and yield the company high profits?

By the end of our analysis, we hope to provide recommendations on which area our client should build in, as well as which types of homes will yield them the highest profits.

### The Data

[Link to dataset on Kaggle](https://www.kaggle.com/becksddf/churn-in-telecoms-dataset)

Our cliend supplied a data set containing information on about 3,300+ of their customers. Here's a detailed description of the features:

* **state:** the state the user lives in
* **account length:**  the number of days the user has this account
* **area code:**  the code of the area the user lives in
* **phone number:**  the phone number of the user
* **international plan:** true if the user has the international plan, otherwise false
* **voice mail plan:** true if the user has the voice mail plan, otherwise false
* **number vmail messages:** the number of voice mail messages the user has sent
* **total day minutes:** total number of minutes the user has been in calls during the day
* **total day calls:** total number of calls the user has done during the day
* **total day charge:** total amount of money the user was charged by the Telecom company for calls during the day
* **total eve minutes:** total number of minutes the user has been in calls during the evening
* **total eve calls:** total number of calls the user has done during the evening
* **total eve charge:** total amount of money the user was charged by the Telecom company for calls during the evening
* **total night minutes:** total number of minutes the user has been in calls during the night
* **total night calls:** total number of calls the user has done during the night
* **total night charge:** total amount of money the user was charged by the Telecom company for calls during the night
* **total intl minutes:** total number of minutes the user has been in international calls
* **total intl calls:** total number of international calls the user has done
* **total intl charge:** total amount of money the user was charged by the Telecom company for international calls
* **customer service calls:** number of customer service calls the user has done
* **churn:** true if the user terminated the contract, otherwise false



### Data Cleanup and EDA

This dataset was incredibly clean: no missing values, no duplicates, no crazy outliers. 

The only issue I had to address was the significant class imbalance. I used SMOTE to fix that:

![churn vs no churn](images/nochurn-churn.png)

Over 14% of the customers are in the churn category. 

In the EDA notebook, I look at the relationship of individual features and decide which ones to keep and drop.

### Vanilla Models

![vanilla models](images/vanilla-models.png)

I fit 10 different vanilla models to explore which ones are worth fine-tuning.

**Metric to use: Recall**
Given the business problem at hand, I believe the best metric to use is Recall. It is better to categorize a loyal customer as someone likely to churn instead of misclassifying a departing customer as loyal, in which case we won't enroll them in our retention program. Financially, that could be the difference between offering someone a discount that wasn't really needed (in a False Positive scenario) vs. having to acquire an entirely new client to make up for False Negative.


### THE FINAL MODEL 

I used GridSearch to fine-tune two models using Bagged Trees and Gradient Boosting. The final model ended up being a Gradient Boosting model with a Recall Score of 93.28% and an Accuracy Score of 96.24%

The most important predictors are:

* Customer Service Calls
* Total Charge
* International Plan
* Voice Mail Plan
* Total International Calls
 
 ### BUSINESS RECOMMENDATIONS:
 
* If the telecom companies notices a client is calling the Customer Support line more than 4 times, it's a good idea to implement a retention plan. Perhaps by offering a discount. 

* Customers who pay more than $40 are at a higher risk of canceling their contract. If a customer is paying more than that and calling your Customer Support line, that's a red flag you don't want to ignore.

 
 
### FUTURE WORK:

* Exploring if area coverage has an impact on customer churn
* Exploring if the state/city the customer lives in is a dominatede by another competitor 
* Look into text message and Data utilization


 

