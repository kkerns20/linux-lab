# Home Lab work log

**Last updated:** 2026-10-28. Append meaningful work chronologically. Historical entries below were reconstructed from local Git history and current documents; commit dates establish documentation changes, not installation or test execution dates. Historical validation statements describe what those documents record, not checks repeated today.

Owner reports are labeled separately. When an execution date is unknown, use the report date and mark the execution date TODO. Never fill gaps with assumed commands, terminal output, or test results. See [current status](PROJECT-STATUS.md), [decisions](DECISIONS.md), and [repository instructions](../AGENTS.md).

## 2026-09-30 — Repository foundation

- **Device:** TODO; execution device not recorded.
- **Objective:** Establish the Home Lab documentation repository and connect the YAMS project.
- **Work completed:** Initial repository README and lab introduction; linked the separate YAMS media server repository.
- **Validation performed:** Git history records the documentation changes. No host or service test evidence is established by these commits.
- **Problems and lessons:** Problems TODO; preserve the distinction between documentation history and deployed state.
- **References:** `f461cc5`, `99747a7`, `89b85d2`; [Home Lab overview](../README.md).
- **Next action at that point:** Document the server direction; captured in the 2026-10-01 roadmap.

## 2026-10-01 — Permanent server and storage roadmap

- **Device:** Temporary Dell server discussed; execution device TODO.
- **Objective:** Plan a permanent wired server and expandable storage.
- **Work completed:** Added the hardware/storage roadmap and linked it from the README. The direction later became the named Hephaestus-to-Olympus migration.
- **Validation performed:** Git history records a plan; no hardware purchase, deployment, migration, or recovery test is established.
- **Problems and lessons:** Roadmap identifies laptop form factor, capacity, and storage expansion constraints. Later documentation marks unverified hardware details and candidate pricing as TODO.
- **References:** `30f26ef`, `cc8373f`; [current server roadmap](../projects/home-server-roadmap.md).
- **Next action:** Verify the current host and requirements before hardware selection or migration.

## 2026-10-12 — Solutions Engineering portfolio direction

- **Device:** TODO; execution device not recorded.
- **Objective:** Connect lab work to customer-facing technical skills and portfolio evidence.
- **Work completed:** Reframed the README and added the six-phase Solutions Engineering roadmap, including APIs, data, cloud, identity, and a customer solution case study.
- **Validation performed:** Git history establishes documentation additions; it does not establish completed portfolio implementations.
- **Problems and lessons:** The roadmap requires requirements, tradeoffs, validation, troubleshooting, and communication evidence beyond a working demonstration.
- **References:** `d732fbf`, `8709444`; [Solutions Engineering roadmap](../projects/solutions-engineering-roadmap.md).
- **Next action:** Build the infrastructure foundation and collect evidence against the portfolio standard.

## 2026-10-27 — Fleet inventory and repository workflow

- **Device:** Atlas, Athena, Hermes, and Hephaestus documented; execution device TODO.
- **Objective:** Establish current roles, planned infrastructure, and safe documentation practices.
- **Work completed:** Added device pages, architecture and operations overviews, and repository `AGENTS.md`; updated README and server roadmap. Distinguished planned Olympus and potential Prometheus from the current fleet.
- **Validation performed:** Device specifications in this change are labeled owner-confirmed, without independent live inspection. Git records the documentation changes; no completed operations runbook is established.
- **Problems and lessons:** Networking, service/storage inventory, backups, access methods, and recovery evidence remain incomplete; unverified details must stay TODO.
- **References:** `8c008a2`; [inventory](devices/README.md), [architecture](architecture/README.md), [operations](operations/README.md).
- **Next action at that point:** Document Atlas and Athena development contexts, recorded in the following entries.

## 2026-10-27 — Atlas WSL2 development environment

- **Device:** Atlas, Ubuntu WSL2 context.
- **Objective:** Document the primary workstation's Linux development and Codex workflow.
- **Work completed:** Recorded WSL2 OS/kernel, shell, checkout path, tools, Windows/Linux path differences, and GitHub/Codex workflow.
- **Validation performed:** The device page records read-only Linux environment and tool checks on this date. Windows hardware/settings and live GitHub/Codex authentication were not independently tested.
- **Problems and lessons:** Codex version check reported inability to create PATH aliases in a read-only filesystem. No corrective configuration was applied. WSL observations do not verify Windows-side tools.
- **References:** `f90f1a7`; [Atlas](devices/atlas.md).
- **Next action:** Verify Windows build and host details separately when needed; document approved access and backup procedures.

