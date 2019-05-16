# Ghost with MSSql
Ghost with Ms SQL

### Prerequisites
1.	Ubuntu 18.04 LTS
2.	Root privileges

## Install Docker Compose
1. Use below command to download the docker-compose binary to the '/usr/local/bin' directory :

 ###### sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-$(uname -s)-$(uname -m) -o usr/local/bin/docker-compose 
  
2. Change ‘docker-compose’ file executable (Need to change file permissions)
 ###### sudo chmod +x /usr/local/bin/docker-compose

3. Once docker- compose has been installed, run below commands to check its version.
    ###### docker-compose version
    ###### docker version

## Configure ghost with MySQL
In this step, we will create docker-compose file for configuration of ghost application as front end and MySql as backend. Also we will create internal ghost network so that ghost application can communicate with MySQL DB.

1) Create ghost directory on ubuntu server.
2) Create docker-compose.yml file in it or download from git repo
3) Copy past containts from above docker-compose.yml file. 
4) Create directory "nginx" into ghost directory
   #### About Nginx
      It is open source reverse proxy server for for HTTP, HTTPS, SMTP, POP3, and IMAP protocols, as well as a load balancer, HTTP             cache and a web server (origin server). It helps application for high performence, high accurecy and high conconrrency.
      For more details about Nginx: wikipedia.org/wiki/Nginx
   1. Use Nginx custom configuration to redirect application to secure protocol i.e. from HTTP to HTTPS.
   2. Create or download two files i.e. docker and default.conf in it (or download directly from git hub).
   3. default.conf contains cutom configuration and path of self-signed certificate ( below are mentioned steps for creating self-signed       certificate)
   4. docker file help us to build Nginx image using custom configurations.
   5. Create self-signed certificates
   6. Create selfsign directory at location "/etc/selfsign/"
   7. Navigate to selfsign directory and execute below command.
   ###### openssl req -x509 -nodes -days 365 -newkey rsa:4096 -keyout nginx-selfsigned.key -out nginx-selfsigned.crt
   8. To generate a DH key and enable dhparam, execute below command 
   ###### openssl dhparam -out dhparam.pem 2048
   9. Make sure path of certificate mentioned in default.conf is same as created one as above.
     1. Also verify certificate path in docker-compose.yml file.
 5) To access the NGINX container from outside world, Make sure to map host port (80/443) with container port (80/443).
     1. Also check if your machine does not block these ports(enable them if not).
 6) Once all above steps completed we are ready for build our containers.
     1. Execute below command from docker-compose.yml file location.
        ###### docker-compose up -d
     2. Check status of containers using below command
        ##### docker ps
 7) Browse URL using http://<host ip> or http://<<hostname>> 
      1. It will redirect to HTTPS protocol.
 



