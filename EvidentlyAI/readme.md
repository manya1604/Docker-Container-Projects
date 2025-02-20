🌊 Navigating Data Monitoring with Evidently AI & Docker 🐳📊

🚀 Overview

Welcome aboard! This guide takes you through deploying an Evidently AI dashboard inside a Docker container using Streamlit. With this setup, you’ll achieve:

✅ Seamless ML model monitoring✅ Interactive dashboards for visual insights✅ Modular and well-organized project structure✅ Hassle-free deployment with Docker

Let’s set sail! ⛵

📌 Project Blueprint

📁 evidently-ai-streamlit
 ├── 📂 projects                # ML monitoring projects
 │    ├── 📂 project_1
 │    │    ├── 📂 reports       # Monitoring reports
 │    │    ├── ...
 │    ├── 📂 project_2
 │    │    ├── 📂 reports
 │    │    ├── ...
 │    ├── ...
 │
 ├── 📂 src                     # Python scripts for UI and utilities
 │    ├── ui.py                 # UI components
 │    ├── utils.py              # Utility functions
 │    ├── ...
 │
 ├── 📂 static                  # Static assets (CSS, images, etc.)
 │    ├── style.css             # Custom styling
 │    ├── ...
 │
 ├── 📄 app.py                   # Main Streamlit application
 ├── 📄 Dockerfile               # Docker configuration
 ├── 📄 requirements.txt         # Dependencies
 ├── 📄 README.md                # Project documentation

🏗️ Main Application (app.py)

Our Streamlit dashboard dynamically loads and renders reports using Evidently AI. Key functionalities include:

🔹 Project & Report Selection: Users can select projects and reports.🔹 Visualization: Evidently AI reports are embedded into Streamlit.🔹 Error Handling: Gracefully manages missing reports or projects.

Key functions:

display_sidebar_header(): Sidebar branding and navigation.

select_project(): Enables project selection.

select_period(): Chooses the reporting period.

select_report(): Retrieves reports dynamically.

display_report(): Displays the chosen report.

🐳 Dockerfile (Containerizing Streamlit App)

# Base Image
FROM python:3.10

# Set working directory
WORKDIR /app

# Install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir --break-system-packages -r requirements.txt

# Copy project files
COPY . .

# Expose the Streamlit port
EXPOSE 8501

# Run the Streamlit app
CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]

📦 Installation & Execution

1️⃣ Clone the Repository

git clone <repo-link>
cd evidently-ai-streamlit

2️⃣ Build & Run Docker Container

docker build -t evidently-streamlit .
docker run -p 8501:8501 evidently-streamlit

3️⃣ Access the Streamlit App

Open your browser and visit:🔗 http://localhost:8501



🚀 Next Steps

🔹 Add authentication for secure project access.🔹 Implement report comparisons over time periods.🔹 Deploy on a cloud platform (AWS/GCP) for scalability.

💡 Keep innovating & happy coding! 🚀

