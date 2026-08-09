# 🚀 Microsoft Fabric End-to-End News Sentiment Analysis & Alerting

## 📌 Project Overview

This project demonstrates an end-to-end **data engineering, analytics, sentiment analysis, and real-time alerting solution using Microsoft Fabric**.

The solution retrieves the latest technology news from an external News API, ingests the data using Microsoft Fabric Data Factory, stores the raw data in OneLake, transforms and processes it using PySpark, performs sentiment analysis, stores the curated results in Delta tables, and visualizes the insights through an interactive Power BI dashboard.

The solution also uses **Microsoft Fabric Activator** to monitor sentiment results and trigger alerts for **Positive, Negative, and Neutral** sentiment.

---

## 🏗️ Solution Architecture

```text
                    External News API
                           │
                           │ REST API
                           ▼
                ┌─────────────────────┐
                │ Microsoft Fabric    │
                │ Data Factory        │
                └──────────┬──────────┘
                           │
                           ▼
                       OneLake
                    Raw JSON Data
                           │
                           ▼
              ┌─────────────────────────┐
              │ Synapse Data Engineering│
              │                         │
              │ PySpark / Spark SQL     │
              └────────────┬────────────┘
                           │
                           ▼
                    Delta Lake Tables
                           │
                           ▼
              ┌─────────────────────────┐
              │   Sentiment Analysis    │
              │                         │
              │   Positive              │
              │   Neutral               │
              │   Negative              │
              └────────────┬────────────┘
                           │
                           ▼
                  Curated Delta Table
                           │
                  ┌────────┴─────────┐
                  │                  │
                  ▼                  ▼
          ┌───────────────┐  ┌─────────────────┐
          │    Power BI   │  │ Fabric Activator│
          │   Dashboard   │  │                 │
          └───────────────┘  └────────┬────────┘
                                      │
                                      ▼
                               Sentiment Alerts
```

---

## 🌐 External News API

The project uses an external News API to retrieve the latest technology news.

The API request is configured for:

- **Country:** India
- **Language:** English
- **Category:** Technology

The API endpoint follows this structure:

```text
/api/1/latest?apikey=<API_KEY>&country=in&language=en&category=technology
```

The API returns news information in JSON format, including fields such as:

- title
- Description
- Category
- link
- Source
- Country
- Authors
- Keywords
- Published date


> **Security Note:** The API key is intentionally not included in this README. API credentials should be stored securely using Fabric parameters, secrets, or another secure credential mechanism.

---

# 🔄 Data Flow

```text
1. External News API
          ↓
2. Microsoft Fabric Data Factory
          ↓
3. Raw JSON Data
          ↓
4. OneLake
          ↓
5. Synapse Data Engineering
          ↓
6. PySpark Data Transformation
          ↓
7. Delta Lake
          ↓
8. Sentiment Analysis
          ↓
9. Curated Sentiment Table
          ↓
10. Power BI Dashboard
          ↓
11. Fabric Activator
          ↓
12. Sentiment Alerts
```

---

# 1️⃣ Data Ingestion

The pipeline starts by calling the external News API through **Microsoft Fabric Data Factory**.

The API retrieves the latest technology news for India.

```text
External News API
        ↓
Fabric Data Factory
        ↓
Raw JSON
```

The API response is stored in **OneLake** for downstream processing.

---

# 2️⃣ Raw Data Storage

The raw API response is stored as JSON data in **Microsoft Fabric OneLake**.

Maintaining the raw data provides a source layer that can be used for:

- Reprocessing
- Debugging
- Data validation
- Historical analysis
- Downstream transformations

---

# 3️⃣ Data Transformation

The raw JSON data is processed using **Microsoft Fabric Synapse Data Engineering notebooks**.

PySpark is used to:

- Read JSON data
- Extract relevant fields
- Flatten nested structures
- Clean the data
- Transform data types
- Process publication dates
- Create formatted date fields
- Prepare the dataset for sentiment analysis

Example fields include:

```text
title
description
category
link
source
country
authors
keywords
published_date
```

---

