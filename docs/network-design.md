# Network Design Notes

![Azure VM traffic path](../assets/azure-vm-nsg-lab-map.png)

The VM is only one part of the connection. Its network interface sits in a subnet inside a virtual network. A public IP makes the interface reachable from outside Azure, while the NSG decides whether the test traffic is allowed through.

## Connection Path

1. My computer starts an RDP or SSH connection to the public IP.
2. Azure evaluates the NSG rules associated with the NIC or subnet.
3. Allowed traffic reaches the VM network interface.
4. The guest firewall evaluates the connection again.
5. RDP or SSH responds only if the service is running and the credentials are valid.

## Resources to Check

| Resource | Useful question |
| --- | --- |
| Resource group | Are all lab resources grouped together for cleanup? |
| Virtual network | Is the address space what I expected? |
| Subnet | Is the VM on the correct segment? |
| Network interface | Does it have the correct private and public IP configuration? |
| NSG | Is it attached where I think it is? |
| Public IP | Is this still needed after the test? |

The design intentionally stays small. A later version would remove the VM public IP and use Bastion, a VPN, or another private management path.
