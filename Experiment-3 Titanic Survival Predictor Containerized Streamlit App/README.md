<h1>🚢 Titanic Survival Predictor:- Containerized Streamlit App</h1><br>
<h2>📌 Overview</h2>
<p>The Titanic Survival Prediction Model is a machine learning application that predicts whether a passenger would have survived the Titanic disaster based on various input features. This project is built using Python, scikit-learn, pandas, and Streamlit for a user-friendly web interface. To ensure seamless deployment and portability, Docker is used to containerize the application.</p>

<h2>📂 Project Structure</h2>
Titanic-Prediction-Model/<br>
│── Dockerfile<br>
│── requirements.txt<br>
│── main.py<br>
│── titanic_model.py<br>
│── titanic_model.pkl<br>
<h2>📜 Description of Files:</h2>
<p>main.py → The Streamlit-based web application for user interaction.</p>
<p>titanic_model.py → Script to train and save the Titanic survival prediction model.</p>
<p>titanic_model.pkl → The serialized machine learning model used for making predictions.</p>
<p>requirements.txt → A list of dependencies required to run the application.</p>
<p>Dockerfile → Configuration file to containerize the application using Docker.</p>
<h2>🤖 Model Training (titanic_model.py)</h2>
<p>The model is trained using a Random Forest Classifier from scikit-learn, based on Titanic dataset features. After training, the model is saved as titanic_model.pkl using joblib, ensuring efficient storage and easy loading in the web application.</p>

<br>Steps in titanic_model.py
<br>Load the Titanic dataset.
<br>Preprocess missing values and encode categorical data.
<br>Train the Random Forest Model.
<br>Save the trained model as titanic_model.pkl.
<h2>🎨 Streamlit Application (main.py)</h2>
<br>The Streamlit app provides a clean and interactive interface for users to input passenger details and predict survival chances.

<h2>✨ Features:</h2>
<br>✔️ User-friendly UI with enhanced CSS <br>✔️ Live prediction updates using the trained .pkl file <br>✔️ Interactive sliders and dropdowns for input selection
