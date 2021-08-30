# Docker cheatsheet

**Configure docker-machine:** 
- MacOS  
```
curl -L https://github.com/docker/machine/releases/download/v0.16.2/docker-machine-`uname -s`-`uname -m` >/usr/local/bin/docker-machine && \
chmod +x /usr/local/bin/docker-machine`
```

- Linux  
```
curl -L https://github.com/docker/machine/releases/download/v0.16.2/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine &&
    chmod +x /tmp/docker-machine &&
    sudo cp /tmp/docker-machine /usr/local/bin/docker-machine
```

| commands 							| description 								|
| --------------------------------- | ----------------------------------------- |
| `docker-machine create default`   | create the "default" VM   				|
| `docker-machine start`            | start the machine         				|
| `docker-machine env`              | commands to setup an env  				|
| `docker-machine stop`             | stop the container        				|
| `docker-machine ip`               | show ip                   				|
| `docker stop $(docker ps -a -q)`  | stop all containers       				|
| `docker rm $(docker ps -a -q)`    | rm all containers         				|
| `docker exec -it jupyter_container bash`  | start bash in the `jupyter_container`	if it is already running 	|
| `docker system df`				| check space allocations					|
| `docker system prune`				| clean dangling data						|
| `docker system prune -a`			| clean dangling containers, images, etc	|
| `docker volume rm $(docker volume ls -qf dangling=true)` | clean volumes		|

Quick reference:  
- `docker build --rm . -t some_docker_name` #build docker environment
- `docker run -it some_docker_name -p 8787:8787 -p 8888:8888` #enter interactive mode


## docker-compose

| command 									| description 														|
| ----------------------------------------- | ----------------------------------------------------------------- |
| `docker-compose up -d --build`   			| create and run the containers     								|
| `docker-compose start`					| start containers													|

- `docker run -d -p 8888:8888 -e JUPYTER_TOKEN="password" -t jupyter/datascience-notebook:latest`
- `docker run --user root -e GRANT_SUDO=yes -it --rm -p 8888:8888 -t image_name`
- `docker run -d -p 8787:8787 -e PASSWORD=password rocker/tidyverse:latest`