# Troubleshooting Notes

These are the first places I would check if the VM or connection did not work.

## Cannot Connect With RDP or SSH

1. Confirm the VM is running.
2. Confirm the public IP address has not changed.
3. Check the NSG inbound rule for the correct port.
4. Check the source IP on the NSG rule.
5. Confirm the operating system firewall allows the traffic.
6. Confirm the service is running inside the VM.

## NSG Rule Looks Correct but Connection Still Fails

Possible causes:

- Rule priority is lower than a deny rule.
- Wrong subnet or network interface has the NSG.
- Public IP is attached to a different network interface.
- OS firewall blocks the port.
- RDP or SSH service is not running.
- Credentials are incorrect.

## Wireshark Does Not Show Expected Traffic

Things to check:

- Capturing on the wrong interface.
- Display filter is too narrow.
- Traffic is blocked before reaching the VM.
- Connection test was not running while capture was active.

## Cleanup Reminder

After testing, I would remove unnecessary public access and delete unused resources. In Azure, leaving a lab running can create cost and security issues.
