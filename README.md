# Deploy Static Website using Ansible

## Project Overview

This project demonstrates how to automate the deployment of a static website on an Ubuntu EC2 instance using Ansible.

Instead of manually installing Nginx, copying files, and restarting services, Ansible performs all these tasks through a single playbook.

---

## Technologies Used

- AWS EC2
- Ubuntu 22.04
- Ansible
- Nginx
- Linux
- SSH

---

## Architecture

Control Node
        │
        │ SSH
        ▼
Ubuntu EC2
        │
 Install Nginx
        │
 Copy index.html
        │
 Restart Nginx
        │
 Website Live

---

## Project Structure

```
Ansible-Nginx-Deployment/
│
├── README.md
├── inventory
├── server.yaml
├── index.html
```

---

## Prerequisites

- Ubuntu Control Node
- Ubuntu EC2 Instance
- SSH Key Pair
- Ansible Installed

---

## Steps

### Clone Repository

```bash
git clone https://github.com/yourusername/Web_Deployment_using_Ansible.git
```

### Run Playbook

```bash
ansible-playbook -i inventory deploy.yml
```

---

## Output

The playbook performs the following tasks:

- Installs Nginx
- Copies HTML file
- Restarts Nginx

Open:

```
http://<EC2-Public-IP>
```

---

## Learning Outcomes

- Configuration Management
- Infrastructure Automation
- Inventory File
- Playbooks
- YAML
- Ansible Modules
- Nginx Deployment

---

## Future Enhancements

- Deploy from GitHub Repository
- Jenkins Integration
- Docker Deployment
- CI/CD Pipeline

---

## Author

Jiya Pardeshi
**Fatebahadur Nandwanshi**

Cloud Application Developer
