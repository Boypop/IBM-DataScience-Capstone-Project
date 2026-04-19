# Repo Update Design — SpaceX Falcon 9 Landing Prediction

**Date:** 2026-04-19  
**Author:** Kounabé Paulin MIEN  
**Goal:** Transform the IBM Data Science Capstone Project repository into a professional portfolio piece that impresses recruiters, educators, and researchers.

---

## 1. Repository Structure

Reorganize from a flat root structure into logical folders:

```
IBM-DataScience-Capstone-Project/
├── notebooks/
│   ├── 01_data_collection_api.ipynb
│   ├── 02_web_scraping.ipynb
│   ├── 03_data_wrangling.ipynb
│   ├── 04_eda_sql.ipynb
│   ├── 05_eda_visualization.ipynb
│   ├── 06_interactive_maps.ipynb
│   └── 07_machine_learning.ipynb
├── app/
│   └── spacex_dash_app.py
├── data/
│   └── (CSV datasets)
├── presentation/
│   ├── capstone_presentation.pptx
│   └── capstone_presentation.pdf
├── assets/
│   └── (screenshots used in README)
├── README.md
├── requirements.txt
├── LICENSE
└── .gitignore
```

All notebooks are renamed with a numbered prefix and clean snake_case names to reflect their role in the data science pipeline.

---

## 2. README Structure

A premium README written entirely in English with the following sections:

1. **Title + Badges** — Python version, MIT License, IBM Certificate, Jupyter Notebook (via shields.io)
2. **Project Overview** — Business context: SpaceX charges ~$62M per Falcon 9 launch vs ~$165M for competitors because of first stage reuse. Goal: predict whether the first stage will land successfully to estimate launch cost.
3. **Key Results** — Table of all 4 ML models with CV accuracy and test accuracy, highlighting the winner (Decision Tree, 88.9% CV accuracy, 83.3% test accuracy).
4. **Project Pipeline** — ASCII or image flowchart: Data Collection → Web Scraping → Data Wrangling → EDA (SQL) → EDA (Visualization) → Interactive Maps → ML Prediction
5. **Notebooks** — Table with link, description, and tools used for each of the 7 notebooks
6. **Dashboard** — Screenshot of the Dash app + instructions to run it locally
7. **Technologies** — Python, Pandas, NumPy, Scikit-learn, Plotly, Dash, Folium, SQL, BeautifulSoup
8. **Installation & Usage** — Clear step-by-step setup instructions
9. **IBM Certificate** — Acknowledgment of the IBM Data Science Professional Certificate program

---

## 3. Technical Details

### Badges
Generated via shields.io:
- Python 3.x
- MIT License
- IBM Data Science Certificate
- Jupyter Notebook

### assets/ folder
Stores 2–3 key screenshots referenced in the README:
- SpaceX Launch Records Dashboard (Dash app)
- Interactive launch site map (Folium)
- ML confusion matrix or model comparison chart

### .gitignore updates
Add:
- `.ipynb_checkpoints/`
- `__pycache__/`
- `.env`
- `*.pyc`

### requirements.txt
Add `folium` which is used in notebook 06 but currently missing.

---

## 4. ML Results Summary (for README)

| Model | CV Accuracy | Test Accuracy |
|-------|-------------|---------------|
| Logistic Regression | 84.6% | 83.3% |
| SVM | 84.8% | 83.3% |
| **Decision Tree** | **88.9%** | **83.3%** |
| KNN | 84.8% | 83.3% |

**Best model: Decision Tree Classifier** (criterion=entropy, max_depth=4)

---

## 5. Out of Scope

- GitHub Pages website (can be added later as a follow-up)
- PowerPoint content corrections (handled separately)
- Notebook content edits (only renamed and moved, not modified)
