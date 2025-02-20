Deploying a Streamlit App with PostgreSQL in Docker

📌 Overview

This project demonstrates how to deploy a Streamlit application that connects to a PostgreSQL database using Docker. The application fetches and displays user data stored in PostgreSQL, ensuring a seamless and containerized workflow.

💁️ Project Structure

Streamlit-Postgres-Docker/
│── Dockerfile
│── app.py

🔹 Description of Files:

app.py – Streamlit app that connects to PostgreSQL and fetches user data.

Dockerfile – Configuration for containerizing the Streamlit app.

🛠 Setting Up PostgreSQL in Docker

Step 1: Pull the PostgreSQL Docker Image

docker pull postgres

Step 2: Create a Docker Network

docker network create my_postgres_network

This network allows PostgreSQL and the Streamlit app to communicate.

Step 3: Run the PostgreSQL Container

docker run --name my_postgres_container --network my_postgres_network -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=secret -e POSTGRES_DB=userdb -p 5432:5432 -d postgres

This starts a PostgreSQL container with authentication settings.

📊 Creating and Populating the Database

Step 4: Access PostgreSQL

docker exec -it my_postgres_container psql -U postgres -d userdb

Step 5: Create the users Table

CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    age INT
);

Step 6: Insert Sample Data

INSERT INTO users (name, age) VALUES
('Alice', 25),
('Bob', 30),
('Charlie', 35);

🎨 Streamlit Application (app.py)

This script connects to PostgreSQL, fetches user data, and displays it in a Streamlit UI.

🔹 Key Features:

Connects to PostgreSQL using psycopg2.

Retrieves and displays user data dynamically.

Simple and interactive UI.

🐋 Dockerizing the Streamlit Application

Step 7: Create a Dockerfile

FROM python:3.9
WORKDIR /app
COPY app.py .
RUN pip install streamlit psycopg2
CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]

🚀 Running the Streamlit Application in Docker

Step 8: Build the Docker Image

docker build -t streamlit_app .

Step 9: Run the Streamlit Container

docker run --name my_streamlit_container --network my_postgres_network -p 8501:8501 -d streamlit_app

This ensures that the Streamlit app can communicate with PostgreSQL.

📞 Access the Application

Open a browser and navigate to:
👉 http://localhost:8501

You should see the list of users displayed in the app.

🎯 Summary

✅ PostgreSQL container stores user data.✅ Streamlit container fetches and displays data from PostgreSQL.✅ Both containers communicate over my_postgres_network.✅ Application accessible at http://localhost:8501.

This project provides a containerized solution for data visualization using Streamlit and PostgreSQL. 🚀

