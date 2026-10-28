# SSH administration — Athena to Hephaestus

**Status:** Successful access exercise documented from owner-provided October 28, 2026 command results. **Last tested:** 2026-10-28 by the owner. Codex did not execute these procedures, inspect private key material, or administer either host during documentation work. Recovery, backup restoration, and broader hardening have not been tested by this exercise.

## Purpose and target environments

Establish an authenticated SSH administration session from [Athena](../devices/athena.md), the Fedora 44 client, to [Hephaestus](../devices/hephaestus.md), the Ubuntu 26.04.1 LTS server, while checking both server identity and user authorization. The successful session validated access and remote identity; it did not validate every hosted application.

## Prerequisites, authorization, and expected impact

- Confirm the local client and target server before using commands. Obtain the approved remote account and current LAN endpoint privately; `REMOTE_USER` and `HEPHAESTUS_LAN_IP` below are placeholders, not configured values.
- Have an independently trusted way to check the server host-key fingerprint directly on Hephaestus, and retain console access for lockout recovery. Do not rely solely on a network-presented fingerprint.
- Confirm the OpenSSH client on Athena and SSH service/reachability on Hephaestus. The exercise verified these prerequisites; their current state must be checked before reuse. DHCP can change the endpoint.
- Use the dedicated private key already provisioned on Athena. The reusable connection workflow assumes enrollment is complete. Future key creation, authorization changes, service/firewall changes, and remote administration require explicit scope and approval; this runbook does not grant them.
- Expect an interactive remote shell, authentication logs, and potentially a local `known_hosts` trust entry after verified acceptance. Enrollment changes server authorization and needs a preserved recovery path. Inventory/application changes are outside the connection workflow.

## Completed exercise and validation evidence

The following is the owner's reported execution record, not a reconstructed terminal transcript:

| Step | Owner-provided result from 2026-10-28 |
| --- | --- |
| Client/server readiness | OpenSSH client verified on Athena; SSH server verified running on Hephaestus |
| Reachability | Network routing and ping succeeded; the later successful SSH session also demonstrated TCP access for that session |
| Server identity | ED25519 fingerprint presented over the network compared with the fingerprint obtained directly from Hephaestus; owner confirmed an exact match |
| Existing user identity | Athena's existing SSH identity did not match the previously authorized key fingerprints; existing authorizations were preserved |
| Dedicated identity | Dedicated ED25519 key pair created for Hephaestus administration |
| Client key permissions | Private key `600`; public key `644` |
| Server authorization permissions | Remote account's `.ssh` directory `700`; `authorized_keys` file `600` |
| Authorization backup | Existing `authorized_keys` backed up and backup compared successfully; restoration was not tested |
| Public-key transport | Dedicated public key transferred using USB media and verified; key contents and identifying metadata are omitted |
| Authorization update | New public key appended without replacing prior entries; an exact-match check verified the new entry |
| Authentication | SSH login using the dedicated key succeeded |
| Remote identity | `hostname` and `id -un` verified the remote host/account; actual output remains private |
| Disconnection | `exit` closed the remote shell and returned to Athena |

Fingerprint comparison and key authorization address different questions: the server host key establishes which server is reached; the user's authorized public key controls which client identity may authenticate. No keys, fingerprint values, account names, or endpoints are reproduced here.

## Reusable connection procedure

These commands are reusable examples, not a claim that these exact command strings were captured in the supplied results. Execute only within an explicitly authorized session.

1. **On Athena, establish client context.** Check `hostname` and `ssh -V` privately and confirm the target account/endpoint from the approved inventory. A customized `HEPHAESTUS` Bash prompt is a visual label; it does not establish the underlying hostname or prove a remote session.
2. **Verify server trust before acceptance.** Through the trusted Hephaestus console, obtain the ED25519 public host-key fingerprint, for example with `ssh-keygen -lf /etc/ssh/ssh_host_ed25519_key.pub`. Compare it exactly with the ED25519 fingerprint presented by the SSH connection. Keep both values private. If they differ or cannot be independently checked, stop before accepting the key or authenticating.
3. **Connect from Athena using the dedicated identity.** Substitute the approved private endpoint and account for the placeholders:

   ```bash
   ssh -o IdentitiesOnly=yes -i ~/.ssh/id_ed25519_hephaestus REMOTE_USER@HEPHAESTUS_LAN_IP
   ```

   The `-i` option selects the dedicated identity. `IdentitiesOnly=yes` limits authentication to configured identities rather than offering every identity available through an agent; other configured identities may still matter. Review unexpected identity selection privately rather than assuming this option ignores all SSH configuration.
