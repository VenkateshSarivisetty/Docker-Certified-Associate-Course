## Docker Commands

# Run a container called **webapp** with image nginx, and in a **interactive mode**.

docker run -it --name=webapp nginx

# Which combination of keys are used to escape from the shell and keep the container **webapp** running?

Cntrl+p+q

# Which combination of keys are used to exit from the shell and stop the container webapp?

Cntrl+c

# You have a running container and want to execute a command inside it. Which command will you use?

docker exec -it <container name> /bin/bash

# We deployed a container called webapp. Inspect this container to get the IPPrefixLen.

docker container inpect webapp | grep IPPrefixLen

# We have deployed some containers. What command is used to get the container with the highest memory?

docker container stats

# How to display the running processes inside the container?

docker container top container-name

# You have a **webapp** container and image **httpd**.Inspect the logs of the webapp container.Which command is used to get the stream logs of the webapp container so that you can view the logs live?

docker container logs -f webapp

# Which command returns only new and/or live events?

docker system events

# Which command returns events since the past 30 minutes?

docker system events --since 30m

# Which command is used to get the events of the container named "webapp"?

docker system events --filter 'container=webapp'

# Run a container named webapp with nginx image in detached mode.

docker container run --detach --name=webapp nginx

# Stop the container named "nginx".

docker container stop nginx

# How do you list running & stopped containers?

docker container ls -a

# Delete the "webapp" Container

docker container rm webapp

# Stop all running containers on the host

docker container stop $(docker container ls -q)

# Delete all running and stopped containers on the host

docker container rm $(docker container ps -qa)

# Which command is used to delete the stopped containers?

docker container prune

# What is the command to pause a running container?

docker container pause

# What are the signals sent to a running container when the docker container stop command is executed?

SIGTERM followed by SIGKILL

# Run a container with image nginx, name nginx and hostname webapp.

docker container run -d --name nginx --hostname=webapp nginx

# What is the hostname set on the container when the following command is run :docker container run -d --name webapp httpd

containers unique id

# What is the default restart policy?

no

# Which policy would restart the containers even after the docker daemon is restarted?

always

# Which policy is used to restart a container unless it is explicitly stopped or Docker is restarted.

unless-stopped

# Which command can be used to check the restart policy of webapp container?

docker container inspect webapp

# Restart container unless it is explicitly stopped or Docker is restarted.

unless-stopped

# Which command should be used to update the httpd container with the always policy?

docker container update --restart always httpd

# Which command should be used to update all the running containers with unless-stopped policy?

docker container update --restart unless-stopped $(docker container ls -q)

# Which option is used to reduce container downtime due to daemon crashes, planned outages, or upgrades?

Live Restore

# What is the path file which is used to add the live restore?

/etc/docker/daemon.json

# How to enable the live restore setting to keep containers alive when the daemon becomes unavailable?

echo '{"live-restore" : "true"}' >>/etc/docker/daemon.json

# hich of the below commands may be used to copy a file /web.conf from a container named webapp with id 89683681 to the /tmp directory on the host?

docker container cp 89683681:/tmp/web.conf /tmp/ (or)
docker container cp webapp:/web.conf /tmp/

# Copy the /etc/nginx directory from the webapp container to the docker host under /tmp/.

docker container cp webapp:/etc/nginx /tmp/

# What is the command to copy the file /root/myfile.txt from the host to /root/ of the webapp container?

docker container cp /root/myfile.txt webapp:/root/

# We can copy a file from a stopped container.

True

# Data inside the container is persistent.

False

# You can run multiple instances of the same application on the docker host.

True

# You can map to the same port on the Docker host more than once.

False

# Which option could be used to expose a webapp container to the outside world?

--publish or -p or -P

# Map TCP port 80 in the container to port 8080 on the Docker host for connections to host IP 192.168.1.10 . Select the all right answers

-p 192.168.1.10:8080:80 or -p 192.168.1.10:8080:80/tcp

# Unless specified otherwise, docker publishes the exposed port on all network interfaces.

True

# Map UDP port 80 in the container to port 8080 on the Docker host.

-p 8080:80/udp

# How does the -P option in the docker container run command know what ports to publish on the container?

