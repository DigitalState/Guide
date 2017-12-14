# Deployments


# Cloud

Cloud deployments can be easily facilitated by updating the Inventory file for the Ansible deployment in the [SDK](https://github.com/DigitalState/Sdk), and using your specific [cloud provider module for Ansible](http://docs.ansible.com/ansible/latest/list_of_cloud_modules.html).


# On-Premise

On-Premise deployments can be easily facilitated by updating the Inventory file for the Ansible deployment in the [SDK](https://github.com/DigitalState/Sdk), and then using SSH keys to connect to your host machine.  The base configuration of the platform is configured for this.  See the [SDK](https://github.com/DigitalState/Sdk) for further deployment instructions.


# Development

Development deployments (typically local machine) are facilitated through the [SDK](https://github.com/DigitalState/Sdk) using the default configurations.  Note that there are two options for deployments when doing development work: you can deploy from a Docker Image (typically the default Docker Hub), or you can create a manual build which will generate a image locally using the downloaded Git Repository.  This is a configuration option in the Ansible Inventory file. 