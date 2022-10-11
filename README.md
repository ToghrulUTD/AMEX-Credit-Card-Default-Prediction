# AMEX-Credit-Card-Default-Prediction

The project has beed implemented using the data from a Kaggle competion "American Express - Default Prediction". Below is the description of the competition.

## Description

Whether out at a restaurant or buying tickets to a concert, modern life counts on the convenience of a credit card to make daily purchases. It saves us from carrying large amounts of cash and also can advance a full purchase that can be paid over time. How do card issuers know we’ll pay back what we charge? That’s a complex problem with many existing solutions—and even more potential improvements, to be explored in this competition.

Credit default prediction is central to managing risk in a consumer lending business. Credit default prediction allows lenders to optimize lending decisions, which leads to a better customer experience and sound business economics. Current models exist to help manage risk. But it's possible to create better models that can outperform those currently in use.

American Express is a globally integrated payments company. The largest payment card issuer in the world, they provide customers with access to products, insights, and experiences that enrich lives and build business success.

In this competition, you’ll apply your machine learning skills to predict credit default. Specifically, you will leverage an industrial scale data set to build a machine learning model that challenges the current model in production. Training, validation, and testing datasets include time-series behavioral data and anonymized customer profile information. You're free to explore any technique to create the most powerful model, from creating features to using the data in a more organic way within a model.

If successful, you'll help create a better customer experience for cardholders by making it easier to be approved for a credit card. Top solutions could challenge the credit default prediction model used by the world's largest payment card issuer—earning you cash prizes, the opportunity to interview with American Express, and potentially a rewarding new career.

## Evaluation metric
The evaluation metric, 𝑀, for this competition is the mean of two measures of rank ordering: Normalized Gini Coefficient, 𝐺, and default rate captured at 4%, 𝐷.

                                                             𝑀=0.5⋅(𝐺+𝐷)
                                                             
The default rate captured at 4% is the percentage of the positive labels (defaults) captured within the highest-ranked 4% of the predictions, and represents a Sensitivity/Recall statistic. For both of the sub-metrics 𝐺 and 𝐷, the negative labels are given a weight of 20 to adjust for downsampling. This metric has a maximum value of 1.0.

## Dataset Description

Dataset Description
The objective of this competition is to predict the probability that a customer does not pay back their credit card balance amount in the future based on their monthly customer profile. The target binary variable is calculated by observing 18 months performance window after the latest credit card statement, and if the customer does not pay due amount in 120 days after their latest statement date it is considered a default event.

The dataset contains aggregated profile features for each customer at each statement date. Features are anonymized and normalized, and fall into the following general categories:

D_* = Delinquency variables
S_* = Spend variables
P_* = Payment variables
B_* = Balance variables
R_* = Risk variables

## Project details

In this project, we have more than 10 million rows of data that captures customers' monthly spending, payment, Balance, Risk and Delinquency features for 18 month of period. First, using Pandas, I have summarized the data for each customer by finding mean, max, min, std of montly quantities and also generate trend variables by getting the percent change between first 3 month statistics and last 3 month statistics. I also applied different transformations and created additional features as a function of the given features. The are around 1500 features after feature engineering step. Next, I have cleaned the data by imputing missing and inf values and split the data for train,val, test datasets. I have used LightGBM module to build GBDT and DART ensemble models, and autotuned the model using OPTUNA framework. For more details, please view the python notebooks.
