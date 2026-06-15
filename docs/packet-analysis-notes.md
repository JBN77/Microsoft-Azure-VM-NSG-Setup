# Packet Analysis Notes

I used Wireshark in this lab to get more comfortable looking at traffic instead of only trusting that a connection worked. The point was not deep packet forensics. The point was to connect the Azure NSG rule to real traffic I could observe.

## My Goal

I wanted to answer a few simple questions:

- Do I see traffic when I try to connect?
- What protocol or port is being used?
- Is the traffic going to the expected destination?
- Does the traffic pattern change when access is blocked or allowed?

## Useful Wireshark Filters

| Filter | What it helps show |
| --- | --- |
| `tcp.port == 3389` | RDP traffic |
| `tcp.port == 22` | SSH traffic |
| `icmp` | Ping traffic |
| `ip.addr == x.x.x.x` | Traffic to or from one IP address |
| `tcp.flags.syn == 1` | New TCP connection attempts |

## What I Was Looking For

| Observation | What it can mean |
| --- | --- |
| SYN packets with no response | Traffic may be blocked or the service may not be listening |
| Successful TCP handshake | The port is reachable and responding |
| Repeated retries | Connectivity or firewall issue |
| No packets visible | Wrong interface, wrong filter, or traffic is not reaching the machine |

## Notes

Wireshark is most useful when paired with a clear test. For example, I would start a capture, attempt RDP or SSH, stop the capture, and then filter for that port. That makes the capture easier to read.
