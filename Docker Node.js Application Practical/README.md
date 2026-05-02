🔹 STEP 1: CREATE PROJECT DIRECTORY
mkdir nodeapp
cd nodeapp

👉 This creates your project folder

🔹 STEP 2: CREATE NODE.JS APPLICATION
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

👉 Simple HTTP server

🔹 STEP 3: CREATE package.json
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

👉 Defines app metadata and start script

🔹 STEP 4: CREATE DOCKERFILE
vim Dockerfile

Add below content:

FROM node:18

WORKDIR /app

COPY package.json .
RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]

👉 Explanation:

FROM node:18 → Base image
WORKDIR → Working directory
COPY → Files copy
RUN npm install → Install dependencies
EXPOSE 3000 → Port
CMD → Start app
🔹 STEP 5: BUILD DOCKER IMAGE
docker build -t node_image .

👉 Builds Docker image

Check images:

docker images
🔹 STEP 6: RUN CONTAINER
docker run -d -p 3000:3000 --name node_container node_image

👉 Explanation:

-d → Run in background
-p 3000:3000 → Port mapping
--name → Container name
🔹 STEP 7: VERIFY CONTAINER
docker ps

👉 Check running container

🌐 STEP 8: ACCESS APPLICATION

Open browser:

http://<your-ec2-public-ip>:3000

👉 Output:

Hello from Node.js Docker App 🚀
📸 SCREENSHOTS

(Add your screenshots here)

Screenshots/
├── build.png
├── run.png
├── output.png
![Build](Screenshots/build.png)
![Run](Screenshots/run.png)
![Output](Screenshots/output.png)
📌 OUTPUT COMMANDS
docker build -t node_image .
docker run -d -p 3000:3000 node_image
🎯 KEY LEARNING
Node.js app ko Docker me containerize kiya
Dockerfile ka use samjha
Port mapping se browser me access kiya
Containerized app deployment sikha
📚 CONCLUSION

Docker + Node.js ek powerful combination hai
Jo development aur deployment ko easy aur consistent banata hai
