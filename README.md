# 🚀 Microsoft Fabric End-to-End Data Engineering Pipeline

## 📌 Project Overview

This project demonstrates an end-to-end data engineering solution using **Microsoft Fabric**. The pipeline ingests data from the **Bing API**, stores it in **OneLake**, transforms it using **Synapse Data Engineering**, performs analytics with **Synapse Data Science**, visualizes insights through **Power BI**, and enables real-time notifications using **Data Activator** integrated with **Microsoft Teams**.


## 🔄 Data Flow

```
Bing API
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
- Bing API
- JSON
- PySpark
- Spark SQL

---

## ⚙️ Workflow

### 1️⃣ Data Ingestion
- Data is extracted from the **Bing API** using Microsoft Fabric Data Factory.
- The extracted data is stored in **JSON** format.

### 2️⃣ Data Storage
- Raw data is stored securely in **OneLake**, Microsoft's unified storage layer.

### 3️⃣ Data Transformation
- Synapse Data Engineering notebooks process the raw JSON data.
- Data cleansing, transformation, and validation are performed using **PySpark**.
- Processed data is stored as **Delta Tables**.

### 4️⃣ Data Analytics
- Synapse Data Science enables advanced analytics and machine learning on the curated datasets.

### 5️⃣ Data Visualization
- Power BI connects directly to the curated Delta tables.
- Interactive dashboards provide business insights and KPI monitoring.

### 6️⃣ Intelligent Alerts
- Data Activator continuously monitors business conditions.
- When predefined thresholds are met, notifications are automatically sent to Microsoft Teams.

---

## 📊 Key Features

- End-to-End Data Pipeline
- Automated Data Ingestion
- Cloud-based Data Lake Storage
- Data Transformation with PySpark
- Delta Lake Architecture
- Interactive Power BI Dashboards
- Event-driven Alerts
- Microsoft Teams Integration
- Scalable Microsoft Fabric Solution

---

## 📂 Project Components

```
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

- Automated data ingestion from APIs
- Centralized cloud storage using OneLake
- Scalable ETL processing
- Faster business reporting
- Real-time business monitoring
- Improved decision-making through interactive dashboards
- Automated notifications for critical events

---

## 👩‍💻 Author

**Malavika S**

**Data Engineer | Azure Data Engineer | Microsoft Fabric | Power BI | SQL | PySpark**

📧 Email: smalavika845@gmail.com

🔗 LinkedIn: https://www.linkedin.com/in/malavika-s-35a383215/

---
⭐ If you found this project useful, consider giving it a Star!
