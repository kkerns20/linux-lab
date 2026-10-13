# Home Lab

A hands-on infrastructure and Solutions Engineering portfolio built through real Linux, networking, self-hosting, automation, and troubleshooting projects.

This repository is not just a collection of installation notes. Each project is being documented around the same workflow used in customer-facing technical work:

**problem → requirements → constraints → design → implementation → validation → troubleshooting → lessons learned**

## Current environment

The lab currently includes an Ubuntu-based Linux system running containerized services, additional Windows hardware for administration and interoperability testing, and a separate laptop planned for alternate-Linux testing.

The current server work includes:

- Ubuntu Linux administration
- Docker and Docker Compose
- persistent storage under `/srv/media`
- Linux users, groups, ownership, and permissions
- SSH and remote administration
- VPN-isolated container networking with Gluetun + WireGuard
- service troubleshooting and health validation
- home networking, switching, DNS, and wired-vs-wireless design
- backup, monitoring, UPS, and reliability planning

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
- observability and incident response
- small-business and customer-solution case studies
- technical demos and executive-level solution summaries

The objective is to build enough technical depth to design and troubleshoot credible solutions while also demonstrating the communication, analysis, and systems thinking expected in Solutions Engineering roles.
