## Docker Commands

#Run a container called **webapp** with image nginx, and in a **interactive mode**.

docker run -it --name=webapp nginx

#Which combination of keys are used to escape from the shell and keep the container **webapp** running?

Cntrl+p+q

#Which combination of keys are used to exit from the shell and stop the container webapp?

Cntrl+c

#You have a running container and want to execute a command inside it. Which command will you use?

docker exec -it <container name> /bin/bash

#We deployed a container called webapp. Inspect this container to get the IPPrefixLen.

docker container inpect webapp | grep IPPrefixLen

#We have deployed some containers. What command is used to get the container with the highest memory?

docker container stats

#How to display the running processes inside the container?

docker container top container-name

#You have a **webapp** container and image **httpd**.Inspect the logs of the webapp container.Which command is used to get the stream logs of the webapp container so that you can view the logs live?

docker container logs -f webapp

#Which command returns only new and/or live events?

docker system events

#Which command returns events since the past 30 minutes?

docker system events --since 30m

#Which command is used to get the events of the container named "webapp"?

docker system events --filter 'container=webapp'

#Run a container named webapp with nginx image in detached mode.

docker container run --detach --name=webapp nginx

#Stop the container named "nginx".

docker container stop nginx

#How do you list running & stopped containers?

docker container ls -a

#Delete the "webapp" Container

docker container rm webapp

#Stop all running containers on the host

docker container stop $(docker container ls -q)

#Delete all running and stopped containers on the host

docker container rm $(docker container ps -qa)

#Which command is used to delete the stopped containers?

docker container prune

#What is the command to pause a running container?

docker container pause

#What are the signals sent to a running container when the docker container stop command is executed?

SIGTERM followed by SIGKILL

