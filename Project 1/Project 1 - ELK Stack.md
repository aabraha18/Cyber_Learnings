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
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound requests to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_  
        - Load Balancers protect a system from potential attacks by evenly distributing web traffic across multiple servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- _TODO: What does Filebeat watch for?_ 
      - Filebeat collects data about the file system.
- _TODO: What does Metricbeat record?_ 
      - Metricbeat records machine metrics and statistics.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     |  Function  | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.4   | Linux            |
| Web 1    | Webserver  | 10.0.0.5   | Linux            |
| Web 2    | Webserver  | 10.0.0.6   | Linux            |
| ELK      | Elk-Server | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_ 
      -Workstation IP

Machines within the network can only be accessed by the workstation and internet.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_ 
          - Allowed the Jump box machine with the ansible container to have access to the ELK VM with IP address: 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | Workstation IP       |
| Web 1 & 2| No                  | 10.0.0.4             |
| ELK      | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_ 
      -The advantage of automating configuration with Ansible is the reduction of server errors, along with less time spent compared to a manual input.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

- Install docker.io
- Install python-pip
- Install docker

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](https://github.com/aabraha18/Cyber-Learnings/blob/d028601a5ac30bb0fe35152d5bb33a59f1839c0a/README/Images/docker_ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_ 
      -Web 1: 10.0.0.5, Web: 2 10.0.0.6

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_ 
      -Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._ 
      -Filebeat collects and organizes log files to send to Logstash and ElasticSearch. It monitors which files have changed and when. Metricbeat collects metrics and statistics. i.e., Collecting data, memory usage, etc.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file and metricbeat-config.yml file to the /etc/ansible/files/ directory.
- Update the filebeat-config.yml file and metricbeat-config.yml file to include the ELK IP 10.1.0.4 on ports 5601 and 9200.
- Run the playbook, and navigate to Kibana > Docker Metrics > Module status > Check data to check that the installation worked as expected.

- [Filebeat-config.yml](https://github.com/aabraha18/Cyber-Learnings/blob/c38061595dee4ad2cf9e9d2f4da8d3e296b9ff5d/Ansible/filebeat-config.yml)
- [Metricbeat-config.yml](https://github.com/aabraha18/Cyber-Learnings/blob/c38061595dee4ad2cf9e9d2f4da8d3e296b9ff5d/Ansible/metricbeat-config.yml) 

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ The Elk-playbook.yml file is the playbook located in the /etc/ansible/ directory. 
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ You must update the /etc/ansible/hosts/ file with the IP's of the webservers and ELK servers. You specify which machine to install ELK by updating the ansible hosts file with the ELK IP address and python script. Where as with Filebeat, you must update the filebeat-config.yml file to work with the ELK server. 
- _Which URL do you navigate to in order to check that the ELK server is running? http://20.114.172.54:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

Commands to run the playbook:
  - ansible-playbook.yml elk-playbook.yml
  - ansible-playbook.yml filebeat-playbook.yml
  - ansible-playbook.yml metricbeat-playbook.yml
