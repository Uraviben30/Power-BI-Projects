# 💳 Loan Analysis Dashboard

The **Loan Analysis Dashboard** is an advanced Power BI report that delivers deep insights into loan performance, borrower profiles, and financial risk. Designed for analysts, risk managers, and financial institutions, this dashboard visualizes key trends in loan defaults, income brackets, education levels, credit scores, and more.

---

## 🧩 Dashboard Overview

### 🔹 Page 1: Loan Default Overview
- **Loan Amount by Purpose**: Bar chart showing loan distribution across purposes (home, business, education, etc.)
- **Average Income by Employment Type**: Bar chart comparing income levels for full-time, part-time, self-employed, and unemployed individuals
- **Default Rate (%) by Employment Type**: Bar chart highlighting higher risk among unemployed and part-time workers
- **Average Loan Amount by Age Group**: Line chart identifying highest loan amounts among adults and middle-aged individuals
- **Default Rate (%) by Year**: Line chart revealing peak default in 2015 followed by a downward trend

### 🔹 Page 2: Applicant Demographics & Financial Profile
- **Median Loan Amount by Credit Score Category**: Line chart showing higher loan values among low-credit-score applicants
- **Average Loan Amount (High Credit) by Age Group & Marital Status**: Donut chart identifying single adults with high credit as top borrowers
- **Total Loan (Adults) by Credit Score Bins**: Line chart highlighting medium credit scores as having the highest total loan volume
- **Loan (Middle-Aged Adults) by Mortgage/Dependents**: Bar chart comparing loan amounts for individuals with/without dependents
- **Number of Loans by Education Type**: Line chart showing Bachelor's degree holders with the most loans

### 🔹 Page 3: Financial Risk Metrics
- **YOY Loan Amount Change by Year**: Line chart showing fluctuating loan volumes, with a peak in 2018
- **YOY Default Loans Change by Year**: Line chart revealing a decline in defaults post-2015
- **YOY Loan Amount by Credit Score Bins & Marital Status**: 📊 *Ribbon Chart* visualizing changes in loan amounts across years segmented by marital status and credit score category
- **Loan Amount by Income Bracket and Employment Type**: 🧩 *Decomposition Tree* used to explore the relationship between income groups and employment types

---

## 📊 Key Visuals

- **Line Charts**
  - Loan Amount by Purpose
  - Average Income by Employment Type
  - Default Rate by Employment Type
  - Average Loan Amount by Age Group
  - Median Loan Amount by Credit Score Category
  - Total Loan (Adults) by Credit Score Bins
  - Loan (Middle Age Adults) by have Mortgage/Dependent
  - Loan Count by Education Type
  - YOY Loan Amount Change by Year
  - YOY Default Loans Change by Year
- **Bar Chart**
  - Loan (Middle Age Adults) by have Mortgage/Dependents
- **Donut Chart**
  - Average Loan Amount by Age Group & Marital Status (High Credit)
- **Ribbon Chart**
  - YOY Loan Amount by Credit Score Bins & Marital Status
- **Decomposition Tree**
  - Loan Amount by Income Bracket and Employment Type

---

## 📂 Data Sources

| Source                          | Description                                                              |
|---------------------------------|--------------------------------------------------------------------------|
| Loan_default.csv                | Csv dataset containing applicant, loan, income, and credit details       |
| Loan Insights Dashboard.pbix    | Power BI file with visuals, filters, DAX calculations, and data modeling |

---

## 🛠️ Tools & Technologies

- **Power BI Desktop** – Dashboard design and visualizations
- **DAX (Data Analysis Expressions)** – Custom KPIs and calculations
- **Power Query Editor** – Data transformation and shaping
- **Csv** – Base data source

---

## 📷 Dashboard Preview

Screenshots:

<img width="895" height="506" alt="dashboard-preview-one" src="https://github.com/user-attachments/assets/00ae50c2-7d11-4596-afbb-a0f34a905467" />


<img width="901" height="508" alt="dashboard-preview-two" src="https://github.com/user-attachments/assets/cbfdbdde-2750-488a-8905-a235dc4875a2" />

<img width="898" height="505" alt="dashboard-preview-three" src="https://github.com/user-attachments/assets/c230e92e-9416-4f5c-b34c-183cf7f6c677" />

---

## 🎥 Demo



https://github.com/user-attachments/assets/fef988e7-5592-4c4f-b9c5-780404481dde


---

## 🚀 Usage

1. Download or clone the repository.
2. Open `Loan Insights Dashboard.pbix` in Power BI Desktop.
3. Reconnect or update the data source if necessary.
4. Explore pages and visuals using slicers and filters (e.g., age, employment, credit score).
5. Use the insights to improve risk modeling, product targeting, or credit decision-making.

---

## 📌 Use Case Highlights

- Understand borrower risk by employment type and income group
- Identify loan approval patterns across credit score ranges
- Analyze demographic impact on borrowing behavior
- Track trends in loan growth and defaults across multiple years
- Perform detailed breakdowns with the Decomposition Tree visual
