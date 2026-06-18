# Credit Card Customer Segmentation using Clustering Algorithms

## Overview

This project applies multiple unsupervised machine learning techniques to segment credit card customers based on their financial behavior, transaction activity, and credit utilization patterns.

The goal is to identify meaningful customer groups that can support targeted marketing, customer retention, premium product recommendations, and business decision-making.

---

## Business Problem

Financial institutions manage customers with different spending habits, credit limits, and transaction behaviors.

Customer segmentation helps answer questions such as:

* Which customers generate the most value?
* Which customers are underutilizing their available credit?
* Which customers should receive premium offers?
* How can retention and engagement strategies be personalized?

---

## Dataset Features

The dataset contains customer demographic and financial information including:

* Customer Age
* Dependent Count
* Months on Book
* Total Relationship Count
* Months Inactive (Last 12 Months)
* Contacts Count (Last 12 Months)
* Credit Limit
* Total Revolving Balance
* Total Transaction Amount
* Total Transaction Count
* Average Utilization Ratio

---

## Data Preprocessing

### Data Cleaning

Removed:

* CLIENTNUM (Customer Identifier)
* Naive Bayes prediction columns

These variables do not provide useful information for clustering.

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

Since clustering algorithms rely on distance calculations, all numerical variables were standardized using:

```python
StandardScaler()
```

---

# K-Means Clustering

## Silhouette Score Analysis

| K | Silhouette Score |
| - | ---------------- |
| 2 | 0.758            |
| 3 | 0.698            |
| 4 | 0.671            |
| 5 | 0.649            |
| 6 | 0.633            |
| 7 | 0.624            |
| 8 | 0.620            |

The silhouette scores indicate strong cluster separation.

For business interpretability, K = 3 was selected.

---

## K-Means Customer Segments

### Standard Customers

* Lower credit limits
* Higher utilization ratios
* Moderate transaction activity
* Largest customer segment

### Premium Customers

* Higher credit limits
* Strong transaction activity
* Lower utilization ratios

### Elite Customers

* Highest credit limits
* Highest transaction amounts
* Lowest utilization ratios

---

# Hierarchical Clustering

## Methodology

Agglomerative Hierarchical Clustering was applied to identify customer groups using a bottom-up clustering approach.

A dendrogram was used to visualize cluster formation and merging behavior.

## Silhouette Score Analysis

| K | Silhouette Score |
| - | ---------------- |
| 2 | 0.761            |
| 3 | 0.654            |
| 4 | 0.666            |
| 5 | 0.645            |
| 6 | 0.604            |

Hierarchical Clustering produced segments similar to K-Means, indicating a stable underlying customer structure.

---

## Hierarchical Clustering Results

### Cluster 0 – Standard Customers

* Customer Count: 8,111
* Credit Limit ≈ 4.7K
* Transaction Amount ≈ 4.1K
* Utilization Ratio ≈ 0.33

### Cluster 1 – Premium Customers

* Customer Count: 1,164
* Credit Limit ≈ 18.6K
* Transaction Amount ≈ 5.4K
* Utilization Ratio ≈ 0.06

### Cluster 2 – Elite Customers

* Customer Count: 852
* Credit Limit ≈ 32.6K
* Transaction Amount ≈ 5.6K
* Utilization Ratio ≈ 0.04

---

# DBSCAN Clustering

## Methodology

DBSCAN (Density-Based Spatial Clustering of Applications with Noise) was evaluated to determine whether customer groups could be identified based on density.

Multiple values of:

* eps
* min_samples

were tested.

## Results

DBSCAN was unable to identify meaningful density-based customer groups.

Observed outcomes included:

* Single-cluster solutions
* All points classified as noise
* No meaningful density separation

Example:

```text
eps=0.3 → 0 clusters, 10000 noise points
eps=0.5 → 0 clusters, 10000 noise points
eps=1.0 → 0 clusters, 10000 noise points
```

### Interpretation

The customer groups in this dataset appear to be compact and better represented by centroid-based and hierarchical clustering methods rather than density-separated structures.

This demonstrates an important machine learning principle:

> Different clustering algorithms perform best on different types of data.

---

# Key Business Insights

### Standard Customers

Represent the majority of customers.

Characteristics:

* Lower credit limits
* Higher credit utilization
* Moderate transaction activity

Potential Actions:

* Credit limit upgrades
* Cashback incentives
* Usage-based reward programs

---

### Premium Customers

Characteristics:

* Strong spending activity
* Higher credit limits
* Responsible credit usage

Potential Actions:

* Premium card upgrades
* Travel rewards
* Personalized promotions

---

### Elite Customers

Characteristics:

* Highest transaction activity
* Highest credit limits
* Lowest utilization ratios

Potential Actions:

* VIP loyalty programs
* Wealth management products
* Retention-focused marketing strategies

---

# Algorithm Comparison

| Algorithm               | Result                                               |
| ----------------------- | ---------------------------------------------------- |
| K-Means                 | Successfully identified meaningful customer segments |
| Hierarchical Clustering | Produced similar and stable customer groups          |
| DBSCAN                  | Failed to identify meaningful density-based clusters |

---

# Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-Learn
* SciPy

---

# Machine Learning Concepts Demonstrated

* Unsupervised Learning
* Customer Segmentation
* K-Means Clustering
* Hierarchical Clustering
* DBSCAN
* Feature Scaling
* Dendrogram Analysis
* Silhouette Score Evaluation
* Cluster Interpretation
* Business Analytics

---

# Conclusion

This project compared three clustering algorithms for customer segmentation in the banking domain.

K-Means and Hierarchical Clustering consistently identified meaningful customer groups based on credit limits, transaction activity, and utilization behavior.

DBSCAN was unable to discover meaningful density-based clusters, suggesting that the dataset is better represented by partitioning and hierarchical approaches.

The analysis demonstrates how clustering techniques can transform customer transaction data into actionable business insights for marketing, retention, and customer relationship management.
