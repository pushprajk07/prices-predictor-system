# 🏡 Prices Predictor System

Welcome to the **Prices Predictor System**! This is an end-to-end Machine Learning project designed to predict housing prices using a structured ML pipeline. 

This project leverages modern MLOps tools like **ZenML** for orchestrating the pipeline and **MLflow** for experiment tracking and model deployment.

Developed by **Pushpraj Kumar**.

---

## 🎯 Project Overview

The main objective of this project is to ingest housing data, process it, train an ML model to predict sale prices, and evaluate its performance. It uses a robust, scalable pipeline architecture to ensure the prediction models can be deployed locally and consistently maintained.

### ✨ Key Features:
- **Modular Pipeline Architecture**: Code is split into reusable ML steps (Data Ingestion, Split, Model Building, Evaluation, etc.).
- **ZenML Integration**: Uses ZenML to organize and run steps seamlessly.
- **MLflow Tracking**: Automatically tracks the parameters and metrics (like MSE) of trained models.
- **Continuous Deployment**: Ability to deploy predicted models and query them using an integrated MLFlow deployment server.

---

## 📂 Project Structure

- `data/` - Contains the dataset (`archive.zip`) used for training.
- `pipelines/` - ZenML pipeline definitions (e.g., `training_pipeline.py`, `deployment_pipeline.py`).
- `src/` - Core reusable ML logic (Data Splitting, Handle Missing Values, Model Evaluator, etc.).
- `steps/` - ZenML step definitions that wrap the functions in `src/`.
- `run_pipeline.py` - Script to execute the primary training ML pipeline.
- `run_deployment.py` - Script to execute the deployment pipeline.
- `setup_zenml.bat` - Utility script to configure the ZenML local stack with MLFlow.
- `analysis/` - Jupyter notebooks containing exploratory data analysis (EDA).

---

## 🚀 Setup & Installation

### ⚠️ Important Prerequisites
Due to dependency compatibility issues between latest library versions (`SQLAlchemy` / `ZenML`), it is highly recommended to run this project using **Python 3.10** or **3.11**. Please avoid using Python 3.13.

### 1. Clone the repository
```bash
git clone https://github.com/pushprajk07/prices-predictor-system.git
cd prices-predictor-system
```

### 2. Create and Activate a Virtual Environment
```bash
# Example for Windows
python -m venv venv
.\venv\Scripts\activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Initialize ZenML and setup MLFlow stack
Run the included batch script to initialize the MLflow integration:
```bash
zenml clean --yes
zenml init
.\setup_zenml.bat
```
*This configures a stack named `mlflow_stack` which sets up an MLflow Experiment Tracker and an MLflow Model Deployer.*

---

## 🧠 Running the Pipeline

To train the model and record the experiment metrics, execute the training pipeline:

```bash
python run_pipeline.py
```

After the run finishes, you can view the metrics locally by typing:
```bash
mlflow ui
```
Then navigate to `http://127.0.0.1:5000` in your web browser.

---

## 🌐 Deploying the Model

To run the deployment pipeline which trains the model and starts a prediction server based on specific constraints:

```bash
python run_deployment.py
```

Once deployed, you can interact with the server using the `sample_predict.py` script.

---

## 🛠 Built With

- **Python** 
- **ZenML** - MLOps framework
- **MLFlow** - Experiment Tracking & Deployment
- **Pandas** & **Scikit-Learn** - Machine Learning backend
