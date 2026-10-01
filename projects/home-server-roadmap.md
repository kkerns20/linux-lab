# Home Server Roadmap

This document captures the next phase of the Home Lab: moving from a portable Dell laptop running Ubuntu and YAMS to a permanent, wired, expandable home server.

## Current hardware

The current lab host is a Dell Latitude 7480 with:

- Intel Core i5-6300U
- 2 physical cores / 4 threads
- 16 GB DDR4 RAM
- 512 GB Samsung NVMe SSD
- Intel I219-LM Ethernet
- Intel 8265 Wi-Fi
- Ubuntu 24.04.5 LTS

The machine is useful as a Linux learning system, but its portable laptop form factor, two-core CPU, 16 GB memory ceiling for practical workloads, and limited storage expansion make it a poor long-term infrastructure host.

## Intended role for the Dell

The Latitude should gradually become a portable lab and administration machine:

- Ubuntu desktop
- VS Code
- Git/GitHub
- SSH administration
- temporary VMs
- Linux experiments
- Docker testing

The permanent services should move to a stationary machine.

## Permanent server target

The next server should be always on, wired to Ethernet, and located permanently in the office.

Target characteristics:

- Intel Core i5, preferably 8th generation or newer
- 6 cores preferred for VM and container headroom
- Intel integrated graphics with Quick Sync for Plex
- 32 GB RAM
- 500 GB to 1 TB NVMe SSD
- Gigabit Ethernet minimum
- 2.5 GbE desirable
- USB 3.x / USB-C connectivity for external storage

Good hardware families to investigate include refurbished:

- Dell OptiPlex Micro
- Lenovo ThinkCentre Tiny
- HP EliteDesk / ProDesk Mini

A newer Intel mini PC is also an option, but very low-power N100/N150 systems should be compared against used six-core business mini PCs before buying because this lab is expected to run VMs as well as containers.

## Compute and storage architecture

The long-term design separates fast compute storage from bulk media storage.

```text
Permanent server
|
+-- NVMe SSD
|   +-- Ubuntu
|   +-- Docker
|   +-- YAMS configuration
|   +-- Plex metadata
|   +-- VM disks
|   +-- application databases
|
+-- external storage / future DAS
    +-- movies
    +-- tvshows
    +-- music
    +-- downloads
    +-- backups
```

YAMS should continue to see a stable path such as `/srv/media` regardless of how many physical disks are underneath it.

## Storage growth plan

### Stage 1: immediate expansion

Budget target: approximately $150.

Add one large CMR hard drive for bulk media while keeping Ubuntu, Docker, Plex metadata, and application configuration on NVMe.

Skills learned:

- `lsblk`
- partitioning and formatting
- ext4
- UUIDs
- `/etc/fstab`
- mount points
- ownership and permissions

### Stage 2: expandable media pool

Budget target: approximately $500.

Add a multi-bay powered DAS and begin building a flexible media pool. MergerFS plus SnapRAID is a strong candidate because the media workload is dominated by large, mostly static files and future expansion is important.

Skills learned:

- storage pooling
- parity
- SMART monitoring
- disk replacement
- failure recovery
- capacity planning

### Stage 3: dedicated storage platform

Long-term target: multi-drive storage with roughly 50-100+ TB usable capacity if needed.

At this stage, evaluate:

- MergerFS + SnapRAID / Unraid-style architecture for flexible media growth
- ZFS for stronger integrity, snapshots, and important non-media data
- direct SATA/SAS or an HBA rather than a large number of USB-attached disks
- UPS integration
- monitoring and alerting
- backup strategy

RAID or parity is not a substitute for backups.

## Migration project

Moving YAMS from the Latitude to the permanent server should be treated as its own Home Lab project rather than a fresh install.

The migration should document:

1. Inventory the current host.
2. Back up `/opt/yams` configuration safely.
3. Preserve secrets outside Git.
4. Recreate the `/srv/media` layout.
5. Install Docker and Docker Compose on the new host.
6. Restore/recreate YAMS containers.
7. Verify UID/GID and filesystem permissions.
8. Verify Gluetun/VPN routing.
9. Verify qBittorrent, Sonarr, Radarr, Prowlarr, and Plex.
10. Test automatic startup after reboot.
11. Test recovery from a failed service.
12. Retire the laptop from permanent-server duty.

## Immediate next work

Before purchasing hardware:

- document the current YAMS system
- triage Sonarr/Radarr automatic download/import behavior
- use wired Ethernet when the Latitude is acting as the server
- establish a backup procedure for configuration
- define a mini-PC budget and compare real candidates
