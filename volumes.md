## Docker Volumes
The file system of a Docker container can be deleted or removed when the container dies.

And Docker solves this problem in two ways
## 1 Volumes
## 2 Bind Directory on a host as a Mount
Volume provide ways to store data on host file system separate from container's file. so that we cant loose data even when container is deleted or recreated after been removed

You can create a new volume using the following command:
## docker volume create <volume_name> 

Once a volume is created, we can mount it to a container using the -v or --mount option by running the following docker command.
## docker run -it -v <volume_name>:/data <image_name> /bin/bash
