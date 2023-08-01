# Explanation for "App containerisation with Ansible" Playbook
This Ansible playbook aims to containerize an application using Docker and Docker Compose. It runs a series of tasks on the localhost host to set up the necessary environment for running the application in containers. The playbook assumes that Docker and Docker Compose are already installed on the target host.

## Playbook Structure
The playbook consists of one play named "App containerisation with Ansible." It runs on the localhost host and utilizes the become directive to execute tasks with elevated privileges using sudo.

#Tasks:

## Check SSH connectivity and ping:
 This task is a basic connectivity check to ensure that the localhost is accessible and responsive.

## Install python3 version: 
The apt module is used to install Python 3 on the localhost.

## Install Docker: 
The raw module executes a shell command to install Docker on the target host using the get.docker.com script.

## Assign Docker to privileges: 
The raw module adds the current user to the docker group to allow running Docker commands without sudo.

## Start Docker: 
The raw module starts the Docker daemon using systemctl.

## Install Git: 
The apt module installs Git on the localhost.

## Create directory: 
The file module creates a directory at /yolo on the localhost with the appropriate permissions (mode 0755).

## Clone the Git repository: 
The git module clones the Git repository from https://github.com/Emaina98/yolo.git and places it in the /yolo directory.

## Build Docker Image for Client: 
The docker_image module builds a Docker image for the client application using the Dockerfile located in /yolo/client directory. The built image is tagged as Emaina98/client:v1.

## Build Docker Image for Backend: 
The docker_image module builds a Docker image for the backend application using the Dockerfile located in /yolo/backend directory. The built image is tagged as Emaina98/backend:v1.

## Install Docker Compose: 
The raw module downloads and installs Docker Compose binary into /usr/local/bin from the specified URL.

## Start Docker Compose services: 
The command module runs the docker-compose up command to start the services defined in the docker-compose.yml file located in the /yolo directory.