## 2026-10-27 — Athena Fedora development environment

- **Device:** Athena, Fedora context.
- **Objective:** Document the Linux development workstation and distinguish observations from owner reports.
- **Work completed:** Recorded hardware observations, Fedora environment, LUKS/Btrfs storage, zram swap, development tools, and GitHub/Codex workflow. Preserved owner-reported hardware interaction and maintenance results.
- **Validation performed:** The device page records read-only hardware, OS, storage, swap, and tool checks on this date. Authentication, hardware interaction tests, updates, and firmware checks were not repeated during that session.
- **Problems and lessons:** Linux exposed approximately 5.69 GiB despite owner-confirmed 8 GB installed. Cause remained unresolved. Codex also reported the read-only PATH-alias warning; no host changes were made.
- **References:** `6dd935d`; [Athena](devices/athena.md).
- **Next action:** Clarify the memory discrepancy and document Python, access, backup, and recovery workflows.

## 2026-10-28 — Owner-reported fleet updates

- **Device:** Athena, Atlas, Hermes, and Hephaestus; Olympus discussed as future infrastructure.
- **Objective:** Capture recent owner reports for session continuity. **Execution dates: TODO; this is the report-received date.**
- **Work completed, per owner:** Athena runs Fedora 44 with LUKS, working GitHub SSH authentication, and Codex CLI. Its NetworkManager Wi-Fi connection uses firewalld's `public` zone with incoming SSH permission removed. Two 4 GiB modules are installed but approximately 5.7 GiB is usable; a substantial firmware reservation was observed. Atlas runs Windows 11 with Ubuntu WSL2 and Codex, with its development environment documented. Hermes has a fresh activated Windows 11 Home 26H2 installation and is no longer enrolled in Insider. Hephaestus continues as the temporary Ubuntu Docker/YAMS/Plex server. Olympus remains planned; networking, backups, and service inventory remain upcoming.
- **Validation performed:** Owner reports Athena's firewall change was verified after reboot and GitHub SSH authentication works. These results, module/reservation observations, and Hermes activation/enrollment state were not independently retested during this documentation session. Earlier documented inspection evidence remains separately dated.
- **Problems and lessons:** Firmware reservation purpose remains unresolved; do not infer a specific cause or treat owner-reported tests as independently observed.
- **References:** Owner's 2026-10-28 request; [Athena](devices/athena.md), [Atlas](devices/atlas.md), [Hermes](devices/hermes.md), [Hephaestus](devices/hephaestus.md), [current status](PROJECT-STATUS.md). No implementation commit supplied for these reports.
- **Next action:** Obtain missing execution dates and sanitized evidence when available; prioritize inventory and backup planning.

## 2026-10-28 — Home Lab HQ documentation draft

