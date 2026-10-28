# Home Lab architectural decision log

**Last updated:** 2026-10-28. This ongoing log records established choices and planned direction. Implementation evidence belongs in the linked device, project, or operations document.

Dates below distinguish first documentation, owner report, and adoption. Original adoption dates are TODO unless supported. Tradeoffs describe implications for future review; they are not claims that the owner used those arguments when deciding. Missing historical rationale remains TODO. Preserve superseded entries and link replacement decisions.

## D-001 — Greek mythology device names

- **Status:** Established convention; Olympus and Prometheus remain future infrastructure names.
- **Date/source:** Names documented in inventory commit `8c008a2` on 2026-10-27; Greek mythology convention explicitly confirmed in the owner's 2026-10-28 request. Adoption date TODO.
- **Decision:** Use Atlas, Athena, Hermes, Hephaestus, Olympus, and Prometheus as lab device/project labels. This does not establish DNS names.
- **Rationale:** Historical naming rationale TODO; the owner has established the convention.
- **Tradeoffs:** Names require a maintained mapping to hardware and roles; labels alone do not identify network endpoints.
- **Authority:** [Device inventory](devices/README.md).

## D-002 — Fedora on Athena

- **Status:** Adopted; Fedora 44 is the documented current OS.
- **Date/source:** Recorded 2026-10-27 in `8c008a2` and inspection document `6dd935d`; reaffirmed by owner 2026-10-28. Fedora 44 also observed in this session on 2026-10-28. Installation/decision date TODO.
- **Decision:** Use Fedora Workstation for Athena's Linux development and learning role.
- **Rationale:** The development/learning role is documented; why Fedora was chosen over other distributions is TODO.
- **Tradeoffs:** Fedora-specific administration must be distinguished from Ubuntu server and WSL procedures.
- **Authority:** [Athena](devices/athena.md).

## D-003 — Windows 11 Home on Hermes

- **Status:** Adopted; installation, activation, and Insider departure are owner-reported.
- **Date/source:** Windows 11 Home 26H2 recorded 2026-10-27 in `8c008a2`; fresh activated installation and no Insider enrollment reported 2026-10-28. Execution/decision dates TODO.
- **Decision:** Use Windows 11 Home for the portable administration workstation.
- **Rationale:** Portable administration is the documented role; edition choice and reinstall/Insider departure rationale TODO.
- **Tradeoffs:** Administration procedures must account for the Home edition and tools actually installed; WSL and Codex are unconfirmed on Hermes.
- **Authority:** [Hermes](devices/hermes.md).

## D-004 — Ubuntu WSL2 on Atlas

- **Status:** Adopted; Linux development environment documented by read-only inspection.
- **Date/source:** Recorded 2026-10-27 in `8c008a2` and `f90f1a7`; owner reaffirmed 2026-10-28. Adoption date TODO.
- **Decision:** Keep Windows 11 as Atlas's primary OS and use Ubuntu 24.04 WSL2 for Linux development and Codex work.
- **Rationale:** Atlas's documented role combines a Windows primary workstation with a Linux development/documentation environment. Original selection rationale TODO.
- **Tradeoffs:** Windows and Linux have separate paths, installed tools, permissions, and settings; WSL checks do not verify the Windows host.
- **Authority:** [Atlas](devices/atlas.md).

## D-005 — LUKS encryption on Athena

