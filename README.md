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
