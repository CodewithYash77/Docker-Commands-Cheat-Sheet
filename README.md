# 🐳 Docker Commands Cheat Sheet

A complete Docker Commands Guide for Beginners and DevOps Engineers.

This repository contains commonly used Docker commands with simple explanations and practical examples.

## 📌 What is Docker?

Docker is a platform used to build, package, and run applications inside containers.

**Simple Example:**

Imagine your application needs Python, MySQL, and other dependencies. Docker packages everything together so your application can run consistently on different systems.

## 📚 Table of Contents

1. Docker Information Commands
2. Docker Images Commands
3. Docker Containers Commands
4. Docker Run Commands
5. Docker Hub Commands
6. Docker Build Commands
7. Dockerfile Commands
8. Docker Network Commands
9. Docker Volume Commands
10. Docker Compose Commands
11. Docker Logs Commands
12. Docker System Commands
13. Docker Cleanup Commands
14. Docker Troubleshooting Commands

---

## 1. Docker Information Commands

| Command                 | Description                         |
| ----------------------- | ----------------------------------- |
| `docker --version`      | Shows Docker version                |
| `docker version`        | Shows client and server information |
| `docker info`           | Shows complete Docker information   |
| `docker help`           | Shows Docker help                   |
| `docker COMMAND --help` | Shows help for a specific command   |
| `docker system df`      | Shows Docker disk usage             |

## 2. Docker Images Commands

Docker Image is a template used to create containers.

| Command                      | Description                        |
| ---------------------------- | ---------------------------------- |
| `docker images`              | Shows all downloaded images        |
| `docker image ls`            | Lists Docker images                |
| `docker pull nginx`          | Downloads Nginx image              |
| `docker pull ubuntu`         | Downloads Ubuntu image             |
| `docker inspect IMAGE`       | Shows image details                |
| `docker image history IMAGE` | Shows image creation history       |
| `docker rmi IMAGE`           | Deletes an image                   |
| `docker image prune`         | Removes unused images              |
| `docker tag SOURCE TARGET`   | Gives another name/tag to an image |

Example:

```bash
docker pull nginx
docker images
docker rmi nginx
```

## 3. Docker Container Commands

A container is a running or stopped instance of an image.

| Command                    | Description                           |
| -------------------------- | ------------------------------------- |
| `docker ps`                | Shows running containers              |
| `docker ps -a`             | Shows all containers                  |
| `docker run nginx`         | Creates and starts an Nginx container |
| `docker start CONTAINER`   | Starts a stopped container            |
| `docker stop CONTAINER`    | Stops a running container             |
| `docker restart CONTAINER` | Restarts a container                  |
| `docker rm CONTAINER`      | Deletes a stopped container           |
| `docker kill CONTAINER`    | Forcefully stops a container          |
| `docker pause CONTAINER`   | Pauses a container                    |
| `docker unpause CONTAINER` | Resumes a paused container            |
| `docker rename OLD NEW`    | Renames a container                   |
| `docker inspect CONTAINER` | Shows container details               |

## 4. Docker Run Commands

| Command                                     | Description                                    |
| ------------------------------------------- | ---------------------------------------------- |
| `docker run nginx`                          | Runs Nginx container                           |
| `docker run -d nginx`                       | Runs container in background                   |
| `docker run -it ubuntu bash`                | Opens Ubuntu terminal                          |
| `docker run --name myapp nginx`             | Creates a named container                      |
| `docker run -p 8080:80 nginx`               | Maps host port 8080 to container port 80       |
| `docker run --rm nginx`                     | Automatically removes container after it exits |
| `docker run -d --name web nginx`            | Runs a background container with a name        |
| `docker run -e NAME=Yash nginx`             | Sets an environment variable                   |
| `docker run --restart unless-stopped nginx` | Restarts container unless manually stopped     |

Example:

```bash
docker run -d -p 8080:80 --name mywebsite nginx
```

Open browser:

`http://localhost:8080`

## 5. Docker Hub Commands

Docker Hub is a public platform where Docker images are stored and shared.

