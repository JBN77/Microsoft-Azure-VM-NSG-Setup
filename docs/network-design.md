# Network Design Notes

This lab uses a simple Azure setup: one resource group, one virtual machine, one virtual network, one subnet, a public IP for remote access testing, and a Network Security Group to control inbound traffic.

![Azure VM and NSG lab map](../assets/azure-vm-nsg-lab-map.png)

## My Goal

I wanted to understand how the basic Azure networking pieces connect to each other. A VM is not just a VM by itself. It is attached to a network interface, which sits in a subnet, which belongs to a virtual network. If the VM needs internet-facing access, it also needs a public IP and an NSG rule that allows the traffic.

## Resource Layout

| Resource | Why it matters |
| --- | --- |
| Resource group | Keeps all lab resources together |
| Virtual network | Defines the private network space |
| Subnet | Places the VM inside a smaller network segment |
| Network interface | Connects the VM to the subnet |
| Public IP | Allows temporary remote access from outside Azure |
| NSG | Controls what traffic is allowed in or out |

## Traffic Flow

1. My computer starts an RDP or SSH session.
2. The connection goes to the VM public IP.
3. Azure checks the NSG rule.
4. If the rule allows the port and source, traffic reaches the network interface.
5. The VM accepts the connection if the operating system firewall and service are configured correctly.

## Design Notes

- I treated public access as temporary for the lab.
- I used the NSG as the first place to control inbound traffic.
- I kept the design small so troubleshooting would be easier.
- In a stronger setup, I would use Azure Bastion or a VPN instead of exposing management ports directly.
