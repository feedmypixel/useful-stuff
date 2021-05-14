# Useful Docker

#### Start docker desktop
```
open -a Docker
```

#### Build from Docker file and tag with <name>
```
docker build -t <name> .
```
or

```
docker build -t <url><name><tag> .
```

#### Run docker image, expose port 80 and run in background
```
docker run -p 80:80 -d node-test
```

#### Run direct from Redis image, expose port 6379, run in background
```
docker run -d -p 6379:6379 --name rediscache redis
```
```
docker run -d -p 6379:6379 redis
```

#### Run and pass in env
```
docker run --env PORT=8080 -p 8080:8080 <tag>
```

#### Run direct from Selenium image, expose port 4444, run in background
```
docker run -d -p 4444:4444 --name selenium selenium/standalone-chrome:3.5.3
```

#### Run direct from DEBUG Selenium image, expose port 4444 and 5900 (for vnc), run in background
```
docker run -d -p 4444:4444 -p 5900:5900 selenium/standalone-chrome-debug
```

#### Start an existing container
```
docker start <name|id>
```

#### See running docker containers
```
docker ps
```

#### View docker images
```
docker images
```

#### Get SHA of docker images
```
docker images --digests
```

#### Delete docker image
```
docker rmi <id>
```

#### Stop
```
docker stop <name>
```

#### Stop all
```
docker stop $(docker ps -a -q)
```

#### Run redis image
Run a "redis" image named "rediscache" and expose port 6379
```
docker run -d -p 6379:6379 --name rediscache redis
```
#### Run redis-cli in redis docker
```
docker exec -it <image_name> redis-cli
```
#### Run local image with interactive mode
```
docker run -it redis /bin/bash
```

#### Run local image with interactive mode When Dockerfile has an ENTRYPOINT on apline
```
docker run -it --entrypoint /bin/bash feedmypixel/hello-world-node
```

#### Run local image with interactive mode When Dockerfile has an ENTRYPOINT on apline
```
docker run -it --entrypoint /bin/ash feedmypixel/hello-world-node
```

#### Run local image with interactive mode on apline
```
docker run -it redis /bin/ash
```

#### New shell process on container called foo
```
docker exec -it redis /bin/bash
```

#### Delete all containers
```
docker rm $(docker ps -a -q)
```

#### Delete all images
```
docker rmi $(docker images -q)
```

#### Get container ip
```
docker inspect --format '{{ .NetworkSettings.IPAddress }}' <container_id>
```

#### Docker Prune
```
docker system prune
```

## PostGres
> [Great turotial](https://www.optimadata.nl/blogs/1/n8dyr5-how-to-run-postgres-on-docker-part-1)

#### Setup local postgres
```
docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
```

#### Connect via exec
```
docker exec -it some-postgres bash
```

#### Run with port
```
docker run --name docker-postgres-local -p 5432:5432 -e POSTGRES_PASSWORD=mysecretpassword -d postgres
```


## Docker Compose

#### Buld docker compose and associated images
```
docker-compose build
```

#### Create compose
```
docker-compose up
```

#### Build compose
```
docker-compose up --build
```

#### See whats running
```
docker-compose ps
```

#### Remove last compose
```
docker-compose rm
```

#### Remove compose instance
```
docker-compose <image-name> rm
```

#### Show available envs on image
```
docker-compose run <image_name> env
```

## Docker hub

#### Build local docker file
```
docker build -t <image_tag_name> . --no-cache
```

#### Tag image to repo 
```
docker tag <image_name> <docker_hub_repo>
```

#### Push tag to repo
```
docker push <docker_hub_repo>
```