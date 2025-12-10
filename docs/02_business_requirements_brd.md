🧾 Business Requirements Document (BRD)
Intelligent Case Triage & Claims Insights Platform
1. Project Overview

Organizations that manage high volumes of support or claim cases struggle with manual triage, inconsistent routing, SLA breaches, and limited visibility into operational performance.
This project simulates an end-to-end system that enhances:

Case intake & routing (Salesforce)

Data processing & engineering (Databricks)

AI-driven predictions (ML)

Analytics & insights (Snowflake + SQL)

The result is a realistic, enterprise-style workflow for your portfolio.

2. Business Problem

Companies face challenges such as:

Manual & inconsistent triage

Incorrect case routing

High SLA breach rates

Limited visibility into backlog & issues

Scattered data across multiple systems

This leads to:

Inefficient operations

Customer dissatisfaction

Poor decision-making

Delays in resolving claims

3. Project Goals & Objectives
Primary Goals

Automate case routing through Salesforce flows

Process, clean, and enrich data in Databricks

Use ML to predict:

Case category

SLA breach risk

Build Snowflake data warehouse tables for analytics

Generate insights through SQL queries

Success Metrics

Reduce manual routing by 50%

Improve routing accuracy by 30%

Identify SLA-risk cases with 70%+ accuracy

Provide leadership with real-time dashboards

4. Scope
✔ In Scope

Salesforce case configuration

Routing flows

Synthetic case data creation

Export → Databricks ingestion

SQL cleaning & transformations

ML modeling for classification & SLA prediction

Snowflake fact/dimension modeling

SQL insights & dashboards

Documentation in GitHub

❌ Out of Scope

Real PHI/PII data

Live API integrations

Production-grade ML pipelines

Real-time streaming

5. Stakeholders / Actors
Actor	Role
Customer	Submits a claim/support request
Support Agent	Creates/updates Salesforce cases
Claims Analyst	Works assigned case queues
Supervisor	Monitors SLA and escalations
Data Engineer	Manages data in Databricks
Data Analyst	Queries Snowflake
ML Model	Predicts category & SLA risk
Leadership	Uses dashboards for decisions
6. Use Cases
Use Case 1 — Case Intake

Agent logs case

Required fields captured

SLA timer starts

Use Case 2 — Auto Routing

Salesforce keywords → auto-category

Flow assigns case to correct queue

Use Case 3 — Escalation

If case sits too long → Flow escalates

Use Case 4 — Data Transformation (Databricks)

Salesforce CSV uploaded

SQL transformations applied

Feature engineering added

Use Case 5 — ML Predictions

Model classifies category

Model predicts risk of SLA breach

Use Case 6 — Analytics (Snowflake)

Load curated dataset

Build fact/dimension tables

KPI SQL queries built

7. Functional Requirements
Salesforce Requirements

Create fields: Category, SLA Target, Risk Score

Create Routing Queues

Build Flows for:

Auto-category

Auto-routing

Escalation

Dashboards for SLA, backlog, categories

Export CSVs

Databricks Requirements

Upload case CSV

Create Delta tables

Clean & normalize using SQL

Feature engineering

Train ML model (classification + risk prediction)

Generate curated dataset

Snowflake Requirements

Create DB + Schema

Load curated datasets

Create FactCase, DimCategory, DimPriority

Write KPI SQL queries

Enable BI connectivity

Documentation Requirements

BRD

Data model

Architecture diagram

Case study write-up

SQL & notebook storage in GitHub

8. Non-Functional Requirements
Area	Requirement
Performance	Handle ~50k synthetic cases
Security	No PHI/PII; synthetic data only
Usability	Dashboards must be intuitive
Maintainability	Notebooks & SQL reproducible
Reliability	Data pipeline repeatable
9. Assumptions

All tools use free tiers

Data is synthetic

Simple ML models are acceptable

Single-user environment

No external APIs needed

10. Risks & Mitigations
Risk	Mitigation
ML complexity	Use logistic regression or simple tree models
Snowflake credit use	Optimize queries; small warehouse
Tool limitations	Stick to supported free features
Data quality issues	Generate deterministic synthetic datasets
11. Success Criteria

The project is successful when:

Routing automation works in Salesforce

Databricks pipeline runs end-to-end

ML model generates predictions

Snowflake analytics tables are populated

SQL queries return meaningful insights

Documentation is complete & professional

12. Appendices

A: Sample Case Data Format

B: Flow Diagram Draft

C: Data Model Draft

D: Folder Structure
