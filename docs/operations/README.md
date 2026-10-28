# Home Lab operations

## Scope and current status

This directory holds sanitized administration and recovery runbooks. The [Athena-to-Hephaestus SSH exercise](ssh-athena-hephaestus.md) was successfully completed on October 28, 2026 according to owner-provided command results. Its tested scope covers reachability, host identity, dedicated-key authorization/login, remote identity checks, and safe disconnection. Codex did not execute the exercise; recovery, backup restoration, and broader hardening remain untested. Current device facts are in the [inventory](../devices/README.md); design context is in [architecture](../architecture/README.md).

Detailed Docker/YAMS/Plex deployment and troubleshooting documentation belongs in the [YAMS repository](https://github.com/kkerns20/yams-media-server). Link to relevant procedures rather than copying sensitive configuration here.

## Runbook backlog

| Procedure | Status and missing information |
| --- | --- |
| Device access and administration | [Athena-to-Hephaestus SSH](ssh-athena-hephaestus.md): owner-tested 2026-10-28; other access paths, recovery, and broader administration TODO |
| Service inventory and health checks | [Hephaestus inventory](../devices/hephaestus.md#container-inventory) recorded from owner-provided 2026-10-28 results; dependencies, versions, and application-level checks TODO |
| Backup and restore | TODO: define scope, destination, retention, access controls, and restore validation |
| Startup and recovery | TODO: document observed reboot behavior and tested recovery steps |
| Storage management | TODO: verify mount layout, capacity checks, permissions, and recovery approach |
| Monitoring and incident response | TODO: define signals, alerting, triage, and incident records |
| Maintenance and updates | TODO: define maintenance windows, compatibility checks, and rollback |
| SSH exposure and CPU security review | TODO: review Hephaestus SSH source restrictions/IPv4/IPv6 exposure and the reported Gather Data Sampling/microcode condition; see [device security findings](../devices/hephaestus.md#networking-and-ssh-security) |
| Hephaestus-to-Olympus migration | Planned: follow the [server roadmap](../../projects/home-server-roadmap.md); execution and validation TODO |

## Runbook standard

Each runbook should state its target device and environment, purpose, prerequisites, authorization needed, expected impact, steps, validation, rollback or recovery, and last-tested date. Label untested procedures explicitly. Never include credentials, private keys, serial numbers, personal files, or VPN configuration details.

Documentation work does not authorize service changes, package installation, storage operations, or remote administration.
