# Customer Churn Analysis: Revenue & Retention Strategy

## 📊 Project Overview
This project analyzes a dataset of 7,043 telecom customers to identify the root causes of customer churn. unlike standard sales reporting, this analysis focuses on building a "Value Profile" of customers to transition the business from a reactive state to a proactive retention strategy.

**Key Objective:** Reduce the **26.54% churn rate** and safeguard the **$17M+ in revenue** currently at risk by identifying high-risk segments and optimizing contract structures.

---

## 🚀 Executive Summary & Key Metrics

* **Total Customers:** 7,043
* **Churn Rate:** 26.54% (1,869 customers lost)
* **Revenue at Risk:** ~$17,177,561
* **Avg Monthly Revenue:** $64.76 per user

### 📉 Key Findings
1.  **Contract Type is the #1 Driver:** Churn is not a general problem; it is a **Month-to-Month** contract problem. Month-to-month users have a **42.71% churn rate**, while 1-year and 2-year contract holders are highly stable.
2.  **Revenue Trap:** The company is financially dependent on its most volatile segment. The highest revenue comes from Month-to-Month Fiber Optic users, who are also the most likely to churn.
3.  **The "Cliff" Exists:** Churn is an early-stage issue. The highest volume of customers leave within months 0–5. If a customer survives the first 6 months, their Lifetime Value (LTV) increases significantly.

---

## 🖼️ Dashboard Gallery

### 1. Overview & Churn Breakdown
*A high-level view of the churn rate, revenue at risk, and demographics.*
<img width="1914" height="1070" alt="Screenshot 2025-12-05 151653" src="https://github.com/user-attachments/assets/6066dcb5-8acc-467b-9603-496d581d5cfc" />


### 2. Services & Revenue Impact
*Analyzing how add-on services and tenure affect the customer value profile.*
<img width="1918" height="1075" alt="Screenshot 2025-12-05 151712" src="https://github.com/user-attachments/assets/32c559ef-d42c-4b05-a407-79a59c11066e" />


### 3. Trend & Forecast Analysis
*Identifying the specific tenure timeline where customer drop-off peaks.*
<img width="1917" height="1073" alt="Screenshot 2025-12-05 151731" src="https://github.com/user-attachments/assets/659f7512-7ed0-43b5-829d-4f6f4ea76368" />


---

## 🛠️ Data Preparation & Technical Approach
**Tools Used:** Tableau (End-to-End Data Cleaning & Visualization), Kaggle (Data Source).

Unlike typical workflows that rely on Python or SQL for pre-processing, this project utilized **Tableau's native data engineering features** to handle complex data structuring.

### Key "Under the Hood" Transformations:
* **Handling Nulls & Data Types:** `TotalCharges` contained blank strings for new customers (tenure = 0). I converted these to decimals and created a calculated field `Total_charges (cleaned)` to handle Nulls as 0.
* **Advanced Pivoting for Service Analysis:**
    * *Challenge:* The dataset had 6 separate columns for add-on services (Online Security, Tech Support, etc.), making it impossible to compare them in a single clean chart.
    * *Solution:* I used **Tableau Pivot** to restructure these 6 columns into two: `Add-on Services` (Dimension) and `Subscribed` (Value).
* **Solving Data Duplication:**
    * *Challenge:* Pivoting the data duplicated customer rows, artificially inflating the customer count.
    * *Solution:* I redefined all key metrics using Level of Detail (LOD) concepts and Distinct Counts.
    * *Code Example:* `Total_customer_lost = COUNTD(IF [CHURN] = 'Yes' THEN [Customer ID] END)`

---

## 💡 Recommendations
Based on the data, the following strategic actions are recommended:
1.  **Target the "Danger Zone" (Months 2-3):** Launch aggressive promotional campaigns targeting Month-to-Month users entering their second month. Offer a discount for switching to a 1-Year contract to bridge the gap past the 5-month "churn cliff."
2.  **Revamp Fiber Optic Onboarding:** Since Fiber Optic users generate the most revenue but churn frequently, the onboarding process must be improved to demonstrate value early, reducing price sensitivity.

---

## 📂 Data Source
The dataset was sourced from Kaggle: [Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
