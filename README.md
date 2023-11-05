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

2. **Instance Configuration**
    - For instance type, select t2.micro for a free tier or a larger size based on your preference.
    - Proceed with default configurations until you reach the "Configure Security Group" section.
    - Setup security groups to allow SSH (port 22) and HTTP (port 80). These will be adjusted later.

3. **Access Key**
    - Review and launch the instance.
    - You'll be prompted to select a key pair. If you have one, use it, otherwise create a new one. Download and store it securely.

4. **Access Your EC2 Instance**
    - Use the following command to access the instance:
    ```bash
    chmod 400 /path/to/your-key.pem
    ssh -i /path/to/your-key.pem ubuntu@<Your-EC2-IP>
    ```

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
    docker-compose up -d
    ```

## Automating Deployment with Ansible

1. **Install Ansible on Your Local Machine** 
    Follow the [official  documentation](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

2. **Set Up Ansible Inventory and Playbook** 
    - Create hosts.ini for inventory.
        ```bash
        [webserver]
        <Your-EC2-IP> ansible_ssh_user=ubuntu ansible_ssh_private_key_file=/path/to/your-key.pem
        ```

    - Create deploy.yml for playbook.
    with the content provided in the previous response.

3. **Run Ansible Playbook** 

    ```
    ansible-playbook -i hosts.ini deploy.yml
    ```

## Securing the Server

1. **Adjust AWS Security Group** 
    - Allow SSH, HTTP, and HTTPS.
    - Deny other ports.

2. **Secure MySQL** 
    - Do not expose MySQL port externally.

3. **Implement TLS with Certbot** 

## URL Redirection

1. **Install NGINX** 
    ```bash
    sudo apt install nginx -y
    ```

2. **Set Up Reverse Proxy with NGINX**
