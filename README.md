# Machine Health State Prediction

[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Kaggle](https://img.shields.io/badge/Dataset-Kaggle-20BEFF.svg)](https://www.kaggle.com/competitions/machine-health-state-main/data)

## 📌 Project Overview
This repository contains the code and methodology for the [Machine Health State](https://www.kaggle.com/competitions/machine-health-state-main/data) Kaggle competition. The goal of this project is to build a robust machine learning model capable of accurately predicting the health state (or remaining useful life) of industrial machines based on sensor telemetry data. 

Predictive maintenance helps in reducing downtime, minimizing maintenance costs, and preventing catastrophic equipment failures.

## 📊 Dataset
The dataset is provided via Kaggle and consists of time-series sensor data (e.g., temperature, pressure, vibration, etc.) collected from various machines. 

*   **`train.csv`**: Contains the training data with sensor readings and the target variable (machine state/health label).
*   **`test.csv`**: Contains the test data for which the health state needs to be predicted.
*   **`sample_submission.csv`**: The required format for submitting predictions to Kaggle.

*Note: Due to size constraints, the dataset is not included in this repository. Please download it directly from Kaggle and place the CSV files in the `data/raw/` directory.*

## 📂 Project Structure

```text
├── data/
│   ├── raw/               # Original downloaded Kaggle datasets
│   └── processed/         # Cleaned and engineered datasets
├── notebooks/             # Jupyter notebooks for EDA and prototyping
│   ├── 01_eda.ipynb
│   └── 02_feature_engineering.ipynb
├── src/                   # Source code for the pipeline
│   ├── data_loader.py     # Scripts to load and preprocess data
│   ├── features.py        # Feature engineering logic
│   ├── train.py           # Model training script
│   └── predict.py         # Inference and submission generation
├── models/                # Saved model binaries (e.g., .pkl, .pt)
├── requirements.txt       # Python dependencies
└── README.md              # Project documentation
```

## ⚙️ Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/machine-health-state.git
   cd machine-health-state
   ```

2. **Create a virtual environment (Recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. **Install the dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Download the data:**
   Download the dataset from Kaggle and place `train.csv` and `test.csv` inside the `data/raw/` folder.

## 🚀 Usage

### 1. Data Processing and Feature Engineering
Run the data preprocessing script to clean missing values, normalize sensor readings, and generate time-series features (rolling means, standard deviations, etc.).
```bash
python src/features.py
```

### 2. Model Training
Train the machine learning model (e.g., XGBoost, Random Forest, or an LSTM network). The script will output validation metrics and save the best model to the `models/` directory.
```bash
python src/train.py --config config.yaml
```

### 3. Inference and Submission
Generate predictions on `test.csv` to create the final submission file for Kaggle.
```bash
python src/predict.py
```
The output will be saved as `submission.csv` in the root directory.

## 🧠 Modeling Approach
*   **Data Preprocessing:** Handling missing sensor values using forward-fill/interpolation. Scaling continuous variables using `StandardScaler`.
*   **Feature Engineering:** Extracting statistical features (mean, min, max, variance) over sliding windows to capture temporal dependencies in the machine's behavior.
*   **Models Evaluated:** 
    *   Logistic Regression (Baseline)
    *   Random Forest Classifier
    *   XGBoost / LightGBM
*   **Evaluation Metric:** The models are primarily evaluated based on the competition's official metric (e.g., Macro F1-Score or Accuracy).

## 🏆 Results
*   **Local Cross-Validation Score:** `[Insert Score, e.g., 0.94 F1-Score]`
*   **Kaggle Public Leaderboard Score:** `[Insert Score]`
*   **Kaggle Private Leaderboard Score:** `[Insert Score]`

## 🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/yourusername/machine-health-state/issues).

## 📄 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
