# Sandpit

This is a containerized sandpit application that contains the necessary basic services for data dev.

## Prerequisites and install

- [Docker](https://docs.docker.com/). Make sure this is installed on whatever platform you are running on.
- Go to root directory of this project in terminal, and execute the following. This should bring up all containers.
- If any changes were made to config files, this will also trigger a rebuild of containers.
```
docker compose -f sandpit.yaml up -d
```
- Verify all containers are running with `docker ps`


## What does it include?

For a full list, see the docker yaml file.

- Mongo (noSQL) and mongo express (management interface)
    - Access via [mongo-express](http://localhost:8081)
    - Can also be access via [mongosh](https://www.mongodb.com/docs/mongodb-shell/install/) at localhost:27017

- Mariadb (SQL) and adminer (management interface)
    - Access via [adminer](http://localhost:8080)

- Jupyterlab
    - Access via [link](http://localhost:8889/lab)


## How to?

### Force image rebuilds
```
docker compose -f sandpit.yaml build
```

### Execute a command on the specific container
1. Example, check the base OS on a docker image, get the container id, by running `docker ps`. Suppose the ID is  0d307873619c, you can execute the following:

```
docker container exec 0d bash -c "cat /etc/os-release"
```

This tells docker to exec the command `pwd` on container id starting with `0d` (no need to enter the full id). To get an interactive terninal:

```
docker container exec -it 0d bash -c "cat /etc/os-release"
```

More docs (here)[https://docs.docker.com/reference/cli/docker/container/exec/]