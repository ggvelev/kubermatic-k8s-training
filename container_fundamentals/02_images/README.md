# Images

In this training, you will learn how to manage images.

## Search for an image

* Check if image is available or not on Docker Hub (default registry for docker images).

  ```bash
  docker search nginx
  ```

## Download an image

* You can pull an image from Docker Hub using below pull command, which can be used for container creation afterwards. Adjust the image tag to download required version.

  ```bash
  docker pull nginx:1.23.1
  ```

## List local docker images

* To verify images is available locally, use following command

  ```bash
  docker images
  ```

## Start a container

* Let's start a container from the downloaded local image in the previous step.

  ```bash
  docker run -d nginx:1.23.1
  ```

## Remove a local docker image

* Try to remove the local image which was downloaded before.

  ```bash
  docker rmi nginx:1.23.1
  ```

  >This will not work out due to the image is currently in use. You will get Error Message on console, similar to this - 'Error response from daemon: conflict: unable to remove repository reference "nginx:1.23.1" (must force) - container xxxxxxxx is using its referenced image xxxxxxxx'

* Remove all running containers

  ```bash
  docker rm -f $(docker ps -qa)
  ```

  > * `-f` option will stop and then remove the running container.
  > * The inline command `docker ps -qa` returns the container id of all containers.
  If you are running this container on existing environment with existing containers, please provide correct container id, instead of `$(docker ps -qa)`

* Try again to remove the image

  ```bash
  docker rmi nginx:1.23.1
  ```

  >At this time, the docker image will be removed as there is no running container associated to this image.

  [Jump to Home](../README.md) | [Previous Training](../01_hello-docker/README.md) | [Next Training](../03_container-lifecycle/README.md)



## Commands executed

```
   33  docker pull nginx
   34  docker images
   35  ## Commands executed
   36  docker run -d nginx
   37  docker ps
   38  docker ps
   39  docker rmi nginx
   40  docker rm -f $(docker ps -qa)
   41  docker ps
   42  docker run -d -p 80:80 nginx
   43  docker ps
   44  docker ps
   45  docker exec trusting_spence bash
   46  docker exec -it trusting_spence bash
   47  docker ps
   48  docker rm -f $(docker ps -qa)

```