# Kubespray role for RDMA Shared Device Plugin

Role Name: mlnx-hca-shared
=======================

The Role is added to K8s cluster availability to use in POD deployment RDMA devices for Apps with Native InfiniBand.

Requirements
------------
1. Kubernetes cluster is deployed by Kubespray
2. Separate InfiniBand fabric with enabled port virtualization support in Subnet manager
3. NVIDIA Mellanox ConnectX-4/5/6 network interface card in InfiniBand mode



Network requirements
-------------------
The Role is required an additional InfiniBand fabric for POD's with Native InfiniBand network interfaces.
For assistance in designing the scaled InfiniBand fabric topology please use the [Mellanox InfiniBand Cluster Configurator](http://www.mellanox.com/clusterconfig/). 
It is an online cluster configuration tool that offers flexible cluster sizes and options.


Role Variables
--------------

The settable variables for the Role must be provided in roles/mlnx-hca-shared/vars/main.yml.

[Mellanox OFED](https://www.mellanox.com/support/mlnx-ofed-public-repository/) and [Kubeflow MPI-Operator](https://github.com/kubeflow/mpi-operator/) are an optional installation components.


Dependencies
------------
During the installation process the Role used host configuration file of Kubespray config/inventory for deployment and provisioning the Kubernetes components.


Role deployment
---------------
Copy Role deployment files (playbook, configuration and deployment staff) to your Kubespray deployment folder.
Configure the Role variables and execute:

With root user:

```
# ansible-playbook -i inventory/mycluster/hosts.yaml  mlnx-hca-shared.yaml
```

With standard user:
```
$ ansible-playbook -i inventory/mycluster/hosts.yaml  --become --become-user=root mlnx-hca-shared.yaml
```
The execution time for this step may take a while to finalize.

License
-------
BSD

Author Information
------------------
author: [Vitaliy Razinkov](vitaliyra@nvidia.com)

company: [NVIDIA](http://www.nvidia.com/), Networking business unit

