# Mini Project: Deep Learning Major Assignment

Pipeline machine learning on two domains: cardiovascular disease classification and building energy consumption prediction.

---

## Team Members

| Name | Student ID |
|------|------------|
| Muhamad Wildan Rizky | 201012520001 |
| Haamid Ahmad Saragih | 201012520025 |

---

## Repository Structure

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

## Datasets

| # | Name | Source | Samples | Task |
|---|------|--------|---------|------|
| 1 | Cardiovascular Disease Dataset | [Kaggle](https://www.kaggle.com/datasets/sulianova/cardiovascular-disease-dataset) | ~70,000 | Binary Classification |
| 2 | Appliances Energy Prediction | [UCI / Kaggle](https://www.kaggle.com/datasets/loveall/appliances-energy-prediction) | ~19,000 | Regression |

> Datasets are not included in this repository due to file size. Download from the links above and place them in the `dataset/` folder.

---

## Pipeline

Each dataset is processed through 4 sequential stages:

```
Feature Engineering  →  Baseline Model  →  Hyperparameter Tuning  →  Report Analysis
```

All experiments are run under two split ratios: **80:20** and **70:30**.

---

## Dataset 1: Cardiovascular Disease Classification

**Models evaluated:** Logistic Regression, KNN, Decision Tree, Random Forest, SVM

**Metrics:** Accuracy, Precision, Recall, F1-Score, CV Accuracy (StratifiedKFold, k=5)

**Preprocessing:**
- Convert `age` from days to years
- Filter blood pressure outliers based on clinical bounds
- StandardScaler
- SelectKBest `f_classif`, top-8 features

**Tuning:** GridSearchCV on Logistic Regression and SVM, metric F1-Score

**Best model:** Logistic Regression (Tuned)

---

## Dataset 2: Building Energy Consumption Prediction

**Models evaluated:** Linear Regression, SVR (RBF kernel)

**Metrics:** MAE, MSE, RMSE, R², CV R² (KFold, k=5)

**Preprocessing:**
- Extract temporal features from `date` column (hour, day_of_week, month, is_weekend)
- Target `energy_total = Appliances + lights`
- Drop columns `rv1`, `rv2`
- IQR outlier removal on target
- StandardScaler
- SelectKBest `f_regression`, top-15 features

**Tuning:** GridSearchCV for Linear Regression, RandomizedSearchCV (16 iterations) for SVR, metric R²

**Best model:** SVR (Tuned, RBF kernel)

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

Install all dependencies:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

---

## How to Run

1. Clone this repository:

```bash
git clone https://github.com/willtanoe/mini-project-deep-learning.git
cd mini-project-deep-learning
```

2. Download the datasets from the links above and place them in the `dataset/` folder

3. Launch Jupyter:

```bash
jupyter notebook
```

4. Open `notebook/dataset1_kardiovaskular.ipynb` or `notebook/dataset2_energi.ipynb` and run all cells in order (Run All)

---

## References

- S. Ulianova, *Cardiovascular Disease Dataset*, Kaggle, 2019.
- L. M. Candanedo, V. Feldheim, D. Deramaix, "Data driven prediction models of energy use of appliances in a low-energy house," *Energy and Buildings*, vol. 140, pp. 81–97, 2017.
- F. Pedregosa et al., "Scikit-learn: Machine learning in Python," *JMLR*, vol. 12, pp. 2825–2830, 2011.

---

*Master's Program in Electrical Engineering — Deep Learning for Electrical Engineering — Telkom University, Bandung, Indonesia*
