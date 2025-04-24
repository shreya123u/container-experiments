Docker Experiment 2: Binary Classification WebApp with Streamlit
Welcome to Docker Experiment 2! This project demonstrates the power of Docker to containerize a machine learning web application built using Streamlit. The app classifies mushrooms as either edible or poisonous based on input features, utilizing machine learning classifiers.

🚀 Project Overview
This is a Binary Classification WebApp designed to predict whether a mushroom is edible or poisonous using machine learning models. The app offers a selection of classifiers, such as Support Vector Machine (SVM), Logistic Regression, and Random Forest.

Key Features:
Interactive UI built with Streamlit for classification and visualization.
Multiple Classifiers: Choose between SVM, Logistic Regression, and Random Forest.
Evaluation Metrics: View Confusion Matrix, ROC Curve, and Precision-Recall Curve.
Dockerized App: Easy deployment and isolated environment.
📝 Prerequisites
Before running the project, ensure you have the following installed:

Docker: Download and install Docker
Docker Compose: For managing multi-container Docker applications.
📂 Project Structure
/Docker_Practices
├── /Exp-2
    ├── Dockerfile                 # Dockerfile to build the container image
    ├── docker-compose.yml         # Docker Compose configuration file
    ├── app.py                     # Streamlit app for mushroom classification
    ├── requirements.txt           # Python dependencies
    └── mushrooms.csv              # Mushroom dataset for classification
