# Atlas

## Role and status

Atlas is the primary workstation for Project Olympus: the development and documentation environment used to prepare the permanent Home Lab server project. Olympus remains a planned server; Hephaestus continues as the temporary Docker/YAMS/Plex server until migration is validated. See the [home server roadmap](../../projects/home-server-roadmap.md) for requirements and migration plans.

Sources and verification date: owner-confirmed configuration and read-only inspection of the Ubuntu WSL2 environment on 2026-10-27. Hardware and Windows settings were not inspected live. Verified Linux details below describe this session, not a Windows installation of the same tools.

## Confirmed specifications

Owner-confirmed on 2026-10-27:

| Item | Value |
| --- | --- |
| Model | Gigabyte AERO X16 |
| CPU | AMD Ryzen AI 7 350 |
| GPU | NVIDIA RTX 5070 Laptop GPU |
| RAM | 32 GB |
| Storage | 1 TB NVMe SSD |
| Operating environments | Windows 11 primary OS; Ubuntu 24.04 LTS through WSL2 |

## Windows host environment

Windows 11 is the primary host operating system. The following are owner-confirmed, not live-verified:

- GiMATE manages laptop performance, cooling, and hardware settings.
- A Dell D6000 dock with DisplayLink supports external displays.

TODO: verify the Windows version/build, GiMATE and DisplayLink versions, and active dock/display configuration before troubleshooting host hardware. Linux tool checks do not establish that corresponding Windows tools are installed.

## Remote access from iPhone (owner-tested 2026-11-03)

An iPhone running Tailscale and Termius successfully connected **over cellular** to the Atlas **Windows** OpenSSH server using a dedicated ED25519 SSH key, then launched the existing Ubuntu WSL2 Bash environment. Windows and Linux account/hostname checks succeeded. This path reaches Windows first; it is not a direct WSL2 SSH listener or an independently configured connection to Hephaestus.

The default OpenSSH inbound firewall allowance was disabled and replaced by a TCP/22 rule restricted to the Tailscale interface (interface filter confirmed by owner). The Windows administrator authorized-keys file was verified to allow only SYSTEM and Administrators. Windows SSH and Tailscale services both showed **Running / Automatic**, but a post-reboot reconnect has not been tested. Full effective firewall coverage, effective password-authentication settings, and SSH host-key fingerprint comparison remain unverified.

The owner elected to retain normal laptop sleep: **30 minutes on AC and 5 minutes on battery**, rather than leaving Atlas awake indefinitely. The AC setting was temporarily changed to Never for testing, then restored by owner report (no subsequent readback). Lid-close action remains unverified. Consequently, remote access works only when Atlas is powered on, awake, and connected.

See the [owner-tested iPhone/Tailscale/Windows SSH runbook](../operations/ssh-iphone-atlas-tailscale.md) for sanitized setup history, validation, troubleshooting, security limits, and recovery. No private network addresses, login names, or SSH keys are stored in this repository.

## Ubuntu WSL2 development environment

Read-only checks on 2026-10-27 established:

| Item | Verified value and source |
| --- | --- |
| Hostname | `Atlas` (`hostname`) |
| Distribution | Ubuntu 24.04.5 LTS, Noble (`/etc/os-release`) |
| WSL status | WSL2 kernel `6.18.54.1-microsoft-standard-WSL2` (`uname -r`) |
| Linux username | `kkerns20` (`id -un`) |
| Home directory | `/home/kkerns20` (Linux account database) |
| Default and active shell | `/bin/bash` in the account database; active process `bash` |
| Repository location | `/home/kkerns20/projects/linux-lab` (`pwd`) |
| Git | 2.43.0 (`git --version`) |
| Codex CLI | 0.165.0 (`codex --version`) |
| Codex executable | `/home/kkerns20/.local/bin/codex` (`command -v codex`) |
| Windows drive mount | `/mnt/c`, filesystem type `9p` (`findmnt`) |

This session ran inside Ubuntu WSL2 on hostname Atlas; no SSH session markers were present. Windows-side WSL distribution registration and settings were not inspected. TODO: verify those separately if needed for WSL troubleshooting.

The Codex version check succeeded but reported that PATH aliases could not be created because of the read-only filesystem. No permission or PATH changes were made to resolve that warning.

### Windows and Linux paths

Windows paths use drive letters and backslashes, such as `C:\`. Within this WSL environment, the Windows C: drive is mounted at `/mnt/c/`; a Windows path such as `C:\Users\` corresponds to `/mnt/c/Users/` in Linux.

The repository is in the Linux home filesystem at `/home/kkerns20/projects/linux-lab`, not under `/mnt/c/`. Linux `~` refers to `/home/kkerns20`, not the Windows user profile. Use Linux paths and Linux tools when working in Ubuntu; identify the target environment before using Windows commands, paths, or installers.

## GitHub workflow

The verified `origin` fetch and push remote is `git@github.com:kkerns20/linux-lab.git`. The initial `git status --short` was empty before this documentation edit.

A public key exists at `/home/kkerns20/.ssh/id_ed25519.pub`, and its type was verified as `ssh-ed25519` without displaying the key material. The owner confirms a dedicated Ed25519 key for GitHub authentication. Key registration, key selection, and live GitHub authentication were not tested; public-key presence alone does not verify access. No private keys or credential files were read.

Work from the Linux checkout in Bash:

```bash
cd /home/kkerns20/projects/linux-lab
git status --short
git diff
```

Read the repository instructions before editing, preserve unrelated changes, and review the complete diff for sensitive content. Commit and push only when explicitly authorized; no commit or push was performed for this update. Detailed access procedures belong in [operations](../operations/README.md).

## Codex workflow

The owner confirms Codex CLI is installed and authenticated within Ubuntu WSL2. Installation location and version were verified above; authentication was not independently tested or inspected.

From the Linux repository directory, run `codex`. The repository-level [AGENTS.md](../../AGENTS.md) supplies shared instructions for scope, environment identification, documentation, validation, and Git actions. Keep each task explicit about whether it permits review, file edits, or host administration; documentation authorization does not authorize configuration changes or remote administration.

For documentation changes, inspect the diff, check relative links, and run `git diff --check`. Leave changes unstaged for review unless staging is explicitly requested. Full operational procedures belong in [operations](../operations/README.md); detailed YAMS documentation remains in the [YAMS repository](https://github.com/kkerns20/yams-media-server).

See the [device inventory](README.md) and [architecture](../architecture/README.md) for the broader lab context.
