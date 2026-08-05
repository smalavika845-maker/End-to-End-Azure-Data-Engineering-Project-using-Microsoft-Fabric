# 🚀 Microsoft Fabric End-to-End Data Engineering Pipeline

## 📌 Project Overview

This project demonstrates an end-to-end data engineering solution using **Microsoft Fabric**. The pipeline ingests data from the **Research API**, stores it in **OneLake**, transforms it using **Synapse Data Engineering**, performs analytics with **Synapse Data Science**, visualizes insights through **Power BI**, and enables real-time notifications using **Data Activator** integrated with **Microsoft Teams**.

---

## 🔄 Data Flow

```text
Research API
    │
    ▼
Data Factory
    │
    ▼
Raw JSON Files
    │
    ▼
OneLake
    │
    ▼
Synapse Data Engineering
(PySpark / Spark SQL)
    │
    ▼
Clean Delta Tables
    │
    ▼
Synapse Data Science
    │
    ▼
Power BI Dashboard
    │
    ▼
Data Activator
    │
    ▼
Microsoft Teams Alerts
```

---

## 🛠️ Technologies Used

- Microsoft Fabric
- Data Factory
- OneLake
- Synapse Data Engineering
- Synapse Data Science
- Power BI
- Data Activator
- Microsoft Teams
- Research API
- JSON
- PySpark
- Spark SQL

---

## ⚙️ Workflow

### 1️⃣ Data Ingestion
- Data is extracted from the **Research API** using Microsoft Fabric Data Factory.
- The API returns structured **JSON** data containing web search and research results.
- The extracted data is stored in OneLake as raw JSON files.

### 2️⃣ Data Storage
- Raw JSON data is stored securely in **OneLake**, Microsoft's unified data lake.

### 3️⃣ Data Transformation
- Synapse Data Engineering notebooks process the raw JSON data.
- Data cleansing, transformation, and validation are performed using **PySpark**.
- Processed data is stored as **Delta Tables** for efficient querying and analytics.

### 4️⃣ Data Analytics
- Synapse Data Science enables advanced analytics and machine learning on the curated datasets.

### 5️⃣ Data Visualization
- Power BI connects directly to the curated Delta tables.
- Interactive dashboards provide business insights, trends, and KPI monitoring.

### 6️⃣ Intelligent Alerts
- Data Activator continuously monitors business conditions.
- When predefined thresholds are met, notifications are automatically sent to Microsoft Teams.

---

## 📊 Key Features

- End-to-End Data Engineering Pipeline
- REST API Data Ingestion
- Automated ETL using Microsoft Fabric Data Factory
- Cloud-based Storage with OneLake
- Data Transformation using PySpark
- Delta Lake Architecture
- Interactive Power BI Dashboards
- Event-driven Alerts with Data Activator
- Microsoft Teams Integration
- Scalable Microsoft Fabric Solution

---

## 📂 Project Components

```text
📁 Data Factory
📁 OneLake
📁 Synapse Data Engineering
📁 Synapse Data Science
📁 Power BI
📁 Data Activator
📁 Documentation
```

---

## 🎯 Business Benefits

- Automated ingestion of research and web search data
- Centralized cloud storage using OneLake
- Scalable ETL processing
- Faster reporting and analytics
- Interactive dashboards for business insights
- Real-time monitoring with automated alerts
- Improved data-driven decision making

---

## 🚀 Future Enhancements

- Incremental data loading
- Parameterized pipelines
- Data quality validation
- Medallion Architecture (Bronze, Silver, Gold)
- CI/CD integration using Azure DevOps
- Automated pipeline scheduling

---

## 👩‍💻 Author

**Malavika S**

**Data Engineer | Microsoft Fabric | Azure Data Factory | Power BI | SQL | PySpark**

📧 Email: **smalavika845@gmail.com**

🔗 LinkedIn: **https://www.linkedin.com/in/malavika-s-35a383215/**

---

⭐ If you found this project useful, consider giving it a **Star**!
