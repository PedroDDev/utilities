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


# Git Commands

## git clone

If you want to get a copy of an existing Git repository — for example, a project you’d like to contribute to — the command you need is `git clone`.

USAGE: `[directory where you want to save]
       $ git clone <url of the repository in github>`
       
## git branch -d

To delete a git branch locally, use `git branch -d`.

The `-d` option will delete the branch only if it has already been pushed and merged with the remote branch. Use `-D` instead if you want to force the branch to be deleted, even if it hasn't been pushed or merged yet.

USAGE: `$ git branch -d <branch name>`

## git config --global user.name

To configure your git username on your machine, use `git config --global user.name`.

The `--global` option will set crendentials to all repositories in your machine.

USAGE: `$ git config --global user.name "your username"`

## git config --global user.email

To configure your git user email on your machine, use `git config --global user.email`.

The `--global` option will set crendentials to all repositories in your machine.

USAGE: `$ git config --global user.email your@email.com`