# 4️⃣ Delta Lake Storage

The transformed data is stored as **Delta tables**.

Delta Lake provides reliable storage and supports incremental data processing.

The article `link` is used as the unique identifier for identifying existing articles.

The incremental logic follows:

```text
Existing Article
      ↓
    UPDATE

New Article
      ↓
    INSERT
```

This approach helps preserve historical records while preventing duplicate articles from being repeatedly inserted.

---

# 5️⃣ Sentiment Analysis

The processed news articles are passed through the sentiment analysis workflow.

Each article is classified into one of three sentiment categories:

```text
🟢 Positive
🔵 Neutral
🔴 Negative
```

The sentiment result is stored together with the article information in the curated Delta table.

Example fields:

```text
Title
Description
Category
Source
Published Date
Keywords
Sentiment
Link
```

The curated sentiment dataset becomes the primary source for the Power BI dashboard and Activator monitoring.

---

# 6️⃣ Power BI Dashboard

The curated Delta table is connected to **Power BI** to create an interactive News Sentiment Analytics dashboard.

The dashboard provides an overview of the news data and sentiment trends.

## 📊 Dashboard Features

- Published date drop-down
- Positive sentiment percentage
- Neutral sentiment percentage
- Negative sentiment percentage
- Articles specific to each date in a tabular format

### Dashboard Structure

```text

┌──────────────────────────────────────────────────────────────┐
│                  NEWS SENTIMENT ANALYTICS                    │
│          Daily news coverage, sentiment and source insights  │
│                                                              │
├───────────────────┬────────────────┬────────────────┬────────┤
│ Published Date    │ Negative       │ Neutral        │Positive│
│                   │ Sentiment %    │ Sentiment %    │Sentiment│
│   [Date Filter]   │                │                │   %    │
├───────────────────┴────────────────┴────────────────┴────────┤
│                                                              │
│                    NEWS ARTICLE TABLE                        │
│                                                              │
│ Title │ Source │ Link │ Keywords │ Published Date            │
│                                                              │
│ Article 1 │ Source │ 🔗 │ Keywords │ Date                    │
│ Article 2 │ Source │ 🔗 │ Keywords │ Date                    │
│ Article 3 │ Source │ 🔗 │ Keywords │ Date                    │
│ Article 4 │ Source │ 🔗 │ Keywords │ Date                    │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

# 7️⃣ Microsoft Fabric Activator

The project uses **Microsoft Fabric Activator** for real-time sentiment monitoring.

Activator monitors the sentiment data and can trigger actions when configured conditions are met.

Three sentiment monitoring scenarios were configured:

### 🟢 Positive Sentiment Alert

Monitors positive sentiment news and triggers the configured alert condition.

### 🔵 Neutral Sentiment Alert

Monitors neutral sentiment news and triggers the configured alert condition.

### 🔴 Negative Sentiment Alert

Monitors negative sentiment news and triggers the configured alert condition.

This extends the project beyond traditional reporting into **automated event monitoring and real-time intelligence**.

---

# 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| **Microsoft Fabric** | End-to-end data platform |
| **Data Factory** | API ingestion and orchestration |
| **OneLake** | Centralized raw data storage |
| **Synapse Data Engineering** | Data transformation and processing |
| **PySpark** | Data cleansing and transformation |
| **Spark SQL** | Data querying and Delta operations |
| **Delta Lake** | Curated and historical data storage |
| **Power BI** | Interactive data visualization |
| **Fabric Activator** | Real-time sentiment monitoring and alerts |
| **Python** | Data processing and pipeline logic |
| **REST API** | External news data source |
| **JSON** | Raw API response format |

---

# ⚙️ End-to-End Workflow

```text
1. Call External News API
             ↓
2. Retrieve Technology News
             ↓
3. Fabric Data Factory
             ↓
4. Store Raw JSON in OneLake
             ↓
5. Read JSON using PySpark
             ↓
6. Clean and Transform Data
             ↓
7. Store Data in Delta Lake
             ↓
8. Perform Sentiment Analysis
             ↓
9. Store Curated Sentiment Data
             ↓
