# Docker

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
> ! Note: this command will block the terminal by showing the log of the running container to avoid add `-d` before the `<image name>`
```bash
docker run -d <image name>
```
