# Monitoring

A custom dashboard (Node.js backend, vanilla-JS frontend, behind login) pulls from the Proxmox API, TrueNAS, the media apps, Tailscale and the guests themselves.

- **Overview:** CPU/RAM/storage, guest status, service uptime checks, temperatures and a storage-growth forecast
- **Alerts:** to my phone via a Telegram bot, with quiet hours and cooldowns. Alerts include: service or site down (and whether the container, tunnel or nginx is at fault), disk SMART problems, high temperature, failed backups or restore tests, Tailscale devices going offline, unexpected SSH logins, firewalled guests trying to reach the LAN
- **Maintenance page:** pending updates per container with one-click update (optional backup first) and "Update all", disk health, backups and snapshots, certificate expiry for the public sites
- **Reports:** a morning summary and a weekly report
- **Admin tooling:** browser terminals with Claude agents per container, a task queue for the agents, snapshot and restore buttons

Also: SMART self-tests (short weekly, long monthly), TrueNAS scrubs and snapshot tasks, security-only unattended upgrades in every container.
