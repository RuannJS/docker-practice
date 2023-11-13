## COMMANDS

_docker run -d -v ${pwd}:/app -v /app/node-modules -p 3000:3000 --name node-container node-image_

_docker build . -t image-name_
-> creates an docker image

_docker image ls_
-> lists all docker images

_docker ps_
-> list all docker containers

_docker run -v ${pwd}:/app p- 3000:3000 -d --name container-name image-name_

-> creates a container that exposes the port 3000 of our local machine to redirect to the port 3000 of the docker container.

left port is the exposed machine port

right port is the container port that will be redirect to

_-v ${pwd}:/app:ro_
-> Is the line command to create the BIND MOUNT VOLUME.
This allows us to sync our LOCAL MACHINE FOLDER (${pwd}) or CURRENT DIRECTORY
To the CONTAINER FOLDER or /app

:ro applies that the the /app is readonly. So it can create,delete or modify any file in your local machine

_PRESERVING CONTAINER NODE-MODULE SO YOU CAN DELETE THE ONE IN YOUR LOCAL MACHINE_

This is a little hack, but you can just add another more specific -v to the line command

The full command goes by

_docker run -d -v ${pwd}:/app -v /app/node-modules -p 3000:3000 --name node-container node-image_

_docker exec -it container-name bash_

    let us inside the container directory

# DOCKER DEVOPS WITH NODE

Every command is like a STEP for the Docker Image

Every command is CACHED, thats why we copy package.json before copying everything else. Package.json is a big file, so we only want to copy it again when we make changes to it.

FROM
-> where the image will start from

WORKDIR
-> sets the working directory of the container

COPY
-> copies the file to the container directory
Example: COPY package.json .

RUN
-> fires a command at BUILT TIME
Example: RUN npm install

EXPOSE
-> exposes a container PORT

CMD
-> fires a command at RUN TIME
after the image is created

## VOLUMES

    Allows us to have persistent data inside containers

    This is a specific type of volume called BIND MOUNT

    Allows us to sync a file or folder in our local machine with the container folder

You will only need node_modules for the first steps, after, you can delete it, by creating another volume that preserves the CONTAINER node_module

## ENVIRONMENT VARIABLES

You can create them in the Docker image file

ENV variable value

And you can change it in line command with

-e variableName=value

OR

## ENVIRONMENT FILE

We can setup every variable inside the file and pass the line command

--env-file ./.env
