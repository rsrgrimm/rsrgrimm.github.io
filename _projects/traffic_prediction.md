---
title: "Traffic Volume, Speed, and Density Forecasting with LSTMs"
excerpt: "Time-series forecasting of highway traffic metrics using a deep learning LSTM model trained on 3 years of data."
categories: ["Time Series", "Deep Learning"]
tags: ["LSTM", "Python", "PyTorch", "Forecasting", "Traffic Modeling"]
layout: single
classes: wide
---

## 📌 Overview
This project explores short-term traffic forecasting using a deep learning model based on Long Short-Term Memory (LSTM) networks. The goal was to predict **traffic volume**, **average speed**, and **vehicle density** using three years of historical highway sensor data enriched with contextual features such as weather conditions, road surface status, and local holidays.

Traffic forecasting is a challenging multivariate time-series problem involving temporal dependencies, cyclic patterns, and external environmental influences. This project demonstrates how LSTM-based architectures can effectively capture these relationships to produce accurate next-step predictions.

---

## Tools & Technologies
- **Python**
- **PyTorch / Keras**
- **Pandas, NumPy**
- **Matplotlib, Seaborn**
- **Scikit-learn**
- **Jupyter Notebooks**

---

## Data Preparation
Before modeling, I conducted extensive preprocessing and feature engineering to improve predictive performance:

### **Data cleaning**
- Handled missing or corrupted sensor readings  
- Removed impossible values (e.g., negative speeds)

### **Feature engineering**
Added contextual and cyclical features, including:  
- Time of year, month, week, day of week  
- Local holidays  
- Weather conditions (temperature, precipitation, visibility)  
- Road surface conditions (wet, icy, snow-covered)  

### **Normalization & scaling**
All continuous features were standardized to stabilize training and improve model convergence.

---

## Exploratory Data Analysis
The dataset exhibited clear seasonal and weekly patterns:
- Higher volumes near commute hours  
- Reduced speed under adverse weather  
- Increased density during holidays and events  

Visual inspection confirmed that traffic metrics display strong **temporal autocorrelation**, making them suitable for recurrent architectures like LSTMs.

---

## Model Architecture
The predictive model uses a multivariate LSTM network designed to capture sequential dependencies and nonlinear interactions between features.

Key architecture choices:
- Windowed sliding sequences for supervised learning  
- 1–2 stacked LSTM layers with dropout  
- Dense output layer for multivariate prediction  
- Mean Squared Error loss function  

Training was performed using an 80/20 train–test split with early stopping to avoid overfitting.

---

## Results
The LSTM model produced strong next-step forecasting performance:

| Metric          | R² Score |
|------------------|----------|
| **Volume**       | **0.96** |
| **Density**      | **0.91** |
| **Average Speed**| **0.56** |

### Interpretation
- Volume and density exhibited strong predictable structure and responded well to the LSTM.  
- Speed proved more volatile, likely influenced by unobserved variables (e.g., accidents, sudden congestion).  
- Additional exogenous inputs or a hybrid CNN–LSTM approach could further improve performance.

---

## Key Takeaways
- Deep learning models can effectively forecast multivariate traffic metrics when supported by robust feature engineering.  
- Enriching raw sensor data with weather, event, and temporal context significantly improves predictive performance.  
- Multivariate LSTMs are particularly well suited for datasets with long-range temporal dependencies.  

---

## Code & Resources
- **Repository:** _Coming soon_  

---

## Future Improvements
- Add a CNN–LSTM or Transformer-based temporal model  
- Predict multi-step sequences rather than single-step  
- Incorporate accident reports and live traffic feeds  
- Deploy the model via a lightweight API for real-time inference  

---

## Summary
This project highlights the effectiveness of LSTM architectures in capturing complex temporal patterns in traffic data. The model achieves high forecasting accuracy on volume and density and lays the groundwork for more advanced deep learning approaches such as attention-based models or hybrid architectures.
