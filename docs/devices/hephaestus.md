# Hephaestus

## Role and status

Current temporary Home Lab server running Docker/YAMS/Plex. The owner confirmed the model and supplied command results from the October 28, 2026 inventory and successful Athena-to-Hephaestus SSH exercise. All October 28 findings below are **owner-provided evidence**, not commands independently executed by Codex. They describe that inspection, not continuous service health.

## System inventory — 2026-10-28

| Item | Value |
| --- | --- |
| Model | Dell Latitude 7480; owner-confirmed |
| Operating system | Ubuntu 26.04.1 LTS, Resolute Raccoon |
| Kernel | `7.0.0-42-generic` |
| Architecture | x86_64 |
| CPU | Intel Core i5-6300U; 2 physical cores / 4 threads |
| Virtualization capability | Intel VT-x reported; running VM workloads were not established |
| Maintenance | Owner performed system update, upgrade, and reboot; this does not establish that every security finding is resolved |

### Memory

| Item | Owner-provided result |
| --- | --- |
| Installed modules | Two 8 GB DDR4 SODIMMs; 16 GB installed |
| Module speed | Rated 2400 MT/s; configured at 2133 MT/s |
| Firmware-reported maximum | 32 GB; upgrade compatibility has not been independently validated |
| Linux-visible total memory | Approximately 14 GiB; total system memory, not a measure of free memory |
| Swap | 2 GiB; unused at inspection |

TODO: establish why installed memory differs from Linux-visible total memory. The supplied results do not establish a reservation purpose or hardware fault.

### Storage and application paths

| Item | Owner-provided result |
| --- | --- |
| Device | Samsung 512 GB NVMe SSD; approximately 476.9 GiB displayed capacity |
| EFI partition | 512 MiB; VFAT |
| Root partition | Approximately 476.4 GiB; ext4 |
| Root filesystem usage | 18% at inventory; approximately 365 GB available at the October 28 backup check; dated observations, not a current capacity guarantee |
| Docker root directory | `/var/lib/docker` |
| YAMS application configuration | `/opt/yams/config/`; 237 MB at the October 28 backup check |
| Shared media directory | `/srv/media`; 29 GB at the October 28 backup check |
| Sonarr and qBittorrent media mapping | Both bind-mount host `/srv/media` to container `/data` |

The matching container mount paths are recorded inventory evidence; they do not prove successful downloading, imports, permissions, or application-level health. Filesystem identifiers, serial numbers, personal data, and sensitive configuration are omitted.

### Container inventory

At the earlier October 28 inventory, ten containers were running: Bazarr, Lidarr, Plex, Portainer, Prowlarr, Radarr, SABnzbd, Sonarr, qBittorrent, and Gluetun. Gluetun reported a healthy Docker health check. Container running state and that health check do not establish that all applications or routing behavior are fully functional.

At that inventory, four additional containers were stopped: an older Watchtower-named container and three with automatically generated names. Their purpose, retirement status, and continued need remain TODO. No deletion, restart, or modification is implied by this inventory.

### Networking and SSH security

| Area | Owner-provided result |
| --- | --- |
| Default IPv4 route | Used a Wi-Fi interface; IPv4 connectivity was DHCP-configured |
| SSH service | Loaded, active, running, and enabled |
| SSH listener | TCP port 22 over IPv4 and IPv6 |
| UFW | Active; default deny incoming and allow outgoing |
| SSH firewall access | Permitted; source restrictions need future review |
| SSH public-key authentication | Enabled |
| Password authentication | Disabled |
| Keyboard-interactive authentication | Disabled |

The successful [SSH administration exercise](../operations/ssh-athena-hephaestus.md) establishes one tested client-to-server access path on October 28. Listening on IPv4/IPv6 does not establish public exposure, and UFW's default policy alone does not establish effective source restrictions. TODO: review intended SSH sources and IPv4/IPv6 exposure through a separately authorized security review; keep real endpoints, private hostnames, and network identifiers outside public documentation.

