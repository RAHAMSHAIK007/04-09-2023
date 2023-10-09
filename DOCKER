MONOLITHIC = SINGLE APPLICATION -- > SINGLE SERVER -- > SINGLE DB
MICROSERVICES = SINGLE APPLICATIO‭N -- > MULTIPLE SERVERS -- > MULTIPLE DB

10 X 1 = 100 RS  (DB=100)   = 200 RS/DAY
10 X 10 = 1000 RS(DB=1000)  = 2000 RS/DAY

MONLITICH = SERVER 
MICROSERVICES = CONTAINERS

CONTAINERS = SERVER 

CONTAINER:
its like a server.
containers are light weighted.
it will not have any os by default.
we can install os with images.

IMAGE: 
it have OS, pkgs, and software used to run our container.


CONTAINERAZATION: the process of packing application with its dependencies.
ex: pubg(app) = play store
    maps(dependencies) = internet

after docker = app + maps = playstore


cake(app) = bakery
kinfe(dependency) = house

after docker = cake + kinfe = bakery


DOCKER:
It is a tool used to create containers.
in containers, we can create, run, and deploy our application.
It's free and open source.
It's platform-independent.
but docker runs good on Linux distributions.
docker is written in the GO language.
year: 2013
written by: Solomen Hykes and Sebastian Phal.
os in docker is very very light when compared to servers.
os level of virtualization is called as containerization.

ARCHITECTURE:
DOCKER CLIENT: it interacts with the user (takes input and gives op)
DOCKER HOST: where we install docker-engine (os)
DOCKER DEAMON: manages all docker components (images, containers, n/w, volumes)
DOCKER REGISTRY: stores all docker images on the internet.

INSTALLATION:
yum install docker -y
systemctl start docker
systemctl status docker
docker version  

COMMANDS:

docker pull amazonlinux		: to downlaod an image 
docker images			: to list images
docker run -it --name cont1 amazonlinux	: to downlaod an image 
yum install git maven -y	: to install packages
ctrl d /ctrl p q		: tp exit from conatiner
docker ps 			: to show running containers
docker ps -a			: to show all containers


HISTORY:
  1  yum install docker -y
    2  systemctl start docker
    3  systemctl status docker
    4  docker version
    5  cd /
    6  du -sh
    7  docker pull amazonlinux
    8  docker images
    9  docker run --name cont1 amazonlinux
   10  docker ps
   11  docker ps -a
   12  docker run -it --name cont2 amazonlinux
   13  docker ps
   14  docker ps -a
   15  history


=====================================================
OS LEVEL OF VIRTUALIZATION:

docker pull ubuntu
docker run -it --name cont1 ubutnu
apt update -y
apt install maven git apache2 tree -y
touch file{1..10}
ctrl p q
docker commit cont1 raham:v1
docker images
docker run -it --name cont2 raham:v1

check all the files and pkgs are installed or not.

Above method is manual method of creating custom images.
so we use docker file for automate the work.


DOCKER FILE:
its a way of creating the image automatically.
docker file is using components for it.
Components inside the docker file will be Capital.
In docker file D will be capital.
we can build the image where our docker file is located.

COMPONENTS:
FROM	: used for base image
RUN	: used to execute commands(image creation)
CMD	: used to execute commands(cont creation)
COPY	: to copy local files to the container
ADD	: to copy internet files to container
WORKDIR	: to go our required folder
LABEL	: to attach labels for images
ENV	: variables will work inside container
ARGS	: variables will work outside container
EXPOSE	: to give port number
VOLUME	: to give volume for container
ENTRYPOINT: high priority than cmd


EX:1

FROM ubuntu
RUN apt update -y
RUN apt install git -y
RUN apt install maven -y

docker build -t raham:v1 .
docker run -it --name cont3 raham:v1

EX-2:

FROM ubuntu
RUN apt update -y
RUN apt install git -y
RUN apt install maven -y
RUN apt install tree -y
CMD apt install mysql-server -y


