# Wireshark Notes

The capture method was simple: start Wireshark on the VM, begin a controlled RDP, SSH, or ping test, stop the capture, then filter for the expected protocol. This keeps the capture small enough to read.

## Filters Used

| Filter | Use |
| --- | --- |
| `tcp.port == 3389` | RDP traffic |
| `tcp.port == 22` | SSH traffic |
| `icmp` | Ping traffic |
| `ip.addr == x.x.x.x` | Traffic to or from one host |
| `tcp.flags.syn == 1` | TCP connection attempts |

## Reading the Result

- A TCP handshake shows that the connection reached a listening service.
- Repeated SYN packets without a response point to a blocked path or a service that is not listening.
- No matching packets can mean the wrong capture interface, an overly narrow display filter, or traffic blocked before it reached the VM.

Wireshark only shows packets visible to the guest. For Azure-side flow records, I would use Network Watcher or another platform logging option.
