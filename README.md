SCI-ICU Length of Stay Modeling:

This project implements a full machine learning pipeline to predict ICU Length of Stay (LOS) for patients with spinal cord injuries (SCI), using a real-world clinical dataset. The project combines exploratory data analysis (EDA), SQL-based data wrangling, unsupervised PCA clustering, and both niche and general-purpose regression models.

Overview:

The application showcases:

Structured data extraction and transformation using PostgreSQL and Python

Clinical data exploration and visualization for ICU patient populations

Dimensionality reduction via Principal Component Analysis (PCA)

KMeans clustering to uncover latent patient phenotypes

Niche ML models trained per cluster for precision prediction

A general regression model trained across all patient groups for benchmarking

Custom metrics and evaluation logic (RMSE, MAE, MedAE, R², MAPE)

Key Components:

SQL Data Ingestion:

PostgreSQL queries to extract ICU and hospital-level data

Merging and joining across schema boundaries

Exported to CSV for downstream preprocessing

Exploratory Data Analysis (EDA):

Distribution plots of LOS, age, and comorbidities

Group-wise mortality and diagnostic pattern analysis

Feature correlation matrices and log-transformed target variable inspection

Outlier and skewness analysis

PCA + Clustering:

Standard scaling and KNN/Simple imputation

Principal Component Analysis to reduce multicollinearity and identify trends

KMeans clustering with Silhouette Score optimization

Kruskal-Wallis tests to assess LOS variance across clusters

Cluster-specific summary statistics and visualizations

Niche ML Models (per cluster):

GroupKFold-safe modeling pipelines

Ridge, LightGBM, CatBoost, and XGBoost regressors

Hyperparameter tuning and cluster-specific feature importance

Evaluation using R², MAE, RMSE, MedAE

General ML Model:

Trained on all patients using consistent feature pipelines

Compared against niche models to assess gains from segmentation

Model interpretability planned via SHAP (in progress)

Evaluation Metrics:

Custom metric functions for MAE, RMSE, R², MedAE

Feature engineering and z-score normalization for numeric features

Label encoding for categorical variables

File Structure:

data/
raw_data.csv : Extracted clinical data
processed_data.csv : Cleaned and imputed dataset
clustered_data.csv : Cluster-assigned data with PCA components

notebooks/
01_SQL_Extraction.ipynb : PostgreSQL data wrangling and export
02_EDA.ipynb : Exploratory Data Analysis
03_PCA_Clustering.ipynb : Dimensionality reduction and clustering
04_Niche_Modeling.ipynb : Per-cluster regression pipelines
05_General_Model.ipynb : Unified model across patient populations

scripts/
utils.py : Helper functions for metrics and visualization
models.py : Wrapper functions for training regressors
preprocessing.py : Data cleaning and feature engineering

requirements.txt : Python dependencies
README.md : Project documentation (this file)

Setup Instructions:

Clone the repository:

git clone https://github.com/Stefanjafry/SCI-ICU-LengthOfStay-Modeling.git
cd SCI-ICU-LengthOfStay-Modeling

(Optional) Create and activate a virtual environment:

python -m venv .venv
On Windows: .venv\Scripts\activate
On Mac/Linux: source .venv/bin/activate

Install dependencies:

pip install -r requirements.txt

Running the Project:

To explore and run each phase of the pipeline, open the appropriate Jupyter notebooks in sequence:

Start with 01_SQL_Extraction.ipynb if replicating the data ingestion

Proceed to EDA, PCA clustering, and then modeling notebooks

License:

This project is licensed under the MIT License. You are free to use, modify, and distribute the code.
