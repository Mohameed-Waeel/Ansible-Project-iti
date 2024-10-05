# Ansible-Project-iti
This project demonstrates the use of Ansible to automate the deployment and configuration of NGINX web servers across multiple machines hosted in a VMware environment. The playbook ensures a consistent setup across all machines, streamlining the installation, configuration, and management of web servers.

## Deployment Steps
![Deployment Steps](https://github.com/user-attachments/assets/15609b28-3c16-4775-b49c-f5bcf185e381)

### Key Features
- Automated installation of NGINX using Ansible roles.
- Configuration of the NGINX server block through a Jinja2 template, allowing flexible and customizable setups.
- Ensures NGINX is started and enabled to run on boot.
- Manages firewalls to allow HTTP traffic, ensuring access to the web server.

---

## Table of Contents
1. [Prerequisites](#prerequisites)
2. [Installation](#installation)
3. [Directory Structure](#directory-structure)
4. [Configuration](#configuration)
5. [Running the Project](#running-the-project)
6. [Testing and Verification](#testing-and-verification)
7. [Troubleshooting](#troubleshooting)

---

## Prerequisites

Before running this project, ensure you have the following installed:
- **Ansible**: Version 2.9 or later.
- **Python**: Ensure Python is installed on your control node.
- **VMware**: A working VMware environment with machines ready for deployment.
- **SSH Access**: Ensure you have SSH access to the target machines.

---

## Installation

1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/Mohameed-Waeel/ansible_nginx_deployment.git
   cd ansible_nginx_deployment
   ```

2. Install required Ansible packages (if needed):
   ```bash
   sudo apt-get update
   sudo apt-get install ansible
   ```

---

## Directory Structure

The project is organized as follows:

```
ansible_nginx_deployment/
├── ansible.cfg              # Ansible configuration file
├── inventory/               # Inventory files (hosts)
│   └── hosts.yml
├── group_vars/              # Group-wide variables
│   └── all.yml
├── roles/                   # Roles for different configurations
│   ├── common/              # Common configurations
│   │   └── tasks/main.yml
│   └── web/                 # Web server role
│       ├── tasks/main.yml
│       ├── handlers/main.yml
│       └── templates/nginx.conf.j2
└── playbooks/               # Playbook to run
    └── site.yml
```

---

## Configuration

### ansible.cfg
This file defines the Ansible behavior, including inventory location and privilege escalation settings.

### Inventory
The inventory file (`inventory/hosts.yml`) lists the target machines where NGINX will be installed. Update the IP addresses as needed.

### Group Variables
The `group_vars/all.yml` file contains variables shared across all machines. You can customize these variables, such as the NGINX port.

### Roles
- **Common Role**: Contains tasks that apply to all machines, like installing basic utilities.
- **Web Role**: Manages the installation and configuration of NGINX.

---

## Running the Project

1. **Test SSH Connection**: Ensure you can connect to the target machines using Ansible:
   ```bash
   ansible -m ping all
   ```

2. **Run the Playbook**: Deploy NGINX by executing the following command:
   ```bash
   ansible-playbook playbooks/site.yml 
   ```

3. **Monitor the Output**: Watch for any errors during the playbook execution to ensure successful installation.

---

## Testing and Verification

After running the playbook:

1. Access the NGINX web server in a web browser or use `curl`:
   ```bash
   curl http://<machine_ip>
   ```

2. Check the status of NGINX on the target machine:
   ```bash
   sudo systemctl status nginx
   ```

3. Verify that NGINX is running and listening on the correct port (default is 80):
   ```bash
   sudo netstat -tuln | grep :80
   ```

---

## Troubleshooting

- If you encounter connection issues, check if NGINX is running and listening on port 80.
- Verify that the firewall is not blocking HTTP traffic.
- Confirm that the correct IP addresses are set in the inventory file.
- Use the verbose flag for more detailed output during playbook execution:
   ```bash
   ansible-playbook playbooks/site.yml -vvv
   ```

## Pictures from the project

## 1
![1](https://github.com/user-attachments/assets/08a9ddd8-3864-438b-9cf8-cfb22553d9c2)

## 2
![2](https://github.com/user-attachments/assets/764bbc86-1af7-40a3-b3fa-8c00e21a9f05)

## 3
![3](https://github.com/user-attachments/assets/bc0dc372-192a-4bc4-bf29-34c539b51f00)

## 4
![4](https://github.com/user-attachments/assets/81358c0d-c8a1-43c3-8548-637514af628b)

## 5
![5](https://github.com/user-attachments/assets/3595c7c1-f0f8-46f0-8e2c-67948ca405f3)

## 6
![6](https://github.com/user-attachments/assets/3905a627-02c9-4d94-b160-62a1106c4a7f)

## 7
![7](https://github.com/user-attachments/assets/561212be-752d-4385-ac39-3ea48b20e0d2)

## 8
![8](https://github.com/user-attachments/assets/7126b27e-ec61-4cd3-b5b4-1d104d0ef8fe)

## 9
![9](https://github.com/user-attachments/assets/a6e4ef9b-53aa-4be9-a180-642589c262ce)

## 10
![10](https://github.com/user-attachments/assets/66a4d469-5ca3-400d-9b46-ad59df6a57d7)

