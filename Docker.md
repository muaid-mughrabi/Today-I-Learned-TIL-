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

# Extras
## Run GUI Applications in Docker (Windows)
- Running gui applications on the host machine requires a windows-X server (e.g. vcxsrv).
- Launch vcxsrv and disable its access control
- Run `ipconfig` to get the ip adress for wsl
- Define the `DISPLAY` env variable based on the obtained ip: `set-variable -name DISPLAY -value WSL_IP:0.0`
- Run the container with `-e DISPLAY=$DISPLAY` argument.

## Allow Container To Access GPU
- Update NVIDIA drivers (and check for windows updates)!
- Pass `--gpus all` or `--gpus device=DEVICE_ID` as an argument to docker run.
- Use the following to test if everything is set up correctly `docker run --rm --gpus all nvidia/cuda:11.0.3-base-ubuntu20.04 nvidia-smi`
