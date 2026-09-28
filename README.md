# Sales-Management-Worflow-and-Performance-Analytics

Synthexa Global Solutions — Sales Management Workflow & Analytics System

🚀 Project Overview
🚨 In fast-paced sales environments, capturing transactional data quickly and accurately is vital for strategic decision-making. However, Synthexa Global Solution's sales-tracking workflow relied on fragmented, unvalidated data collection methods. Sales representatives submitted their daily transaction logs via disparate formats, including email, chat apps, and unstructured spreadsheets.This ad-hoc workflow created severe operational bottlenecks and financial risks such as:

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
                          GOOGLE SHEET                                            
                               |                                                          
                               ▼                                                          
                       DISTRIBUTER DATABASE                                               
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
                       (Sales interface)
                               │
                               ▼
                       Credit and Debit
                       (Balance sheet)
                               |
                               ▼
                         Rep Metrics
                    (Sales rep performance)
                             
                               ▼
                           RAW DATA
                    Staging / Organization
                               │
                               ▼
                         CLEAN DATA
              Standardized Analytical Dataset
                               │
                               ▼
                      ANALYTICAL ENGINE
                 PivotTables + Calculations
                               │
              ┌────────────────┼────────────────┐
              ▼                ▼                ▼
        Sales Analysis   Payment Analysis   KPI Analysis
              │                │                │
              └────────────────┼────────────────┘
                               ▼
                     MANAGEMENT DASHBOARD
                               │
                               ▼
                     MANAGEMENT INSIGHTS

This architecture intentionally separates operations from analytics.

The person entering sales data does not need to manually manipulate the management dashboard.

Instead, the workflow is designed so that new operational records can flow through the system and become available for analysis.

---

🎯 The Business Problem

---

🔄 How the Workflow Works

1. Operational Data Capture

Google Sheets

Google Sheets acts as the operational interface.

Sales information can be entered as transactions occur.

The dataset captures:

- Sales Representative
- Distributor
- Product
- Quantity
- Current Tier
- Tier at Purchase
- Supply Date
- Expected Payment Date
- Payment Status
- Amount Due
- Unit Price
- Total Price

This allows the operational side of the business to work with a simple data-entry environment without directly interacting with the analytical calculations.

---

2. Automated Data Flow

The operational Google Sheet is connected to the analytical workbook through a published data feed.

This creates a workflow in which:

New transaction entered
        ↓
Google Sheets updated
        ↓
Published data source updated
        ↓
WPS imports the updated data
        ↓
Analytical layers update
        ↓
Dashboard reflects new information

The WPS import was configured to refresh automatically, allowing the management workbook to receive updated source information without requiring the entire workflow to be rebuilt manually.

---

3. Dumped Data Layer

"Dumped_Data"

The dumped layer represents the incoming source data.

Its purpose is preservation.

Rather than immediately manipulating the source information, the system maintains a layer representing what was received from the operational source.

This provides a useful separation between:

incoming data

and

processed data.

---

4. Raw Data Layer

"Raw_Data"

The raw layer acts as the staging environment.

Data is organized into a consistent tabular structure before entering the analytical cleaning layer.

This creates a clear progression:

Dumped Data
     ↓
Raw Data
     ↓
Clean Data

Each stage has a defined responsibility rather than mixing source data, transformations, and reporting logic together.

---

5. Clean Data Layer

"Clean_Data"

This is the system's analytical data layer.

The objective is not simply to make the data visually clean.

Each field is converted to its expected analytical data type.

Field| Expected Type
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

📊 Analytical Layer

Once the data has been standardized, it enters the analytical layer.

The system uses PivotTables and spreadsheet calculations to transform transaction-level records into management-level metrics.

---

📈 Sales Performance

The system analyzes sales performance by representative using metrics including:

- Total Revenue
- Quantity Sold
- Distributor Coverage
- Target
- Achievement
- Debt Recovery

This allows management to move from individual transaction records to representative-level performance.

---

🎯 Target Management

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

💰 Revenue & Payment Workflow

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

📦 Product & Distributor Analysis

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

---

📁 Project Structure

OG-Enterprise-Sales-Workflow/
│
├── README.md
│
├── Data/
│   └── sales_data.csv
│
├── Workflow/
│   └── OG_Enterprise_Sales_Workflow.xlsx
│
├── Analysis/
│   └── exploratory_data_analysis.ipynb
│
├── SQL/
│   └── sales_analysis.sql
│
└── Images/
    └── management_dashboard.png

---

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

Aspiring Data Analyst focused on data analytics, business intelligence, data workflows, and practical data-driven solutions.

My portfolio focuses on building projects that demonstrate not only technical skills, but also the ability to translate real business processes into structured analytical systems.

---

⭐ Project Principle

«Don't just build a dashboard. Build the system that makes the dashboard trustworthy.»
