🔹 Step 1: Create Project Directory

```bash
mkdir nodeapp
cd nodeapp
-----------------------------------------------------------
🔹 Step 2: Create Node.js Application
vim app.js

Add the following code:

const http = require("http");

const server = http.createServer((req, res) => {
  res.write("Hello from Node.js Docker App 🚀");
  res.end();
});

server.listen(3000, () => {
  console.log("Server running on port 3000");
});
---------------------------------------------------------------------------------------
🔹 Step 3: Create package.json
vim package.json

Add the following content:

{
  "name": "node-docker-app",
  "version": "1.0.0",
  "main": "app.js",
  "scripts": {
    "start": "node app.js"
  }
}
-----------------------------------------------------------------------------------------
🔹 Step 4: Create Dockerfile
vim Dockerfile

Add the following instructions:

FROM node:18

WORKDIR /app

COPY package.json .
RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
-------------------------------------------------------------------------------------------
🔹 Step 5: Build Docker Image
docker build -t node_image .

Verify image:

docker images
-------------------------------------------------------------------------------------------
🔹 Step 6: Run Docker Container
docker run -d -p 3000:3000 --name node_container node_image
------------------------------------------------------------------------------------------

🔹 Step 7: Verify Running Container
docker ps
🌐 Step 8: Access Application

Open your browser and visit:

http://<your-ec2-public-ip>:3000

Expected Output:

Hello from Node.js Docker App 🚀
📸 Screenshots

Create a folder named Screenshots and add images:

Screenshots/
├── build.png
├── run.png
├── output.png

Add in README:

![Build](Screenshots/build.png)
![Run](Screenshots/run.png)
![Output](Screenshots/output.png)
📌 Key Learnings
How to containerize a Node.js application
Writing a Dockerfile
Building Docker images
Running containers with port mapping
📚 Conclusion

Docker makes it easy to package and run applications in isolated environments.
Using Node.js with Docker ensures consistency across development and production.
