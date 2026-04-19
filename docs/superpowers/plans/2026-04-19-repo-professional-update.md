# Repository Professional Update — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Transform the IBM Data Science Capstone Project into a professional portfolio repository with clean structure, premium README, and proper documentation.

**Architecture:** Reorganize flat root structure into logical folders (`notebooks/`, `app/`, `data/`, `presentation/`, `assets/`), rename notebooks with numbered prefixes, write a premium English README with badges and ML results, and update supporting files.

**Tech Stack:** Python, Jupyter, Dash/Plotly, Folium, Scikit-learn, shields.io (badges), Git

---

## File Map

| Action | Path | Responsibility |
|--------|------|----------------|
| Create | `notebooks/` | All 7 renamed notebooks |
| Create | `app/` | Dash application |
| Create | `data/` | All CSV datasets |
| Create | `presentation/` | PPTX + PDF |
| Create | `assets/` | Screenshots for README |
| Modify | `README.md` | Premium portfolio README |
| Modify | `requirements.txt` | Add missing `folium` |
| Modify | `.gitignore` | Add standard Python ignores |

---

## Task 1: Create Folder Structure and Move Notebooks

**Files:**
- Create: `notebooks/01_data_collection_api.ipynb` (renamed from `jupyter-labs-spacex-data-collection-api.ipynb`)
- Create: `notebooks/02_web_scraping.ipynb` (renamed from `jupyter-labs-webscraping.ipynb`)
- Create: `notebooks/03_data_wrangling.ipynb` (renamed from `labs-jupyter-spacex-Data wrangling.ipynb`)
- Create: `notebooks/04_eda_sql.ipynb` (renamed from `jupyter-labs-eda-sql-coursera_sqllite.ipynb`)
- Create: `notebooks/05_eda_visualization.ipynb` (renamed from `edadataviz.ipynb`)
- Create: `notebooks/06_interactive_maps.ipynb` (renamed from `lab_jupyter_launch_site_location.ipynb`)
- Create: `notebooks/07_machine_learning.ipynb` (renamed from `SpaceX_Machine Learning Prediction_Part_5.ipynb`)

- [ ] **Step 1: Create the notebooks folder and move+rename all notebooks**

```bash
mkdir -p notebooks
git mv "jupyter-labs-spacex-data-collection-api.ipynb" "notebooks/01_data_collection_api.ipynb"
git mv "jupyter-labs-webscraping.ipynb" "notebooks/02_web_scraping.ipynb"
git mv "labs-jupyter-spacex-Data wrangling.ipynb" "notebooks/03_data_wrangling.ipynb"
git mv "jupyter-labs-eda-sql-coursera_sqllite.ipynb" "notebooks/04_eda_sql.ipynb"
git mv "edadataviz.ipynb" "notebooks/05_eda_visualization.ipynb"
git mv "lab_jupyter_launch_site_location.ipynb" "notebooks/06_interactive_maps.ipynb"
git mv "SpaceX_Machine Learning Prediction_Part_5.ipynb" "notebooks/07_machine_learning.ipynb"
```

- [ ] **Step 2: Verify the moves**

```bash
ls notebooks/
```

Expected output:
```
01_data_collection_api.ipynb
02_web_scraping.ipynb
03_data_wrangling.ipynb
04_eda_sql.ipynb
05_eda_visualization.ipynb
06_interactive_maps.ipynb
07_machine_learning.ipynb
```

- [ ] **Step 3: Commit**

```bash
git add -A
git commit -m "refactor: move notebooks to notebooks/ with clean numbered names"
```

---

## Task 2: Move App and Presentation

**Files:**
- Create: `app/spacex_dash_app.py` (renamed from `spacex-dash-app.py`)
- Create: `presentation/` (move `ds-capstone-template-coursera.pptx` here)

- [ ] **Step 1: Create app folder and move the Dash app**

