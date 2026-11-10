# Services

| Guest | Type | What it runs |
|---|---|---|
| TrueNAS | VM | TrueNAS SCALE: storage pool plus an app stack (media automation, Plex, Jellyfin, requests, torrent client behind a VPN) |
| immich | LXC | Self-hosted photo library (Immich, Postgres, Redis, ML) with a 5 TB volume |
| AMP | LXC | Game-server panel (Minecraft servers) + tunnel for friends |
| Dash-Board | LXC | My own monitoring and admin dashboard (Node backend + static frontend) |
| PBS | LXC | Proxmox Backup Server (dedup, verify jobs, garbage collection) |
| Website 1 / Website 2 | LXC ×2 | Public sites (Node API + nginx), published via Cloudflare Tunnel, firewalled to internet-only |
| AI agent experiment | LXC | Isolated container with the GPU and a firewall that keeps it off the LAN |
| Project containers | LXC ×2 | Scratch space for new projects (cloned from a clean template) |
| Windows AD lab | VMs ×6 | Domain controller + Win 10/11 clients, powered off until needed |
| Templates | LXC / VM | Clean Ubuntu container template and VM for fast, consistent builds |

New containers are created with a single script (full clone of the template, sized and addressed on the command line, added to the nightly backup automatically): see `automated-proxmox-provisioning`.
