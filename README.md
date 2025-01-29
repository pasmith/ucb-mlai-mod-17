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

After cleaning and preparing the data for analysis, the model, presented in [prompt_III.ipynb](prompt_III.ipynb), was constructed that was able to predict with accuracy of $90%$ whether customers would subscribe to a deposit product.

A key finding is that when the banking institution decides to run the marketing campaign may be as significant as who, or which customers, the bank targets. For example, March seems to be a month that results in higher probability of successful subscription, probably because of quarterly economy reports. Similarly, strong quarterly economic indicators like consumer price index, or consumer confidence appear to result in successful conversions. In contrast, uncertainty in employment rates may make customers hesitant to invest in products that are less liquid.

It was not immediately clear what customer demographics would be best to target to predict subscription to deposit products.

The analysis compared several classifier models including Logistic Regression, K-Nearest Neighbors, Decision Trees, and Support Vector classifier. Hyperparameters tuning for each was also performed to determine the best performing model.

For this analysis, the SVC classifier appears to be the best performing classifier, but takes a long time to train. In contrast, the Decision Tree and Logistic Regression classifiers seem to perform relatively well, while the K-Nearest Neighbor classifier is slightly weaker when hyperparameters are tuned. All three seem to train relatively fast compared to the Support Vector classifier.

## Recommendations

Based on the model, the recommendations for improving the efficiency of marketing campaigns seem to be to target marketing campaign at times when the economy is strong:
- high consumer price index
- high consumer confidence
- strong lending rates (`euribor3m`)
- March

# Next Steps

While several models were analyzed, and tuning of their parameters was performed, based on the results of the logistic regression classifier coefficients, it suggests that feature selection may be effective at deriving similar predictive accuracy with much lower computing requirements. As a next step, it would be interesting to introduce a feature selection step in the processing pipeline to reduce the size of the model and see whether similar performance can be achieved with faster training times.

Also, since the target classes are not evenly distributed, the yield, or successful conversion rate of subscribers is only about 12%, a different analysis like F1 score or ROC/AUC curves may be a better method to compare the models.

As for narrowing the target customer profile, it seems the product the banking institution is targeting is a product that makes cash assets illiquid for a period of time. The data shows that customers are amenable to such products when the economy is strong, and hesitant when there is uncertainty in the market or employment rates. Retirees and students seem to respond well, while working professionals seem less inclined. The recommendation is for the banking institution to explore what demographics have a tendency to invest in these types of products, and also to compare how their product offerings in this area compares to industry benchmark and competitors. They may want to consider refining their product by investigating whether rates or term periods or withdrawal penalties are affecting the success of their campaigns.
