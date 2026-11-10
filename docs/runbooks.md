# Runbooks

## After a host reboot / kernel update
1. `uname -r` shows the new kernel
2. `pct list` / `qm list`: everything with *start on boot* is running
3. GPU driver: `dkms status` shows the module built for the new kernel, `nvidia-smi` works on the host and in the GPU container
4. Check the public sites and TrueNAS apps (apps take a few minutes to come up)

## Update the host
`apt update && apt dist-upgrade`, then reboot (every guest restarts, so do it at a quiet time and after container updates have finished). Containers are updated from the dashboard.

## Restore a guest from backup
1. Proxmox → storage `pbs` → Backups → pick the newest *verified* backup → Restore (use a new ID first to compare)
2. Start it, check services, then swap in place if needed

## Add a container
Run the provisioning script (clone template → size → start → add to nightly backup), then join Tailscale and reserve its IP on the router.

## Network-isolate a guest
Enable the Proxmox firewall on that guest's NIC and add a per-guest rule set: allow DNS/DHCP to the router, drop the private ranges, allow internet. Keep the node firewall off.
