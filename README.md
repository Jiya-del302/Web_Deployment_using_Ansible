# 🚀 Web Deployment Using Ansible

Automated web server provisioning and website deployment using **Ansible**. This project demonstrates how to configure multiple remote Ubuntu servers, install Nginx, deploy a static portfolio website, and manage the entire infrastructure through Ansible Playbooks.

---

## 📌 Project Overview

This project automates the deployment of a static portfolio website across multiple AWS EC2 instances using **Ansible**.

Instead of manually installing Nginx and copying website files to each server, Ansible performs the complete deployment in a single command, making the process faster, consistent, and scalable.

---

## 🛠️ Tech Stack

- Ansible
- AWS EC2 (Ubuntu)
- Linux
- Nginx
- SSH
- HTML
- YAML

---

## 📂 Project Structure

```
Web-Deployment-Using-Ansible/
│
├── inventory
├── server.yaml
└── README.md
```

---

## ⚙️ Prerequisites

Before running this project, ensure you have:

- Ubuntu/Linux machine
- Ansible installed
- AWS EC2 Ubuntu instances
- SSH private key (.pem)
- Internet connectivity
- Security Group allowing:
  - SSH (22)
  - HTTP (80)
- Create a key pair using ssh-keygen 
---

## 🏗️ Infrastructure

### Control Node

- Ubuntu EC2 Instance
- Ansible Installed

### Managed Nodes

- Ubuntu EC2 Instance 1
- Ubuntu EC2 Instance 2

---

## 📄 Inventory File

The inventory file defines the managed nodes.

```ini
[nodes]

ansible_node1 ansible_host=<Public-IP-1>
ansible_node2 ansible_host=<Public-IP-2>

ansible_node1 ansible_user=ubuntu
ansible_node2 ansible_user=ubuntu

[all:vars]
ansible_ssh_private_key_file=/home/ubuntu/private_key
```

---

## 📄 Ansible Playbook

The playbook performs the following tasks:

- Connects to all managed nodes
- Installs Nginx
- Copies the portfolio website
- Restarts the Nginx service

```yaml
---
- name: Deploying website
  hosts: nodes
  become: yes

  tasks:
    - name: Install Nginx Server
      apt:
        name: nginx
        state: present

    - name: Copy File
      copy:
        src: index.html
        dest: /var/www/html/index.html

    - name: Restart Nginx
      service:
        name: nginx
        state: restarted
```

---

## 🚀 Deployment Steps

### 1. Clone the Repository

```bash
git clone <repository-url>
cd Web-Deployment-Using-Ansible
```

---

### 2. Verify Connectivity

```bash
ansible -i inventory nodes -m ping
```

Expected Output:

```
SUCCESS
```

---

### 3. Run the Playbook

```bash
ansible-playbook -i inventory server.yaml
```

---

### 4. Access the Website

Open the public IP of any managed node in your browser.

Example:

```
http://<EC2-Public-IP>
```

Your portfolio website will be displayed.

---

## 📌 Ansible Modules Used

| Module | Purpose |
|----------|----------|
| apt | Installs Nginx package |
| copy | Copies index.html to the web server |
| service | Restarts the Nginx service |

---

## 📸 Workflow

```
               GitHub Repository
                      │
                      │
                      ▼
            Ansible Control Node
                      │
          SSH Connection (Port 22)
        ┌─────────────┴─────────────┐
        ▼                           ▼
 Ubuntu EC2 Node 1             Ubuntu EC2 Node 2
        │                           │
 Install Nginx                 Install Nginx
        │                           │
 Copy index.html              Copy index.html
        │                           │
 Restart Nginx                Restart Nginx
        └─────────────┬─────────────┘
                      ▼
            Portfolio Website Live
```

---

## 📚 Key Features

- Infrastructure automation using Ansible
- Agentless configuration management
- Multi-node deployment
- Automated Nginx installation
- Static website deployment
- Simple and reusable playbook
- SSH-based remote management

---

## 🎯 Learning Outcomes

Through this project, I gained hands-on experience with:

- Ansible Inventory
- Playbook creation
- YAML syntax
- Configuration Management
- SSH-based automation
- Managing multiple servers simultaneously
- Nginx web server deployment
- Infrastructure as Code (IaC) concepts

---

## 🔮 Future Enhancements

- Use Ansible Roles
- Add Ansible Galaxy roles
- Deploy dynamic web applications
- Configure HTTPS using Let's Encrypt
- Automate deployments with Jenkins
- Use Ansible Vault for secure secret management
- Integrate with GitHub Actions
- Deploy on larger server clusters

---

## 👩‍💻 Author

**Jiya Pardeshi**

Aspiring Cloud & DevOps Engineer

### Connect with Me

- LinkedIn: https://www.linkedin.com/in/jiya-pardeshi-8b2b6040b

---

## ⭐ If you found this project useful, don't forget to star the repository!
