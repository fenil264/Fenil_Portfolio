# 🧠 Career Recommendation System  
*A Machine Learning Pipeline for Student Guidance*

---

## 🧭 Project Overview

This industry-focused project, conducted under IBM's academic collaboration, addresses the challenge of helping students discover suitable career paths. We built a smart, ML-driven system that recommends careers based on test input and interest scores — trained on labeled student performance data.

The project included **model benchmarking**, **full-stack deployment**, and **cloud integration** using AWS.

---

## 🎯 Objectives

- Predict best-fit career domains using test/interest scores
- Evaluate multiple ML models for classification performance
- Build an interactive web interface using Flask
- Host the app for public access on AWS

---

## 🗂️ Dataset Description

| Feature Type     | Examples                            |
|------------------|-------------------------------------|
| Input Scores     | Logical, Verbal, Analytical, Coding |
| Labels (Target)  | Career Fields (e.g., DevOps, Data Science, Cloud, Security) |
| Size             | ~200 samples (student-level)        |

---

## ⚙️ Methodology

### 🧠 Model Development
- **Algorithms**: KNN, Decision Tree, SVM, ANN (TensorFlow)
- **Evaluation**: Accuracy, confusion matrix, cross-validation
- **Best Model**: Decision Tree (85% accuracy)

### 🌐 System Architecture
- **Frontend**: HTML, CSS, Bootstrap (responsive form)
- **Backend**: Flask app with pre-trained model
- **Deployment**: AWS EC2 (Ubuntu server)

---

## 📊 Key Results

- **Model Benchmarking**:
  - ANN and Decision Tree performed best (84–85% accuracy)
  - SVM slightly underperformed on small dataset

- **Live Deployment**:
  - Real-time predictions via a hosted web form
  - Responsive UI with user-friendly design

---

## 🔍 User Interaction Flow

1. User submits interest/test scores via web form  
2. Backend processes input, applies pre-trained ML model  
3. Career recommendation returned instantly  

---

## 📍 Business/Academic Relevance

- Provides accessible, low-cost career guidance for students
- Can be scaled into a career recommendation engine for ed-tech platforms
- Demonstrates an end-to-end machine learning deployment pipeline

---

## 🛠️ Tools & Technologies

- Python (pandas, scikit-learn, TensorFlow)
- Flask (backend), HTML/CSS/Bootstrap (frontend)
- Git, GitHub, AWS EC2
- Jupyter Notebook

---

## 📌 Next Steps

- Improve training data scale and feature variety  
- Add feedback loop to track user outcomes  
- Explore NLP for resume/job alignment  
- Dockerize the deployment pipeline for portability  

---

## 📂 GitHub Repository

> [Career Recommendation System on GitHub](https://github.com/fenil264/IBM_Career_Recommendation_Project)
