Here's a **professional and visually appealing `README.md`** that showcases your MLOps project for recruiters and visitors. This highlights your technical proficiency, tools used, cloud integrations, CI/CD setup, and project features in a structured, impressive way.

---

## 🚗 Vehicle Fault Detection System (MLOps Project)

Welcome to the **Vehicle Fault Detection MLOps Pipeline**, an end-to-end machine learning system that automates everything from data ingestion to CI/CD deployment using modern MLOps best practices.

This project showcases my ability to build production-grade ML pipelines using Python, MongoDB, Docker, AWS, CI/CD workflows, and modular project structuring.

---

### 🧰 Tools & Technologies

| Category           | Tools Used                                                                  |
| ------------------ | --------------------------------------------------------------------------- |
| **Languages**      | Python 3.10                                                                 |
| **Libraries**      | Scikit-learn, Pandas, NumPy, PyYAML, logging, etc.                          |
| **Database**       | MongoDB Atlas (Cloud NoSQL)                                                 |
| **Cloud Services** | AWS S3, EC2, ECR, IAM                                                       |
| **CI/CD**          | GitHub Actions, Docker, Self-hosted Runner (EC2)                            |
| **Project Infra**  | setup.py, pyproject.toml, conda virtualenv, structured logging & exceptions |
| **Web App**        | Flask + HTML (Jinja2 templating)                                            |

---

## 📁 Project Structure

```
├── src/
│   ├── components/            # Feature modular components (ingestion, transformation, training, etc.)
│   ├── configuration/         # MongoDB & AWS configurations
│   ├── entity/                # Entity classes: config, artifact, estimator, s3_estimator
│   ├── utils/                 # Utility scripts (main_utils.py)
│   ├── aws_storage/           # AWS S3 operations
│   └── constants/             # Global constants (paths, thresholds, keys)
│
├── templates/                 # HTML templates for Flask app
├── static/                    # CSS/JS assets for frontend
├── app.py                     # Main Flask app
├── setup.py                   # Python project setup
├── pyproject.toml             # Python build system config
├── requirements.txt           # Required packages
├── Dockerfile                 # Docker image setup
├── .github/workflows/aws.yaml# CI/CD Workflow
└── notebook/                  # Jupyter notebooks (EDA, MongoDB, etc.)
```

---

## ⚙️ Setup & Installation

### 1. 🧪 Create and Activate Virtual Environment

```bash
conda create -n vehicle python=3.10 -y
conda activate vehicle
```

### 2. 📦 Install Dependencies

```bash
pip install -r requirements.txt
```

> ✅ Use `pip list` to verify successful installations.

### 3. 🏗️ Set Up Project Modules

Run:

```bash
python template.py
```

This creates the full project folder structure.

---

## 🗃️ MongoDB Integration (Atlas Cloud)

1. Sign up at [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a project & cluster (M0 tier)
3. Add user credentials and whitelist IP `0.0.0.0/0`
4. Get your **MongoDB connection string** and set as:

```bash
export MONGODB_URL="your-mongodb-url"
```

5. Run the notebook `notebook/mongoDB_demo.ipynb` to push dataset to MongoDB.
6. Data will be available in Atlas under **Collections** in key-value format.

---

## 🧱 Modular ML Pipeline

### 🔸 Data Ingestion

* Connects to MongoDB and converts raw JSON into Pandas DataFrame.
* Output saved as artifact for further use.

### 🔸 Data Validation

* Uses `schema.yaml` to validate incoming data schema.
* Logs missing columns, invalid datatypes.

### 🔸 Data Transformation

* Feature engineering (encoding, scaling, imputation).
* Converts data to a numerical format for model consumption.

### 🔸 Model Trainer

* Trains a model on transformed dataset.
* Supports model versioning and score-based validation.

### 🔸 Model Evaluation & Model Pusher

* Evaluates model performance on validation set.
* Pushes best model to AWS S3 if performance improves.

---

## ☁️ AWS Integration

### 🔐 IAM Setup

* Created IAM users with `AdministratorAccess` for programmatic access.
* Stored `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, and `AWS_DEFAULT_REGION` as GitHub secrets.

### 🪣 S3 Bucket

* Created S3 bucket: `my-model-mlopsproj`
* Models are pushed and retrieved using custom logic in `aws_storage/` and `s3_estimator.py`.

---

## 🚀 CI/CD with GitHub Actions & Docker

### 🔄 Workflow Overview

* Dockerized the app using `Dockerfile`
* Set up `aws.yaml` GitHub Actions workflow
* Configured **self-hosted runner** on **AWS EC2 Ubuntu instance**
* CI pipeline:

  1. Pull repo → Build Docker image → Push to AWS ECR
  2. Deploy to EC2 and expose on port `5080`

> EC2 Security Group configured to allow traffic on port `5080`

---

## 🌐 Web Interface

### FastAPI-based prediction UI hosted on EC2

* **URL Format:** `http://<EC2_PUBLIC_IP>:5080`
* Routes:

  * `/` → Home
  * `/predict` → Vehicle fault prediction interface
  * `/train` → Manually trigger model training

---

## 🔁 Continuous Training

* Training pipeline integrated in `/train` route
* Model retrains and updates S3 model registry if performance improves

---

## ✅ Highlights

✅ Modular codebase with separation of concerns
✅ Full pipeline from **data ingestion to model deployment**
✅ Real-time model versioning with AWS S3
✅ **GitHub Actions CI/CD** with **EC2 self-hosted runner**
✅ **MongoDB** as NoSQL backend for raw data
✅ Fully containerized with **Docker + ECR**
✅ Streamlined for **retraining, evaluation, and rollback**

---