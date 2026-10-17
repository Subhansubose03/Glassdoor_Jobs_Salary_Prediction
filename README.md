<div align="center">

# 💼 Glassdoor Jobs Salary Prediction

### An End-to-End Regression Machine Learning Project

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=for-the-badge)
![Seaborn](https://img.shields.io/badge/Seaborn-4c72b0?style=for-the-badge)

</div>

---

## 📑 Table of Contents
- [Overview](#-overview)
- [Problem Statements](#-problem-statements)
- [Dataset](#-dataset)
- [Data Cleaning & Feature Engineering](#-data-cleaning--feature-engineering)
- [Exploratory Data Analysis](#-exploratory-data-analysis)
- [Machine Learning Models](#-machine-learning-models)
- [Results](#-results)
- [Business Insights](#-business-insights)
- [Tech Stack](#-tech-stack)
- [How to Run](#-how-to-run)
- [Conclusion](#-conclusion)
- [Future Improvements](#-future-improvements)
- [Author](#-author)

---

## 📌 Overview

This project analyzes **technology job salaries** using the Glassdoor Jobs dataset (collected 2017–2018) and builds a machine learning model that **predicts the average salary** for a job based on role and company attributes.

It covers the full data science workflow: data cleaning, feature engineering, exploratory data analysis, visualization, model building and evaluation.

**Who can benefit?**
- 🧑‍💻 Job seekers estimating expected pay
- 🏢 Employers benchmarking compensation
- 🔎 Recruiters planning competitive offers
- 📊 Analysts studying salary trends

---

## ❓ Problem Statements

1. How does salary vary by **job position** (for example Data Scientist vs. Software Engineer vs. DevOps Engineer)?
2. What is the impact of **company size** on salary levels?
3. How do salaries differ by **location**?
4. Can we build a **predictive model** to estimate salaries from job attributes?

---

## 📊 Dataset

| Detail | Value |
|--------|-------|
| **Source** | Glassdoor Jobs dataset (2017–2018) |
| **Rows** | 956 job listings |
| **Columns** | 15 (14 after dropping the index column) |
| **Target** | Average salary (in $K) |

**Main columns:** Job Title, Salary Estimate, Job Description, Rating, Company Name, Location, Headquarters, Size, Founded, Type of Ownership, Industry, Sector, Revenue, Competitors

---

## 🧹 Data Cleaning & Feature Engineering

**Cleaning**
- ✅ Dropped the unnecessary `Unnamed: 0` index column
- ✅ Cleaned the text-based **Salary Estimate** (for example `$53K-$91K (Glassdoor est.)`) into numeric values
- ✅ Replaced the `-1` placeholder in `Rating` with the **median** (robust to skewed data)
- ✅ Removed extreme salary outliers using the **IQR method**
- ✅ Cleaned company names that had ratings attached

**Engineered features**

| New Feature | How it was created |
|-------------|--------------------|
| `min_salary`, `max_salary` | Parsed from the salary range text |
| `avg_salary` | Mean of min and max salary (**target variable**) |
| `job_state` | Extracted from the Location column |
| `company_age` | `2020 − Founded year` |
| `job_desc_length` | Character length of the job description |

---

## 🔍 Exploratory Data Analysis

Six visualizations were built to understand salary patterns:

1. **Salary distribution:** most salaries cluster in the mid-range, with high salaries rarer
2. **Top job roles:** Data Scientist and Data Engineer roles appear most frequently
3. **Salary by company size:** larger companies tend to pay more
4. **Salary by state:** tech hubs like CA and NY generally offer higher pay
5. **Correlation heatmap:** min and max salary strongly relate to average salary
6. **Industry vs. salary:** compensation varies across industries

---

## 🤖 Machine Learning Models

**Features used:** Job Title, Rating, Size, Industry, Sector, Revenue, Job State, Company Age, Job Description Length

**Pipeline**
1. Label-encoded categorical variables
2. Split the data **80% train / 20% test** (`random_state=42`)
3. Trained and compared two regression models:
   - 📉 **Linear Regression** (baseline)
   - 🌲 **Random Forest Regressor** (100 trees)

---

## 🏆 Results

| Model | MAE | RMSE | R² Score |
|-------|-----|------|----------|
| Linear Regression | 25.90 | 32.90 | 0.04 |
| **Random Forest** ⭐ | **12.64** | **18.22** | **0.71** |

**What this means**
- 🌲 Random Forest explains about **71%** of salary variation, versus only 4% for Linear Regression
- 💵 Average prediction error is about **±$12.6K**
- 🔀 Salary depends on **non-linear, interacting factors** (role, location, company size) that Linear Regression cannot capture

**Sample predictions (Random Forest)**

| Actual ($K) | Predicted ($K) |
|-------------|----------------|
| 128.5 | 129.2 |
| 81.0 | 82.3 |
| 95.5 | 93.7 |
| 113.5 | 112.6 |

A **feature importance** analysis shows which attributes drive salary predictions the most, with job title, location and company size among the key factors.

---

## 💡 Business Insights

- 🎯 **Role matters:** specialized technical roles command higher pay
- 🏢 **Company size matters:** larger organizations generally offer higher salaries
- 📍 **Location matters:** tech hubs such as California and New York pay more
- 🤖 **Prediction is feasible:** a Random Forest model can estimate salaries reasonably well and help with benchmarking

---

## 🛠️ Tech Stack

- **Language:** Python
- **Data:** Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Machine Learning:** Scikit-learn (Linear Regression, Random Forest, LabelEncoder, train_test_split, metrics)
- **Environment:** Google Colab / Jupyter Notebook

---

## 🚀 How to Run

1. Clone the repository
```bash
   git clone https://github.com/Subhansubose03/<your-repo-name>.git
   cd <your-repo-name>
```
2. Install the required libraries
```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
```
3. Place `glassdoor_jobs.csv` in the project folder
4. Open `Glassdoor_Jobs_Salary_Prediction_Project.ipynb` in Jupyter Notebook or Google Colab and run all cells

---

## ✅ Conclusion

This project shows that tech salaries are strongly shaped by **job title, company size and location**. After thorough cleaning and feature engineering, a **Random Forest model reached R² ≈ 0.71 with an average error of about $12.6K**, far outperforming Linear Regression (R² ≈ 0.04).

It highlights how proper preprocessing, outlier handling and model selection improve predictions, and how machine learning can support data-driven salary decisions.

---

## 🔮 Future Improvements

- Use **One-Hot or Target Encoding** instead of Label Encoding for categorical features
- Extract **skills** (Python, SQL, AWS and so on) from job descriptions as features
- Try **Gradient Boosting / XGBoost** and **hyperparameter tuning**
- Use **cross-validation** for more reliable evaluation
- Deploy the model as a simple **web app** for live salary prediction

---

## 👤 Author

**Subhansu Bose**
Aspiring Data Analyst | Python • SQL • Power BI • Excel

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/subhansu-bose-576872246/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Subhansubose03)

⭐ If you found this project helpful, consider giving it a star!
