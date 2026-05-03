# 🌦️ Multivariate Time Series Forecasting using LSTM & Transformer Models

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange?logo=tensorflow)](https://www.tensorflow.org/)
[![Keras](https://img.shields.io/badge/Keras-2.x-red?logo=keras)](https://keras.io/)
[![Optuna](https://img.shields.io/badge/Optuna-Hyperparameter%20Tuning-purple)](https://optuna.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1SsGQ0IHjnfh6qqUaGMvAwqRHmjDJfLFp?usp=sharing)

> Predicting daily temperature in Delhi using advanced deep learning architectures — LSTM, Transformer, and an optimized Ensemble model.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Dataset](#-dataset)
- [Architecture](#-architecture)
- [Results](#-results)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Future Work](#-future-work)
- [Author](#-author)

---

## 🔍 Overview

This project tackles **multivariate time series forecasting** on climate data from Delhi. Given 30 days of historical readings (temperature, humidity, wind speed, pressure), the models predict the **temperature on the 31st day**.

Three models are implemented and compared:
- **LSTM** — captures sequential temporal dependencies
- **Transformer** — uses self-attention for global pattern recognition
- **Ensemble** — combines both using Optuna-optimized weights for best performance

---

## 📊 Dataset

**Daily Delhi Climate Dataset** containing:

| Feature       | Description                  |
|---------------|------------------------------|
| `meantemp`    | Mean daily temperature (°C)  |
| `humidity`    | Relative humidity (%)        |
| `wind_speed`  | Wind speed (km/h)            |
| `meanpressure`| Atmospheric pressure (hPa)   |

- **Preprocessing**: Features normalized with `StandardScaler`
- **Sequence Length**: 30 days → predict day 31
- **Split**: Historical data for training; recent data reserved for testing

---

## 🏗️ Architecture

### 1. LSTM Model
- Two stacked LSTM layers (128 → 64 units)
- Dropout (0.2) after each LSTM layer to prevent overfitting
- Dense output layer for single-step prediction
- Optimizer: Adam (lr=0.001) | Loss: MSE

### 2. Transformer Model
- Custom **Positional Encoding** layer to preserve temporal structure
- **Multi-head Self-Attention** to identify cross-timestep patterns
- Feed-forward layers with Layer Normalization and Residual Connections
- 8 attention heads | 128-unit feed-forward dimension
- Dense output layer for prediction

### 3. Enhanced Models
| Model | Enhancement |
|-------|-------------|
| LSTM | Bidirectional layers + Dropout 0.3 |
| Transformer | Positional encoding as layer + 8 attention heads |

### 4. Ensemble Model
- Weighted average of LSTM + Transformer predictions
- Weights optimized using **Optuna** to minimize RMSE on test set

---

## 📈 Results

| Model       | RMSE   | MAE    | R²     |
|-------------|--------|--------|--------|
| LSTM        | 0.2287 | 0.1744 | 0.9296 |
| Transformer | 0.2475 | 0.1895 | 0.9177 |
| **Ensemble**| **0.2286** | **0.1738** | **0.9298** |

> ✅ The **Ensemble model** achieved the best overall performance by combining the strengths of both architectures.

---

## 📁 Project Structure

```
📦 multivariate-ts-forecasting/
├── 📓 notebooks/
│   └── forecasting_lstm_transformer.ipynb   # Main Colab notebook
├── 📂 src/
│   ├── data_preprocessing.py               # Data loading & normalization
│   ├── lstm_model.py                       # LSTM architecture
│   ├── transformer_model.py                # Transformer architecture
│   ├── ensemble_model.py                   # Ensemble with Optuna
│   └── evaluate.py                         # RMSE, MAE, R² metrics
├── 📂 data/
│   └── README.md                           # Dataset download instructions
├── 📂 results/
│   └── model_comparison.png                # Performance visualization
├── requirements.txt
├── LICENSE
└── README.md
```

---

## 🚀 Getting Started

### Option 1: Run on Google Colab (Recommended)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1SsGQ0IHjnfh6qqUaGMvAwqRHmjDJfLFp?usp=sharing)

Click the badge above — no setup required.

---

### Option 2: Run Locally

**1. Clone the repository**
```bash
git clone https://github.com/YOUR_USERNAME/multivariate-ts-forecasting.git
cd multivariate-ts-forecasting
```

**2. Create a virtual environment**
```bash
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate
```

**3. Install dependencies**
```bash
pip install -r requirements.txt
```

**4. Download the dataset**

Get the [Daily Delhi Climate Dataset](https://www.kaggle.com/datasets/sumanthvrao/daily-climate-time-series-data) from Kaggle and place CSVs in the `data/` folder.

**5. Run the notebook**
```bash
jupyter notebook notebooks/forecasting_lstm_transformer.ipynb
```

---

## 🔮 Future Work

- **Multi-Region Forecasting** — extend to geospatial multi-city datasets
- **Extreme Weather Detection** — integrate anomaly detection for heatwaves/storms
- **Climate Change Analysis** — apply to long-term trend modeling
- **Domain Extensions** — renewable energy planning, agricultural yield forecasting

---

## 👤 Author

**Satyasai Gangadhar Baddireddi**  
Instructor: Akshay Rangamani

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