docker build -t raham:v2 .
docker run -it --name cont4 raham:v2


EX-3:


FROM ubuntu
RUN apt update -y
RUN apt install git -y
RUN apt install maven -y
COPY index.html /tmp
ADD http://dlcdn.apache.org/tomcat/tomcat-9/v9.0.80/bin/apache-tomcat-9.0.80.tar.gz /tmp


docker build -t raham:v3 .
docker run -it --name cont5 raham:v3


EX-4:

FROM ubuntu
RUN apt update -y
RUN apt install git -y
RUN apt install maven -y
COPY index.html /tmp
ADD http://dlcdn.apache.org/tomcat/tomcat-9/v9.0.80/bin/apache-tomcat-9.0.80.tar.gz /tmp
WORKDIR /tmp
LABEL author Rahamshaik

docker build -t raham:v4 .
docker run -it --name cont6 raham:v4
docker inspect cont6


EX-5:

FROM ubuntu
RUN apt update -y
RUN apt install git -y
RUN apt install maven -y
COPY index.html /tmp
ADD http://dlcdn.apache.org/tomcat/tomcat-9/v9.0.80/bin/apache-tomcat-9.0.80.tar.gz /tmp
WORKDIR /tmp
LABEL author Rahamshaik
ENV client swiggy
ENV env prod
EXPOSE 8080

LINK FOR INDEX.HTML: https://www.w3schools.com/howto/tryit.asp?filename=tryhow_css_form_icon

DEPLOYMENT:

FROM ubuntu
RUN apt update -y
RUN apt install apache2 -y
COPY index.html /var/www/html
CMD ["/usr/sbin/apachectl", "-D", "FOREGROUND"]

=========================================================================================


DOCKER VOLUMES:

in docker, we use volumes to store the data.
volume is nothing but a folder inside a container.
we can share a volume from one container to another.
the volume contains the files which have data.
we can attach the single volume to multiple containers.
but at a time we can attach only one volume to one container.
volumes are decoupled (loosely attached)
if we delete the container volume will not be deleted.


1. DOCKER FILE:

vim Dockerfile

FROM ubuntu
VOLUME ["/volume1"]

docker build -t raham:v1 .

docker run -it --name cont1 raham:v1 
cd volume1
touch file{1..10}
ctrl p q
docker run -it --name cont2 --volumes-from cont1 --privileged=true ubuntu
cd volume1
ll
touch file{11..20}
ctrl p q
docker run -it --name cont3 --volumes-from  cont1 --privileged=true ubuntu

2. CLI:
docker run -it --name cont4 -v /volume2 ubuntu
cd volume2
ll
touch java{1..10}
ctrl p q
docker run -it --name cont5 --volumes-from cont4 --privileged=true ubuntu
cd volume2 
ls

3. VOLUME MOUNTING:
docker volume ls		: to list volumes
docker volume create raham	: to create volume
docker volume inspect raham	: to get complete info volumes
cd /var/lib/docker/volumes/raham/_data
touch python{1..10}
docker run -it --name cont6 --mount source=raham,destination=/raham ubuntu
cd raham
ls



COPYING FILES FROM CONTAINER TO LOCAL:
docker volume inspect raham
cd /var/lib/docker/volumes/raham/_data
cp * /root

docker volume rm raham1		: to remove volume
docker volume prune		: to remove unused volume
Note: we cant remove attached volume

DOCKER SYSTEM: these commands used to show the docker components information

docker system df    : to show the docker components resource utilzation
docker system df -v : to show the docker components resource utilzation
docker system prune : to remove unused docker components

docker stop : will wait for the proccess to complete inside the container
docker kill : will not wait for the proccess to complete inside the container
docker history raham:v1


RESOURCE MANAGEMENT:
By default docker containers will use host resources (cpu, mem and ram)
there is no limits for containers by default
so we need to set the limit for containers

docker run -it --name cont1 --cpus="0.5" --memory="512MB" ubuntu
docker stats
docker top cont1

