# Dockerized ARIA-tools + Mintpy
* if you want to build your images locally, follow step 1b
* if you want to pull from my personal dockerhub, follow step 1a

## 1a. Running the `mintpy` and `ARIA-tools` containers
```
# pulling from Dockerhub
docker-compose -f docker-compose-PullFromDockerHub.yml up -d
```

## 1b. building the images locally (without Dockerhub)
Run these commands:
```
# starting
docker-compose -f docker-compose-BuildLocally.yml up -d

# shutting down
docker-compose -f docker-compose-BuildLocally.yml down
```

## 2. Entering the containers
`docker ps  # displays the list of running containers`

```
CONTAINER ID        IMAGE                             COMMAND             CREATED             STATUS              PORTS               NAMES
468c9ec13f22        dustinklo/mintpy-jpl:latest       "/bin/bash"         5 minutes ago       Up 5 minutes                            unavco-docker-images_mintpy_1
1884fca09d93        dustinklo/aria-tools-jpl:latest   "/bin/bash"         5 minutes ago       Up 5 minutes                            unavco-docker-images_aria-tools_1
```

`docker exec -it <CONTAINER ID> bash`