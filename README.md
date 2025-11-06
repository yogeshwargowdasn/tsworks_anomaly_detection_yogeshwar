#  Time Series Anomaly Detection for IoT Sensors

### Author: Yogeshwar Gowda S N

---

##  Project Overview
This project demonstrates an end-to-end anomaly detection pipeline for IoT sensor data using both:
1. **Isolation Forest (Unsupervised Machine Learning)**
2. **LSTM Autoencoder (Deep Learning – PyTorch)**

The goal is to identify unusual temperature readings that may indicate equipment malfunction or maintenance needs in a manufacturing environment.

Dataset used:
It uses a real-world dataset from the **Numenta Anomaly Benchmark (NAB)** – ambient temperature readings before a system failure.

---




##  Folder Structure
tsworks_anomaly/
│
├── data/
│   ├── ambient_temperature_system_failure.csv       # Raw dataset
│   ├── processed_temperature_features.csv           # Cleaned & engineered features
│
├── notebooks/
│   └── anomaly_detection.ipynb                      # Main Jupyter Notebook
│
├── outputs/
│   ├── isolation_forest_results.csv
│   ├── lstm_autoencoder_results.csv
│   ├── model_comparison_results.csv
│   └── plots/
│       ├── aws_temperature_timeseries.png
│       ├── scaled_temperature_features.png
│       ├── isolation_forest_anomalies.png
│       ├── lstm_autoencoder_errors.png
│       └── comparison_isoforest_lstm.png
│
├── summary.docx                                     # 2–3 page technical summary
├── requirements.txt                                 # Environment dependencies
└── README.md                                        # You are here


---

##  How to Run
### 1️⃣ Open the Project in VS Code

Download or clone the folder tsworks_anomaly/.

Open it directly in VS Code.

Ensure Python 3.10.x is installed (recommended version: 3.10.11).

You can verify your Python version by running:
python --version

---


2️⃣ Create and Activate a Virtual Environment

This keeps your dependencies isolated and prevents system-level conflicts.
# Create a virtual environment
python -m venv venv

# Activate it (Windows)
venv\Scripts\activate

# (If on Mac/Linux)
# source venv/bin/activate


After activation, your terminal should show something like:
(venv) PS E:\tsworks_anomaly>


---


## 3️⃣ Install All Required Packages

Make sure requirements.txt is in your project root, then run:
pip install -r requirements.txt


This will install:

1. pandas, numpy, scikit-learn, matplotlib, seaborn, statsmodels, tqdm, torch (PyTorch 2.5.1 with CUDA 12.1 support), jupyter, ipykernel, notebook
2. If your system does not have GPU/CUDA, use CPU-only PyTorch:
3. pip install torch==2.5.1+cpu torchvision==0.20.1+cpu torchaudio==2.5.1+cpu


---


## 4️⃣ Run the Jupyter Notebook

Launch Jupyter inside VS Code:

1. Open the Command Palette (Ctrl+Shift+P) → “Python: Select Interpreter”
2. Choose your virtual environment (venv)
3. Then open notebooks/anomaly_detection.ipynb
4. Run all cells sequentially (from top to bottom):

Cell 1: Sets up environment and folders

Cell 2: Downloads and loads dataset

Cell 3: Cleans and engineers new features

Cell 4: Trains Isolation Forest model (takes some time to train)

Cell 5: Trains LSTM Autoencoder (PyTorch) (takes some time to train)

Cell 6: Compares both and visualizes anomalies


---


## 5️⃣ View Your Outputs

All results are automatically saved inside:
outputs/
└── plots/

## Key result files:

    File	                   ----             Description
isolation_forest_results.csv =	Anomaly predictions from Isolation Forest
lstm_autoencoder_results.csv =	Anomaly predictions from LSTM Autoencoder
model_comparison_results.csv = 	Combined comparison of both models
comparison_isoforest_lstm.png = Visualization comparing detected anomalies


---


## 6️⃣ Interpreting the Results

1. The Isolation Forest model quickly identifies sharp temperature spikes.
2. The LSTM Autoencoder catches more subtle drifts over time.
3. Around 23–25% overlap in anomalies shows both models agree on critical points.
4. Use the visual plots in outputs/plots/ for deeper insights.


---


## 7️⃣ Optional: Re-run Feature Engineering or Models

You can modify (optional):

1. The sequence length (SEQ_LEN = 24) for LSTM
2. The contamination rate (0.01) for Isolation Forest
3. Or add new rolling features (e.g., rolling_mean_12h, etc.)
4. All parameters are clearly commented in the code for experimentati


---


## Tech Stack Summary

| Category         | Tools Used                         |
| ---------------- | ---------------------------------- |
| Language         | Python 3.10                        |
| Libraries        | pandas, numpy, matplotlib, seaborn |
| Machine Learning | scikit-learn (Isolation Forest)    |
| Deep Learning    | PyTorch (LSTM Autoencoder)         |
| Visualization    | Matplotlib, Seaborn                |
| Environment      | Jupyter Notebook in VS Code        |


---


## Future Improvements

1. Extend to multivariate sensor input (temperature + vibration + pressure)
2. Use adaptive thresholds (MAD or percentile-based)
3. Integrate live monitoring via Flask/FastAPI dashboard