HISTORY:
  2  docker version
    3  vim Dockerfile
    4  docker build -t raham:v1 .
    5  docker run  -it --name cont1 raham:v1
    6  docker run -it --name cont2 --volumes-from cont1 --privileged=true ubuntu
    7  docker attach cont1
    8  docker run -it --name cont3 --volumes-from  cont1 --privileged=true ubuntu
    9  docker run -it --name cont4 -v /volume2 ubuntu
   10  docker run -it --name cont5 --volumes-from cont4 --privileged=true ubuntu
   11  docker volume ls
   12  docker volume create raham
   13  docker volume describe raham
   14  docker volume inspect raham
   15  cd /var/lib/docker/volumes/raham/_data
   16  touch python{1..10}
   17  ls
   18  docker run -it --name cont6 --mount source=raham dest=raham ubuntu
   19  docker run -it --name cont6 --mount source=raham,dest=raham ubuntu
   20  docker run -it --name cont6 --mount source=raham,dest=/raham ubuntu
   21  docker run -it --name cont6 --mount source=raham dest=/raham ubuntu
   22  docker run -it --name cont6 --mount source=raham,destination=/raham ubuntu
   23  docker volume inspect raham
   24  cd /var/lib/docker/volumes/raham/_data
   25  ll
   26  cp * /root/
   27  cd
   28  ll
   29  rm -rf *
   30  touch php{1..10}
   31  ll
   32  docker volume inspect raham
   33  cp * /var/lib/docker/volumes/raham/_data
   34  cd /var/lib/docker/volumes/raham/_data
   35  ls
   36  cd
   37  docker volume ls
   38  docker volume inspect b5d30bacf19db8ca2c5c9605200df69b7c898bfcf887b6fd3ab4cfaa45103d48
   39  cd /var/lib/docker/volumes/b5d30bacf19db8ca2c5c9605200df69b7c898bfcf887b6fd3ab4cfaa45103d48/_data
   40  ll
   41  cd
   42  docker volume create raham1
   43  docker volume ls
   44  docker volume rm raham1
   45  docker volume ls
   46  docker volume rm raham
   47  docker volume create raham1
   48  docker system df
   49  docker system df -v
   50  docker kill cont1
   51  docker kill cont2
   52  docker kill cont3
   53  docker ps -a
   54  vim Dockerfile
   55  docker build -t raham:v2 .
   56  docker images
   57  docker network create swiggy
   58  docker system prune
   59  docker build -t raham:v2 .
   60  docker system prune
   61  docker ps -a
   62  docker kill cont4
   63  docker ps -a
   64  docker start cont4
   65  docker ps -a
   66  docker rm cont4
   67  docker kill cont4
   68  docker rm cont4
   69  docker stop cont5
   70  docker rm cont5
   71  docker history raham:v1
   72  vim Dockerfile
   73  touch index.html
   74  docker build -t raham:v1 .
   75  docker history raham:v1
   76  lscpu
   77  lsmem
   83  docker run -it --name cont1 --cpus="0.5" --memory="512MB" ubuntu
   84  docker inspect cont1
   85  docker stats
   86  docker top cont1
   87  history



==============================================
vim Dockerfile

FROM ubuntu
RUN apt update -y
RUN apt install apache2 -y
COPY index.html /var/www/html
CMD ["/usr/sbin/apachectl", "-D", "FOREGROUND"]

Index.html: take form w3 schools 

docker build -t movies:v1 .
docker run -itd --name movies -p 81:80 movies:v1

docker build -t train:v1 .
docker run -itd --name train -p 82:80 train:v1

docker build -t dth:v1 .
docker run -itd --name dth -p 83:80 dth:v1

docker build -t recharge:v1 .
docker run -itd --name recharge -p 84:80 recharge:v1

docker ps -a -q		: to list container ids
docker kill $(docker ps -a -q) : to kill all containers 
docker rm $(docker ps -a -q) : to remove all containers 


