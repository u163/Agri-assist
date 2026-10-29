# 🌱 Agri-assist

**AI-Powered Crop Intelligence and Agriculture Assistance Platform**

Agri-assist is a full-stack web application designed to help farmers make informed agricultural decisions using machine learning, deep learning, and data-driven insights.

## ✨ Features

- **Crop Recommendation:** Recommends suitable crops based on agricultural input parameters.
- **Yield Prediction:** Estimates crop yield using the available prediction model.
- **Plant Disease Detection:** Analyzes uploaded plant images and provides a predicted disease, confidence score, and treatment suggestions.
- **Smart Dashboard:** Displays agricultural information, charts, and IoT-related data.
- **Weather Information:** Provides weather-related information through the application.
- **Prediction History:** Supports viewing saved prediction records where available.
- **Explainable AI:** Includes SHAP-related components for model interpretability.
- **Authentication:** Includes user registration, login, and protected API functionality.

## 🛠️ Technology Stack

### Frontend
- React
- JavaScript
- Vite
- CSS

### Backend
- Node.js
- Express.js
- REST APIs
- MongoDB
- Mongoose

### Machine Learning and Deep Learning
- Python
- scikit-learn
- TensorFlow / Keras
- SHAP

*The exact libraries used by each model are defined in the project's requirements files.*

## 🏗️ Project Structure

```text
Agri-assist/
├── client/          # Frontend application
├── server/          # Backend APIs and services
├── ml/              # Machine learning scripts and artifacts
├── deep-learning/   # Deep learning scripts and model artifacts
├── .gitignore
└── README.md
```

## ⚙️ Prerequisites

Install the following before running the project:

- Node.js and npm
- Python
- MongoDB Community Server
- Git

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/u163/Agri-assist.git
cd Agri-assist
```

### 2. Configure the backend

```bash
cd server
npm install
```

Configure the environment variables using the project's environment example file, if available.

Example development configuration:

```env
MONGO_URI=mongodb://127.0.0.1:27017/crop-planning
PORT=5000
NODE_ENV=development
CLIENT_URL=http://localhost:5173
```

Configure all other required credentials and secrets locally. Never commit your actual `.env` file.

Start the backend:

```bash
npm start
```

The development API is expected at `http://localhost:5000/api`.

### 3. Start the frontend

Open another terminal:

```bash
cd client
npm install
npm run dev
```

Open the local URL displayed by Vite, typically `http://localhost:5173`.

### 4. Set up the Python environment

Install the Python dependencies using the requirements files provided in the `ml/` and `deep-learning/` directories.

For disease detection, the project has a Python virtual environment setup and a TensorFlow/Keras model artifact. Use the relevant project requirements and model paths when configuring the Python environment.

## 🧠 Model and Prediction Workflow

1. The user enters agricultural parameters or uploads a plant image.
2. The frontend sends a request to the backend API.
3. The backend validates the input and invokes the relevant prediction service.
4. The model produces a prediction.
5. The application returns the result to the frontend for display.

Actual training datasets, preprocessing steps, model architectures, evaluation metrics, and training history should be documented alongside the corresponding model scripts and artifacts.

## 🔐 Security Notes

- Keep API keys, database credentials, JWT secrets, and other private configuration out of version control.
- Use environment variables for secrets.
- Validate uploaded images and API inputs.
- Do not treat model confidence as equivalent to model accuracy.
- Disease predictions and treatment suggestions should be verified before making real-world agricultural decisions.

## ⚠️ Limitations

Prediction quality depends on the training data, model configuration, input quality, and deployment environment. Results should be evaluated against appropriate test data before the system is used for critical agricultural decisions.

## 👨‍💻 Repository

GitHub: https://github.com/u163/Agri-assist

---

*Agri-assist: Supporting smarter, data-driven farming decisions.*

## 🤖 ML Model Architecture and Verification

### 1. Crop Recommendation

- **Model artifact:** `ml/models/best_model.pkl`
- **Algorithm:** Random Forest Classifier
- **Estimators:** 200
- **Maximum tree depth:** 20
- **Input features:** 7
- **Output classes:** 22 crop labels
- **Supporting artifacts:** `ml/scalers/scaler.pkl` and `ml/scalers/label_encoder.pkl`

The saved model and label encoder were inspected locally. Their class indices were compatible, with 22 output classes and 22 crop labels.

### 2. Plant Disease Detection

- **Model artifact:** `deep-learning/models/disease_model.h5`
- **Architecture:** EfficientNetB0
- **Input shape:** 224 × 224 × 3
- **Output classes:** 38
- **Total parameters:** 4,392,393
- **Class metadata:** `deep-learning/models/disease_classes.json`

The saved model was loaded successfully. The metadata was verified to contain 38 class labels with complete indices from 0 through 37.

### 3. Training Pipeline

The repository includes training scripts:

- `ml/train_model.py`
- `deep-learning/train_disease_model.py`

The crop training script defines Random Forest and XGBoost evaluation, with model selection based on F1-score. The disease training script defines transfer-learning and fine-tuning workflows.

**Reproducibility note:** The expected training datasets were not found in their configured project locations during verification. Historical training metrics and training plots have not yet been verified. Therefore, no training accuracy or benchmark is claimed here.

### 4. Verification Scope

The checks performed covered saved model loading, model configuration, output class counts, and label-mapping compatibility. These checks do not independently establish model accuracy, dataset provenance, or who originally trained the saved artifacts.
