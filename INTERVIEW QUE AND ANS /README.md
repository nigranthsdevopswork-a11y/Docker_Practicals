🐳 Docker Interview Questions & Answers (Simple English)
🔹 1. What is Docker?

👉 Answer:
Docker is a tool used to create, run, and manage containers.
Containers allow applications to run in isolated environments with all dependencies included.

🔹 2. What is a Container?

👉 Answer:
A container is a lightweight, portable environment that runs an application with all required dependencies.

🔹 3. What is a Docker Image?

👉 Answer:
A Docker image is a read-only template used to create containers.
It contains application code, libraries, and dependencies.

🔹 4. Difference between Image and Container?

👉 Answer:

Image	Container
Template	Running instance
Static	Dynamic
Cannot run	Can run
🔹 5. What is a Dockerfile?

👉 Answer:
A Dockerfile is a script containing instructions to build a Docker image.

🔹 6. What is Docker Volume?

👉 Answer:
Docker volume is used to store data outside the container so that data is not lost when the container is deleted.

🔹 7. What is Port Mapping?

👉 Answer:
Port mapping connects a container port to a host port so the application can be accessed from outside.

Example:

docker run -p 8080:80 nginx
🔹 8. What is the difference between CMD and ENTRYPOINT?

👉 Answer:

CMD	ENTRYPOINT
Default command	Fixed command
Can be overridden	Hard to override
🔹 9. What is Docker Compose?

👉 Answer:
Docker Compose is a tool used to run multiple containers using a single YAML file.

🔹 10. What is Docker Hub?

👉 Answer:
Docker Hub is a public registry where Docker images are stored and shared.

🔹 11. What is the difference between COPY and ADD?

👉 Answer:

COPY	ADD
Simple copy	Advanced (URL + extract)
Recommended	Less used
🔹 12. What is a Layer in Docker?

👉 Answer:
Each instruction in a Dockerfile creates a layer.
Layers help in caching and faster builds.

🔹 13. What is Docker Network?

👉 Answer:
Docker network allows containers to communicate with each other.

🔹 14. How to check running containers?

👉 Answer:

docker ps
🔹 15. How to stop a container?

👉 Answer:

docker stop <container_id>
🔹 16. What happens if a container is deleted?

👉 Answer:
All data inside the container is lost unless volumes are used.

🔹 17. What is the use of EXPOSE?

👉 Answer:
EXPOSE is used to document which port the container uses.
It does not actually open the port.

🔹 18. Difference between Docker and Virtual Machine?

👉 Answer:

Docker	VM
Lightweight	Heavy
Fast	Slow
Share OS	Separate OS
🔹 19. How to remove a Docker container?

👉 Answer:

docker rm <container_id>
🔹 20. How to remove a Docker image?

👉 Answer:

docker rmi <image_id>
🔥 Scenario-Based Questions (IMPORTANT)
🔹 21. Container is not accessible in browser. What will you check?

👉 Answer:

Port mapping (-p)
Security group (AWS)
Container running or not (docker ps)
Application port correct or not
🔹 22. Data is lost after container restart. Why?

👉 Answer:
Because volume is not used. Container storage is temporary.

🔹 23. Docker image build is slow. How to optimize?

👉 Answer:

Use caching (copy package.json first)
Use lightweight image (alpine)
Use .dockerignore
🔹 24. How to run multiple containers together?

👉 Answer:
Using Docker Compose.

🔹 25. Why use Docker in DevOps?

👉 Answer:
Docker ensures:

Consistency
Easy deployment
Faster scaling
Isolation
🎯 Final Tip (Interview)

👉 Agar interviewer bole: “Explain Docker in one line”

💬 Bol:
"Docker is a containerization platform that packages applications with dependencies and runs them consistently across environments."

Agar tu next level jaana chahta hai 🔥
👉 main tujhe real interview questions (company level)
👉 ya mock interview (Q&A practice)

live karwa deta hoon 😎


🔥 Real Docker Interview Questions (Company Level)
🔹 1. How is Docker different from Virtual Machine?

👉 Answer (strong):
Docker uses containerization and shares the host OS kernel, while VMs run a full OS.
That’s why Docker is lightweight, faster, and uses fewer resources compared to VMs.

🔹 2. What happens when you run docker run nginx?

👉 Answer:

Docker checks local image
If not found → pulls from Docker Hub
Creates a container
Starts nginx server inside container
🔹 3. Why do we use COPY package.json first in Dockerfile?

👉 Answer:
To use Docker layer caching.
If dependencies don’t change, Docker skips reinstalling them → faster builds.

🔹 4. Difference between CMD and ENTRYPOINT with example?

👉 Answer:
CMD provides default command, ENTRYPOINT defines fixed command.

Example:

CMD ["npm", "start"]
ENTRYPOINT ["node"]

👉 ENTRYPOINT cannot be easily overridden, CMD can.

🔹 5. What is Docker volume and why is it needed?

👉 Answer:
Docker volume stores data outside the container, so data is not lost when the container is deleted.
Used for databases and persistent storage.

🔹 6. How do containers communicate with each other?

👉 Answer:
Using Docker network.
Containers can talk using container names as hostnames.

🔹 7. What is the use of .dockerignore?

👉 Answer:
It excludes unnecessary files (like node_modules, .git) from build context → reduces image size and speeds up build.

🔹 8. What is the difference between docker stop and docker kill?

👉 Answer:

Command	Behavior
stop	Graceful shutdown
kill	Force stop immediately
🔹 9. Why is your Docker image size too large? How to reduce it?

👉 Answer:

Use Alpine image
Remove unnecessary files
Use .dockerignore
Use multi-stage builds
🔹 10. What is multi-stage build?

👉 Answer:
It allows using multiple images in one Dockerfile to reduce final image size by copying only required files.

🔹 11. How to debug a running container?

👉 Answer:

docker exec -it <container_id> bash
🔹 12. Container is running but app is not accessible. Why?

👉 Answer:

Port not mapped
Wrong port exposed
Firewall/Security group issue
App not listening on correct port
🔹 13. What is the difference between docker run and docker start?

👉 Answer:

docker run	docker start
Creates + starts container	Starts existing container
🔹 14. What is Docker Compose and why used?

👉 Answer:
Docker Compose is used to manage multi-container applications using a single YAML file.

🔹 15. What is bind mount vs volume?

👉 Answer:

Volume	Bind Mount
Managed by Docker	Uses host path
Portable	Depends on host
🔥 Scenario-Based (VERY IMPORTANT)
🔹 16. Your container stops immediately after starting. Why?

👉 Answer:
Because the main process inside container has stopped.
Container runs only while the main process is running.

🔹 17. How will you deploy Node.js + MySQL using Docker?

👉 Answer:
Use Docker Compose with:

One container for Node.js
One for MySQL
Use network for communication
Use volume for MySQL data
🔹 18. How do you update an application in Docker?

👉 Answer:

Update code
Rebuild image
Stop old container
Run new container
🔹 19. How to share data between containers?

👉 Answer:
Using Docker volumes or shared network.

🔹 20. What is the default network in Docker?

👉 Answer:
Bridge network.

🎯 FINAL INTERVIEW TIP

👉 Agar interviewer bole:
“Why should we use Docker?”

💬 Answer confidently:

"Docker ensures consistency across environments, simplifies deployment, and reduces dependency issues by packaging the application with all its requirements."
