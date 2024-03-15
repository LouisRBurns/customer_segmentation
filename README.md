# Customer Segmentation Analysis
This data was from Laurie's Books' inventory system in Oregon City, OR. The system started recording transactions in September 2023, and this data covers through February 2024. There are around 900 unique customers across 6000 individual inventory changes. The original sales data, including customer names, has been omitted. The clean exported data is included. 
### 1. Laurie's Preprocessing Customers
This notebook consists of exploring and cleaning the dataset. Steps include removing rows where there is a placeholder customer name, removing unused columns, converting data types, anonymizing customer names, and exporting the result as `transactions_cleaned.csv.` 
### 2. Laurie's Cohort Analysis
In this notebook, we wrangle dates and orders to get first and last purchases, total transactions, and total spending. We develop these into Recency, Frequency, Monetary Value (RFM), and Tenure. We assign quartile values and label aggregated observations as gold, silver, and bronze. We export `lauries_general_segments.csv` and `customers_for_clustering.csv.` 

![General Segments](https://github.com/LouisRBurns/customer_segmentation/blob/main/general_segments.png)
### 3. Laurie's Customer Clustering
Using RFM, we use the k-means unsupervised machine learning algorithm for clustering. Because some of the data cannot be adequately transformed to approximately normal, we run models with and without the non-normalized data to see which model performs better according to the elbow method and the silhouette coefficients. We find four clusters using two features to be the best. 
![Customer Clusters](https://github.com/LouisRBurns/customer_segmentation/blob/main/customer_clusters.png)

The clusters break down into a 2x2 matrix between higher or lower spending and more or less recent purchases. The breaks appear to be around $50 total spending and 50 days since the last purchase. We export the cluster labels as `customer_clusters.csv.` 
### 4. Laurie's Deanonymization
All of the previously exported data is rejoined for an aggregated list of customer segments. The final export is `customer_segments_final.csv`, which is not included here. 
### Discussion
While this store has been in the community for 42 years, tracking transactions only began in September 2023. This followed a relocation about a half mile away. Remodeling and inventory entry were ongoing throughout the observation period. 

Around 20% of the transactions did not have a unique customer name attached and were discarded. These would be included in a market basket analysis and grouped by order number, assuming that each of those orders was a one-time customer. 

Given the short timeframe, many of the best customers in the top segment could have been observed from a basic top spending report. Once the store is at full inventory capacity, it would make sense to run this analysis again after a full year has passed. 
