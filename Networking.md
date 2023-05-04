# Docker Networking

<p align="center">
  <img src="https://user-images.githubusercontent.com/72669865/236332665-5e266807-0c92-4e7f-a805-2aaa86805db7.png"/>
</p>


### - The Default Bridge

#### To List your docker network, run:

```bash
sudo docker network ls
```
![Screenshot from 2023-05-04 20-45-47](https://user-images.githubusercontent.com/72669865/236328909-e6cf3ac1-06ee-4246-8a0a-c6ecec8b949e.png)

 #### To run a container on your network, run:
 ```bash
sudo docker run -itd --rm --name <container name>
 ```
 ![Screenshot from 2023-05-04 20-46-56](https://user-images.githubusercontent.com/72669865/236329093-e6ce5339-5eb0-4b8c-97ab-679367ab201d.png)

##### let's brak down the command options:

- `-itd`: **`it`** to make interactive and **`d`** to make it run in the background
- `--rm`: to clean the space after finish with container and delete it
- `--name`: to define the containers name

#### To check if the container is connected, just run
```bash
bridge link
```
![Screenshot from 2023-05-04 20-49-05](https://user-images.githubusercontent.com/72669865/236329312-0e4dec30-dfa8-4d51-b51e-5e750ef76abf.png)

#### As we know in docker you inspect anything to see what it has, in this case we gonna inspect a network (bridge), run
```bash
sudo docker inspect bridge
```
![Screenshot from 2023-05-04 20-55-10](https://user-images.githubusercontent.com/72669865/236329452-afcc595b-fb4c-4b4b-b5c0-cd8c622b9d83.png)

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

### To learn more about about Docker networking i recommand this [video](https://youtu.be/bKFMS5C4CG0)
