# Ecommerce website Containerization with Ansible

This Ansible playbook automates the process of setting up Docker and running a containerized application on the target hosts. It installs the necessary prerequisites, Docker, and Git, and then clones a Git repository containing the containerized application. Finally, it starts the Docker Compose services to run the application.

## Prerequisites

Before running the playbook, ensure you have the following:

- Ansible installed on your control machine.
- SSH access to the target hosts with the necessary privileges.
- Targets have access to the internet to install Docker and Git.

## Usage

1. Clone the Ansible playbook repository to your local machine:

   <git clone https://github.com/Emaina98/yolo.git>
   <cd yolo>
   Update the hosts file with the target hosts' information where you want to set up the application.

## Run the Ansible playbook:

<ansible-playbook -i hosts playbook.yml>

The playbook will install Docker, Git, clone the Git repository with the containerized application, and start the Docker Compose services.

## Playbook Structure
The playbook is structured as follows:

Install Prerequisites: Installs required packages to set up Docker and Git.
Install Docker: Fetches and installs Docker using the official script.
Assign Docker to Privileges: Adds the current user to the 'docker' group to avoid using 'sudo' for Docker commands.
Start Docker: Starts the Docker service on the target host.
Install Git: Installs Git to clone the application repository.
Clone the Git Repository: Clones the Git repository containing the containerized application.
Start Docker Compose Services: Starts the Docker Compose services to run the application.
