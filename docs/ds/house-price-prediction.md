# 🏡 House Price Prediction  
*A Machine Learning Application in Real Estate Forecasting*

---

## 🧭 Project Overview

This project focuses on building a predictive system to estimate house prices based on property attributes. The goal was to explore regression techniques and deploy a working web application that makes predictions based on user input. The solution is enhanced by a complementary Tableau dashboard for visual analytics.

---

## 🎯 Objectives

- Predict residential property prices using structured housing data  
- Compare regression models to evaluate fit and interpretability  
- Build a simple, interactive web app for user-facing predictions  
- Use Tableau to explore pricing trends visually

---

## 🗂️ Dataset Description

| Feature Type     | Examples                                  |
|------------------|-------------------------------------------|
| Numerical Inputs | Area (sqft), Bedrooms, Bathrooms          |
| Categorical Data | City, Location                            |
| Size             | ~10,000 records from diverse regions      |

---

## ⚙️ Methodology

### 📦 Data Preprocessing
- Removed extreme outliers and inconsistent records  
- Consolidated sparse locations and cleaned missing values  
- One-hot encoded categorical variables for modeling

### 🤖 Model Selection
- **Linear Regression**
- **Polynomial Regression**
- **Decision Tree Regressor**
- **Random Forest**
- **Artificial Neural Network (ANN)** using TensorFlow

### 🌐 Deployment Architecture
- **Frontend**: Streamlit (form + result interface)  
- **Backend**: Pre-trained `.pkl` model embedded in app  
- **Deployment**: Tested locally and on Netlify

---

## 📊 Key Learnings

- Tree-based models provided stable predictions on cleaned data  
- Input skew and granularity (e.g., location) strongly influenced model quality  
- Streamlit enabled quick deployment and feedback integration  
- ANN required more compute and hyperparameter tuning

---

## 📈 Interactive Dashboard (BI Layer)

To complement the ML model, an interactive Tableau dashboard was created for business-level insight into house price trends.

It enables filtering and exploration of:

- Price distribution by city and property type  
- Area, bedroom, and bathroom influence on pricing  
- Comparative views across locations

View the dashboard here:  
> [Launch Tableau Dashboard](https://public.tableau.com/app/profile/fenil5823/viz/House_Industry/Dashboard2)

---

## 🛠️ Tools & Technologies

- Python (pandas, numpy, scikit-learn, tensorflow)  
- Streamlit (for deployment), Jupyter Notebook  
- Tableau Public (BI dashboard)  
- Git & GitHub (version control)

---

## 📌 Next Steps

- Integrate housing APIs for live data  
- Add geospatial mapping using `folium` or `plotly`  
- Build model explainability with SHAP or LIME  
- Dockerize and containerize for scalable deployment

---

## 📂 GitHub Repository

> [House Price Prediction – GitHub](https://github.com/fenil264/House_Price_Prediction)