```bash
mkdir -p app
git mv "spacex-dash-app.py" "app/spacex_dash_app.py"
```

- [ ] **Step 2: Create presentation folder and move the PPTX**

```bash
mkdir -p presentation
git mv "ds-capstone-template-coursera.pptx" "presentation/capstone_presentation.pptx"
```

- [ ] **Step 3: Verify**

```bash
ls app/ && ls presentation/
```

Expected:
```
spacex_dash_app.py
capstone_presentation.pptx
```

- [ ] **Step 3b: Fix CSV path in the Dash app**

After moving to `app/`, the line `spacex_df = pd.read_csv("spacex_launch_dash.csv")` will fail because the CSV will be in `data/`, not `app/`. Update `app/spacex_dash_app.py` line 9:

```python
# Change from:
spacex_df = pd.read_csv("spacex_launch_dash.csv")
# Change to:
spacex_df = pd.read_csv("../data/spacex_launch_dash.csv")
```

- [ ] **Step 4: Commit**

```bash
git add -A
git commit -m "refactor: move dash app to app/ and presentation to presentation/"
```

---

## Task 3: Add Data Files

**Files:**
- Create: `data/dataset_part_1.csv`
- Create: `data/spacex_web_scraped.csv`
- Create: `data/dataset_part_2.csv`
- Create: `data/dataset_part_3.csv`
- Create: `data/Spacex.csv`
- Create: `data/spacex_launch_geo.csv`
- Create: `data/spacex_launch_dash.csv`

- [ ] **Step 1: Create data folder**

```bash
mkdir -p data
```

