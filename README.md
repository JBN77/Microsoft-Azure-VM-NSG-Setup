# Azure VM Networking Lab

This lab follows the network path around an Azure virtual machine: resource group, virtual network, subnet, network interface, public IP, and Network Security Group. I used RDP or SSH as the test traffic and Wireshark as a second way to see what happened during a connection attempt.

![Azure VM traffic path](assets/azure-vm-nsg-lab-map.png)

## What I Wanted to Understand

Creating a VM in the portal is straightforward. The part I wanted to slow down and examine was everything that makes the connection possible:

- Which Azure resource owns the public address?
- Where does the VM sit inside the private network?
- Which NSG rule allows the management connection?
- What changes when a rule is too broad, missing, or attached in the wrong place?
- What traffic can I see from inside the VM?

## Lab Pieces

| Resource | Use in this lab |
| --- | --- |
| Resource group | Keeps the VM and its network resources together |
| Virtual network | Provides the private address space |
| Subnet | Places the VM in a defined network segment |
| Network interface | Connects the VM to the subnet |
| Public IP | Temporary endpoint for the remote-access test |
| Network Security Group | Filters inbound traffic before it reaches the VM |
| Wireshark | Captures traffic seen by the guest operating system |

The traffic path is described in more detail in [docs/network-design.md](docs/network-design.md).

## Screenshots From the Build

### VM Creation

![Azure VM creation screen](https://imgur.com/ckUj7LJ.png)

![Azure VM configuration screen](https://imgur.com/pvjGl9G.png)

### Resource Group

![Azure resource group screen](https://imgur.com/wb6YuaA.png)

### Network Security Group

![Azure NSG configuration screen](https://imgur.com/3Ze8Dbx.png)

## Rule Choices

For this lab, management access is the only inbound traffic I need:

| Test | Port | Protocol | Source |
| --- | --- | --- | --- |
| RDP to a Windows VM | `3389` | TCP | My current public IP when possible |
| SSH to a Linux VM | `22` | TCP | My current public IP when possible |

I would not leave either rule open to the whole internet after testing. The decision notes are in [docs/nsg-rule-plan.md](docs/nsg-rule-plan.md).

## How I Checked the Setup

1. Confirmed the VM was running and attached to the expected subnet.
2. Confirmed the public IP belonged to the correct network interface.
3. Checked the NSG association and inbound rule priority.
4. Attempted the RDP or SSH connection.
5. Checked the guest firewall and service if the connection failed.
6. Captured traffic with Wireshark during a controlled test.

The complete checklist is in [docs/validation-checklist.md](docs/validation-checklist.md). Wireshark filters and observations are in [docs/packet-analysis-notes.md](docs/packet-analysis-notes.md).

## Troubleshooting Order

When the connection does not work, I check the path from outside to inside:

1. VM state and public IP
2. NSG rule, source, port, and priority
3. NSG association to the subnet or NIC
4. Guest operating system firewall
5. RDP or SSH service inside the VM

More detail is in [docs/troubleshooting-notes.md](docs/troubleshooting-notes.md).

## Scope and Limits

- This is a small lab, not a production Azure design.
- The public IP exists for testing; Azure Bastion or private connectivity would be a better long-term approach.
- The screenshots document VM, resource group, and NSG setup. They do not show Network Watcher flow logs or a Bastion deployment.
- Wireshark shows traffic visible to the guest. It does not replace Azure platform logging.

## Next Lab

I would add a second VM without a public IP, test private communication between the two machines, and compare the result with an NSG rule that blocks one direction. Afterward, I would delete the resource group and confirm that no public IPs or managed disks were left behind.
