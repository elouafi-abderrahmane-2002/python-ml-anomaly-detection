# 🔍 Python ML Anomaly Detection

> Detecting the unexpected — because outliers tell the most interesting stories.

A complete end-to-end pipeline for **anomaly detection on time-series data**, built with Python and Scikit-learn. Models are exposed via a lightweight **FastAPI REST endpoint**, ready for integration into any data platform or dashboard.

---

## 🧠 Models Implemented

| Model | Library | Use Case |
|---|---|---|
| Isolation Forest | Scikit-learn | General-purpose anomaly detection |
| Local Outlier Factor (LOF) | Scikit-learn | Density-based outlier scoring |
| Z-Score baseline | NumPy | Quick statistical threshold check |

---

## 🗂️ Project Structure

```
python-ml-anomaly-detection/
│
├── src/
│   ├── data_preprocessing.py     # Load, clean, scale time-series data
│   ├── model_isolation_forest.py # Isolation Forest training & scoring
│   ├── model_lof.py              # LOF training & scoring
│   ├── evaluate.py               # Comparative evaluation (precision, recall, F1)
│   └── api.py                    # FastAPI REST endpoint
│
├── data/
│   └── sample_timeseries.csv     # Sample dataset
│
├── notebooks/
│   └── exploration.ipynb         # EDA and model comparison
│
├── Dockerfile
├── requirements.txt
└── README.md
```

---

## ⚙️ Quickstart

```bash
# Install dependencies
pip install -r requirements.txt

# Run the API locally
uvicorn src.api:app --reload
```

API available at: `http://localhost:8000/docs`

---

## 🐳 Docker

```bash
docker build -t anomaly-detection-api .
docker run -p 8000:8000 anomaly-detection-api
```

---

## 📡 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/health` | Health check |
| POST | `/predict` | Run anomaly detection on input records |
| GET | `/models` | List available models |

**Example request:**
```json
POST /predict
{
  "model": "isolation_forest",
  "features": ["value", "rate"],
  "records": [
    {"timestamp": "2024-01-01", "value": 12.4, "rate": 0.8},
    {"timestamp": "2024-01-02", "value": 98.7, "rate": 4.5}
  ]
}
```

---

## 📦 Tech Stack

- **Python 3.11**
- **Pandas / NumPy** — data manipulation
- **Scikit-learn** — ML models
- **FastAPI + Uvicorn** — REST API
- **Docker** — containerization
- **Matplotlib / Seaborn** — visualization

---

## 📊 Results

| Model | Precision | Recall | F1-Score |
|---|---|---|---|
| Isolation Forest | 0.87 | 0.83 | 0.85 |
| LOF | 0.81 | 0.79 | 0.80 |
| Z-Score | 0.74 | 0.91 | 0.82 |

---

## 👤 Author

**ELOUAFI Abderrahmane**  
Ingénieur Big Data & Cloud — ENSET Mohammedia  
[LinkedIn](https://www.linkedin.com/in/abderrahmane-elouafi-43226736b/) • [Portfolio](https://my-first-porfolio-six.vercel.app/)
