# 🪙 BTC Price Prediction with AI, Databricks & Airflow

This is an end-to-end learning project using **Databricks**, **Airflow**, and **AI/ML models** to predict the price of **Bitcoin (BTC)** based on historical cryptocurrency data from the **CoinGecko API**.

---

## 📌 Project Goals

- Ingest historical BTC data via public API (CoinGecko)
- Build a Lakehouse pipeline in **Databricks** using Delta tables
- Orchestrate the workflow using **Apache Airflow**
- Train an AI model (LSTM / Prophet) to forecast BTC price
- Interact with the data using an LLM-based interface

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Databricks** | Data engineering, processing & model training |
| **Apache Airflow** | Orchestration of data ingestion & model runs |
| **CoinGecko API** | Source of BTC market data |
| **Python** | Core language |
| **MLflow / PyTorch / Prophet** | AI model training |
| **LangChain / OpenAI / LLamaIndex** | LLM interaction with data (optional)

---

## 📈 Data Source

**CoinGecko Market Chart API**

- Endpoint: `https://api.coingecko.com/api/v3/coins/bitcoin/market_chart`
- Frequency: Hourly
- Data: `price`, `market_cap`, `volume`
- Time Period: Last 180 days

---

## 📂 Project Structure

```text
btc-price-prediction-ai/
├── notebooks/
│   ├── 01_ingest_data_coingecko.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_model_training.ipynb
│   └── 04_llm_interface.ipynb
├── airflow/
│   └── dag_btc_pipeline.py
├── data/
│   └── (optional sample data files)
├── README.md
├── requirements.txt
└── LICENSE
```

---

## 🚀 How to Run

### 1. Clone the repo

```bash
git clone https://github.com/your-username/btc-price-prediction-ai.git
cd btc-price-prediction-ai

pip install -r requirements.txt


