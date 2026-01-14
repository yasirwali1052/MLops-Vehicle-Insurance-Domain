# 🚗 Vehicle Insurance MLOps Pipeline

> **An end-to-end, production‑ready MLOps project** that demonstrates how real‑world machine learning systems are built, versioned, validated, deployed, and served using modern industry tools.

This project is designed to **impress recruiters and engineers** by showcasing **clean architecture, scalable pipelines, cloud deployment, CI/CD automation, and best MLOps practices**.

---

## 🌟 Key Highlights

* 🔁 **End-to-End MLOps Lifecycle** (Ingestion → Validation → Training → Evaluation → Deployment)
* ☁️ **Cloud‑native architecture using AWS (S3, ECR, EC2, IAM)**
* 🐳 **Dockerized application with CI/CD using GitHub Actions**
* 🧠 **Modular, production‑grade Python codebase (no notebooks-only ML)**
* 🗄️ **MongoDB Atlas as real-world data source**
* 🚀 **FastAPI-based prediction & training service**

---

## 🧱 Project Architecture

```
MongoDB Atlas
      ↓
Data Ingestion
      ↓
Data Validation
      ↓
Data Transformation
      ↓
Model Trainer
      ↓
Model Evaluation
      ↓
Model Registry (AWS S3)
      ↓
Model Pusher
      ↓
FastAPI App (Docker)
      ↓
AWS EC2 (via GitHub Actions CI/CD)
```

---

## 🛠️ Tech Stack

### 👨‍💻 Programming & ML

* Python 3.10
* Scikit-learn
* Pandas, NumPy
* FastAPI

### 📦 MLOps & Engineering

* Modular pipeline design
* Custom logging & exception handling
* Artifact‑based pipeline tracking
* Schema‑driven data validation

### 🗄️ Data Layer

* MongoDB Atlas (cloud NoSQL)

### ☁️ Cloud & DevOps

* AWS S3 (model registry)
* AWS ECR (Docker image registry)
* AWS EC2 (production deployment)
* IAM (secure access)

### 🔁 CI/CD & Automation

* GitHub Actions
* Self‑hosted EC2 runner
* Docker & DockerHub base images

---

## 📁 Project Structure

```
vehicle-insurance-mlops/
│
├── src/
│   ├── components/          # Pipeline components
│   ├── configuration/       # DB & AWS configs
│   ├── constants/           # Centralized constants
│   ├── entity/              # Config & artifact entities
│   ├── exception/           # Custom exceptions
│   ├── logger/              # Logging system
│   ├── utils/               # Utility functions
│
├── notebooks/               # EDA & experiments
├── templates/               # HTML templates
├── static/                  # CSS / static assets
├── app.py                   # FastAPI entry point
├── demo.py                  # Pipeline trigger
├── Dockerfile               # Container setup
├── requirements.txt         # Dependencies
├── setup.py                 # Local package installation
├── pyproject.toml           # Modern packaging config
└── .github/workflows/       # CI/CD pipeline
```

---

## ⚙️ Setup & Installation

### 1️⃣ Create Project Template

```bash
python template.py
```

### 2️⃣ Local Package Setup

* Configure `setup.py` and `pyproject.toml`
* Enables clean imports across the project

📄 Learn more: `crashcourse.txt`

### 3️⃣ Environment Setup

```bash
conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt
```

Verify installation:

```bash
pip list
```

---

## 🗄️ MongoDB Atlas Setup

* Create MongoDB Atlas account
* Deploy **M0 free cluster**
* Create DB user
* Allow network access: `0.0.0.0/0`
* Get Python connection string

Set environment variable:

**Bash**

```bash
export MONGODB_URL="mongodb+srv://<username>:<password>@..."
```

**PowerShell**

```powershell
$env:MONGODB_URL="mongodb+srv://<username>:<password>@..."
```

---

## 📊 Data & Pipeline Components

* ✅ Data Ingestion from MongoDB
* ✅ Schema‑based Data Validation
* ✅ Feature Engineering & Transformation
* ✅ Model Training
* ✅ Model Evaluation (threshold‑based comparison)
* ✅ Model Registry (AWS S3)
* ✅ Model Pusher

Artifacts are stored in the `artifact/` directory.

---

## ☁️ AWS Setup (Model Registry)

* IAM user with programmatic access
* S3 bucket for model storage
* Environment variables for credentials

```bash
export AWS_ACCESS_KEY_ID=...
export AWS_SECRET_ACCESS_KEY=...
```

---

## 🚀 Deployment & CI/CD

### 🔁 CI/CD Workflow

1. Push code to `main`
2. GitHub Actions builds Docker image
3. Image pushed to **AWS ECR**
4. EC2 (self‑hosted runner) pulls image
5. Container runs FastAPI app

---

## 🐳 Docker & EC2 Setup

* Docker installed on EC2
* Port **5000** exposed
* Application served via FastAPI

Access app:

```
http://54.87.1.186:5000/
```



## 👤 Author

**Yasir Wali**
Aspiring MLOps 
Focused on building scalable, production‑grade ML systems


