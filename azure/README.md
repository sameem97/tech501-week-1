## Azure Fundamentals

Azure is one of the 3 major cloud providers. Cloud computing is a way of accessing computing resources over the internet typically. The services provided by a cloud provider, such as Azure, can vary from Compute, Storage and Database, Analytics and AI, IoT, Networking etc.

### VNet

Azure Virtual Network (VNet) is the foundation of our infrastructure. It allows other services, like VMs, to connect to each other. In addition, if we configure public IPs and gateways, we can reach our resources from our local machine.

By default, VNets have a CIDR address space of 10.0.0.0/16.

### Subnet

Division of a VNet. For example, we can define one subnet for particular components of our infrastructure e.g. worker nodes (VMs).

See below for simple example architecture of how VNets, Subnets and resources such as a VM fit together:

![vnet subnet vm](../images/vnet_subnet_vm.png)

### Connecting to the VM

We can connect to our VM via its public IP using SSH, a frequently used network protocol to securely access devices over an unsecure network. We first have to generate an SSH public-private keypair, using RSA algorithm. This method is a lot safer than using login credentials to connect to the VM.