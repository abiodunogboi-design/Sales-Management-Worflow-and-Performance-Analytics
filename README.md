# Sales-Management-Worflow-And-Performance-Analytics

Synthexa Global Solutions — Sales Management Workflow & Analytics System

🚀 This project is an interactive sales management dashboard built in Excel to analyze sales performance, customer payments, outstanding debts, and target achievement. Using data cleaning, formulas, pivot tables, slicers, and dynamic KPIs, I transformed raw sales records into actionable insights for monitoring both sales representatives and distributors. The dashboard is designed as a practical business tool that supports daily performance tracking and data-driven decision-making.

---

🎯 The Business Problem

---
🚨 In fast-paced sales environments, capturing transactional data quickly and accurately is vital for strategic decision-making. However, Synthexa Global Solution's sales-tracking workflow relied on fragmented, unvalidated data collection methods. Sales representatives submitted their daily transaction logs via disparate formats, including email, chat apps, and unstructured spreadsheets.This ad-hoc workflow created severe operational bottlenecks and financial risks

**Severe Data Corruption & Manual Errors:** Representatives frequently entered invalid SKUs, left critical data fields blank, or accidentally over-wrote orders.

**The "Lag Time" Bottleneck:** Because data wasn't centralized or live, operations managers had to spend hours every week manually aggregating entries, cleaning formatting inconsistencies, and manually auditing calculation metrics.

**Blind Leadership Decision-Making:** A growing sales operation can quickly become difficult to manage when information is scattered across transaction records. For Synthexa Global Solutions. Management needs to know:
- What has been sold?
- Who sold it?
- How much was sold?
- Which distributors purchased products?
- Which products are generating the most revenue?
- How are sales representatives performing against their targets?
- How much money has been collected?
- How much is still outstanding?
- Which payments are overdue?
- How is performance changing over time?.
  
  **Issue:** A conventional spreadsheet containing raw transactions can answer some of these questions, but it does not provide a complete operational-to-management workflow. Also, executive dashboards could only be updated at the end of the week or month. This lack of real-time visibility meant leadership was constantly looking in the rearview mirror, unable to pivot strategies or spot dropping conversion rates when they actually occurred.
💡 The App aims to eliminate this operational friction, this project re-engineered the entire collection pipeline into a self-contained, interactive Excel application.The objective was to create a unified, bulletproof interface that balances two distinct user experiences:

**For Sales Reps:** A streamlined, app-like input interface that strictly enforces data integrity rules at the exact moment of entry—making it physically impossible for a user to break the underlying math.

**For Leadership:** A zero lag, automated engine that processes those raw entries instantly through a matrix of advanced formulas, immediately feeding a live executive KPI board for real time strategic steering upon refresh.
  This project addresses that gap by creating a structured system connecting data entry, processing, analysis, and reporting.

The Synthexa Global Solutions Sales Management Workflow & Analytics System is an end-to-end business data workflow designed to connect sales operations, data collection, data processing, performance monitoring, and management reporting in one system. 

The project goes beyond building a static dashboard.

It was designed as a workflow system in which sales information can move from the point of operational entry through structured data processing and ultimately into management-level analytics.

The system connects two sub-systems:

- **Sales Operations (Google sheet):** Distributor Tiers assignment(discounting purpose) → Sales Data Capture → Data Staging → Balance Sheet → Sales Rep KPI Calculation → Sales Rep Performance Analysis.
  
- **Analytics (WPS):** Dumped data → Data Staging → Data Cleaning → KPI Calculations → Executive Dashboard.

The objective is to create a repeatable workflow where operational data can continuously flow into the analytical environment, reducing manual intervention while giving management visibility into sales performance, target achievement, customer activity, and debt recovery.

---

