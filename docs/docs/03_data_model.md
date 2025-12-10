
## Intelligent Case Triage & Claims Insights Platform

This document describes the logical data model used across Salesforce, Databricks, and Snowflake.

The goal is to keep the model simple but realistic, so it can support routing, ML features, and analytics.

## 1. Core Entities

### 1.1 Case
Represents a single support/claim case submitted by a customer.

**Key fields (examples):**

- `CaseId` (primary key)
- `CreatedDate`
- `ClosedDate`
- `Status` (New, In Progress, Resolved, Closed)
- `Priority` (Low, Medium, High, Critical)
- `Category` (Billing, Technical, Policy, Other)
- `Channel` (Phone, Email, Web, Other)
- `AgentId` (who is handling it)
- `QueueName`
- `Description`
- `SlaTargetDate`
- `SlaBreachedFlag` (Yes/No)
- `PredictedCategory`
- `PredictedSlaRiskScore` (0–1)
- `PredictedSlaRiskBucket` (Low/Medium/High)

### 1.2 Customer (optional, can be simplified)
Represents the customer associated with a case (can be basic for this project).

- `CustomerId`
- `CustomerName`
- `Segment` (Retail, Enterprise, etc.)
- `Region`
- `Email`
- `Phone`

### 1.3 Agent
Represents support or claims staff.

- `AgentId`
- `AgentName`
- `Team`
- `Region`
- `Role` (Agent, Senior Agent, Supervisor)

### 1.4 Category Dimension
Used for analytics and grouping.

- `CategoryKey`
- `CategoryName` (Billing, Technical, Policy, Other)
- `CategoryDescription`

### 1.5 Priority Dimension
- `PriorityKey`
- `PriorityLevel` (1–4)
- `PriorityLabel` (Low, Medium, High, Critical)

### 1.6 SLA Bucket Dimension
- `SlaBucketKey`
- `SlaBucketName` (On-Time, Slightly Late, Very Late)
- `SlaRange` (e.g., 0–24h, 24–48h, 48h+)

## 2. Fact Table (Analytics Layer)

### 2.1 FactCase

Fact table containing one record per case.

**Example fields:**

- `CaseKey` (surrogate key)
- `CaseId`
- `CustomerKey` (FK)
- `AgentKey` (FK)
- `CategoryKey` (FK)
- `PriorityKey` (FK)
- `SlaBucketKey` (FK)
- `CreatedDate`
- `ClosedDate`
- `TimeToCloseHours`
- `IsSlaBreached` (Yes/No)
- `PredictedSlaRiskScore`
- `PredictedSlaRiskBucket`
- `PredictedCategoryKey` (FK to Category)

This table is what we will ultimately load into Snowflake for analytics.

## 3. Relationships (ERD Style)

```text
          +-------------------+
          |   DimCategory     |
          |-------------------|
          | CategoryKey (PK)  |
          | CategoryName      |
          +---------+---------+
                    |
                    |  (FK)
                    v
 +-------------------------+
 |        FactCase         |
 |-------------------------|
 | CaseKey (PK)           |
 | CaseId                 |
 | CategoryKey (FK)       |
 | PriorityKey (FK)       |
 | CustomerKey (FK)       |
 | AgentKey (FK)          |
 | SlaBucketKey (FK)      |
 | ... metrics ...        |
 +----+---------+---------+
      |         |
      |         |
      v         v

+-------------+      +----------------+
| DimPriority |      |  DimCustomer   |
+-------------+      +----------------+

      ^
      |
      |
+-------------+
|  DimAgent   |
+-------------+

      ^
      |
      |
+----------------+
| DimSlaBucket   |
+----------------+
