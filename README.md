# ⚙️ AMES: Automated Machine Learning Expert System

> A full-stack microservice platform that automates the end-to-end machine learning workflow — from data ingestion and cleaning to model training, evaluation, and result visualization — through a React frontend and Flask-based backend services.

**📄 Published at IEEE COM-IT-CON 2022** — [View Paper](https://ieeexplore.ieee.org/document/9850909)

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────┐
│            React Frontend               │
│   (Upload data, configure, view results)│
└────────────────┬────────────────────────┘
                 │ REST API calls
       ┌─────────┴──────────┐
       │                    │
┌──────▼──────┐    ┌────────▼────────┐
│ Data Cleaner│    │  Model Builder  │
│ Flask API   │    │  ML Pipeline    │
│             │    │                 │
│ categorical │    │  AutoML         │
│ continuous  │    │  Model select   │
│ image       │    │  Evaluation     │
└─────────────┘    └─────────────────┘
```

---

## 🎯 Problem

Building a machine learning model for a new dataset requires significant manual effort — data preprocessing, feature engineering, algorithm selection, hyperparameter tuning, and evaluation. AMES automates this entire workflow through a unified web platform, enabling consistent and reproducible model development for both classification and regression tasks.

---

## ⚙️ What AMES Automates

| Task | Service | Description |
|------|---------|-------------|
| **Data Ingestion** | Frontend | Upload CSV, image, or structured datasets via UI |
| **Data Cleaning** | data-cleaner | Handles categorical encoding, continuous scaling, and image preprocessing |
| **Model Training** | model-builder | Benchmarks multiple algorithms, selects the most accurate |
| **Hyperparameter Tuning** | model-builder | Optimizes model parameters via AutoML (EvalML) |
| **Result Visualization** | Frontend | Displays model comparisons, metrics, and performance charts |

---

## 🛠️ Tech Stack

| Layer | Tools |
|-------|-------|
| Frontend | React, Firebase, JavaScript |
| Backend Services | Python, Flask, REST APIs |
| ML Pipeline | EvalML, Scikit-learn, PyTorch (CNN) |
| Data Processing | Pandas, NumPy |
| Auth & Storage | Firebase |
| Containerization | Docker, Docker Compose |

---

## 📁 Repository Structure

```
├── frontend/                  # React web application
│   └── src/
│       ├── Components/        # Reusable UI components
│       ├── Pages/             # Route-level page components
│       ├── App.js             # App entry point
│       └── firebase.js        # Firebase config and auth
├── data-cleaner/              # Flask microservice for data preprocessing
│   ├── api.py                 # REST API endpoints
│   ├── categorical.py         # Categorical feature encoding
│   ├── continuous.py          # Continuous feature scaling
│   ├── image.py               # Image data preprocessing
│   └── requirements.txt
├── model-builder/             # ML training and evaluation pipeline
│   ├── notebooks/             # Experimentation notebooks
│   ├── model.pkl              # Serialized trained model artifact
│   └── requirements.txt
└── README.md
```

---

## 🚀 How to Run

### Option 1 — Docker Compose (recommended)
Spins up all services together with a single command:
```bash
docker-compose up --build
```
Then open `http://localhost:3000` in your browser.

| Service | URL |
|---------|-----|
| Frontend | http://localhost:3000 |
| Data Cleaner API | http://localhost:5001 |
| Model Builder API | http://localhost:5002 |

### Option 2 — Run services individually

**Frontend**
```bash
cd frontend
npm install
npm start
```

**Data Cleaner Service**
```bash
cd data-cleaner
pip install -r requirements.txt
python api.py
```

**Model Builder**
```bash
cd model-builder
pip install -r requirements.txt
jupyter notebook
```
