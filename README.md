# AI-Based Predictive Maintenance System

**Portfolio maintainer: Arpit Gupta | M.Tech Computer Science and Engineering**

![Python](https://img.shields.io/badge/Python-3.10-3776AB?logo=python&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-F7931E?logo=scikitlearn&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-Dashboard-FF4B4B?logo=streamlit&logoColor=white)

## Overview

A supervised machine learning application that estimates the risk of CNC machine failure from operating parameters and presents the results through an interactive Streamlit dashboard. The application combines a binary classification model with rule-based maintenance suggestions.

This portfolio project is based on an existing open-source implementation. My focus is on understanding the ML workflow, reproducing the application locally, and improving its evaluation.

## Features

- Interactive input form for six machine operating parameters.
- Machine health classification and estimated failure probability using XGBoost.
- Comparison of multiple supervised classification algorithms.
- Rule-based identification of possible failure factors and maintenance suggestions.
- Visualization of predicted machine health and model evaluation results.

## Dataset

The project uses the AI4I 2020 Predictive Maintenance dataset, a synthetic dataset designed to represent industrial machine operating conditions. The local project includes `predictive_maintenance.csv`.

[Dataset source (Kaggle)](https://www.kaggle.com/datasets/stephanmatzka/predictive-maintenance-dataset-ai4i-2020)

| Input feature | Unit / values |
| --- | --- |
| Machine type | L, M, H |
| Air temperature | Kelvin |
| Process temperature | Kelvin |
| Rotational speed | RPM |
| Torque | Nm |
| Tool wear | Minutes |

Target: `0` = no failure; `1` = failure.

## Machine Learning Workflow

1. Load the CSV and remove identifier columns.
2. Encode categorical features and scale numerical features.
3. Split data into training and testing sets (80:20 in the existing implementation).
4. Train and compare classification models.
5. Evaluate using accuracy, precision, recall, F1-score and ROC-AUC.
6. Use XGBoost to generate predictions in the dashboard and apply rule-based suggestions.

The inherited training pipeline includes Logistic Regression, Decision Tree, Random Forest, KNN, SVM, Naive Bayes, AdaBoost, Gradient Boosting, XGBoost and LightGBM.

## Technology Stack

Python, Pandas, NumPy, Scikit-learn, XGBoost, LightGBM, Matplotlib and Streamlit.

## Project Structure

```text
app.py                      # Streamlit interface and prediction display
model.py                    # Data preprocessing and model training
predictive_maintenance.csv  # Dataset
requirements.txt            # Python dependencies
pictures/                   # Original project screenshots
LICENSE                     # Original license
README.md                   # Project documentation
```

## Installation and Execution

Open the project folder containing `app.py` in VS Code. In a Windows PowerShell terminal, set up an environment if you do not already have one:

```powershell
python -m venv "$env:USERPROFILE\mlenv"
& "$env:USERPROFILE\mlenv\Scripts\python.exe" -m pip install -r requirements.txt
```

Ensure `predictive_maintenance.csv` is in the project root. To launch the application using the existing environment:

```powershell
& "$env:USERPROFILE\mlenv\Scripts\python.exe" -m streamlit run app.py
```

Open <http://localhost:8501> in a browser. Keep the terminal running and press `Ctrl+C` to stop the server.

The application initializes model training at startup; a separate training command is not needed for normal use.

## My Contributions — Arpit Gupta

- Configured a local Python 3.10 environment and installed the project dependencies.
- Resolved environment setup issues and reproduced the Streamlit application locally.
- Ran the training pipeline and inspected the training logs, including the six input features and class imbalance among 8,000 training samples.
- Reorganized the project documentation with reproducible Windows launch instructions.

## Limitations and Planned Improvements

- The training data is imbalanced; accuracy alone is not sufficient to evaluate failure detection.
- Fit preprocessing transformations on training data only to reduce data leakage risk, and verify consistent feature encoding at inference.
- Add a confusion matrix and compare minority-class recall and precision.
- Validate model performance before reporting any accuracy score as a personal result.
- Maintenance suggestions are educational, not validated industrial safety recommendations.

