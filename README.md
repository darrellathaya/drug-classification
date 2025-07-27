# Drug Classification System

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)

  
## Project Description

**Drug Classification System** is a complete machine learning application that predicts appropriate drug prescriptions based on a patient's medical profile. It integrates a training pipeline, REST-based inference API using FastAPI, and GitHub Actions for lightweight MLOps automation.

The model is trained on structured health records (e.g., age, sex, BP, cholesterol, sodium-to-potassium ratio) and outputs a drug class. This system follows best practices in reproducibility, modularity, and deployment-readiness using skops, automation scripts, and organized artifacts.

  
## Features

- Trains a drug classifier model on structured medical data  
- Inference API using FastAPI and skops-serialized model  
- GitHub Actions for CI/CD automation  
- Evaluation outputs (metrics, visuals) in `Results/`  
- Modular structure with reproducible Makefile automation  


## Technologies Used

- **Python** — Core programming language  
- **FastAPI** — Lightweight web framework for serving ML predictions  
- **GitHub Actions** — CI/CD workflow automation  


## Getting Started

### Prerequisites

- Python 3.8+
- Git
- pip (Python package manager)

### Installation

1. **Clone the Repository**
   ```bash
   git clone https://github.com/your-username/drug-classification-mlops.git
   cd drug-classification-mlops
   ```

2. **Install Project Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Train the Model**
   ```bash
   python train.py
   ```

   This will generate:
   - `Model/drug_pipeline.skops`
   - `Results/metrics.txt`
   - `Results/model_results.png`


4. **Run the FastAPI Server**
   ```bash
   cd App
   uvicorn drug_app:app --reload
   ```

   Access the interactive docs at: [http://localhost:8000/docs](http://localhost:8000/docs)

  
## Usage Guide

### API Prediction Example

**Endpoint:** `POST /predict`  
**Payload:**
```json
{
  "Age": 45,
  "Sex": "F",
  "BP": "LOW",
  "Cholesterol": "NORMAL",
  "Na_to_K": 15.5
}
```

**Response:**
```json
{
  "prediction": "DrugY"
}
```

### CI/CD Workflows

GitHub Actions workflows (`.github/workflows/`) handle the following:
- Run checks, tests, or linting
- Train model automatically (optional customization)
- Validate environment setup via `Makefile` targets


## Project Structure

```
drug-classification-mlops/
├── .github/
│   └── workflows/
│       ├── cd.yml                  # Optional CD script
│       └── ci.yml                  # Continuous integration workflow
│
├── App/
│   ├── drug_app.py                 # FastAPI API code
│   ├── requirements.txt            # App-specific dependencies
│   └── README.md                   # API usage docs
│
├── Data/
│   └── drug.csv                    # Training dataset
│
├── Model/
│   └── drug_pipeline.skops        # Serialized trained pipeline
│
├── Results/
│   ├── metrics.txt                 # Evaluation results
│   └── model_results.png           # Visuals (e.g., confusion matrix)
│
├── train.py                        # Training pipeline script
├── notebook.ipynb                  # EDA and model experiments
├── requirements.txt                # Root dependencies
├── Makefile                        # Automation commands
├── LICENSE                         # Project license
└── README.md                       # Project overview and usage
```

---

## License

This project is licensed under the Apache 2.0 License.
