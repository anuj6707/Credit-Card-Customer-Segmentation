# Credit Card Customer Segmentation: K-Means, Hierarchical Clustering & DBSCAN

## Project Overview

This project explores customer segmentation using multiple unsupervised machine learning techniques on a credit card customer dataset.

The objective is to identify distinct customer groups based on credit behavior, transaction activity, and account characteristics to support personalized marketing, customer retention, and product recommendation strategies.

---

## Business Problem

Banks and financial institutions manage customers with varying spending habits, credit limits, and utilization patterns.

Understanding customer segments can help answer questions such as:

- Which customers generate the highest value?
- Which customers are underutilizing available credit?
- Which customers should receive premium products?
- How can retention and engagement strategies be improved?

---

## Dataset Description

The dataset contains customer demographic, account, and transaction information including:

- Customer Age
- Dependent Count
- Months on Book
- Total Relationship Count
- Months Inactive (Last 12 Months)
- Contacts Count (Last 12 Months)
- Credit Limit
- Total Revolving Balance
- Total Transaction Amount
- Total Transaction Count
- Average Utilization Ratio

---

## Data Preprocessing

### Data Cleaning

The following columns were removed:

- CLIENTNUM
- Naive Bayes prediction columns

These variables do not contribute meaningful information for clustering.

### Feature Selection

Selected features:

```python
features = [
    "Customer_Age",
    "Dependent_count",
    "Months_on_book",
    "Total_Relationship_Count",
    "Months_Inactive_12_mon",
    "Contacts_Count_12_mon",
    "Credit_Limit",
    "Total_Revolving_Bal",
    "Total_Trans_Amt",
    "Total_Trans_Ct",
    "Avg_Utilization_Ratio"
]
```

### Feature Scaling

Since clustering algorithms are distance-based, all numerical variables were standardized using:

```python
StandardScaler()
```

---

# K-Means Clustering

## Methodology

K-Means clustering was used to partition customers into distinct groups based on behavioral and financial characteristics.

### Silhouette Score Analysis

| K | Silhouette Score |
|---|---|
| 2 | 0.758 |
| 3 | 0.698 |
| 4 | 0.671 |
| 5 | 0.649 |
| 6 | 0.633 |
| 7 | 0.624 |
| 8 | 0.620 |

The results indicate strong cluster separation.

For business interpretability, K=3 was selected.

---

## K-Means Results

### Cluster 1 — Standard Customers

- Customer Count: ~7000
- Lower credit limits
- Higher credit utilization
- Moderate transaction activity

### Cluster 2 — Premium Customers

- Customer Count: ~2000
- Higher credit limits
- Strong transaction activity
- Low utilization ratio

### Cluster 3 — Elite Customers

- Customer Count: ~1000
- Highest credit limits
- Highest transaction volume
- Lowest utilization ratio

---

# Hierarchical Clustering

## Methodology

Agglomerative Hierarchical Clustering was applied to identify customer groups through a bottom-up clustering approach.

A dendrogram was used to visualize cluster formation and merging behavior.

### Silhouette Score Analysis

| K | Silhouette Score |
|---|---|
| 2 | 0.761 |
| 3 | 0.654 |
| 4 | 0.666 |
| 5 | 0.645 |
| 6 | 0.604 |

Hierarchical clustering produced customer segments very similar to K-Means, suggesting stable cluster structures within the dataset.

---

## Hierarchical Clustering Results

### Standard Customers

- Lower credit limits
- Higher utilization rates
- Largest customer segment

### Premium Customers

- Higher transaction activity
- Moderate utilization
- Strong purchasing power

### Elite Customers

- Highest credit limits
- Highest transaction amounts
- Lowest utilization ratios

---

# DBSCAN Clustering

## Methodology

DBSCAN was evaluated as a density-based clustering algorithm.

Parameters explored:

- eps
- min_samples

### Observations

DBSCAN was unable to identify meaningful density-separated customer groups within this dataset.

The algorithm frequently produced:

- A single dominant cluster
- Excessive noise points
- Poor cluster separation

As a result, silhouette score evaluation was not meaningful.

---

## DBSCAN Conclusion

The customer segments in this dataset appear to be compact and well-suited to centroid-based and hierarchical clustering methods.

This highlights an important machine learning insight:

> Different clustering algorithms perform best on different data structures.

While K-Means and Hierarchical Clustering successfully identified meaningful customer segments, DBSCAN struggled because the dataset lacked strong density-separated regions.

---

# Key Business Insights

Three primary customer groups emerged:

## Standard Customers

- Lower credit limits
- Higher credit utilization
- Largest customer base

### Business Opportunity

- Credit limit increases
- Cashback incentives
- Usage-based rewards

---

## Premium Customers

- Higher spending behavior
- Low utilization
- Healthy credit management

### Business Opportunity

- Premium card upgrades
- Travel benefits
- Personalized promotions

---

## Elite Customers

- Highest transaction activity
- Highest credit limits
- Lowest utilization rates

### Business Opportunity

- VIP loyalty programs
- Wealth management services
- Retention-focused marketing

---

# Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn
- SciPy

---

# Machine Learning Concepts Demonstrated

- Unsupervised Learning
- K-Means Clustering
- Hierarchical Clustering
- DBSCAN
- Customer Segmentation
- Feature Engineering
- Feature Scaling
- Elbow Method
- Silhouette Score Analysis
- Dendrogram Analysis
- Cluster Interpretation

---

# Conclusion

This project compared three clustering techniques for customer segmentation in the banking domain.

Key findings:

- K-Means and Hierarchical Clustering consistently identified meaningful customer segments.
- Customer groups differed significantly in credit limits, transaction behavior, and utilization patterns.
- DBSCAN was less effective due to the compact structure of the dataset.
- Elite and Premium customer groups present strong opportunities for personalized marketing and retention strategies.

The project demonstrates how unsupervised learning can transform customer transaction data into actionable business intelligence.
