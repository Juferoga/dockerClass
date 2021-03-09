# dockerClass

Clase de docker para el Grupo GNU/Linux Universidad Distrital

Comandos a usar 
docker ps
docker run hello-world
docker pull alpine | ubuntu | wordpress | lo que sea | hello-world
docker pull alpine:3.7

docker run alpine:3.7 ls -l1
docker run -it alpine:3.7 sh
    cat /etc/notd

--Ejecutar 2 contenedores o más crear archivos
    docker exec -it <hash> sh
    buscar archivos

___IMAGENES___

docker run -it ubuntu /bin/bash
    apt-get update
    apt-get install sl | figlet | cowsay | fortune
docker ps -a | head # primeros 10

buscamos ubuntu ...

docker commit <hash_ubuntu>
docker image ls | head

Tagueando la imagen

docker image tag <hash> perrito:1.0
docker run perrito sl | fortune
docker run ubuntu sl | fortune

___DOCKER FILE___

FROM UBUNTU

RUN apt-get update; apt-get install sl | fortune

docker build -t perrito:1.1 .
docker image history <hash>

___VOLUMENES Y PUERTOS___

Dockerhub ngnix (Official)

alpine linux de 3 o 4 mb

docker run -d ngnix:1.15.7
docker ps
docker exec -it <hash_ngnix> /bin/bash # exec xq el contenedor ya existe
    apt-get update && apt-get install ps
    ps
    ps fax
    apt-get install curl
    curl localhost
docker stop <hash_ngnix> # para poner codigo :)

***create a index.html

    docker run -v ~/repos/dokerClass/index.html:/usr/share/ngnix/html/index.html:ro -d ngnix:1:15:7 # ubicacionLocal:ubicacionDocker:ReadOnly
    docker ps
    docker exec -it <hash_nginix> bash
        cd /usr/share/ngnix/html/index.html
        apt-get update
        apt-get install curl
        curl localhost
   docker run -v ~/repos/dokerClass/index.html:/usr/share/ngnix/html/index.html:ro -p 8080:80 -d ngnix:1.15.7
   curl localhost:8080
   cambiar index
   curl localhost:8080              :(

TALLER WORDPRESS***

Variables de entorno
    docker run -e MY_SQL_PASSWORD=miclave -e MYSQL_DATABASE=midb -v ~/repos/dockerClass/mysqldata:/var/lib/mysql -d mysql:8.0.13 #Horrible esa linea no?
    
    Para eso tenemos docker compose --> archivo .Yaml en el cul podemos setear todo 
    docker ps
    docker-compose up -d
    docker ps
    docker-compose -ps # wrapper de docker más fácil de manejar

*** Networking ***

docker-compose up -d 
docker ps
docker exec -it <hash_rutorrent> bash
    ifconfig

Desde el navegador entrar a la ip del contenedor

docker ps
docker exec -it <hash_samba> bash
    apt-get update
    apt-get install ifconfig
    apt-get install curl
    curl -I https://192.168.0.5
