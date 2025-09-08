# 🏦 Bank Loan Report Dashboard  

📌 **Project Objective**  
To build a **comprehensive Bank Loan Analysis Dashboard in Power BI**, powered by **MS SQL Server queries**, with the goal of delivering **end-to-end visibility** into:  

- Loan Applications (total, MTD, MoM)  
- Funded Amounts & Repayments  
- Interest Rates & Debt-to-Income Ratios (DTI)  
- Good vs Bad Loan Performance  
- Loan Status Distribution  
- Borrower Segmentation (State, Term, Purpose, Employment, Home Ownership)  

The project provides **actionable insights** to banks and financial institutions, enabling them to:  

✔ Monitor lending performance in real-time  
✔ Identify repayment risks early  
✔ Optimize portfolio health & profitability  
✔ Strengthen customer targeting strategies  

---

## 📊 Live Dashboard  

- **Summary Dashboard** – Loan KPIs (Applications, Funded Amount, Amount Received), Good vs Bad Loans, Loan Status breakdown  
- **Overview Dashboard** – Monthly trends, regional performance (state), term analysis, purpose of loans, employment length, and home ownership insights  
- **Details Dashboard** – Loan-level data table with filters (State, Grade, Loan Status) for drill-down analysis  

🔗 You can explore it **Live** here: [View Dashboard](#)  

---

## 📌 Project Background  

Banking institutions deal with thousands of loan applications every month. Each loan brings:  
- **Opportunity** (interest income, cross-selling potential)  
- **Risk** (default, charge-off, fraud)  

Without proper monitoring, banks struggle to answer key questions like:  
- *Are loan applications increasing or declining?*  
- *Which segments are most profitable?*  
- *Where are the highest risks (state, employment, grade)?*  
- *How are repayments performing against funded amounts?*  

This project addresses these pain points through **data-driven dashboards** that combine SQL-based KPIs with interactive Power BI reports.  

---

## 📊 Dashboard Overview  

I designed **3 dashboards** for a complete analysis:  

---

### 1️⃣ Summary Dashboard – **Portfolio Health & KPIs**  
![Summary Dashboard](Screenshot1.png)  

This is the **executive-level view** providing quick answers to: *“How are we performing overall?”*  

**Key Metrics (with MTD vs PMTD comparison):**  
- 📑 **Total Loan Applications:** 38.6K overall | 4.3K this month (**-6.9% MoM**)  
- 💰 **Total Funded Amount:** ¥435.8M overall | ¥54M this month (**-13% MoM**)  
- 💵 **Total Amount Received:** ¥473.1M overall | ¥98.1M this month (**-15.8% MoM**)  
- 📈 **Average Interest Rate:** 12.0% overall | 12.4% this month (**+3.5% MoM**)  
- 📊 **Average DTI:** 13.3% overall | 13.7% this month (**+2.7% MoM**)  

**Good vs Bad Loans:**  
- ✅ Good Loans (Fully Paid + Current) → Higher share → Indicating portfolio strength  
- ❌ Bad Loans (Charged-Off) → Lower share → Still critical to monitor  

**Loan Status Grid:**  
- Loan count, repayment, funded amount, Avg Int Rate & Avg DTI → segmented by status  

📌 **Business Value:**  
- Helps executives monitor health **at a glance**  
- Identifies **declines in applications, funding, and repayments** early  
- Supports **risk-adjusted decision-making**  

---

### 2️⃣ Overview Dashboard – **Segmentation & Trends**  
![Overview Dashboard](Screenshot2.png)  

This dashboard answers: *“Where are the opportunities & risks?”*  

**Visual Insights:**  
- 📅 **Monthly Trends (Line Chart):** Identifies seasonal spikes, lending cycles  
- 🌍 **State-wise Lending (Map):** Detects regional demand concentration  
- 🕒 **Loan Term Analysis (Donut):** 36 vs 60-month loan preferences  
- 👔 **Employment Length (Bar):** Stability effect on approval & repayment  
- 🎯 **Purpose Breakdown (Bar):** Debt consolidation, credit card, small business, etc.  
- 🏡 **Home Ownership (Tree Map):** Rent vs Mortgage vs Own distribution  

📌 **Business Value:**  
- Regional teams can **customize lending strategies**  
- Marketing can focus on **high-demand loan purposes**  
- Risk teams can track **unstable employment segments**  

---

### 3️⃣ Details Dashboard – **Loan-Level Drilldown**
![Details  Dashboard](Screenshot1.png)  

A **tabular view** with filters for:  
- State, Loan Grade, Good vs Bad Loan  

**Columns Include:**  
Loan ID | Purpose | Home Ownership | Grade | Sub Grade | Issue Date | Loan Amount | Interest Rate | Installments | Amount Received  

📌 **Business Value:**  
- Enables **loan officers & analysts** to drill down into specifics  
- Allows **auditing & exception management**  
- Provides **transparency across all loans**  

---

## ⚙️ Technical Process  

### 🔹 Step 1: Data Import  
- Raw dataset imported into **MS SQL Server**  
- Tables structured and cleaned  

---

### 🔹 Step 2: SQL Querying  
KPIs calculated with SQL queries in **SSMS**  

Example Queries:  

```sql
-- Total Applications
SELECT COUNT(id) AS Total_Applications 
FROM bank_loan_data;

-- MTD Applications
SELECT COUNT(id) AS MTD_Applications 
FROM bank_loan_data
WHERE MONTH(issue_date) = 12;

-- Good Loan Percentage
SELECT 
 (COUNT(CASE WHEN loan_status IN ('Fully Paid','Current') THEN id END)*100.0)/
 COUNT(id) AS Good_Loan_Percentage
FROM bank_loan_data;
```
➡️ **[Full SQL Queries Here](./Query%20Doc.docx)**  

---

## 🔹 Step 3: Power BI Integration  

- Data connected via **Direct Query** for real-time sync  
- Relationships modeled  
- DAX applied where necessary  

---

## 🔹 Step 4: Dashboard Development  

- KPI cards  
- Line charts  
- Bar charts  
- Maps  
- Donut charts  
- Tree maps  
- Filters & slicers added for interactivity  

---

## 🔹 Step 5: Validation  

- Cross-checked SQL outputs with Excel summaries  
- Ensured KPI consistency  

---

## 🚨 Business Problems Solved  

- 📉 Identified declining loan activity (**-6.9% MoM applications**)  
- ✅ Confirmed Good Loan dominance, but flagged risks in Bad Loans  
- 🌍 Highlighted geographic variations → Targeted regional marketing  
- 👔 Employment data → Stable jobs = stronger repayment  
- 🏡 Home ownership trends → Mortgage group dominates → stable customers  
- 🎯 Debt Consolidation & Credit Card loans = primary loan purpose  

---

## 🔎 Insights & Recommendations  

### 📌 Marketing Strategy  
- Focus campaigns in high-demand states  
- Promote loan products for top purposes (Debt Consolidation, Credit Card)  

### 📌 Risk Management  
- Stricter checks for unstable employment segments  
- Monitor Bad Loan borrowers → enhance collection strategy  

### 📌 Customer Targeting  
- Offer refinancing to Good Loan borrowers (high repayment track record)  
- Customize offers by Home Ownership status  

### 📌 Product Strategy  
- 60-month loans carry higher risk → monitor carefully  
- Review underperforming segments → optimize portfolio  

---

## 📄 Bank Loan Report  

Bank loans are a crucial financial tool that enable individuals and businesses to achieve their goals and manage financial needs. However, it is equally important for banks to **track, analyze, and monitor loans** to ensure profitability and minimize risks.  

This **Bank Loan Report Dashboard** was built to:  
- Monitor overall loan applications and repayments  
- Track **Funded Amounts, Amounts Received, Interest Rates, and DTI**  
- Compare **Month-to-Date (MTD) vs Previous Month-to-Date (PMTD)** performance  
- Analyze **Good vs Bad Loans** for risk assessment  
- Provide segmentation by **State, Loan Purpose, Term, Employment Length, and Home Ownership**  

### 🔑 Why Banks Analyze Loan Data?  
- **Risk Assessment** → Evaluate borrower creditworthiness and predict defaults  
- **Decision-Making** → Approve/deny loans based on data-driven insights  
- **Portfolio Management** → Monitor loan performance & optimize terms  
- **Fraud Detection** → Detect unusual loan activity and prevent losses  
- **Regulatory Compliance** → Generate reports for KYC, HMDA, and other compliance needs  
- **Customer Insights** → Understand borrower behavior and improve loan products  
- **Profitability Analysis** → Assess margins from interest income vs defaults  
📊 By consolidating these insights into **interactive Power BI dashboards**, banks can make faster, smarter, and data-driven lending decisions.  

➡️ **[Read Full Report Here](./BANK%20LOAN%20REPORT.docx)**  

---

## 🎤 Project Presentation (PPT)  

To complement the dashboard and SQL queries, I designed a **professional presentation** that explains the project in a structured way.  

The PPT is divided into two main parts:  

### 🔹 Part 1: MS SQL Server (Backend Analysis)  
- Imported raw bank loan dataset into **SQL Server**  
- Created **database & tables** for structured storage  
- Wrote **SQL queries** to calculate KPIs:  
  - Total Applications, Funded Amount, Amount Received  
  - Average Interest Rate & Average DTI  
  - Good Loan vs Bad Loan (Applications, Funded Amount, Amount Received)  
- Compared SQL outputs with **Power BI & Excel** for validation  

### 🔹 Part 2: Power BI Dashboards (Visualization)  
The presentation highlights **three dashboards** designed in Power BI:  

1. **Summary Dashboard**  
   - KPIs: Applications, Funded Amount, Amount Received (MTD vs PMTD)  
   - Good vs Bad Loan KPIs  
   - Loan Status Grid with breakdown of Loan Count, Funded Amount, Amount Received, Interest Rate, and DTI  

2. **Overview Dashboard**  
   - Monthly Trends (line chart for seasonality)  
   - Regional Analysis (map by state)  
   - Loan Term Analysis (donut chart)  
   - Employment Length Analysis (bar chart)  
   - Loan Purpose Breakdown (bar chart)  
   - Home Ownership Analysis (tree map)  

3. **Details Dashboard**  
   - Loan-level table with filters (State, Loan Grade, Loan Status)  
   - Columns: Loan ID, Purpose, Grade, Sub-Grade, Term, Funded Amount, Interest Rate, Installments, Amount Received  
   - Helps with **drill-down analysis** and borrower profiling  

### 🎯 Purpose of the PPT  
- Acts as a **step-by-step walkthrough** of the entire project  
- Useful for **interviews, client demos, or academic presentations**  
- Clearly explains the **problem statement, methodology, dashboards, and insights**  

➡️ **[View Full PPT Here](./Bank%20Loan%20PPT%20Power%20BI.pptx)**  

---

## 📄 Terminologies Used  

Some key fields from the dataset and their purpose:  

- **Loan ID** → Unique identifier for each loan application.  
- **Address State** → Borrower’s location, useful for regional analysis.  
- **Employee Length** → Years of employment; stability indicator for repayment.  
- **Grade & Sub Grade** → Credit risk classification; used to set loan terms.  
- **Home Ownership** → RENT / MORTGAGE / OWN; reflects borrower stability.  
- **Issue Date** → Loan origination date; used for maturity & tracking.  
- **Loan Status** → Current state (Fully Paid, Current, Charged Off).  
- **Purpose** → Reason for loan (Debt consolidation, Business, Education).  
- **Term** → Duration of the loan (36/60 months).  
- **Annual Income** → Borrower’s reported yearly income.  
- **DTI (Debt-to-Income)** → Ratio of monthly debt to income; repayment capacity.  
- **Interest Rate** → Annual cost of borrowing as a percentage.  
- **Installment** → Fixed monthly repayment (principal + interest).  
- **Loan Amount** → Total borrowed sum (principal).  

➡️ **[Full Terminologies Here](./Terminologies%20in%20Data.docx)**  

---

## ✅ Key Learnings  

- SQL is critical for **KPI accuracy** before dashboarding  
- Power BI enables **executive + detailed views** in one project  
- Data validation across SQL, Power BI, and Excel ensures **consistency**  
- Business insights are only as strong as the **data cleaning & preparation**  

---

## 🚀 Future Improvements  

- Add **predictive analytics (ML models)** → Predict default risk  
- Automate **ETL pipeline** from SQL to Power BI  
- Integrate **Real-Time Power BI Service alerts** for KPI changes  
- Expand dataset → Include **income ranges, FICO scores, and demographics**  

---

## 🛠️ Tech Stack  

- **MS SQL Server** – Data storage & processing  
- **SSMS** – Query development  
- **Microsoft Power BI** – Visualization & interactivity  
- **Excel** – Cross-validation & backup analysis  

---

## 👨‍💻 Author & Contact  

**Kamal Nayan Tiwary**  
*Data Analyst*  

📧 Email: **kamalnayantiwary73@gmail.com**  
🔗 [LinkedIn](https://www.linkedin.com/in/kamal-nayan-tiwary-2022-2026-/)  


