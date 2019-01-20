
## HOWTO
You can download and execute the project without problems, but if you want to create your own ssh-key, jobs, another among, you can delete the `jenkins_home` folder and the `ssh-keys` and start from the beginning.
### Generate the ssh-key
First, you need to create a ssh key. For example, you can generate it with the following command inside the [centos7](https://github.com/cmardonespino/devops_jenkins/tree/create_docker_compose_for_jenkins/centos7) folder:

* `ssh-keygen -f remote-key`

### Build the images
Execute the following command where is the [docher-compose](https://github.com/cmardonespino/devops_jenkins/blob/create_docker_compose_for_jenkins/docker-compose.yml) file 

* `docker-compose build`

### Start up the containers

`docker-compose up -d`

### Login the containers
When you execute the command `docker ps` you can see the containers that are running. You must to have at least two containers: `jenkins` and `remote` and `remote-host`.

To login to a container, you need to execute the following:

`docker exec -it jenkins bash`

When you execute the previous command, you will to stay inside the jenkins container. You can login by ssh to the `remote-host` (centos7) from ssh.

`ssh remote_user@remote_host`

`remote_user` corresponds to the user that we created in the [centos Dockerfile](https://github.com/cmardonespino/devops_jenkins/tree/create_docker_compose_for_jenkins/centos7/Dockerfile).

`remote_host` corresponds to the centos service name that we can found in the [docker-compose file](https://github.com/cmardonespino/devops_jenkins/blob/create_docker_compose_for_jenkins/docker-compose.yml)

### Useful commands

Copy local files inside a path container

* docker cp "file name" "container name":"path to copy"

Example:

* `docker cp first_script.sh jenkins:/tmp/script.sh`