It uses the ExposedPorts fields set on the container or Expose instructions in Dockerfile

# How does docker map a port on a container to a port on the host?

IPTables Rules

# What IPTables chains does Docker modify to configure port mapping on a host?

Docker

# How to check the logs of the docker daemon?

journalctl -u docker.service or less /var/log/messages or less /var/log/daemon.log or less /var/log/docker

# Enable the debugging mode. Select the right answer

echo '{"debug": true}' > /etc/docker/daemon.json

# How to check if the docker service is running or not?

sudo systemctl status docker

# Which environment variable will be used to connect a remote docker server?

DOCKER_HOST

# What may be the cause of this error: "unable to configure the Docker daemon with file /etc/docker/daemon.json: the following directives are specified both as a flag and in the configuration file: tls: (from flag: true, from file: false)"?

The tls flag is set to false in daemon.json file and true in the command line

# What is the default logging driver?

json-file

# Where is the log of the webapp container with id 78373635 on the Docker Host?

/var/lib/docker/container/78373635/78373635.json

# Which command is used to check the default logging driver?

docker system info

# How to change the default logging driver to syslog?

echo '{"log-driver" : "syslog"}' > /etc/docker/daemon.json

# Run a webapp container, and make sure that no logs are configured for this container.

docker container run -it --logging-driver none webapp

# How to display the running processes inside the container?

docker container top container-name

# Delete all running and stopped containers on the host.

docker container rm -f $(docker container ls -qa)

# Which of the below commands create a container with redis image and name redis?

docker container create --name=redis redis

# What file is used to configure the docker daemon?

/etc/docker/daemon.json

# What is the port used to configure encrypted traffic on TCP?

2376

# Delete the stopped container named db.

docker container rm db

# We have deployed some containers. What command is used to get the container with the highest memory?

docker container stats

# Run a container called apps with image nginx, and in an interactive mode.

docker container run -it --name apps nginx

# Which policy should be used to restart the container at all times except when it is stopped manually by a user?

unless-stopped

# Which command should be used to update the restart policy of the httpd container with always?

docker container update --restart always httpd

# What is the path to the file which is used to add the live restore option?

/etc/docker/daemon.json

# Copy the /etc/nginx directory from the webapp container to the docker host at the path /tmp/.

docker container cp webapp:/etc/nginx /tmp

# You can map multiple containers to the same port on the Docker host

FALSE

# Which environment variable will be used to connect to a remote docker server?

DOCKER_HOST

# Which command is used to check the default logging driver?

docker system info

# Run a dev container, and make sure that no logs are configured for this container.

docker container run -it --log-driver none devs

# What is the default logging driver?

json-file

# How to check if the docker service is running?

sudo systemctl status docker

# How does docker map a port on a container to a port on the host?

Using IP Tables Rules

# How does docker map a port on a container to a port on the host?

DOCKER

# What option is used in the docker command to map UDP port 80 in the container to port 9595 on the Docker host?

-p 9595:80/udp

# Unless specified otherwise, docker publishes the exposed port on all network interfaces

True

# You can run multiple instances of the same application on the docker host.

True

# Data inside the container is deleted when the container is destroyed.

True

# What is the command to copy the file /root/myconfig.txt from the host to /root/ of the data container?

docker container cp /root/myconfig.txt data:/root/

# Which option is used to reduce container downtime due to daemon crashes, planned outages, or upgrades?

Live Restore

# Which command is used to update all running containers with the unless-stopped restart policy?

docker container update --restart unless-stopped $(docker container -q)

# Which command can be used to check the restart policy of a webapp container?

docker container inspect webapp

# Run a container with image nginx, name lab and hostname testing.

docker run -d --name lab --hostname=test nginx

# What is the command to pause a running container?

docker container pause

# Which command is used to get the events of the container named dev-apps?

docker system events --filter 'container=dev-apps'

# Which command is used to get the stream logs of the web-app container so that you can view the logs live?

docker container logs -f webapp

# What is the purpose of a private registry?
1. Tightly control where your images are being stored.
2. Fully own your images distribution pipeline
3. Integrate image storage and distribution tightly into your in-house developme   nt workflow.

# What is the default public registry for docker?

DockerHub

# What is the default tag if not specified when building an image with the name webapp?

