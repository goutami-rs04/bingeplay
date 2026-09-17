# bingeplay
# 🎬 BingePlay — Streaming Analytics with Advanced SQL

> **An end-to-end SQL & Data Analytics project focused on solving real-world streaming business problems using MySQL and Python.**

---

## 📌 About the Project

**BingePlay** is a fictional Indian OTT streaming platform launched in January 2024.

The project simulates the work of a **Data Analyst** working with a streaming platform's production database and answering real business questions related to:

* 💰 Revenue & subscriptions
* 👥 User signups
* 📺 Content performance
* 📱 Device usage
* ⭐ Ratings
* 🍿 Binge-watching behaviour
* 🔄 Subscription upgrades
* 🔥 User engagement
* 📉 Churn signals

The project contains **12 business-focused SQL problems**, progressing from basic SQL analysis to advanced concepts such as **window functions, LAG(), self-joins, CTEs, and gaps-and-islands analysis**.

---

## 🎯 Project Objectives

The main objectives of this project are to:

* Analyze streaming platform user behaviour
* Extract meaningful insights from relational data
* Solve real-world business questions using SQL
* Practice advanced SQL querying techniques
* Identify user engagement and churn patterns
* Understand subscription and content performance
* Develop analytical thinking using structured business problems

---

## 🗃️ Dataset

The BingePlay database contains **5 relational tables**:

| Table            | Records | Description                         |
| ---------------- | ------: | ----------------------------------- |
| `users`          |   3,000 | User profile and signup information |
| `subscriptions`  |   4,497 | Subscription history                |
| `shows`          |     100 | OTT content catalogue               |
| `watch_sessions` | 100,351 | User viewing activity               |
| `ratings`        |   5,000 | User ratings for shows              |

### Database Highlights

* 3 subscription plans: **Basic, Premium, Family**
* Content available across **7 languages**
* Multiple subscription records per user
* Watch sessions across **Mobile, TV, Laptop and Tablet**
* Shows classified as **Originals or Acquired**
* Ratings ranging from **1 to 5 stars**

---

## 🔍 Business Questions

The project answers **12 business questions** divided into three levels.

### 🟢 Tier 1 — SQL Foundations

**1. Active Revenue**

Calculate the monthly recurring revenue from active subscriptions as of June 30, 2024.

**2. Signup Momentum**

Analyze monthly user signups from January to June 2024 and identify the month with the highest number of signups.

**3. Device Analytics**

Analyze:

* Total sessions
* Total watch minutes
* Average watch minutes per session
* Completion rate

for each device type.

**4. Rating Distribution**

Analyze the distribution of 1–5 star ratings and calculate the percentage of ratings that are 4 or 5 stars.

**5. Originals vs Acquired Content**

Compare BingePlay Originals and acquired shows based on:

* Number of shows
* Average IMDb rating
* Average release year

---

### 🟡 Tier 2 — Joins & Subqueries

**6. Binge Day Detection**

Identify days where a user watched the **same show at least 5 times** on the same date.

**7. Q1 Users Who Never Watched**

Find users who signed up during Q1 2024 but never watched anything.

This question specifically handles the **SQL NULL trap** caused by nullable `user_id` values.

**8. Over-Paying Premium/Family Users**

Identify Premium or Family users who only watched content available on the Basic plan.

**9. Upgrade Success Cohort**

Identify users who:

* Signed up in January 2024
* Started with Basic
* Later upgraded to Premium or Family
* Were still active as of June 30, 2024

---

### 🔴 Tier 3 — Advanced SQL

**10. Cliffhanger Comebacks**

Identify users who returned to watch the same show within **1–7 days** after an incomplete session.

**11. Consecutive-Week Engagement**

Find users who watched content for **4 or more consecutive calendar weeks**.

This uses the classic **gaps-and-islands** technique.

**12. Churn Signal Detection**

Identify users whose total watch time in June 2024 dropped by **50% or more** compared with May 2024.

These users can be considered potential early churn signals.

---

## 🧠 SQL Concepts Used

This project helped me work with:

```text
SELECT
WHERE
GROUP BY
ORDER BY
Aggregate Functions
JOINs
LEFT JOIN
Self JOIN
Subqueries
NOT EXISTS
NULL Handling
CTEs
ROW_NUMBER()
LAG()
Window Functions
Date Functions
Gaps-and-Islands
Conditional Aggregation
```

