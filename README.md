# Docker

Docker is an open-source tool that allows developers to easily deploy their applications in a blackbox (called containers) to run on the host operating system.

A container is a standard unit of software that packages an application with all of its dependencies to run the application with portable support. An image is an executable package of software that includes all necessary resources required to run the application.



##### Useful commands


| Command                                       | Description                               |
| ---                                           | ---                                       |
| *docker images*                               | To list available image in local machine  |
| *docker search image*                         | Search available the image on DockerHub repositories  |
| *docker pull image*                           | Pull an image from a registry             |
| *docker ps*                                   | Shows running containers              |
| *docker ps -a*                                | Show all container process including: running, stopped, etc |
| *docker build -t name:tag .*                  | Build the image with specific name and tag |
| *docker commit _CONTAINER_ID_ new_image*      | Create new images from an existing images or running images   |
| *docker run -d -p host:container -it image*   | Run the container image with detach mode and binding listening port from container (80) to host (8080) |
| *docker pause image*                          | Pause all process on the specific containers       |
| *docker unpause image*                        | Unpause all process on the specific containers     |
| *docker exec -it image _command_*             | Run a command inside the running container        |
| *docker logs image*                           | To display the logs of the image                  |
| *docker stop _CONTAINER_ID_*                  | Stop one or more running containers               |
| *docker kill image*                           | Kill one or more running containers               |
| *docker rm*                                   | Remove one or more images                         |
| *docker stop $(docker ps -aq)*                | Stop all running containers                       |
| *docker rmi _CONTAINER_ID_*                   | Delete specific image with CONTAINER_ID            |
| *docker rmi $(docker images --filter "dangling=true" -q --no-trunc) --force*  | Remove all untagged images |
| *docker rm $(docker ps -aqf status=exited)*   | Remove all exited containers                      |
| *docker rm -f _CONTAINER_ID_*                 | Remove running container                          |
| *docker rmi -f $(docker images -a -q)*                  | Remove all images                                 |
| *docker system prune*                         | Remove all unused data including: image, network, stop container |
