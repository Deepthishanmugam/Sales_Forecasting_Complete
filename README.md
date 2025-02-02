## **Product sales forecasting**

### **Contents**
1. Introduction
2. Exploratory Data Analysis
3. Hypothesis Testing
4. Pre-Processing of data before modelling
5. Feature Engineering
6. Modelling
7. Comparison of model performance and conclusions
8. Further Studies
9. GitHub Repository and LinkedIn
10. Recommendations
    
## **1. Introduction**
Sales forecasting is the process of predicting future sales using historical data and analytical techniques. It plays a crucial role in business planning, inventory management, marketing strategies, and budgeting. By accurately forecasting sales, businesses can anticipate demand, optimize operations, and make informed decisions about resource allocation.

**1.1 Objective**
By forecasting helping businesses to meet customer demand without overstocking or understocking inventory, thus maximizing profits and minimizing waste.

**1.2 Importance of Sales Forecasting**
Sales forecasting is critical for several reasons:
 —  Inventory Management:
Accurate forecasting helps ensure you have the right amount of product in stock to meet demand without tying up excessive capital in unsold inventory.
 —  Budgeting and Financial Planning:
Sales forecasts provide a foundation for budgeting, financial projections, and cash flow planning, allowing businesses to allocate resources more efficiently.
 — Marketing and Promotions:
By understanding expected sales, businesses can better plan marketing campaigns, promotional activities, and discounts to drive demand when it’s needed most.
 — Workforce Planning:
Accurate sales forecasts help businesses plan staffing levels, ensuring they have the right number of employees to handle expected sales volumes.
 — Investment Decisions:
Sales forecasts help in strategic decision-making, such as deciding when to launch new products or when to discontinue underperforming ones.

**1.3 Step in Sales Forecasting**
Data Collection:
Collecting historical sales data for forecasting. This data could include factors like units sold, pricing, promotional activity, and any external factors.
Data Preprocessing:
Clean and organize the data. Handle any missing values, outliers, or anomalies in the dataset.
Model Selection:
Choosing the appropriate forecasting method based on the data and the objective. For example:
- Time series models
- Regression models
- Machine learning models
Model Training & Forecasting:
Train the model using historical data. Use the trained model to generate forecasts for future sales. This can involve predicting sales for the upcoming months, quarters, or even years.
Evaluation & Refinement:
Compare the forecasted sales with actual sales data to evaluate the accuracy. Common evaluation metrics include Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), and Mean Absolute Percentage Error (MAPE). & Refine models based on the evaluation

**1.4 Factors affecting Sales Forecasting**
Several factors can affect product sales, and they should be considered during the forecasting process:
Seasonality:
Many products experience seasonal variations (e.g., higher sales during the holiday season).
Promotions and Discounts:
Special offers can drive sales, and these need to be factored into the forecast.
Market Conditions:
Economic factors like inflation, consumer confidence, or competitor behavior can impact sales.
External Events:
Events such as natural disasters, or trends (e.g., pandemics) can affect demand unexpectedly.
Product Lifecycle:
Sales may decline as a product moves through its lifecycle from introduction to maturity and then decline stages.

**1.5 Concepts used:**
 — Data Cleaning
 — Feature Engineering
— Data Transformation
— Train-Test Split
— Model Selection
— Ensemble Techniques
— Model Evaluation and Validation

**1.6 Data Source:**
We will use the dataset — SalesData that is available on drive.
There are two types of datasets available, one for training and other for testing. For analysis we have used the training dataset, which contains 1,88,340 records and use about 8+ MB of memory. There are 10 columns present in the dataset. The dataset is in the form of .csv format.

**1.7 Column Profile**
· ID — ID of each individual Order
· Store_id — ID of individual store
· Store_Type — Types of stores available, differentiated by 4 different types
· Location_Type — Types of location available, differentiated by 4 different types
· Region_Code — Types of region available, differentiated by 4 different types
· Date — Dates are given for individual days for two years 2018 & 2019
· Holiday — This column is given to notify about holiday if its holiday its notified by 1 else 0
· Discount — This column is given to notify about Discount if discount is provided its notified by ‘yes’ else ‘no’
· #Order — Number of orders done in that particular day
· Sales — Total sales data