latest

# Run ubuntu container with the trusty tag.

docker run ubuntu:trusty

# Which command is used to list the local images?

docker image ls

# List the full length image IDs.

docker images --no-trunc

# Display images with a name containing postgres, at least 12 stars.

docker search postgres --filter=stars=12

# Download nginx image from the Google Container Registry hub registry.

docker pull gcr.io/kodekloud/nginx

# Display images with a name containing busybox, at least 3 stars and are official builds.

docker search --filter=stars=3 --filter is-official=true busybox

# What is the command to change the tag of "httpd:latest" to "httpd:v1" ?

docker image tag http:latest httpd:v1

# You have an nginx:v1 image with size 100M. You’ve now created your own version of the image - nginx:v2 by retagging the first image, what is the total size of both?

100M

# Which command should be used to get the total size consumed by all images on a host?

docker system df

# In the output of the "docker system df" command what does the ACTIVE field indicate on the images row?

Number of Images with containers

# What is the user/account and image/repository name for the image company/nginx?

image=nginx,user=company

# Choose the right command to pull ubuntu image from a private registry at gcr.io

docker pull gcr.io/kk/ubuntu

# Which command is used to authenticate with azr.com registry which listens on port 5000?

docker login azr.com:5000

# You are required to store a copy of the official alpine image in your company's internal docker registry. What would be your approach?

pull the official image, tag it with the address of the internal docker registry and push to the internal docker registry

# When you log in to a registry, the command stores credentials in … (Please explore the documentation pages for this)

$HOME/.docker/config.json

# While trying to delete image postgres, you got an error "conflict: unable to remove repository reference "postgres" (must force) - container 1a56b95e073c is using its referenced image adf2b126dda8". What may be the cause of this error?

A container is using this image

# Which command is used to remove webapp:v1 image locally?

docker image rmi webapp:v1

# Remove all unused images on the Docker Host

docker image prune -a

# Display all layers of httpd image along with the size on each layer.

docker image history httpd

# Which command can be used to get the ExposedPorts of a webapp image?

docker image inspect webapp

# How to get the Os field alone of the httpd image?

docker image inspect httpd -f '{{.Os}}'

# Which subcommand will be used to get more info about images?

inspect

# Print the value of 'Architecture' and 'Os' for a 'webapp' image.

docker image inspect webapp -f '{{.Os}}' '{{.Architecture}}'

# Which command can be used to get a backup of image webapp?

docker image save webapp -o webapp.tar

# A tarfile - nginx.tar - has been created using the docker image save command. Which command can be used to extract it into your docker host.

docker image load -i nginx.tar

# A government facility runs a secure data center with no internet connectivity. A new application requires access to docker images hosted on docker hub. What is the best approach to solve this?

pull docker images from the host with access to docker hub,convert to a tarball using docker image save command, and copy to the restricted environment and extract the tarball.

# You have created a nginx container and customized it to create your own webpage. How can you create an image out of it to share with others?

docker export

# How do you restore an image created from the docker export command?

docker image import

# The “export” command works with Docker images.

True

# Export webapp container’s filesystem as a tar archive. Select the right answer

docker container export webapp > mywebapp.tar

# Steps to import/export image and container respectively

save and load images as a tarball.
Export and import the containers as a tarball.

# Which of the following commands used to match all images with the com.example.version label?

docker images --filter "com.example.version"

# Which of the following is not an instruction supported in the Dockerfile? Select the all right answers.

EXEC

# The ... is a text document that contains all the commands a user could call on the command line to assemble an image.

Dockerfile

# Which method can be used to build an image using existing containers?

docker export or docker commit

# The container being committed and its processes will be paused while the image is committed.

True

# We have a running container named webapp with the nginx image. We added a custom html file to this container. How do we create an image named mynginx from this container?

docker container commit webapp mynginx

# The docker container commit is the recommended approach for building a custom image.

False

# You are required to create an image from an existing image. What is the recommended approach?

Use docker image save and load docker image command

# You are required to create an image from an existing container. What is the recommended approach?

Use docker container export and docker image import command

# Whenever a build is initiated by running the Docker build command, the files under the build context are transferred to the Docker daemon, at a temporary directory under the docker’s filesystem. Which directory are these files stored in?

