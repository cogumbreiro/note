# How to stop and remove all docker images

    docker stop $(docker ps -a -q)
    docker rm $(docker ps -a -q)
    docker rmi $(docker images -q)

Source: https://coderwall.com/p/ewk0mq/ and http://techoverflow.net/blog/2013/10/22/docker-remove-all-images-and-containers/
