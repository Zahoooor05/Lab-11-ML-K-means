# Credit Card Customer Segmentation using K-Means

## Overview
This project uses the K-Means clustering algorithm to segment credit card customers based on their credit card usage behavior. Since the dataset does not contain predefined labels, this is an unsupervised learning problem. The goal is to identify customer groups that can help businesses improve marketing and customer management strategies.

---

## Dataset

**Dataset:** CC_GENERAL.csv

The dataset contains information about credit card customers, including:

- BALANCE
- PURCHASES
- ONEOFF_PURCHASES
- INSTALLMENTS_PURCHASES
- CASH_ADVANCE
- PURCHASES_FREQUENCY
- CASH_ADVANCE_FREQUENCY
- CREDIT_LIMIT
- PAYMENTS
- MINIMUM_PAYMENTS
- TENURE

Each row represents one credit card customer.

---

## Data Preprocessing

### Remove Identifier Column
The `CUST_ID` column was removed because it is only an identification field and does not describe customer behavior.

### Handle Missing Values
Missing values were found in:

- CREDIT_LIMIT
- MINIMUM_PAYMENTS

Mean imputation was used to replace missing values.

### Feature Scaling
StandardScaler was applied to standardize all features before clustering because K-Means is a distance-based algorithm.

---

## Exploratory Data Analysis

The following visualizations were created:

- Histograms for numerical features
- Correlation heatmap
- BALANCE vs PURCHASES scatter plot
- BALANCE vs CASH_ADVANCE scatter plot

These visualizations helped understand customer spending behavior and feature relationships.

---

## Choosing the Number of Clusters

### Elbow Method
The Elbow Method was used by calculating inertia values for K values from 1 to 10.

### Silhouette Score
Silhouette scores were calculated for K values from 2 to 10.

| K | Silhouette Score |
|---|------------------|
| 2 | 0.210 |
| 3 | 0.251 |
| 4 | 0.198 |
| 5 | 0.193 |
| 6 | 0.203 |
| 7 | 0.215 |
| 8 | 0.208 |
| 9 | 0.215 |
| 10 | 0.221 |

Although K = 3 had the highest silhouette score, K = 4 was selected because it provided more meaningful customer segments while maintaining reasonable clustering quality.

---

## K-Means Clustering

Final model configuration:

```python
KMeans(
    n_clusters=4,
    random_state=42,
    n_init=10
)
```

Cluster labels were added to the dataset in a new column named `Cluster`.

---

## Cluster Summary

| Cluster | Number of Customers |
|----------|-------------------|
| 0 | 3367 |
| 1 | 409 |
| 2 | 1198 |
| 3 | 3976 |

### Cluster 0
- Moderate balance
- Moderate purchases
- Regular customers

### Cluster 1
- Highest purchases
- High balances
- Premium or high-value customers

### Cluster 2
- High balances
- Lower purchases
- Customers likely relying on cash advances

### Cluster 3
- Low spending
- Lower balances
- Low-activity customers

---

## PCA Visualization

Principal Component Analysis (PCA) was used to reduce the dataset to two dimensions for visualization purposes.

This provided a simplified 2D view of the customer segments while preserving important information from the original dataset.

---

## Key Findings

- Four meaningful customer segments were identified.
- Cluster 1 represents high-value customers with high spending behavior.
- Cluster 2 contains customers with high balances but lower purchasing activity.
- Cluster 3 consists of low-activity customers.
- Customer segmentation can help businesses better understand customer behavior and spending patterns.

---

## Business Applications

The identified customer segments can be used for:

- Personalized marketing campaigns
- Customer retention programs
- Loyalty rewards
- Product recommendations
- Credit risk analysis
- Customer relationship management

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn

---

## Conclusion

This project successfully applied K-Means clustering to segment credit card customers based on their usage behavior. Through data preprocessing, feature scaling, cluster evaluation, and visualization, four meaningful customer groups were identified. These segments can support data-driven business decisions and targeted marketing strategies.
