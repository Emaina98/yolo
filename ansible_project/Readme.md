# YOLO Ecommerce containerization

This repository contains an Ansible playbook to set up a YOLO Ecommerce environment on the target `my_vm` virtual machine. The playbook performs the following tasks:

1.  Checks SSH connectivity and performs a ping test.
2.  Installs Python3.
3.  Installs Docker using the `get.docker.com` script.
4.  Assigns Docker privileges to the current user.
5.  Starts the Docker service.
6.  Installs Git.
7.  Creates a directory `/yolo`.
8.  Clones the YOLO repository from `https://github.com/Emaina98/yolo.git` to the `/yolo` directory.
9.  Builds Docker images for the client and backend with the tag `v1
10.  Installs Docker Compose.
11.  Starts the Docker Compose services for YOLO Ecommerce.

## Requirements

Before running the playbook, ensure the following:

1.  The target machine (`localhost') has SSH connectivity and the Ansible control machine can access it.
2.  The target machine should have internet access to install packages and fetch Docker images.
3.  The user executing the playbook has sudo privileges.

## Usage

1.  Clone this repository to your local machine.

bashCopy code

`git clone https://github.com/Emaina98/yolo.git
cd yolo

2.Run the Ansible playbook:
Navigate to yolo then to ansible_project

<cd yolo>
<cd ansible_project>
    

bashCopy code

`ansible-playbook yolo.yml` 

The playbook will execute all the tasks, setting up the YOLO Ecommerce environment on the target machine.

