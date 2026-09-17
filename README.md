# Online Retail Data Cleaning, Visualization & Predictive Modeling

## Project Overview

This project focuses on cleaning, processing, analyzing, and visualizing a real-world Online Retail dataset.

The objective is to demonstrate how raw transactional data can be transformed into a clean dataset and meaningful business insights using Python.

## Objectives

- Identify and handle missing values
- Detect and remove duplicate records
- Identify cancelled transactions
- Handle invalid price values
- Detect and treat numerical outliers
- Create new analytical features
- Perform exploratory data analysis
- Create meaningful data visualizations
- Extract useful business insights

## Dataset

The project uses the Online Retail dataset provided by the UCI Machine Learning Repository.

The dataset contains online retail transactions with information such as:

- Invoice Number
- Stock Code
- Product Description
- Quantity
- Invoice Date
- Unit Price
- Customer ID
- Country

Dataset Source:

UCI Machine Learning Repository - Online Retail Dataset

https://archive.ics.uci.edu/dataset/352/online+retail

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

## Data Cleaning Process

### 1. Missing Values

Missing product descriptions were replaced with "Unknown".

CustomerID contains missing values because customer identification was not available for some transactions. These rows were retained because CustomerID was not required for overall sales analysis.

### 2. Duplicate Records

Duplicate transaction records were identified and removed.

### 3. Cancelled Transactions

Transactions with invoice numbers beginning with "C" were treated as cancelled transactions and removed from completed-sales analysis.

### 4. Invalid Prices

Transactions with UnitPrice less than or equal to zero were removed.

### 5. Outlier Detection

The Interquartile Range (IQR) method was used to identify potential outliers in Quantity and UnitPrice.

Extreme values were capped using the calculated IQR boundaries rather than removing the corresponding transactions.

### 6. Feature Engineering

A TotalSales column was created:

TotalSales = Quantity × UnitPrice

## Visualizations

The project includes the following visualizations:

1. Missing Values by Column
2. Quantity and Unit Price Outlier Box Plots
3. Top 10 Countries by Revenue
4. Monthly Revenue Trend
5. Top 10 Products by Revenue
6. Quantity Distribution
7. Top 10 Products by Quantity Sold
8. Correlation Heatmap

## Key Findings

- The United Kingdom generated the highest revenue among the countries analyzed.
- November recorded the highest monthly revenue in the analyzed period.
- A small number of products contributed significantly to total revenue.
- Most transactions contain relatively small order quantities.
- Extreme values were identified in both Quantity and UnitPrice.
- Data cleaning improved the consistency and reliability of the dataset for analysis.

## Project Structure

```text
Data-Cleaning-Visualization/
│
├── data/
│   └── Online Retail.xlsx
│
├── notebook/
│   └── Data_Cleaning_Visualization.ipynb
│
├── output/
│   └── cleaned_online_retail.csv
│
├── visualizations/
│   ├── missing_values.png
│   ├── outlier_boxplots.png
│   ├── top_10_countries_revenue.png
│   ├── monthly_revenue_trend.png
│   ├── top_10_products_revenue.png
│   ├── quantity_distribution.png
│   ├── top_10_products_quantity.png
│   └── correlation_heatmap.png
│
└── README.md
# Week 2: Predictive Modeling Using Machine Learning

## Objective

The second phase of this project extends the cleaned Online Retail dataset by applying supervised machine learning techniques.

The objective is to classify transactions as normal-value or high-value transactions.

## Machine Learning Approach

A binary target variable named `HighValue` was created using the median transaction sales value.

- `1` = High-value transaction
- `0` = Normal-value transaction

The dataset was divided into:

- 80% training data
- 20% testing data

Stratified sampling was used to maintain the class distribution.

## Models Used

### Decision Tree Classifier

A Decision Tree classifier was trained with a maximum depth of 10 to control model complexity and reduce overfitting.

### Random Forest Classifier

A Random Forest classifier using 100 decision trees was trained for comparison.

## Model Performance

| Model | Accuracy | AUC |
|---|---:|---:|
| Decision Tree | 94% | 0.99 |
| Random Forest | 92% | 0.98 |

The Decision Tree performed slightly better than the Random Forest in this experiment.

## Evaluation Methods

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix
- ROC Curve
- AUC

## Machine Learning Visualizations

The following visualizations were created:

- Decision Tree Confusion Matrix
- Random Forest Confusion Matrix
- Model Performance Comparison
- ROC Curve Comparison
- Feature Importance

## Feature Importance

The most important features for the Decision Tree were:

1. Quantity
2. UnitPrice
3. Country
4. Month

Quantity and UnitPrice had substantially higher importance than the categorical features.

## Limitation

The `HighValue` target was derived from `TotalSales`, while `TotalSales` is calculated from Quantity and UnitPrice.

Therefore, Quantity and UnitPrice naturally have strong predictive power. The machine learning component is intended to demonstrate supervised learning, preprocessing, model training, and evaluation rather than serve as a production-ready future prediction system.
## Week 3 – Exploratory Data Analysis

### Objective

The objective of this week was to analyze the cleaned Online Retail dataset and identify meaningful patterns, relationships, and trends.

### EDA Performed

- Statistical summary
- Sales distribution analysis
- Quantity distribution analysis
- Correlation analysis
- Country-wise revenue analysis
- Product-wise revenue analysis
- Customer revenue analysis
- Monthly transaction analysis
- Identification of key influencing factors

### Key Insights

- Most transactions have relatively low sales values.
- Sales distribution is right-skewed.
- Quantity has a moderate positive relationship with TotalSales.
- UnitPrice has a weaker positive relationship with TotalSales.
- The United Kingdom generates the highest revenue.
- REGENCY CAKESTAND 3 TIER is the highest-revenue product.
- Customer 14911 has the highest revenue among the top customers analyzed.
- November has the highest transaction volume in the analyzed period.

### EDA Visualizations

The project includes visualizations for:

1. Sales distribution
2. Quantity distribution
3. Correlation heatmap
4. Country-wise revenue
5. Product-wise revenue
6. Top customers by revenue
7. Monthly transaction volume

### Tools Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook