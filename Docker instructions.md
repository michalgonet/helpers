## Basic Dockerfile:

<span style="color:cyan">**FROM </span> <span style="color:magenta"> python:3.8-alpine** </span>-based compatibility,
you can choose the closest to your program

<span style="color:cyan">**COPY </span>. <span style="color:magenta"> /app**  </span> - this will copy all from my repo
into the app folder which will be created in the container (also <span style="color:magenta">. .</span> can be used)

<span style="color:cyan">**WORKDIR</span> <span style="color:magenta"> /app** </span>- working directory, simply the
same which was select in the COPY

<span style="color:cyan">**RUN</span> <span style="color:magenta"> pip install -r requirements.txt**  </span>- next lets
install what we need for the app working

<span style="color:cyan">**CMD </span><span style="color:magenta">python app.py** </span>- finally run our application

## Basic commands:

1) To build the image run

```shell
docker build -t <aplication-name> . Ex: docker build -t welcome-app .
```

2) To check what docker image are already build:

```shell
docker images
```

3) To run a specific image as a container two important information need to be given:
    - host port
    - container port

```shell
docker run -p <host_port>:<container_port> <docker_image> Ex. docker run -p 5000:5000 welcome-app
```

4) To check how many containers are running

```shell
docker ps
```

5) To stop the container, the container ID is required (`docker ps`)

```shell
docker stop <container_ID> Ex. docker stop 406854b36a84
```

6) To remove docker image

```shell
docker image rm -f <docker_image_name> Ex docker rm -f welcome-app
```

7) To change the name of the docker image (this will create new image with new name without build it again)

```shell
docker tag <old_name> <new_name> Ex docker tag welcome-app welcome-app1 
```

8) To upload application into the docker hub the name of the image need to be as:
   <dockerhub_username>/<application_name> Ex. `user01/welcome-app`


9) To push app into the docker hub 3 steps need to be included:
    - login to docker hub `docker login`
    - application need to be in form `<username>/<application_name>`
    - to push `docker push <username>/<application_name>` Ex. `docker push user01/welcome-app`
    - add `:latest` at the end will specify the newest version of the app (include TAG)

   Ex:

```shell
docker push user01/welcome-app:latest
```

10) To pull the application from docker hub copy the link in the docker hub

## Docker compose 
If the app in the container is using other services such as MySQL, Redis, MongodB and so on
then they are also in containers. It is impossible to run for example MySQL inside the application 
container, then it needs to be run in separate container. However, containers can interact between them
and store and retrieve the data.

Docker compose is a tool for defining and running multi container docker applications. 
To do this we prepare **Docker-compose.yaml** file which manage the interaction between containers.

Flask app can be start using `RUN` but also we can create environment variable `ENV` for run different apps
For example: 

FROM python:3.8-alpine

WORKDIR /code

ENV FLASK_APP=app.py

ENV FLASK_RUN_HOST=0.0.0.0

COPY . . 

RUN pip install -r requirements.txt

EXPOSE 5000

CMD ["flask", "run"]


Next docker-compose.yaml file need to be created (key-value pairs)

version: "3.0"
services: 
   web: 
      image: web-app
      build: .
      ports:
         - "8000:5000"
   redis:
      image: redis
   mysql: 
      image: mysql


To run docker-compose.yaml
```shell
docker compose up
```

To stop 
```shell
docker compose stop
```

After some change in the code it will not work until we rebuild the docker image and create new containers
to solve this issue `volumes` are helpful and allows for avoid such problems. 







