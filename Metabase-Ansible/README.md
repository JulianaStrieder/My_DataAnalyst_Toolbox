# Install Metabase on Ubuntu as a service with Nginx

This project aims to facilitate the installation of Metabase as a service on Ubuntu with Ansible. The server is an EC2 instance on AWS, and the database hosting the data is MySQL Server.

## Motivation

Recently I have been learning a little bit about Infrastructure as Code (IaC), and I found out how cool it is. Thus, I decided to join IaC with data analysis whenever I see fit, bringing a little bit of IaC ideas to data analysis.

## Installation

You need to have Ansible installed in your machine. The following commands work on Ubuntu:

> sudo apt update\
> sudo apt install software-properties-common\
> sudo apt-add-repository --yes --update ppa:ansible/ansible\
> sudo apt install ansible

## How to use

This code is meant to install a Metabase application using Ansible.

You need a running EC2 instance on AWS and the key pair to be able to access it via SSH.

Then you have to git clone this repo to your machine and change the following variables:

1. Add the IP address of your EC2 instance in these files:
- group_vars directory: all.yml:
    > nginx:\
        > ip_myhost: your ip will be here

- inventory: hosts.yml:
    > all:\
    > hosts:\
    > metabase:\
    > ansible_connection: ssh\
    > ansible_host: PASTE_YOUR_IP_HERE

2. Set the path to your key pair file:
- inventory: hosts.yml:
    > all:\
    > hosts:\
    > metabase:\
    > ansible_connection: ssh\
    > ansible_host: PASTE_YOUR_IP_HERE\
    > ansible_port: 22\
    > ansible_user: ubuntu\
    > ansible_ssh_private_key_file: /PATH_TO_YOUR_KEYPAIR_PEM_FILE/YOUR_KP_FILE.pem

3. Add your database information:
- group_vars: all.yml:
    > metabase:\
    >  metabase_version: v0.34.3\
    >  db_type: mysql\
    >  db_dbname: YOUR_DATABASE_NAME\
    >  db_port: 3306\
    >  db_user: YOUR_USER\
    >  db_password: YOUR_PASSWORD\
    >  db_host: YOUR_DB_ENDPOINT

4. Run the command below in the directory where you have cloned the repo:

> ansible-playbook playbook.yml

5. After Ansible finishes the configuration, you can access Metabase through its web interface:

> http://YOUR_IP_HERE

# TO DO

Implement this solution with Docker.


# References

[Ansible documentation](https://docs.ansible.com/ansible/latest/index.html)

[Metabase documentation](https://www.metabase.com/docs/latest/operations-guide/running-metabase-on-debian.html)

[Nginx documentation](https://nginx.org/en/docs/)


# Hat tip

To [Gabriel Xavier](https://github.com/gabxav) who is responsible for me to make acquaintance with Ansible, teach me what he knows about it, and kindly reviewed this code.



