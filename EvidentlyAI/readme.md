🌊 Navigating Data Monitoring with Evidently AI & Docker 🐳📊

🚀 Overview

Welcome aboard! This guide will take you through launching an interactive Evidently AI dashboard inside a Docker container using Streamlit. This setup ensures:

✅ Seamless ML model monitoring.✅ Interactive dashboards for visual insights.✅ Modular and organized project structure.✅ Hassle-free deployment with Docker.

Let’s set sail! ⛵

📂 Project Blueprint

Your project directory should look like this:

📁 evidently-docker-dashboard
 ├── 📂 projects                # Separate ML monitoring projects
 │    ├── 📂 project_1
 │    │    ├── 📂 reports       # Holds generated reports
 │    ├── 📂 project_2
 │    │    ├── 📂 reports
 │    ├── ...
 │
 ├── 📂 src                     # Core scripts
 │    ├── ui.py                 # UI components
 │    ├── utils.py              # Helper functions
 │
 ├── 📂 static                  # Styling & assets
 │    ├── style.css
 │
 ├── 📄 app.py                   # Main Streamlit application
 ├── 📄 Dockerfile               # Docker setup
 ├── 📄 requirements.txt          # Dependencies
 ├── 📄 README.md                 # You are here! 📖

🎬 Inside app.py

The heart of the project, app.py, does the magic:

🚀 Dynamically loads projects and reports.🎯 Enables selection of projects, periods, and reports.📊 Displays Evidently AI reports within Streamlit.🛡️ Handles missing reports gracefully.

Key functions:

display_sidebar_header(): Creates a sleek sidebar for navigation.

select_project(): Lets users explore projects.

select_period(): Enables report period selection.

select_report(): Fetches available reports.

display_report(): Loads and presents the chosen report.

🏗️ Dockerizing the Application

# Start with the official Python image
FROM python:3.10

# Set working directory
WORKDIR /app

# Install dependencies
COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt

# Copy everything into the container
COPY . /app/

# Expose the Streamlit port
EXPOSE 8501

# Launch the app
CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]

📜 Dependencies (requirements.txt)

evidently==0.2.6
streamlit==1.19.0
pandas==1.5.3
numpy==1.24.2
scikit-learn==1.2.1
matplotlib==3.7.0
seaborn==0.12.2
pyarrow==11.0.0
altair==4.0
requests==2.28.2
pyyaml==5.1
category_encoders==2.6.0

🛠 How to Set Up and Run

🏗 Step 1: Clone & Enter the Project

git clone <repo-link>
cd evidently-docker-dashboard

🐳 Step 2: Build & Launch the Container

docker build -t evidently-dashboard .
docker run -p 8501:8501 evidently-dashboard

🌎 Step 3: Access the Dashboard

Open http://localhost:8501 in your browser. 🚀



🎯 What's Next?

🔹 Implement user authentication for secure access.🔹 Enable report comparisons across different periods.🔹 Deploy seamlessly on AWS/GCP.

Keep innovating, and happy coding! 💡🚀