/var/lib/docker/tmp

# Which of the below commands may be used to build an image with the Dockerfile filename?

docker build . or docker build -f dockerfile .

# While building a docker image from code stored in a remote URL, which command will be used to build from a directory called docker in the branch dev?

docker build https://github.com/kk/dca.git#dev:docker

# A build’s context is the set of files located in the specified PATH or URL, Which kind of resources can the URL parameter refer to ?

Git repositories/pre-packaged tarball contexts/path to a local directory

# Choose the correct flag to apply a tag to an image done

-t

# If you do not specify a tag name, you can’t build the image

False

# Build an image using a context build under path /tmp/docker and name it webapp.

docker build /tmp/docker -t webapp

# What is the default tag if not specified when building an image with the name webapp?

latest

# What is the command to build an image using a Dockerfile.dev file under path /opt/myapp with the name webapp. The current directory you are in is /tmp.

docker build -f /opt/myapp/Dockerfile.dev /opt/myapp -t webapp

# What is the file used to exclude temporary files such as log files or builds from the context during a build?

.dockerignore

# If the build fails at a particular stage, it repurposes the previous layers from the cache and does not really rebuild them.

True

# What is a recommended approach for installing packages and libraries while building an image?

Use the RUN instruction and have the apt-get update and apt-get install commands  on the same instructions

# Using RUN apt-get update && apt-get install -y ensures your Dockerfile installs the latest package versions with no further coding or manual intervention. This technique is known as …..

Build-Context

# What is a best practice while installing multiple packages as part of the install instruction?

Add them on seperate lines seperated by slash in alphanumeric order.

# Which among the following scenarios will lead to docker invalidating cache on a given layer?

Chane in instruction/Change in a file with the ADD instruction

# forces the build to install a particular version of package regardless of what’s in the cache. This technique can also reduce failures due to unanticipated changes in required packages.

Version Pinning

# What is a recommended approach to reduce build time while building docker images?

Instuctions likely to change more often must be at the bottom of the Dockerfile.

# A Dockerfile is built from the Ubuntu image as the base image. What would happen to the cache when a new version of the Ubuntu image is made available at Dockerhub?

Cache is not validated and docker continues to use existing cache

# Which option can be used to disable the cache while building a docker image? (Explore the docker documentation for this)

--no-cache=true

# COPY instruction only supports the basic copying of local files into the container

True

# What is the right instruction to download a file from "https://file.tar.xz" and auto-extract it into "/testdir" in the image?

ADD https://file.tar.xz /testdir

# COPY instruction has some features like local-only tar extraction and remote URL support.

False

# Which instruction(s) can be used in the Dockerfile to copy content from the local filesystem into the containers?

COPY and ADD

# Which of the following is the correct format for CMD instruction?

CMD ["executable","param1","param2"] or CMD ["param1","param2"] or CMD command param1 param2

# If CMD is used to provide default arguments for the ENTRYPOINT instruction, both the CMD and ENTRYPOINT instructions should be specified.

True

# When a user runs the command docker run my-custom-image sleep 1000

docker overrides the CMD instruction with "sleep 1000"

# Choose the correct instruction to add the echo "Hello World" command in the Dockerfile.

CMD ["echo", "Hello World"]

#  What is the output of the following Dockerfile snippet when container runs as docker run -it < image> ?
ENTRYPOINT ["/bin/echo", "Hello"]
CMD ["world"]

Hello World

# What is the output of the following Dockerfile snippet when container runs as docker run -it <image> kk ?
ENTRYPOINT ["/bin/echo", "Hello"]
CMD ["World"]

Hello kk

# If you list more than one CMD instruction in the Dockerfile then only the last CMD will take effect.

True

# A parent image is the image that your image is based on. It refers to the contents of the FROM directive in the Dockerfile.

True

# A parent image has FROM scratch in its Dockerfile.

False

# While building an image, You have one base image, but there could be multiple parent images.

True

# How do you identify if a Docker file is configured to use multi-stage builds?

The Dockerfile has multiple FROM instructions

# The "--from=0" in the following Dockerfile instruction line refers to:
"COPY --from=0 /go/src/github.com/alexellis/href-counter/app ."

