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