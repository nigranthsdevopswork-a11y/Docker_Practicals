# 🐳 Docker Node.js Practical

## 🧠 What is Node.js in Docker?
Node.js application ko Docker container me run karna ek tarika hai jisse hum apne app ko containerize kar sakte hain.  
Isse application har environment me same tarike se run hota hai.

---

## 🚀 Steps Performed

### 🔹 Step 1: Create Project Directory
```bash
mkdir nodeapp
cd nodeapp

👉 This creates a project folder

🔹 Step 2: Create Node.js Application
vim app.js

Add below code:

const http = require("http");

const server = http.createServer((req, res) => {
  res.write("Hello from Node.js Docker App 🚀");
  res.end();
});

server.listen(3000, () => {
  console.log("Server running on port 3000");
});

👉 This is a simple Node.js web server

🔹 Step 3: Create package.json
vim package.json

Add this:

{
  "name": "node-docker-app",
  "version": "1.0.0",
  "main": "app.js",
  "scripts": {
    "start": "node app.js"
  }
}

👉 Defines app configuration

🔹 Step 4: Create Dockerfile
vim Dockerfile

Add content:

FROM node:18

WORKDIR /app

COPY package.json .
RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]

👉 Explanation:

FROM → Base image
WORKDIR → Working directory
COPY → Files copy
RUN → Install dependencies
EXPOSE → Port define
CMD → Start app
🔹 Step 5: Build Docker Image
docker build -t node_image .

👉 Builds Docker image

🔹 Step 6: Run Container
docker run -d --name node_container -p 3000:3000 node_image

👉 Explanation:

-d → Run in background
--name → Container name
-p → Port mapping
🔹 Step 7: Verify Container
docker ps

👉 Shows running container

🔹 Step 8: Access Output in Browser

Open browser and visit:

http://<your-ec2-public-ip>:3000

👉 You should see:

Hello from Node.js Docker App 🚀
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
docker build -t node_image .
docker run -d -p 3000:3000 node_image
🎯 Key Learning
Node.js app ko Docker me containerize kiya
Dockerfile ka use samjha
Port mapping ka concept clear hua
Container based deployment sikha
📚 Conclusion

Docker ke through Node.js application ko easily deploy kiya ja sakta hai.
Ye approach development aur production environment me consistency maintain karta hai.
