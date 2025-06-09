# 🍔 McDonald's Customer Segmentation & Satisfaction Prediction

Welcome to the McDonald's Data Analysis project. This repository presents a comprehensive approach to understanding customer preferences, segmenting them into distinct clusters, and predicting their satisfaction scores using machine learning.

---

## 🧠 Project Overview

This project combines **data analysis**, **customer segmentation**, and **regression modeling** to understand how McDonald's customers feel about different aspects of their dining experience. It uses survey responses about food characteristics (e.g., tasty, greasy, healthy), demographics (e.g., age, gender), and behavioral data (visit frequency) to:

- Perform **Exploratory Data Analysis (EDA)**
- Segment customers using **K-Means Clustering**
- Predict customer **Likeability score** using **regression models**

---

## 📊 Dataset Description

The dataset includes 1,453 responses collected from McDonald's customers. Each row represents one customer with:

- **Binary features** for food attributes (e.g., `yummy`, `greasy`)
- **Demographic features** (`Age`, `Gender`)
- **Visit pattern** (`VisitFrequency`)
- **Target**: `Like` (how much the customer likes McDonald's)

| Column Name        | Type       | Description                                 |
|-------------------|------------|---------------------------------------------|
| yummy             | Binary     | Whether customer finds food yummy           |
| convenient        | Binary     | Perceived convenience of the service        |
| spicy             | Binary     | Perceived spiciness                         |
| fattening         | Binary     | Perceived unhealthiness/fat content         |
| greasy            | Binary     | Perceived greasiness                        |
| fast              | Binary     | Whether service is fast                     |
| cheap             | Binary     | Whether food is cheap                       |
| tasty             | Binary     | Overall taste quality                       |
| expensive         | Binary     | Perceived expense                           |
| healthy           | Binary     | Whether food is considered healthy          |
| disgusting        | Binary     | Perceived disgust                           |
| Like              | Continuous | Target variable (scaled customer rating)    |
| Age               | Numeric    | Age of the customer                         |
| VisitFrequency    | Ordinal    | How often the customer visits               |
| Gender            | Categorical| Gender of the customer                      |

---

## 🔧 Preprocessing Steps

- ✅ **Label Encoding**: Converted `Gender` to 0 (Male) / 1 (Female)
- ✅ **Visit Frequency Mapping**:
  ```python
  {
      'Never': 0,
      'Once a year': 1,
      'Every three months': 2,
      'Once a month': 3,
      'Once a week': 4,
      'More than once a week': 5
  }


✅ MinMax Scaling: Applied to Like, Age, and VisitFrequency

✅ Clustering: Added Cluster column using KMeans

✅ One-hot encoding: Not necessary since binary features are already numerical  

🔬 Techniques Used
Technique	Purpose
PCA	Reduce 11 binary features to 2 components
KMeans	Segment customers into clusters
XGBoost	Predict "Like" score from 13 features
GridSearchCV	Hyperparameter tuning for best model
MinMaxScaler	Normalize numeric features to [0, 1]

🎯 Target: Like Score Prediction
The primary goal is to predict the Like score (scaled between 0 and 1) using the following 13 features:

11 binary features: yummy, convenient, ..., disgusting

Age (scaled)

VisitFrequency (mapped and scaled)

❌ The Cluster column is not used in regression—it is for analysis/segmentation only.

📈 Model Performance
| Model        | R² Score | RMSE |
| ------------ | -------- | ---- |
| XGBoost      | 0.76     | 1.62|
| RandomForest | 0.74     | 1.66 |

