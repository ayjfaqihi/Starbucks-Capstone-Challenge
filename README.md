
# 
# Starbucks Capstone Challenge
##### Ahmad faqihi, 22, Feb, 2022
https://medium.com/@ayjfaqihi/starbucks-capstone-challenge-3088ea2030fb
## Table Of Content

### Project Overview

### Problem Statement
### Data Discovery
##### 1- portfolio.json
##### 2- profile.json
##### 3- transcript.json
### Data Cleaning
##### 1- portfolio
##### 2- profile
##### 3- transcript
##### 4- Consolidation
### Visualizations
### Modeling
##### 1- Build Decision Tree Classifier
##### 2- Build Random Forest Classifier
##### 3- Build Gradient Boosting Classifier
### Conclusion
##### - Findings
##### - Challenges & Obstacles
###  References
## Project Overview
This data set contains simulated data that mimics customer behavior on the Starbucks rewards mobile app. Once every few days, Starbucks sends out an offer to users of the mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount or BOGO (buy one get one free). Some users might not receive any offer during certain weeks. 

Not all users receive the same offer, and that is the challenge to solve with this data set.

My ur task is to combine transaction, demographic and offer data to determine which demographic groups respond best to which offer type. This data set is a simplified version of the real Starbucks app because the underlying simulator only has one product whereas Starbucks actually sells dozens of products.

Every offer has a validity period before the offer expires. As an example, a BOGO offer might be valid for only 5 days. You'll see in the data set that informational offers have a validity period even though these ads are merely providing information about a product; for example, if an informational offer has 7 days of validity, you can assume the customer is feeling the influence of the offer for 7 days after receiving the advertisement.

Keep in mind as well that someone using the app might make a purchase through the app without having received an offer or seen an offer.

## Problem Statment
In this project, we'll begin by discovering the data frames, then clean and merge them into a single data frame to perform some visualizations and build a model to predict the event type based on demographic data and other information.
 

## Data Discovery


In this section, we'll use certain methodologies and visualization to get a concept of each file and what it contains.

### portfolio.json
containing offer ids and meta data about each offer (duration, type, etc.).
#### Here is the schema and explanation of each variable in the files:
* id (string) - offer id
* offer_type (string) - type of offer ie BOGO, discount, informational
* difficulty (int) - minimum required spend to complete an offer
* reward (int) - reward given for completing an offer
* duration (int) - time for offer to be open, in days
* channels (list of strings)

### profile.json

demographic data for each customer.

#### Here is the schema and explanation of each variable in the files:[]

-   age (int) - age of the customer
-   became_member_on (int) - date when customer created an app account
-   gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
-   id (str) - customer id
-   income (float) - customer's income
### transcript.json

records for transactions, offers received, offers viewed, and offers completed

#### Here is the schema and explanation of each variable in the files:

-   event (str) - record description (ie transaction, offer received, offer viewed, etc.)
-   person (str) - customer id
-   time (int) - time in hours since start of test. The data begins at time t=0
-   value - (dict of strings) - either an offer id or transaction amount depending on the record
## Data Cleaning

In this section. We'll clean the data and get it ready for the visualizationsphase and the modeling phase.
### portfolio
As you can see, the portfolio doesn't have much data to clean, but if we intend to merge the dataframes, we'll notice that we have two ID variables the offer ID and the customer ID. As a precaution, we'll rename the variable to make everything more apparent. The channels column is the bigger problem. It's a list that we don't want in a dataframe, so we'll divide it into four columns email, mobile, social and web, and mark 1 if the offer has this channel and 0 if it doesn't.
### profile
Since the profile dataframe has an ID column, we'll rename it to resemble the other one. We also have to drop all null values. Another issue is in 'became_member_on' column, we can't store the date values as int, therefore we need to reformat it.
### transcript
The event column have serious issue here. Given that the event column is a list, we must divide it into multiple columns. We also have a massive problem with the value column. It is an offer id if the event was related to offer, and it may or may not contain a reward, and if the event was a transaction, the value is an amount, so we must separate it and store the values, which is the difficult part. We also have person column witch is contain the custmer ID so, we will change the name to match the previus one.
### Consolidation
All of our dataframes are now ready to use. We're all set to combine all of them.
## Visualizations
Now that we can extract any information we want from the cleaning data, we'll look at an example of what we can do with it using graphs.
## Modeling
Building three machine learning models to predict which offer will be completed. Witch is:-
- Build Decision Tree Classifier
-  Build Random Forest Classifier
-  Build Gradient Boosting Classifier
## Conclusion
During this project, I learned a lot of things that helped me improve myself, and I was able to find information and knowledge from the data.

### Findings
- Social media does not provide us with a high-completed offer, we must string it out.
- We have a higher number of customers between the ages of 50 and 60.
- The number of male customers is higher than the number of female customers.
- Less than half of the offers received are complete.
### Challenges & Obstacles
- Due to my lack of experience with Python and Pandas, I had some difficulties to complete this project.
- Cleaning the value column was difficult it took longer than it should have.
## References

-   [https://www.datarmatics.com](https://www.datarmatics.com/)
-   [https://blog.finxter.com](https://blog.finxter.com/)
-   [https://pandas.pydata.org](https://pandas.pydata.org/)
-   [https://matplotlib.org](https://matplotlib.org/)