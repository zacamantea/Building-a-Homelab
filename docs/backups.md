# Backups

## Strategy
- **Deduplicated nightly backups** of every running guest to a Proxmox Backup Server (PBS) with its datastore on a *different physical disk* than most guests.
- A second job backs up the photo library and the PBS container itself as plain compressed files to the other disk, so PBS is never the only copy of itself.
- Retention: 7 daily, 4 weekly, 3 monthly.
- Stopped lab VMs are backed up weekly.

## Schedule
| When | What |
|---|---|
| 02:00 daily | Running guests → PBS |
| 02:30 daily | Photo library + PBS container → file backups on the other disk |
| 03:00 Sunday | Stopped lab VMs → PBS |
| 05:15 daily | PBS garbage collection |
| 05:45 daily | PBS verify job (reads and checks every chunk) |
| Saturday 04:00 | Backup verification script (newest backup of every guest) |
| Wednesday 04:00 | **Restore test**: restore one guest to a temporary ID with networking unplugged, boot it, check it, delete it |

## Why restore tests
A backup that has never been restored is a hope, not a backup. The weekly test proves the newest backups actually boot; failures raise an alert on my phone. Scripts: see `backup-and-dr-automation`.

## Known gaps
- No off-site copy yet.
- The big TrueNAS data pool image is excluded from VM-level backups (it is protected by TrueNAS snapshots instead).