- [ ] **Step 2: Copy all local CSV files into data/**

Manually copy all your local CSV files into the `data/` folder. The following files are needed (referenced by the notebooks and app):

| File | Used by |
|------|---------|
| `dataset_part_1.csv` | `01_data_collection_api.ipynb` |
| `spacex_web_scraped.csv` | `02_web_scraping.ipynb` |
| `dataset_part_2.csv` | `03_data_wrangling.ipynb`, `05_eda_visualization.ipynb`, `07_machine_learning.ipynb` |
| `dataset_part_3.csv` | `05_eda_visualization.ipynb`, `07_machine_learning.ipynb` |
| `Spacex.csv` | `04_eda_sql.ipynb` |
| `spacex_launch_geo.csv` | `06_interactive_maps.ipynb` |
| `spacex_launch_dash.csv` | `app/spacex_dash_app.py` |

- [ ] **Step 3: Verify all files are present**

```bash
ls data/
```

- [ ] **Step 4: Commit**

```bash
git add data/
git commit -m "data: add SpaceX datasets to data/"
```

---

## Task 4: Update .gitignore and requirements.txt

**Files:**
- Modify: `.gitignore`
- Modify: `requirements.txt`

- [ ] **Step 1: Update .gitignore**

Replace the content of `.gitignore` with:

```gitignore
# Python
__pycache__/
*.py[cod]
*.pyo
*.pyd
.Python
*.egg-info/
dist/
build/
.env
.venv
venv/
env/

# Jupyter
.ipynb_checkpoints/
*.ipynb_checkpoints

# OS
.DS_Store
Thumbs.db

# IDE
.vscode/
.idea/
*.swp
```

- [ ] **Step 2: Add folium to requirements.txt**

Open `requirements.txt` and add at the end:

```
folium>=0.12.0
```

Final `requirements.txt` should look like:
```
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.2
seaborn>=0.11.1
scikit-learn>=0.24.2
jupyter>=1.0.0
jupyterlab>=3.0.0
requests>=2.26.0
beautifulsoup4>=4.9.3
plotly>=5.0.0
dash>=1.20.0
dash-bootstrap-components>=1.0.0
sqlalchemy>=1.4.0
folium>=0.12.0
```

- [ ] **Step 3: Commit**

```bash
git add .gitignore requirements.txt
git commit -m "chore: update .gitignore and add folium to requirements"
```

---

## Task 5: Extract Screenshots from Notebooks

**Files:**
- Create: `assets/dashboard_preview.png`
- Create: `assets/launch_site_map.png`
- Create: `assets/ml_model_comparison.png`

- [ ] **Step 1: Create assets folder**

```bash
mkdir -p assets
```

- [ ] **Step 2: Extract confusion matrix / model comparison image from ML notebook**

Run this Python script to extract the first matplotlib figure from the ML notebook:

```python
import json, base64

with open("notebooks/07_machine_learning.ipynb", encoding="utf-8", errors="replace") as f:
    nb = json.load(f)

saved = 0
for i, cell in enumerate(nb["cells"]):
    for out in cell.get("outputs", []):
        data = out.get("data", {})
        if "image/png" in data:
            img_data = data["image/png"]
            if isinstance(img_data, list):
                img_data = "".join(img_data)
            with open(f"assets/ml_figure_{saved+1}.png", "wb") as f:
                f.write(base64.b64decode(img_data))
            print(f"Saved assets/ml_figure_{saved+1}.png (cell {i})")
            saved += 1
            if saved >= 4:
                break
    if saved >= 4:
        break
```

Run it:
```bash
python -c "<paste script above>"
```

- [ ] **Step 3: Inspect extracted images and keep the best ones**

```bash
ls assets/
```

Rename the most useful ones:
- The confusion matrix → `assets/ml_confusion_matrix.png`
- Any model comparison chart → `assets/ml_model_comparison.png`

```bash
# Example (adjust number based on what was extracted):
cp assets/ml_figure_1.png assets/ml_confusion_matrix.png
```

- [ ] **Step 4: Take a screenshot of the Dash dashboard (manual step)**

```bash
# Start the Dash app
cd app
python spacex_dash_app.py
```

Open `http://127.0.0.1:8050` in your browser, take a screenshot, save it as `assets/dashboard_preview.png`.

- [ ] **Step 5: Commit**

```bash
git add assets/
git commit -m "assets: add screenshots for README"
```

---

## Task 6: Write the Premium README

**Files:**
- Modify: `README.md`

- [ ] **Step 1: Replace README.md with the following content**

```markdown
# SpaceX Falcon 9 First Stage Landing Prediction

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)
![License](https://img.shields.io/badge/License-MIT-green)
![IBM](https://img.shields.io/badge/IBM-Data%20Science%20Certificate-054ADA?logo=ibm)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)

## Overview

SpaceX advertises Falcon 9 rocket launches at **$62 million**, significantly cheaper than competitors (~$165 million), largely because the first stage booster is recovered and reused. This project builds a **machine learning pipeline** to predict whether the Falcon 9 first stage will land successfully, enabling cost estimation for a hypothetical competitor bidding against SpaceX.

## Key Results

| Model | CV Accuracy | Test Accuracy |
|-------|:-----------:|:-------------:|
| Logistic Regression | 84.6% | 83.3% |
| Support Vector Machine | 84.8% | 83.3% |
| **Decision Tree** ✅ | **88.9%** | **83.3%** |
| K-Nearest Neighbors | 84.8% | 83.3% |

**Best model: Decision Tree Classifier** (`criterion=entropy`, `max_depth=4`)

## Project Pipeline

```
Data Collection (API) → Web Scraping → Data Wrangling
        ↓
EDA with SQL → EDA with Visualization → Interactive Maps
        ↓
Machine Learning Prediction
```

## Notebooks

| # | Notebook | Description | Tools |
|---|----------|-------------|-------|
| 1 | [Data Collection — API](notebooks/01_data_collection_api.ipynb) | Collect SpaceX launch data via REST API | Requests, Pandas |
| 2 | [Web Scraping](notebooks/02_web_scraping.ipynb) | Scrape launch records from Wikipedia | BeautifulSoup, Pandas |
| 3 | [Data Wrangling](notebooks/03_data_wrangling.ipynb) | Clean, encode, and prepare data for analysis | Pandas, NumPy |
| 4 | [EDA — SQL](notebooks/04_eda_sql.ipynb) | Explore data using SQL queries | SQLAlchemy, SQLite |
| 5 | [EDA — Visualization](notebooks/05_eda_visualization.ipynb) | Visual patterns and correlations | Matplotlib, Seaborn, Plotly |
| 6 | [Interactive Maps](notebooks/06_interactive_maps.ipynb) | Geospatial analysis of launch sites | Folium |
| 7 | [Machine Learning](notebooks/07_machine_learning.ipynb) | Train and evaluate 4 classification models | Scikit-learn, GridSearchCV |

## Dashboard

An interactive **Plotly Dash** dashboard to explore SpaceX launch records:

![Dashboard Preview](assets/dashboard_preview.png)

**Features:**
- Filter launches by site (All Sites / CCAFS LC-40 / VAFB SLC-4E / KSC LC-39A / CCAFS SLC-40)
- Pie chart of success rates per site
- Scatter plot of payload mass vs. launch outcome by booster version

**Run locally:**
```bash
cd app
python spacex_dash_app.py
# Open http://127.0.0.1:8050
```

## Technologies

| Category | Tools |
|----------|-------|
| Data Processing | Python, Pandas, NumPy |
| Visualization | Matplotlib, Seaborn, Plotly |
| Machine Learning | Scikit-learn (LR, SVM, DT, KNN, GridSearchCV) |
| Interactive Analytics | Dash, Folium |
| Data Collection | Requests, BeautifulSoup, SQLAlchemy |

## Installation

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/IBM-DataScience-Capstone-Project.git
cd IBM-DataScience-Capstone-Project

# 2. Install dependencies
pip install -r requirements.txt

# 3. Launch Jupyter
jupyter notebook
# Open any notebook from the notebooks/ folder
```

## Project Structure

```
IBM-DataScience-Capstone-Project/
├── notebooks/          # 7 Jupyter notebooks (full pipeline)
├── app/                # Interactive Dash dashboard
├── data/               # SpaceX datasets (CSV)
├── presentation/       # Final capstone presentation
├── assets/             # Screenshots and visuals
├── requirements.txt
└── README.md
```

## Certificate

This project is the capstone of the [IBM Data Science Professional Certificate](https://www.coursera.org/professional-certificates/ibm-data-science) on Coursera — a 10-course program covering data science fundamentals, Python, SQL, data visualization, machine learning, and more.

## License

This project is licensed under the [MIT License](LICENSE).
```

- [ ] **Step 2: Update the GitHub username in the clone URL**

In the README, replace `YOUR_USERNAME` with your actual GitHub username:
```
https://github.com/Boypop/IBM-DataScience-Capstone-Project.git
```

- [ ] **Step 3: Verify the README renders correctly (optional)**

```bash
# If you have grip installed:
pip install grip
grip README.md
# Open http://localhost:6419 to preview
```

- [ ] **Step 4: Commit**

```bash
git add README.md
git commit -m "docs: rewrite README as premium portfolio page with badges and results"
```

---

## Task 7: Final Verification and Cleanup

- [ ] **Step 1: Verify root directory is clean**

```bash
ls -la
```

Expected root contents:
```
.git/
.gitignore
LICENSE
README.md
app/
assets/
data/
docs/
notebooks/
presentation/
requirements.txt
```

No stray `.ipynb` or `.py` files should remain at the root.

- [ ] **Step 2: Check git status is clean**

```bash
git status
```

Expected: `nothing to commit, working tree clean`

- [ ] **Step 3: Push to GitHub**

```bash
git push origin main
```

- [ ] **Step 4: Verify on GitHub**

Open your repository on GitHub and confirm:
- README renders with badges and tables
- Folder structure is visible
- Dashboard screenshot displays in README
