# Cloud-Native Client Segmentation Pipeline

## 📌 Project Overview
This project transforms a local Python-based machine learning script into a scalable, cloud-native analytics pipeline on Google Cloud Platform (GCP). It utilizes K-Means clustering to segment bank customers based on their financial behavior, engagement levels, and demographics, ultimately identifying high-risk churn candidates and high-value loyalists.

By migrating the processing to GCP, the project bridges the gap between raw data science models and business intelligence, providing automated insights through an interactive dashboard.

## 🏗️ Architecture & Tech Stack
This pipeline leverages modern data stack principles, moving from local execution to a robust cloud environment:

* **Compute & Orchestration:** Google Colab (Python, `pandas`, `scikit-learn`)
* **Data Warehousing:** Google BigQuery
* **Business Intelligence & Visualization:** Looker Studio

### The Workflow:
1.  **Data Ingestion & Preprocessing:** Raw Kaggle dataset is processed in a Google Colab notebook.
2.  **Feature Engineering & Scaling:** Applying `StandardScaler` to normalize features (Balance, Age, Tenure, etc.).
3.  **Clustering (K-Means):** Optimal K is determined via the Elbow Method and Silhouette Scores. Clients are assigned to distinct personas (e.g., *High-Value At-Risk*, *Young Engaged Growers*).
4.  **Cloud Storage:** The final segmented dataset is pushed directly to a Google BigQuery table using the `google-cloud-bigquery` library.
5.  **Interactive Dashboarding:** Looker Studio connects natively to BigQuery to visualize segment KPIs, churn rates, and PCA scatter plots dynamically.

## 📊 Business Impact & Personas
The K-Means algorithm identified 4 actionable customer segments, allowing for targeted retention and growth strategies:

1.  **High-Value At-Risk:** High account balances but low engagement. Prime candidates for personalized wealth management outreach.
2.  **Young Engaged Growers:** High activity, younger demographic. Ideal for multi-product upselling (e.g., credit cards, auto loans).
3.  **Senior Loyal Clients:** Long tenure, older demographic. Focus on retirement planning and wealth preservation.
4.  **Active Mid-Tier Clients:** Consistent users with average balances. Focus on incremental volume growth.

## 📂 Repository Structure
```text
├── data/
│   └── churn_data.csv                  # Raw dataset (Git ignored)
├── notebooks/
│   └── GCP_Segmentation_Pipeline.ipynb # Google Colab notebook for ML & BigQuery upload
├── src/
│   └── client_segmentation.py          # Original local execution script
└── README.md
