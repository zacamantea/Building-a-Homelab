# Changelog

Newest first.

## 2026-11-09
- Host upgraded (51 packages, kernel 7.0.14-28), rebooted, all guests verified
- Dashboard: task queue for agents, split-screen second terminal, "Update all" containers
- All projects put in private GitHub repos with a sync tool

## 2026-11-04
- Proxmox Backup Server added; nightly backups are now deduplicated and verified daily
- Public websites and the AI-agent container isolated from the home network (internet-only) with alerting
- GPU shared with a container; dashboard gained temperature, storage forecast, security and snapshot pages

## 2026-11-03
- Host upgraded to Proxmox VE 9.2; backup jobs created for all guests; weekly backup verification and restore tests
- TrueNAS tuned (RAM lowered after ZFS cache pushed the host into swap); snapshot tasks added
- Alerts moved to Telegram; router DHCP reservations and Wi-Fi hardening

## 2026-01-12
- Repo created
