   ```
    0 docker stack deploy -c docker-compose.yaml visual
    1  docker service ls 
    2  docker service ps visual
    3  docker service create --name my_web --replicas 3 amitvashist7/python-web-app
    4  docker service ls 
    5  docker ps 
    6  docker inspect 7e6bb848bc79
    7  curl 172.17.0.2
    8  curl 172.17.0.2:8081
    9  curl 172.17.0.2:8081/info
   11  docker service create --name my_web_2 --replicas 3 --publish published=8005,target=8081 amitvashist7/python-web-app
   12  docker service ls 
   13  docker service ps my_web_2
```
