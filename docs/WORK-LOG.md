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
