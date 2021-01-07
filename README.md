<<<<<<< HEAD
=======
# Project-ELK-stack
Introduction to Cloud security
>>>>>>> 928d16a83e29187eb3cc9abffd99fd25f6b6f2b2
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible directory may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log data and system metrics and statistics.

The configuration details of each machine may be found below.

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.1   | Linux            |
| Web-1    | Web Server | 10.0.1.5   | Linux            |
| Web-2    | Web Server | 10.0.1.6   | Linux            |
| Web-3    | Web Server | 10.0.1.7   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Network Security Group machine can accept connections from the Internet. Access to this machine is only allowed from the "workstation".


Machines within the network can only be accessed by Jumpbox Provisioner 52.255.158.253

A summary of the access policies in place can be found in the table below.

| Name            | Publicly Accessible | Allowed IP Addresses    |
|-----------------|---------------------|-------------------------|
| Jump Box        | no                  |workstation IP           |
| virtual Network | no                  |Jumpbox 52.255.158.253   |
| Web-1,2, and 3  | no                  |workstation IP           |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because consistent configurations is guaranteed.

The playbook implements the following tasks:
- Configure ELK server
- Maximize RAM usage
- Install docker containers
- download an ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.1.5
10.0.1.6
10.0.1.7

We have installed the following Beats on these machines:
filebeat

### Using the filebeat Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat_playbook.yml.txt file to /etc/ansible/roles
- Update the ansible config file to include webserver IP addresses under a group called [webservers] (10.0.1.5, 10.0.1.6, 10.0.1.7)
- Run the playbook, and navigate to http://104.209.193.157:5601/ to check that the installation worked as expected.