The CPU inspection reported a **Gather Data Sampling vulnerability condition involving microcode**. This remains an unresolved security review item, not evidence of compromise. TODO: retain sanitized evidence privately and establish the exact reported condition, applicable mitigation, and follow-up validation. The owner's update/upgrade/reboot does not by itself demonstrate remediation.

## Backup failure and recovery — 2026-10-28

Source: owner-provided October 28 terminal output; Codex did not execute the backup, recovery, or checks.

- **Prior backup:** The August 5 YAMS archive was readable and contained Compose files, `.env`, and application configuration. Its permissions were successfully restricted from `664` to `600`; contents and secrets are not reproduced here.
- **Failure and recovery:** The first October 28 backup failed because `/opt/yams/config/portainer/backups` is owned by root with permissions `700`. The YAMS backup script exits on archive failure without restarting services, leaving all YAMS containers stopped. The owner recovered them using `yams start`. At that point Gluetun and Watchtower reported healthy in Docker.
- **Successful retry:** A second backup succeeded with elevated privileges and an `EXIT` trap to restart YAMS. Archive `yams-backup-2026-10-28-1793234179.tar.gz` is 97,943,918 bytes, owned by `root:root`, with permissions `600`; it passed a tar readability check.
- **Post-backup state:** YAMS reported all 11 containers running following the successful retry; a separate Docker health check was not performed afterward. Application-level functionality was not independently reverified; these results supersede the earlier YAMS running count without establishing the disposition of other stopped containers.
- **Protection gaps:** No external backup disk or mounted network backup storage was detected. No off-device backup exists, and no backup restoration test has occurred. A readable local archive does not establish recoverability or protection against loss of the server/SSD; media backup coverage remains TODO.
- **Next actions:** Arrange and verify an off-device copy; define backup scope (including media), retention, and recovery requirements; document a controlled restore test with prerequisites, validation, and rollback; reverify application behavior. Document backup permission preflight and guaranteed service restart on failure in the [YAMS troubleshooting log](https://github.com/kkerns20/yams-media-server/blob/main/docs/troubleshooting.md) before the next backup. Script hardening and operational tests require separate authorization; the successful retry does not establish a permanent script fix.

## Terminal identity

Owner-selected appearance, reported October 28, 2026:

| Item | Selection |
| --- | --- |
| Theme identity | Dark Oxblood / Oxblood Forge |
| Terminal emulator | Ptyxis |
| Palette | Dark Pastel |
| Bash prompt | Two lines with a `HEPHAESTUS` label |
| Hostname accent | `#C45A69` |
| Separator | `#93858A` |
| Directory | `#E8DCCF` |
| Command arrow | `#C9A66B` |

The owner reported updating `~/.bashrc`. Persistence in a separately verified fresh terminal session was not established in the supplied results and remains TODO. A custom prompt label does not establish the underlying system hostname; the SSH exercise verified remote identity using `hostname` and `id -un`, without publishing their output.

## Administration and documentation

The [Athena-to-Hephaestus SSH runbook](../operations/ssh-athena-hephaestus.md) records the owner-tested dedicated-key access workflow, host-key verification, validation, and untested recovery considerations. Detailed YAMS deployment and troubleshooting remain in the [YAMS repository](https://github.com/kkerns20/yams-media-server).

TODO: expand service dependency/version and storage inventory, validate application behavior, close the [backup protection gaps](#backup-failure-and-recovery--2026-10-28) and test restoration under separate authorization, review security findings above, and verify terminal persistence. Wired-network readiness and migration/recovery acceptance criteria remain future work. The October 28 authorization-file backup and comparison were not a system backup or a restoration test.

## Future role

Migration to Olympus is planned, not completed. Hephaestus remains the temporary server until migration and validation succeed. A later lab or Docker-testing role remains an option; Hermes currently fills the portable administration role. See the [server roadmap](../../projects/home-server-roadmap.md).

See the [device inventory](README.md), [architecture](../architecture/README.md), and [operations](../operations/README.md).
