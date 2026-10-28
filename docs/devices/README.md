# Home Lab device inventory

Current specifications below were confirmed by the owner on 2026-10-27. They have not been independently inspected during documentation work. Device names are lab labels; DNS names and network configuration are TODO.

## Current devices

| Device | Hardware | Operating environment | Role |
| --- | --- | --- | --- |
| [Atlas](atlas.md) | Gigabyte AERO X16; Ryzen AI 7 350; RTX 5070 Laptop GPU; 32 GB RAM; 1 TB NVMe | Windows 11; Ubuntu 24.04 WSL2; Codex CLI | Primary workstation |
| [Hermes](hermes.md) | Surface Pro 7; Core i5-1035G4; 8 GB RAM; 128 GB SSD | Windows 11 Home 26H2 | Portable administration workstation |
| [Hephaestus](hephaestus.md) | Dell Latitude 7480; Core i5-6300U; 16 GB RAM; 512 GB SSD | Ubuntu 26.04.1 LTS; Docker; YAMS; Plex | Current temporary server |
| [Athena](athena.md) | HP Envy x360 15m-ds0xxx; Ryzen 5 3500U; 8 GB RAM; 256 GB SSD | Fedora Workstation 44; encrypted Btrfs; Git; SSH; Codex CLI 0.165.0 | Linux development workstation |

## Planned infrastructure

| Name | Status | Intended role |
| --- | --- | --- |
| Olympus | Planned; hardware and deployment TODO | Permanent Home Lab server; see the [server roadmap](../../projects/home-server-roadmap.md) |
| Prometheus | Potential; adoption and hardware TODO | Raspberry Pi automation platform |

These planned systems are not documented as deployed. Future automation and monetization experiments remain exploratory; scope, validation, costs, and success criteria are TODO.

## Documentation conventions

Each device page records confirmed facts, administration context, and missing details. Keep sensitive identifiers and configuration out of this inventory. Record future verification dates and sources when facts change.

See the [architecture overview](../architecture/README.md), [operations overview](../operations/README.md), and [Home Lab overview](../../README.md).
