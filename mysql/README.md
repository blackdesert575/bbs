# MySQL

## Setup with podman/docker compose

* replcae podman with docker if your're running with docker related tools

```shell
podman commpose up -d
```

## Running on macOS

```shell
$ podman compose up
>>>> Executing external compose provider "/usr/local/bin/docker-compose". Please see podman-compose(1) for how to disable this message. <<<<

[+] up 1/1
 ✘ Image mysql:5.7 Error no image found in image index for architecture "arm64", variant "v8", OS "linux"                          3.4s
Error response from daemon: no image found in image index for architecture "arm64", variant "v8", OS "linux"
Error: executing /usr/local/bin/docker-compose up: exit status 1
```

* Upgrade mysql:5.7 to mysql:8.0

## Tips

* [docker hub/MySQL](https://hub.docker.com/_/mysql)
* [MySQL 5.7 Reference Manual](https://dev.mysql.com/doc/refman/5.7/en/)
* [MySQL 8.0 Reference Manual](https://dev.mysql.com/doc/refman/8.0/en/)
* [教學課程：使用 MySQL 和 Docker Compose 建立多容器應用程式](https://learn.microsoft.com/zh-tw/visualstudio/docker/tutorials/tutorial-multi-container-app-mysql) 