## **2. Exploratory Data Analysis**
Exploratory Data Analysis (EDA) is a crucial step in the data analysis process. (EDA) is the process of analyzing and visualizing datasets to summarize their main characteristics and uncover patterns, relationships, and insights before applying any formal modeling techniques. It helps in understanding the structure and nuances of the data, and can often guide subsequent steps in data preprocessing, feature engineering, and model selection.
Key factors involved in EDA:
1.	Check for data quality (e.g., missing values, duplicates).
2.	Understand distributions of variables.
3.	Identify relationships between features.
4.	Uncover patterns and anomalies (outliers).
5.	Generate hypotheses and insights
Before moving ahead with EDA we will first, import some libraries like pandas, numpy, matplotlib etc. Then we will be reading the data. Note that data is in .csv format.
![image](https://github.com/user-attachments/assets/1527e09e-3621-456f-bbf7-a0b5b05b7714)

 
Below is how the data looks like, Data is quite straight forward, that consist of int, string, & float datatypes which is also properly formatted hence we are proceeding with the given data directly, where almost all the column are non-null
  ![image](https://github.com/user-attachments/assets/908e16e5-3557-469a-ac77-c2f15e0ab238)
![image](https://github.com/user-attachments/assets/cb705e9a-e719-44c7-837d-801b50411875)


As we progress further, Below factors are analyzed in EDA, which are as follows,

**2.1 Handling Missing Values:**
Missing values needs to be handled mainly to ensure below,
· Accuracy
· Data Integrity &
· Bias Prevention
From the given data we could see that there are no missing values present, which makes it easier for further Imputations & Analyzations
![image](https://github.com/user-attachments/assets/04ce258d-421b-455e-a0ca-f929d1ca1bc5)

 
Basic data distribution analysis:
Its important to analyze and understand existing historical data, in order to modify it for future predictions. Below Interpretations gives us clear picture about the distribution of data.
Interpretations:
 — Among Store_Type, S1 records higher Sales
— Among Region, R1 records higher Sales
 ![image](https://github.com/user-attachments/assets/ee3f880b-d36d-4111-8e97-0349592d70a8)

— Among Locations, L1 records higher Sales
 ![image](https://github.com/user-attachments/assets/48ef4a16-84d4-45fb-bfc5-48a216f028cf)

— Among Months, 3rd month records higher Sales
![image](https://github.com/user-attachments/assets/10538412-91f0-439b-ba61-42fd8f62d008)

 
— From Holiday & Discounts, we could see variations are its equally distributed.
![image](https://github.com/user-attachments/assets/8e3ab2e2-7d8f-47a8-9598-71779a130b59)

 
**2.2 Univariate Analysis:**
As it is the first step of EDA, Basically refers to the analysis of a single variable in a dataset.
It is done to understand the following:
· Distribution
· Central tendency
· Spread &
· Overall characteristics of that variable.
For this we are mainly considering below features from the data
- Sales
- Order
 ![image](https://github.com/user-attachments/assets/45e766bf-0896-4f10-8488-b6ac0c67282f)

**2.2.1 Sales Analysis Interpretations:**
Below shows the basic distribution and Outliers present under Sales.
![image](https://github.com/user-attachments/assets/2b36553a-244b-45ef-bfc9-a136ae5f621e)

Central Tendency:
The mean (42784) and median (39678) are fairly close, suggesting that the data is somewhat symmetrical.
Dispersion:
The standard deviation of 18456 indicates that there is moderate variability in sales values.
Skewness:
Since the mean is slightly greater than the median, the data may be right-skewed (positively skewed), there might be few very high sales figures present in data which is pulling the distribution to the right.
Percentiles:
The 25th percentile (Q1) is 30426, the median (50th percentile) is 39678, and the 75th percentile (Q3) is 51909 which shows that half of the sales lies around 30426 & 39678. Therefore, the majority of sales transactions are clustered around these values, with a few very low or very high sales figures outside this range.
Outliers:
Considering the range extends from 0 to 247215 sales record of 0 could be a low-performing transaction, while 247215 could be an unusually high sale.

**2.2.2 Orders Analysis Interpretations:**
Below shows the basic distribution and Outliers present under Orders.
 ![image](https://github.com/user-attachments/assets/7ba3099b-9ef9-430c-814f-39c47368a84e)

Central Tendency:
The mean (68) and median (63) are fairly close, suggesting that the data is somewhat symmetrical.
Dispersion:
The standard deviation of 30 indicates that there is moderate variability in sales values.
Skewness:
Since the mean is slightly greater than the median, the data may be right-skewed (positively skewed), there might be few very high Orders present in data which is pulling the distribution to the right.
Percentiles:
The 25th percentile (Q1) is 48, the median (50th percentile) is 63, and the 75th percentile (Q3) is 82 which shows that half of the sales lies around 48 & 82. Therefore, the majority of Orders are clustered around these values, with a few very low or very high sales figures outside this range.
Outliers:
Considering the range extends from 0 to 371 sales record of 0 could be a low-performing transaction, while 371 could be an unusually highest Order.

**2.3 Bivariate Analysis:**
As the analyzation step of EDA, Basically it analyses the relationship between variables, It is done to do following analysis
· Strength of the Relationship
· Direction of the Relationship
· Significance
· Cause and Effect.

**2.3.1 Sales across Orders**
 ![image](https://github.com/user-attachments/assets/d091e070-e5ba-4c1c-9e92-e0a00938f4a7)

Strength of the Relationship:
Since the correlation coefficient is to 0.9, it indicates the stronger the relationship between Sales & Orders.
Direction of the Relationship:
As we can see as Order increases, Sales also gets increased, so we can conclude its positively correlated.
Significance:
Statistical tests shows that observed relationship is statistically significant.
Further t-test and chi-square tests are done to analyze the statistical significance, results are shown below,
 ![image](https://github.com/user-attachments/assets/b8afcabf-96e7-46e5-8db1-a6f159c5618f)

**2.3.2 Sales across Discounts**
 ![image](https://github.com/user-attachments/assets/b0d7bbcc-b039-401f-8c40-d60aac32754e)

Strength of the Relationship:
Since the correlation coefficient is 0.3, it indicates the weak to moderate positive relationship.
Direction of the Relationship:
Since the correlation coefficient is 0.3, there is a positive relationship between Sales and Discount. which means as the discount increases, sales tend to increase, although the relationship is weak to moderate.
Significance:
Statistical tests shows that the relationship has very less statistical significance.
Further t-test and chi-square tests are done to analyze the statistical significance, results are shown below,
![image](https://github.com/user-attachments/assets/768aadbf-29cc-477f-ab90-cb303ce680a3)


**2.3.3 Sales vs Holidays**
 ![image](https://github.com/user-attachments/assets/6030fbe8-6295-42fe-a7aa-e7120ede58a5)

Strength of the Relationship:
Since the correlation coefficient is -0.2, it indicates very less or no relationship between Sales & Holiday.
Direction of the Relationship:
Since the correlation coefficient is -0.2, there is a Negative relationship between Sales and Holiday. Which means holiday has very less or no effect on Sales increase.
Significance:
Statistical tests shows that the relationship has no statistical significance, results are shown below,
 ![image](https://github.com/user-attachments/assets/51bad258-bf74-4d98-b92d-ecffc436033d)

**2.3.4 Sales vs Store_type**
 ![image](https://github.com/user-attachments/assets/04471533-f185-403f-90c9-3e9840018cd1)

Median:
Median of store S4 seems to be higher than other stores, we can assume that in S4 location the sales is quite high compared to other stores.
Interquartile Range (IQR):
Similarly, IQR for S4 seems to be wider than other stores IQR, so we can assume that in S4 location the sales is quite high compared to other stores.
Whiskers:
From below we can see that the whiskers of S4 is quite big which indicates that the sales are more spread out in S4.
Outliers:
For Outlier too S4 stands out, where there are more variations among sales done by customers.
 ![image](https://github.com/user-attachments/assets/986300b7-fc3b-45bb-8327-77ee44d09cfa)

**2.3.5 Sales vs Location_type**
 ![image](https://github.com/user-attachments/assets/34baad46-a9f6-4f04-a93e-095f7a311e11)

Median:
Median of store L2 seems to be higher than other stores, we can assume that in L2 location the sales is quite high compared to other stores.
Interquartile Range (IQR):
Similarly, IQR for L2 seems to be wider than other stores IQR, so we can assume that in L2 location the sales is quite high compared to oher stores.
Whiskers:
From below we can see that the whiskers of L2 is quite big which indicates that the sales are more spread out in L2.
Outliers:
For Outlier too L2 stands out, where there are more variations among sales done by customers.
 ![image](https://github.com/user-attachments/assets/e37d6fbc-4fab-491a-adba-e37679ad3bbf)

**2.3.6 Sales vs Region_Code**
 ![image](https://github.com/user-attachments/assets/be4f2467-96b7-4599-a45c-1d6a82e02043)

Median:
Median of store R1 seems to be higher than other stores, we can assume that in R1 location the sales is quite high compared to other stores.
Interquartile Range (IQR):
Similarly, IQR for R1 seems to be wider than other stores IQR, so we can assume that in R1 location the sales is quite high compared to other stores.
Whiskers:
From below we can see that the whiskers of R1 is quite big which indicates that the sales are more spread out in R1.
Outliers:
For Outlier too R1 stands out, where there are more variations among sales done by customers.
 
**2.4 Time Series Analysis**
The time series plot shows the total sales over time. It is done to determine the following:
· Trend
· Seasonality
· Outliers
  ![image](https://github.com/user-attachments/assets/31aac72b-ab13-4824-9c49-cb957e3436ce)
  ![image](https://github.com/user-attachments/assets/7e891f80-361b-4a75-91a6-cdf0c64cf239)


Trend Component:
However from the given data sales variations are quite high, but in the last month of the given data sales is towards upward trend, so we can assume that there is a gradual increase in sales.
Seasonal Component:
Repeating fluctuations are found in the given data that occur at specific periods, consistent peaks are found after April month maybe due to seasonality i-e. holidays
Residual Component (Noise):
The data is scattered randomly and there are no patterns to be found which indicates the proper decomposition.
Forecasting:
In addition to the above forecasting is also done for next 6 months down the line, which shows the consistent sales, means there is no steep downfall in the sales.
ARIMA Forecasting for next 5 months:
 ![image](https://github.com/user-attachments/assets/32e754dd-32e3-4844-9303-cd8529f3fa38)

**2.5 Categorical Analysis**
This specific analysation is done to analyse the overall distribution of categories from the given historical data, Further below analyzations are done for coming to conclusions,
Frequency Distribution:
A simple calculation of how often each category appears in the dataset.
Contingency Tables:
Via which the relationships between categorical variables are analysed.
Chi-Square Test:
It is mainly done to determine if there is a significant relationship between two categorical variables. Above tests will be done from the given data, from which we are analysing if below relationships are present,
Holiday & Discount impact on
· Store_Type
· Location_Type
· Region_Code
From the below inferences we can quite come to assumption that there are no significant relationships between any of the categorical variables.
 ![image](https://github.com/user-attachments/assets/dfb3fe5a-18b6-4ae7-910c-7eb7edcdd55e)

**2.6 Outlier Detection**
It is mainly done to identify data points that are significantly different from the majority of the data in order to decide whether to correct them, or remove them from the analysis. It mainly helps in below,
· Improving Model Accuracy
· Data Quality
· Insights
From the given data we could see there are quite high outliers present, Further Z & IQR test has been done to micro analyse the outliers present inside the given data.
 ![image](https://github.com/user-attachments/assets/28750cbd-1454-47e9-b0cb-fa1d8919c0dc)

## **3. Hypothesis Testing**
It is a statistical method used to evaluate whether there is enough evidence in a sample of data to support or reject a given hypothesis. It involves formulating a null hypothesis (H₀) and an alternative hypothesis (H₁), and then using sample data to calculate a test statistic and p-value. If the p-value is below a predetermined significance level (α), the null hypothesis is rejected in favor of the alternative hypothesis.
It is mainly used to make inferences by following below steps,
· Hypothesis stating
· Choosing Significance Level (α)
· Selecting appropriate testing
· Test Statistic computation
· P-value identification
· Decision making
· Result Interpretation

**3.1 Impact of Discount on Sales**
As Discounts are often used to attract customers, & encourage more purchases and sometimes used to clear inventory. In addition to above discounts are provided to encourage below factors such as,
· Increased Demand Due to Lower Prices
· Customer Perception and Behavior
· Attracting New Customers and Retaining Existing Ones
· Competitive Advantages
· Impact on Profitability
Why t-test?
As it allows to determine if there is a statistically significant difference in the sales before and after a discount is applied,
Assumptions of the T-test:
· Sample Groups :
1. Sales before discount
2. Sales after discount
· Normality:
Data is normally distributed
· Equal variance:
Group variances are similar
· Form Hypotheses:
Null Hypothesis (H₀): The discount does not impact sales
Alternative Hypothesis (H₁): The discount impacts sales
Below are the inferences made out of it,
 ![image](https://github.com/user-attachments/assets/77cd1165-1183-45d8-b212-af60dd6fb7c6)

**3.2 Effect of Holidays on Sales**
Similar to Discounts we can further analyze if Holidays impact sales
· Time availability of customer for purchase
· Shopping mode
· Possibility of increased visits
Why t-test?
As it allows to determine if there is a statistically significant difference in the sales before and after a Holidays,
Assumptions of the T-test:
· Sample Groups :
1. Sales during holidays
2. Sales during non- holidays
· Normality:
Data is normally distributed
· Equal variance:
Group variances are similar
· Form Hypotheses:
Null Hypothesis (H₀): Holidays does not impact sales
Alternative Hypothesis (H₁): Holidays impacts sales
Below are the inferences made out of it,
 ![image](https://github.com/user-attachments/assets/eba5b25b-48e9-4e03-8338-52e9d15c31cb)

**3.3 Sales Difference across Store_Types**
We can analyze if the sales happening across different store_types are different in order to do following,
· Replicate the same business strategies to increase sales
· Collecting feedback from locality customers, what they are seeking for
· Getting to know the demand
· Implementing new advertisement stategies for improving sales
Why ANOVA?
Since we have more than two groups anova helps us to do comparison easily as it is a well-established, efficient, and widely-used method in statistics.
Assumptions of the ANOVA:
· Independence :
Sales from each store type should be independent of each other
· Normality:
The sales data for each store type should follow a normal distribution.
· Equal variance:
Group variances are similar
· Form Hypotheses:
The variance in sales should be roughly equal across the store types Since Levene’s test is flexible & robust to Non-Normality, it is used in analysing homoscedasticity.
Null Hypothesis (H₀): There is no significant difference in sales across store types.
 Alternative Hypothesis (H₁): There is a statistically significant difference in sales across store types.
 ![image](https://github.com/user-attachments/assets/be0a1760-882a-4328-a602-5cd87522d67e)

**3.4 Regional Sales Variability**
We can analyse if the sales happening across different Regions are different in order to do following
· Getting to know the factors affecting sales
· Understanding the distribution of population across region
· Factors affecting sales
· Interest of people
· Identifying Advertisement stategies
· Identifying demand
Why ANOVA?
Since we have more than two groups anova helps us to do comparison easily as it is a well-established, efficient, and widely-used method in statistics.
Assumptions of the ANOVA:
· Independence :
Sales from each Region should be independent of each other
· Normality:
The sales data for each Region should follow a normal distribution.
· Equal variance:
Group variances are similar
· Form Hypotheses:
The variance in sales should be roughly equal across the Regions. Since Levene’s test is flexible & robust to Non-Normality, it is used in analysing homoscedasticity.
Null Hypothesis (H₀): There is no significant difference in sales across Regions.
 Alternative Hypothesis (H₁): There is a statistically significant difference in sales across Regions.
 ![image](https://github.com/user-attachments/assets/b88d185a-714e-4882-ad5a-f4849528b5fd)

**3.5 Correlation between Number of Orders & Sales**
As it helps in identifying the relationship between two factors, Sales & Order in our case. It helps in below factor,
· Getting to know the relationship
· Helps improvising marketing
· Helps implementing promotional efforts
· Helps us focusing on increasing the order volume
· Helps to forecast sales based on expected orders
From below we can see the positive correlation between sales & orders, which means if Order increases sales also increases.
 ![image](https://github.com/user-attachments/assets/473450c4-1e11-45b3-b330-516b3406b2c3)

## **4. Pre-processing of Data before modelling**
It involves preparing the raw data to improve the performance of machine learning models. This includes handling missing values, encoding categorical variables, normalizing or scaling numerical features, and addressing outliers. Proper pre-processing ensures the data is clean, consistent, and formatted in a way that models can efficiently learn from it.
**4.1 Data Cleaning:** Address missing values, remove duplicates, and correct inconsistencies in the dataset.
Data cleaning is an essential step in data preprocessing that involves preparing a dataset for analysis by addressing issues such as missing values, duplicates, and inconsistencies.
Addressing Missing Values :
Purpose :
Since missing data can lead to inaccurate analysis and misleading results we are addressing Missing values.
Implementation :
By removing or Imputing the missing values
Given Data has No Missing Values
 ![image](https://github.com/user-attachments/assets/16321af9-a247-4672-a03e-fb7f28141504)

Removing Duplicates :
Purpose :
Duplicates can skew the analysis, leading to overrepresentation of certain data points or incorrect conclusions.
Implementation :
By removing dupicates
Given Data has No Duplicate Values
 ![image](https://github.com/user-attachments/assets/1a04f35f-2709-44f1-b1ad-869db09cb699)

Correcting Inconsistencies:
Purpose :
Inconsistencies, such as typos, different units of measurement, or varied formatting, can lead to incorrect analysis.
Implementation :
By Standardizing formats
In Given Data Sales & Date columns are standardised
 ![image](https://github.com/user-attachments/assets/913eca7a-6155-4e03-9caf-4bf8ea08e917)

## **5. Feature Engineering**
Feature engineering is the process of creating new features from the existing data to improve the performance of machine learning models. The goal is to make the model better at capturing patterns and relationships.
Developing new features that could enhance the model’s predictive power, such as time-based aggregates (e.g., sales in the last week), ratios, or interaction terms between features.
Time-Based Aggregates:
Purpose :
Creating time-based features helps the model recognize trends or seasonal patterns.
Implementation :
By identifying Time periods such as days of weeks etc.
 ![image](https://github.com/user-attachments/assets/06e11b13-78b8-4318-86a2-c7ac34e7aea4)

Sales per Order:
Purpose :
Creating this feature helps to identify individual sales for each order
Implementation :
By identifying new feature derived by doing a ratio
  ![image](https://github.com/user-attachments/assets/91be8cad-e410-4641-8342-dae960615a2c)
Create a Rolling Average of Sales:
Purpose :
A rolling average smooths out helps identify longer-term trends, making it useful for time-series analysis.
Implementation :
for each day, the average sales of the previous 7 days is calculated, including that day. This helps reduce the impact of daily volatility

 ![image](https://github.com/user-attachments/assets/4d52f222-8da3-444d-b78b-580cefb2b381)


Discount Effectiveness:
Purpose :
Discounts often affect sales, and this feature can help the model understand if the increase (or decrease) in sales is due to the discount.
Implementation :
Implementing a simple flag that indicates whether a discount was offered during a given period.
   ![image](https://github.com/user-attachments/assets/bd0d279d-ec56-47f0-a246-dbee64d735c9)

Interaction Term:
Purpose :
It allows the model to capture how the combined effect of these features might influence the target variable.
Implementation :
It is implemented by combining the Store_Type and Region_Code variables.
 ![image](https://github.com/user-attachments/assets/b0220b84-da9a-472e-b509-50d304e2f0c3)

Lagged Features :
Purpose :
Lagged features help the model use past data to predict future events.
Implementation :
By creating a new feature that represents the sales from a previous time period, the previous day
 ![image](https://github.com/user-attachments/assets/1a6842c5-3ac8-47ad-a4da-88e9bafc8ac8)

Rolling Window:
Purpose :
A rolling sum can provide a sense of the cumulative sales activity over a longer period.
Implementation :
For each day, calculating the sum of sales for the past 30 days, including the current day
 ![image](https://github.com/user-attachments/assets/107db199-d835-49ac-a958-b4765a8bb468)

Total Orders per Store:
Purpose :
Aggregating by Store Type can help capture the overall performance and behavior of each store type
Implementation :
This basically aggregates the total number of orders for each store type
 ![image](https://github.com/user-attachments/assets/f700311d-7585-423c-b824-ef967c956b23)

**5.1 Data Transformation**
Data transformation is a crucial step in data preprocessing that prepares raw data for modeling. This process involves scaling numerical features and encoding categorical variables so that they are in a suitable form for machine learning algorithms.
Scaling Numerical Features:
Purpose :
If numerical features are not scaled models may give disproportionate weight to larger values, leading to biased or inefficient learning.
Implementation :
Done using Normalization & Standardization
Encoding Categorical Variables:
Purpose :
Many machine learning algorithms cannot directly work with categorical variables, so these variables are converted into a numerical format so that the model can process them.
Implementation :
Done using One-Hot Encoding that creates binary columns for each category in the feature.
Further, Data is splitted into train-test split, where a dataset is divided into two subsets: one for training the model and the other for testing its performance. which helps assess how well the model generalizes to new, unseen data and prevents overfitting.
 ![image](https://github.com/user-attachments/assets/2c2dae9c-c0a9-49a5-9725-c1b55ebbb4d3)

**5.2 Train-Test Split**
The train-test split is a fundamental technique used in machine learning used to evaluate the performance of a model.
Training Set:
Purpose :
This portion of the data is used to train the model, i.e., to learn patterns and make predictions.
Test Set:
Purpose :
This portion is used to evaluate the model’s performance after training, giving an unbiased estimate of how well the model will perform on new, unseen data.
Implementation :
Splitting the data in ration 80:20 for training and testing and implementing train_test_split method accordingly.
 ![image](https://github.com/user-attachments/assets/aa1b7e2d-e81b-411b-84dc-27fb005d6541)

## **6. Modelling**
Model selection is a critical step in the machine learning pipeline where you choose the appropriate model (algorithm) to solve your problem. It involves evaluating and selecting the best model based on its performance on your data. The process requires balancing factors such as accuracy, complexity, interpretability, and training time, among others.
Why Model Selection?
To address below
· Performance Variability
· Trade-offs
· Generalization
**6.1. Baseline Model:** Starting with a simple model to establish a baseline performance. Linear regression is a common choice.
A baseline model is a simple model that is easy to implement and provides a starting point for assessing the performance of more complex models. It gives us an initial benchmark that helps understanding the “minimum” performance we should expect. Below are the main purpose of it,
· Initial Performance Estimate
· Quick Evaluation
· Avoid Overfitting
Why Linear Regression?
Purpose :
Linear regression is one of the simplest models and assumes a linear relationship between the input features and the target variable which will be ease for implementation. Since the coefficients of a linear regression model directly indicate the relationship between each feature and the target. This makes it easier to explain the results. Additionally its Quick to Train
Implementation :
By providing Train & Test data as input model makes the prediction by making the values fit a straight line.
- R-squared (0.92): The Linear Regression model explains 92% of the variance in the target variable, indicating a strong fit and good predictive power.
- Mean Absolute Error (3678.6): On average, the model’s predictions are off by 3678.6, which is acceptable based on the scale of the sales data
From above we can conclude that the model performs quite well.
Interpretations:
 ![image](https://github.com/user-attachments/assets/69cf99a9-5d4f-4ddd-82cb-90e97c4bf54c)

**6.2. Complex Models:** Explore more sophisticated models to improve accuracy. Potential models include:
These models are often more powerful and flexible, capable of capturing complex patterns and relationships in the data. The goal is to improve accuracy and enhance the model’s predictive power by moving beyond the basic approach. Below are the main purpose of it,
· Better Accuracy
· Non-linearity
· Flexibility
· Handling More Complex Data
**6.2.1 Complex Models:**
Time Series Model: Applying ARIMA for data forecasting
Purpose:
ARIMA (AutoRegressive Integrated Moving Average) is one of the most widely used models for forecasting time series data.
· It is particularly effective when the data shows trends or seasonality and is based on past observations.
· ARIMA helps predict future values by analyzing past values (autoregressive), the differences between consecutive values (integrated), and the moving average of past errors.
Dickey-Fuller test
•	Using statistical analysis — Dickey-Fuller Test we can determine whether a given time series is stationary or non-stationary.
•	In time series analysis, we will find stationarity(constant over time) / non-stationary(show trends or seasonality, which need to be addressed before modeling.)
 
Differencing
•	From the data considered the series was already stationary, still the differencing is done and got the below p-values and other factors,
ADF Statistic: -3.4590273622955423
 p-value: 0.009103860345178972
 Critical Values:
 1%: -3.4436029548776395
 5%: -2.867384756137026
 10%: -2.5698830308597813
•	Using Differencing technique for time series analysis to transform a non-stationary series into a stationary one.
•	Differencing helps to remove trends and seasonality from a time series, making it more suitable for modeling.
 ![image](https://github.com/user-attachments/assets/cd642cb3-180f-4b63-9fdd-69ac8ba8674f)

Decomposition
•	Time series decomposition is helps to understand the underlying patterns and improving forecasting accuracy & improve decision-making..
•	where the time series split into components: trend, seasonality, and residual (or noise).
 ![image](https://github.com/user-attachments/assets/03ebe920-264b-4bbc-9d4e-358767a226b6)

ACF and PACF
•	In order to understand the relationships between an observation and its past values &
•	Identifying appropriate time series models & understanding the structure of the data below plots are implemented.
 ![image](https://github.com/user-attachments/assets/599b6eba-b3db-47ec-b132-b58965ddd316)


•	ARIMA Forecasting
 ![image](https://github.com/user-attachments/assets/38276ce0-7c6e-45b8-9845-d1560379eef1)
Components:
The ARIMA model is denoted as ARIMA(p, d, q), where:
· p is the number of lag observations in the autoregressive part (AR).
· d is the number of times the data is differenced to make it stationary.
· q is the size of the moving average window (MA).
Once the model is fitted it can be used to make predictions and forecasts.
![image](https://github.com/user-attachments/assets/13eca0e2-9b34-4eb8-92c2-6d50fc94a9f3)

 

SARIMA Forecasting
•	SARIMA (Seasonal AutoRegressive Integrated Moving Average) an extension of the ARIMA model which explicitly accounts for seasonality in time series data.
•	It is mainly used to model time series data that exhibits both non-seasonal and seasonal behaviors using components such as (AutoRegressive, Integrated, Moving Average & Seasonality)
Dickey-Fuller test
•	Using statistical analysis — Dickey-Fuller Test we can determine whether a given time series is stationary or non-stationary.
•	In time series analysis, we will find stationarity(constant over time) / non-stationary(show trends or seasonality, which need to be addressed before modeling.)
  ![image](https://github.com/user-attachments/assets/3ad1c029-4a0b-4f9b-9f2a-bd8e1589008c)

Decomposition
•	Time series decomposition is helps to understand the underlying patterns and improving forecasting accuracy.
•	where the time series split into components: trend, seasonality, and residual (or noise).
 ![image](https://github.com/user-attachments/assets/d7ce867c-dd45-4edc-8e44-f65cf94d8402)

ACF and PACF
•	In order to understand the relationships between an observation and its past values &
•	Identifying appropriate time series models (like ARIMA) & understanding the structure of the data below plots are implemented.
 ![image](https://github.com/user-attachments/assets/3ea16497-9686-40df-9ee1-b717cd28c174)

SARIMA Forecasting
 ![image](https://github.com/user-attachments/assets/2d5fd736-00e5-4c22-a968-b1f6c17567e8)

fb Prophet
•	A reliable forecast which handles time series data with strong seasonal patterns and missing data.
•	It handles Trend, Seasonality, Holiday, Errors etc.
Interpretation 1:
 ![image](https://github.com/user-attachments/assets/2c5f9232-493c-4649-a7c1-bd4627c14444)

•	The yhat values represent the model’s forecasted values for future periods (e.g., predicted sales).
•	The uncertainty intervals (yhat_lower and yhat_upper) show the model’s confidence in the forecast. The larger the interval, the higher the uncertainty.
•	The trend line shows the underlying pattern of the data over time. It helps us understand whether the model expects the value to increase, decrease, or remain stable.
The plot visually demonstrates how the forecast fits into the historical data and extends into the future, along with uncertainty bounds.
Interpretation 2:
 ![image](https://github.com/user-attachments/assets/092ea997-d239-4b81-a9c8-b6460bf65c55)

Trend:
•	It implies the overall long-term pattern the model has learned based on historical data.
•	The trend line helps us understand the broader movement in the data over time, such as the general growth, downfall may be due to any factors such as competition, pandemic, natural causes etc.
Seasonality:
•	The seasonality component shows how the data behaves in recurring cycles, here in weekly patterns.
•	We could see that Sales increases during holidays rather than working days
Interpretation 3:
 ![image](https://github.com/user-attachments/assets/16f5f4e5-8802-45bd-9283-b19e260e25dc)

Forecast Line:
The plot will show the predicted values for future periods
Uncertainty Interval:
The shaded area represents the range within which the actual future values are expected to fall, with the model’s confidence.
Changepoints:
The vertical lines indicate when a change in trend occurs. These points are critical to understanding where significant shifts in the data are happening.
**6.2.2 Tree-Based Model:** Applying Random Forest to improve performance by capturing complex relationships between features:
Purpose:
It is an ensemble learning method that builds multiple decision trees and combines their predictions to improve overall performance.
· It is particularly effective for capturing complex relationships between features in your data that might be difficult for simpler models to identify.
· It also offers advantages like reducing overfitting, improving accuracy, and handling both numerical and categorical features well.
Components:
· Ensemble of Trees
· Bootstrap Aggregating (Bagging)
· Feature Randomness
· Voting
Implementation:
· Prepare the Data
· Split the Data into Training and Testing Sets
· Train the Random Forest Model
· Make Predicitions
· Evaluate the model (R2 & MAE)
By providing Train & Test data as input model makes the prediction by making the values fit a straight line.
•	R-squared (0.96): The RandomForest model explains 96% of the variance in the target variable, indicating a strong fit and good predictive power.
•	Mean Absolute Error (2309.2): On average, the model’s predictions are off by 2083.91, which is acceptable based on the scale of the sales data
Further below plots implies the good fit of data & additionally shows the feature importance where feature- #Order stands out.
 ![image](https://github.com/user-attachments/assets/4b4eded3-3f36-4bc8-96f2-837f686a343b)

**6.2.3 Gradient Boosting Model:** XGBoost XGBoost is a powerful boosting algorithm that often yields state-of-the-art results:
Purpose:
Gradient Boosting is an ensemble learning technique that builds multiple weak learners (usually decision trees) sequentially. Each new tree tries to correct the errors made by the previous tree. It does so by fitting the new tree to the residual errors of the previous model, meaning it focuses on learning where the previous models made mistakes.
XGBoost is particularly known for its speed, accuracy, and ability to handle a variety of data types and challenges, such as missing values and overfitting.
Components:
· Boosting Process
· Gradient Descent Optimization
· Regularization
· Shrinkage
Implementation:
· Install XGBoost
· Prepare Data
· Convert Data to DMatrix Format
· Define the Model
· Train the Model
· Make Predictions and Evaluate the Model
· Feature Importance
· R-squared (0.9700): The XGBoost model explains 97% of the variance in the target variable, indicating a strong fit and good predictive power.
· Mean Absolute Error (2083.9067): On average, the model’s predictions are off by 2083.91, which is acceptable based on the scale of the sales data
Further below plots implies the good fit of data & additionally shows the feature importance where feature- #Order stands out.
 ![image](https://github.com/user-attachments/assets/f3b0f58f-090a-40f0-abca-268bdb350596)

**6.2.4 Deep Learning Model:** LSTM for Time Series Forecasting implementing an LSTM model for forecasting future sales. LSTMs are ideal for sequential data like time series.
Purpose:
These models are capable of learning long-term dependencies in data, which makes them highly effective for forecasting tasks where future values are influenced by historical observations.
Components:
· Ensemble of Trees
· Bootstrap Aggregating (Bagging)
· Feature Randomness
· Voting
Implementation:
· Prepare the Data
· Normalize the Data
· Create Time Series Sequences
· Split the Data into Training and Test Sets
· Build the LSTM Model
· Train & Evaluate the model
· Make Predictions
Interpertation
•	The model predicts that sales will fluctuate slightly across the next 5 periods, with values ranging from 42,492.63 to 44,855.38.
•	There is no drastic change in sales, suggesting relative stability or moderate growth/decline over the forecasted periods.
•	This prediction can be useful for making business decisions related to stock, staffing, or marketing strategies.
· R-squared (60.6522): A value of 60.6522 suggests that the model tends to have relatively small errors.
· Mean Absolute Error (3678.6912): On average, the model’s predictions are off by 3,678.69. This represents the average magnitude of error
Model Output : 
  ![image](https://github.com/user-attachments/assets/e00127c3-f543-446f-a39e-1ab33230fdc6)

## **7. Model Comparison (Comparison of model performance and conclusions):**
•	XGBoost 
performs the best with the lowest MAE (2054.81) and RMSE (3174.78), along with the highest R² (0.9702), indicating it makes the most accurate predictions and explains the highest proportion of variance in the data.
•	Random Forest 
also performs well with a slightly higher MAE (2280.82) and RMSE (3559.49), but still offers a strong R² (0.9625), indicating robust predictive performance.
•	LSTM 
has a higher MAE (3516.16) and RMSE (4827.48) compared to XGBoost and Random Forest, and its R² (0.9311) is slightly lower comparatively, but still it provides a good accuracy.
•	Linear Regression
has highest MAE (4055.23), RMSE (5512.46), and the lowest R² (0.9101), Comparatively which is low but still provides good data variances
 
Model Evaluation and Validation:
Model evaluation involves assessing a model’s performance using metrics like accuracy, precision, recall, R-squared, MAE, and RMSE on a test dataset to understand how well it generalizes to unseen data.
Validation ensures that the model’s performance is consistent across different subsets of the data, often using techniques like cross-validation.
This process helps prevent overfitting and ensures the model is reliable and robust for deployment.
Cross-Validation: Implement time-series specific cross-validation techniques to evaluate model performance over different temporal splits of the data.
•	Time-series cross-validation ensures that the temporal order of data is maintained, preventing future data from being used to predict past events.
•	Techniques like rolling-window or expanding-window splits are used, where the model is trained on past data and tested on future data.
•	This method evaluates how well the model generalizes over different time periods and prevents data leakage.
Interpretations:
The model evaluation shows the following:
MAE (Mean Absolute Error):
•	The MAE for each fold ranges from 2499.98 to 4317.44, with an average of 3397.08. This indicates that, on average, the model’s predictions deviate by about 3397.08 units from the actual values.
RMSE (Root Mean Squared Error):
•	The RMSE values range from 3836.37 to 5593.73, with an average of 4936.23. Since RMSE penalizes larger errors more heavily, this suggests that the model has some larger prediction errors but generally performs reasonably well.
R2 (R-squared):
•	The R2 values range from 0.90 to 0.96, with an average of 0.93. This indicates that the model explains about 93% of the variance in the data, which is a strong performance.
From below we can conclude that the models performs well, with high R2 indicating strong predictive power, and MAE and RMSE showing moderate prediction errors. There’s a slight variance in performance across the folds, but overall, the model generalizes well.
 ![image](https://github.com/user-attachments/assets/2208d58d-cee8-4ea2-a2ab-22241d576927)

Performance Metrics: Using metrics appropriate for regression tasks, such as MAE (Mean Absolute Error), MSE (Mean Squared Error), RMSE (Root Mean Squared Error), and MAPE (Mean Absolute Percentage Error).
Performance metrics for regression tasks help evaluate the accuracy of predictions.
MAE (Mean Absolute Error):
•	The MAE of 35,815.65 indicates that, on average, the model’s predictions are off by about 35,815.65 units from the actual values. This gives a sense of the model’s overall prediction accuracy.
MSE (Mean Squared Error):
•	The MSE of 1,620,327,772.24 is very large, which suggests that the model has some significant prediction errors. MSE penalizes larger errors more heavily due to the squaring of differences, indicating that the model might be producing large outliers in predictions.
RMSE (Root Mean Squared Error):
•	The RMSE of 40,253.30 represents the square root of the MSE and gives a more interpretable scale. It’s still large, showing that the model has substantial prediction errors, which could affect the model’s reliability.
MAPE (Mean Absolute Percentage Error):
•	The MAPE is infinite (inf%), which suggests that the model is making predictions where the actual values are zero or close to zero in some cases. Since MAPE involves division by the actual values, it cannot handle zero values and thus leads to an “infinite” result.
 ![image](https://github.com/user-attachments/assets/be1e7a15-7fa3-4579-a623-9c6acfe42554)

Residual Analysis: Analyzing the residuals to ensure there are no patterns left unmodeled.
Performance metrics for regression tasks help evaluate the accuracy of predictions.
•	MAE (Mean Absolute Error):
•	The MAE of 3653.6488 indicates that, on average, the model’s predictions are off by about 3653.6488 units from the actual values. This gives a sense of the model’s overall prediction accuracy.
 ![image](https://github.com/user-attachments/assets/e150284a-b350-4eea-b4f7-9980f73ac5a0)

Residual vs Predicted Sales:
This plot shows the relationship between the residuals (the difference between actual and predicted values) and the predicted sales.
•	Since there is no pattern (i.e., the residuals are scattered randomly around zero), it suggests that the model is well-fitted and has captured the underlying patterns in the data.
Histogram of Residuals: 
The histogram shows the distribution of the residuals (errors). It helps assess the normality of the residuals.
•	As its normally distributed but very slightly skewed towards other side we can assume that errors are randomly distributed assuming normality
Autocorrelation of Residuals:
This plot or test checks if residuals are correlated with their own lagged values. It’s commonly used in time series data to detect if there are temporal structures not captured by the model.
•	There’s no significant autocorrelation at any lag (i.e., values are close to zero), it suggests that the residuals are independent, and the model has captured all the temporal dependencies.
Residual vs Time:
This plot shows the residuals over time, helping to check for time-based patterns that the model may not have captured.
•	Since there are no patterns, residuals appear randomly scattered, it indicates that the model has accounted for any temporal dependencies in the data.
 ![image](https://github.com/user-attachments/assets/42a0cc5a-44dc-4069-803f-c65769e99573)

Overall residuals are randomly scattered without clear patterns in any of these plots (residual vs predicted, residual vs time, and autocorrelation), it suggests a good model fit.

## **8. Further Studies**
We have trained less models from the data for fast computation. And data is also quite huge it takes quite a bit more time than normal.
- Further we could check using other ML models for more results and accuracy.
- Forecasting can be further made more precise with more data to cope up with any time periods.
•	If above are followed more insights can be provided for sales improvement.

## **9. GitHub Repository and LinkedIn**

## **10. Recommendations**
1. Understand the Customer behavior
Research customer behavior and preferences to tailor the products and marketing strategies effectively.
2. Optimize Inventory Management
Maintain the right balance between supply and demand by monitoring inventory levels and reducing stockouts or excess stock.
3. Offer Promotions and Discounts
Use targeted promotions, seasonal discounts, and limited-time offers to boost sales and attract customers.
4. Leverage Social Media Marketing
Promote products on social media platforms to increase brand awareness, reach a wider audience, and drive sales.
5. Personalize Customer Experience
Provide personalized recommendations, offers, and experiences based on customer data to enhance engagement and sales.
6. Improve Website User Experience
Optimize the website for faster loading times, mobile responsiveness, and easy navigation to enhance online shopping experiences.
7. Enhance Customer Support
Offer excellent customer service via multiple channels (chat, email, phone) to build trust and loyalty, leading to repeat sales.
8. Utilize Influencer Marketing
Partner with influencers in current industry to increase visibility and drive targeted traffic to the product.
9. Implement Referral Programs
Encourage existing customers to refer others by offering incentives like discounts, free products, or loyalty points.
10. Improve Product Availability
Ensure the products are available where the customers shop, whether in-store, online, or via third-party retailers.
11. Track Competitor Performance
Monitor competitors’ pricing, promotions, and sales strategies to stay competitive in the market and adjust the approach.
12. Leverage Customer Reviews and Testimonials
Encourage happy customers to leave reviews. Positive testimonials build social proof and attract more buyers.
13. Introduce New Product Variants
Keep the product offerings fresh by introducing new colors, sizes, or features to cater to different customer needs.
14. Diversify Sales Channels
Sell on multiple platforms like e-commerce sites, marketplaces (Amazon, eBay), or physical stores to reach more customers.
15. Conduct A/B Testing
Regularly test different sales strategies, landing pages, and marketing tactics to identify the most effective approaches.
16. Build Partnerships with Retailers
Strengthen relationships with wholesalers and retailers to expand distribution networks and increase product reach.
17. Focus on Sustainability
Market the product as environmentally friendly or sustainable if it aligns with out brand values to attract conscious consumers.
18. Offer Subscription Models
Create subscription-based pricing for products with consistent demand, ensuring recurring revenue and customer retention.
19. Engage in Cross-Selling and Upselling
Promote complementary products (cross-selling) or higher-value items (upselling) to increase the average order value and sales.
By implementing these recommendations, we can not only increase sales but also improve customer retention and brand loyalty.










### 1. **Understand the Customer behavior**  
   Research customer behavior and preferences to tailor the products and marketing strategies effectively.

### 2. **Optimize Inventory Management**  
   Maintain the right balance between supply and demand by monitoring inventory levels and reducing stockouts or excess stock.

### 3. **Offer Promotions and Discounts**  
   Use targeted promotions, seasonal discounts, and limited-time offers to boost sales and attract customers.

### 4. **Leverage Social Media Marketing**  
   Promote products on social media platforms to increase brand awareness, reach a wider audience, and drive sales.

### 5. **Personalize Customer Experience**  
   Provide personalized recommendations, offers, and experiences based on customer data to enhance engagement and sales.

### 6. **Improve Website User Experience**  
   Optimize the website for faster loading times, mobile responsiveness, and easy navigation to enhance online shopping experiences.

### 7. **Enhance Customer Support**  
   Offer excellent customer service via multiple channels (chat, email, phone) to build trust and loyalty, leading to repeat sales.

### 8. **Utilize Influencer Marketing**  
   Partner with influencers in current industry to increase visibility and drive targeted traffic to the product.

### 9. **Implement Referral Programs**  
   Encourage existing customers to refer others by offering incentives like discounts, free products, or loyalty points.

### 10. **Improve Product Availability**  
   Ensure the products are available where the customers shop, whether in-store, online, or via third-party retailers.

### 11. **Track Competitor Performance**  
   Monitor competitors' pricing, promotions, and sales strategies to stay competitive in the market and adjust the approach.

### 12. **Leverage Customer Reviews and Testimonials**  
   Encourage happy customers to leave reviews. Positive testimonials build social proof and attract more buyers.

### 13. **Introduce New Product Variants**  
   Keep the product offerings fresh by introducing new colors, sizes, or features to cater to different customer needs.

### 14. **Diversify Sales Channels**  
   Sell on multiple platforms like e-commerce sites, marketplaces (Amazon, eBay), or physical stores to reach more customers.

### 15. **Conduct A/B Testing**  
   Regularly test different sales strategies, landing pages, and marketing tactics to identify the most effective approaches.

### 16. **Build Partnerships with Retailers**  
   Strengthen relationships with wholesalers and retailers to expand distribution networks and increase product reach.

### 17. **Focus on Sustainability**  
   Market the product as environmentally friendly or sustainable if it aligns with out brand values to attract conscious consumers.

### 18. **Offer Subscription Models**  
   Create subscription-based pricing for products with consistent demand, ensuring recurring revenue and customer retention.

### 19. **Engage in Cross-Selling and Upselling**  
   Promote complementary products (cross-selling) or higher-value items (upselling) to increase the average order value and sales.

By implementing these recommendations, we can not only increase sales but also improve customer retention and brand loyalty.
