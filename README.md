# Airflow Weather ETL Project (Mumbai)

## 📌 Project Overview

This project demonstrates an **ETL (Extract, Transform, Load) data pipeline using Apache Airflow**. The pipeline fetches **real-time weather data for Mumbai** from the Open-Meteo API, processes the data, and **stores it into a PostgreSQL database**.

This project is ideal for beginners learning **Airflow DAGs, task-based pipelines, APIs, and database integration**.

---

## 🏗️ Architecture

1. **Apache Airflow** – Orchestrates the ETL workflow
2. **Open-Meteo Weather API** – Source of weather data
3. **PostgreSQL** – Stores transformed weather data
4. **Python** – Used for data extraction, transformation, and loading

---

## 📂 Project Structure

```
Weather_ETL_Project/
├── dags/
│   └── ETL_Weather.py
├── docker-compose.yaml   (optional – for Airflow setup)
└── README.md
```

---

## ⚙️ Prerequisites

Ensure the following are installed:

* Python 3.8+
* Apache Airflow 2.x
* PostgreSQL
* Docker & Docker Compose (optional but recommended)

---

## 🔗 Connections Required in Airflow

Create the following connections in **Airflow UI → Admin → Connections**:

### 1️⃣ Open-Meteo API Connection

* **Conn ID**: `open_meteo_api`
* **Conn Type**: HTTP
* **Host**: `https://api.open-meteo.com`

### 2️⃣ PostgreSQL Connection

* **Conn ID**: `postgres_default`
* **Conn Type**: Postgres
* **Host**: `localhost`
* **Schema**: `postgres`
* **Login**: your_username
* **Password**: your_password
* **Port**: `5432`

---

## 🧾 DAG Details

* **DAG ID**: `ETL_Weather`
* **Schedule**: `@daily`
* **Catchup**: Disabled
* **Start Date**: 20 December 2025

---

## 🔄 ETL Workflow

### 🔹 Extract

* Fetches current weather data for Mumbai using latitude and longitude
* Uses Airflow `HttpHook`

### 🔹 Transform

* Extracts required fields:

  * Latitude
  * Longitude
  * Temperature
  * Wind Speed
  * Wind Direction
  * Weather Code

### 🔹 Load

* Creates PostgreSQL table if it does not exist
* Inserts transformed weather data into the database

---

## 📊 Database Table Schema

```sql
CREATE TABLE weather_data (
    latitude FLOAT,
    longitude FLOAT,
    temperature FLOAT,
    windspeed FLOAT,
    winddirection FLOAT,
    weathercode INT,
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## ▶️ How to Run the Project

1. Start Airflow services:

```bash
airflow standalone
```

(or using Docker Compose)

2. Place `ETL_Weather.py` inside the `dags/` folder

3. Open Airflow UI:

```text
http://localhost:8080
```

4. Enable the DAG **ETL_Weather**

5. Trigger the DAG manually or wait for scheduled run

---

## 📥 Output

* Weather data for Mumbai is stored in PostgreSQL
* Each DAG run inserts a new record with timestamp

---

## 📝 Key Learning Outcomes

* Airflow DAG creation using TaskFlow API
* API data extraction using HttpHook
* Data transformation in Python
* Loading data into PostgreSQL using PostgresHook
* ETL pipeline automation

---

## 📌 Use Cases

* Weather analytics
* Scheduled data ingestion pipelines
* Learning Airflow for Data Engineering
* API-to-database ETL workflows

---

## ✅ Conclusion

This project provides a **clear and practical example of an Airflow-based ETL pipeline**, integrating API data with a relational database. It serves as a strong foundation for more advanced data engineering projects.

---

👤 **Author**: Arya Kurup
📅 **Project Type**: Airflow ETL Learning Project
🌍 **City**: Mumbai Weather Data
