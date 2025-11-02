# 🪙 Crypto Trading Data Analysis Dashboard

This project visualizes cryptocurrency trading activity using **Power BI** and **Python**.  
It combines multiple data sources (ohlctrades.csv, currencypairs.csv, vertexs.csv) to create interactive insights on transaction volume, currency relationships, and trading patterns.

---

<img width="830" height="446" alt="Screenshot 2025-11-02 at 12 08 03 AM" src="https://github.com/user-attachments/assets/14d6a3b8-4acd-4490-9633-b9203de80865" />


## 📊 Dashboard Overview

The Power BI dashboard includes the following visuals:

1. **Transactions and Volume by Date**  
   - Bar + line combo chart showing simulated transaction counts and trading volume.

2. **Transactions by Destination Currency**  
   - Horizontal bar chart ranking top destination currencies by total transaction volume.

3. **Network Graph of Crypto Transactions**  
   - Built using networkx to show connections between source (from_currency) and destination (to_currency) cryptos.  
   - Color-coded by origin (teal) and destination (violet).

4. **KPI Summary**  
   - Displays total transactions, number of origin cryptos, and number of destination cryptos.

---

## 🧩 Files Description

| File Name | Description |
|------------|-------------|
| ohlctrades.csv | Contains core transaction data (date, from, to, vertex mappings). |
| currencypairs.csv | Contains details about available cryptocurrency pairs. |
| vertexs.csv | Contains currency index-to-name mapping. |
| Crypto_Trading_Dashboard.pbix | Power BI report file containing all visuals. |
| dashboard_script.py | Python script used inside the Power BI visual. |

---

## 🔄 Data Ingestion & Transformation Process

The data ingestion process is handled within **Power BI** using Python scripting:

1. **Data Source Loading**  
   - Power BI imports raw data from three CSV files:  
     - ohlctrades.csv → transactional and vertex relationship data  
     - currencypairs.csv → crypto pair definitions  
     - vertexs.csv → vertex-to-currency mapping  

2. **Python Integration**  
   - Inside Power BI, a Python visual or transformation step uses **Pandas** to load and preprocess the data.  
   - The data passed into Python from Power BI’s fields (date, from, to, etc.) is automatically converted into a Pandas DataFrame called `dataset`.

3. **Data Cleaning & Preparation**  
   - Columns are renamed and standardized (from → from_currency, etc.)  
   - Missing values are handled or simulated for analysis.  
   - Simulated numeric columns (transactions, volume) are created if missing in the dataset.  
   - The processed data is then used to create summary tables and relationships for visualization.

4. **Data Modeling in Power BI**  
   - Relationships between tables (ohlctrades, vertexs, currencypairs) are established through vertex IDs.  
   - The cleaned data flows into visuals such as bar charts, network graphs, and KPI cards.

5. **Visualization Rendering**  
   - Power BI executes the Python script within its sandbox environment to render Matplotlib and NetworkX visuals dynamically.  
   - The result is a fully interactive dashboard that refreshes when data sources are updated.

---

## ⚙️ Installation & Setup

### 1️⃣ Install Dependencies
Open PowerShell or Command Prompt and run:

```powershell
& "C:\Users\<YourUser>\AppData\Local\Programs\Python\Python311\python.exe" -m pip install pandas matplotlib numpy networkx
