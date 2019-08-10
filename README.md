# Dockerized ARIA-tools + Mintpy

* if you want to build your images locally, follow step 1b
* if you want to pull from my personal dockerhub, follow step 1a

## 1a. Pull the `mintpy` and `ARIA-tools` containers from DockerHub

```
docker-compose -f docker-compose-PullFromDockerHub.yml up -d
```

## 1b. Build the images locally (without Dockerhub)

Run the command below to start (create if not exist) the container. Add `--build` suffix to re-build the existing container.

```
docker-compose -f docker-compose-BuildLocally.yml up -d
```

Run the command below to shut down the container:

```
docker-compose -f docker-compose-BuildLocally.yml down
```

## 2. Entering the containers

Display the list of running containers

```
docker ps
```

```
CONTAINER ID        IMAGE                             COMMAND             CREATED             STATUS              PORTS               NAMES
468c9ec13f22        dustinklo/mintpy-jpl:latest       "/bin/bash"         5 minutes ago       Up 5 minutes                            unavco-docker-images_mintpy_1
1884fca09d93        dustinklo/aria-tools-jpl:latest   "/bin/bash"         5 minutes ago       Up 5 minutes                            unavco-docker-images_aria-tools_1
```

```
docker exec -it <CONTAINER ID> bash
```
