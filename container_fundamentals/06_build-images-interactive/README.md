# Build Images Interactive

In this task, you will create a new image via interactive commands.
>Note that this approach is not recommended for production usecases, use Dockerfiles instead.

## Make a change in a container

* Start an Debian container

  ```bash
  docker run -it --name my-debian debian:10.5
  ```

* Create a new file in the container

  ```bash
  touch /my.file
  exit
  ```

## Inspect the changes

* We can inspect changes to files and directories on a container's filesystem using

  ```bash
  docker diff my-debian 
  ```

  >This show the list of added, changed or deleted with capital `A`, `C` or `D` respectively prefixed with each file.

## Create an image using `docker commit`

* You can create a new image from changes using following command.

  ```bash
  docker commit my-debian
  ```

* Run the image using

  ```bash
  docker run -it <newImageId>
  ```

* Verify whether the newly added file still exists in the new container or not?

  ```bash
  ls /my.file
  ```

  To Exit from the container.

  ```bash
  exit
  ```

## Tag an image

* You can tag the newly created image using

  ```bash
  docker tag <newImageId> my-image
  ```

* After tagging the image, you can run it with a tag.

  ```bash
  docker run -it my-image
  ```

* Verify that your file still exists in the new container

  ```bash
  ls /my.file
  ```

  To Exit from the container.

  ```bash
  exit
  ```

## Cleanup

* Remove all the containers

  ```bash
  docker rm -f $(docker ps -qa)
  ```

* Remove all the images

  ```bash
  docker rmi -f $(docker images -qa)
  ```

[Jump to Home](../README.md) | [Previous Training](../05_layers/README.md) | [Next Training](../07_dockerfile/README.md)


## Commands executed

Not a good practice to build images interactively, only for local testing!
For prod use cases always use dockerfiles.

```
   95  docker ps -a
   96  docker run -it --name my-debian debian:10.5
   97  docker diff my-debian
   98  docker commit my-debian
   99  docker run -it sha256:f3d1650a0f878c473e05a1ee0aa821022e7dfd7066c1ef8cb4344e1eb44ed89c
  100  docker tag sha256:f3d1650a0f878c473e05a1ee0aa821022e7dfd7066c1ef8cb4344e1eb44ed89c my-image-vlv
  101  docker images
  102  docker rm -f $(docker ps -qa)
```