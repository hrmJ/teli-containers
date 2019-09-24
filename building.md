# Building the docker containers for tekstitliikkeessä

1. create a network called `teli`

2. start a mongodb container

`docker run --name telimongo --network teli -d mongo:bionic`

You can try to access this database from another container: `docker run -it --network teli --rm mongo:bionic mongo --host telimongo mongotest`

3. Start a container for the api

NOTE that mapping the user to a user on the host

`docker run -it --network teli --user $(id -u):$(id -g)   --rm -v $PWD:/home/developer/project teliapi`
