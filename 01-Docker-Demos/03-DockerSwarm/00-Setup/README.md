## Setup Docker Swarm 

### 1. Remove all you old containers.
```
docker kill $(docker ps -q) ; docker rm $(docker ps -qa)
```

### 2. Initalize Docker Swarm Mode.
```
docker swarm init --advertise-addr 172.31.0.99
```

### 3. Check the status
```
docker info
```

```
docker node ls 
```