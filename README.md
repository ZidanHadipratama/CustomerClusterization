# Customer Segmentation Analysis

## Overview
This notebook performs customer segmentation analysis using clustering techniques to group customers based on demographics and purchasing behavior. The goal is to identify distinct customer segments that can inform targeted marketing strategies, improve customer engagement, and optimize resource allocation.

---

## Dataset
The dataset contains **2,240 customer records** with features including:
- **Demographics**: Age, Income, Education, Marital Status, Children.
- **Purchasing Behavior**: Spending on product categories (Wines, Fruits, Meat, etc.), purchase channels (Web, Store, Catalog).
- **Engagement Metrics**: Recency, Tenure (`Customer_For`), Campaign Responses, Complaints.

**Source**: [Customer Segmentation Dataset on Kaggle](https://www.kaggle.com/datasets/7508845/customer-segmentation).

---

## Workflow
1. **Data Preprocessing**:
   - Imputed missing `Income` values.
   - Engineered features: `Age`, `Spent` (total spending), `Customer_For` (tenure), `Children` (total kids).
   - Simplified categorical variables (e.g., grouped marital status into "Married," "Single," etc.).
   - Removed irrelevant columns (e.g., `ID`, `Z_CostContact`).

2. **Outlier Handling**:
   - Applied IQR capping to numerical features (e.g., `Income`, `Spent`) to reduce skewness.

3. **Dimensionality Reduction**:
   - Used **PCA** to reduce features to 2 principal components (explaining 98.6% of variance).

4. **Clustering**:
   - **K-Means**: Identified optimal clusters using the Elbow Method and Silhouette Score (optimal `k=4`).
   - Validated with Hierarchical Clustering and DBSCAN (for density-based outlier detection).

5. **Interpretation**:
   - Analyzed cluster characteristics (mean values, distributions).
   - Visualized clusters in PCA space.

---

## Key Findings
### Cluster 0: **Occasional, Young Families on a Budget**
- **Demographics**: Moderate age (\~53 years), highest number of children, low income (\~$35K/year).
- **Behavior**: Minimal engagement (lowest purchase frequency), negligible campaign response.
- **Spending**: Focused on essentials (meat, wine) with the lowest total spend (~$116/customer).
- **Strategy**: Target with price incentives or family-oriented promotions.

### Cluster 1: **Premium, Digital-First Empty-Nest Households**
- **Demographics**: Older (\~57 years), high income (\~$69K/year), few children.
- **Behavior**: Highest digital engagement, frequent purchases, strong campaign response (~25% acceptance).
- **Spending**: Top spenders (~$1,166/customer), especially on premium products (wine, meat, gold).
- **Strategy**: Offer exclusive loyalty programs and premium deals.

### Cluster 2: **Value-Conscious, Moderately Active Families**
- **Demographics**: Similar to Cluster 0 but slightly higher income (~$34K/year).
- **Behavior**: Moderate purchase frequency, minimal campaign interest.
- **Spending**: Mid-low spend (~$209/customer), slightly more diversified.
- **Strategy**: Promote value bundles or bulk discounts.

### Cluster 3: **Established, Multi-Channel Affluent Customers**
- **Demographics**: High income (\~$70K/year), older (\~57 years), few young children.
- **Behavior**: Omni-channel shoppers, moderate campaign response.
- **Spending**: High spend (~$975/customer) across all categories, including premium products.
- **Strategy**: Focus on cross-channel loyalty programs.

---

## Business Impact
- **Cluster 1 & 3**: Prioritize for high-margin campaigns and personalized recommendations.
- **Cluster 2**: Encourage upselling with targeted promotions.
- **Cluster 0**: Re-engage with introductory offers or subscription models.

---
