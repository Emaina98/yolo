# Explanation for the "App containerisation with Ansible" Playbook
The provided Ansible playbook aims to containerize an application using Docker and run it on multiple hosts. It includes tasks to install prerequisites, Docker, Git, and then proceeds to clone a Git repository containing the containerized application. Finally, it starts Docker Compose services to run the application inside Docker containers.

## Playbook Structure
name: App containerisation with ansible
hosts: all
gather_facts: no
become: yes
Tasks
## Install Prerequisites:
## apt
The apt module installs necessary packages, including apt-transport-https, ca-certificates, curl, and gnupg.
The state: latest ensures that the packages are updated to their latest versions.
The task is tagged with os-prerequisite.
Install Docker:
## raw
The raw module runs the command to install Docker using the official installation script obtained from https://get.docker.com/.
The installation script downloads and installs Docker on the target hosts.
Assign Docker to Privileges:

The raw module adds the current user ($(whoami)) to the 'docker' group to allow Docker commands without sudo.
## Start Docker:

The raw module starts the Docker service on the target hosts using sudo systemctl start docker.
Install Git:
## install git
The apt module installs Git on the target hosts, making it ready for repository cloning.
Clone the Git Repository:
## Clone the Repository
The raw module clones a Git repository containing the containerized application from https://github.com/Emaina98/yolo.git.
The repository will be cloned into the /home/vagrant/yolo directory on the target hosts.
Start Docker Compose services:
## Docder compose
The command module executes the docker compose up -d command to start the Docker Compose services.
The become: yes ensures running the command with elevated privileges.
The args specify the working directory for the docker compose command, which is /home/vagrant/yolo.
The task is tagged with docker-compose.