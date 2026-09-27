# 🎬 Netflix Data Analytics Project

![Netflix](https://img.shields.io/badge/Netflix-Data%20Analytics-E50914?style=for-the-badge\&logo=netflix\&logoColor=white)
![Python](https://img.shields.io/badge/Python-Data%20Analysis-3776AB?style=for-the-badge\&logo=python\&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-Database-4479A1?style=for-the-badge\&logo=mysql\&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=for-the-badge\&logo=powerbi\&logoColor=black)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Cleaning-150458?style=for-the-badge\&logo=pandas\&logoColor=white)

# 📊 Netflix Data Analytics

## 📌 Project Overview

This is an **end-to-end Netflix Data Analytics project** built to analyze customer behavior, subscription plans, content preferences, device usage, viewing activity, and account information.

The project starts with an **unclean/raw Excel dataset** and follows a complete data analytics workflow:

```text
Unclean Excel Dataset
        ↓
Data Cleaning & Transformation
        ↓
Exploratory Data Analysis
        ↓
MySQL Database
        ↓
SQL Analysis
        ↓
Power BI Dashboard
        ↓
Business Insights
```

The main objective is to convert raw and inconsistent data into a clean, structured dataset and generate meaningful insights using **Python, SQL, MySQL, and Power BI**.

---

# 🎯 Project Objectives

* Clean and preprocess the raw Netflix dataset.
* Identify and handle missing values.
* Detect and remove duplicate records.
* Standardize inconsistent categorical values.
* Convert columns into appropriate data types.
* Analyze customer demographics.
* Analyze subscription plans and payment methods.
* Analyze customer viewing behavior.
* Analyze device usage.
* Analyze account status.
* Store cleaned data in MySQL.
* Perform SQL-based analysis.
* Build an interactive Power BI dashboard.
* Generate useful business insights.

---

# 📁 Dataset Information

## Raw Dataset

The original dataset used in this project is:

```text
Netflix_Unclean_Project.xlsx
```

This is the **unclean/raw dataset** used as the starting point of the project.

### Dataset Size

* **Rows:** 1,013
* **Columns:** 20
* **File Format:** Excel (`.xlsx`)

---

# 📋 Dataset Columns

| Column              | Description                              |
| ------------------- | ---------------------------------------- |
| `Customer_ID`       | Unique customer identifier               |
| `Customer_Name`     | Customer name                            |
| `Age`               | Customer age                             |
| `Title`             | Netflix content title                    |
| `Content_Type`      | Type of content such as Movie or TV Show |
| `Genre`             | Content genre                            |
| `Country`           | Customer/content country                 |
| `Subscription_Plan` | Customer subscription plan               |
| `Device`            | Device used to access Netflix            |
| `Payment_Method`    | Customer payment method                  |
| `Account_Status`    | Current account status                   |
| `Join_Date`         | Date customer joined                     |
| `Last_Watch_Date`   | Customer's latest watch date             |
| `Watch_Hours`       | Total hours watched                      |
| `Monthly_Fee`       | Monthly subscription fee                 |
| `Movies_Watched`    | Number of movies watched                 |
| `Episodes_Watched`  | Number of episodes watched               |
| `Avg_Rating`        | Average customer/content rating          |
| `Monthly_Sessions`  | Number of monthly viewing sessions       |
| `Download_Count`    | Number of downloaded contents            |

---

# 🛠️ Tools & Technologies

| Technology           | Usage                       |
| -------------------- | --------------------------- |
| **Microsoft Excel**  | Raw dataset                 |
| **Python**           | Data cleaning and analysis  |
| **Pandas**           | Data manipulation           |
| **NumPy**            | Numerical operations        |
| **Jupyter Notebook** | Python analysis             |
| **MySQL**            | Database management         |
| **SQL**              | Data querying and analysis  |
| **Power BI**         | Dashboard and visualization |
| **Git**              | Version control             |
| **GitHub**           | Project hosting             |

---

# 🧹 Step 1 — Data Cleaning

Since the original dataset is **unclean**, data cleaning is an important part of this project.

The raw Excel file is first loaded into Python using Pandas.

```python
import pandas as pd

df = pd.read_excel("Netflix_Unclean_Project.xlsx")

print(df.head())
print(df.shape)
print(df.info())
```

---

## 🔍 Data Quality Checks

The following checks are performed:

### Check Missing Values

```python
df.isnull().sum()
```

### Check Duplicate Records

```python
df.duplicated().sum()
```

### Check Dataset Information

```python
df.info()
```

### Statistical Summary

```python
df.describe()
```

---

# 🧽 Data Transformation

The dataset is standardized before analysis.

Examples include:

* Removing unnecessary spaces.
* Standardizing text values.
* Fixing inconsistent capitalization.
* Removing duplicate records.
* Handling missing values.
* Converting dates into proper date format.
* Converting numerical columns into appropriate data types.
* Standardizing device names.
* Standardizing genre names.
* Standardizing subscription plan names.
* Standardizing account status values.

### Example

```python
df["Country"] = df["Country"].str.strip().str.title()

df["Genre"] = df["Genre"].str.strip().str.title()

df["Subscription_Plan"] = df["Subscription_Plan"].str.strip().str.title()

df["Account_Status"] = df["Account_Status"].str.strip().str.title()

df["Device"] = df["Device"].str.strip().str.title()
```

---

# 📊 Step 2 — Exploratory Data Analysis

After cleaning, Python is used to understand the dataset.

The analysis focuses on:

* Customer demographics
* Content types
* Genres
* Countries
* Subscription plans
* Payment methods
* Devices
* Account status
* Watch hours
* Movies watched
* Episodes watched
* Average ratings
* Monthly sessions
* Downloads
* Monthly subscription fees

---

# 🗄️ Step 3 — MySQL Database

After the cleaning process, the cleaned dataset is stored in MySQL.

### Database

```text
Netflix_db
```

### Main Table

```text
netflix_data
```

The cleaned data can be loaded into MySQL using Python and SQLAlchemy.

Example:

```python
from sqlalchemy import create_engine

engine = create_engine(
    "mysql+pymysql://username:password@localhost/Netflix_db"
)

df.to_sql(
    "netflix_data",
    con=engine,
    if_exists="replace",
    index=False
)
```

---

# 💻 Step 4 — SQL Analysis

SQL is used to analyze the cleaned Netflix dataset.

## 👥 Total Customers

```sql
SELECT COUNT(DISTINCT Customer_ID) AS Total_Customers
FROM netflix_data;
```

---

## 💳 Subscription Plan Analysis

```sql
SELECT 
    Subscription_Plan,
    COUNT(DISTINCT Customer_ID) AS Total_Customers
FROM netflix_data
GROUP BY Subscription_Plan
ORDER BY Total_Customers DESC;
```

---

## 🌍 Country Analysis

```sql
SELECT 
    Country,
    COUNT(DISTINCT Customer_ID) AS Total_Customers
FROM netflix_data
GROUP BY Country
ORDER BY Total_Customers DESC;
```

---

## 📱 Device Analysis

```sql
SELECT 
    Device,
    COUNT(DISTINCT Customer_ID) AS Users
FROM netflix_data
GROUP BY Device
ORDER BY Users DESC;
```

---

## 🎬 Content Type Analysis

```sql
SELECT 
    Content_Type,
    COUNT(*) AS Total_Content
FROM netflix_data
GROUP BY Content_Type;
```

---

## 🎭 Genre Analysis

```sql
SELECT 
    Genre,
    COUNT(*) AS Total_Content
FROM netflix_data
GROUP BY Genre
ORDER BY Total_Content DESC;
```

---

## 💰 Revenue Analysis

```sql
SELECT 
    SUM(Monthly_Fee) AS Total_Monthly_Revenue
FROM netflix_data;
```

---

## ⭐ Average Rating

```sql
SELECT 
    AVG(Avg_Rating) AS Average_Rating
FROM netflix_data;
```

---

## ⏱️ Total Watch Hours

```sql
SELECT 
    SUM(Watch_Hours) AS Total_Watch_Hours
FROM netflix_data;
```

---

# 📈 Step 5 — Power BI Dashboard

The cleaned MySQL dataset is connected to Power BI to create an interactive dashboard.

The dashboard provides a visual overview of Netflix customers, content, subscriptions, and viewing behavior.

---

# 📌 Key Performance Indicators

The dashboard can include the following KPIs:

### 👥 Total Customers

Number of unique customers.

### 💰 Monthly Revenue

Total monthly subscription revenue.

### ⏱️ Total Watch Hours

Total viewing hours across customers.

### 🎬 Total Movies Watched

Total movies watched by customers.

### 📺 Total Episodes Watched

Total episodes watched.

### ⭐ Average Rating

Average rating across the dataset.

### 📱 Total Downloads

Total number of downloaded contents.

### 💳 Average Monthly Fee

Average subscription fee per customer/record.

---

# 📊 Power BI Visualizations

The dashboard contains visualizations such as:

### 1. Customer Distribution

Customer distribution by country.

### 2. Subscription Plan Analysis

Customer count by subscription plan.

### 3. Device Usage

Analysis of devices used to access Netflix.

### 4. Genre Distribution

Distribution of content across genres.

### 5. Content Type

Comparison between Movies and TV Shows.

### 6. Account Status

Distribution of active/inactive/cancelled accounts.

### 7. Payment Method

Customer distribution by payment method.

### 8. Watch Hours

Analysis of customer viewing activity.

### 9. Monthly Sessions

Customer engagement based on monthly viewing sessions.

### 10. Download Analysis

Analysis of Netflix content downloads.

### 11. Rating Analysis

Average rating and rating distribution.

### 12. Customer Age Analysis

Customer distribution across different age groups.

---

# 🔍 Business Questions

This project answers questions such as:

1. How many unique Netflix customers are there?
2. Which subscription plan has the most customers?
3. Which country has the highest number of customers?
4. Which device is used most frequently?
5. Which genres are most popular?
6. What percentage of customers have active accounts?
7. Which payment methods are most commonly used?
8. How many total hours of content are watched?
9. What is the average customer rating?
10. How many movies and episodes are watched?
11. Which customers show higher engagement?
12. How much monthly subscription revenue is generated?
13. Which content type is more common?
14. How does customer age vary across the dataset?
15. How many contents are downloaded by customers?

---

# 💡 Business Insights

The analysis can provide insights into:

### Customer Behavior

Understanding how customers use Netflix and how frequently they engage with the platform.

### Subscription Strategy

Understanding the distribution of customers across subscription plans.

### Content Strategy

Identifying popular genres and content types.

### Device Strategy

Understanding the devices customers use to consume Netflix content.

### Customer Engagement

Analyzing watch hours, sessions, downloads, movies watched, and episodes watched.

### Revenue Analysis

Understanding subscription revenue based on monthly fees.

---

# 📂 Project Structure

```text
Netflix-Data-Analytics/
│
├── Dataset/
│   ├── Netflix_Unclean_Project.xlsx
│   └── Netflix_Cleaned.xlsx
│
├── Python/
│   └── Netflix_Data_Cleaning_Analysis.ipynb
│
├── SQL/
│   └── Netflix_Analysis.sql
│
├── PowerBI/
│   └── Netflix_Dashboard.pbix
│
├── Images/
│   └── Netflix_Dashboard.png
│
└── README.md
```

---

# ⚙️ How to Use

## 1. Clone the Repository

```bash
git clone https://github.com/iamafzal-06/netflix_data_analysis
```

```bash
cd Netflix-Data-Analytics
```

---

## 2. Install Python Libraries

```bash
pip install pandas numpy openpyxl sqlalchemy pymysql jupyter
```

---

## 3. Open Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
Python/Netflix_Data_Cleaning_Analysis.ipynb
```

Run the notebook step by step.

---

## 4. Create MySQL Database

Open MySQL Workbench and run:

```sql
CREATE DATABASE Netflix_db;
```

Then select the database:

```sql
USE Netflix_db;
```

---

## 5. Load Cleaned Data

Run the Python data-loading code to upload the cleaned dataset into:

```text
Netflix_db
    └── netflix_data
```

---

## 6. Run SQL Analysis

Open:

```text
SQL/Netflix_Analysis.sql
```

Run the required queries in MySQL Workbench.

---

## 7. Open Power BI

Open:

```text
PowerBI/Netflix_Dashboard.pbix
```

Connect Power BI to the MySQL database and refresh the dataset.

---

# 📸 Dashboard Preview

Add your Power BI dashboard screenshot here:

```markdown
![Netflix Dashboard](Images/Netflix_Dashboard.png)
```

---

# 🧠 Skills Demonstrated

This project demonstrates practical knowledge of:

* Data Cleaning
* Data Preprocessing
* Exploratory Data Analysis
* Python
* Pandas
* NumPy
* SQL
* MySQL
* Power BI
* Data Visualization
* KPI Development
* Business Intelligence
* Data Transformation
* Database Management
* Git
* GitHub

---

# 🚀 Project Highlights

```text
✔ Raw / Unclean Excel Dataset
✔ Data Cleaning with Python & Pandas
✔ Exploratory Data Analysis
✔ Data Transformation
✔ MySQL Database
✔ SQL Analysis
✔ Power BI Dashboard
✔ KPI Development
✔ Customer Analysis
✔ Subscription Analysis
✔ Content Analysis
✔ Viewing Behavior Analysis
✔ Business Insights
```

---

# 👨‍💻 Author

## Md Afzal

**B.Tech – Computer Science & Engineering**

### Technical Skills

```text
Python | SQL | MySQL | Power BI | Excel
Pandas | NumPy | Data Analysis | Data Visualization
Git | GitHub
Java | Spring Boot
```

---

# 📜 Project Purpose

This project was created as a **portfolio project to demonstrate practical Data Analytics skills** by taking an unclean dataset through the complete analytics lifecycle:

```text
Raw Data
   ↓
Clean Data
   ↓
Analysis
   ↓
Database
   ↓
SQL
   ↓
Visualization
   ↓
Insights
```

---

# ⭐ Conclusion

The Netflix Data Analytics project demonstrates how raw and unclean data can be transformed into meaningful information using modern data analytics tools.

By combining **Python, Pandas, MySQL, SQL, and Power BI**, the project provides an end-to-end example of data cleaning, analysis, visualization, and business intelligence.

---
