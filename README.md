# CodeClause-price-recommendation-for-online-sellers
## Problem Statement
Mercari is Japan’s biggest community-powered shopping app. Some items on Mercari cannot be sold because their listing prices are too high compared to the market price. Conversely, If the listing price is lower than the market price, customers lose out. Product pricing gets even harder at the sale, considering just how many products are sold online.

Therefore, listing becomes easier if we automatically display a suitable price for users when they list an item.

In this problem statement, the goal is to predict the suitable price of an item given its user-inputted text descriptions of their products, product category name, brand name, and item condition in order to minimize the difference between predicted price and actual price.

## Use of Machine Learning
This is a Regression problem as the price is a continuous variable which we have to predict. Machine learning is an area that deals with different ml/dl regression (predictive modeling) algorithms that can be applied to learn the relationship amongst the dataset variables like product name, category, prices, etc. and can predict the product prices based on that. In this post, we’ll discuss how effectively some of the regression algorithms like Ridge, SGD, MLP, etc. have solved the problem.

## Data Source
This case study is based on the Kaggle Competition Mercari Price Suggestion Challenge, the dataset can be downloaded from https://www.kaggle.com/c/mercari-price-suggestion-challenge/overview/evaluation

## Data Description
Datasets consists of two files train.tsv, test.tsv having following fields:-

train_id or test_id — the id of the listing

name — the title of the listing. Note that we have cleaned the data to remove text that looks like prices (e.g. $20) to avoid leakage. These removed prices are represented as [rm]

item_condition_id — the condition of the items provided by the seller

category_name — the category of the listing

brand_name — brand name of the product

price — the price that the item was sold for. This is the target variable that you will predict. The unit is USD. This column doesn’t exist in test.tsv since that is what you will predict

shipping — 1 if the shipping fee is paid by seller and 0 by buyer

item_description — the full description of the item. Note that we have cleaned the data to remove text that looks like prices (e.g. $20) to avoid leakage. These removed prices are represented as [rm]


## Evaluation Metric — RMSLE
The evaluation metric (or error metric) for this competition is Root Mean Squared Logarithmic Error (RMSLE) which needs to be optimized. The lower the score is, the higher the accuracy of the price suggestion function will be.

## Exploratory Data Analysis (EDA)
It is not easy to look at a data field (column) or a whole spreadsheet and determine important characteristics of the data. EDA is a crucial step in understanding how the data fields are distributed in the dataset to summarize their main characteristics, discover patterns and anomalies, which can be useful in building a better machine learning model. Let’s analyze the data and summarize characteristics:

### Univariate Analysis
Analysis based on one feature or variable only.

### Price
Plotting price histogram shown that price follows a log-normal distribution i.e most of the products lie in between a small range and few of the products have high prices. We can also get sight of the price range lying between 0 and 2500$.

Boxplot gives a nice visualization of data through quartiles. Boxplotting price gave the intuition that 25% of the products range 0–10$, 50% of the product price range between 0–17$%, and 75% of product price is in the range between 0–29$. Investigating further through plotting percentiles revealed that only 1% of the products have a price of more than 170$.

Boxplot gives a nice visualization of data through quartiles. Boxplotting price gave the intuition that 75% of product price is in the range between 0–29$. Investigating further through plotting percentiles revealed that only 1% of the products have a price of more than 170$.



### Brand Name
Plotting the Barplot of top 10 brand_name revealed that almost 50% of the products don’t have brand_name(i.e having brand_name = missing). Top 10 brands that are widely used are ‘missing’, ‘PINK’, ‘Nike’, “Victoria’s Secret”, ‘LuLaRoe’, ‘Apple’, ‘FOREVER 21’, ‘Nintendo’, ‘Lululemon’, ‘Michael Kors’.


### Category Name
This is the category of the item for eg. Men/Tops/T-shirts, Women/Jewelry/Necklaces, etc. It’s separated by ‘/’ into three parts so to better generalize we’ll split category_name into 3 categories namely category_one, category_two, and category_three.

## Conclusion
### Exploratory Data Analysis (EDA) Insights:

Most items fall within the 10 to 20 price range, suggesting a popular price bracket.

Prominent brands include PINK, Nike, Victoria's Secret, and LuLaRoe.

High-end brands such as Demdaco and Proenza Schouler were identified.

Women's products dominate primary categories, led by Women, Beauty, Kids, and Electronics.

Women's category shows substantial items with and without brands.

### Machine Learning Model Insights:

Linear Regression: Achieved an RMSLE of 0.4748, indicating reasonable accuracy.

Random Forest: RMSLE of 0.7192, showing potential for further refinement.

Ridge Regression: Impressive RMSLE of 0.4745, offering superior predictive accuracy.

So, The Ridge Regression model excels in price prediction, proving valuable for online sellers.


This summary provides key findings from the project and highlights the performance of machine learning models.


