<div align="center">

# Phishing Detection & Prevention System

**AI/ML-powered URL and email phishing detection**

[![Python](https://img.shields.io/badge/Python-3.10+-3776ab?style=for-the-badge&logo=python&logoColor=white)](.)
[![FastAPI](https://img.shields.io/badge/FastAPI-backend-009688?style=for-the-badge&logo=fastapi)](.)
[![React](https://img.shields.io/badge/React-frontend-61dafb?style=for-the-badge&logo=react)](.)
[![ML](https://img.shields.io/badge/ML-500K%20URL%20dataset-ff6b35?style=for-the-badge)](.)
[![Accuracy](https://img.shields.io/badge/accuracy-85%25-22cc66?style=for-the-badge)](.)

*Real-time phishing URL detection · Machine learning classification · Sub-10-second analysis*

---

</div>

## What is this?

A full-stack AI-powered phishing detection system that analyses URLs in real time and classifies them as phishing or legitimate using a trained machine learning model. Built with a FastAPI backend, React frontend, and an ML pipeline trained on a 500,000-URL dataset.

Designed as a practical defensive security tool — the kind a SOC analyst or security engineer would actually use to triage suspicious links.

---

## Key Results

| Metric | Result |
|---|---|
| Training dataset size | 500,000 URLs |
| Detection accuracy | **85%** |
| End-to-end analysis time | **< 10 seconds** |
| False positive rate | Minimised via feature engineering |

---

## Features

- **Real-time URL analysis** — paste any URL, get a phishing/legitimate verdict instantly
- **ML classification** — trained on 500K URLs with feature extraction (URL length, special characters, domain age indicators, subdomain depth, HTTPS presence, suspicious keywords)
- **FastAPI backend** — RESTful API with clean `/predict` endpoint
- **React frontend** — clean UI for URL submission and result display
- **Confidence scoring** — model outputs probability alongside binary classification

---

## Project Structure

```
Phishing-Detection-Project/
├── backend/                  # FastAPI application
│   ├── main.py               # API endpoints
│   ├── model/                # Trained ML model files
│   └── utils/                # Feature extraction logic
├── ml_model/                 # Model training pipeline
│   ├── train.py              # Training script
│   ├── features.py           # Feature engineering
│   └── evaluate.py           # Model evaluation
├── phishing-detection-frontend/  # React application
│   ├── src/
│   │   ├── App.jsx           # Main component
│   │   └── components/       # UI components
│   └── public/
├── requirements.txt          # Python dependencies
└── .gitignore
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| ML Model | Scikit-learn / Python |
| Feature Engineering | URL parsing, regex, custom extractors |
| Backend API | FastAPI (Python) |
| Frontend | React.js |
| Dataset | 500,000 labelled URLs |

---

## Installation & Setup

### Backend

```bash
# Clone the repo
git clone https://github.com/ANIMAALS/Phishing-Detection-Project.git
cd Phishing-Detection-Project

# Install dependencies
pip install -r requirements.txt

# Start FastAPI server
cd backend
uvicorn main:app --reload
```

API will be running at `http://localhost:8000`

### Frontend

```bash
cd phishing-detection-frontend
npm install
npm start
```

Frontend will be running at `http://localhost:3000`

---

## API Usage

**Endpoint:** `POST /predict`

```bash
curl -X POST "http://localhost:8000/predict" \
     -H "Content-Type: application/json" \
     -d '{"url": "http://suspicious-login.xyz/paypal/verify"}'
```

**Response:**
```json
{
  "url": "http://suspicious-login.xyz/paypal/verify",
  "prediction": "phishing",
  "confidence": 0.94
}
```

---

## How It Works

```
User submits URL
      ↓
Feature Extraction
  · URL length
  · Special character count (@, -, //)
  · Subdomain depth
  · HTTPS presence
  · Suspicious keyword match
  · Domain structure analysis
      ↓
ML Model Inference
  · Trained on 500K URLs
  · Binary classification
  · Confidence score output
      ↓
Result returned to UI (< 10 seconds)
```

---

## Model Training

The model was trained on a balanced dataset of 500,000 URLs — 250,000 phishing, 250,000 legitimate. Feature engineering extracts 15+ URL-based characteristics without making external DNS or WHOIS calls, keeping inference fast and offline-capable.

```bash
# Retrain the model
cd ml_model
python train.py
```

---

## Author

**Anirudh N.S.** — Cybersecurity Student, Dayananda Sagar University, Bengaluru

Part of a cybersecurity project portfolio alongside [WatchDog 2.4](https://github.com/ANIMAALS/WatchDog-2.4) and [KeyForge](https://github.com/ANIMAALS/KeyForge).
