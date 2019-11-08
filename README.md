# FMMI Simple Project
 > This is a simple project to demonstrate how to build a simple Flask RESTful API with Docker-Compose and Send it to Picasso Server.

Based on the work of https://github.com/Krlier

## What is this project about?

This is the project that was used to create the tutorial on how to create a simpleFlask RESTful API with Docker-Compose.
The tutorial on Medium is available [here].

## Requirements

To build this project you will need [Docker][Docker Install] and [Docker Compose][Docker Compose Install].

## Clone repository

```sh
git clone https://github.com/FranciscoGutierrez/SimpleProject
```

## Deploy and Run  

```sh
make install
```

Then simply visit [localhost:4000][App]

## Generate docker image locally with docker compose:

```sh
make install
```
> Please check MakeFile for all the details. Also check /deployments folder here you can set up everything.

## Save image locally:

```sh
docker save -o ./docker-image.tar simple-app
```
## Send to the server:

```sh
scp -P 2222 docker-image.tar student@picasso.experiments.cs.kuleuven.be:~
```
><use-your-password>

## [Server] Load the Docker Image:
ssh student@picasso.experiments.cs.kuleuven.be -p 2222
><use-your-password>

## [Server] Load the Docker Image:
```sh
podman load --input docker-image.tar
```

## [Server] Check the Loaded Image:
```sh
podman images
```
## [Server] Run image
```sh
podman run -p 4000:5000 localhost/simple-app
```
Live demo running on picasso: http://192.31.23.25:4000/

## Links of interest

- Docker docs: https://docs.docker.com/compose/gettingstarted/
- CS KU Leuven Podman Info: https://system.cs.kuleuven.be/cs/system/software/Docker/
- Docker cheat sheet: https://jrebel.com/wp-content/uploads/docker-commands-cheat-sheet.pdf


[Docker Install]:  https://docs.docker.com/install/
[Docker Compose Install]: https://docs.docker.com/compose/install/
[App]: http://127.0.0.1:4000
[here]: https://medium.com/@daniel.carlier/how-to-build-a-simple-flask-restful-api-with-docker-compose-2d849d738137
