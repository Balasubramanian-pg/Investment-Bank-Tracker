# Investment-Bank-Tracker Project

## **1. Objective**

To define the requirements for developing SQL-based analytical reports supporting business use cases involving segmentation, time-based analysis, hierarchical reporting, and performance metrics. This initiative aims to enhance the decision-making capabilities of business stakeholders through accurate, structured, and scalable SQL queries.

---

## **2. Background**

Current business analysis requires complex data transformations, non-standard joins, and advanced aggregations that go beyond basic SQL. There is a need to structure these transformations into reusable, modular logic blocks that can support statistical analysis, business KPIs, and temporal insights.

---

## **3. Functional Requirements**

### 3.1 Window Functions

**Purpose:** Segmentation, rank tracking, percentile calculations
**Functions Required:**

* `NTILE()` for bucket segmentation
* `LEAD()`, `LAG()` for sequential value comparison
* `RANK()` for ordered ranking logic
* `PERCENTILE_CONT()` for statistical distribution analysis
  **Use Cases:**
* Customer quartile classification
* Detecting product movement across ranks
* Calculating median value metrics

---

### 3.2 Common Table Expressions (CTEs)

**Purpose:** Multi-stage transformation pipelines
**Requirement:**

* Layered CTEs to clean, transform, and enrich transactional datasets in stages
  **Use Cases:**
* Building a reporting layer on top of denormalized inputs
* Replacing deeply nested subqueries with maintainable logic

---

### 3.3 Advanced Join Conditions

**Types of Joins Required:**

* **Self-joins**: Compare entities across time or state
* **Non-equi joins**: Match based on range or inequality (e.g., date alignment)
* **Composite joins**: Match on multiple foreign keys
  **Use Cases:**
* Time-to-event tracking
* Historical state comparisons
* Multi-key customer-to-region mapping

---

### 3.4 Statistical Analysis

**Required Calculations:**

* Z-score
* Standard deviation
* Herfindahl Index
  **Use Cases:**
* Anomaly detection
* Concentration risk measurement
* Score normalization for dashboards

---

### 3.5 Time Intelligence Logic

**Features:**

* Rolling average (7-day, 30-day)
* Year-over-Year (YoY), Month-over-Month (MoM) growth
* Seasonality breakdowns
  **Implementation Details:**
* Date reference table (calendar)
* Handling of missing date rows
  **Use Cases:**
* Revenue trend comparisons
* Active users tracking by week/month

---

### 3.6 Aggregation Logic

**Requirement:**

* Use of `FILTER` clause for conditional aggregation
* Aggregations based on business categories (e.g., channel, product, region)
  **Use Cases:**
* Revenue split by category
* Conditional performance metrics for dashboards

---

### 3.7 Business Metrics

**Metrics to be Tracked:**

* Conversion Rates
* Volatility Score
* Concentration Risk Index
  **Data Sources:**
* Web sessions, orders, customer activity logs
  **Use Cases:**
* Marketing performance
* Operational exposure monitoring
* Channel-specific analytics

---

### 3.8 Hierarchical and Cumulative Analysis

**Required Logic:**

* Cumulative sums over time or status
* Ordered sequencing logic
  **Use Cases:**
* Approval workflow tracking
* Financial instrument maturity ladders
* Employee progression levels

---

## **4. Technical Requirements**

* SQL compatibility with PostgreSQL or T-SQL engines
* Access to date dimension table
* Raw transactional data tables (orders, customers, sessions, etc.)
* Support for user-defined functions (UDFs) for statistical logic if needed
* Optimization for execution time on large datasets (>1M rows)

---

## **5. Non-Functional Requirements**

* Maintainable SQL scripts (use of CTEs and modular components)
* Scalable to accommodate future KPIs and logic extensions
* Documented query logic with in-line comments
* Query versioning through Git or similar tools

## **6. Assumptions and Constraints**

* All raw data sources are accessible and updated regularly
* No requirement for real-time streaming; batch mode execution is sufficient
* Final reporting platform is compatible with SQL output (e.g., Power BI, Tableau)
