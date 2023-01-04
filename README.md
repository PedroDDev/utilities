# Docker Commands

## docker-compose up

The `docker-compose up` command aggregates the output of each container. When the command exits, all containers are stopped.

USAGE: `[docker compose file repository]> docker-compose up`

Beside that, running `docker-compose up -d` starts the containers in the background and leaves them running.

USAGE: `[docker compose file repository]> docker-compose up -d`


## docker-compose down

The `docker-compose down` command stops containers and removes containers, networks, volumes, and images created by `docker-compose up`.

By default, the only things removed are:

  + Containers for services defined in the Compose file
  + Networks defined in the networks section of the Compose file
  + The default network, if one is used

Networks and volumes defined as `external` are never removed.

USAGE: `[docker compose file repository]> docker-compose down`


## docker system prune -f -a --volumes

The `docker system prune -f -a --volumes` command removes all docker containers, images and volumes. Start from scratch.

USAGE: `docker system prune -f -a --volumes`
