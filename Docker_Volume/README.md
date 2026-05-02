# 🐳 Docker Volume Practical

## 🧠 What is Docker Volume?

Docker volume is a storage mechanism used to **persist data outside the container**.
It ensures that data is not lost when a container is stopped or deleted.
---
## 🚀 Steps Performed

### 🔹 Step 1: Create a Docker Volume

```bash
docker volume create myvolume
```

👉 This command creates a volume named **myvolume**

---

### 🔹 Step 2: List Docker Volumes

```bash
docker volume ls
```

👉 Verify that the volume is created

---

### 🔹 Step 3: Run Container with Volume

```bash
docker run -d --name my_container -p 8080:80 -v myvolume:/usr/share/nginx/html nginx
```

👉 Explanation:

* `-d` → Run container in background
* `--name` → Assign container name
* `-p 8080:80` → Map port
* `-v myvolume:/usr/share/nginx/html` → Attach volume

---

### 🔹 Step 4: Copy Data into Container

```bash
echo "Hello from Docker Volume" > index.html
docker cp index.html my_container:/usr/share/nginx/html/
```

👉 This copies the file into the container's web root directory

---

### 🔹 Step 5: Access Output in Browser

Open browser and visit:

```
http://<your-ec2-public-ip>:8080
```

👉 You should see:

```
Hello from Docker Volume
```

---

### 🔹 Step 6: Verify Data Persistence

Stop and remove container:

```bash
docker stop my_container
docker rm my_container
```

Run a new container using same volume:

```bash
docker run -d --name new_container -p 8080:80 -v myvolume:/usr/share/nginx/html nginx
```

👉 Open browser again — data will still be there ✅

---

## 📸 Screenshots

(Add your screenshots here)

```md
![Step1](Screenshots/step1.png)
![Step2](Screenshots/step2.png)
![Output](Screenshots/output.png)
```

---

## 📌 Output

```bash
docker volume create myvolume
docker run -d -v myvolume:/usr/share/nginx/html nginx
```

---

## 🎯 Key Learning

* Docker volumes store data **outside container**
* Data remains safe even if container is deleted
* Useful for databases, logs, and persistent storage

---

## 📚 Conclusion

Docker volumes are essential for managing persistent data in containerized environments.
They help in maintaining data integrity and are widely used in production systems.

---

## 👨‍💻 Author

Your Name
