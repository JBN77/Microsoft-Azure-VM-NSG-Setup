# NSG Rule Plan

The Network Security Group was the main security control in this lab. My goal was to allow only the traffic needed for testing and avoid opening unnecessary inbound access.

## The Problem

When a VM has a public IP, management ports can become reachable from the internet if the NSG is too open. RDP and SSH are useful for administration, but they should not be casually exposed.

## Rules I Practiced

| Purpose | Direction | Port | Protocol | Source | Action |
| --- | --- | --- | --- | --- | --- |
| RDP to Windows VM | Inbound | `3389` | TCP | My public IP when possible | Allow |
| SSH to Linux VM | Inbound | `22` | TCP | My public IP when possible | Allow |
| Default inbound protection | Inbound | Any | Any | Internet | Deny by default |

## How I Would Review a Rule

Before leaving a rule enabled, I would ask:

- Do I still need this port open?
- Is the source restricted, or is it open to the internet?
- Is the priority correct?
- Does the operating system firewall also allow the traffic?
- Can I replace public access with Bastion, VPN, or another safer method?

## Safer Admin Access Notes

For a short lab, exposing RDP or SSH can be acceptable if I understand the risk and clean up afterward. For a real environment, I would prefer:

- Azure Bastion
- VPN access
- Just-in-time VM access
- Restricting source IPs
- Disabling public IP access when not needed
