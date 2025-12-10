# Business Requirements Document (BRD)
## Intelligent Case Triage & Claims Insights Platform

## 1. Project Overview
Organizations that manage high volumes of support or claim cases struggle with manual triage, inconsistent routing, SLA breaches, and limited visibility into operational performance.

This project simulates an end-to-end intelligent case triage and analytics workflow using:

- Salesforce (case intake and routing)
- Databricks (data engineering and ML)
- Snowflake (analytics warehouse)
- SQL (transformations and analysis)
- AI/ML (classification and risk prediction)

## 2. Business Problem
Companies face challenges such as:

- Manual and inconsistent triage  
- Incorrect case routing  
- High SLA breach rates  
- Limited visibility into backlog trends  
- No early identification of risky cases  

This results in:

- Inefficiencies  
- Customer dissatisfaction  
- Delayed resolutions  
- Poor visibility for leadership  

## 3. Project Goals and Objectives

### Primary Goals
1. Automate case categorization and routing in Salesforce  
2. Clean, transform, and enhance data using Databricks  
3. Build ML models for case classification and SLA risk scoring  
4. Build Snowflake warehouse tables for analytics  
5. Deliver actionable insights using SQL  

### Success Measures
- Reduce manual routing by 50%  
- Improve routing accuracy by 30%  
- Predict SLA-risk cases with at least 70% accuracy  
- Provide KPI visibility across backlog, SLA, and case categories  

## 4. Scope

### In Scope
- Salesforce Case configuration  
- Routing flows and escalations  
- Synthetic case data generation  
- Databricks SQL transformations  
- ML classification and prediction  
- Snowflake warehouse tables  
- SQL analytics queries  
- Documentation and GitHub structure  

### Out of Scope
- Real PHI/PII data  
- Production-grade ML pipelines  
- API integrations between systems  
- Real-time dashboards  

## 5. Stakeholders and Actors

| Actor | Description |
|-------|-------------|
| Customer | Submits support/claim requests |
| Support Agent | Logs and updates cases in Salesforce |
| Claims Analyst | Works assigned cases |
| Supervisor | Monitors SLA and escalations |
| Data Engineer | Builds Databricks pipelines |
| Data Analyst | Queries Snowflake |
| ML Model | Generates predictions |
| Leadership | Uses insights and dashboards |

## 6. Use Cases

### Use Case 1: Case Intake
- Case is created in Salesforce  
- SLA timer begins  

### Use Case 2: Automatic Routing
- Case category determined by keywords  
- Case assigned to appropriate queue  

### Use Case 3: Escalation
- Case escalated if no activity before SLA deadline  

### Use Case 4: Data Processing (Databricks)
- Salesforce data exported as CSV  
- Databricks cleans and engineers data  

### Use Case 5: Machine Learning
- Model predicts case category  
- Model predicts SLA risk  

### Use Case 6: Analytics and Reporting (Snowflake)
- Curated data loaded into Snowflake  
- Queries return KPIs such as SLA breach rate, backlog size, etc.  

## 7. Functional Requirements

### Salesforce Requirements
1. Create Case fields (Category, SLA Target, Risk Score)  
2. Create Routing Queues  
3. Create Flows for:
   - Auto-categorization  
   - Auto-routing  
   - Escalations  
4. Build operational dashboards  
5. Export data as CSV  

### Databricks Requirements
6. Upload Salesforce CSV  
7. Clean and normalize data using SQL  
8. Engineer features such as description length and keywords  
9. Tr