4. **Inside the remote session, verify identity.** Run `hostname` and `id -un` and compare privately with the expected server/account before any administrative work. Successful authentication alone does not prove the chosen endpoint/account is the intended one.
5. **Disconnect safely.** Finish any approved foreground work, then run `exit`. Verify the return to Athena with `hostname`; do not infer context only from prompt styling. Closing the connection is not a server shutdown.

## Host-key trust and `known_hosts`

The client's `~/.ssh/known_hosts` records accepted server host keys for subsequent comparison. It is distinct from the server's `authorized_keys`, which authorizes user public keys. The October 28 exact-match comparison is historical evidence, not blanket approval of future host-key changes.

An unexpected host-key warning can indicate an endpoint change, server reinstall/key rotation, or an impersonation attempt. Stop and independently establish the cause and correct fingerprint. Do not bypass checking, blindly accept a replacement, or automatically remove an old trust entry. A trust-entry correction is future work requiring verification and authorization; it was not tested as recovery here.

## Safe key handling and SSH agents

- Keep the private key on the client under its intended owner's control; do not copy it to USB media, the server, chat, or Git. The documented USB transfer was of the public key only. Public-key material and authorization-file contents also stay out of this public repository.
- Preserve previous authorized entries when enrolling an additional key. The exercise verified a backup comparison and an exact new-entry match; these are not proof of a tested restore procedure.
- The verified permissions were private key `600`, public key `644`, remote `.ssh` directory `700`, and remote `authorized_keys` `600`. TODO: capture sanitized ownership/parent-directory checks if needed; do not change permissions merely to follow a documentation example.
- A local SSH agent can offer loaded identities or cache access to a passphrase-protected key. Agent state, passphrase protection, and agent-forwarding configuration were not established by the supplied results. The explicit identity example helps diagnose selection; do not assume a loaded GitHub identity is authorized on Hephaestus.
- **Future recommendation, not tested here:** review key passphrase/agent policy and avoid forwarding an agent unless there is a separately justified need. Do not copy secrets or verbose authentication output into public troubleshooting notes.

## Authentication and connectivity troubleshooting

| Symptom | Safe diagnostic direction; changes require separate authorization |
| --- | --- |
| Timeout or unreachable destination | Reconfirm the private DHCP endpoint, route, client network, server availability, and intended firewall sources. Ping success alone does not prove SSH availability; do not open broader firewall access as a shortcut. |
| Connection refused | Check service/listener state through trusted console access before proposing changes; a historical running service does not guarantee current availability. |
| Host-key mismatch | Stop; independently verify host identity and investigate the change. Do not disable host-key checking. |
| Public-key authentication rejected | Check remote account, selected identity, matching authorized public key, file ownership/permissions, and account policy through an approved path. The earlier identity mismatch did not mean that existing keys were invalid for their other uses. |
| Agent offers unexpected keys | Inspect agent/configuration locally and privately; use the dedicated identity selection example. Do not expose key fingerprints or verbose logs publicly. |
| Password fallback unavailable | The supplied Hephaestus results report password and keyboard-interactive authentication disabled. Use trusted console/recovery access; do not enable password login without a separate security decision and authorization. |
| Session context uncertain | Verify `hostname` and `id -un` privately. Prompt labels and terminal colors are not authentication evidence. |

## Risks, recovery considerations, and remaining validation

Risks include trusting an unverified host, authorizing the wrong key/account, exposing key material, losing access while changing authorization, and assuming a DHCP endpoint or container state is permanent. Hephaestus's [security review items](../devices/hephaestus.md#networking-and-ssh-security) include SSH source restrictions, IPv4/IPv6 exposure, and a reported CPU microcode-related condition; the access exercise does not resolve them.

**Recovery planning, untested:** retain a trusted console path and preserve existing authorized entries before future enrollment. If an authorization change fails, review the intended account and preserved backup through that console before a controlled correction. Restoring an older file can remove later legitimate entries; reconcile changes rather than blindly replacing it. Do not close the only working administration path while changing access. No backup restoration, key revocation/rotation, trust-entry repair, service recovery, or broader hardening test is established here.

The tested endpoint was a single owner-confirmed connection on October 28. TODO: define and separately authorize repeat-access checks, backup/restore testing, source-restriction review, key lifecycle policy, and recovery acceptance criteria. Record later test dates and sanitized outcomes rather than extending the last-tested date from documentation edits alone.
