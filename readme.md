# Simple PHP Website for Demo

## How to create a Dockerfile

First Line: `FROM php:7.4-cli`

The **FROM** instruction specifies the base image for the container, here we use **php:7.4-cli** docker image, which is official docker image for php, as the base image (it contains the php binary).

---

Second Line: `COPY . /usr/src/myapp`

The **COPY** instruction will copy all the files and folders in our current directory to the **/usr/src/myapp** directory in the container.

---

Third Line: `WORKDIR /usr/src/myapp`

The **WORKDIR** instruction sets the working directory in the container to **/usr/src/myapp**, i.e., whenever you exec into the container you will be present inside this directory.

---

Fourth Line: `CMD [ "php", "-S", "0.0.0.0:8080" ]`

The `CMD` instruction runs the command passed to it (in our case **php -S 0.0.0.0:8080**) when the container starts. The command along with its arguments is specified in a json array.

---

## Build the docker image

```bash
docker build -t app .
```

The build command is used to build a docker image from a dockerfile. We provide the name of the docker image to be built using the `-t` flag. `.` is used to specify the build context, i.e., where to look for the Dockerfile.

## Run the docker image

```bash
docker run -d -p 8080:8080 app
```

The run command is used to run a container. `-d` flag is used to run the container in background. `-p` flag is used to map a host port to a port in the container, syntax - **<host_port>:<container_port>**. Finally we specify the name of the docker image to run.

After running the command, go to `http://localhost:8080` to view the simple php website.

<center><h1>THANK YOU!<h1><center>