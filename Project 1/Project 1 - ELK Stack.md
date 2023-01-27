# Cyber-Learnings

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](https://github.com/aabraha18/Cyber_Learnings/blob/03bd33eed159cae4fb4e6654bd940be2c98c1bf5/Diagrams/Cloud%20Security.png) 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

- [Ansible.cfg](https://github.com/aabraha18/Cyber-Learnings/blob/c38061595dee4ad2cf9e9d2f4da8d3e296b9ff5d/Ansible/ansible.cfg)
- [ELK-playbook.yml](https://github.com/aabraha18/Cyber-Learnings/blob/50efadadd7844007f716a3484b8e72171bbb7315/Ansible/elk-playbook.yml)
- [Filebeat-playbook.yml](https://github.com/aabraha18/Cyber-Learnings/blob/c38061595dee4ad2cf9e9d2f4da8d3e296b9ff5d/Ansible/file-beat.yml)
- [Metricbeat-playbook.yml](https://github.com/aabraha18/Cyber-Learnings/blob/c38061595dee4ad2cf9e9d2f4da8d3e296b9ff5d/Ansible/metricbeat-config.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application. 

Load balancing ensures that the application will be highly available, in addition to restricting inbound requests to the network. Load balancers also protect a system from potential attacks by evenly distributing web traffic across multiple servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
  - Filebeat collects data about the file system.
  - Metricbeat records machine metrics and statistics.

The configuration details of each machine may be found below.

| Name     |  Function  | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.4   | Linux            |
| Web 1    | Webserver  | 10.0.0.5   | Linux            |
| Web 2    | Webserver  | 10.0.0.6   | Linux            |
| ELK      | Elk-Server | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the Workstation IP.

Machines within the network can only be accessed by the workstation and internet. Allowing the Jump box machine with the ansible container to have access to the ELK VM with IP address: 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | Workstation IP       |
| Web 1 & 2| No                  | 10.0.0.4             |
| ELK      | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because automated configuration with Ansible reduces server errors, along with time less spent compared to manual input.

The playbook implements the following tasks:
- Install docker.io
- Install python-pip
- Install docker

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](https://github.com/aabraha18/Cyber-Learnings/blob/d028601a5ac30bb0fe35152d5bb33a59f1839c0a/README/Images/docker_ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web 1: 10.0.0.5
- Web 2: 10.0.0.6

The following Beats have been installed on these machines:
- Filebeat
- Metricbeat

Filebeat collects and organizes log files to send to Logstash and ElasticSearch, monitoring which files changed and when. Metricbeat collects metrics and statistics. (i.e., collecting data, memory usage, etc.)

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file and metricbeat-config.yml file to the /etc/ansible/files/ directory.
- Update the filebeat-config.yml file and metricbeat-config.yml file to include the ELK IP 10.1.0.4 on ports 5601 and 9200.
- Run the playbook, and navigate to Kibana > Docker Metrics > Module status > Check data to ensure that the installation worked as expected.

- [Filebeat-config.yml](https://github.com/aabraha18/Cyber-Learnings/blob/c38061595dee4ad2cf9e9d2f4da8d3e296b9ff5d/Ansible/filebeat-config.yml)
- [Metricbeat-config.yml](https://github.com/aabraha18/Cyber-Learnings/blob/c38061595dee4ad2cf9e9d2f4da8d3e296b9ff5d/Ansible/metricbeat-config.yml) 


The Elk-playbook.yml file is the playbook located in the /etc/ansible/ directory. You must update the /etc/ansible/hosts/ file with the IP's of the webservers and ELK servers. You specify which machine to install ELK by updating the ansible hosts file with the ELK IP address and python script. Where as with Filebeat, you must update the filebeat-config.yml file to work with the ELK server. Then navigate to http://20.114.172.54:5601/app/kibana to ensure the ELK server is running.


Commands to run the playbook:

- [Ansible.cfg](https://github.com/aabraha18/Cyber-Learnings/blob/c38061595dee4ad2cf9e9d2f4da8d3e296b9ff5d/Ansible/ansible.cfg)
- [ELK-playbook.yml](https://github.com/aabraha18/Cyber-Learnings/blob/50efadadd7844007f716a3484b8e72171bbb7315/Ansible/elk-playbook.yml)
- [Filebeat-playbook.yml](https://github.com/aabraha18/Cyber-Learnings/blob/c38061595dee4ad2cf9e9d2f4da8d3e296b9ff5d/Ansible/file-beat.yml)
- [Metricbeat-playbook.yml](https://github.com/aabraha18/Cyber-Learnings/blob/c38061595dee4ad2cf9e9d2f4da8d3e296b9ff5d/Ansible/metricbeat-config.yml)

