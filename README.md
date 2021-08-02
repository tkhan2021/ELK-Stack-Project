# Automated ELK Stack Development Project

Tanveer Khan 04/03/2021

This repository's files were used to set up the network shown below.

The final setup was 4 servers running vulnerable DVWA containers along with a JumpBox Provisioner and a server running an ELK Stack container.

## Network Topology

![image](https://user-images.githubusercontent.com/74847116/127726650-730e7627-7b1e-4340-b4b7-44b6b8a1a9ea.png)

These files have been thoroughly tested and are now being used to set up an ELK deployment on Azure. They can be used to re-create the entire deployment seen above. Only some elements of the playbook (.yml) file, such as Filebeat, can be installed.

The following ansible-playbooks are needed to create and install DVWA and the ELK-server:

- my-playbook.yml
- elk-playbook.yml
- filebeat.playbook.yml

### Please use the .yml links above to view playbook codes.

## This document contains the following details:

- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

## Description of the Topology

The purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the system is highly available while also restricting network access to select IP addresses. Load Balancing ensures the web-servers' availability, which is an important part of security in the CIA Triad.

What is the advantage of a jump box? 

Using a JumpBox Provisioner has the advantage of providing a single point of entry for administrative functions. As a result, the JumpBox Provisioner becomes a Secure Administrative Workstation (SAW). Administrators must first access the JumpBox Provisioner before proceeding to other servers to perform administrative operations.

Users can quickly monitor the susceptible VMs for changes to the logs and system traffic by integrating an ELK server.

- Filebeat watches for log files/locations and collects log events. (Filebeat: Lightweight Log Analysis & Elasticsearch)
- Metricbeat records metrics and statistical data from the operating system and from services running on the server. (Metricbeat: Lightweight Shipper for Metrics)

The configuration details of each machine may be found below:

| Name | Function | IP Address | Operating System |
| --- | --- | --- | --- |
| Jumpbox Provisioner | Gateway | 10.1.0.7 | Linux (Ubuntu 18.04 LTS |
| Web-1 | Web Server - Docker - DVWA | 10.1.0.5 | Linux (Ubuntu 18.04 LTS |
| Web-2 | Web Server - Docker - DVWA | 10.1.0.6 | Linux (Ubuntu 18.04 LTS |
| ELK Server | ELK Stack | 10.1.0.4 | Linux (Ubuntu 18.04 LTS |

## Access Policies

The machines on the internal network are not exposed to the Public Internet.

Only the Jump Box Provisioner machine can accept connections from the Public Internet. Access to this machine is only allowed from the following IP addresses:

- Personal IP Address

Machines within the network can only be accessed by SSH.

- The ELK-Server is only accessible by SSH from the JumpBox Provisioner and via web access from the Personal IP Address.

A summary of the access policies in place can be found in the table below.

| Name	| Publicly Accessible |	Allowed IP Address |
| --- | --- | --- |
| Jump-Box |	No	| Personal IP Address |
| Web-1	| Yes - Load Balancer	13.66.204.159 | Public IP 10.0.0.4 - JumpBox |
| Web-2 |	Yes - Load Balancer	13.66.204.159 | Public IP 10.0.0.4 JumpBox |
| ELK-Server |	No |	SSH 10.0.0.4 - JumpBox HTTP Port 5601 Personal IP |

## Elk Configuration

Ansible was used to automate the ELK machine's configuration. There was no manual configuration, which is advantageous because...

- The benefit of automating the installation procedure is that we can rapidly and easily deploy several servers without having to manually configure each one.

The playbook implements the following tasks:

1. Install Docker.io and pip3
2. Increases VM memory
3. Download and Configure elk docker container
4. Sets Published Ports

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

![docker-ps](https://user-images.githubusercontent.com/74847116/127727841-acccfd8a-2995-46ae-9236-05bc7078788b.png)

## Target Machines & Beats

This ELK server is configured to monitor the following machines:

- Web-1 10.1.5
- Web-2 10.1.6

We have installed the following *Beat on these machines:

- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:

- Filebeat watches for log files/locations and collect log events. (Filebeat: Lightweight Log Analysis & Elasticsearch)
- Metricbeat records metrics and statistical data from the operating system and from services running on the server (Metricbeat: Lightweight Shipper for Metrics)

## Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

- Copy the filebeat-config.yml and metricbeat-config.yml file to /etc/ansible/files.
- Update the configuration files to include the Private IP of the ELK-Server to the ElasticSearch and Kibana Sections of the Configuration File.
- Run the playbook, and navigate to ELK-Server-PublicIP:5601/app/kibana to check that the installation worked as expected.

Which file is the playbook? There were 3 playbook files used in this project:

- my-playbook.yml
- elk-playbook.yml
- filebeat-playbook.yml

Where do you copy it?

/etc/ansible/

Which file do you update to make Ansible run the playbook on a specific machine?

/etc/ansible/hosts.cfg

How do you specify which machine to install the ELK server on versus which to install Filebeat on?

/etc/ansible/hosts - you configure where each machine should be installed whether it is ELK Server or FileBeat

Which URL do you navigate to in order to check that the ELK server is running?

http://publicip(elkserver):5601

## Commands needed to run the Anisble Configuration for the Elk-Server are:

1. ssh RedAdmin@JumpBox (your private IP)
2. sudo docker container list -a - Locates the ansible container
3. sudo docker start (unique_name)
4. sudo docker attach (unique_name)
5. cd /etc/ansible
6. ansible-playbook elk-playbook.yml (Installs and Configures ELK-Server)
7. cd /etc/ansible/
8. ansible-playbook beats-playbook.yml (Installs and Configures FileBeat)
9. Open a new browser on any of your web browser platform, navigate to (ELK-Server-PublicIP:5601/app/kibana) - This will bring up the Kibana Web Portal
