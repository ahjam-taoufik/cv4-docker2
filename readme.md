build -t => specify a name 
docker image ls -q =>get only images id
docker image ls                 => list of image
docker image rm <name or id of image> =>remove image
docker ps    =>list of container running
docker ps -a =>list of container running and stopped
===============================================================  


docker build -t hello-docker .  =>build image named hello-docker
docker build -t hello-docker:tag_name_orNumber .  =>build image named hello-docker with tag
========================================================================
docker run ubuntu   => new container from ubuntu image without running

docker run -i -d ubuntu                  => new container from ubuntu image and running it  with detach
docker run --name ubuntu1 -i -d ubuntu   => naming container

docker run -i ubuntu   => new container from ubuntu image and running it  with attach
docker run -i -t ubuntu   => new container from ubuntu image and running it with interactive


============================================================
docker image prune => remove dangling images (none name and none tag)
docker container prune => remove all container stopped



docker image tag <name or id of image> <name>:<tag>  => create tag for an image  
docker login
docker logout
docker push <name_of_image>:tag => push image in hub.docker
docker image save -o name_image.zip <name_of_image>:<tag> => save image without uploaded in hub.docker
docker image load -i name_image.zip   =>load image in your local docker

docker exec -it <name_of_container> sh

docker volume create app-data
docker volume inspect app-data

docker cp <name or id of container>:<name of file ex:/app/log.txt> . => copy file from container to local file
docker cp file.txt <container>:<file ex: /app> =>copy file from local to container
docker run -d -p 5001:3000 -v $(pwd):/app react-app  => mapping between the local directory and container for the live changing 

docker container rm -f $(docker container ls -aq) =>remove all containers
docker image rm -f $(docker image ls -q) =>remove all images
======================================
docker-compose build => build image
docker-compose up  => start container
docker-compose up -d --build => build image and start container with detach
docker-compose stop => stop container
docker-compose logs
docker-compose logs <id or name of container>
======================
======================
docker --version
docker -v
docker version
docker info
docker container run -d <name of image>       =>he create container immediately if you have image , otherwise docker download this image from   
                                                hub.docker (-d or --detach : detached from cmd)
docker run --name <container_name> <image_name> 
docker container run -d <name of image>:version ( example : docker container run -d redis:alpine )                             
docker container start n1
docker container stop <name of container>
docker ps -all                   => show containers list
docker container ls -a           => show containers list (all copies)
docker images ls                   => show all images
docker rm <id of container>   => remove container
docker image rm <name of image or id>  => remove image
docker system prune -a => delete all images all containers all volumes
docker inspect <name of image>           
docker inspect <name of image>:version
docker logs <name or id  of container>  
docker stats <container>   => statics (cpu, memoir . . .)
docker container run --detach --publish 80:80 --name n1 nginx
docker container run --detach --publish 80:80 --name n1 --rm nginx => (remove container ones we stopped )
docker login
docker logout
docker exec -it <container> bash
  example command bash :
     service nginx -V
     service nginx status
     service nginx reload
     service nginx stop
     ls
     nginx -T
     touch index.html
     cat index.html
     mkdir file1
     rm file1
     cp file1 content =>copy file1 in content folder
==========================================
docker build .
docker build -t my_image .  => (-t = to give him a name) 
docker build --tag hello .  => create image with tag
docker tag <id of image or old_name> <name>:<name_tag>
docker pull mariadb   =>only import image (don't create container)
docker run -d --name mymariadb -e MARIADB_ROOT_PASSWORD=1234 mariadb
docker run -d --name mymariadb -e MARIADB_ROOT_PASSWORD=1234 -v mariavolume:/var/lib/mysql mariadb => container with volume
docker volume ls


docker volume create maria_test => create empty volume
docker run -d --name mymariadb1 -e MARIADB_ROOT_PASSWORD=1234 -v maria_test:/var/lib/mysql mariadb 
docker run -d --name mymariadb2 -e MARIADB_ROOT_PASSWORD=1234 -v maria_test:/var/lib/mysql mariadb 
   ( NB:  mymariadb1 and mymariadb2 connect to the same volume )

        docker exec -it maria-test bash
        root#33124545:/# mysql --version
        root#33124545:/# mysql -u root -p
        mariaDB > show databases;
        mariaDB > create database testbase;
=============================================================
Bind Mounting
============
  C:\data> docker container run -it --name alpine -v ${pwd}:/mounted_folder alpine
  C:\data> docker container run -d --name nginx1 -p 8080:80 -v ${pwd}:/usr/share/nginx/html nginx
     NB: -d =>  detach
====================================================
docker network ls                                 => list of network
docker network inspect bridge
docker network create --driver bridge n1           => create network of type bridge
docker network create --driver bridge --subnet 172.25.0.0/16 n2          
docker network inspect n1
docker run --network=n1 -d -it nginx                 => create container in network n1
docker network disconnect n2 <container1>
docker network connect n1 <container1>

=================================================
docker-composer down --rmi all -v
