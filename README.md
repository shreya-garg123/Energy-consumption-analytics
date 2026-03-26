# Energy Consumption Analytics
# ⚡ Energy Consumption Analytics — AWS S3 + Snowflake + Tableau

An end-to-end data analytics pipeline that ingests raw energy consumption data from **AWS S3**, transforms it using **Snowflake SQL**, and visualizes insights through an interactive **Tableau Dashboard**.

---

## 📊 Dashboard Preview

<img width="1920" height="1080" alt="Energy Consumption Dashboard" src="https://github.com/user-attachments/assets/cc865b6b-c991-48ce-87dd-deed5867925d" />


---

## 🏗️ Project Architecture

```
Raw Data (Excel)
      ↓
AWS S3 Bucket (Cloud Storage)
      ↓
Snowflake (Data Warehouse)
  → Data Loading via S3 Integration
  → Data Transformation using SQL
      ↓
Tableau Desktop
  → Connected to Snowflake
  → Interactive Dashboard
```

---

## 📁 Project Structure

```
energy-consumption-analytics/
│
├── README.md
├── data/
│   └── energy_data.xlsx          # Raw energy consumption dataset
│
├── sql/
│   └── data_transformation.sql   # Snowflake SQL transformations
│
├── tableau/
│   └── energy_dashboard.twbx     # Tableau packaged workbook
│
└── screenshots/
    └── dashboard_overview.png    # Final dashboard screenshot
```

---

## 📌 Key Features

- 🪣 **AWS S3** — Cloud storage for raw data ingestion
- ❄️ **Snowflake** — Scalable data warehouse with role-based access and S3 integration
- 🔄 **SQL Transformations** — Data cleaning and aggregation using Snowflake SQL
- 📈 **Tableau Dashboard** — 6 interactive charts covering:
  - KWH by Country & Region
  - CSU (Cost Savings Units) by Country & Region
  - KWH & CSU breakdown by Energy Source (Biomass, Geothermal, Hydro, Solar, Wind)

---

## 🗺️ Dashboard Highlights

| Chart | Description |
|-------|-------------|
| KWH by Country | Horizontal bar chart comparing energy usage across 25+ countries |
| CSU by Country | Cost savings comparison per country |
| KWH by Region | Energy consumption across Africa, Asia, Australia, Europe, North America, South America |
| KWH by Energy Source | Breakdown: Biomass, Geothermal, Hydro, Solar, Wind |
| CSU by Region | Cost savings unit breakdown by region |
| CSU by Energy Source | Cost efficiency per energy source type |

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| Microsoft Excel | Raw data source |
| AWS S3 | Cloud data storage |
| AWS IAM | Role creation & trust policy for Snowflake access |
| Snowflake | Data warehouse, loading & SQL transformation |
| Tableau Desktop | Data visualization & dashboard |

---

## 🚀 Steps to Reproduce

### 1. Set Up AWS S3
- Create an S3 bucket
- Upload the `data/energy_data.xlsx` file

### 2. Configure Snowflake
- Create a Snowflake account (free trial works)
- Create a new database and schema
- Set up an **Integration Object** with S3
- Create an **IAM Role** in AWS and update the trust policy with Snowflake's details

### 3. Load Data into Snowflake
```sql
-- Example: Create a stage and load data
CREATE STAGE my_s3_stage
  URL = 's3://your-bucket-name/'
  CREDENTIALS = (AWS_ROLE = 'arn:aws:iam::YOUR_ACCOUNT:role/YOUR_ROLE');

COPY INTO energy_table FROM @my_s3_stage;
```

### 4. Transform Data
- Run the SQL scripts in `/sql/data_transformation.sql`
- Key transformations: aggregations by country, region, and energy source

### 5. Connect Tableau to Snowflake
- Open Tableau Desktop → Connect → Snowflake
- Enter your Snowflake account URL, username, and password
- Select the database and schema

### 6. Explore the Dashboard
- Open `tableau/energy_dashboard.twbx`
- All 6 charts will load automatically

---

## 📊 Dataset Overview

The dataset contains global energy consumption records including:

- **Country & Region** — 25+ countries across 6 regions
- **KWH** — Kilowatt-hours consumed
- **CSU** — Cost Savings Units
- **Energy Source** — Biomass, Geothermal, Hydro, Solar, Wind

---

## 🔍 Key Insights from the Dashboard

- 🌏 **Australia & New Zealand** have the highest per-country KWH consumption
- 💨 **Wind energy** leads all sources with 251,427 KWH total
- 🌍 **Europe** has the highest KWH by region (189,337)
- 💰 **Wind** is also the most cost-efficient energy source (CSU: 47,507)



