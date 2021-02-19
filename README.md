## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
Images/Network-Topology.png

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

| Name                 | Function            | IP Address | Operating System |
|----------------------|---------------------|------------|------------------|
| Jump-Box-Provisioner | Gateway             | 10.0.1.4   | Linux            |
| Web-1                | Web Server          | 10.0.1.5   | Linux            |
| Web-2                | Web Server          | 10.0.1.6   | Linux            |
| Web-3                | Web Server          | 10.0.1.7   | Linux            |
| Elk                  | Elk stack Container | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Load Balancer (13.92.31.233) machine can accept connections from the Internet. Access to this machine is only allowed from the workstation (142.114.114.0/24).


Machines within the network can only be accessed by Jumpbox Provisioner (10.0.1.4).

A summary of the access policies in place can be found in the table below.

| Name                                 | Publicly Accessible | Allowed IP Addresses |
|--------------------------------------|---------------------|----------------------|
| Jump Box Provisioner 10.0.1.4:22     | no                  | Workstation          |
| Load Balancer 13.92.31.233:80        | no                  | Workstation          |
| Elk-VM 104.209.193.157:5601          | no                  | Workstation 
| Ansible Docker 10.0.1.4              | no                  | Jump Box 10.0.1.4    |
| DVWA Dockers 10.0.1.{5-7}            | no                  | Jump Box 10.0.1.4    |
| Elk-stack-container 10.1.0.4         | no                  | Jump Box 10.0.1.4    |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because consistent configuration is guaranteed.

The playbook implements the following tasks:
- Configure ELK server
- Maximize RAM usage
- Install docker containers
- download an ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images/docker-ps-Output.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.1.5,
10.0.1.6,
10.0.1.7

We have installed the following Beats on these machines:
filebeat
metricbeat

These Beats allow us to collect the following information from each machine:

filebeat: Collects data about the file system, helps generate and organize logfiles to send to logstash and elasticsearch it is an agent that takes unix syslogs and converts it for logstash to deliver to elastic search. 

metricbeat: collects machine metrics, from operating system and from services running on the server, to also send to logstash and elastic search. 

### Using the filebeat Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat_playbook.yml.txt file to /etc/ansible/roles
- Update the hosts file to include webserver IP addresses under a group called [webservers] (10.0.1.5, 10.0.1.6, 10.0.1.7)
- Update the hosts file to include ELK-VM's IP address under a group called [Elk] (10.1.0.4)
- Run the playbook, and navigate to http://104.209.193.157:5601/ to check that the installation worked as expected.

### Linux Command line

The following file contains the commands necessary to download and install the playbooks and update the configuration files:

Linux/Bash Script.txt

