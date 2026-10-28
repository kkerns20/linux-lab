# Home Lab architecture

## Current state

Source: owner-confirmed device inventory, 2026-10-27. This is a role overview, not a verified network topology.

- Atlas is the primary workstation, with Windows 11 and Ubuntu 24.04 WSL2.
- Hermes is the portable administration workstation.
- Hephaestus is the temporary Ubuntu server running Docker, YAMS, and Plex.
- Athena is the Fedora Linux development workstation.

Hardware and operating environment details belong in the [device inventory](../devices/README.md). Detailed YAMS architecture and configuration belong in the [YAMS repository](https://github.com/kkerns20/yams-media-server).

## Planned architecture

Olympus is the planned permanent server. The [home server roadmap](../../projects/home-server-roadmap.md) describes candidate hardware, storage growth, and migration from Hephaestus. Prometheus is a potential Raspberry Pi automation platform; no deployment is confirmed.

## TODO

- Document a sanitized network topology, connection types, and trust boundaries.
- Confirm administration paths and local versus remote execution contexts.
- Document service dependencies and storage boundaries without copying sensitive configuration.
- Verify current storage mount points and data flows before describing them as implemented.
- Record architecture decisions, constraints, alternatives, and validation evidence.
- Define Olympus and Prometheus requirements before choosing hardware or deployment designs.

See [operations](../operations/README.md) for runbook gaps and the [Solutions Engineering roadmap](../../projects/solutions-engineering-roadmap.md) for portfolio goals.
