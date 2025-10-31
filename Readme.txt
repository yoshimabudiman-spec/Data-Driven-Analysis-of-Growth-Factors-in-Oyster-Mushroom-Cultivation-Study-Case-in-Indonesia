Overview:
Modular AI pipeline for crop-yield prediction: preprocessing → EDA → feature selection under uncertainty (RFE) → model training/validation → explainability (permutation importance / SHAP-style).
Scopes: precision agriculture, AI for sustainability, intelligent systems for rural development.
Main notebook: Data_Driven_Analysis_of_Growth_Factors_in_Oyster_Mushroom_Cultivation_A_Case_Study_from_Indonesia’s_Market.ipynb
Reproducibility: fixed seeds, pinned deps, deterministic steps.


Please follow step-by-step as follows:

1) Open the project in Colab
Go to Google Colab → File → Open notebook → GitHub.
Paste your repo URL and open the main notebook:
Data_Driven_Analysis_of_Growth_Factors_in_Oyster_Mushroom_Cultivation_A_Case_Study_from_Indonesia’s_Market.ipynb

2) Run the setup cell (first cell)
# === Colab setup ===
import pathlib, sys

# Create folders
for p in ["data/raw","data/interim","data/processed","models","outputs"]:
    pathlib.Path(p).mkdir(parents=True, exist_ok=True)

# Install dependencies
!pip -q install --upgrade pip
!pip -q install numpy pandas scikit-learn matplotlib shap scipy joblib

# (Optional) add /src to import path if your repo has helper modules
if "src" not in sys.path:
    sys.path.append("src")

print("Colab environment ready.")

3) Add your data
In the left Files panel → upload your CSV to data/raw/
(e.g., data/raw/oyster_market_indonesia.csv).

4) Run the pipeline
From the Colab menu: Runtime → Run all (or run cells top-to-bottom).
The notebook will preprocess data, select features (RFE), train models, and generate figures/metrics.

5) View & save outputs
Cleaned/processed data → data/interim/, data/processed/
Trained models → models/
Figures/reports (if generated) → outputs/

(Optional) Make results persistent in Google Drive
from google.colab import drive
drive.mount('/content/drive')

# Example: copy outputs to Drive
!mkdir -p /content/drive/MyDrive/oyster-ml/outputs
!cp -r outputs/* /content/drive/MyDrive/oyster-ml/outputs/ 2>/dev/null || true


Notes
The target (yield) and feature mapping are set inside the notebook—adjust if your column names differ.
Random seeds are fixed for reproducibility.
If imports from src/ fail, re-run the setup cell to ensure src is on sys.path.
