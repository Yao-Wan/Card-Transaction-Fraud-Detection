# Fraud Detection for Credit Card Transaction
A supervised machine learning model in Python

## Description
- This is a group project from the *Fraud Analytics* course at Rady School of Management, UC San Diego.
- The goal was to build a fraud model to identify and predict fraudulent credit card transactions, and to choose an optimal cutoff point for rejecting potential fraudulent transaction.
- Various algorithms were attempted including Logistic Regression, Neural Networks, Random Forest, and XGBoost.

## Dataset
- Actual credit card purchase records from a US government organization.
- Has almost 100,000 records in 2010, including 1059 fraud records.

## Methods
- Performed exploratory data analysis, then conducted a data quality report.
- Cleaned data and filled in missing values.
- By grouping some fields and creating bins, we created 7 new entities that will be used for candidate variables building (e.g., Grouping Card number and zip code to create new entity that indicate the combination of the two pieces of information for each record). Along with 2 entities from the original dataset, we now have a total of 9 entities. 
- Then, 4 different categories of variables were developed for each entity, and 603 candidate variables were made including: 
- 432 amount variables (e.g., maximum transaction amount over the past 3 days under the same condition);
- 54 frequency variables (e.g., count of the transactions under the same condition over past 7 days);
- 9 days-since variables (e.g., count of number of days since the most recent transaction under the same condition)
- 108 velocity change variables (e.g., the ratio between the count of transaction in one day and 7 days under the same condition)
- Transformed two categorical variables using target encoding method. To avoid the risk of overfitting, the last 4 months’ worth of data were taken out as out of time sample, an only data from the first 8 months were used when calculating the values.
- Reduced dimensionality of the data by using filter and wrapper methods.
	- In the filter, univariate Kolmogorov-Smirnov (KS) and Fraud Detection Rate (FDR) were used, and the average of the two ranks generated are used to determine the top 80 variables to be used in the wrapper.
	- The wrapper was run through the mlxtend_feature_selection library and a simple Random Forest model and the top 30 variables were selected.
- Multiple models with different combination of variables and hyper parameters were built including:
	- 12 Logistic Regression models
	- 12 Neutral Network models
	- 8 Gradient Boosted Tree models
	- 10 Random Forest models
	- 5 Decision Tree models
- Each model has been run for 10 times and the average of their metrics were used to determine their performances
- Using the best performed model, the data were sorted by the predicted fraud score. The results were then split into bins and the actual fraud rate in each bin has been calculated.
- By plotting the fraud savings, lost sales, and overall savings for all bins from the out of time data in the order of their fraud scores, a cutoff of 3% is recommended for rejection to achieve the highest overall savings.

## Conclusion
- The fraud algorithms used in this project worked well and helped identify credit card fraud. 
- There is room for improvement. A lot of the processes were manual and time consuming; need more research and communicated with domain experts to come up with finer candidate variables more or hyper parameter tuning could provide a better performing model etc.

**Please refer to the report and code files for more detail**