10. Connect Curated Data to Power BI
             ↓
11. Build Interactive Dashboard
             ↓
12. Monitor Sentiment using Activator
             ↓
13. Trigger Sentiment Alerts
```

---

# 📂 Project Components

```text
📁 End-to-End-Azure-Data-Engineering-Project-using-Microsoft-Fabric
│
├── 📁 Data Factory
│   └── News API Ingestion Pipeline
|   └── manifest.json
│
├── 📁 Notebooks
│   └── Data transformation.ipynb
|   └── news-sentiment-analysis.ipynb
│
├── 📁 screenshots
│   ├── Activator.png
│   └── dashboard.png
│
📄 README.md

```

---

# 🔑 Key Technical Features

## Historical Data Preservation

The pipeline is designed to retain historical news records rather than replacing the entire dataset whenever new news is ingested.

The article `link` is used as a matching key for incremental processing.

```text
                    Incoming News
                         │
                         ▼
                  Does link exist?
                    /          \
                  YES           NO
                   │             │
                   ▼             ▼
                UPDATE         INSERT
                   │             │
                   └──────┬──────┘
                          ▼
                    Delta Table
```

This allows Power BI to analyze news across multiple publication dates.

---


## Date Transformation

Publication dates are transformed into usable date fields for historical analysis and Power BI filtering.

Example:

```python
from pyspark.sql.functions import col, to_date

df = df.withColumn(
    "datePublished",
    to_date(col("datePublished"), "dd-MMM-yyyy")
)
```

---

# 📈 Business Insights

The solution can help answer questions such as:

- How many technology news articles were published?
- What percentage of news is positive, neutral, or negative?
- How does sentiment change over time?
- Which news sources publish the most articles?
- Which technology categories receive the most coverage?
- What are the latest technology stories?
- When does negative or positive sentiment reach a defined threshold?
- Can sentiment changes trigger automated alerts?

---

# 🎯 Business Benefits

- Automated news data ingestion
- Centralized storage using OneLake
- Scalable PySpark data processing
- Historical news data retention
- Duplicate prevention
- Sentiment-based analytics
- Interactive Power BI reporting
- Automated sentiment monitoring
- Event-driven alerts
- End-to-end Microsoft Fabric implementation

---

# 🚀 Future Enhancements

Potential improvements include:

- Incremental API ingestion based on publication date
- Automated pipeline scheduling
- Parameterized API requests
- Bronze / Silver / Gold Medallion Architecture
- Advanced data quality checks
- Additional news categories
- Multiple external news APIs
- Topic classification
- Keyword trend analysis
- Source-level sentiment comparison
- Geographic news analysis
- Sentiment anomaly detection
- Advanced Activator alert thresholds
- Microsoft Teams or email notification integration
- Power BI drill-through pages
- Historical sentiment forecasting

---

# 🎓 Learning Outcomes

This project demonstrates practical experience with:

- Microsoft Fabric
- REST API integration
- Data Factory
- OneLake
- PySpark
- Spark SQL
- JSON processing
- Data cleansing
- Delta Lake
- Incremental data processing
- MERGE / upsert operations
- Sentiment analysis
- Power BI
- Data visualization
- Fabric Activator
- Event-driven monitoring
- End-to-end data engineering

---

# 🏆 Project Highlights

### Data Engineering

Built an end-to-end pipeline that ingests external API data, stores raw data in OneLake, transforms it using PySpark, and maintains curated Delta tables.

### Data Analytics

Performed sentiment analysis and created an interactive Power BI dashboard for monitoring news trends and sentiment distribution.

### Real-Time Intelligence

Integrated Microsoft Fabric Activator to monitor sentiment conditions and trigger automated alerts.

### Historical Analytics

Implemented an incremental data approach to retain historical news records and support date-based analysis in Power BI.

---

# 👩‍💻 Author

**Malavika S**

**Data Engineer | Microsoft Fabric | Azure Data Factory | Power BI | SQL | PySpark**

---

## ⭐ Project

If you found this project useful, consider giving it a Star!
