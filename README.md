# microservice-application

## Pre-requisites
* EC2 Instance
* Installations
    * Git
    * Docker
    * Docker Compose

## Setup Git, Docker and Docker Compose on EC2 Instance

```bash
## Install Git
yum install git -y

## Install Docker
yum install docker -y
service docker start

## Install docker-compose
curl -SL https://github.com/docker/compose/releases/download/v2.35.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker-compose version
```

## Deploy Application using Docker Compose

```bash
docker-compose up -d --build
```

## Check Application in UI to register user

Enable port "3000" in security Group and check with below url

```bash
http:://<PublicIp-Address>:3000
```

![Image](https://github.com/user-attachments/assets/f8a7195d-6458-4fd8-8d4d-90e092e799ef)

## Check Data under database Container

```bash
## Connect the Container
docker exec -it postgres-db psql -U user -d users

## To check tables in postgres
\dt

## To check table information
select * from users;
```

## Clean up Application Deployment

```bash
docker-compose down
## docker system prune -a --volumes (This will remove all images, containers and volumes etc..,)
```

```Note:``` Some of the docker commands

```bash
docker images                               ## To check Images
docker ps -a                                ## To check running container
docker logs <containerID>                   ## To check logs of the container
docker exec -it <containerID> /bin/bash     ## To connect the container
```