# Home Lab HQ — Project Olympus status

**Last updated:** 2026-10-28. **Last verified:** 2026-10-28, limited to repository/history review and current Athena session identity and OS. Earlier device inspections are dated 2026-10-27; this is not a fleet health check.

Start here for new ChatGPT conversations and Codex sessions, then read [repository instructions](../AGENTS.md) and the relevant authoritative documents below. Home Lab HQ is the central planning and documentation workflow for Project Olympus. See the [decision log](DECISIONS.md) and [chronological work log](WORK-LOG.md) for context.

Evidence labels: **Observed** means directly checked in this session; **Recorded inspection** means evidence documented in an earlier device page; **Owner-reported** means supplied by the owner without independent retesting; **Planned** means future work. TODO marks missing facts. Owner updates below were received on 2026-10-28; underlying execution dates are TODO unless separately documented.

## Current fleet

| Device and authoritative page | OS / environment | Assigned role and evidence |
| --- | --- | --- |
| [Atlas](devices/atlas.md) | Windows 11; Ubuntu 24.04 WSL2; Codex CLI | Primary development and documentation workstation. Owner-reported 2026-10-28; WSL2 development environment has a recorded inspection dated 2026-10-27. Windows host settings were not live-inspected. |
| [Athena](devices/athena.md) | Fedora Workstation 44; LUKS-encrypted Btrfs; Git/SSH/Codex CLI | Linux development and learning workstation. Owner-reported 2026-10-28; recorded storage/tool inspection 2026-10-27. Fedora 44 and hostname observed 2026-10-28; encryption and authentication were not retested. |
| [Hermes](devices/hermes.md) | Windows 11 Home 26H2 | Portable administration workstation. Fresh installation, activation, and departure from Insider Program are owner-reported 2026-10-28; no live inspection. |
| [Hephaestus](devices/hephaestus.md) | Ubuntu 26.04.1 LTS; Docker/YAMS/Plex | Temporary server, owner-reported as continuing in this role on 2026-10-28. Exact OS version comes from the 2026-10-27 inventory; no live inspection. |

Hardware specifications remain in the [device inventory](devices/README.md) and individual device pages.

## Future infrastructure

