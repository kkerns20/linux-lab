# iPhone-to-Atlas SSH through Tailscale

**Status:** Owner-tested 2026-11-03 over cellular. **Scope:** iPhone → Tailscale private network → Atlas Windows OpenSSH → Ubuntu WSL2. This is not direct access to Hephaestus or a verified post-reboot recovery path.

## Purpose and architecture

Access the Windows workstation and its Ubuntu WSL2 development environment occasionally from an iPhone without public router port forwarding. SSH terminates on **Windows**, then the user launches Ubuntu using the WSL command.

- **iPhone:** Tailscale VPN and Termius SSH client with a dedicated ED25519 key pair.
- **Atlas Windows:** Tailscale network interface, Windows OpenSSH Server, and a firewall allow rule scoped to the Tailscale interface.
- **Ubuntu WSL2:** Existing Bash/Linux account launched from the Windows SSH session.
- **Privacy:** Do not commit credentials, key material (public or private), private Tailscale addresses, tailnet names, SSH host fingerprints, or device-specific VPN configuration.

## Implementation record (owner-reported)

1. Windows OpenSSH Server was initially absent. Adding its Windows capability failed due to component-store corruption. DISM CheckHealth reported repairable corruption; RestoreHealth completed, and the OpenSSH Server capability installation then succeeded without a required restart. **This repair is incident history, not a routine installation step.**
2. Tailscale was installed on Atlas with Windows Package Manager. The iPhone joined the same private network, and the Windows Tailscale tunnel adapter was observed **Up**.
3. The default Windows OpenSSH inbound allow rule (OpenSSH-Server-In-TCP) was disabled. A new inbound TCP/22 allow rule (SSH via Tailscale) was created with InterfaceAlias Tailscale and Profile Any; its interface filter was checked and returned Tailscale. Other effective firewall rules have **not** been comprehensively audited.
4. The Windows SSH service (sshd) was started and configured **Running / Automatic**; the Tailscale service was also checked **Running / Automatic**. No reboot-persistence test was performed.
5. Termius generated a dedicated ED25519 key. Its public key was placed in the administrator-specific OpenSSH key file at C:\ProgramData\ssh\administrators_authorized_keys, because the Windows account belongs to the Administrators group. A Notepad-added .txt extension was corrected. File inheritance was removed and icacls confirmed full-control entries for **SYSTEM** and **BUILTIN\Administrators** only. The private key remains on the phone.
6. Termius used Atlas's private Tailscale address, Windows account, port 22, and dedicated key. The owner switched off Wi-Fi, connected over cellular with Tailscale, and opened a Windows SSH session. The remote shell appeared to be Command Prompt, so commands were tested individually rather than joined with a PowerShell semicolon.
7. The owner confirmed the Windows account and hostname, ran the WSL launch command, reached the familiar Ubuntu Bash prompt, and confirmed the Linux account.
8. Windows Balanced plan sleep was originally **30 minutes plugged in / 5 minutes on battery**. AC sleep was temporarily changed to Never, then the owner **restored the 30-minute AC timeout**. The restored value was not reread, and lid-close action was not checked.

## Validation and limitations

| Check | Result | What is not established |
| --- | --- | --- |
| Tailscale / sshd services | Both Running and Automatic per owner-provided PowerShell output | Availability after a Windows reboot |
| Windows firewall restriction | New SSH allow rule's interface filter showed Tailscale; default OpenSSH allow rule disabled | Full effective firewall audit |
| Administrator authorized-keys file | Correct filename; ACL showed only Administrators and SYSTEM | Server-side authentication mechanism/log confirmation |
| iPhone connection over cellular | Successful SSH terminal; Windows account and hostname confirmed | Independent confirmation of SSH host-key fingerprint comparison |
| Ubuntu WSL2 | Ubuntu Bash prompt and Linux account confirmed | Cold-boot WSL launch testing |
| Power policy | Normal 30-minute AC sleep restored per owner | Final readback and lid-close behavior |

**Security note:** A successful login using a key-configured client is not proof that password authentication is disabled. Review effective OpenSSH configuration, other inbound firewall allowances, Tailscale device policies, and host-key trust separately. Do not disable password authentication until key login and a local recovery method are verified.

## Read-only diagnostic commands

From **Windows PowerShell on Atlas**:

~~~powershell
Get-Service sshd | Select-Object Name, Status, StartType
Get-Service -Name "Tailscale*" | Select-Object Name, Status, StartType
Get-NetFirewallRule -DisplayName "SSH via Tailscale" |
    Get-NetFirewallInterfaceFilter |
    Select-Object InterfaceAlias
icacls "C:\ProgramData\ssh\administrators_authorized_keys"
powercfg /query SCHEME_CURRENT SUB_SLEEP STANDBYIDLE
~~~

From **Termius**: verify the Windows user and hostname with separate whoami and hostname commands, then run wsl and use whoami inside Ubuntu Bash. Never publish the device-specific outputs.

## Troubleshooting, recovery, and tradeoffs

- If remote SSH fails, check **Atlas is on and awake**, both Tailscale clients are connected, and both Windows services are running. Then check the address/key chosen in Termius, firewall interface rule, key-file ACL, and server logs. Do **not** open router ports to fix connectivity.
- Local Windows administrator access is the fallback for lockouts; do not change firewall or SSH configuration without understanding the recovery path.
- Automatic service startup does **not** wake a sleeping laptop. Atlas is primarily a workstation, so normal sleep behavior was retained rather than 24/7 availability.
- Future validation: post-reboot cellular reconnect, lid-close behavior, full effective firewall/authentication review, and explicit SSH host-key fingerprint comparison.
- For frequent always-on server administration, consider independently secured Tailscale access on Hephaestus instead; **not configured or tested in this session**.
- Decommissioning requires a separately authorized local change to disable the dedicated inbound firewall rule and SSH service after checking dependencies; do not alter the power policy without a new requirement.

Related: [Atlas](../devices/atlas.md), [status](../PROJECT-STATUS.md), [decisions](../DECISIONS.md), [work log](../WORK-LOG.md).