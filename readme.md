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
