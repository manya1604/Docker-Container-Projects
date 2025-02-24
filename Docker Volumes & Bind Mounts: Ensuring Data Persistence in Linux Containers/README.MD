# 🚀 Docker Volumes & Bind Mounts: Ensuring Data Persistence in Linux Containers 🐳

## 📌 Introduction
This guide demonstrates how to use Docker **bind mounts** with a **Linux container** to retain data beyond a container’s lifecycle. By linking a local directory to a container, data remains available even after the container is deleted.

---

## 🔧 Steps & Observations

### 🏗 Step 1: Running a Container with a Bind Mount
Execute the following command:
```sh
docker run -dit --name alpine_with_bind_mount -v C:\Users\asus\docker_data:/data alpine:latest sh
```
#### 🔍 What Happens?
- If `alpine:latest` is not found locally, Docker pulls it from the official repository.
- A new container named **alpine_with_bind_mount** is created.
- The `-v` flag mounts the local directory `C:\Users\asus\docker_data` to `/data` in the container.
- The container starts a shell (`sh`) in detached mode.

---

### 📄 Step 2: Creating a File Inside the Bind Mount
Run the following command:
```sh
docker exec -it alpine_with_bind_mount sh -c "echo 'Hello, Manya!' > /data/testfile.txt"
```
#### 🔍 What Happens?
- A shell command is executed inside the running container.
- It creates a file `testfile.txt` in `/data` with the text **"Hello, Manya!"**.
- Since `/data` is a bind-mounted directory, the file is stored in `C:\Users\asus\docker_data` on the host machine.

---

### ✅ Step 3: Verifying the File Exists
To check the contents of the file:
```sh
docker exec -it alpine_with_bind_mount sh -c "cat /data/testfile.txt"
```
#### 📌 Expected Output:
```
Hello, Manya!
```
This confirms the file was successfully created and is accessible inside the container. 🎉

---

### 🗑 Step 4: Removing the First Container
Remove the container:
```sh
docker rm -f alpine_with_bind_mount
```
#### 🔍 What Happens?
- The container is **forcefully stopped and removed**.
- However, since `testfile.txt` is inside the bind-mounted directory, it **remains on the host system**. 🏠

---

### 🔄 Step 5: Creating a New Container with the Same Bind Mount
Start a new container:
```sh
docker run -dit --name new_alpine -v C:\Users\asus\docker_data:/data alpine sh
```
#### 🔍 What Happens?
- A new container named **new_alpine** is created.
- The same bind-mounted directory (`C:\Users\asus\docker_data`) is mounted to `/data`.

---

### 🔎 Step 6: Verifying File Persistence
Inside the new container, check if `testfile.txt` still exists:
```sh
docker exec -it new_alpine sh -c "cat /data/testfile.txt"
```
#### 📌 Expected Output:
```
Hello, Manya!
```
This confirms that **bind mounts ensure data persistence even after a container is removed**. 🔥

---

## 🎯 Conclusion
✅ Bind mounts allow **data retention across multiple container instances**.
✅ Deleting a container does **not** erase data in the bind-mounted directory.
✅ Any new container using the same mount can access previous container data.
✅ Useful for **sharing files between containers** and **ensuring persistent storage**.

---

### 🚀 Next Steps
- 🛠 Experiment with **named volumes** (`docker volume create`) for better data management.
- 🐳 Try bind mounts with **different container images**.
- 🔐 Explore how **file permissions** affect bind-mounted data across host and container.

---

🎯 *This guide highlights the advantages of bind mounts in Docker. Keep exploring, and happy coding!* 🚀
