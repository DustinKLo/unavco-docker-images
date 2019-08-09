h2. Running the `mintpy` and `ARIA-tools` containers
`docker-compose up -d`

h2. Entering the containers
`docker ps  # displays the list of running containers`

```
CONTAINER ID        IMAGE                             COMMAND             CREATED             STATUS              PORTS               NAMES
468c9ec13f22        dustinklo/mintpy-jpl:latest       "/bin/bash"         5 minutes ago       Up 5 minutes                            unavco-docker-images_mintpy_1
1884fca09d93        dustinklo/aria-tools-jpl:latest   "/bin/bash"         5 minutes ago       Up 5 minutes                            unavco-docker-images_aria-tools_1
```

`docker exec -it <CONTAINER ID> bash`


h1. building the images
if you want to build the images from the `Dockerfile`, run these commands
```
# building the mintpy image
cd mintpy-docker
docker build -t mintpy-jpl .

# building the aria-tools image
cd aria-tools-docker
docker build -t aria-tools-jpl .
```