- **Status:** Adopted; encrypted storage layout recorded by inspection on 2026-10-27; owner reaffirmed 2026-10-28.
- **Date/source:** Explicit LUKS evidence in `6dd935d` on 2026-10-27. Enablement/decision date TODO.
- **Decision:** Use LUKS-encrypted storage for Athena's Btrfs root and home filesystems. Separate EFI and boot partitions are not documented as LUKS-encrypted.
- **Rationale:** Historical encryption rationale TODO; the encrypted layout is established.
- **Tradeoffs:** Unlock and recovery planning are required; encryption does not establish a working backup or restore path. Recovery material stays outside this repository.
- **Authority:** [Athena storage](devices/athena.md#storage-and-swap).

## D-006 — GitHub documentation source of truth

- **Status:** Established; explicitly designated by owner for Home Lab HQ on 2026-10-28.
- **Date/source:** Repository history starts 2026-09-30 (`f461cc5`); GitHub source-of-truth decision confirmed in the 2026-10-28 request. Earlier adoption date TODO.
- **Decision:** Maintain authoritative Home Lab documentation in the GitHub `linux-lab` repository; keep detailed YAMS documentation in its separate repository. Capture meaningful session outcomes here rather than relying on conversation history.
- **Rationale:** The owner requests a central planning/documentation workflow that provides continuity for new ChatGPT and Codex sessions.
- **Tradeoffs:** Summaries can drift without maintenance; drafts are local until reviewed and explicitly authorized for commit/push. Documentation history proves recorded changes, not live infrastructure state.
- **Authority:** [Home Lab overview](../README.md), [Home Lab HQ status](PROJECT-STATUS.md), [YAMS repository](https://github.com/kkerns20/yams-media-server).

## D-007 — Repository-level Codex instructions

- **Status:** Adopted; Home Lab HQ reading/maintenance guidance added as a review draft on 2026-10-28.
- **Date/source:** `AGENTS.md` introduced by `8c008a2` on 2026-10-27; consistency and status-first reading requested by owner 2026-10-28.
- **Decision:** Maintain repository-level `AGENTS.md` for shared scope, environment identification, documentation, validation, and Git rules; read the status page at the start of substantial Home Lab tasks.
- **Rationale:** Provide consistent Codex instructions across devices and sessions, as requested by the owner.
- **Tradeoffs:** Instructions need maintenance as workflows evolve; reading them does not authorize administration or Git publication.
- **Authority:** [Repository instructions](../AGENTS.md).

## D-008 — Migrate permanent services from Hephaestus to Olympus

- **Status:** Accepted direction; migration is planned and not executed. Hephaestus remains temporary.
- **Date/source:** Permanent-server direction documented 2026-10-01 in `30f26ef`; named migration recorded 2026-10-27 in `8c008a2`; owner reaffirmed Olympus is not deployed on 2026-10-28. Original decision date TODO.
- **Decision:** Move permanent services to a stationary, wired, expandable Olympus server after readiness and migration validation. Hephaestus's later role remains TODO.
- **Rationale:** The roadmap calls for an intentional always-on server with storage expansion and VM/container headroom beyond the temporary laptop role.
- **Tradeoffs:** Requires hardware budget, verified inventory, backups, service/storage compatibility, and a validated recovery plan; hardware and storage candidates remain proposals.
- **Authority:** [Home server roadmap](../projects/home-server-roadmap.md), [Hephaestus](devices/hephaestus.md).

## D-009 — Athena outbound-oriented firewall

- **Status:** Adopted per owner report; not independently verified.
- **Date/source:** Report received 2026-10-28. Actual change and reboot/test dates TODO.
- **Decision:** Use firewalld's `public` zone for Athena's NetworkManager Wi-Fi connection, with incoming SSH permission removed. Owner reports verification after reboot.
- **Rationale:** The owner identifies an outbound-oriented workstation posture. Detailed threat model and original change rationale TODO.
- **Tradeoffs:** Incoming SSH administration on this connection cannot be assumed available. Full effective rules, other profiles, and exposure have not been inspected; this is not evidence that all incoming traffic is blocked. Any future access change needs explicit authorization and a documented recovery path.
- **Authority:** [Athena firewall posture](devices/athena.md#firewall-posture), [operations backlog](operations/README.md).

## Future decision template

### D-TODO — Decision title

- **Status:** Proposed / adopted / planned / superseded (link replacement).
- **Date/source:** Decision date or TODO; report/documentation date and source; verification date and scope if applicable.
- **Decision:** What is established and what remains planned.
- **Rationale:** Supported reasons; TODO for missing history.
- **Tradeoffs:** Known costs, limits, alternatives, and unresolved questions.
- **Authority:** Link to the detailed device, architecture, project, or operations document.