---

## ⚠️ Interesting SQL Challenges

### 1. Handling NULL values

The `watch_sessions.user_id` column contains NULL values.

A simple:

```sql
NOT IN (SELECT user_id FROM watch_sessions)
```

can produce incorrect results when NULL exists in the subquery.

The project therefore uses approaches such as:

```sql
LEFT JOIN ... IS NULL
```

or

```sql
NOT EXISTS
```

to correctly identify users who never watched anything.

### 2. Gaps-and-Islands

The consecutive-week engagement problem requires identifying groups of consecutive weeks for each user using window functions and a gaps-and-islands approach.

### 3. Window Function Filtering

For churn detection, monthly watch-time aggregates are compared using `LAG()` and filtered through a CTE rather than directly referencing the window-function result inside `WHERE`.

---

## 🛠️ Tech Stack

| Technology              | Purpose                       |
| ----------------------- | ----------------------------- |
| 🐬 **MySQL**            | Database & SQL analysis       |
| 🐍 **Python**           | Data analysis                 |
| 🐼 **Pandas**           | Query results & data handling |
| 📓 **Jupyter Notebook** | Analysis & documentation      |
| 🔗 **SQLAlchemy**       | Database connection           |
| 🔌 **PyMySQL**          | MySQL connectivity            |

The project notebook connects to the MySQL database using **SQLAlchemy + PyMySQL** and executes queries through Pandas.

---

## 📂 Project Structure

```text
BingePlay/
│
├── 📓 bingeplay_<yourname>.ipynb
├── 🗄️ bingeplay_setup.sql
├── 📄 BingePlay_Project_Brief.pdf
└── 📖 README.md
```

---

## ⚙️ How to Run

### 1️⃣ Clone the repository

```bash
git clone https://github.com/yourusername/BingePlay.git
```

### 2️⃣ Open MySQL

Run the database setup script:

```sql
SOURCE bingeplay_setup.sql;
```

Or execute the SQL script using MySQL Workbench.

### 3️⃣ Verify the database

```sql
USE bingeplay;
```

Then verify the tables and record counts.

Expected dataset size:

```text
users            → 3,000
subscriptions    → 4,497
shows            → 100
watch_sessions   → 100,351
ratings          → 5,000
```

The project brief specifies these expected row counts.

### 4️⃣ Open the Jupyter Notebook

Install the required Python libraries if necessary:

```bash
pip install pandas sqlalchemy pymysql jupyter
```

Then open:

```bash
jupyter notebook
```

Run the notebook cells to execute the SQL queries and view the results.

---

## 📊 Key Analytical Areas

The project focuses on several areas of streaming analytics:

```text
Subscription Analytics
        ↓
Revenue Analysis
        ↓
User Behaviour
        ↓
Content Performance
        ↓
Engagement Analysis
        ↓
Upgrade Behaviour
        ↓
Binge Detection
        ↓
Churn Signals
```

---

## 💡 What I Learned

Through this project, I strengthened my understanding of:

* Writing structured SQL queries
* Working with relational databases
* Joining multiple tables
* Handling NULL values correctly
* Using CTEs for complex queries
* Applying window functions
* Using `ROW_NUMBER()` and `LAG()`
* Solving gaps-and-islands problems
* Translating business questions into SQL
* Interpreting query results from a business perspective

---

## 🚀 Future Improvements

Some possible extensions to BingePlay include:

* 📊 Interactive Power BI dashboard
* 📈 Revenue and subscription trend dashboards
* 👥 Customer segmentation
* 🤖 Churn prediction using Machine Learning
* 🎯 Personalized content recommendations
* 📱 Deeper device and engagement analysis

---

## 👩‍💻 Author

**Goutami RS**

Information Science & Engineering Student

Interested in **Data Analytics, SQL, Python & Data Science**

---

## ⭐ If You Found This Project Interesting

Feel free to explore the repository, check out the SQL queries, and share your feedback!

**If you found it useful, consider giving the repository a ⭐**

---

### 📌 Project Note

BingePlay is a **fictional OTT platform and dataset created for analytics practice**. The project is designed to simulate real-world data analyst tasks and business questions.
