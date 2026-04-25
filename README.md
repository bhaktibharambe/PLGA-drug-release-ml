# PLGA-drug-release-ml
ML model to predict PLGA nanoparticle drug release kinetics
# 💊 PLGA Drug Release ML Pipeline

A machine learning pipeline to predict drug release from PLGA (Poly Lactic-co-Glycolic Acid) nanoparticles using physicochemical and formulation features.

---

## 📌 Overview

This project builds a **Random Forest Regression** model to predict cumulative drug release (%) from PLGA-based nanoparticles, based on the dataset published by Bao et al. (2024).

> **Dataset:** Bao et al., 2024 — Mendeley Data  
> **DOI:** [https://doi.org/10.17632/zzvtdrcy76.2](https://doi.org/10.17632/zzvtdrcy76.2)

---

## 🧪 Features Used

| Feature | Description |
|---|---|
| `Drug MW` | Molecular weight of the drug |
| `Drug TPSA` | Topological polar surface area |
| `Drug LogP` | Lipophilicity (hydrophobic drugs only, LogP > 2) |
| `Polymer MW` | Molecular weight of PLGA polymer |
| `LA/GA` | Lactide to Glycolide ratio |
| `Particle Size` | Size of nanoparticles (nm) |
| `Drug Loading Capacity` | Drug mass fraction in the particle |
| `Drug Encapsulation Efficiency` | % drug successfully encapsulated |
| `log_time` | Log-transformed time (log(t + 1)) |

---

## 🔧 Preprocessing

- Dropped rows with missing values
- Filtered to **hydrophobic drugs only** (Drug LogP > 2) for domain consistency
- Log-transformed time to handle right-skewed distribution
- Normalized release values to **fraction scale (0–1)** where needed

---

## 🤖 Model

- **Algorithm:** Random Forest Regressor (`sklearn`)
- **Estimators:** 100 trees
- **Train/Test Split:** 80/20 (random state = 42)

---

## 📊 Evaluation Metrics

| Metric | Description |
|---|---|
| R² | Coefficient of determination |
| RMSE | Root Mean Square Error |
| MAE | Mean Absolute Error |

Results are printed to the console after training.

---

## 📁 Project Structure

```
├── plga.py                      # Main ML pipeline script
├── mp_dataset_processed.xlsx    # Input dataset (Bao et al., 2024)
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install pandas numpy matplotlib scikit-learn openpyxl
```

### Run

```bash
python plga.py
```

Make sure `mp_dataset_processed.xlsx` is in the same directory as the script.

---

## 📈 Output

- Console output with R², RMSE, and MAE scores
- Scatter plot: **Predicted vs Actual Release (%)**

---

## 📚 Citation

If you use this work or the dataset, please cite:

> Bao et al. (2024). PLGA Drug Release Dataset. *Mendeley Data*.  
> DOI: [https://doi.org/10.17632/zzvtdrcy76.2](https://doi.org/10.17632/zzvtdrcy76.2)

---

## 🙋 Author

Built as part of a pharmaceutical ML research project.
