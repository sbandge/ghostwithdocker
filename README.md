Prerequisites
•	Ubuntu 18.04 LTS
•	Root privileges

Install Docker Compose
Use below steps to install docker compose from git hub repository.
Use below command to download the docker-compose binary to the '/usr/local/bin' directory.

sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose

change ‘docker-compose’ file executable (Need to change file permissions)

sudo chmod +x /usr/local/bin/docker-compose

Once docker- compose has been installed, run below commands to check its version.

docker-compose version
docker version

Configure ghost with MySQL
In this step, we will create docker-compose file for configuration of ghost application as front end and MySql as backend. Also we will create internal ghost network so that ghost application can communicate with MySQL DB.
 



