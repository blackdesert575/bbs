# MySQL (deprecated)

## Setup with podman/docker compose

* replcae podman with docker if your're running with docker related tools

```shell
podman compose up -d
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