# Distributed System Failure Analysis using Machine Learning
This project explores the application of Machine Learning (ML) to predict system failures and identify root causes within distributed system architectures. It was developed as part of the Application of Data Science (Assignment #2) course.

# 👥 Authors
Bilal Ahmed

# 📌 Project Overview
The study analyzes how different distributed system architectures (Monolithic, Microservices, Event-Driven, etc.) behave under various stress conditions. Using a dataset of 200,000 system snapshots, we developed models to categorize system health and provide actionable insights for Site Reliability Engineering (SRE).

# 🎯 Objectives
Predict System States: Classify health as Healthy, Degraded, Cascading Failure, or Total Outage.
Root Cause Analysis: Identify specific triggers like CPU saturation or network partitions.
Model Benchmarking: Compare the effectiveness of Logistic Regression, Random Forest, and Linear SVM.

# 📊 Methodology
Data Preprocessing
To prepare the raw performance metrics for analysis, we implemented a robust pipeline:
Encoding: Categorical variables (Architecture, Deployment, Communication) were processed using OneHotEncoder.
Scaling: Numerical metrics were normalized via StandardScaler.

# 📈 Model Performance
We evaluated our models using standard classification metrics:
Model,                Accuracy,  Precision,  Recall,  F1-Score
Random Forest,          99.99%,    1.00,      1.00,    1.00
Logistic Regression,    98.80%,    0.99,      0.99,     0.99
Linear SVM,              98.57%,    0.99,      0.99,      0.99
Key Finding: The Random Forest Classifier is the superior model for this task, successfully capturing non-linear dependencies between tail latency and error rates.
tratification: Used an 80/20 train-test split with stratification to preserve the representation of rare failure events (e.g., Total Outages).

# 🔍 Key Insights (Root Cause Analysis)
The top 5 predictors for system failure identified by the model are:
p95_latency_ms (0.2366): The primary signal for impending crashes.
error_rate_percent (0.1803): Direct evidence of service distress.
requests_per_second (0.1146): The primary external stress driver
retry_storm_detected (0.1084): Indication of failed recovery attempts.
network_latency_ms (0.0929): Core infrastructure health signal.

## 📂 Project Structure
* [distributed_system_architecture_stress_dataset.ipynb](./distributed_system_architecture_stress_dataset.ipynb): Complete Python code, EDA, and Model training.
* [Project_Report.docx](./reports/Project Report.docx): Formal technical report with findings and SRE recommendations.
* [Dataset Source](https://www.kaggle.com/code/bilalahmed211/stress-and-failure-in-distributed-system): Link to the original Kaggle dataset.

# 🚀 How to Run
Dataset: Ensure the distributed_system_architecture_stress_dataset.csv is in your input directory.
Environment: ```bash pip install pandas numpy scikit-learn seaborn matplotlib
Execution: Run the Jupyter Notebook or the Python script provided in this repository.

# 💡 Conclusion
The analysis proves that ML can predict distributed system failures with near-perfect accuracy. For SRE teams, the results suggest prioritizing the monitoring of P95 Latency and Retry Storms to prevent minor degradations from escalating into total outages.
