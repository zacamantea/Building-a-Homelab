# Network

## Layout
```
Internet ── Fios router ──┬── Proxmox host (static IP)
                          ├── guests (DHCP reservations on the router)
                          └── Wi-Fi: main + separate IoT network
```
- One flat LAN for servers; addresses come from DHCP with **reservations**, the Proxmox host is static and sits outside the DHCP pool.
- No inbound port forwards. UPnP is limited to Tailscale and TrueNAS mappings.

## Remote access
**Tailscale** on the Proxmox host, TrueNAS, the dashboard, photos and game-server guests. Away from home I reach everything over the tailnet; there is no other way in. Offline devices on the tailnet trigger an alert.

## Public websites
Two public sites run in containers and are published through **Cloudflare Tunnels** (outbound-only connection, nothing exposed on the router).

## Isolation ("internet only" guests)
The Proxmox firewall is enabled **per guest**, not on the host. Internet-facing and experimental guests (the two websites and the AI-agent container) can reach the internet but **not** the home network: Proxmox, the router, NAS and other servers are all blocked. Blocked attempts are logged and send me an alert, so an attempted lateral move is visible immediately.
