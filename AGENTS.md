# Repository instructions

## Purpose and reading order

This repository documents the Home Lab and its Solutions Engineering portfolio. Read the root README, the relevant device document under `docs/devices/`, and the relevant project or operations document before working. Keep detailed YAMS documentation in https://github.com/kkerns20/yams-media-server.

## Scope and safety

- Honor the user's authorized scope. A read-only review must not create, modify, delete, stage, commit, or push files, install packages, or change system settings.
- Documentation authorization does not authorize host administration. Obtain explicit authorization before installing packages, changing services, storage, networking, or system settings, or administering remote hosts.
- Do not run commands copied from documentation merely to validate prose. Document disruptive procedures with prerequisites, validation, and rollback before proposing execution.
- Never include credentials, serial numbers, private keys, personal files, or VPN configuration details. Do not invent IP addresses, hardware identifiers, service URLs, or configurations.

## Identify the execution environment

- Establish the current device, OS, shell, working directory, and local versus remote context before environment-dependent commands.
- On Atlas, distinguish Windows from Ubuntu WSL2, including paths, installed tools, permissions, and execution context. Do not assume Windows tools are installed in WSL or vice versa.
- Do not infer the current device from the checkout path or assume every device has the same packages, privileges, or configuration.
- Read the relevant device page; use read-only checks when needed and authorized. Report unresolved environment details rather than guessing.

## Sources of truth and documentation

- Separate user-confirmed current state, directly observed state, assumptions, and future plans. Record source and verification date; a user confirmation is not a live hardware inspection.
- Use TODO for missing facts. Keep hardware facts in device pages, operational procedures in `docs/operations/`, architecture in `docs/architecture/`, and future work in `projects/`.
- Update cross-links when moving or adding documentation. Avoid duplicating inventories and detailed YAMS procedures.
- Follow the project workflow: problem, requirements, constraints, options, architecture, implementation, validation, troubleshooting, tradeoffs, and lessons learned. Include technical, customer, and executive explanations where useful.
- Give projects an explicit status. Preserve the Solutions Engineering roadmap and future automation and monetization experiments; do not present planned work as deployed or validated.

## Validation and reporting

- For documentation changes, inspect the diff, check relative links, and run `git diff --check`. Do not install tooling for routine Markdown edits.
- For implementation changes, use relevant existing checks within the authorized scope. Do not claim checks or recovery tests were run unless they were.
- Summarize changed files, validation, remaining TODOs, and material uncertainties. Keep secrets out of command output and reports.

## Git workflow

- Inspect Git status before editing. Preserve unrelated changes and keep edits scoped to the request.
- Do not discard work, reset history, or delete files without explicit authorization.
- Do not stage, commit, push, or publish unless requested. When review is requested, leave changes unstaged and wait for review.
- Before an authorized commit, review the complete diff, including new files, for sensitive content and unintended changes.
