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

---

### Steps followed
Step 1: Load data into Power BI Desktop, dataset is a csv file.
Step 2: Open Power Query Editor & in view tab under Data preview section, check "column distribution," "column quality," & "column profile" options.
Step 3: Since by default, profile will be opened only for 1000 rows, select "column profiling based on entire dataset."
Step 4: It was observed that in none of the columns errors & empty values were present.

📌 DAX Formulas with Description & Purpose
1️⃣ Age Groups
Age Groups = 
IF('Loan_default'[Age] <= 19, "Teen",
IF('Loan_default'[Age] <= 39, "Adults",
IF('Loan_default'[Age] <= 59, "Middle Age Adults", "Senior Citizens")))
Groups customers into age-based segments for analyzing borrowing and default behavior.

2️⃣ Income Bracket
Income Bracket = 
SWITCH(TRUE(),
    'Loan_default'[Income] < 30000, "Low Income",
    'Loan_default'[Income] < 60000, "Medium Income",
    "High Income")
Categorizes applicants into income bands for demographic and financial insights.

3️⃣ Credit Score Bins
Credit Score Bins = 
IF('Loan_default'[CreditScore] <= 400, "Very Low",
IF('Loan_default'[CreditScore] <= 450, "Low",
IF('Loan_default'[CreditScore] <= 650, "Medium", "High")))
Groups credit scores into bins based on risk levels.

4️⃣ Year
Year = YEAR('Loan_default'[Loan_Date_DD_MM_YYYY].[Date])
Extracts year from loan date for YOY comparisons.

5️⃣ YOY Default Loans Change
YOY Default Loans Change = 
DIVIDE(
    CALCULATE(COUNTROWS(FILTER('Loan_default', 'Loan_default'[Default] = TRUE())),
              'Loan_default'[Year] = YEAR(MAX('Loan_default'[Loan_Date_DD_MM_YYYY]))) -
    CALCULATE(COUNTROWS(FILTER('Loan_default', 'Loan_default'[Default] = TRUE())),
              'Loan_default'[Year] = YEAR(MAX('Loan_default'[Loan_Date_DD_MM_YYYY])) - 1),
    CALCULATE(COUNTROWS(FILTER('Loan_default', 'Loan_default'[Default] = TRUE())),
              'Loan_default'[Year] = YEAR(MAX('Loan_default'[Loan_Date_DD_MM_YYYY])) - 1),
    0
) * 100
Calculates year-over-year change (%) in number of defaulted loans.

6️⃣ YOY Loan Amount Change
YOY Loan Amount Change = 
DIVIDE(
    CALCULATE(SUM('Loan_default'[LoanAmount]),
              'Loan_default'[Year] = YEAR(MAX('Loan_default'[Loan_Date_DD_MM_YYYY]))) -
    CALCULATE(SUM('Loan_default'[LoanAmount]),
              'Loan_default'[Year] = YEAR(MAX('Loan_default'[Loan_Date_DD_MM_YYYY])) - 1),
    CALCULATE(SUM('Loan_default'[LoanAmount]),
              'Loan_default'[Year] = YEAR(MAX('Loan_default'[Loan_Date_DD_MM_YYYY])) - 1),
    0
) * 100
Measures YOY change (%) in loan disbursement.

7️⃣ YTD Loan Amount
YTD Loan Amount = 
CALCULATE(
    SUM('Loan_default'[LoanAmount]),
    DATESYTD('Loan_default'[Loan_Date_DD_MM_YYYY].[Date]),
    ALLEXCEPT('Loan_default', 'Loan_default'[Credit Score Bins], 'Loan_default'[MaritalStatus])
)
Computes Year-To-Date loan total segmented by credit score and marital status.

8️⃣ Average Loan Amt (High Credit)
Average Loan Amt (High Credit) = 
AVERAGEX(
    FILTER('Loan_default', 'Loan_default'[Credit Score Bins] = "High"),
    'Loan_default'[LoanAmount]
)
Finds average loan amount for high credit score customers.

9️⃣ Loans by Education Type
Loans by Education type = 
COUNTROWS(FILTER('Loan_default', NOT(ISBLANK('Loan_default'[LoanID]))))
Counts number of loans grouped by education level.

🔟 Median by Credit Score Bins
Median by Credit score bins = 
MEDIANX('Loan_default', 'Loan_default'[LoanAmount])
Returns median loan amount for typical loan behavior analysis.

1️⃣1️⃣ Total Loan (Credit Bins)
Total Loan (Credit Bins) = 
CALCULATE(
    SUM('Loan_default'[LoanAmount]),
    'Loan_default'[Age Groups] = "Adults",
    ALLEXCEPT('Loan_default', 
              'Loan_default'[Age], 
              'Loan_default'[Age Groups], 
              'Loan_default'[CreditScore], 
              'Loan_default'[Credit Score Bins])
)
Total loan amount given to adult borrowers by credit bins.

1️⃣2️⃣ Total Loan (Middle Age Adults)
Total Loan (Middle Age Adults) = 
SUMX(
    FILTER('Loan_default', 'Loan_default'[Age Groups] = "Middle Age Adults"),
    'Loan_default'[LoanAmount]
)
Sum of loans issued to middle-aged adults.

1️⃣3️⃣ Average Income by Employment Type
Average Income by Employment type = 
CALCULATE(
    AVERAGE('Loan_default'[Income]),
    ALLEXCEPT('Loan_default', 'Loan_default'[EmploymentType])
)
Average income per employment group.

1️⃣4️⃣ Average Loan by Age Group
Average Loan by Age Group = 
AVERAGEX(
    VALUES('Loan_default'[Age Groups]),
    AVERAGE('Loan_default'[LoanAmount])
)
Average loan amount per age group.

1️⃣5️⃣ Default Rate by Employment Type
Default Rate by Employment type = 
VAR totalrecords = COUNTROWS(ALL('Loan_default'))
VAR DefaultCases = COUNTROWS(FILTER('Loan_default', 'Loan_default'[Default] = TRUE()))
RETURN
CALCULATE(
    DIVIDE(DefaultCases, totalrecords),
    ALLEXCEPT('Loan_default', 'Loan_default'[EmploymentType])
) * 100
Default percentage within each employment type.

1️⃣6️⃣ Default Rate by Year
Default Rate by Year = 
VAR totalloans = 
    CALCULATE(
        COUNTROWS('Loan_default'),
        ALLEXCEPT('Loan_default', 'Loan_default'[Year])
    )
VAR default = 
    CALCULATE(
        COUNTROWS(FILTER('Loan_default', 'Loan_default'[Default] = TRUE())),
        ALLEXCEPT('Loan_default', 'Loan_default'[Year])
    )
RETURN
DIVIDE(default, totalloans) * 100
Default rate for each year.

1️⃣7️⃣ Loan Amount by Purpose
Loan Amount by Purpose = 
SUMX(
    FILTER('Loan_default', NOT(ISBLANK('Loan_default'[LoanAmount]))),
    'Loan_default'[LoanAmount]
)
Total loan amount borrowed per purpose.