| System | Status and authoritative plan |
| --- | --- |
| Olympus | **Planned, not deployed**, reaffirmed by owner 2026-10-28. Permanent wired, expandable server; hardware selection and migration validation remain TODO in the [home server roadmap](../projects/home-server-roadmap.md). |
| Prometheus | **Potential, not deployed in the documentation.** Raspberry Pi automation platform; adoption, hardware, and workloads TODO in the [inventory](devices/README.md#planned-infrastructure) and [roadmap](../projects/home-server-roadmap.md#related-future-infrastructure). |

## Completed milestones

- **Documentation recorded in Git:** initial lab/YAMS links (2026-09-30), server roadmap (2026-10-01), Solutions Engineering portfolio roadmap (2026-10-12), device inventory and Codex instructions (2026-10-27), and Atlas/Athena development environment documentation (2026-10-27). Commit references are in the [work log](WORK-LOG.md). These dates establish documentation milestones, not deployment dates.
- **Owner-reported 2026-10-28:** Athena runs Fedora 44 with LUKS, working GitHub SSH authentication, and Codex CLI. Its NetworkManager Wi-Fi connection profile now uses firewalld's `public` zone with incoming SSH permission removed; the owner reports verification after reboot. See [Athena](devices/athena.md#firewall-posture).
- **Owner-reported 2026-10-28:** Atlas runs Windows 11 with Ubuntu WSL2 and Codex, with its development environment documented; Hermes has a fresh, activated Windows 11 Home 26H2 installation and is no longer enrolled in Insider. See their device pages for evidence limits.

## Active projects and upcoming work

| Workstream | Status and next deliverable |
| --- | --- |
| Home Lab HQ | Ongoing documentation system. Maintain status, decisions, and work log after significant sessions and refresh ChatGPT Home Lab Project reference snapshots after significant GitHub documentation updates; maintenance rules are in [AGENTS.md](../AGENTS.md#home-lab-hq-maintenance). |
| Home infrastructure / Project Olympus | Active foundation and planning work. Hephaestus remains temporary; Olympus migration is planned. See the [server roadmap](../projects/home-server-roadmap.md). |
| YAMS media environment | Running on Hephaestus per owner; current service inventory and health remain unverified. Detailed technical work belongs in the [YAMS repository](https://github.com/kkerns20/yams-media-server). |
| Networking, backups, and service inventory | Upcoming, reaffirmed by owner 2026-10-28. Sanitized topology, approved access paths, backup/restore runbook, and verified service list are TODO in [architecture](architecture/README.md) and [operations](operations/README.md). |
| Solutions Engineering portfolio | Infrastructure foundation underway; API, data, cloud, identity, and customer case studies remain planned in the [six-phase roadmap](../projects/solutions-engineering-roadmap.md). Future automation and monetization experiments remain exploratory. |

## Known issues, blockers, and unresolved questions

- **Athena memory:** owner reports two 4 GiB modules but approximately 5.7 GiB usable. The 2026-10-27 recorded inspection showed approximately 5.69 GiB visible to Linux. A substantial firmware reservation is owner-reported; its exact purpose is unresolved. TODO: establish cause using sanitized evidence; do not assume a graphics allocation or memory fault. Details: [Athena](devices/athena.md#directly-verified-hardware).
- **YAMS troubleshooting:** the [server roadmap](../projects/home-server-roadmap.md#immediate-next-work) notes a prior Sonarr/Radarr automatic download/import issue. TODO: ask whether it remains open before treating it as a current fault.
- **Migration readiness:** no verified service/storage inventory or tested backup/restore procedure is established here. Olympus hardware, budget, and final design remain TODO. These are prerequisites to a reviewable migration plan; migration execution and recovery tests have not been completed in this repository.
- **Evidence gaps:** Athena firewall/reboot and GitHub authentication reports, Hermes activation/Insider status, and current Hephaestus health have not been independently verified. Atlas Windows build and Hermes administration tooling remain TODO. Historical Codex PATH warnings on Atlas/Athena are recorded; current recurrence was not checked.

## Prioritized next actions

1. **P1 — Review Home Lab HQ:** owner reviews documentation changes and confirms missing execution dates or decision rationale where known. Owner approval is required before any Git commit or push; do not invent missing history.
2. **P1 — Synchronize the ChatGPT Home Lab Project:** refresh its reference files from the authoritative GitHub documentation. Project reference files are snapshots and must be refreshed after significant GitHub documentation updates; record the source revision and refresh date to make their currency clear.
3. **P1 — Establish the current baseline:** document sanitized networking, access paths, storage, deployed services, dependencies, and health evidence in [architecture](architecture/README.md) and [operations](operations/README.md). Confirm the YAMS import issue's status. Any remote inspection or host administration needs explicit authorization.
4. **P1 — Plan and validate backups:** define scope, destination, retention, recovery requirements, and rollback before any migration or storage change. Restore testing is future work requiring an approved procedure; record results only after execution.
5. **P2 — Resolve workstation evidence gaps:** clarify Athena's firmware reservation and obtain dated firewall/reboot evidence; confirm Hermes build, activation/enrollment evidence, and administration tools. Keep detailed findings in device pages and procedures in operations.
6. **P2 — Define Olympus requirements:** after inventory and backup planning, confirm workload capacity, budget, candidate hardware, storage design, migration acceptance criteria, and recovery approach in the [server roadmap](../projects/home-server-roadmap.md). No purchase or deployment is implied.
7. **P3 — Extend the portfolio:** progress through the [Solutions Engineering roadmap](../projects/solutions-engineering-roadmap.md); scope Prometheus, automation, and monetization experiments with costs and success criteria before implementation.
