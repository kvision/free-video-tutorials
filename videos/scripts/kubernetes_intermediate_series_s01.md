# Kubernetes - Intermediate Series - Season 01
This will be an intermediate level series covering Kubernetes on bare metal (technically bare vms). We will be using KVM to create "bare-metal" guest vms for the nodes and the management client. In addition to covering Kubernetes and KVM, we will also be leveraging Ansible & AWX for deployment and configuration automation, Helm 3 for container deployments, Rook & Ceph for persistent storage, MetalLB for Load Balancing, Flannel Networking, Kubernetes UI Dashboard, and Git/GitHub for version control.

## e01 _ Kubernetes - Host and Client Configuration (KVM Guests)

### VM Overview
  - Nodes: Ubuntu Server 18.04.4 LTS
    - ubuntu-18.04.4-live-server-amd64.iso
  - Client: Ubuntu Desktop 19.10
    - ubuntu-19.10-desktop-amd64.iso
  - Virt-Manager / VMM
  - Export virsh configuration to json/xml and save to github repo
    - Document how to import config and launch vm from config

### VM Settings
  - All Nodes:
    - OS Disk - QCOW 10GB
    - Kubernetes Mount - RAW 20GB
    - ClusterFS Mount - RAW 100GB
  - Master Node
    - CPU 1 Socket 4 Cores 1 Thread
    - RAM 4GB
  - Cluster Node
    - CPU 1 Socket 8 Cores 1 Thread
    - RAM 8GB
  - Client:
    - Disk - QCOW 40GB
    - CPU 1 Socket 4 Cores 1 Thread
    - RAM 8GB

## e02 _ Kubernetes - Installing Dependencies, Hosts and Client

## e03 _ Kubernetes - Automating Dependency Installation with Ansible

## e04 _ Kubernetes - Initializing Single Node Master

## e05 _ Kubernetes - Joining Nodes to Cluster

## e06 _ Kubernetes - Automating Cluster Initialization with Ansible

## e07 _ Kubernetes - Backup and Recovery

## e08 _ Kubernetes - Deploying WordPress with Helm

## e09 _ Kubernetes - Building a Pre-Configured KVM Host Image