- **Device:** Current command environment reports hostname `athena`, Fedora 44, Bash, and `/home/kkerns20/projects/linux-lab`; no SSH or WSL markers were present. A local Fedora context is indicated; connection method is not conclusively established.
- **Objective:** Establish a concise status entry point, ongoing decision log, and meaningful work history for Project Olympus.
- **Work completed:** Read repository instructions, README, all device pages, architecture/operations documentation, both roadmaps, and Git history. Created the three master documents, linked them from README, updated Codex reading/maintenance guidance, and added dated owner reports to Athena/Hermes pages. Status: draft awaiting owner review.
- **Validation performed:** Initial Git status was clean. Read-only session checks confirmed hostname, Fedora 44, kernel `7.2.13-200.fc44.x86_64`, Bash, and working directory. Reviewed the full documentation diff, including new files; checked 105 relative Markdown links and heading fragments across 14 Markdown files with no missing targets. `git diff --check` passed; new files were also checked for whitespace errors. External URL reachability was not tested. No fleet health, firewall, authentication, activation, or recovery tests were run.
- **Problems and lessons:** Adoption/execution dates and some original decision rationales are unavailable. Keep report dates, documentation commits, recorded inspections, and current observations distinct.
- **References:** [Current status](PROJECT-STATUS.md), [decisions](DECISIONS.md), [repository instructions](../AGENTS.md). No commit; changes remain unstaged for review.
- **Next action:** Owner reviews the draft; then proceed through the [prioritized actions](PROJECT-STATUS.md#prioritized-next-actions) within explicitly authorized scope.

## 2026-10-28 — Home Lab HQ established

- **Date and device:** Establishment and owner report dated 2026-10-28. Documentation update performed on Atlas: observed hostname `Atlas`, Ubuntu 24.04.5 LTS, WSL2 kernel, Bash, and `/home/kkerns20/projects/linux-lab`. WSL markers were present and SSH session markers absent; the connection method is not conclusively established. Athena synchronization is owner-reported, not a remote inspection.
- **Objective:** Record successful Home Lab HQ establishment and completed synchronization; update current priorities within documentation-only scope.
- **Work completed — Git evidence:** Baseline commit `ec75e06` (`docs: establish Home Lab HQ project tracking and documentation workflow`) is dated 2026-10-28. Before this edit, Atlas's `HEAD`, `main`, and cached `origin/main` all pointed to it and the working tree was clean. The owner reports that this baseline was published to GitHub and that Athena and Atlas synchronized with `origin/main`. Local Git state corroborates Atlas's baseline; it does not independently prove Athena's state or current GitHub state.
- **Work completed — owner-reported ChatGPT actions:** Home Lab Project instructions were updated. `PROJECT-STATUS.md`, `DECISIONS.md`, and `WORK-LOG.md` were uploaded as shared Project sources. A separate Home Lab conversation successfully accessed and summarized those sources. These actions establish the reported Project workflow; they were not independently inspected in this repository session.
- **Work completed — documentation:** Updated [current status](PROJECT-STATUS.md) to record the milestone and shift priorities to infrastructure inventory, backups, evidence gaps, and Olympus planning. Preserved the historical documentation draft entry above.
- **Validation performed:** Reviewed repository instructions, status, work log, README, decisions, relevant workstation pages, and architecture/operations context. Inspected local Git status, history, baseline commit, remote configuration, and cached tracking refs. A read-only `git ls-remote origin refs/heads/main` attempt failed because `github.com` could not be resolved; live publication verification remains unavailable in this session. Checked relative Markdown links and heading fragments in both changed documents, reviewed the diff, and ran `git diff --check` successfully. No ChatGPT source-access test, Athena inspection, fleet health check, or recovery test was independently run here.
- **Problems and lessons:** GitHub remains authoritative under [D-006](DECISIONS.md#d-006--github-documentation-source-of-truth). Shared Project sources are snapshots requiring refresh after significant GitHub documentation updates; record the source revision and refresh date on refresh. Local tracking refs are cached evidence, and owner-reported ChatGPT actions must remain distinct from Git-verifiable facts.
- **References:** Baseline `ec75e06`; owner's 2026-10-28 establishment report; [current status](PROJECT-STATUS.md), [decisions](DECISIONS.md), [repository instructions](../AGENTS.md). This follow-up update is uncommitted and unstaged for review; no commit, push, or system configuration change was performed.
- **Next action:** Review this update, then prioritize sanitized infrastructure inventory and backup/restore planning through the [current next actions](PROJECT-STATUS.md#prioritized-next-actions). Refresh shared Project snapshots after significant authorized GitHub documentation updates.

## 2026-10-28 — Hephaestus inventory and successful SSH administration

- **Date and device:** Owner's exercise and inventory dated 2026-10-28: Athena (Fedora 44) as SSH client; Hephaestus (Ubuntu 26.04.1 LTS) as server. Documentation prepared in an observed Athena Fedora/Bash context. No Hephaestus inspection or administration was performed by Codex.
- **Objective:** Record the successful access exercise and a sanitized infrastructure baseline for Project Olympus, preserving application-health, recovery, and security evidence limits.
- **Work completed — owner-provided evidence:** Host-key fingerprints compared exactly through network and direct-server paths; dedicated ED25519 user identity enrolled while preserving previous authorizations; client/server file permissions, authorization-file backup comparison, and exact new-entry match verified. Dedicated-key login, remote hostname/account checks, and return to Athena succeeded. The owner also supplied system/memory/storage, container, networking/security, maintenance, and terminal-appearance results; details remain in the authoritative documents below.
- **Work completed — documentation:** Expanded the Hephaestus device page, added the SSH runbook, linked Athena's workflow and the operations index, and refreshed the status/next actions. Existing architectural decisions were preserved without adding unsupported rationale or adoption dates. The pre-existing local SSH exercise handoff is a related planning artifact, retained unchanged and excluded from the documentation commit.
- **Validation performed — exercise:** The owner verified client/server readiness, route/ping, host identity, key enrollment/permissions, authorization backup comparison, authentication, remote identity, and logout. Ten running containers and Gluetun's healthy Docker check were reported; these do not prove all applications function. Recovery, backup restoration, broader security hardening, and fresh-terminal prompt persistence were not tested in the supplied results.
- **Validation performed — documentation:** Fetched `origin/main` and confirmed local `main` matched it before editing; no fast-forward merge was needed. Reviewed the complete intended diff, including the new runbook; `git diff --check` passed, 130 relative Markdown links/heading references across 16 files resolved, and privacy/scope review found only the six intended documentation changes. The related untracked handoff was preserved. Owner-provided October 28 results were not represented as independently executed Codex checks. No SSH service, firewall, container, host/network configuration, key, or authentication-file changes were performed by Codex.
- **Problems and lessons:** Existing client identity mismatch required deliberate dedicated-key enrollment rather than replacement of old entries. Host trust and user authorization are separate checks; prompt labels do not establish host identity. Gather Data Sampling/microcode status and SSH source/exposure review remain unresolved security items, without evidence of compromise. Linux-visible memory differs from installed capacity; cause remains TODO.
- **References:** Owner-provided October 28 command results in this task; [Hephaestus inventory](devices/hephaestus.md), [SSH runbook](operations/ssh-athena-hephaestus.md), [Athena workflow](devices/athena.md#dedicated-key-ssh-administration-of-hephaestus), [operations](operations/README.md), [current status](PROJECT-STATUS.md). The owner authorizes the scoped documentation commit/push after validation; Git results are reported separately rather than assumed here.
- **Next action / Home Lab HQ checkpoint:** Record the baseline and successful access milestone; prioritize the security review, tested backups, complete service/topology validation, and Olympus migration criteria. After the authorized GitHub update succeeds, refresh ChatGPT Home Lab Project shared reference snapshots and record their source revision and refresh date. Olympus remains planned, not deployed.

## 2026-10-28 — Hephaestus YAMS backup failure, recovery, and successful retry

- **Date and device:** Backup/recovery execution and owner-provided terminal evidence dated 2026-10-28; target Hephaestus, Ubuntu 26.04.1 LTS. Documentation-only session; Codex did not execute host or service operations.
- **Objective:** Record the local backup milestone, service interruption/recovery, and remaining recovery risks.
- **Work completed — owner-provided evidence:** Storage check reported a 512 GB NVMe SSD with approximately 365 GB available, 237 MB of YAMS application configuration, and 29 GB of media. The readable August 5 backup contained Compose files, `.env`, and application configuration; permissions were restricted from `664` to `600`. The first October 28 backup failed on the root-owned, mode-`700` Portainer backups directory. All YAMS containers stopped and were recovered using `yams start`. An elevated retry with an `EXIT` restart trap succeeded; exact archive metadata is in the [device backup record](devices/hephaestus.md#backup-failure-and-recovery--2026-10-28).
- **Validation performed — owner-provided evidence:** New archive passed a tar readability check; ownership `root:root`, permissions `600`. Gluetun and Watchtower reported healthy in Docker after recovery from the initial failed backup. Following the successful retry, YAMS reported all 11 containers running, but no separate Docker health check was performed afterward. Application-level functionality was not independently reverified. No restoration test has occurred. No external backup disk or mounted network backup storage was detected, and no off-device backup exists.
- **Problems and lessons:** The YAMS backup script exits on archive failure without restarting services. Elevated access and the retry's restart trap addressed this attempt; a permanent script fix is not established. Local archive readability does not prove restoration or protect against server/SSD loss.
- **Work completed — documentation:** Updated the Hephaestus page, current status, and this log in a separate non-Git local review snapshot based on GitHub; the older local checkout was preserved because Git fetch failed on DNS resolution. Codex reviewed the three-file diff, checked 71 relative links/heading references, and used `git diff --no-index --check` with no whitespace errors. The snapshot itself was not a Git checkout; changes were subsequently prepared in a separate Git checkout. No Docker, YAMS, server configuration, or running service changes were performed by Codex during documentation work.
- **References:** Owner-provided October 28 terminal findings in this task; [Hephaestus](devices/hephaestus.md#backup-failure-and-recovery--2026-10-28), [current status](PROJECT-STATUS.md). Separate [YAMS troubleshooting log](https://github.com/kkerns20/yams-media-server/blob/main/docs/troubleshooting.md) needs a backup failure/recovery case covering permission preflight, restart guarantees, and validation limits; that repository was not modified.
- **Next action:** Verify an off-device copy; define scope/media coverage, retention, and recovery requirements; plan an authorized controlled restore test with rollback; reverify applications; document and separately authorize backup script hardening before the next run.

## 2026-10-28 — Codex sandbox networking isolated and troubleshooting documented

- **Date and device:** October 28 investigation and owner report; Hephaestus, Ubuntu 26.04.1 LTS, Bash. Codex sandbox results are directly observed; regular-terminal results and the **Ask for approval** permission selection are owner-reported.
- **Objective:** Explain the GitHub lookup failure without assuming a host DNS fault; record the YAMS backup incident in its authoritative repository. Scope: documentation and repository synchronization only.
- **Work completed:** Recorded the sandbox/terminal comparison and recommended approval workflow in the [Hephaestus device page](devices/hephaestus.md#codex-sandbox-networking-investigation--2026-10-28). Added a dated backup failure/recovery case to the separate [YAMS troubleshooting log](https://github.com/kkerns20/yams-media-server/blob/main/docs/troubleshooting.md#case-4-backup-archive-failed-and-left-yams-services-stopped--2026-10-28), with script improvements explicitly marked planned. The documentation was prepared in local Git checkouts and reviewed through repository diffs.
- **Validation performed — investigation:** In the sandbox, `getent ahosts github.com` failed with no output/exit `2`, and Git failed with a DNS resolution error/exit `128`. The owner confirmed that the same lookup and Git worked in the regular terminal. After Codex requested network access and the owner approved, Git's remote revision check succeeded/exit `0`. GitHub and the Hephaestus checkout were synchronized at `65c689c1bb4dd129223cf510784bc3c9240d53b7`, with a clean working tree before these edits.
- **Validation performed — repository baseline:** Connected GitHub checks confirmed Linux Lab `main` at `65c689c1bb4dd129223cf510784bc3c9240d53b7` and YAMS `main` at `1422bb2419da36b315dcc71568ac0388530b3c52` before editing. Both checkouts were clean; the older YAMS documentation checkout was fast-forwarded after an approved network fetch. Repository synchronization is not host or service validation.
- **Validation performed — documentation:** Reviewed complete diffs in both repositories; `git diff --check` passed. Relative file/heading links and cross-repository document targets resolved against the local drafts. Privacy and scope review found only the intended documentation edits, with no staged or untracked files. The new YAMS incident link will become available on GitHub after publication.
- **Problems and lessons:** The observed failure was caused by sandbox network restrictions; a host DNS problem was not verified. No Ubuntu DNS configuration changes were needed or made. No server configuration, Docker, YAMS script, or running services were changed; no backup or restoration test was run.
- **References:** Owner-provided October 28 findings and Codex command results in this session; [device investigation](devices/hephaestus.md#codex-sandbox-networking-investigation--2026-10-28), [current status](PROJECT-STATUS.md), and the YAMS incident linked above.
- **Next action:** Retain sandbox protection and approve individual required network operations. Review the documentation before any authorized commit/push; separately authorize YAMS script hardening, off-device backup, and controlled restore testing.

## Reusable entry template

Copy this template above this section for each meaningful session. Append in date order; if adding older history, insert by supported event date and state when it was reconstructed. Use TODO for unavailable evidence and preserve historical next actions as historical context.

```markdown
## YYYY-MM-DD — Short work description

- **Date and device:** Execution date, target device, OS/shell, and local/remote context; report date separately if different. Unknown details: TODO.
- **Objective:** Problem or outcome sought; authorized scope.
- **Work completed:** Meaningful changes and resulting status; label owner-reported information and plans.
- **Validation performed:** Checks actually run, date, scope, result, and sanitized evidence; explicitly state untested areas.
- **Problems and lessons:** Observed failures, established causes, unresolved questions, and useful lessons. Unsupported cause: TODO.
- **References:** Relevant Git commit if one exists, and/or authoritative document links. Uncommitted work: state that explicitly.
- **Next action:** Concrete priority, dependencies, and any authorization needed.
```
