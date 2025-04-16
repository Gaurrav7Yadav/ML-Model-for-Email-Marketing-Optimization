# 📧 Email Campaign Optimization

## 🔍 Objective
This project analyzes an email marketing campaign conducted by an e-commerce platform. The key goals are:

- Measure **open** and **click-through rates (CTR)**
- Build a **predictive model** to maximize link clicks
- Estimate CTR improvements through smarter targeting
- Analyze user behavior across segments

---

## 📂 Dataset Description

This project uses **3 CSV files**:

### 1. `email_table.csv`
Contains info about each sent email.

| Column             | Description                                      |
|--------------------|--------------------------------------------------|
| `email_id`         | Unique ID of the email                          |
| `email_text`       | "short" or "long" version of the email          |
| `email_version`    | "personalized" or "generic"                     |
| `hour`             | Local time the email was sent                   |
| `weekday`          | Day of the week                                 |
| `user_country`     | Country based on user IP                        |
| `user_past_purchases` | Number of past purchases by the user        |

### 2. `email_opened_table.csv`
List of emails that were opened.

| Column     | Description           |
|------------|-----------------------|
| `email_id` | Email that was opened |

### 3. `link_clicked_table.csv`
List of emails where the link inside was clicked.

| Column     | Description             |
|------------|-------------------------|
| `email_id` | Email with a link click |

---

## 🧮 Steps Performed

### ✅ Step 1: Data Loading
- Load the 3 CSV files using Pandas

### ✅ Step 2: Basic Metrics
- **Open Rate** = Emails Opened / Total Emails Sent  
- **CTR** = Emails Clicked / Total Emails Sent

### ✅ Step 3: Data Preprocessing
- Merge open and click data with the main table
- Add binary labels: `opened`, `clicked`
- Encode categorical columns and fill missing values

### ✅ Step 4: Modeling
- **Features Used:** `email_text`, `email_version`, `hour`, `weekday`, `user_country`, `user_past_purchases`
- **Target Variable:** `clicked`
- **Model Used:** `XGBoost Classifier`
- Evaluation metrics:
  - Classification Report
  - AUC Score
  - Confusion Matrix

### ✅ Step 5: CTR Optimization
- Predict click probabilities for all users
- Select top 20% highest-probability users
- Calculate CTR of this subgroup
- Compare with overall CTR to estimate gain

### ✅ Step 6: Segment Analysis
- Analyze CTR by:
  - `email_text`
  - `email_version`
  - `hour`
  - `weekday`
  - `user_country`

---


