[README.md](https://github.com/user-attachments/files/32232419/README.md)
# renewable-energy-adoption-classification
Multiclass classification of countrie# 🌿 Global Sustainable Energy Analysis (2000–2020)
*Predicting renewable energy adoption through demographic, economic, and infrastructure metrics.*

---

## 📌 Project Overview
This project presents an end-to-end Machine Learning pipeline aimed at predicting a country's share of renewable energy in final energy consumption. 

Using historical global data from 2000 to 2020, the goal is to classify countries into three distinct categories (**Low**, **Medium**, **High** renewable energy share) while handling geographical and temporal structures without data leakage.

---

## 🛠️ Key Features & Workflow

1. **Data Cleaning & Integration:**
   * Replaced static/anomalous population density records with dynamic yearly metrics using external data sources.
   * Addressed missing values across features using domain-specific thresholds and median imputations.

2. **Feature Engineering:**
   * Created normalized per-capita features: `estimated_population`, `co2_per_capita`, and `people_without_electricity`.
   * Evaluated feature distribution skewness and applied logarithmic transformations (`log1p`) to highly asymmetric variables.

3. **Leakage Prevention & Group Splitting:**
   * Splitted data via **`GroupShuffleSplit`** based on country entities (`Entity`) to ensure no single country overlaps between training and test sets.
   * Removed direct target-leakage features (e.g., individual TWh breakdowns, derived renewable ratios).

4. **Modeling & Cross-Validation:**
   * Evaluated **Logistic Regression**, **Decision Trees**, and **Random Forests**.
   * Performed validation using **`StratifiedGroupKFold`** to preserve class balance and geographic grouping during cross-validation.
   * **Best Model:** Random Forest Classifier achieving **69% Accuracy** and a **0.70 Macro F1-Score** on unseen countries.

---

## 📁 Repository Structure

```text
├── data/
│   ├── global-data-on-sustainable-energy.csv    # Primary dataset
│   └── density.csv                              # External population density dataset
├── renewable-energy-machine-learning.ipynb      # Main Jupyter Notebook
├── requirements.txt                             # Python dependencies
└── README.md                                    # Project documentation
```
---

## 🛠️ Requirements

* **Python:** 3.10+
* **Core Libraries:** pandas, numpy, matplotlib, scikit-learn
---

## 📦 Installation

Clone the repository:

```bash
git clone https://github.com/HackCollus/global-sustainable-energy-ml.git
cd global-sustainable-energy-ml
```

Install the required packages:

```bash
pip install -r requirements.txt
```s' renewable energy adoption (low/medium/high) from socio-economic and energy indicators. End-to-end scikit-learn pipeline: per-country split to avoid panel leakage, feature engineering, Logistic Regression / Decision Tree / Random Forest.
