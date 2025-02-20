# 🚢 **Titanic Survival Predictor – A Containerized ML App!**  

Predict Titanic survival with an interactive **Streamlit** app, powered by **Machine Learning** and containerized using **Docker**! ⚡🚢  
---

## 🌟 **Project Overview**  
This **Titanic Survival Prediction Model** determines whether a passenger would have survived the Titanic disaster. It’s built with **Python**, **scikit-learn**, **pandas**, and **Streamlit** for an intuitive web UI. **Docker** ensures seamless deployment!  

---

## 📂 **Project Structure**  
```bash  
Titanic-Prediction-Model/  
│── Dockerfile  
│── requirements.txt  
│── main.py  
│── titanic_model.py  
│── titanic_model.pkl  
```

### 📜 **File Breakdown**  
- **`main.py`** → Streamlit web app for user interaction.  
- **`titanic_model.py`** → Machine learning model training script.  
- **`titanic_model.pkl`** → Trained **Random Forest Classifier** model.  
- **`requirements.txt`** → Required dependencies.  
- **`Dockerfile`** → Docker configuration for containerization.  

---

## 🤖 **Model Training (`titanic_model.py`)**  
1️⃣ **Load the Titanic dataset**  
2️⃣ **Preprocess data** (handle missing values, encode categorical features)  
3️⃣ **Train the model** using **Random Forest Classifier**  
4️⃣ **Save the model** as `titanic_model.pkl`  

```python  
from sklearn.ensemble import RandomForestClassifier  
import pandas as pd  
import joblib  

# Load and preprocess dataset  
data = pd.read_csv("titanic.csv")  
# Feature Engineering... (not shown for brevity)

# Train and save model  
model = RandomForestClassifier()  
model.fit(X_train, y_train)  
joblib.dump(model, "titanic_model.pkl")  
```

---

## 🎨 **Streamlit UI (`main.py`)**  
The **interactive web app** allows users to input passenger details and predict survival chances! 🎛️  

✔️ **User-friendly UI**  
✔️ **Live prediction updates**  
✔️ **Interactive input fields**  

```python  
import streamlit as st  
import joblib  

model = joblib.load("titanic_model.pkl")  
st.title("🚢 Titanic Survival Predictor")  

age = st.slider("Age", 0, 100, 25)  
sex = st.selectbox("Gender", ["Male", "Female"])  

if st.button("Predict Survival"):  
    prediction = model.predict([[age, 1 if sex == "Male" else 0]])  
    st.success(f"Survival Prediction: {'Survived' if prediction[0] else 'Did Not Survive'}")  
```

---

## 🐳 **Docker Setup (`Dockerfile`)**  
```dockerfile  
# Use a lightweight Python image  
FROM python:3.12-slim  

# Set working directory  
WORKDIR /app  

# Copy files  
COPY requirements.txt main.py titanic_model.pkl /app/  

# Install dependencies  
RUN pip install --no-cache-dir -r requirements.txt  

# Expose the app’s port  
EXPOSE 8501  

# Run the Streamlit app  
CMD ["streamlit", "run", "main.py", "--server.port=8501", "--server.address=0.0.0.0"]  
```

---

## 🚀 **Running the Application with Docker**  

### 1️⃣ **Navigate to the Project Directory**  
```bash  
cd Titanic-Prediction-Model  
```

### 2️⃣ **Build the Docker Image**  
```bash  
docker build -t titanic-prediction .  
```

### 3️⃣ **Run the Docker Container**  
```bash  
docker run -p 8501:8501 titanic-prediction  
```

### 4️⃣ **Access the App**  
🌍 Open → **[http://localhost:8501](http://localhost:8501)**  

---

## 📊 **Preview of the App**  
![Streamlit App Screenshot](https://github.com/manya1604/Docker-Container-Projects/blob/main/Titanic%20Survival%20Predictor%20Containerized%20Streamlit%20App/image.png)
---

## 🎯 **Next Steps & Enhancements**  
🚀 **Deploy to AWS/GCP** using **Docker Hub** ☁️  
🎨 **Improve UI** with **advanced visualizations** 📊  
🧠 **Optimize model performance** with **feature engineering** 🔍  

🔹 **Happy Coding & Containerizing!** 🐳⚡

