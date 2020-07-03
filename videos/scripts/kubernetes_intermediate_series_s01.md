# Kubernetes - Intermediate Series - Season 01
The goal of this series is to provide an intermediate to advanced level of education covering Kubernetes on bare metal (technically plain vms). The content covered in this series will be useful for deploying your own on-prem Kubernetes deployments and for creating learning labs. This series will use KVM on Ubuntu Server to create "bare-metal" guest vms for the Kubernetes nodes and the management client.

In addition to covering Kubernetes and KVM, this series will also be leveraging Ansible & AWX for deployment and configuration automation, Helm 3 for service deployments, Rook & Ceph for persistent storage, MetalLB for Load Balancing, Flannel Networking, Kubernetes UI Dashboard, and Git/GitHub for version control.

## e01 _ Kubernetes - Host and Client Configuration (KVM Guests)
In this episode, we will review and configure the VM specifications and install Ubuntu to the 4 VMs, 3 Kubernetes Nodes and 1 Management Client.

### VM Overview
  - Nodes: Ubuntu Server 18.04.4 LTS
    - ubuntu-18.04.4-live-server-amd64.iso
  - Client: Ubuntu Desktop 19.10
    - ubuntu-19.10-desktop-amd64.iso
  - Virt-Manager / VMM
  - Storage is backed by zfs, so disks are raw format zvols
  - Export virsh configuration to json/xml and save to github repo
    - Document how to import config and launch vm from config
    - `virsh dumpxml kube_client > kube_client_virsh.xml`
    - `zfs send pool1/kube_client@os_installed| xz -9 > kube_client_-_os_installed.xz`

### VM Settings
  - All Nodes:
    - OS Disk - 10GiB
    - Kubernetes Mount - 20GiB
    - ClusterFS Mount - 100GiB
  - Master Node
    - CPU 1 Socket 4 Cores 1 Thread
    - RAM 4GiB
  - Cluster Node
    - CPU 1 Socket 8 Cores 1 Thread
    - RAM 8GiB
  - Client:
    - Disk - 40GiB
    - CPU 1 Socket 4 Cores 1 Thread
    - RAM 8GiB

### Client Installation Steps
1. Create Client virtual machine, using VMM
2. Select Ubuntu Desktop 19.10 ISO
3. For OS, you can choose any "Ubuntu xx.yy LTS"
4. Memory: 8192MiB(8GiB), CPUs: 4
5. Create a disk image, 40GiB (Ensure it isn't named .qcow2)
6. Name the vm "kube_client", Check the box for customize before install, and select the appropriate KVM network that has internet access
7. CPUs Tab: Check the box for copy host CPU configuration, Manually set CPU topology to 1 Socket 4 Cores 1 Thread, ensure "current allocation" is "4", hit apply.
8. Begin Installation of Ubuntu
    1. Choose English for language
    2. Choose Install Ubuntu
    3. In virt-manager window menu, select View / Resize to VM
    4. Select English, Continue
    5. Select English (US) for keyboard layout
    6. Choose Minimal Installation and Download updates while installing, Continue
    7. Erase disk and install ubuntu, leave everything else unchecked, Install Now, Continue
    8. Select your TimeZone (Chicago)
    9. Your name: Local Admin
    10. Your computer's name: kube-client
    11. Username: localadmin
    12. Password: "Password"
    13. Restart now, Eject ISO, "Enter"
    14. Login, Skip Account setup, No do not send..., location off.
    15. Shutdown VM, then take a snapshot with `zfs snapshot pool1/kube_client@os_installed`

## e02 _ Kubernetes - Installing Dependencies, Hosts and Client

## e03 _ Kubernetes - Automating Dependency Installation with Ansible

## e04 _ Kubernetes - Initializing Single Node Master

## e05 _ Kubernetes - Joining Nodes to Cluster

## e06 _ Kubernetes - Automating Cluster Initialization with Ansible

## e07 _ Kubernetes - Backup and Recovery

## e08 _ Kubernetes - Deploying WordPress with Helm

## e09 _ Kubernetes - Building a Pre-Configured KVM Host Image