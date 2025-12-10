# Intelligent Case Triage & Claims Insights Platform

An end-to-end **case management & analytics platform** built with:

- **Salesforce** – for case intake, routing, and dashboards  
- **Databricks** – for data engineering, feature creation, and ML  
- **Snowflake** – for analytics warehouse and SQL insights  
- **AI/ML** – for case classification, SLA risk scoring, and summaries  
- **SQL** – across Databricks + Snowflake for transformations & reporting  

The goal is to simulate how a real organization handles a high volume of support/claim cases, and how a Business/Data Analyst can design a workflow from **CRM → Data Platform → AI → Insights**.

---

## Business Problem

Organizations receive thousands of support/claim cases every month.  
Common pain points:

- Manual, inconsistent **triage and routing**
- Little to no visibility into **backlog, SLA breaches, and root causes**
- No intelligent way to **prioritize high-risk cases**
- Scattered data across CRM, spreadsheets, and reports

This project designs and prototypes an **Intelligent Case Triage Platform** that:

1. Captures cases in **Salesforce**
2. Exports and enriches data in **Databricks** using SQL + ML
3. Loads curated data into **Snowflake** as an analytics warehouse
4. Uses SQL & dashboards to deliver actionable insights

---

## High-Level Architecture

```text
Salesforce (Case Intake & Routing)
        ↓  CSV export
Databricks (Data Engineering + AI/ML)
        ↓  curated tables
Snowflake (Data Warehouse & Analytics)
        ↓
SQL queries, dashboards, & insights
