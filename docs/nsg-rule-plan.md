# NSG Rule Notes

The NSG is the main Azure-side filter in this lab. I only need one management port at a time, so the rule should be narrow and temporary.

## Test Rules

| Use | Direction | Port | Protocol | Source | Action |
| --- | --- | --- | --- | --- | --- |
| RDP to Windows | Inbound | `3389` | TCP | My public IP | Allow |
| SSH to Linux | Inbound | `22` | TCP | My public IP | Allow |

The default inbound deny remains in place for traffic that does not match an allow rule.

## Review Before Testing

- Confirm the rule is attached to the correct NIC or subnet.
- Confirm the source is my current public IP, not `Any`.
- Check rule priority for conflicts.
- Open only the port used by the current VM.
- Confirm the guest firewall has a matching rule.

## Cleanup

After the test, I would remove the temporary rule or the public IP. For a longer-lived VM, I would use Bastion, private connectivity, or just-in-time access instead of leaving RDP or SSH exposed.
