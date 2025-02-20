# 🐳 **Streamlit DockStation – Your Containerized Data App Hub!**  
---

## 🚀 **Why Use Docker for Streamlit?**  

✅ **Consistent Environment** – No more "it works on my machine" issues!  
✅ **Portability** – Run anywhere: local, cloud, or a team workspace!  
✅ **Rapid Setup** – No need for dependency nightmares!  
✅ **Scalability** – Deploy with **Kubernetes, Docker Compose, or Cloud Run** easily!  

---

## 🔧 **Prerequisites**  

Before you start, ensure you have the following:  

🔹 **Docker** 🐳 *(Ensure the daemon is running!)*  
🔹 **Python 3.9+** 🐍 *(Check with `python --version`)*  
🔹 **pip** 📦 *(Ensure it's up-to-date with `pip --version`)*  
🔹 **Basic Streamlit Knowledge** 🎨 *(If not, check [Streamlit Docs](https://docs.streamlit.io/))*  

---

## 💂 **Project Directory Structure**  

```
Streamlit-DockStation/
│── .streamlit/
│   └── config.toml       # Streamlit configuration
│── src/
│   └── app.py            # Streamlit application file
│── Dockerfile            # Docker container setup
│── requirements.txt      # Python dependencies
│── README.md             # You’re reading it now! 😉
```

---

## 📝 **File Breakdown**  

### **1️⃣ `.streamlit/config.toml` – Customizing Streamlit**  
This configuration **enables live updates & headless mode** for smooth Docker execution.  

```toml
[server]
headless = true
runOnSave = true
fileWatcherType = "poll"
```

---

### **2️⃣ `src/app.py` – The Core Streamlit App**  
🏠 **Home Page** – Interactive Dashboard  
📊 **Data Explorer** – Upload & analyze CSV files  
📈 **Visualization** – Charts, Graphs, and more!  

```python
import streamlit as st
import pandas as pd
import plotly.express as px

st.title("🚀 Streamlit DockStation")
st.write("Seamlessly Run Streamlit Apps in Docker!")

uploaded_file = st.file_uploader("📂 Upload a CSV file", type=["csv"])
if uploaded_file:
    df = pd.read_csv(uploaded_file)
    st.write(df.head())
    fig = px.histogram(df, x=df.columns[0])
    st.plotly_chart(fig)
```

---

### **3️⃣ `Dockerfile` – The Heart of Containerization**  

```dockerfile
# Use a lightweight Python image
FROM python:3.9-slim  

# Set working directory
WORKDIR /app  

# Copy dependencies and install them
COPY requirements.txt /app/  
RUN pip install --no-cache-dir -r requirements.txt  

# Copy all project files
COPY . /app/  

# Expose Streamlit’s default port
EXPOSE 8501  

# Run the Streamlit app
CMD ["streamlit", "run", "src/app.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

---

### **4️⃣ `requirements.txt` – Dependencies**  
```text
streamlit
pandas
numpy
matplotlib
plotly
```

---

## 🛠️ **Setting Up and Running the App**  

### **1️⃣ Navigate to the Project Directory**  
```bash
cd path/to/Streamlit-DockStation
```

### **2️⃣ Build the Docker Image**  
```bash
docker build -t streamlit-dockstation .
```

### **3️⃣ Run the Container**  
```bash
docker run -p 8501:8501 streamlit-dockstation
```

### **4️⃣ Open in Browser**  
🌍 Visit → **[http://localhost:8501](http://localhost:8501)**  

---

## 📸 **Sneak Peek!**  

![Streamlit App](https://github.com/manya1604/Docker-Container-Projects/blob/main/Dockerized%20Streamlit%20Development%20Environment/1.png?raw=true)
![Streamlit App](https://github.com/manya1604/Docker-Container-Projects/blob/main/Dockerized%20Streamlit%20Development%20Environment/2.png?raw=true)
 
 ---

## 🚀 **What’s Next?**  

🔹 **Deploy on AWS/GCP/Azure** for cloud hosting! ☁️  
🔹 **Integrate with Databases** like PostgreSQL, Firebase, or MongoDB! 💾  
🔹 **Add Multi-Container Support** using Docker Compose! 🏠  

---

## 🎯 **Final Thoughts**  

With **Streamlit DockStation**, you can build, test, and deploy **Streamlit apps effortlessly!** 🐳💙  

💡 **Ready to take it further?**  
Check out **Docker Compose** for multi-container setups! 🔥  

🚀 **Happy Coding!** 🎨✨

