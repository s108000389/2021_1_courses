# 實戰主題
```
1.docker pull
2.

docker exec
```
# 1.docker pull
```
A minimal Docker image based on Alpine Linux with a complete package index and only 5 MB in size!
https://hub.docker.com/_/alpine

Alpine Linux is a Linux distribution built around musl libc and BusyBox. 
The image is only 5 MB in size and has access to a package repository 
that is much more complete than other BusyBox based images. 

This makes Alpine Linux a great image base for utilities and even production applications. 
Read more about Alpine Linux here and you can see how their mantra fits in right at home with Docker images.
```
```
docker pull alpine

docker run -it --rm alpine /bin/ash
(inside container) / # 

/bin/ash is Ash (Almquist Shell) provided by BusyBox
--rm Automatically remove the container when it exits (docker run --help)
-i Interactive mode (Keep STDIN open even if not attached)
-t Allocate a pseudo-TTY

https://stackoverflow.com/questions/35689628/starting-a-shell-in-the-docker-alpine-container
```

## 作業:建置與測試redis 資料庫

```
獲取redis鏡像 ==> sudo docker pull redis

How To Deploy And Run Redis In Docker
https://phoenixnap.com/kb/docker-redis

啟動一個Docker Redis Container  

先檢查 ==> sudo systemctl status docker

啟動一個Redis container (名字叫做 my-first-redis) 
 ==> sudo docker run --name my-first-redis -d redis

sudo docker ps  
==> 查看 The unique container ID 
         Access Port – 6379 (default Redis port number)
         The defined container name

使用 redis-cli連線到 Redis 伺服器 
==> sudo docker exec -it my-first-redis sh

在sh環境 redis-cli

Access Redis from Another Docker Container

```

```
Google search ==> dcoker hub .NET Core

==> https://hub.docker.com/_/microsoft-dotnet-core
```
# docker exec==>Run docker exec on a running container
```
https://docs.docker.com/engine/reference/commandline/exec/
```

## 啟動一個container
```
docker run --name ubuntu_bash --rm -i -t ubuntu bash
```

## 在執行中的container 執行應用程式
```
docker exec -d ubuntu_bash touch /tmp/execWorks
```


## 在執行中的container 執行interactive bash shell 
```
docker exec -it ubuntu_bash bash
```

##  set an environment variable in the current bash session
```
docker exec -it -e VAR=1 ubuntu_bash bash
```


## You can select working directory for the command to execute into
```
docker exec -it -w /root ubuntu_bash pwd
```
