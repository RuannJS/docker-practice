# commands

_docker-compose up -d_
-> in this one command, you build an image and run as many containers as you want with any specifications you want

-> if the image already exists, it will just run the container

_docker-compose down -v_
-> this commands shuts everything down
the -v shuts down the volumes too

_docker-compose up --build_
-> this commands forces a new image build

# HOW TO SET DIFFERENT DOCKER-COMPOSE FOR PRODUCTION AND DEVELOPMENT

# RUNS THE DEVELOPMENT COMPOSE

_docker-compose -f docker-compose.yml -f docker-compose.dev.yml up -d_

# RUNS THE PRODUCTION COMPOSE

_docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d_

_PRODUCTION_ -> REACHES THE CLIENT

_DEVELOPMENT_ -> DEV

We create 3 different types of YML files

1 MAIN YML
1 PROD YML
1 DEV YML

In the MAIN YML we write down every shared aspect of the YML files

In the DEV we add the volumes, and environment variables that we need and also change the command that will run after image creation

In the PROD we do the same as the dev, but for production

Line commands were getting pretty big, so docker has a tool to help us and prevent typos

# DOCKER COMPOSE

With it, we can create multiple containers with n specification with a single command.

docker-compose.yml

First we have to specify which COMPOSE version we want to use

version: "3"

Each container, in compose, is called SERVICES

in .YML files, spacing matters, so keep an eye for that

CHECK THE DOCKER-COMPOSE.YML FILE TO SEE THE RIGHT WAY TO CODE IT
