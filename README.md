# 🚗 Vehicle Insurance MLOps Pipeline

> **A complete, production‑grade MLOps project** that demonstrates how machine learning systems are designed, built, deployed, and maintained in real industry environments.

---

## 📌 What This Project Demonstrates

This project showcases:

* ✅ **Industry‑style project structure** (not notebook‑only ML)
* ✅ **End‑to‑end MLOps pipeline** from raw data to live deployment
* ✅ **Clean separation of concerns** using configuration, entity, components, and pipeline layers
* ✅ **Cloud‑native ML** using AWS & MongoDB
* ✅ **CI/CD automation** using Docker, GitHub Actions, ECR, and EC2


##  High‑Level Architecture

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
FastAPI Application (Docker)
      ↓
AWS EC2 (CI/CD via GitHub Actions)
```

Each block above is implemented as an **independent, testable Python module**.

---

## 🛠️ Technology Stack (Why These Tools?)

### Programming & ML

* **Python 3.10** – stable, production‑friendly
* **Pandas / NumPy** – data processing
* **Scikit‑learn** – classical ML modeling
* **FastAPI** – lightweight, fast ML serving

### Data & Storage

* **MongoDB Atlas** – realistic cloud NoSQL data source
* **AWS S3** – model registry & artifact storage

### MLOps & Engineering

* Modular pipelines
* Artifact‑based tracking
* Schema‑driven data validation
* Custom logging & exception handling

### DevOps & Cloud

* **Docker** – environment consistency
* **AWS ECR** – container registry
* **AWS EC2** – production server
* **GitHub Actions** – CI/CD automation

---

## 📁 Detailed Project Structure

```
vehicle-insurance-mlops/
│
├── src/
│   ├── components/          # Core ML pipeline logic
│   ├── configuration/       # MongoDB & AWS connection logic
│   ├── constants/           # Centralized constants & env keys
│   ├── entity/              # Config & artifact definitions
│   ├── exception/           # Custom exception handling
│   ├── logger/              # Central logging system
│   ├── utils/               # Reusable helper functions
│
├── notebooks/               # EDA & MongoDB upload demos
├── templates/               # FastAPI HTML templates
├── static/                  # Static assets
├── artifact/                # Generated pipeline artifacts (ignored in git)
├── app.py                   # FastAPI application entry point
├── demo.py                  # Training pipeline trigger
├── Dockerfile               # Docker configuration
├── requirements.txt         # Dependencies
├── setup.py                 # Local package installation
├── pyproject.toml           # Modern Python packaging
└── .github/workflows/       # CI/CD pipelines
```

---

## ⚙️ STEP‑BY‑STEP IMPLEMENTATION GUIDE

---

## 🔹 STEP 1: Project Template Creation

A Python script (`template.py`) is used to generate a **standardized folder structure**.

```bash
python template.py
```

🔹 **Why this matters**:
Consistent structure is critical in large ML systems to maintain readability and scalability.

---

## 🔹 STEP 2: Local Package Configuration

Files used:

* `setup.py`
* `pyproject.toml`

Purpose:

* Treat the project as a **Python package**
* Enable clean imports like:

  ```python
  from src.components.data_ingestion import DataIngestion
  ```

📄 Reference: `crashcourse.txt`

---

## 🔹 STEP 3: Environment Setup

```bash
conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt
```

Verify installation:

```bash
pip list
```

🔹 Ensures reproducible development environment.

---

## 🔹 STEP 4: MongoDB Atlas Configuration

MongoDB is used as the **raw data source** to simulate real production data ingestion.

Steps:

1. Create MongoDB Atlas account
2. Deploy **M0 (free tier)** cluster
3. Create DB user
4. Allow network access: `0.0.0.0/0`
5. Copy Python connection string

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

## 🔹 STEP 5: Logging & Exception Handling

Custom modules:

* `logger/`
* `exception/`

Purpose:

* Centralized logging across pipeline
* Meaningful error traces

Tested via `demo.py`.

---

## 🔹 STEP 6: Exploratory Data Analysis (EDA)

Notebooks included for:

* Data understanding
* Feature engineering logic
* Schema preparation

🔹 **Note**: ML logic is NOT executed in notebooks.

---

## 🔹 STEP 7: Data Ingestion Component

Key responsibilities:

* Connect to MongoDB
* Fetch data in key‑value format
* Convert to Pandas DataFrame
* Save raw artifacts

Implemented using:

* `configuration.mongo_db_connections.py`
* `data_access/`
* `components.data_ingestion.py`

---

## 🔹 STEP 8: Data Validation

Driven by:

* `schema.yaml`

Checks include:

* Column presence
* Data types
* Missing values

Ensures **training data quality**.

---

## 🔹 STEP 9: Data Transformation

Includes:

* Feature encoding
* Scaling
* Train/test split

Reusable transformation objects are stored as artifacts.

---

## 🔹 STEP 10: Model Trainer

Responsibilities:

* Train ML model
* Save trained model
* Generate evaluation metrics

Designed to be easily replaceable with new models.

---

## 🔹 STEP 11: AWS & Model Registry Setup

Services used:

* IAM
* S3

Purpose:

* Store trained models centrally
* Enable versioning & rollback

---

## 🔹 STEP 12: Model Evaluation & Model Pusher

* Compare new model vs previous model
* Push to S3 if performance improves

Implements **production‑style gating logic**.

---

## 🔹 STEP 13: Prediction Pipeline & FastAPI

FastAPI endpoints:

* `/predict`
* `/training`

Supports:

* Real‑time predictions
* On‑demand retraining

---

## 🔹 STEP 14: Dockerization

* Dockerfile
* .dockerignore

Purpose:

* Consistent runtime
* Easy deployment

---

## 🔹 STEP 15: CI/CD with GitHub Actions

Pipeline stages:

1. Build Docker image
2. Push to AWS ECR
3. Pull image on EC2
4. Run container automatically

Uses **self‑hosted EC2 runner**.

---

## 🔹 STEP 16: EC2 Deployment

* Ubuntu EC2
* Docker installed
* Port 5000 exposed

Access app:

```
http://<EC2_PUBLIC_IP>:5000
```
http://54.87.1.186:5000/

## 👤 Author

**Yasir Wali**
Aspiring MLOps 
Focused on building scalable ML systems

