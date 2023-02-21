# Ansible
This repository contains [Ansible](https://www.ansible.com/) playbooks and roles for certain configuration of the [Queercraft](https://www.queercraft.net/) server.   

You might also want to check out the [Terraform](https://www.terraform.io/) repository for the server, which can be found [here](
https://github.com/Queercraft/terraform_queercraft)

## Contents
Roles:
Role | Description
--- | ---
[nginx_config](roles/nginx_config) | Configures nginx to serve redirects and revere proxies to applications running on the server.
[ufw_config](roles/ufw_config) | Configures the firewall to allow access to Minecraft through TCPShield.

## Usage
To use these playbooks, you must have Ansible installed on your machine. You can install Ansible using your package manager, or by following the instructions on the [Ansible website](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).  

The `inventory/main` file contains the hostname of the server as configured in your `~/.ssh/config` file. Make sure you can connect to the server using the `ssh` command before running the playbooks.  

To run a playbook, use the following command: (`-K` prompts for the sudo password of the user)  
```bash
ansible-playbook -i inventory/main playbooks/main.yml -K
```

To limit the playbook to a specific role, use the `--tags` flag. For example, to run only the `nginx_config` role:  
```bash
ansible-playbook -i inventory/main playbooks/main.yml -K --tags nginx
```

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
