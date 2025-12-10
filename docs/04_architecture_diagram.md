# Architecture Overview
## Intelligent Case Triage & Claims Insights Platform

This document describes the high-level architecture of the Intelligent Case Triage & Claims Insights Platform, including the main systems, data flows, and processing steps.

## 1. Components

- **Salesforce**
  - Captures and stores support/claim cases
  - Handles case routing, categorization, and escalation using Flows
  - Provides operational dashboards for agents and supervisors
  - Exports case data as CSV for downstream processing

- **Databricks (Community Edition)**
  - Ingests exported Salesforce data
  - Performs data cleaning and transformation using SQL and notebooks
  - Engineers features for machine learning (e.g., text length, keywords, timings)
  - Trains and evaluates ML models for case classification and SLA risk scoring
  - Outputs a curated dataset ready for analytics

- **Snowflake**
  - Serves as the analytics data warehouse
  - Stores curated fact and dimension tables
  - Provides a central SQL layer for KPI reporting and trend analysis

- **AI / ML Layer**
  - Implemented inside Databricks notebooks using Python and ML libraries
  - Produces predictions and risk scores that are written back to curated tables

- **GitHub**
  - Stores documentation, SQL scripts, and notebook exports
  - Acts as the main portfolio artifact for the project

## 2. Data Flow

```text
+------------------+         +------------------------+        +----------------------+
|                  |  CSV    |                        |  CSV   |                      |
|   Salesforce     +--------->      Databricks        +------->       Snowflake       |
| (Case Intake &   | export  | (ETL, Feature Eng, ML) | load   | (Data Warehouse &    |
|  Routing)        |         |                        |        |  Analytics)          |
+------------------+         +------------------------+        +----------------------+
                                   |
                                   | Predictions, risk scores
                                   v
                             AI / ML Models