| Command                              | Description                 |
| ------------------------------------ | --------------------------- |
| `docker login`                       | Logs in to Docker Hub       |
| `docker logout`                      | Logs out                    |
| `docker search nginx`                | Searches for images         |
| `docker pull nginx`                  | Downloads an image          |
| `docker push USERNAME/IMAGE:TAG`     | Uploads image to Docker Hub |
| `docker tag nginx USERNAME/nginx:v1` | Tags an image for uploading |

Example:

```bash
docker login

docker tag myapp yashpawar/myapp:v1

docker push yashpawar/myapp:v1
```

## 6. Docker Build Commands

Used to create Docker images from Dockerfiles.

| Command                                     | Description                            |
| ------------------------------------------- | -------------------------------------- |
| `docker build .`                            | Builds an image from current directory |
| `docker build -t myapp .`                   | Builds an image with a name            |
| `docker build -t myapp:v1 .`                | Builds an image with a version         |
| `docker build --no-cache -t myapp .`        | Builds without using cached layers     |
| `docker build -f Dockerfile.dev -t myapp .` | Uses a specific Dockerfile             |

Example:

```bash
docker build -t myapp:v1 .
docker images
```

## 7. Dockerfile Commands

Dockerfile is a text file containing instructions to build a Docker image.

| Instruction  | Description                                   |
| ------------ | --------------------------------------------- |
| `FROM`       | Defines the base image                        |
| `RUN`        | Executes commands during image building       |
| `CMD`        | Sets the default command                      |
| `ENTRYPOINT` | Defines the main executable                   |
| `COPY`       | Copies files into the image                   |
| `ADD`        | Copies files and supports additional features |
| `WORKDIR`    | Sets the working directory                    |
| `EXPOSE`     | Documents the container port                  |
| `ENV`        | Sets environment variables                    |
| `ARG`        | Defines build-time variables                  |
| `USER`       | Sets the user                                 |
| `VOLUME`     | Defines a mount point                         |
| `LABEL`      | Adds image metadata                           |

Example Dockerfile:

```dockerfile
FROM nginx:latest

WORKDIR /usr/share/nginx/html

COPY index.html .

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

Build image:

```bash
docker build -t mywebsite:v1 .
```

Run container:

```bash
docker run -d -p 8080:80 mywebsite:v1
```

## 8. Docker Network Commands

Docker Networks allow containers to communicate with each other.

| Command                                         | Description                   |
| ----------------------------------------------- | ----------------------------- |
| `docker network ls`                             | Lists all networks            |
| `docker network create mynetwork`               | Creates a network             |
| `docker network inspect mynetwork`              | Shows network details         |
| `docker network connect mynetwork CONTAINER`    | Connects container to network |
| `docker network disconnect mynetwork CONTAINER` | Disconnects container         |
| `docker network rm mynetwork`                   | Deletes a network             |
| `docker network prune`                          | Removes unused networks       |

Example:

```bash
docker network create devops-network

docker run -d --name web --network devops-network nginx
```

## 9. Docker Volume Commands

Volumes are used to store persistent data outside the container's writable layer.

| Command                          | Description            |
| -------------------------------- | ---------------------- |
| `docker volume ls`               | Lists all volumes      |
| `docker volume create myvolume`  | Creates a volume       |
| `docker volume inspect myvolume` | Shows volume details   |
| `docker volume rm myvolume`      | Deletes a volume       |
| `docker volume prune`            | Removes unused volumes |

Example:

```bash
docker volume create mydata

docker run -d --name database \
-v mydata:/var/lib/mysql \
mysql:8.0
```

## 10. Docker Compose Commands

Docker Compose is used to manage multiple containers using a YAML configuration file.

| Command                            | Description                   |
| ---------------------------------- | ----------------------------- |
| `docker compose version`           | Shows Compose version         |
| `docker compose up`                | Starts services               |
| `docker compose up -d`             | Starts services in background |
| `docker compose down`              | Stops and removes services    |
| `docker compose ps`                | Shows Compose containers      |
| `docker compose logs`              | Shows service logs            |
| `docker compose logs -f`           | Follows logs                  |
| `docker compose build`             | Builds services               |
| `docker compose restart`           | Restarts services             |
| `docker compose pull`              | Downloads service images      |
| `docker compose exec SERVICE bash` | Opens shell inside a service  |

Example docker-compose.yml:

```yaml
services:
  web:
    image: nginx
    ports:
      - "8080:80"

  database:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: example
