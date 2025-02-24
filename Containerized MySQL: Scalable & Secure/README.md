# 🐬 Deploying MySQL in Docker with Automatic Initialization 🚀  

## 📌 Prerequisites  
✔ Ensure **Docker** is installed and running.  
✔ Create an **SQL initialization script** (`database_students.sql`) to set up the database and tables.  

## 📂 Project Structure  
Organize your project as follows:  

```
project-directory/
│—— Dockerfile
│—— database_students.sql
```
This setup ensures all necessary files are structured efficiently.  

## 🛠 Step 1: Writing the Dockerfile  
Create a `Dockerfile` in your project directory:  

```dockerfile
# 🏧 Use MySQL’s official image
FROM mysql:latest

# 📂 Copy the SQL script to the initialization directory
COPY database_students.sql /docker-entrypoint-initdb.d/

# 🔥 Open MySQL’s default port
EXPOSE 3306
```

## 📝 Step 2: Creating the Initialization Script  
Inside the same directory, create `database_students.sql` with the following content:  

```sql
CREATE DATABASE student_db;
USE student_db;

CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);

INSERT INTO students (name, age) VALUES ('Alice', 22), ('Bob', 24);
```

## 🛠 Step 3: Building the Docker Image  
Generate the custom MySQL image using:  

```bash
docker build -t mysql-custom .
```
💡 This creates an image named `mysql-custom`.  

## 🚀 Step 4: Running the MySQL Container  
Start the MySQL container using the built image:  

```bash
docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=root -d mysql-custom
```

### 🤔 Breakdown:  
🔹 Creates a container named `mysql-container`.  
🔹 Sets the MySQL root password to `root`.  
🔹 Runs the container in **detached mode (`-d`)**.  
🔹 Uses the **custom MySQL image** (`mysql-custom`).  

## 🔍 Step 5: Accessing the Container  
To open a shell inside the running container, execute:  

```bash
docker exec -it mysql-container bash
```
💡 This allows interactive access to the **`mysql-container`**.  

## 💻 Step 6: Connecting to MySQL  
Once inside the container, connect to MySQL with:  

```bash
mysql -u root -p
```
🔑 Enter **`root`** as the password when prompted.  

## 🛠 Step 7: Verifying the Database Setup  
After logging into MySQL, check available databases:  

```sql
SHOW DATABASES;
```

🔄 Switch to **student_db**:  

```sql
USE student_db;
```

📊 Retrieve records from the **students** table:  

```sql
SELECT * FROM students;
```

## 🎉 Summary  
✅ Successfully deployed **MySQL in a Docker container** with automatic database initialization.  
✅ Each time the container starts, the predefined **schema and sample data** load automatically.  

🚀 **Your MySQL setup is now ready to use!** 🎯  

