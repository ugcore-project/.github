# Security Policy

This security policy applies to all repositories under the **UgCore Framework** organization.

---

## Supported Versions

| Repository | Supported Version | Status |
|---|---|---|
| ug-core | Latest (`main`) | ✅ Actively maintained |
| ug-core | Previous minor | ⚠️ Critical fixes only |
| ug-core | Older releases | ❌ Not supported |

We strongly recommend always running the latest stable release. Older versions will not receive patches, even for critical vulnerabilities.

---

## Reporting a Vulnerability

**Please do not open a public GitHub issue for security vulnerabilities.**

Disclosing a vulnerability publicly before a fix is available puts every server running UgCore at risk. We ask that you follow responsible disclosure practices.

### How to Report

**Preferred — GitHub Private Advisory:**
Use GitHub's built-in [private vulnerability reporting](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing/privately-reporting-a-security-vulnerability) on the affected repository. This keeps the report confidential and lets us collaborate on a fix before any public disclosure.

**Alternative — Discord:**
Reach out privately to a **Core Team** member on our [Discord server](https://discord.gg/pCJUcyVw5X). Do not post in public channels.

### What to Include

Please provide as much detail as possible:

- Affected repository and version(s)
- A clear description of the vulnerability and its potential impact
- Steps to reproduce or a proof-of-concept
- FiveM server artifact version you are running
- Any suggested mitigation or fix (optional)

---

## Scope

### In Scope

- Server-side event abuse — triggering `TriggerServerEvent` from the client without proper validation
- ACE permission bypasses or privilege escalation
- SQL injection in database queries
- Unprotected exports that allow unauthorized access to player data
- Identity, money, inventory, or permission spoofing via logic flaws
- Improper storage or logging of sensitive player data (identifiers, tokens)

### Out of Scope

- Vulnerabilities in FiveM / CitizenFX itself → report to [FiveM](https://fivem.net)
- Issues only reproducible in modified or intentionally misconfigured setups
- Denial-of-service attacks requiring direct server or database access
- Social engineering or phishing

---

## Security Best Practices for Server Owners

Running UgCore on your server? Follow these guidelines to harden your setup.

### Event Validation
- Never trust client-provided data. Always validate on the server side.
- Gate sensitive `RegisterNetEvent` handlers with `source` checks and ACE permission guards.
- Use parameterized queries for all database operations — never interpolate raw player input into SQL.

### ACE Permissions
- Grant the minimum ACE permissions each resource needs to function.
- Audit your `server.cfg` ACE entries regularly and remove anything unused.
- Never grant `command.*` or `resource.*` to untrusted players or unreviewed resources.

### Database
- Use a dedicated database user with only `SELECT`, `INSERT`, `UPDATE`, and `DELETE` on your schema.
- Never commit database credentials to version control. Store them as convars in `server.cfg`.

### Dependencies
- Keep UgCore and all dependent resources updated to their latest releases.
- Audit third-party scripts before installing — review their server-side event handlers before adding them to your server.

### Server Hardening
- Expose only the necessary port (default: `30120`) and run behind a firewall.
- Keep your OS and FiveM artifact up to date.
- Enable server-side logging and monitor for unusual event patterns or unexpected resource triggers.

---

## Response Process

| Stage | Target |
|---|---|
| Acknowledgement | Within 48 hours |
| Preliminary assessment | Within 5 business days |
| Fix or mitigation plan | Depends on severity |
| Coordinated public disclosure | After fix is released |

We will keep you updated throughout the process. You will be credited in the release notes unless you prefer to remain anonymous.

---

## Hall of Fame

We are grateful to the community members who have responsibly disclosed vulnerabilities:

*No entries yet — be the first.*

---

## Disclaimer

UgCore Framework is provided as-is. While we strive to maintain a secure codebase, server owners are ultimately responsible for properly configuring and securing their environments.
