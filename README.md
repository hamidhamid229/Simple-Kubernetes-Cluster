# Simple Kubernetes Cluster Setup with Ansible

Hello,

This Ansible project is a very simple setup to deploy a Kubernetes cluster with a single master node. It is mainly created for learning purposes and to help you understand how Kubernetes can be installed and configured using Ansible.

⚠️ This setup is NOT suitable for production environments. It does not include HA, Keepalived, load balancing, or other production-grade components. A more advanced and complete version will be added in the future.

---

## Configuration

First, you need to define your servers inside the inventory file:

/inventory/hosts.ini

You can add your server IPs there, for example:

[master]
192.168.1.10

[worker]
192.168.1.11
192.168.1.12

You can also use domain names instead of IPs if needed.

---

Next, you should set the Kubernetes network CIDR in the following file:

/inventory/group_vars/all.yml

By default, I have used:

pod_network_cidr: "10.244.0.0/16"

It is recommended not to change this value, because it is also used in the CNI (Flannel) configuration. If you change it, you must also update it in the CNI role accordingly.

---

## How to Run

After configuring everything, just run the playbook with the following command:

ansible-playbook -i inventory/hosts.ini playbooks/site.yml

---

## Requirements

Make sure Ansible is installed on your control machine, and you have SSH access to all target nodes. Python should also be available on the remote machines.

---

## Notes

This setup installs a basic Kubernetes cluster with one master node. It is designed for learning and testing only, not for production use.

---

## Future Work

In future versions, I will add support for HA clusters, Keepalived, load balancers, and a more production-ready architecture.

