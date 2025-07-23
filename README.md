# 🧪 Labtest Data Engineering & AI Project

This project focuses on cleaning and processing a messy cancer diagnostics dataset, building a data pipeline, and formulating a machine learning approach. It was developed as part of a take-home technical assessment.

---

## 📁 Dataset

The dataset simulates real-world healthcare data challenges and includes test orders across multiple facilities and test types:
- Histology
- Cytology
- Haematology
- Immunohistochemistry

🗂 Source: [Kaggle - Labtest Dataset](https://www.kaggle.com/datasets/eustusmurea/labtest-dataset)

---

## 🧼 Task 1: Data Cleaning & Standardization

### ✔ Cleaning Goals:
- Handle **missing values**
- Standardize **date formats**
- Correct **typos** and inconsistencies
- Convert **price** to numeric
- Remove **duplicates**
- Normalize **categorical fields**

### 🛠 Tools:
- Python
- Pandas
- Regex

### 📄 Output:
- `cleaned_labtest_dataset.csv`
- `data_cleaning.py`: Reusable cleaning script
- Documented assumptions (see below)

---

## 🔁 Task 2: ETL Pipeline

### ✔ Pipeline Stages:
- **Extract**: Load raw CSV
- **Transform**: Clean and standardize data
- **Load**: Store data into SQLite database

### 🛠 Tools:
- Python
- SQLite
- SQLAlchemy (optional for ORM)
- Modular pipeline functions

### 📄 Output:
- `etl_pipeline.py`
- `labtest.sqlite`
- `etl_report.md` (explains each pipeline step)

---

## 🤖 Task 3: Machine Learning Task

### 🔍 Objective:
Predict **delay in test processing** (in days) based on test type, facility, category, etc.

### ✔ ML Plan:
- **Target Variable**: `delay_days` (calculated as `signout_date - creation_date`)
- **Features**:
  - Test type/category
  - Facility
  - Service
  - Price
- **Model Options**: Linear Regression, Random Forest
- **Metrics**: MAE, RMSE

### 📄 Output:
- `ml_task_writeup.md`: Machine learning strategy & justification

---

## 📌 Assumptions & Cleaning Decisions

- Replaced variations like `"INS"`, `"ins"`, `"insurance"` with `"Insurance"`
- Standardized date columns using `pd.to_datetime(errors='coerce')`
- Dropped records with missing `order_id`, `patient_name`, or invalid dates
- Converted `price` strings (e.g., `"KES 3,000"`) to floats
- Applied lowercasing and trimming to all string fields
- Replaced invalid or missing entries with `"Unknown"` where appropriate

---

## 📦 File Structure

