# Saudi Used Car Price Prediction

## 📌 Overview
Proyek ini bertujuan untuk mengembangkan model **Machine Learning** yang mampu memprediksi harga mobil bekas di Arab Saudi berdasarkan data historis yang tersedia. Dengan menggunakan algoritma regresi, terutama **Xtreme Gradient Boosting (XGBoost)**, model ini diharapkan dapat memberikan estimasi harga yang akurat dan membantu berbagai pemangku kepentingan seperti dealer mobil, pembeli, penjual, dan platform e-commerce otomotif dalam menentukan harga yang wajar.

## 🚀 Features
- **Prediksi harga mobil bekas** berdasarkan fitur kendaraan seperti merek, tahun pembuatan, kapasitas mesin, jarak tempuh, dan lainnya.
- **Data preprocessing lengkap** mencakup data cleaning, handling missing values, outlier removal, encoding, dan scaling.
- **Evaluasi model dengan metrik standar** seperti RMSE, MAE, MAPE, dan R².
- **Hyperparameter tuning** menggunakan RandomizedSearchCV untuk meningkatkan performa model.
- **Visualisasi feature importance** untuk memahami faktor yang paling berpengaruh terhadap harga.
- **Sistem deployment-ready** dengan model yang sudah disimpan dalam format `.pkl` untuk digunakan dalam aplikasi real-world.

## 📊 Dataset
Dataset yang digunakan dalam proyek ini berasal dari situs otomotif yang berisi informasi tentang **mobil bekas di Arab Saudi**. Dataset mencakup beberapa fitur utama:
- **Type** (Jenis mobil bekas)
- **Region** (Lokasi penjualan)
- **Make** (Merek mobil)
- **Gear_Type** (Jenis transmisi)
- **Origin** (Asal mobil)
- **Options** (Fitur tambahan)
- **Year** (Tahun pembuatan)
- **Engine_Size** (Ukuran mesin dalam liter)
- **Mileage** (Jarak tempuh kendaraan)
- **Price** (Harga jual kendaraan)

## 🏗️ Model Development
### 1️⃣ **Data Cleaning & Preprocessing**
- Menghapus **duplikasi dan data tidak valid**
- Menangani **outliers** dengan metode IQR
- **Encoding** kategori dengan **Binary Encoding** dan **One-Hot Encoding**
- **Feature Scaling** menggunakan **Standard Scaler** untuk fitur numerik

### 2️⃣ **Model Training & Evaluation**
Beberapa algoritma yang diuji dalam proyek ini:
- **Base Models:**
  - Linear Regression
  - K-Nearest Neighbors (KNN)
  - Decision Tree
  - Ridge Regression, Lasso Regression, Elastic Net
- **Ensemble Models:**
  - Random Forest Regressor
  - AdaBoost Regressor
  - Gradient Boosting Regressor
  - **XGBoost (Best Model)** ✅

### 3️⃣ **Hyperparameter Tuning**
Dilakukan **RandomizedSearchCV** untuk menemukan kombinasi parameter terbaik dari **XGBoost**.

## 🎯 Model Performance (Setelah Hyperparameter Tuning)
| Model                    | RMSE        | MAE         | MAPE     | R²      |
|--------------------------|------------|------------|---------|---------|
| **Loaded XGBoost Model** | 26353.130257 | 15419.080626 | 1.184472 | 0.838573 |

## 📈 Feature Importance
Fitur yang paling berkontribusi dalam prediksi harga:
1. **Make (Merek Mobil)** 🚗
2. **Year (Tahun Pembuatan)** 📆
3. **Engine_Size (Ukuran Mesin)** ⚙️
4. **Mileage (Jarak Tempuh)** 📏
5. **Gear_Type (Jenis Transmisi)** ⚡

## 🔧 Cara Menggunakan Model

### **Menguji Model dengan Data Baru**
```python
import pickle
import pandas as pd

# Load model
with open('models/best_xgb_model.pkl', 'rb') as file:
    model = pickle.load(file)

# Contoh data input
sample_input = pd.DataFrame({
    'Type': ['Hilux'],
    'Region': ['Dammam'],
    'Make': ['Toyota'],
    'Gear_Type': ['Automatic'],
    'Origin': ['Saudi'],
    'Options': ['Full'],
    'Year': [2018],
    'Engine_Size': [2.8],
    'Mileage': [110500]
})

# Preprocess data (sesuai dengan pipeline di training)
# ... [kode preprocessing di sini]

# Prediksi harga
predicted_price = model.predict(sample_input)
print(f'Predicted Price: {predicted_price[0]}')
```

## 🔮 Future Improvements
- 🔹 **Integrasi API:** Membuat API dengan **FastAPI/Flask** untuk prediksi harga secara real-time.
- 🔹 **Pembaruan Dataset:** Menambah data dari sumber baru agar lebih representatif.
- 🔹 **Deep Learning Model:** Menerapkan metode **Neural Network** untuk eksplorasi alternatif model.
- 🔹 **Dashboard Visualisasi:** Menggunakan **Streamlit** atau **Dash** untuk menampilkan insight harga mobil.

🚗💨 **"Accurate Pricing, Smarter Decisions!"**

