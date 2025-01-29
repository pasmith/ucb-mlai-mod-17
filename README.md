# ucb-mlai-mod-17
Module 17 assignment: compare the performance of several classifiers on a dataset related to the marketing of bank products over the telephone

# Overview
This repository contains an analysis of a dataset containing data from several direct marketing campaigns performed by a Portuguese banking institution trying to enroll customers to subscribe to long term deposit products.

The goal of this analysis is to determine how the bank can improve its direct marketing campaigns to increase the yield of customers subscribing while decreasing the cost to run such campaigns.

### Data source:
The dataset comes from the [UC Irvine Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/bank+marketing). The data is from a Portuguese banking institution and is a collection of the results of multiple marketing campaigns.

### Repository Organization:
- `data\`: folder containing the data set that was examined
- `data\bank-additional-full.csv`: the data set analyzed
- `data\bank-additional.csv`: a random subset of the data in the file above
- `data\bank-additional-names.txt`: description of the fields in the csv dataset files
- `CRISP-DM-BANK.pdf`: article written based on an analysis of the data set
- `prompt_III.ipynb`: file containing the code and analysis for this project
- `README.md`: this page

### To Run
- Create a python environment:

  `python3.12 -m venv .venv`
- Activate the environment:

  `source .venv/bin/activate`
- Then install dependencies:

  `pip install -r requirements.txt`

- Open the jupyter notebook `prompt_III.ipynb` and run it

## Summary of Findings

A dataset consisting of $41k$ samples from several direct marketing campaigns run by a Portuguese banking institution was analyzed to determine what factors predict whether customers would subscribe to a term deposit product.

After cleaning and preparing the data for analysis, the model, presented in [prompt_III.ipynb](prompt_III.ipynb), was constructed that was able to demonstrate the ability to predict the price of a car based on its feature with a $R^2$ correlation coefficient of roughly $0.665$ on the test data set.

The model suggests the factors that most influence price are mileage and year. Newer used vehicles with low miles have the most potential to sell for more.

![importance](images/feature_importance.png)


Vehicles with more than 680k miles don't sell for more than $50k. Newer cars are likely correlated with less mileage, and may also have features and amenities that drivers prefer.

![mileage](images/odometer_price.png)


**Recommendations**

Based on the model, the recommendations for used vehicle inventory include the following:
- Newer model vehicles
- Low mileage vehicles
- Diesel vehicles
- Ram made vehicles
- pickups or trucks
- 10 cylinders vehicles
- 4wd vehicles

# Next Steps

The data appears to favor certain types of vehicles that may not represent fairly the set of used vehicles generally available. The count of values by feature is shown in the figure below.

![features](images/cat_features.png)

The distribution of vehicle mileage is shown below.

![features](images/odometer-dist.png)

The vehicles in the dataset are predominantly recent model vehicles with 4, 6, or 8 cylinder gas engines and automatic transmission, in good or excellent condition, with around 100k miles. This is consistent with common observations of cars on the road in general, and most vehicles have 100k mile warranty. Many owners choose to sell their cars before the warranty expires. However, the vehicles in the dataset analyzed heavily favor 4wd vehicles. That may not represent generally used vehicles that are available for sale. 

![features](images/cat_features_manufacturer_state.png)

As the chart above suggests, the number of vehicles vary greatly from state to state. Driving conditions can vary greatly depending on the types of weather conditions. Also, depending on whether the state is largely rural, or contains heavily populated urban centers, all these factors may impact the type of vehicle, or buyer preference by area. It may make sense to analyze the data by region or state to see whether there are regional preferences.

Possible next steps include:
- Evaluating with a dataset that is more representative of the set of vehicles generally available.
- Evaluating by state to see if there are regional preferences.
