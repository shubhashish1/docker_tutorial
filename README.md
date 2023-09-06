## Here we will be having the first file as a Dockerfile to create the docker image
```
There are few basic ketwords needed in order to create a docker image

FROM, COPY, WORKDIR, RUN, CMD

In the FROM we need to specify any linux image as the base in linux.
One of the linku image wrt python is python:3.8-alpine

In the COPY we have specify a folder name that we need to create to transfer all files
. denotes all and we will be creating the file named /app
Also . refers to current local repository

In WORKDIR we need to specify our working directory for docker which is /app here

In RUN we need to do the first step i.e to install all the dependencies.
Hence we will do pip install -r requirements.txt

Under CMD we need to provide the single python filename which connects to the entire application.
Here it is app.py. So will do python app.py
```

## Now let's build the docker image using the command in cmd

```
docker build -t welcome-app .   # welcome-app is the name . is considering all files
```

## To check whether the docker image is created or not command

```
docker images
```

## Now we need to run this docker image as a container

```
Here we need to provide 2 imp informations one is host port and another is container port
docker run -p 5000:5000 welcome-app   # Here first 5000 is host port and next 5000 is container port


 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:5000
 * Running on http://172.17.0.2:5000

 Here http://172.17.0.2:5000 is the container ip or docker container ip
 We can't directly run it in our local. We can access it via our localhost ip which is http://172.17.0.2:5000 or localhost:5000 or http://0.0.0.0:5000
```

## To check howmany containers are running we can use the command

```
docker ps
This will give us the container name as well as the ip address on which it is running which is 
http://0.0.0.0:5000

details are:

CONTAINER ID   IMAGE         COMMAND                  CREATED         STATUS         PORTS                    NAMES
219e5aff8b7e   welcome-app   "/bin/sh -c 'python …"   5 minutes ago   Up 5 minutes   0.0.0.0:5000->5000/tcp   infallible_shtern
```

## If we want to stop the docker we can use command

```
docker stop <the id> 219e5aff8b7e
```

## Let's push the docker image created to docker hub

```
Login to dockehub from url hub.docker.com

Then go to cmd and login to docker hub with command "docker login"
```

## If we want to check the images

```
docker images
```

## Now if we want to rename our docker image then:

```
We can remove the existing image and recreate it.

To remove the image command is : "docker image rm -f <imagename> welcome-app"

But why are we renaming it?

Becz in docker hub the naming should be username/dockerimage

To recreate the command is "docker build -t shubhashishmishra/welcome-app .
```

## second way of renaming the docker image

```
docker tag welcome-app shubhashishmishra/welcome-apps

But it doesn't rename the same image rather it will create a copy of same image with the different name
```

## Now to push the docker image into the dockerhub

```
docker push shubhashishmishra/welcome-apps:latest  
latest is used here for the latest version to be picked as same docker image can haqve many versions.
But we need to pick the latest one which we can find from the latest tag

REPOSITORY                       TAG       IMAGE ID       CREATED        SIZE
welcome-app                      latest    4d54f8c438b4   11 hours ago   60.7MB
shubhashishmishra/welcome-apps   latest    4d54f8c438b4   11 hours ago   60.7MB

```

## To pull a docker image from dockerhub

```
We can use a command 
docker pull shubhashishmishra/welcome-apps:latest
This command we can find from the dockerhub and then inside our image then to the tags section
```

## Once pulled we can run by command

```
docker run -d -p 5000:5000 shubhashishmishra/welcome-apps:latest

In detach mode we only get one id
Then we can go to our browser and run the localhost we have created and everything will work as it is
```