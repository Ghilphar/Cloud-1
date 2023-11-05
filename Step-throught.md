# GG WP EZ

1. **Setting up the AWS EC2 Instance:**
- Launch a EC2 instance, select t2.micro
- In the "Configure Security Group", allow port 22 (SSH) and port 80 (HTTP).
- Download and securely store the PEM key file wich will allow you to SSH into the instance.

### To SSH into your EC2 instance:
```bash
chmod 400 /path/to/your-key.pem
ssh -i /path/to/your-key.pem ubuntu@<Your-EC2-IP>
```

2. **Installing Docker and Docker-Compose:**
In the EC2 instance run:
```bash
# Update repositories
sudo apt-get update

# Install Docker
sudo apt-get install docker.io -y

# Start Docker and enable at boot
sudo systemctl start docker
sudo systemctl enable docker

# Install Docker Compose
sudo apt-get install docker-compose -y
```

3. **Setting up WordPress, PHPMyAdmin, and MySQL using Docker-Compose:**

Create a docker-compose.yml (look src)

and run it:
```bash
docker-compose up -d
```

This will pull the necessary images and start the containers.

4. **Automating Deployment with Ansible:**
