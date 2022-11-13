# containers-learning

sudo apt update
And then install any prerequisite packages.

sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
Note that many of these packages are already installed on our Playground server.

We can now add Docker's GPG key.

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
And verify its configuration.

sudo apt-key fingerprint 0EBFCD88
To add the Docker repository, we now just need to run:

sudo add-apt-repository  "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
And update our server again.

sudo apt update
We can now install the necessary packages.

sudo apt install docker-ce docker-ce-cli containerd.io
To finish up, we want to add our cloud_user user to the docker group.

sudo usermod cloud_user -aG docker
Log out then log back in to refresh the Bash session before running any docker commands.



docker run hello-world
docker run alpine
docker container ls
docker container list
docker container list -a

CONTAINER ID   IMAGE         COMMAND     CREATED          STATUS                      PORTS     NAMES
12a7878df6f4   alpine        "/bin/sh"   45 seconds ago   Exited (0) 44 seconds ago             hungry_lovelace
cea8500d9b31   hello-world   "/hello"    7 hours ago      Exited (0) 7 hours ago                funny_meninsky
a8dc363d1dbe   hello-world   "/hello"    2 days ago       Exited (0) 2 days ago                 strange_albattani


docker run -it --name a-container alpine

restart on reboot
docker run -dt --name bg-container --restart always alpine

Unexpected stop / Manual stop
docker run -dt --name bg-container --restart unless-stopped alpine

When Failure occurs
docker run -dt --name bg-container --restart on-failure alpine

default
docker run -dt --name bg-container --restart no alpine

remove containers
docker run -it --name rm-test --rm alpine


docker container ls - List running containers
-a - List all containers
docker run <image> - Create and run a container based on the provided image
-i, --interactive - Keep STDIN open
-t, --tty - Locate a psuedo-tty; without this, there's no command prompt
-d, --detach - Run the container in the background
restart <value> - Set restarting parameters
no - Never restart
always - Always restart when stopped
unless-stopped - Restart unless manually stopped
on-failure<:retries> - Restart when the container fails; we can supply the maximum amount of retries
--rm - Remove the container upon exit
--name <name> - Provide a nickname for the container


docker container start a-container

docker exec a-container apk add nginx

docker exec -it <container> <shell>
docker exec -it a-container ash      <--- For Alpine
docker exec -it a-container bash      <--- For Ubuntu

docker exec a-container cat /etc/nginx/conf.d/default.conf
docker start <container>: Start a container
-i: Attach to STDOUT
docker exec <container> <command>: Run a command against the container
-it <container> <shell>: Drop into a shell prompt
docker cp <source> <container>:<destination>: Copy a file to the container
<container>:<source> <destination>: Copy from a container to localhost

# Container Management 
docker stop <container>: Stop a container

docker restart <container>: Restart a container

docker rm <container>: Remove a container (more than one container can be specified)

docker container prune: Remove all stopped containers

docker rename <container> <new-name>: Rename a container

docker stats: List resource stats for all containers

docker stats <container>: List resource stats for the specified container


https://dockerlabs.collabnix.com/docker/cheatsheet/ 


docker exec -dt web01 nginx -g 'pid /tmp/nginx.pid; daemon off;'

docker inspect <container>: View container information
docker commit <container> <image-name>: Create an image of an existing container
docker run -p <host_port>:<container_port> <container>: Publish to host port




