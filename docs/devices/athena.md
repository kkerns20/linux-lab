# Athena

## Role and status

Athena is the dedicated Fedora development and Linux learning workstation. It supports Git/GitHub documentation, SSH administration, Python development, and Codex CLI work. Olympus remains a planned permanent server; Hephaestus continues as the temporary Docker/YAMS/Plex server. See the [home server roadmap](../../projects/home-server-roadmap.md).

Sources and verification date: owner-confirmed hardware, role, and testing history, supplemented by read-only inspection of the current Fedora environment on 2026-10-27. Directly verified observations and owner-confirmed information are distinguished below. Hardware interaction tests, system updates, and firmware checks were not repeated during this documentation session.

## Confirmed specifications

Owner-confirmed on 2026-10-27:

| Item | Value |
| --- | --- |
| Model | HP Envy x360 15m-ds0xxx |
| CPU | AMD Ryzen 5 3500U |
| RAM | 8 GB installed |
| Storage | 256 GB Samsung NVMe SSD; LUKS-encrypted Btrfs storage |
| Operating system | Fedora Workstation 44 |
| Tools | Git, SSH, Codex CLI 0.165.0 |

### Directly verified hardware

| Item | Verified value and source |
| --- | --- |
| Manufacturer and model | HP; HP ENVY x360 Convertible 15m-ds0xxx (non-unique DMI vendor/model fields) |
| CPU | AMD Ryzen 5 3500U with Radeon Vega Mobile Gfx; 4 cores / 8 threads (`lscpu`) |
| Architecture | `x86_64` (`uname -m`) |
| Memory visible to Linux | 5,962,196 KiB, approximately 5.69 GiB (`MemTotal` in `/proc/meminfo`) |
| SSD | Samsung NVMe, model MZVLB256HAHQ-000H1; 238.5 GiB displayed capacity (`lsblk`) |

The SSD model is a product model, not a serial number. The observed Linux memory total differs from the owner-confirmed 8 GB installed capacity. TODO: verify the reason for the difference; no hardware reservation or memory fault is inferred from this check.

## Fedora development environment

Read-only checks on 2026-10-27 established:

| Item | Verified value and source |
| --- | --- |
| Hostname | `athena` (`hostname`) |
| Distribution | Fedora Linux 44 (Workstation Edition), stable (`/etc/os-release`) |
| Current kernel | `7.2.12-200.fc44.x86_64` (`uname -r`) |
| Linux username | `kkerns20` (`id -un`) |
| Home directory | `/home/kkerns20` (account database) |
| Default and active shell | `/bin/bash` in the account database; command-session parent process `bash` |
| Repository location | `/home/kkerns20/projects/linux-lab`, equivalent to `~/projects/linux-lab` (`pwd`) |

This session ran in the Fedora environment on hostname `athena`; no SSH session markers were present. This observation does not establish how every future administration session will connect.

### Storage and swap

The following layout was directly observed with `lsblk`, `findmnt`, and `swapon`. Sizes are rounded as displayed by the tools. Unique filesystem identifiers and encrypted mapper names are deliberately omitted.

| Device or mount | Observed layout |
| --- | --- |
| `/dev/nvme0n1` | 238.5 GiB NVMe SSD |
| `/dev/nvme0n1p1`, `/boot/efi` | 600 MiB EFI partition, VFAT |
| `/dev/nvme0n1p2`, `/boot` | 2 GiB boot partition, ext4 |
| `/dev/nvme0n1p3` | 235.9 GiB partition identified as `crypto_LUKS` |
| `/` | Btrfs root subvolume on the unlocked encrypted mapper |
| `/home` | Btrfs home subvolume on the same encrypted mapper |
| `/dev/zram0` | Approximately 5.7 GiB active compressed RAM swap, priority 100 |

The root and home filesystems are on encrypted storage; the separate EFI and boot partitions are not shown as LUKS-encrypted. TODO: document backup and recovery procedures and verify encryption parameters if needed through a separately authorized review. Do not publish encryption keys, recovery material, or unique volume identifiers.

### Development tools

Versions and executable locations were directly verified using version commands and executable lookup in the current Fedora environment:

| Tool | Version | Executable |
| --- | --- | --- |
| Git | 2.56.0 | `/usr/bin/git` |
| SSH client | OpenSSH 10.2p1; OpenSSL 3.5.9 | `/usr/bin/ssh` |
| Python | 3.14.8 | `/usr/bin/python3` |
| Codex CLI | 0.165.0 | `/home/kkerns20/.local/bin/codex` |

The Codex version check succeeded but warned that PATH aliases could not be created because of the read-only filesystem. No permissions, PATH settings, packages, or configurations were changed to resolve the warning.

## GitHub workflow

The checkout is at `~/projects/linux-lab`. The verified `origin` URL is `git@github.com:kkerns20/linux-lab.git`, which uses SSH transport. The owner confirms SSH authentication for GitHub. Live authentication, key registration, and key selection were not tested; an SSH remote URL alone does not verify access. No private keys or credential files were read.

The initial `git status --short` was empty before this documentation edit. Work from the Fedora checkout in Bash:

```bash
cd ~/projects/linux-lab
git status --short
git diff
```

Read the repository instructions before editing, preserve unrelated changes, and review the complete diff for sensitive content. Commit and push only when explicitly authorized. Detailed access procedures belong in [operations](../operations/README.md).

## Hardware testing and maintenance

Owner-confirmed on 2026-10-27; not independently retested in this session:

| Area | Owner-confirmed result |
| --- | --- |
| Wi-Fi | Tested and working |
| Touchscreen | Tested and working |
| Keyboard backlight | Tested and working |
| Trackpad | Tested and working |
| Audio | Tested and working |
| Video playback | Tested and working |
| Brightness controls | Tested and working |
| System updates | Completed |
| Firmware | `fwupdmgr` reported no available firmware updates |

These maintenance results record the owner's reported state, not a live guarantee that no newer updates exist. TODO: record test methods, maintenance execution dates, and sanitized validation evidence when available. No package installation, update transaction, firmware refresh, or system-service change was performed during this documentation work.

## Codex workflow and remaining documentation

From the Fedora repository directory, run `codex`. The repository-level [AGENTS.md](../../AGENTS.md) supplies shared instructions for scope, environment identification, documentation, validation, and Git actions. The CLI location and version were verified; authentication status was not inspected and remains TODO if needed.

For documentation changes, inspect the diff, check relative links, and run `git diff --check`. Leave changes unstaged for review unless staging is explicitly requested. Documentation authorization does not authorize configuration changes or remote administration.

TODO: document the Python project/virtual-environment workflow, approved SSH administration procedures, and tested backup and recovery procedures. Detailed operational instructions belong in [operations](../operations/README.md). Keep detailed YAMS documentation in the [YAMS repository](https://github.com/kkerns20/yams-media-server).

See the [device inventory](README.md) and [architecture](../architecture/README.md) for the broader lab context.