🏗️ System Architecture

                          Google Sheet                                          
                               |                                                          
                               ▼                                                          
                       Distributor Database                                          
      (Tiers, Sales rep and discount automatic assignment)                                
                               │                                                          
                               ▼                                                          
                         All Price List                                                   
               (Source of truth for all tier pricing)                                     
                               |                                                          
                               ▼                                                          
                         Sales Operation                                                  
                               |                                                          
                               ▼                                                          
                     Operational Data Entry ─────────────────────────────────────────── **WPS**
                       (Sales interface)               (Published to web)                  |
                               │                                                           ▼
                               ▼                                                       Dumped Data
                           Rep Metrics                                                     |
                    (Sales rep performance)                                                ▼
                                                                                        Raw Data
                                                                                  (Staging / Organization)
                                                                                           |
                                                                                           ▼
                                                                                      Cleam Data  
                                                                              (Standardized Analytical Dataset)
                                                                                           |
                                                                                           ▼
                                                                                     Analytical Engine
                                                                                 (PivotTables + Calculations)
                                                                                           |
                                                                          ┌────────────────┼────────────────┐
                                                                          ▼                ▼                ▼
                                                                   Sales Analysis    Payment Analysis    KPI Analysis
                                                                          |                |                |
                                                                          └────────────────┼────────────────┘
                                                                                           ▼ 
                                                                                  Management Dashboard
                                                                                           |
                                                                                           ▼
                                                                                    MAnagement Insights

This architecture intentionally separates operations from analytics.

The person entering sales data does not need to manually manipulate the management dashboard.

Instead, the workflow is designed so that new operational records can flow through the system and become available for analysis.

---

🔄 **How the Workflow Works**

---

**1. Operational Data Capture**

Google Sheets
<img width="959" height="352" alt="Screenshot 2026-09-23 143741" src="https://github.com/user-attachments/assets/4dc5a6b2-75e0-492d-a37a-5e5d1a07635d" />
<img width="917" height="345" alt="Screenshot 2026-09-23 143816" src="https://github.com/user-attachments/assets/aace21a7-6162-4405-91ed-15651ca1c4eb" />

Google Sheets acts as the operational interface.

