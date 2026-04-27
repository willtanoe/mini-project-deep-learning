# Mini Project: Machine Learning Fundamentals

> Deep Learning for Electrical Engineering — S2 Teknik Elektro, Universitas Telkom

Pipeline machine learning end-to-end pada dua domain: klasifikasi penyakit kardiovaskular dan prediksi konsumsi energi bangunan.

---

## Anggota Kelompok

| Nama | NIM |
|------|-----|
| Muhamad Wildan Rizky |201012520001|
| Haamid Ahmad Saragih |201012520025|

---

## Struktur Repository

```
.
├── dataset/
│   ├── cardio_train.csv          # Dataset 1: Cardiovascular Disease (Kaggle)
│   └── energy_data.csv           # Dataset 2: Appliances Energy Prediction (UCI)
│
├── notebook/
│   ├── dataset1_kardiovaskular.ipynb
│   └── dataset2_energi.ipynb
│
└── README.md
```

---

## Dataset

| # | Nama | Sumber | Sampel | Task |
|---|------|--------|--------|------|
| 1 | Cardiovascular Disease Dataset | [Kaggle](https://www.kaggle.com/datasets/sulianova/cardiovascular-disease-dataset) | ~70.000 | Binary Classification |
| 2 | Appliances Energy Prediction | [UCI / Kaggle](https://www.kaggle.com/datasets/loveall/appliances-energy-prediction) | ~19.000 | Regression |

> Dataset tidak disertakan dalam repository karena ukuran file. Unduh dari tautan di atas dan letakkan di folder `dataset/`.

---

## Pipeline

Setiap dataset diproses melalui 4 tahap berurutan:

```
Feature Engineering  →  Baseline Model  →  Hyperparameter Tuning  →  Analisis Laporan
```

Seluruh eksperimen dijalankan pada dua variasi split: **80:20** dan **70:30**.

---

## Dataset 1: Klasifikasi Kardiovaskular

**Model yang dievaluasi:** Logistic Regression, KNN, Decision Tree, Random Forest, SVM

**Metrik:** Accuracy, Precision, Recall, F1-Score, CV Accuracy (StratifiedKFold, k=5)

**Preprocessing:**
- Konversi `age` dari hari ke tahun
- Filter outlier tekanan darah berdasarkan batas klinis
- StandardScaler
- SelectKBest `f_classif`, top-8 fitur

**Tuning:** GridSearchCV pada Logistic Regression dan SVM, metrik F1-Score

**Model terbaik:** Logistic Regression (Tuned)

---

## Dataset 2: Prediksi Konsumsi Energi

**Model yang dievaluasi:** Linear Regression, SVR (kernel RBF)

**Metrik:** MAE, MSE, RMSE, R², CV R² (KFold, k=5)

**Preprocessing:**
- Ekstraksi fitur temporal dari kolom `date` (hour, day_of_week, month, is_weekend)
- Target `energy_total = Appliances + lights`
- Hapus kolom `rv1`, `rv2`
- Outlier removal IQR pada target
- StandardScaler
- SelectKBest `f_regression`, top-15 fitur

**Tuning:** GridSearchCV untuk Linear Regression, RandomizedSearchCV (16 iterasi) untuk SVR, metrik R²

**Model terbaik:** SVR (Tuned, kernel RBF)

---

## Requirements

```
python >= 3.9
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
```

Install semua dependency:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

---

## Cara Menjalankan

1. Clone repository ini:

```bash
git clone https://github.com/willtanoe/mini-project-deep-learning.git
cd mini-project-deep-learning
```

2. Unduh dataset dari tautan di atas dan letakkan di folder `dataset/`

3. Jalankan notebook:

```bash
jupyter notebook
```

4. Buka `notebook/dataset1_kardiovaskular.ipynb` atau `notebook/dataset2_energi.ipynb` dan jalankan seluruh cell secara berurutan (Run All)

---

## Referensi

- S. Ulianova, *Cardiovascular Disease Dataset*, Kaggle, 2019.
- L. M. Candanedo, V. Feldheim, D. Deramaix, "Data driven prediction models of energy use of appliances in a low-energy house," *Energy and Buildings*, vol. 140, pp. 81–97, 2017.
- F. Pedregosa et al., "Scikit-learn: Machine learning in Python," *JMLR*, vol. 12, pp. 2825–2830, 2011.

---

*Program Studi S2 Teknik Elektro — Universitas Telkom, Bandung, Indonesia*
