# Docker Learning

Hands-on Docker examples, from basics through multi-language apps and CI image builds with Kaniko.

Docker is an open-source tool that lets developers package applications and their dependencies into **containers** that run consistently on any host. A **container** is a portable unit of software; an **image** is the executable package used to create containers.

---

## Repository structure

| Directory | Description |
| --- | --- |
| [`docker_basics/`](./docker_basics/) | Install Docker (Windows & Ubuntu) and first `hello-world` run |
| [`simple-node/`](./simple-node/) | Minimal Node.js app that logs every 5 seconds |
| [`nodejs-docker/`](./nodejs-docker/) | Express app serving “Hello World” on port 8080 |
| [`python_app/`](./python_app/) | Flask app serving “Hello World!” on port 5000 |
| [`sample-kaniko/`](./sample-kaniko/) | C++ “Hello World” built with Docker + GitLab CI (Kaniko) |
| [`docker-kubernetes-tutorial/`](./docker-kubernetes-tutorial/) | Notes for Docker & Kubernetes (work in progress) |

---

## Samples

### 1. Docker basics (`docker_basics/`)

Install Docker Desktop on Windows or Docker CE on Ubuntu, then verify:

```sh
docker --version
docker run hello-world
```

See [docker_basics/README.md](./docker_basics/README.md) for full install steps.

### 2. Simple Node (`simple-node/`)

Bare-bones Node.js process that prints `Containers rule!` every 5 seconds.

```sh
cd simple-node
docker build -t simple-node .
docker run simple-node
```

Local (without Docker):

```sh
npm install
node server.js
```

### 3. Node.js Express (`nodejs-docker/`)

Express app listening on port **8080**.

```sh
cd nodejs-docker
docker build -t nodejs-docker .
docker run -p 8080:8080 nodejs-docker
```

Open [http://localhost:8080](http://localhost:8080) — response: `Hello World from Docker NodeJS App`.

### 4. Python Flask (`python_app/`)

Flask app on port **5000**.

```sh
cd python_app
docker build -t python-app .
docker run -p 5000:5000 python-app
```

Open [http://localhost:5000](http://localhost:5000) — response: `Hello World!`.

### 5. Sample Kaniko (`sample-kaniko/`)

C++ Hello World image built in GitLab CI with **Kaniko** (no Docker daemon required in CI).

```sh
cd sample-kaniko
docker build -t my-cpp-app .
docker run my-cpp-app
```

CI (`.gitlab-ci.yml`) uses `gcr.io/kaniko-project/executor` to build and push to Docker Hub as `$DOCKER_USERNAME/my-cpp-app:$CI_COMMIT_SHA`. Set `DOCKER_USERNAME` and `DOCKER_PASSWORD` as CI variables.

### 6. Docker & Kubernetes tutorial (`docker-kubernetes-tutorial/`)

Additional notes (CMD vs ENTRYPOINT, cleanup, logs, Dive image inspection). Expand as you go — see [docker-kubernetes-tutorial/docker/README.md](./docker-kubernetes-tutorial/docker/README.md).

---

## Useful Docker commands

| Command | Description |
| --- | --- |
| `docker images` | List local images |
| `docker search <image>` | Search images on Docker Hub |
| `docker pull <image>` | Pull an image from a registry |
| `docker push <image>` | Push an image to a registry |
| `docker ps` | List running containers |
| `docker ps -a` | List all containers (running, stopped, etc.) |
| `docker build -t name:tag .` | Build an image with a name and tag |
| `docker commit <CONTAINER_ID> new_image` | Create an image from a container |
| `docker run -d -p host:container -it <image>` | Run a container (detached, port mapping, interactive) |
| `docker pause <CONTAINER>` | Pause all processes in a container |
| `docker unpause <CONTAINER>` | Unpause a paused container |
| `docker exec -it <CONTAINER> <command>` | Run a command inside a running container |
| `docker logs <CONTAINER>` | Show container logs |
| `docker stop <CONTAINER_ID>` | Stop one or more running containers |
| `docker kill <CONTAINER>` | Force-kill one or more containers |
| `docker rm <CONTAINER>` | Remove one or more containers |
| `docker stop $(docker ps -aq)` | Stop all containers |
| `docker rmi <IMAGE_ID>` | Remove a specific image |
| `docker rmi $(docker images --filter "dangling=true" -q --no-trunc) --force` | Remove dangling (untagged) images |
| `docker rm $(docker ps -aqf status=exited)` | Remove all exited containers |
| `docker rm -f <CONTAINER_ID>` | Force-remove a container |
| `docker rmi -f $(docker images -a -q)` | Remove all images |
| `docker system prune` | Remove unused data (images, networks, stopped containers) |

---

## Quick reference: common patterns

```sh
# Build
docker build -t my-app:latest .

# Run in background with port publish
docker run -d --name my-app -p 8080:8080 my-app:latest

# Follow logs
docker logs -f my-app

# Shell into a running container
docker exec -it my-app sh

# Stop and remove
docker stop my-app && docker rm my-app
```

---

## Learning path

1. Install Docker → `docker_basics/`
2. Build & run a simple image → `simple-node/`
3. Port mapping & HTTP apps → `nodejs-docker/`, `python_app/`
4. CI image builds without a Docker daemon → `sample-kaniko/`
5. Deeper notes & Kubernetes → `docker-kubernetes-tutorial/`
