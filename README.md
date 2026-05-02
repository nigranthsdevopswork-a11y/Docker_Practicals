	🔹 1. Check Docker installation - docker --version
	________________________________________

	🔹 3. Work with containers
	Run a container
	docker run nginx
	Run in detached mode (background)
	docker run -d nginx
	Run with port mapping
	docker run -d -p 8080:80 nginx
	List running containers
	docker ps
	List all containers (including stopped)
	docker ps -a
	Stop a container
	docker stop <container_id>
	Start a stopped container
	docker start <container_id>
	Remove a container
	docker rm <container_id>
	________________________________________
	🔹 4. Inspect & logs
	View logs
	docker logs <container_id>
	Inspect container details
	docker inspect <container_id>
	________________________________________
	🔹 5. Execute commands inside container
	docker exec -it <container_id> /bin/bash
	________________________________________
	🔹 6. Build your own image
	Build from Dockerfile
	docker build -t myapp .
	________________________________________
	🔹 7. Volumes (data persistence)
	docker volume create myvolume
docker run -d -v myvolume:/data nginx
	________________________________________
	🔹 8. Clean up
	Remove unused stuff
	docker system prune
	________________________________________
	🔹 9. Docker Compose (multi-container apps)
	Using Docker Compose:
	docker-compose up
docker-compose down

