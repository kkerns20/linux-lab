# Home Server Roadmap

This roadmap plans migration from **Hephaestus**, the current temporary Dell laptop server, to **Olympus**, a planned permanent, wired, expandable Home Lab server. Migration has not been documented as completed.

## Current hardware and role

Owner-confirmed on 2026-10-27:

- Dell Latitude 7480 (Hephaestus)
- Intel Core i5-6300U
- 16 GB RAM
- 512 GB SSD
- Ubuntu 26.04.1 LTS
- Docker, YAMS, and Plex

See the [Hephaestus device page](../docs/devices/hephaestus.md) for current inventory. Earlier SSD manufacturer/interface and network-adapter details require verification; they are not treated as confirmed specifications. TODO: verify storage expansion limits, workload capacity, and utilization before selecting replacement hardware.

## Future role for Hephaestus

Hephaestus remains the temporary server until Olympus is ready and migration is validated. After migration, it could support Linux experiments, temporary VMs, or Docker testing. Its final role is TODO. Hermes currently fills the portable administration role, while Athena is the Linux development workstation.

The original direction of moving permanent services to a stationary machine remains the plan.

## Permanent server target: Olympus (planned)

Olympus should be always on, wired to Ethernet, and located permanently in the office. Hardware has not been selected. The specifications and hardware families below are planning candidates, not confirmed purchases or current market recommendations. TODO: validate requirements, compatibility, pricing, and availability before purchase.

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

The proposed long-term design separates fast compute storage from bulk media storage. OS, paths, filesystem choices, and physical layout require validation before implementation.

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

Planning budget: approximately $150; current pricing and feasibility TODO.

Add one large CMR hard drive for bulk media while keeping Ubuntu, Docker, Plex metadata, and application configuration on NVMe.

Learning goals:

- `lsblk`
- partitioning and formatting
- ext4
- UUIDs
- `/etc/fstab`
- mount points
- ownership and permissions

### Stage 2: expandable media pool

Planning budget: approximately $500; current pricing and feasibility TODO.

Add a multi-bay powered DAS and begin building a flexible media pool. MergerFS plus SnapRAID is a strong candidate because the media workload is dominated by large, mostly static files and future expansion is important.

Learning goals:

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

Moving YAMS from Hephaestus to Olympus should be treated as its own Home Lab project rather than a fresh install.

Detailed YAMS procedures belong in the [YAMS repository](https://github.com/kkerns20/yams-media-server); keep secrets and VPN configuration details out of this repository. This checklist is planned work, not an executed procedure.

The migration should document:

1. Inventory the current host.
2. Verify the current configuration location (previously documented as `/opt/yams`) and back it up safely.
3. Preserve secrets outside Git.
4. Verify the current media layout (previously documented as `/srv/media`) and recreate the required paths.
5. Install Docker and Docker Compose on the new host.
6. Restore/recreate YAMS containers.
7. Verify UID/GID and filesystem permissions.
8. Verify Gluetun/VPN routing.
9. Confirm the deployed service inventory, then validate Plex and applicable YAMS services such as qBittorrent, Sonarr, Radarr, and Prowlarr.
10. Test automatic startup after reboot.
11. Test recovery from a failed service.
12. Retire the laptop from permanent-server duty.

## Immediate next work

Before purchasing hardware:

- document the current YAMS system
- confirm whether the previously noted Sonarr/Radarr automatic download/import issue remains open, then triage if needed
- use wired Ethernet when the Latitude is acting as the server
- establish a backup procedure for configuration
- define a mini-PC budget and compare real candidates

## Related future infrastructure

Prometheus is a potential Raspberry Pi automation platform. Adoption, model, workloads, and integration are TODO; no system is confirmed as deployed. Future automation and monetization experiments remain exploratory and should be evaluated alongside the [Solutions Engineering roadmap](solutions-engineering-roadmap.md).

See the [architecture overview](../docs/architecture/README.md) and [operations backlog](../docs/operations/README.md) for documentation still needed before migration.
