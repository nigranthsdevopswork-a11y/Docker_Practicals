# 🐳 Docker Nginx Static Website Practical

## 🧠 What is Dockerfile?
Dockerfile ek script hoti hai jisme instructions likhe hote hain jisse Docker image create hoti hai.

Iska use karke hum apni custom image bana sakte hain (jaise Nginx + HTML website).

---

## 🚀 Steps Performed

### 🔹 Step 1: Create Project Directory
```bash
mkdir myapp
cd myapp

👉 Ye project ke liye ek folder create karega

🔹 Step 2: Create index.html
vim index.html

Add content:

<!DOCTYPE html>
<html>
<head>
    <title>Docker App</title>
</head>
<body>
    <h1>Hello from Docker 🚀</h1>
</body>
</html>

👉 Ye ek simple static website hai

🔹 Step 3: Create Dockerfile
vim Dockerfile

Add content:

FROM nginx:latest

EXPOSE 80

COPY index.html /usr/share/nginx/html/

CMD ["nginx", "-g", "daemon off;"]

👉 Explanation:

FROM nginx:latest → Base image
EXPOSE 80 → Port expose
COPY → HTML file container me copy karega
CMD → Nginx run karega
🔹 Step 4: Build Docker Image
docker build -t my_image .

👉 Ye command image build karega

Check images:

docker images
🔹 Step 5: Run Container
docker run -d -p 8080:80 --name container1 my_image

👉 Explanation:

-d → Background me run
-p 8080:80 → Port mapping
--name → Container name
🔹 Step 6: Verify Container
docker ps

👉 Running container show karega

🔹 Step 7: Access Output in Browser

Open browser:

http://<your-ec2-public-ip>:8080

👉 Output:

Hello from Docker 🚀
📸 Screenshots

(Add your screenshots here)

Screenshots/
├── build.png
├── run.png
├── output.png
![Build](Screenshots/build.png)
![Run](Screenshots/run.png)
![Output](Screenshots/output.png)
📌 Output
docker build -t my_image .
docker run -d -p 8080:80 my_image
🎯 Key Learning
Dockerfile se custom image create hoti hai
Nginx container me static website host kar sakte hain
Port mapping se browser me access milta hai
📚 Conclusion

Dockerfile ka use karke hum easily kisi bhi application ko containerize kar sakte hain.
Nginx ek lightweight web server hai jo static content serve karne ke liye use hota hai.
