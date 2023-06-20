# Steps for setting up a VM
1. Firstly you need an azure subscription
2. Then create a resource group
3. Create a virtual network and assign it a subnet
4. Create ssh key pair via git bash. Use cd to go home directory. (git bash)
5. Make ssh folder using mkdir .ssh (git bash)
6. Use command: ssh-keygen -t rsa -b 4096 -C "personal email" (git bash)
7. Enter file to save key: tech241-ryan-az-key (git bash)
8. Access key: cat tech241-ramon-az-key.pub (git bash)
9. Create ssh key in Azure: paste existing key (Azure)
10. Create virtual machine in azure: Security type standard, Image Ubuntu Server 18.04 LTS. Size standard_B1s. Username adminuser. Stored keys tech241-ryan-az-key. Inbound ports SSH and HTTP.
11. Click connect on virtual machine page (azure): chmod 400 <keyname>
12. Paste keyname into git bash
13. ls -l to see if it has worked
14. Input private key path (azure), ~/.ssh/tech241-ryan-az-key
15. Copy the run example command to your clipboard and paste into gitbash
16. Enter yes to authenticity fingerprint
17. ls -a to check hidden files
18. Stop vm on azure portal if you are not using it.




 # Virtulisation
### What is virtualisation?
Virtualisation is the process of creating a virtual version of a resource, such as an operating system, server, storage device, or network, to simulate the behaviour of the physical counterpart.
### What is a virtual machine?
A virtual machine (VM) is a software emulation of a physical computer, allowing multiple operating systems or applications to run on a single physical machine.
### Where can they be run?
Virtual machines can be run on various platforms, including desktop computers, servers, cloud infrastructure, and data centres.
### What determines how many can run?
The number of virtual machines that can run depends on the available resources, such as CPU, memory, storage, and network bandwidth of the underlying physical machine or virtualisation host.
### What does a virtual machine include?
A virtual machine includes a virtualised hardware environment (processor, memory, storage), an operating system, and any software applications installed within it.
### What software is required to orchestrate/run the virtual machines?
To orchestrate and run virtual machines, specialised software called a hypervisor or virtual machine monitor (VMM) is required. Examples include VMware vSphere, Microsoft Hyper-V, and KVM (Kernel-based Virtual Machine).
### What is the importance of an image when creating an VM?
An image is a preconfigured software template or snapshot that contains the necessary files and settings to create a virtual machine. It serves as a blueprint for the VM's initial state and enables easy deployment and replication of virtual machines.