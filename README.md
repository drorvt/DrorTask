
<!-- ABOUT THE PROJECT -->
## About The Project
1. In this project we create a  continuous integration process using Github, Travis-CI and Docker HUB, the files used here can be found * [HERE](https://github.com/drorvt/drortask/)

2. Deploy docker container from Dockerhub with Vagrant and Ansible



<!-- GETTING STARTED -->
## Getting Started



### Prerequisites

1. We need to install *.[virtualbox](https://www.virtualbox.org/wiki/Downloads) and *.[vagrant](https://www.vagrantup.com/downloads.html) on our local computer to work with vagrant.
2. Create a public docker repository at dockerhub, to push the docker images 
3. Setup continous build, use in github Travis CI to build and push the docker image to dockerhub
4. install virtualbox and vagrant on our local computer to work with vagrant.



### Installation Application

We will review the docker file, the app code and the travis-ci file

## main.go
first we check for the port to use, then convert it to a number, register the handler for our HTTP function and listen for requests, this code should print our ip address as you would expect by the name.

## main_test.go
The test is fairly simple it just checks that the web server works by trying to fetch / and checking for an empty body and 200 status code.

## Dockerfile
We set the working directory to please go, then fetch dependencies and install our binary, we also generate a test binary, expose the port that we want to use and set the user as nobody in case someone can exploit our app and jump into our container, then just set the command to execute on docker run.

## .travis.yml
We let travis know that we will be running some go code and also docker, then build the image, run the tests and then the app as initialization, after that we validate that the app works and lastly login to dockerhub and push the image, the important things to have in mind here is that we use variables for example the repo name, the commit SHA, and the docker username and password in a secure way, since travis-ci hides the values that we tell them to.


## Application

1. Putting everything together (all files)
2. connect to travis ci , then link your github account to it, then you will be able to sync your repositories 
3. sync and enable repositories to be built.After enabling the repository you can configure some details like environment variables.
4. set the credentials for dockerhub.(settings --> add environment variables)
DOCKER_PASSWORD
DOCKER_USER
5. created we can trigger a build from travis or push a commit to the repo in order to trigger a build and to validate that everything works.
6. You can validate that everything went well by checking the commit SHA that triggered the build And on dockerhub The same SHA will be used to tag the image.


### Deploy application

We will review the vagrant & ansible files:

## vagrantfile
configuring Vagrantfile for being provisioned by ANSIBLE / Forwarding  port 8000

## playbook
Running this playbook will perform the following actions on your Ansible hosts:

1. Install aptitude, which is preferred by Ansible as an alternative to the apt package manager.
2. Install the required system packages.
3. Checking docker on latest version
4. Checking python
5. Checking docker-compose on latest version
6. Pull the default image specified by default_container_image from Docker Hub.
7. Create the number of containers defined by create_containers field, each using the image defined by 



## Deploy

1. create Vagrantfile
2. create ansible files (inventory,ansible.cfg,playbook.yml) under Deploy folder.
3. edit "default_container_image" in playbook file with relevant commit 
4. vagrant up



<!-- CONTACT -->
## Contact

Your Name - dror virt

Project Link: [https://github.com/your_username/repo_name](https://github.com/drorvt/drortask/)

