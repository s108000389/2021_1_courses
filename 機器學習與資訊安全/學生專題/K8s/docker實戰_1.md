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

docker pull alpine


Alpine Linux is a Linux distribution built around musl libc and BusyBox. 
The image is only 5 MB in size and has access to a package repository 
that is much more complete than other BusyBox based images. 

This makes Alpine Linux a great image base for utilities and even production applications. 
Read more about Alpine Linux here and you can see how their mantra fits in right at home with Docker images.
```
```
獲取redis鏡像 ==> sudo docker pull redis
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
