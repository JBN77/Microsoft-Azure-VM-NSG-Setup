# Validation Checklist

This is the checklist I would use before considering the lab complete.

## Azure Resource Checks

- [ ] Resource group exists and has a clear lab name.
- [ ] VM is running.
- [ ] VM is attached to the expected virtual network.
- [ ] VM is attached to the expected subnet.
- [ ] Public IP is present only if needed for testing.
- [ ] Network interface is connected to the expected NSG.

## NSG Checks

- [ ] Required remote access rule exists.
- [ ] Rule uses the correct port.
- [ ] Rule source is restricted when possible.
- [ ] Rule priority does not conflict with another rule.
- [ ] Unneeded inbound rules are removed.

## Connection Checks

- [ ] RDP or SSH test succeeds.
- [ ] OS firewall is not blocking the intended test.
- [ ] Credentials are stored safely and not documented in the repo.
- [ ] Wireshark capture shows traffic for the expected protocol or port.

## Cleanup Checks

- [ ] Stop or delete VM if the lab is no longer needed.
- [ ] Remove unused public IPs.
- [ ] Remove unused disks.
- [ ] Delete the resource group if the lab is complete.
