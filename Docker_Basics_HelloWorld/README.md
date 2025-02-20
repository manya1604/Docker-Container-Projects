# **🐳 DOCKER BASICS – Your First Dockerized Python App 🚀**  

🎉 Welcome to **Docker Basics**! In this project, I started with the classic **"Hello, World!"** using Docker. This guide will walk you through **setting up a basic Dockerized Python application** in a visually engaging way!  

---

## **📂 Step 1: Create Your Application File**  

📝 **Create a Python file** named **`app.py`** with a simple print statement:  

```python
print("Hello, World!")
```  

🔹 This file will be executed inside a **Docker container** to print `"Hello, World!"`.  

---

## **📌 Prerequisites – Install Docker & Python**  

### ✅ **1. Install Docker & Python**  
🔗 [**Download Docker Desktop**](https://www.docker.com/products/docker-desktop/)  
🔗 [**Python Installation Guide**](https://www.python.org/downloads/)  

Ensure Docker is running after installation! 🚀  

### ✅ **2. Verify Installation**  

Run the following commands in your terminal to check versions:  

```bash
docker --version  # ✅ Check Docker version
python --version  # ✅ Check Python version
```  

If both return valid versions, you're **ready to roll!** 🎉  

---

## **🚀 Step 2: Build & Run Your Dockerized Application**  

### **🛠️ i) Create a Dockerfile**  
Inside your project folder, create a file named **`Dockerfile`** with the following content:  

```dockerfile
# Use official Python base image
FROM python:3.9

# Copy app.py to container
COPY app.py /app.py

# Run the application
CMD ["python", "/app.py"]
```  

---

### **🔹 ii) Build the Docker Image**  
Use this command to **build your Docker image**:  

```bash
docker build -t myapp .
```  

📌 **Tip:** `myapp` is the name of your Docker image. You can change it!  

---

### **🔍 iii) Verify the Image Creation**  
Check if your image was successfully created:  

```bash
docker images
```  

This will display a list of **Docker images**, and you should see `myapp` in the list!  

---

### **▶️ iv) Run the Docker Container**  
Execute the container to **run your Python script inside Docker**:  

```bash
docker run myapp
```  

🎉 If everything is set up correctly, **"Hello, World!"** should appear in your terminal like shown below! 🎊 
![Docker Image](https://github.com/manya1604/Docker-Container-Projects/blob/main/Docker_Basics_HelloWorld/ss%20(1).png)


---

## **📖 Useful Docker Resources**  
🔹 [**Official Docker Documentation**](https://docs.docker.com/)  
🔹 [**Docker Cheat Sheet**](https://dockerlabs.collabnix.com/docker/cheatsheet/)  
🔹 [**Docker Hub**](https://hub.docker.com/)  

---

## **🎯 Conclusion & Next Steps**  

🚀 **Congratulations!** You've successfully created and run your **first Dockerized Python application**! 🐳✨  

💡 **Next Steps:**  
✅ Explore **Docker Volumes** for persistent storage  
✅ Learn **Docker Networking** for multi-container apps  
✅ Use **Docker Compose** for managing complex applications  

🚢 **Happy Docking!** ⚓🌊  

---

