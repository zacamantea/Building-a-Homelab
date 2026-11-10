# Hardware

## Main node ("zac"): Proxmox VE 9
| Part | Detail |
|---|---|
| Board | ASRock B650I Lightning WiFi (mini-ITX) |
| CPU | AMD Ryzen 9 7900, 12 cores / 24 threads |
| RAM | 32 GB DDR5 |
| GPU | NVIDIA Quadro T1000 (4 GB), shared with one container via device passthrough |
| Boot / fast storage | 2 TB NVMe (Proxmox system, `local-lvm`) |
| Bulk storage | 2 × 8 TB HDD: one for most guests, one for photos and backups |
| Power | No UPS yet (planned). Sleep/suspend disabled. Wake-on-LAN enabled |

## Storage layout
| Storage | Disk | Used for |
|---|---|---|
| `local`, `local-lvm` | NVMe | Proxmox, templates, latency-sensitive guests (supports snapshots) |
| `EightTB` | 8 TB HDD | Most guest disks, the TrueNAS data pool image |
| `NewForImage` | 8 TB HDD | Photo library and the backup datastore |
| `pbs` | on `NewForImage` | Proxmox Backup Server datastore (deduplicated) |

Design rule: **a guest never backs up to the disk it lives on.**

## Network gear
Fios router (CR1000A) with DHCP reservations for servers, a separate IoT Wi-Fi network for smart devices, WPA2/WPA3 on the main network.
