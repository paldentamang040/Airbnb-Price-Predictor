# Airbnb Price Prediction with MLflow

## Project Overview

This project predicts Airbnb listing prices using machine learning regression models.  
The workflow covers data loading, preprocessing, feature engineering, model training, model comparison, and experiment tracking with MLflow.

## Project Objectives

The objectives of this project are:

- Load and prepare Airbnb listing data for modeling.
- Clean missing values and engineer useful features.
- Train multiple regression models for price prediction.
- Evaluate model performance using MAE and R2.
- Track model experiments using MLflow.
- Compare runs to identify the best-performing model.
- Register the top model in the MLflow Model Registry.

## Dataset

The dataset contains Airbnb listing information such as:

- Listing and host identifiers
- Listing name and host name
- Neighbourhood and neighbourhood group
- Latitude and longitude
- Room type
- Minimum nights
- Number of reviews
- Review history
- Availability
- Price as the target variable

In this notebook, the dataset is loaded from Amazon S3 using `boto3`. [file:235]

## Preprocessing and Feature Engineering

The following steps were applied in the notebook:

- Checked missing values.
- Converted `last_review` into datetime.
- Extracted:
  - `reviewyear`
  - `reviewmonth`
  - `reviewday`
- Filled missing review-related values with `0`.
- Dropped the original `last_review` column.
- Removed price outliers using the IQR method.
- Applied one-hot encoding to:
  - `neighbourhood`
  - `neighbourhood_group`
  - `room_type`
- Dropped `name` and `host_name` before modeling. [file:235]

## Models Trained

The following models were trained and compared:

- Linear Regression
- RandomForestRegressor
- XGBoost Regressor [file:235]

## Evaluation Metrics

Model performance was evaluated using:

- Mean Absolute Error (MAE)
- R2 Score [file:235]

## Results

The notebook results show the following model comparison:

| Model | Train MAE | Train R2 | Test MAE | Test R2 |
|---|---:|---:|---:|---:|
| XGBoost [file:235] | 29.552 [file:235] | 0.638 [file:235] | 31.454 [file:235] | 0.587 [file:235] |
| RandomForestRegressor [file:235] | 11.667 [file:235] | 0.942 [file:235] | 31.440 [file:235] | 0.582 [file:235] |
| LinearRegression [file:235] | 33.957 [file:235] | 0.536 [file:235] | 34.257 [file:235] | 0.526 [file:235] |

Based on the highest test R2, **XGBoost** was selected as the best model. The notebook then registers the best model in MLflow under the name `AirbnbPricePredictor`. [file:235]

## MLflow Tracking

MLflow was used to:

- Create an experiment named `airbnb-price-prediction`.
- Log parameters for each model run.
- Log training and testing metrics.
- Save model artifacts.
- Compare model runs.
- Register the best model in the Model Registry. [file:235]

## Repository Structure

```text
project-folder/
│
├── main.ipynb
├── README.md
├── requirements.txt
├── .gitignore
├── mlruns/                 # generated locally by MLflow
└── data/                   # optional local data folder
```

## Workflow

The workflow used in this project is:

1. Load the dataset from S3.
2. Inspect missing values and data types.
3. Convert and engineer date-related features.
4. Handle missing values.
5. Remove price outliers.
6. Encode categorical features.
7. Drop unnecessary text columns.
8. Split data into training and testing sets.
9. Train Linear Regression, Random Forest, and XGBoost models.
10. Track all model runs in MLflow.
11. Compare run metrics.
12. Register the best model. [file:235]

## Setup Instructions

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd <your-repository-folder>
```

### 2. Create and activate a virtual environment

#### Windows
```bash
python -m venv .venv
.venv\Scripts\activate
```

#### macOS / Linux
```bash
python -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Launch Jupyter

```bash
jupyter notebook
```

Then open:

```text
main.ipynb
```

## Running MLflow

To launch the MLflow UI locally, run:

```bash
mlflow ui
```

Then open:

```text
http://127.0.0.1:5000
```

Your notebook currently uses a local file-based MLflow tracking URI, which stores runs inside the `mlruns` folder. [file:235]

## Screenshots

### MLflow Experiment Runs
[Insert screenshot of MLflow experiment runs here]

### MLflow Metrics Comparison
[Insert screenshot of MLflow metrics comparison here]

### MLflow Model Registry
[Insert screenshot of MLflow Model Registry showing `AirbnbPricePredictor` here]

## Key Insights and Observations

- Linear Regression provided the weakest baseline performance on the test set. [file:235]
- Random Forest achieved strong performance, but the large gap between training and testing metrics suggests stronger overfitting than XGBoost. [file:235]
- XGBoost achieved the best overall test R2 and was chosen as the final model. [file:235]
- MLflow made it easier to compare models consistently and store the final registered model. [file:235]

## Notes

- The notebook includes package installation commands for `boto3`, `pandas`, `xgboost`, and `mlflow`. [file:235]
- A `requirements.txt` file was generated in the notebook using `pip freeze`. [file:235]
- For security, AWS credentials should not be committed to the repository and should be moved to environment variables or a secure secret manager. [file:235]