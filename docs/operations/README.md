# Home Lab operations

## Scope and current status

This directory will hold sanitized administration and recovery runbooks. No completed or tested operational procedure is established by this introductory page. Current device facts are in the [inventory](../devices/README.md); design context is in [architecture](../architecture/README.md).

Detailed Docker/YAMS/Plex deployment and troubleshooting documentation belongs in the [YAMS repository](https://github.com/kkerns20/yams-media-server). Link to relevant procedures rather than copying sensitive configuration here.

## Runbook backlog

| Procedure | Status and missing information |
| --- | --- |
| Device access and administration | TODO: confirm shell, execution context, prerequisites, and approved access methods |
| Service inventory and health checks | TODO: confirm deployed services, dependencies, and safe checks |
| Backup and restore | TODO: define scope, destination, retention, access controls, and restore validation |
| Startup and recovery | TODO: document observed reboot behavior and tested recovery steps |
| Storage management | TODO: verify mount layout, capacity checks, permissions, and recovery approach |
| Monitoring and incident response | TODO: define signals, alerting, triage, and incident records |
| Maintenance and updates | TODO: define maintenance windows, compatibility checks, and rollback |
| Hephaestus-to-Olympus migration | Planned: follow the [server roadmap](../../projects/home-server-roadmap.md); execution and validation TODO |

## Runbook standard

Each runbook should state its target device and environment, purpose, prerequisites, authorization needed, expected impact, steps, validation, rollback or recovery, and last-tested date. Label untested procedures explicitly. Never include credentials, private keys, serial numbers, personal files, or VPN configuration details.

Documentation work does not authorize service changes, package installation, storage operations, or remote administration.
