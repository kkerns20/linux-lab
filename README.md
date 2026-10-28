# Home Lab

A hands-on infrastructure and Solutions Engineering portfolio built through real Linux, networking, self-hosting, automation, and troubleshooting projects.

This repository is not just a collection of installation notes. Each project is being documented around the same workflow used in customer-facing technical work:

**problem → requirements → constraints → design → implementation → validation → troubleshooting → lessons learned**

## Current environment

Current device specifications were confirmed by the owner on 2026-10-27:

- **Atlas** — Gigabyte AERO X16; Windows 11 with Ubuntu 24.04 WSL2; primary workstation.
- **Hermes** — Microsoft Surface Pro 7; Windows 11 Home 26H2; portable administration workstation.
- **Hephaestus** — Dell Latitude 7480; Ubuntu 26.04.1 LTS; current temporary Docker/YAMS/Plex server.
- **Athena** — HP Envy x360; Fedora Workstation 44 with encrypted Btrfs; Linux development workstation.

**Olympus** is the planned permanent Home Lab server. **Prometheus** is a potential Raspberry Pi automation platform. Neither is documented as deployed.

## Documentation

- [Home Lab HQ: project status and next actions](docs/PROJECT-STATUS.md) — start here for a new ChatGPT conversation or Codex session.
- [Architectural decision log](docs/DECISIONS.md)
- [Work log and session template](docs/WORK-LOG.md)
- [Device inventory and specifications](docs/devices/README.md)
- [Architecture overview and TODOs](docs/architecture/README.md)
- [Operations and runbook backlog](docs/operations/README.md)
- [Codex repository instructions](AGENTS.md)

Current work centers on Linux administration, Docker, persistent storage, permissions, remote administration, and service troubleshooting. Backup, monitoring, UPS, storage expansion, and migration remain planning areas unless documented with validation evidence. Detailed YAMS documentation stays in its separate repository.

## Featured projects

### [YAMS Media Server](https://github.com/kkerns20/yams-media-server)
A containerized media environment used to learn Docker architecture, persistent storage, VPN routing, service dependencies, troubleshooting, and secure handling of secrets.

### [Home Server Roadmap](projects/home-server-roadmap.md)
Hardware, storage, migration, and reliability planning for moving from an experimental Linux machine toward an intentional always-on home server.

### [Solutions Engineering Roadmap](projects/solutions-engineering-roadmap.md)
A six-month portfolio plan connecting the Home Lab to customer discovery, architecture, APIs, cloud, data analysis, demos, and technical solution design.

## How projects are documented

For portfolio-grade projects, I aim to capture:

1. **Problem** — What needs to be solved?
2. **Requirements** — What must the solution do?
3. **Constraints** — Budget, hardware, security, performance, or operational limits.
4. **Options considered** — What alternatives were evaluated?
5. **Architecture** — How the components fit together.
6. **Implementation** — Commands, configuration, and deployment.
7. **Validation** — How the solution was tested.
8. **Troubleshooting** — Failures, diagnosis, root cause, and resolution.
9. **Tradeoffs** — What was gained or sacrificed by the chosen design?
10. **Communication** — How the solution would be explained to a technical or business audience.

## Skills being developed

`Linux` `Docker` `Networking` `DNS` `VPNs` `SSH` `Storage` `Git/GitHub` `Bash` `Python` `APIs` `SQL` `Monitoring` `Cloud Fundamentals` `Architecture` `Technical Documentation`

## Long-term direction

The lab will expand into projects that demonstrate not only infrastructure administration, but also the ability to translate requirements into working technical solutions. Planned areas include:

- REST APIs, HTTP, JSON, authentication, and webhooks
- Python automation and data analysis
- cloud deployment and architecture
- identity, SSO, OAuth/OIDC, and role-based access
- infrastructure automation
- exploratory automation and monetization experiments (scope and validation TODO)
- observability and incident response
- small-business and customer-solution case studies
- technical demos and executive-level solution summaries

The objective is to build enough technical depth to design and troubleshoot credible solutions while also demonstrating the communication, analysis, and systems thinking expected in Solutions Engineering roles.
