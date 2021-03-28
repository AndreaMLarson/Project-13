# Project-13
Automated ELK Stack Deployment - Azure

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.


[Cloud Security Diagram](https://github.com/AndreaMLarson/Project-13/blob/main/Diagrams/Cloud%20Security%20Diagram.png)

[ELK Stack Diagram](https://github.com/AndreaMLarson/Project-13/blob/main/Diagrams/ELK-Stack.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._
[Ansible Playbook](https://github.com/AndreaMLarson/Project-13/blob/main/Ansible/ansible_config.yml)

  ---
  - name: Config Web VM with Docker
    hosts: webservers
    become: true
    tasks:
      - name: docker.io
        apt:
          update_cache: yes
          name: docker.io
          state: present

      - name: Install pip3
        apt:
          name: python3-pip
          state: present

      - name: Install Docker python module
        pip:
          name: docker
          state: present

      - name: download and launch a docker web container
        docker_container:
          name: dvwa
          image: cyberxsecurity/dvwa
          state: started
          restart_policy: always
          published_ports: 80:80

      - name: Enable docker service
        systemd:
          name: docker
          enabled: yes


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, performant, and secure, in addition to restricting traffic to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
A load balancer receives traffic that comes into the website and distributes it across multiple servers to "balance" the "load" that is put on each server. +++Load balancers offer a health probe function to regularly check all the machines behind the load balancer. Machines with issues are reported, and the load balancers stop sending traffic to those machines. Load Balancers also help distribute traffic evenly across the servers and mitigates DoS attacks.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_   Filebeat is a lightweight shipper for forwarding and centralizing log data. It monitors the log files, (or designated locations) collects log events, and forwards them to Elasticsearch for indexing.
- _TODO: What does Metricbeat record?_ Metricbeat is a lightweight shipper that you can install on your servers to collect metrics from the operating system and services running on the server. It takes the metrics and statistics that it collects and ships them to  Elasticsearch

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name       | Function | IP Address | Operating System |
|------------|----------|------------|------------------|
| Jump Box   | Gateway     | 10.0.0.4   | Linux            |
| Web-1      | Client      | 10.0.0.5   | Linux            |
| Web-2      | Client      | 10.0.0.6   | Linux            |
| Web-3      | Client      | 10.0.0.7   | Linux            |
| Elk-Server | Monitoring  | 10.1.0.4   | Linux            |


### Access Policies

<<<<<<< HEAD
The machines on the internal network are not exposed to the public Internet.
=======

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the workstation IP address. (Home network IP in this scenario)

Machines within the network can only be accessed by ssh from the Jump-Box virtual machine.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.1 10.0.0.2    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server (IP 10.1.0.4) is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
Web-1: 10.0.0.5
Web-2: 10.0.0.6
Web-3: 10.0.0.7

We have installed the following Beats on these machines:
Filebeat
Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat: collects and ships log files to Elasticsearch for indexing.
Metricbeat: collects metrics from the operating system and from services running on the server (such as "up-time", CPU usage, and memory usage) and ships these metrics to Elasticsearch.


### Using the Playbook
<<<<<<< HEAD
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
=======
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
>>>>>>> e4870a4dec014c91e59fa25e148a733617734e10

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