The image built using the first set of instructions in the Dockerfile.

# By default, the stages are not named, and you refer to them by their integer number, starting with 1 for the first FROM instruction in the multi-stage build.

False

# Name the stage which uses nginx as a base image to builder in the Dockerfile.

From nginx AS builder

# What is the instruction used to copy a file from an external image named redis not part of any stage in the multi-stage build process. (Refer to the documentation for this one)

--from=redis

# You are developing an e-commerce application. The application must store cart details of users temporarily as long as the user’s session is active. What is the recommended approach to storing the cart details with the application deployed as a docker container?

Store the cart details in a volume backed by a in-memory cache service like redis

# It’s recommended to avoid sending unwanted files to the build context by using .gitignore file to exclude those files.

False

# An application you are developing requires an httpd server as frontend, a python application as the backend API server, a MongoDB database and a worker developed in Python. What is the recommended approach in building images for these containers?

Build seperate images for each component of the application.

# Which of the below can help minimize the image size?

only install necessary packages within the image/ Combine multiple dependent instructions into a single one and cleanup temporary files / Use multi-stage builds

# Which is the recommended approach to install packages following the best practices in Dockerfile?

Run apt-get update && apt-get install -y \
    git \
    httpd
    
# Which of the below steps can help minimize the build time of images?

Avoid sending unwanted files to the build context using .dockerignore
Move the instructions that are likely to change most frequently to the bottom of the Dockerfile.

# Which of the following tag image will get when creating a redis container with image redis?
docker run -itd --name redis redis

# What is the command to change the tag of busybox:latest to busybox:v1?

docker image tag busybox:latest busybox:v1

# What is the command to list the images in Docker host?

docker image ls

# What is the command to remove all unused images on the Docker host?

docker image prune -a

# What is the command to build an image with the name webapp using a Dockerfile file under path /opt/myapp . The current directory you are in is /tmp.

docker build -f /opt/myapp/Dockerfile /opt/myapp -t webapp

# Which command is used to list the full length image IDs?

docker image --no-trunc

# Which command is used to download the redis image from Docker Hub?

docker image pull redis

# Which method can be used to build an image using existing containers?

docker commit

# You are required to generate a report of the total amount of space consumed by docker images, containers and build cache on a docker host. What would be your approach?

Run the command docker system df

# Which command can be used to get a backup of image mysql?

docker image save mysql -o mysql.tar

# What is a best practice while installing multiple packages as part of the install instruction?

Add them on seperate lines seperated by a slash in alphanumeric order

# Which of the below statements are true:

By default a container runs with unlimited cpu and memory resources

# What will happen if the --memory-swap is set to -1?

the container allowed to use unlimited swap.

# Each container gets a CPU share of .... assigned by default

1024

# What is a linux feature that prevents a process within the container to access raw sockets?

Kernal capabilities

# By default, all containers get the same share of CPU cycles. How to modify the shares?

docker container run --cpu-shares=513 nginx 

# Which command is used to list the default available networks?

docker network ls

# Which command is used to see the network settings and IP address assigned to a container with id c164825bb3d3 that uses the myapp image?

docker inspect c164825bb3d3

# What is the default network driver used on a container if you haven’t specified one?

bridge

# Overlay networks connect multiple Docker daemons together and enable swarm services to communicate with each other.

True

# f you use the …... network mode for a container, that container’s network stack is not isolated from the Docker host (the container shares the host’s networking namespace), and the container does not get its own IP-address allocated.

host

# How to get the subnet, gateway of the network c0a0b59a3807?

docker network inspect c0a0b59a3807

# Which of the following commands would create a user-defined bridge network called my-net?

docker network create my-net / docker network create -d bridge my-net / docker network create --driver bridge my-net

# What is the command to connect a running container with name myapp to the existing bridge network my-net?

docker network connect my-net myapp

# What is the command to remove all unused networks?

docker network prune

# What is the command to remove the my-net network?

docker network rm my-net

# Which of the following commands would create a user-defined bridge network called dev-net?

docker network create dev-net / docker network create -d bridge dev-net / docker network create --driver bridge dev-net

# What is the command to connect a running container with name myapp to the existing bridge network dev-net?

docker network connect dev-net myapp