DOCKER COMPOSE:
It's a tool used to manage multiple containers
we can create, start, stop, and delete all containers together.
we write container information in a file called a compose file.
compose file is in YAML format.
inside the compose file we can give images, ports, and volumes info of containers.
we need to download this tool and use it.

INSTALLATION:
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
ls /usr/local/bin/
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose version


vim docker-compose.yml

version: '3.8'
services:
  movies:
    image: movies:v1
    ports:
      - "81:80"
  train:
    image: train:v1
    ports:
      - "82:80"
  dth:
    image: dth:v1
    ports:
      - "83:80"
  recharge:
    image: recharge:v1
    ports:
      - "84:80"

COMMANDS:
docker-compose up -d		: to create and start all containers
docker-compose stop		: to stop all containers
docker-compose start		: to start all containers
docker-compose kill		: to kill all containers
docker-compose rm		: to delete all containers
docker-compose down		: to stop and delete all containers
docker-compose pause		: to pause all containers
docker-compose unpause		: to unpause all containers
docker-compose ps -a		: to list the containers managed by compose file
docker-compose images		: to list the images managed by compose file
docker-compose logs		: to show logs of docker compose
docker-compose top		: to show the process of compose containers
docker-compose restart		: to restart all the compose containers
docker-compose scale train=10	: to scale the service


CHANGING THE DEFULT FILE:
by default the docker-compose wil support the following names
docker-compose.yml, docker-compose.yaml, compose.yml, compose.yaml

mv docker-compose.yml raham.yml
docker-compose up -d	: throws an error

docker-compose -f raham.yml up -d
docker-compose -f raham.yml ps
docker-compose -f raham.yml down


images we create on server.
these images will work on only this server.

git (local) -- > github (internet) = to access by others
image (local) -- > dockerhub (internet) = to access by others


STEPS:
create dockerhub account
create a repo

docker tag movies:v1 abduljavvadkhan786/movies
docker login -- > username and password
docker push abduljavvadkhan786/movies


docker tag train:v1 abduljavvadkhan786/train
docker push abduljavvadkhan786/train


docker tag dth:v1 abduljavvadkhan786/dth
docker push abduljavvadkhan786/dth

docker tag recharge:v1 abduljavvadkhan786/recharge
docker push abduljavvadkhan786/recharge

docker rmi -f $(docker images -q)

