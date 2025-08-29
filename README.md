# Customer Churn Analysis Project

## Overview
This repository contains the code and resources for a customer churn analysis project developed during my internship at Insider. The project aims to predict customer churn for a telecommunications company using machine learning techniques. It includes data preprocessing, exploratory data analysis (EDA), model development, and deployment through Flask and FastAPI web applications. The project was built from scratch to provide actionable insights for customer retention strategies and a user-friendly interface for real-time predictions.

## Dataset
The dataset used is `WA_Fn-UseC_-Telco-Customer-Churn.csv`, sourced from Kaggle. It contains 7,043 records with 21 features, including customer demographics (e.g., `gender`, `SeniorCitizen`), service details (e.g., `InternetService`, `Contract`), billing information (e.g., `MonthlyCharges`, `TotalCharges`), and the target variable `Churn`.

## Project Structure
- **CustomerChurnAnalysis.ipynb**: Jupyter Notebook with data preprocessing, EDA, and model development.
- **app.py**: Flask web application for a user-friendly interface to predict churn.
- **index.html**: HTML template for the Flask app, styled with Bootstrap and JavaScript for dynamic visualization.
- **fastapi_app.py**: FastAPI application for API-based churn predictions.
- **encoder.pkl**: Pickle file storing `LabelEncoder` objects for categorical feature encoding.
- **scaler.pkl**: Pickle file storing `StandardScaler` for numerical feature scaling.
- **best_model.pkl**: Pickle file storing the trained Random Forest model.

## Features
- **Exploratory Data Analysis (EDA)**: Visualizations of feature distributions and correlations using `seaborn` and `matplotlib`. Key insights include higher churn rates for month-to-month contract customers.
- **Data Preprocessing**: Handling missing values, encoding categorical variables with `LabelEncoder`, scaling numerical features with `StandardScaler`, and balancing classes with SMOTE.
- **Model Development**: Random Forest and XGBoost models trained with hyperparameter tuning via `GridSearchCV`. The Random Forest model achieved ~80% accuracy and 0.75 ROC-AUC score.
- **Web Applications**:
  - **Flask App**: A user-friendly interface with a form for inputting customer data and a dynamic progress bar to display churn probability.
  - **FastAPI App**: A scalable API endpoint (`/predict`) for programmatic churn predictions.

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/BaranParmak/Customer-Churn-Analysis-Project.git
   cd Customer-Churn-Analysis-Project
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
   Required libraries: `pandas`, `numpy`, `seaborn`, `matplotlib`, `scikit-learn`, `imblearn`, `flask`, `fastapi`, `pydantic`, `uvicorn`.

3. Download the dataset (`WA_Fn-UseC_-Telco-Customer-Churn.csv`) from Kaggle and place it in the project directory.

## Usage
### Running the Jupyter Notebook
1. Open `CustomerChurnAnalysis.ipynb` in Jupyter Notebook.
2. Run the cells to perform EDA, preprocess data, and train the model.
3. The notebook saves `encoder.pkl`, `scaler.pkl`, and `best_model.pkl` for use in the web applications.

### Running the Flask App
1. Navigate to the project directory.
2. Run the Flask application:
   ```bash
   python app.py
   ```
3. Open `http://127.0.0.1:5000` in a browser to access the GUI.
4. Enter customer details in the form to predict churn and view the probability.

### Running the FastAPI App
1. Navigate to the project directory.
2. Run the FastAPI application:
   ```bash
   uvicorn fastapi_app:app --reload
   ```
3. Access the API documentation at `http://127.0.0.1:8000/docs`.
4. Send a POST request to `/predict` with customer data in JSON format, e.g.:
   ```json
   {
       "gender": "Female",
       "SeniorCitizen": 0,
       "Partner": "Yes",
       "Dependents": "No",
       "tenure": 1,
       "PhoneService": "No",
       "MultipleLines": "No phone service",
       "InternetService": "DSL",
       "OnlineSecurity": "No",
       "OnlineBackup": "Yes",
       "DeviceProtection": "No",
       "TechSupport": "No",
       "StreamingTV": "No",
       "StreamingMovies": "No",
       "Contract": "Month-to-month",
       "PaperlessBilling": "Yes",
       "PaymentMethod": "Electronic check",
       "MonthlyCharges": 29.85,
       "TotalCharges": 29.85
   }
   ```

## Results
- **Model Performance**: The Random Forest model achieved ~80% accuracy and a 0.75 ROC-AUC score on the test set.
- **Key Insights**: Customers with month-to-month contracts and shorter tenure are more likely to churn.
- **Applications**: The Flask app provides an intuitive GUI for end-users, while the FastAPI app enables scalable integration with other systems.

## Contributing
Feel free to fork this repository, submit issues, or create pull requests to suggest improvements or additional features.

## License
This project is licensed under the MIT License.

## Acknowledgments
- Developed during my internship at Insider.
- Thanks to my mentor and the Optimus team for their guidance.
- Dataset sourced from Kaggle.
