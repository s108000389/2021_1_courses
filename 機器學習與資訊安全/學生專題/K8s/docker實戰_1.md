# 實戰主題
```
1.
2.

docker exec
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
