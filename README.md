# Docker Web Application Container	

This repository contains a simple Hello World Web page in HTML and a Dockerfile. I've used a nginx alpine base image to create a continer that displays a simple static webpage when run.


## Pre Requisites

For first use, you may need to login via the CLI to be able to source the base image from the docker registry.

To do so, from the CLI use ```docker login [OPTIONS]```  where 

```
--password , -p		Password
--username , -u		Username
```

Also, please ensure that the docker daemon is running in order to perform the basic docker commands (build, run, ... etc)

```
service docker start
```

## Usage

### Build the image from Dockerfile

Build the base image and populate it with a index.html that contains a static "Hello World" page.

```
docker build -t my-nginx-image:latest .
```
Perform ```docker images``` to confirm the pre requisiste image (alpine) have been sourced and used in order to build your image

### Create a container

Now create a running container detached listening locally on a port that's not currently in use. I've used 80 below
```
docker run -d -p 80:80 my-nginx-image:latest
```

But you can change this to a different port if port 80 is already in use. Alternatively kill the process running on port 80 before creating the continer.

```
docker run -d -p 5432:80 my-nginx-image:latest
```

### Test container

Browser input (using local port 80 or 5432 from example above)
```
http://localhost:80
```

## Author
```
Dan Kulkarni
```