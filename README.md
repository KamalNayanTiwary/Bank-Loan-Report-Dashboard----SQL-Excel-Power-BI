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

### 🔹 Step 2: SQL Querying  
KPIs calculated with SQL queries in **SSMS**  

Examples:  
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

## 📄 Terminologies Used  

Some critical fields in dataset:  

- **Loan ID** – Unique identifier per loan  
- **Grade & Sub Grade** – Borrower risk classification  
- **DTI** – Debt-to-Income ratio (borrower risk measure)  
- **Purpose** – Reason for loan (Debt consolidation, Business, etc.)  
- **Home Ownership** – RENT / MORTGAGE / OWN → stability indicator  
- **Loan Status** – Fully Paid, Current, Charged-Off  

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
