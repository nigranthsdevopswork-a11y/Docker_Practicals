1. Check Docker installation - docker --version
3. Work with containers
Run a container
docker run nginx
Run in detached mode (background)
docker run -d nginx
Run with port mapping
docker run -d -p 8080:80 nginx
List running containers
docker ps
List all containers (including stopped)
docker ps -a
Stop a container
docker stop <container_id>
Start a stopped container
docker start <container_id>
Remove a container
docker rm <container_id>
