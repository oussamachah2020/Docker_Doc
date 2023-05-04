# Docker Networking

### - The Default Bridge

#### To List your docker network, run:

```bash
sudo docker network ls
```
 #### To run a container on your network, run:
 ```bash
sudo docker run -itd --rm --name <container name>
 ```

##### let's brak down the command options:

- `-itd`: **`it`** to make interactive and **`d`** to make it run in the background
- `--rm`: to clean the space after finish with container and delete it
- `--name`: to define the containers name

#### To check if the container is connected, just run
```bash
bridge link
```
#### As we know in docker you inspect anything to see what it has, in this case we gonna inspect a network (bridge), run
```bash
sudo docker inspect bridge
```

#### The **Docker0** acts like a switch so as you guessed the containes can talk with each others, so to jump from a container to an other you can simply run:

```bash
sudo docker exec -it <container 1> sh
```
> A prompt is going to open, to enter an other continer just paste its `IP ADDRESS`

### - The User-Defined Bridge

#### You can create your own network in docker by simply run:
```bash
sudo docker network create <network name>
```

> The goal from this is _isolation_

### - HOST network
The HOST is a lazy network that puts the container next to its father which is the hist iself, that's it.To create one just run:
```bash
sudo docker run -itd --rm --network host --name <name>
```
the new option here is 
`--network`: it allows to specify the network type you want to use

> It is better to specify an IP ADDRESS for each container , because docker chooses for u if you don't and that may cause a conflict
