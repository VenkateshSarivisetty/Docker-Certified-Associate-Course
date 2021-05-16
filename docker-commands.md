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
