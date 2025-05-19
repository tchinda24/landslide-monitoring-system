# 🌍 Intelligent Landslide Prediction and Alarm System

A real-time, machine learning–based system for predicting landslides using IoT sensors and a trained ML model deployed on a local server.

---

## 📌 Project Description

This project aims to reduce the risk of landslides by detecting critical environmental conditions using sensors, sending the data via Wi-Fi from an ESP32 microcontroller to a Python server, and triggering alerts using a trained machine learning model.

---

## ⚙️ System Components

### 🔧 Hardware
- ESP32 microcontroller
- Soil moisture sensor
- Rain gauge
- MPU6050 (Tilt & Vibration sensor)
- DHT22 (Temperature & Humidity)
- Optional: SIM800L (for SMS alerts)

### 💻 Software Stack
- Python 3.10+
- Flask (for local server)
- scikit-learn (ML model)
- pandas, numpy, seaborn, matplotlib
- SHAP (for explainability)
- Arduino IDE (ESP32 firmware)

---

## 🧠 Machine Learning Model

### ✅ Model Details
- Model type: `RandomForestClassifier` (plus SVM/XGBoost comparisons)
- Target output: 
  - `0` = Safe
  - `1` = Moderate Risk
  - `2` = Danger (High Risk)
- Input features:
  - `rainfall_mm`, `soil_moisture_percent`, `slope_angle_deg`
  - `ground_vibration_mg`, `temperature_c`, `humidity_percent`, etc.
- Evaluation:
  - Confusion Matrix
  - ROC Curve & AUC Score
  - SHAP Feature Importance

### ✅ Training Dataset
- Simulated landslide dataset based on real-world environmental patterns
- Includes timestamp, elevation, vegetation index, and previous events

---

## 🌐 Real-Time Data Flow

```plaintext
[ESP32 + Sensors]
        ↓ Wi-Fi
Sends JSON data to Flask server
        ↓
[Python server on Laptop]
Scales input → Runs ML model → Triggers alert
