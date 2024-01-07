# Docker-Project 
## The Project Outline
'' Docker LifeCycle
'' Containers vs Virtual Machine
'' What is Docker, container, and images
'' Files and folders that each containers have
'' volume and its important 
'' Docker registries
'' How to install docker
'' Docker Command

## What is a container?

A container is a standard unit of software that packages up code and all its dependencies, so the application runs quickly and reliably from one computing environment to another. A Docker container image is package of software that has everything needed to run an application e.g. code, runtime, system tools, system libraries and settings.

## Containers vs Virtual Machine 

Containers and virtual machines have diff key

    1. Utilization of resource: Containers share the host operating system kernel, making them lighter and faster than VMs. VMs have a full-fledged OS and hypervisor, making them more resource-intensive.

    2. Portability: Containers are designed to be portable and can run on any system with a compatible host operating system. VMs are less portable as they need a compatible hypervisor to run.

    3. Security: VMs provide a higher level of security as each VM has its own operating system and can be isolated from the host and other VMs. Containers provide less isolation, as they share the host operating system.

## Every Container base images it has files and folders that containers use from host operating system 


### Bellow are Files and Folders that are in each containers application base images

```
   /bin: contains binary executable files, such as the ls, cp, and ps commands.

    /sbin: contains system binary executable files, such as the init and shutdown commands.

    /etc: contains configuration files for various system services.

    /lib: contains library files that are used by the binary executables.

    /usr: contains user-related files and utilities, such as applications, libraries, and documentation.

    /var: contains variable data, such as log files, spool files, and temporary files.

    /root: is the home directory of the root user.
```

## Docker

### What is Docker ?

Docker is a containerization platform- which means, using Docker you can build container images- run the images to create containers and push these containers to container regestries like DockerHub.

### Docker Architecture

Docker Deamon- a brain of Docker. If Docker Deamon is killed, it will stop working

### Docker LifeCycle 

Docker has three stages of lifecycle

1. docker build -> we builds docker images from Dockerfile
2. docker run   -> we runs container from docker images
3. docker push  -> we push the container image to public or private regestries so we can share the docker images.


### Docker Docs terminology

#### 1 Docker daemon

The Docker daemon -it communicate and listens to Docker API requests on how to manages Docker objects such as images, containers, networks, and volumes.


#### 2 Docker client

The Docker client - how Docker users interact with Docker. e.g When you use commands such as docker run, the client sends these commands to dockerd, which carries them out. The docker command uses the Docker API and Docker client can communicate with more than one daemon.

#### 3 Docker registries

A Docker registry - where we stores Docker images.

When you use the docker pull or docker run commands, the required images are pulled from your configured registry. When you use the docker push command, your image is pushed to your configured registry.

#### Dockerfile

A Dockerfile is a file where you provide the steps to build your Docker Image. 


#### Images

An image is a read-only template with instructions for creating a Docker container. An image is created based on another image
or you can create your own images and published in a registry. To build your own image, you create a Dockerfile with a simple syntax defining the steps needed to create the image and run it.



## TO INSTALL A DOCKER

Below are instructions on how to install Docker

a) You can create an Ubuntu EC2 Instance on AWS and run the below commands

```
sudo apt update
sudo apt install docker.io -y
```

### Than you need to Start Docker and Grant Access

Always ensure the docker daemon is up and running.

By running the below command

```
docker run hello-world
```

If you received an error message that says:

```
docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/create": dial unix /var/run/docker.sock: connect permission denied.
See 'docker run --help'.
```
This error can mean two things, 

1. Docker deamon is not running.
2. Your user does not have access to run docker commands.

To solve this error message you need
### you need to Start Docker daemon

You use the below command to verify if the docker daemon is actually started and Active

```
sudo systemctl status docker
```

If you notice that the docker daemon is not running, you can start the daemon using the below command

```
sudo systemctl start docker
```


### Then to Grant Access to your user to run docker commands

You should add the user to the Docker Linux group. Because Docker group is created by default when docker is installed.

## So run the following command 
```
sudo usermod -aG docker ubuntu
```
In the above command `ubuntu` is the name of the user, you can change the username appropriately.

**NOTE:** : after running those command You need to logout and login back for the changes to be reflected. To do this just type the word logout in you terminal than close that terminal and open up again. or type docker login

### The to see if Docker is Installed, and if it's up and running 

Use the same command again, to verify that docker is up and running.

```
docker run hello-world
```
## Now let start with creating folder to write my first Dockerfile 

To do that clone you git repository 
by writting 
## git clone https://github.com/hannahmaina/Docker-Project.git