# Which command is used to disconnect the my-net network from the redis container?

docker network disconnect my-net redis

# Which command is used to see the details of the subnet and gateway of network id ce982a9edf65?

docker network inspect ce982a9edf65

# By default, all files created inside a container are stored on a writable container layer.

True

# Volumes are the preferred mechanism for persisting data generated by and used by Docker containers.

True

# What is the command to remove unused volumes?

docker volume prune

# What is the command to create a volume with the name my-vol?

docker volume create my-vol

# What is the command to list volumes?

docker volume ls

# What is the command to get details of the volume my-vol such as the driver, mountpoint, volumename, ..etc?
 
docker volume inspect my-vol

# Which command is used to remove the my-vol volume?

docker volume rm my-vol

# The volumes are mounted as “readonly” by default inside the container if no options are specified.

False

# You can remove a vol1 which is in use by a container using the command docker volume rm --force vol1.

False

# Which option is used to mount a volume ?

--mount --volume -v

# Which among the below is a correct command to start a webapp container with the volume vol2, mounted to the destination directory /app?

docker run -d --name webapp -v vol2:/app httpd
docker run -d --name webapp --mount source=vol2,target=/app httpd
docke run -d --name webapp --volume vol2:/app httpd

# Which among the below is a correct command to start a webapp container with the volume vol3, mounted to the destination directory /opt in readonly mode?

docker run -d --name webapp -v vol3:/opt:ro httpd
docker run -d --name webapp --volume vol3:/opt:ro httpd
docker run -d --name webapp --mount source=vol3,target=/opt,readonly httpd

# By default, all files inside an image are in a writable layer.

False

# What is the command to create a volume with the name first-volume?

docker volume create first-volume

# Which among the below is a correct command to start an appstore container with the volume vol1, mounted to the destination directory /opt in read-only mode?

docker run -d --name appstore -v vol1:/opt:ro httpd
docker run -d --name appstore --volume vol1:/opt:ro httpd
docker volume -d --name appstore --mount source=vol1,target=/opt,readonly httpd

# Volumes are the preferred mechanism for persisting data generated by and used by Docker containers.

True

# Using ...... we can configure containers and communication between them in a declarative way.

Docker-Compose

# ....... is a YAML file which contains details about the services, networks, and volumes for setting up a Docker application.

Docker Compose

# Which command can be used to create and start containers in foreground using the existing docker-compose.yml?

docker-compose up

# Which command can be used to create and start containers in background or in detached mode in compose using the existing docker-compose.yml?

docker-compose up -d

# ...... is the command to list the containers created by compose file.

docker-compose ps

# ...... is the command to check the logs for the whole stack defined inside compose file.

docker-compose logs

# Which command can be used to stop (only and not delete) the whole stack of containers created by compose file?

docker-compose stop

# docker-compose stop command stops and removes the whole stack of container created by compose file.

False

# Select the right answer. Which command can be used to delete the application stack created using compose file?

docker-compose down

# Compose files that doesn't declare a version are considered “version 0”

False

# Compose files using the version 2 and version 3 syntax must indicate the version number at the root of the document.

True

# With the docker-compose up command, we can run containers on multiple docker hosts.

False

# The RAFT logs are stored in memory on the manager nodes.

False

# The RAFT logs are stored on disk and not protected.

False

# The default behaviour requires you to unlock the swarm when a new node joins the swarm cluster. 

False

# After restarting the docker service and trying to run docker service ls, you get an error "Error response from daemon: Swarm is encrypted and needs to be unlocked before it can be used. How can you solve this error?

docker swarm unlock

# Which command can be used to return the current key which is used inside the cluster ?

docker swarm unlock-key

# Which command can be used to enable auto lock on an existing swarm?

docker swarm update --auto-lock=true

# ... are one or more instances of a single application that runs across the Swarm Cluster.

services

# Which command can be used to run an instance on swarm?

docker service create webapp

# What is the command to run 3 instances of httpd on a swarm cluster?

docker service create --replicas=3 httpd

# What component is responsible for creating tasks in swarm?

orchestrator

# What component is responsible for instructing a worker to run a task?

scheduler

# The .... assigns tasks to nodes in swarm.

dispatcher







