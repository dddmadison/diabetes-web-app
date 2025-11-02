Diabetes Web App

A Flask-based web application that predicts the likelihood of diabetes using a deep learning model trained on the Pima Indians Diabetes dataset.
This project demonstrates the full pipeline from model training to web deployment.

Features

Predicts diabetes risk using a Keras deep learning model

Simple web interface for manual input and instant prediction

Optional REST API endpoint for JSON-based predictions

Modular structure for easy retraining and deployment

Project Structure
diabetes-web-app/
├─ flask-diabetes.py        # Flask main server
├─ pima_model.py            # Model training and saving script
├─ pima_model.keras         # Trained Keras model file
├─ diabetes.py              # Utility script for testing or preprocessing
├─ diabetes.csv             # Pima Indians Diabetes dataset
├─ templates/               # HTML templates (Jinja2)
└─ requirements.txt         # Dependency list

Setup & Run Locally
1. Create Environment
# Optional: Create virtual environment
python -m venv .venv
# Windows
. .venv/Scripts/activate
# macOS/Linux
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

2. (Optional) Retrain the Model

A trained model (pima_model.keras) is already included.
To retrain from scratch:

python pima_model.py

3. Start the Flask App
# Option A: Run directly
python flask-diabetes.py

# Option B: Use Flask CLI
# Windows PowerShell
$env:FLASK_APP="flask-diabetes.py"; flask run
# macOS/Linux
export FLASK_APP=flask-diabetes.py && flask run


App runs by default on:
http://127.0.0.1:5000/

Usage
Web Interface

Open http://127.0.0.1:5000/ in your browser

Enter patient information (e.g., glucose, BMI, age, etc.)

Click Predict to view results instantly

API Example (JSON Request)
curl -X POST http://127.0.0.1:5000/predict \
  -H "Content-Type: application/json" \
  -d '{
    "Pregnancies": 2,
    "Glucose": 120,
    "BloodPressure": 70,
    "SkinThickness": 20,
    "Insulin": 80,
    "BMI": 28.5,
    "DiabetesPedigreeFunction": 0.45,
    "Age": 33
  }'


Response:

{
  "probability": 0.27,
  "label": 0
}

Dataset

Pima Indians Diabetes Dataset

Features include pregnancy count, glucose level, BMI, age, etc.

Used for binary classification: Diabetic (1) or Non-diabetic (0)

Tech Stack
Category	Technology
Backend	Flask (Python)
Machine Learning	TensorFlow / Keras, scikit-learn
Data	NumPy, pandas
Frontend	Jinja2 Templates (HTML)
To-Do / Improvements

 Add input validation and error handling

 Include result visualization (charts)

 Add model evaluation metrics on UI

 Provide API documentation (Swagger / Postman)

 Deploy on Render / Railway / Heroku

License

MIT License — feel free to use and modify.

Contributions

Pull requests and feedback are always welcome!
Found a bug or have an idea? Open an Issue in this repository.
