# Docker

<p align="center">
    <img src="https://user-images.githubusercontent.com/72669865/235264378-45035787-8cd5-45f7-add5-72b4c562f7b2.png"/>
</p>

### This is a Docker documentation
#### It will contain a docker explanation and some commands

> Let's start
- 1.What is Docker? 
    > Docker is a platform that vertualize the os to deliever a full configured, minimal software package called containers.
- 2.Doker image VS Docker Container
    > simply a Docker container is a running instance for the image that represent the app that we want to use, with all its configuration

### Docker Commands!

#### We have a Docker Hub, it is a docker registry that contains many images with different versions
##### to pull an image from `Docker Hub` we have to ways
```bash
  docker pull <image name>:version
```

```bash
docker pull <image name>
```
> ! the last command will pull the lastes version.

#### After we got the image we want, you can check with 
```bash
docker image
```
#### To run the image you can simply run
```bash
docker run <image name>
```
> ! Note: this command will block the terminal by showing the log of the running container to avoid that add `-d` before the `<image name>`
```bash
docker run -d <image name>
```

#### To list you containers simply run 
```bash
docker ps
```

#### to stop a container run
```bash
docker stop <container id>
```

##### Let's say you want to run a container on a port on you local machine, docker container runs that on a host port (80 for example). To change that run
```bash
docker run -d -p 9000:80 <image name>
```

> Command explanation
- `-d`: detatch mode so it doeasn't block the terminal
- `-p` or `--pubilsh`: to publish your container on a localhost port
- `9000`: the local port
- `80`: the port taken by the container
- `image name`: the name of the existed image that we want to run

> Note: if you try to run an unexisted image docker will pull by default from the registry

#### You can also run a container and give it a name to use it instead of the ID
```bash
docker run -d --name <container name> -p 9000:80 <image name>
```

- 3.How to dockerize you app
#### On the root of your app, create a `dockerfile` file, it have the following structure
> let's take a simple node app as an example

```docker
FROM node:18

COPY package.json /app/
COPY src /app/

WORKDIR /app

RUN npm install

CMD ["node", "server.js"]
```
#### now let's explain the code

- `FROM`: Keyword that allows us to use an image from docker hub in our docker container
- `COPY`: Keyword that allows us to copy a file wihtout recreate it inside the host
- `WORKDIR`: Keyword that indicates the working directory in which docker container files will be in most cases it is `/app/` a directory totally independent from you machine
- `RUN`: Keyword that allows us to run command, like you do inside the terminal
- `CMD`: Keyword that allows us to run a command that will run our up, it takes an array of strings that forms the command

#### Now to build this image and turns into a usable one, you can run
```bash
docker build -t name:version .
```
- `-t` or `--tag`: an option to give a tag to your built image
- `.`: path where you want that build in that case we indicated the current working directory but you can indicate wherever you want
