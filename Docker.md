# Docker
- Docker is a way to run applications in a standard environment.
- Docker containers are runnable applications (processies), they can be created using a docker image.
- Docker images can be downloaded (pulled) so that they can be used to create docker containers later. 
- Docker images can be created using dockerfiles. This can be done using the command `docker build -t optional/tag:0.0.1`. 
- Each line in a dockerfile creates a cachable layer that can be used later in case previous layers have not been changed, so make sure to keep less changable calls such as `FROM` before changable ones such as `COPY`.
- Turning off a docker container deletes all of its internal changes, to keep changes you need to use volumes. 

# Docker-compose
- To keep things clean, each docker image should perform only one task.
- docker-compose.yml describes the different services of the application (e.g. web server, database, etc.).
- `docker-compose up` can be used to run the application, whereas `docker-compose down` can be used to turn off all of its layers at the same time.