HISTORY:
  1  yum install docker -y
    2  systemctl start docker
    3  systemctl status docker
    4  vim Dockerfile
    5  vim index.html
    6  docker build -t movies:v1 .
    7  docker run -itd --name movies -p 81:80 movies:v1
    8  vim index.html
    9  docker build -t train:v1 .
   10  docker run -itd --name train -p 82:80 train:v1
   11  vim Dockerfile
   12  vim index.html
   13  docker build -t dth:v1 .
   14  docker run -itd --name dth -p 83:80 dth:v1
   15  vim index.html
   16  docker build -t recharge:v1 .
   17  docker run -itd --name recharge -p 84:80 recharge:v1
   18  docker ps -a
   19  docker ps -a -q
   20  docker kill $(docker ps -a -q)
   21  docker ps -a
   22  docker rm $(docker ps -a -q)
   23  docker ps -a
   24  docker-compose
   25  sudo curl -L "https://github.com/docker/compose/releases/download/1.29.1/docker-compose-$(uname -s)-$(uname                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   -m)" -o /usr/local/bin/docker-compose
   26  ls /usr/local/bin/
   27  sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
   28  sudo chmod +x /usr/local/bin/docker-compose
   29  docker-compose version
   30  vim docker-compose.yml
   31  docker-compose up -d
   32  docker ps -a
   33  docker-compose kill
   34  docker ps -a
   35  docker-compose start
   36  docker ps -a
   37  docker-compose stop
   38  docker ps -a
   39  docker-compose rm
   40  docker ps -a
   41  docker-compose up -d
   42  docker ps -a
   43  docker-compose down
   44  docker ps -a
   45  docker-compose up -d
   46  docker ps -a
   47  docker-compose pause
   48  docker ps -a
   49  docker-compose unpause
   50  docker ps -a
   51  docker run -itd --name cont1 -p 85:80 ubuntu
   52  docker run -itd --name cont2 -p 86:80 ubuntu
   53  docker run -itd --name cont3 -p 87:80 ubuntu
   54  docker run -itd --name cont4 -p 88:80 ubuntu
   55  docker ps -a
   56  docker-compose ps -a
   57  docker-compose images
   58  docker images
   59  docker-compose logs
   60  docker-compose top
   61  docker-compose stats
   62  docker-compose scale train scale=10
   63  docker-compose scale train --scale=10
   64  docker-compose scale train=10
   65  docker-compose  ps
   66  docker-compose ps
   67  docker-compose restart
   68  docker-compose port
   69  docker-compose ports
   70  docker-compose ps
   71  docker-compose down
   72  docker ps -a
   73  docker kill $(docker ps -a -q)
   74  docker rm  $(docker ps -a -q)
   75  docker ps -a
   76  ll
   77  mv docker-compose.yml raham.yml
   78  ll
   79  rm -rf Dockerfile index.html
   80  ll
   81  docker-compose up -d
   82  docker-compose -f raham.yml up -d
   83  docker-compose ps
   84  docker-compose -f raham.yml ps
   85  docker-compose -f raham.yml down
   86  docker images
   87  docker tag movies:v1 abduljavvadkhan786/movies
   88  docker images
   89  docker push abduljavvadkhan786/movies
   90  docker login
   91  docker push abduljavvadkhan786/movies
   92  docker images
   93  docker tag train:v1 abduljavvadkhan786/train
   94  docker push abduljavvadkhan786/train
   95  docker tag dth:v1 abduljavvadkhan786/dth
   96  docker push abduljavvadkhan786/dth
   97  docker tag recharge:v1 abduljavvadkhan786/recharge
   98  docker push abduljavvadkhan786/recharge
   99  docker rmi -f $(docker images -q)
  100  docker images
  101  docker ps -a
  102  docker run -itd --name cont1 -p 81:80 abduljavvadkhan786/movies:latest
  103  docker ps -a
  104  history


==========================================
High Avaliabilty: more than one server
why: if one server got deleted then other server will gives the app

DOCKER SWARM:
its an orchestration tool for containers. 
used to manage multiple containers on multiple servers.
here we create a cluster (group of servers).
in that clutser we can create same container on multiple servers.
here we have master node and worker node.
master node will distribute the container to worker nodes.
worker node main purpose is to maintain the container.
withut docker engine we cant create the cluster.


SETUP:
create 3 servers
install docker and start the service
hostnamectl set-hostname manager/worker-1/worker-2

docker swarm init (manager) -- > copy-paste the token to worker nodes
docker node ls

Note: individual containers are not going to replicate.
if we create a service then only containers will be distributed.

SERVICE: it's a way of exposing and managing multipe conatiners.

docker service create --name movies --replicas 3 -p 81:80 abduljavvadkhan786/movies:latest
docker service ls		: to list services
docker service inspect movies	: to get complete info of service
docker service ps movies	: to list the containers of movies
docker service scale movies=10	: to scale in the containers
docker service scale movies=3	: to scale out the containers
docker service rollback movies	: to go previous state
docker service logs movies	: to see the logs
docker service rm movies	: to delete the services.

Note: if we delete a container it will recreate automatically itself.
it is called as self healing.


CLUSTER ACTIVIES:
docker swarm leave (worker)	: to make node inactive from cluster
docker node rm node-id (manager): to delete worker node which is on down state
docker swarm join-token manager	: to generate the token to join
docker node inspect node_id	: to get comple info of worker node

Note: we cant delete the node which is ready state
if we want to join the node to cluster again we need to paste the token on worker node