**Interract with the google sheet interface [here](https://docs.google.com/spreadsheets/d/11vOJej1EhdzehAz3htSsr2jR4gbEbQv5AfkF0_2Q5Wo/edit?usp=sharing)**

Sales information can be entered as transactions occur.

The dataset captures:

- Sales Representative: The name of the sales rep executing the order
- Distributor: The Distributor raising the order
- Product: The products raised by the distributor
- Quantity: The quantity of products raised by the distributor
- Current Tier: The discount percentage tier the distributor is currently on
- Tier at Purchase: The discout percentage tier the distributor was at the time of purchase
- Supply Date: The date the distributor received their order
- Expected Payment Date: The date the distributor is expected to pay for orders received
- Payment Status: Paid/Unpaid as of current date
- Due For Payment: shows whether the expected payment date has passed
- Unit Price: The price per unit product
- Total Price: The total cost of the order.

This allows the operational side of the business to work with a simple data-entry environment without directly interacting with the analytical calculations.

 **Technicality:**
 - "Sales Reprecentative" and "Distributor" are both dropdown from a list while each product are made as column to reduce typographic error. Sales rep only needs to type in the quantity purchased under each product.
 - The sales interface functions like an app that records and process orders. Therefore, it wasn't designed to look like the conventional data structure. However, it was collapsed into the conventional data structure in the analytics data tab to enhance analytics uning a query that splits and flattens the products columns ***C to S*** into a a single column with the header quantity because each of the product column contains the respective quantity ordered.

<img width="788" height="345" alt="Screenshot 2026-09-23 143834" src="https://github.com/user-attachments/assets/2474e115-1632-46ad-b988-ce4c6d317a3f" />

  ```
   =ARRAYFORMULA(
  QUERY(
    SPLIT(
      FLATTEN(
        Sales!A2:A&"♦"&
        Sales!B2:B&"♦"&
        Sales!C$1:S$1&"♦"&
        Sales!C2:S&"♦"&
        Sales!T2:T&"♦"&
        Sales!U2:U&"♦"&
        Sales!V2:V&"♦"&
        Sales!W2:W&"♦"&
        Sales!Y2:Y&"♦"&
        Sales!Z2:Z
      ),
      "♦"
    ),
    "where Col1 is not null and Col3 is not null and Col4 is not null",
    0
  )
)
```

 -  Each distributor is automatically assigned a tier based on their total quantity purched history. Any distributor that has less than 20,000 units in total quantity purchased in assigned a tier 1 with 0% discount on all purchase. Distributors with more than 20,000 and less than 50,000 units in total quantities purchased is assigned a tier 2 with 1.5% discount on all subsequent purchases upon attaining the tier, distributors with more than 50,000 and less than 100,000 units in total quantities purchased are assigned a tier 3 with 3% discount on all subsequent purchases upon attaining the tier, while distributors with over 100,000 units in total quantities purchased are assigned tier 4 with 5% discount on all subsequent purchases upon attaining the tier. This is achieved using the formula:

```

=XLOOKUP(SUMPRODUCT((Sales!$B$2:$B$801=$A17) * Sales!$C$2:$S$100000), $E$2:$E$5, $F$2:$F$5, "Tier 1", -1)

```
<img width="959" height="373" alt="image" src="https://github.com/user-attachments/assets/8be8037c-c6ff-4cdd-b80c-2618aad408c2" />


**2. Automated Data Flow**

The operational Google Sheet is connected to the analytical workbook through a published data feed.

This creates a workflow in which:

New transaction entered
        → 
Google Sheets updated
        → 
Published data source updated
        → 
WPS imports the updated data
        → 
Analytical layers update
        → 
Dashboard reflects new information

The back-end workbook utilizes an automated data connection to pull live records from the operational layer, eliminating manual data handling. Once imported, the raw staging data passes through automated cleaning formulas that programmatically standardize fields and cast them into their appropriate analytical data types."

Sales Rep| Text

Distributor| Text

Product| Text

Quantity| Numeric

Current Tier| Text

Tier at Purchase| Text

Supply Date| Date

Expected Payment Date| Date

Paid| Text

Due for Payment| Text

Unit Price| Numeric

Total Price| Numeric

For example, imported quantities that arrived as text are converted into numeric values using "VALUE()".

Imported dates are converted into genuine date values using "DATEVALUE()".

This is important because downstream aggregation, PivotTables, calculations, and date filtering depend on the correct underlying data types.

---

***📊 Analytical Layer***

Once the data has been standardized, it enters the analytical layer.

The system uses PivotTables and spreadsheet calculations to transform transaction-level records into management-level metrics.

<img width="953" height="388" alt="Screenshot 2026-09-23 144420" src="https://github.com/user-attachments/assets/a928a588-c851-47cb-b1fb-224bdd159bc5" />

---

**📈 Sales Performance**

<img width="686" height="428" alt="Screenshot 2026-09-23 143036" src="https://github.com/user-attachments/assets/81c1a17d-83d0-4a13-a16c-53a1cc88d2f8" />

The system analyzes sales performance by representative using metrics including:

- Total Revenue
- Quantity Sold
- Distributor Coverage
- Target
- Achievement
- Debt Recovery

This allows management to move from individual transaction records to representative-level performance.

---

**🎯 Target Management**

Each sales representative has a monthly sales target of:

$5,000,000

The system is designed to recognize that this is a monthly target, rather than an all-time target.

Therefore:

Monthly Target
= $5,000,000 per representative

For multiple months:

Period Target
= $5,000,000 × Number of Months

This allows target achievement to remain meaningful when management changes the reporting period.

---

**💰 Revenue & Payment Workflow**

The system does not stop at sales generation.

Because the sales representatives are also responsible for debt recovery, payment information forms part of the performance workflow.

The system therefore tracks:

- Total Sales
- Paid Transactions
- Amount Collected
- Amount Due
- Payment Status
- Debt Recovery

This connects sales generation with cash collection.

That is an important distinction between a simple sales dashboard and a sales management workflow.

---

**📦 Product & Distributor Analysis**

The workflow also transforms transaction records into product and distributor intelligence.

Management can analyze:

Products

- Quantity sold
- Revenue generated
- Product contribution
- Sales trends

Distributors

- Number of distributors served
- Distributor purchasing activity
- Revenue generated
- Sales representative relationships

The system distinguishes between transaction volume and unique distributor count so repeated purchases from the same distributor are not incorrectly treated as multiple customers.

---

📅 Time-Based Workflow

Every transaction contains date information that allows the system to analyze performance across time.

The workflow supports analysis by:

- Date
- Month
- Year
- Reporting period

This allows management to move from:

overall performance

to:

yearly performance

to:

monthly performance

and eventually to more granular periods.

For example, month values can be extracted from standardized dates using:

=TEXT(A2,"mmmm")

---

🎛️ Interactive Management Reporting

The final stage of the workflow is the management dashboard.

The dashboard is designed to allow users to investigate the underlying business information rather than simply view static numbers.

Potential filtering dimensions include:

- Sales Representative
- Distributor
- Product
- Current Tier
- Payment Status
- Year
- Month
- Date

This creates an interactive analytical workflow:

Management Dashboard
        ↓
Select Year
        ↓
Select Month
        ↓
Select Sales Representative
        ↓
Investigate Sales / Products / Distributors / Payments

---

📊 Dashboard KPIs

The management dashboard brings together key indicators such as:

- Total Sales
- Total Quantity Sold
- Target
- Achievement %
- Distributor Coverage
- Debt Recovered
- Outstanding Amount

These KPIs provide a high-level view while the supporting charts allow users to investigate the underlying drivers.

---

🔁 Why This Is a Workflow System

The defining feature of this project is that it is not dependent on a one-time analysis.

A traditional portfolio project might follow:

CSV → Analysis → Dashboard

This project is designed differently:

Operational Entry
       ↓
Continuous Data Flow
       ↓
Data Staging
       ↓
Data Cleaning
       ↓
Data-Type Standardization
       ↓
Analytical Processing
       ↓
KPI Generation
       ↓
Interactive Dashboard
       ↓
Management Monitoring

The workflow can therefore continue operating as new transactions are introduced.

This makes the project closer to a small-scale business information system than a standalone visualization exercise.

---

🧠 Data Analytics Concepts Demonstrated

This project demonstrates practical understanding of:

Data Engineering Concepts

- Data ingestion
- Data staging
- ETL workflow design
- Data-type standardization
- Layered data architecture
- Automated data refresh

Data Analytics

- Aggregation
- KPI development
- Target vs achievement analysis
- Sales performance analysis
- Product analysis
- Distributor analysis
- Payment analysis
- Time-based analysis

Spreadsheet Analytics

- "TEXTSPLIT"
- "VALUE"
- "DATEVALUE"
- "SUMPRODUCT"
- "SUMIF"
- "UNIQUE"
- "FILTER"
- "XLOOKUP"
- PivotTables
- Charts
- Interactive filtering

Business Intelligence

- KPI design
- Management reporting
- Interactive dashboards
- Operational-to-management reporting
- Decision-support workflows

---

🛠️ Technology Stack

Layer| Technology
Operational Data Entry| Google Sheets
Data Transfer| Published Google Sheets data feed
Data Processing| WPS Spreadsheet
Data Cleaning| Spreadsheet formulas
Analytical Processing| PivotTables & formulas
Visualization| WPS Spreadsheet
Version Control / Portfolio| GitHub

🔮 Future Development

The current spreadsheet-based workflow provides the foundation for a more advanced business intelligence system.

Potential future iterations include:

- SQL database integration
- Automated data validation
- Automated anomaly detection
- Debt-aging analysis
- Automated overdue-payment alerts
- Sales forecasting
- Rep performance monitoring
- Profitability analysis
- Python-based ETL
- Tableau implementation
- Power BI implementation
- Automated management reporting
- Role-based operational and management interfaces

The long-term objective would be to evolve the system from a spreadsheet workflow into a scalable data-driven sales management platform.

---

💼 What This Project Demonstrates

This project demonstrates my ability to approach analytics as a business workflow problem, rather than simply a chart-building exercise.

I designed the system around a fundamental principle:

«Operational data should flow through a controlled process before it becomes management information.»

The project therefore considers not only:

"What does the data say?"

but also:

"Where does the data come from?"
"How is it transformed?"
"How is data quality maintained?"
"How are business rules applied?"
"How does management consume the information?"

That workflow perspective is the core of the project.

---

👤 Author

Sunday Ogboi

Data Analyst focused on data analytics, business intelligence, data workflows, and practical data-driven solutions.

My portfolio focuses on building projects that demonstrate not only technical skills, but also the ability to translate real business processes into structured analytical systems.

---

⭐ Project Principle

«Don't just build a dashboard. Build the system that makes the dashboard trustworthy.»
