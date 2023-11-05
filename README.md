# WordPress Deployment on AWS EC2 using Docker

This guide will walk you through deploying WordPress on an AWS EC2 instance using Docker and automating the process with Ansible.

## Table of Contents


- [Setting up the AWS EC2 Instance](#setting-up-the-aws-ec2-instance)
- [Setting up Docker and Docker-Compose](#setting-up-docker-and-docker-compose)
- [Preparing for Deployment with Docker-Compose](#preparing-for-deployment-with-docker-compose)
- [Automating Deployment with Ansible](#automating-deployment-with-ansible)
- [Securing the Server](#securing-the-server)
- [URL Redirection](#url-redirection)
- [Making the Server Robust](#making-the-server-robust)
- [Additional Security Measures](#additional-security-measures)
- [Database Configuration](#database-configuration)
- [SSL Configuration](#ssl-configuration)
- [Scaling and High Availability](#scaling-and-high-availability)
- [Testing](#testing)
- [Maintenance and Monitoring](#maintenance-and-monitoring)

## Setting up the AWS EC2 Instance

1. **Login & Launch Instance**
    - Open AWS Management Console and navigate to EC2.
    - Click on "Launch Instance".
    - Choose "Ubuntu Server 20.04 LTS" from the AMIs list.

## Setting up Docker and Docker-Compose


1. **Update and Install Docker on EC2 Instance**
   ```bash
   sudo apt update
   sudo apt install docker.io -y
   sudo systemctl start docker
   sudo systemctl enable docker
   ```

2. **Install Docker Compose**
   ```bash
   sudo apt install docker-compose -y
   ```

## Preparing for Deployment with Docker-Compose

1. **Set Up Directory Structure** 
    ```bash
    mkdir ~/wordpress-deployment
    cd ~/wordpress-deployment
    ```

2. **Create docker-compose.yml File** 

    ```bash
    vim docker-compose.yml
    ```

3. **Start the Services** 

    ```
    docker-compose up -
    ```

## Automating Deployment with Ansible

1. **Install Ansible on Your Local Machine** 
    Follow the [official  documentation](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

2. **Set Up Ansible Inventory and Playbook** 
    - Create hosts.ini for inventory.
    - Create deploy.yml for playbook.

3. **Run Ansible Playbook** 

    ```
    ansible-playbook -i hosts.ini deploy.yml
    ```