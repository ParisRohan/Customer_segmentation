# Customer_segmentation
An Unsupervised learning model built for customer segmentation using RFM modelling and K-Means clustering algorithm. The model is built on Online retail store dataset from UCI ML repository.

# Workflow

## 1. Data Collection and Description
* The dataset is available on UCI Machine Learning Repository :- https://archive.ics.uci.edu/ml/datasets/Online+Retail
* The dataset contains data about the transactions occuring between 01/12/2010 and 09/12/2011 for a UK based online gift store.
* The dataset contains 1067371 rows and 8 columns
* Identifiers:
  * InvoiceNo: Invoice number. A 6-digit integral number uniquely assigned to each transaction. Code starting with 'C' indicate cancellation.
  * StockCode: Product (item) code. A 5-digit integral number uniquely assigned to each distinct product.
  * CustomerID: Customer number. A 5-digit integral number uniquely assigned to each customer.
* Categorical Data:
  * Country: Country name. The name of the country where each customer resides.
  * Description: Product (item) name.
* Numeric Data:
  * InvoiceDate: Invice Date and time. The day and time when each transaction was generated.
  * Quantity: The quantities of each product (item) per transaction.
  * UnitPrice: Unit price. Product price per unit in sterling.

## 2. Data Cleaning
* 91% of the available customers belong to the United Kingdom -> So we have only selected the customers from UK for our analysis
* 240029 of the transactions records are not having a Customer ID -> These records have been dropped
* Drop the records where the 'Price' feature is either 0 or a null value
* 16005 records are cancelled transactions as their Invoice Number starts with a 'C' -> These records also contain negative values in the 'Quantity' feature -> These records have been dropped
* A new feature named 'TotalPrice' is created by multiplying 'Quantity' and 'Price' feature

## 3. RFM Modelling
* 'Recency' is calculated by subtracting today_date - the last day the customer made a purchase
* 'Frequency' is calculated by getting the unique count of Invoices
* 'Monetary' value is calculated by getting the sum of totalprice
* Split the newly created features into quantiles and then created R, F and M scores

## 4. Data Preprocessing
* Transform 'Recency', 'Frequency' and 'Monetary' features using Log Transformation
* Apply StandardScaler on the transformed features

## 5. K-Means Clustering
* The value of 'K' is found out using Elbow method
* Create and apply the K-Means model on the dataset