```

Run:

```bash
docker compose up -d
```

Stop:

```bash
docker compose down
```

## 11. Docker Logs Commands

| Command                           | Description                         |
| --------------------------------- | ----------------------------------- |
| `docker logs CONTAINER`           | Shows container logs                |
| `docker logs -f CONTAINER`        | Follows live logs                   |
| `docker logs --tail 50 CONTAINER` | Shows last 50 lines                 |
| `docker logs -t CONTAINER`        | Shows logs with timestamps          |
| `docker stats`                    | Shows live container resource usage |
| `docker top CONTAINER`            | Shows container processes           |

## 12. Docker Exec Commands

Used to execute commands inside running containers.

| Command                          | Description                  |
| -------------------------------- | ---------------------------- |
| `docker exec CONTAINER ls`       | Lists files inside container |
| `docker exec -it CONTAINER bash` | Opens Bash terminal          |
| `docker exec -it CONTAINER sh`   | Opens Shell terminal         |
| `docker exec CONTAINER pwd`      | Shows current directory      |
| `docker exec CONTAINER env`      | Shows environment variables  |

Example:

```bash
docker exec -it mywebsite bash
```

## 13. Docker System Commands

| Command                  | Description                                 |
| ------------------------ | ------------------------------------------- |
| `docker system df`       | Shows disk usage                            |
| `docker system info`     | Shows system information                    |
| `docker system events`   | Shows Docker events                         |
| `docker system prune`    | Removes unused Docker data                  |
| `docker system prune -a` | Removes unused images and other unused data |

## 14. Docker Cleanup Commands

**Warning:** Cleanup commands can permanently delete Docker resources and data.

| Command                  | Description                |
| ------------------------ | -------------------------- |
| `docker container prune` | Removes stopped containers |
| `docker image prune`     | Removes dangling images    |
| `docker image prune -a`  | Removes unused images      |
| `docker volume prune`    | Removes unused volumes     |
| `docker network prune`   | Removes unused networks    |
| `docker system prune`    | Removes unused Docker data |

Always check your data before running cleanup commands.

## 15. Docker Troubleshooting Commands

| Command                    | Description                      |
| -------------------------- | -------------------------------- |
| `docker ps -a`             | Checks container status          |
| `docker logs CONTAINER`    | Checks error logs                |
| `docker inspect CONTAINER` | Checks container configuration   |
| `docker stats`             | Checks CPU and memory usage      |
| `docker events`            | Checks Docker events             |
| `docker port CONTAINER`    | Checks port mapping              |
| `docker diff CONTAINER`    | Shows filesystem changes         |
| `docker info`              | Checks Docker engine information |

---

## 🎯 Docker Practical Tasks

Try these practical tasks to improve your Docker skills.

1. Download an Nginx image.
2. Create an Nginx container.
3. Run the container in detached mode.
4. Map container port 80 to local port 8080.
5. Check running containers.
6. Open the container terminal.
7. Check container logs.
8. Stop the container.
9. Start the container again.
10. Delete the container.
11. Create a Docker volume.
12. Create a Docker network.
13. Build a custom Docker image.
14. Push your image to Docker Hub.
15. Run multiple containers using Docker Compose.

## 💡 Important Docker Concepts

| Concept        | Meaning                            |
| -------------- | ---------------------------------- |
| Image          | Template used to create containers |
| Container      | Running instance of an image       |
| Dockerfile     | Instructions to build an image     |
| Docker Hub     | Image storage and sharing platform |
| Volume         | Persistent data storage            |
| Network        | Communication between containers   |
| Docker Compose | Manages multiple containers        |
| Registry       | Stores and distributes images      |

## 👨‍💻 Author

**Yash Pawar**

Cloud & DevOps Engineer | AWS | Linux | Docker | Kubernetes

* GitHub: https://github.com/CodewithYash77
* LinkedIn: https://linkedin.com/in/yashpawar11092005
* Portfolio: https://my-portfolio-nine-woad-73.vercel.app

---

⭐ If this repository helps you learn Docker, don't forget to Star this repository!

**Keep Learning | Keep Practicing | Keep Building 🚀**
