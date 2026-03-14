---
tags:
  - DevOps
---
[[Docker]]

### `docker build`- создаёт образ из инструкций в Dockerfile ле. 

В терминале находясь в папке с dockerfile выполнив 
```
docker buil -t app:v1 .
# -t дать имя образу-app и версию v1
. - указывает путь к Dockerfile в этой же folder
```

### `docker images`- показывает список образов (скачанных или созданных)
```
docker images
IMAGE      ID             DISK USAGE   CONTENT SIZE   EXTRA
myapp:v1   1bf1840e2a71        203MB         49.7MB
```

### `docker pull` - скачивает готовый образ из интернета, но не запускает его самостоятельно
```
docker pull nginx:latest
```
cкачает последнюю версию Nginx.

### `docker push`- загрузка образа в интернет (Docker Hub)
```
docker push твойлогин/myapp:v1
```

### `docker tag` - создаёт псевдоним/ссылку для существующего образа. Нужно чтобы загрузить себе образ или сделать другую версию 
```
docker tag myapp:v1 user123/myapp:v1
```
Теперь у тебя два имени для одного и того же образа: `myapp:v1` и `user123/myapp:v1`

### `docker history` - показывает подноготную историю как был создан образ и почему он столько весит
```
$ docker history nginx:latest
IMAGE          CREATED       CREATED BY                                      SIZE      COMMENT
bc45d248c4e1   3 days ago    CMD ["nginx" "-g" "daemon off;"]                0B        buildkit.dockerfile.v0
<missing>      3 days ago    STOPSIGNAL SIGQUIT                              0B        buildkit.dockerfile.v0
<missing>      3 days ago    EXPOSE map[80/tcp:{}]                           0B        buildkit.dockerfile.v0
```


### `docker run` -самая полезная комманда запускающая образы в контейнер 
```
docker run -d -p 8080:5000 --name my-running-app myapp:v1
- -d — фоновый режим (detach), чтобы не привязывать консоль.
  
- -p 8080:5000 — проброс портов: говорим, что на компьютере порт `8080` ведет в контейнер на порт `5000` (который мы открыли через `EXPOSE`).
  
- --name — даем контейнеру понятное имя.
 
- myapp:v1 — имя образа.
```

### `docker ps` - список запущенных (процессов докера/контейнера)

```
docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

### `docker stop` - остановить контейнер

```
docker stop my-running-app
```

### `docker logs`- logi docker контейнера 