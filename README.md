# Project-1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Google Drive/Diagram

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics and statistics.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.5   | Linux            |
| Web-1    | Server   | 10.0.0.6   | Linux            |
| Web-2    | Server   | 10.0.0.7   | Linux            |
| ElkServer| Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 72.208.203.2

Machines within the network can only be accessed by Jumpbox with the IP address 20.64.240.24

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses      |
|----------|---------------------|---------------------------|
| Jump Box | Yes                 | 72.208.203.2              |
| Web-1    | No                  | 72.208.203.2 20.64.410.24 |
| web-2    | No                  | 72.208.203.2 20.64.410.24 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it reduces time spent on configuration to create more time for other tasks.

The playbook implements the following tasks:
- Installs Docker
- Allows more memory to be used to enable use of elk
- Downloads and luanches the docker web container\
- Enables docker service on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Pictures/elk install.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.6
- 10.0.0.7

We have installed the following Beats on these machines:
- filebeat
- metricbeat

These Beats allow us to collect the following information from each machine:
-Filebeat collects log events and send them to Elasticsearch or logstash while metricbeat collects information on the operating system and services that are running.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible.
- Update the hosts file to include the IP for the elk server which is 10.1.0.4
- Run the playbook, and navigate to kibana to check that the installation worked as expected.
