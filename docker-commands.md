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