DOCKER NETWORKING:
Docker networks are used to make communication between the multiple containers that are running on same or different docker hosts. 
We have different types of docker networks.
Bridge Network
Host Network
None network
Overlay network

BRIDGE NETWORK: It is a default network that container will communicate with each other within the same host.

HOST NETWORK: When you Want your container IP and ec2 instance IP same then you use host network

NONE NETWORK: When you don’t Want The container to get exposed to the world, we use none network. It will not provide any network to our container.

OVERLAY NETWORK: Used to communicate containers with each other across the multiple docker hosts.


To create a network: docker network create network_name
To see the list: docker network ls
To delete a network: docker network rm network_name
To inspect: docker network inspect network_name
To connect a container to the network: docker network connect network_name container_id/name
apt install iputils-ping -y : command to install ping checks
To disconnect from the container: docker network disconnect network_name container_name
To prune: docker network prune



HISTORY:
  1  docker run -itd --name cont1 -p 81:80 abduljavvadkhan786/movies:latest
    2  docker ps -a
    3  docker swarm init
    4  docker node ls
    5  docker run -itd --name cont2 -p 82:80 abduljavvadkhan786/movies:latest
    6  docker ps -a
    7  docker kill cont1 cont2
    8*
    9  docker ps -a
   10  docker service create --name movies --replicas 3 -p 81:80 abduljavvadkhan786/movies:latest
   11  docker ps -a
   12  docker service ls
   13  docker service create --name train --replicas 6 -p 82:80 abduljavvadkhan786/train:latest
   14  docker service ls
   15  docker service inspect movies
   16  docker service ps movies
   17  docker service ps train
   18  docker service scale movies=10
   19  docker service ps movies
   20  docker service scale movies=3
   21  docker service ps movies
   22  docker service rollback movies
   23  docker service ps movies
   24  docker service logs movies
   25  docker ps -a
   26  docker kill 7f8ed843dcb7
   27  docker ps -a
   28  docker kill cc96db0e3219
   29  docker ps -a
   30  docker kill 80da2636e6b8
   31  docker ps -a
   32  docker service rm movies
   33  docker service rm train
   34  docker service ls
   35  docker ps -a
   36* docker service create --name movies --replicas 3 -p 81:80 abduljavvadkhan786/movies:latestdocdock
   37  docker service ps movieses
   38  docker service ps movies
   39  docker node ls
   40  docker node ls4
   41  docker node ls
   42  docker node rm op5w79wi6svb3j4fjp9pq5dal
   43  docker node ls
   44  docker node rm 9j2xs9t04irs4dje6e5eox8f6
   45  docker node ls
   46  docker node rm 4jdjs2hp42nm8egc90gyyrvjq
   47  docker swarm join-token manager
   48  docker node inspect xs0vn9mk4a2e8wudsqrkrsm3w
   49  docker network ls
   50  docker service rm movies
   51  docker network create raham
   52  docker network ls
   53  docker network insepect raham
   54  docker network inspect raham
   55  docker run -itd --name cont1 -p 81:80 abduljavvadkhan786/movies:latest
   56  docker run -itd --name cont2 -p 82:80 abduljavvadkhan786/movies:latest
   57  docker inspect cont1 | grep -i network
   58  docker network connect cont1 raham
   59  docker network connect raham cont1
   60  docker network inspect raham
   61  docker network connect cont2 raham
   62  docker network connect raham cont2
   63  docker network inspect raham
   64  docker run -itd --name cont3 -p 32:80 abduljavvadkhan786/movies:latest
   65  docker network connect raham cont3
   66  docker network inspect raham
   67  docker attach cont1
   68  docker attach cont2
   69  docker ps -a
   70  docker exec -it cont3 ls
   71  docker exec -it cont3 apt update -y
   72  docker exec -it cont3 ping 172.19.0.2
   73  docker exec -it cont3 apt install iputils-ping -y
   74  docker exec -it cont3 ping 172.19.0.2
   75  history
