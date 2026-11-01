# Security policy

OpenWarden handles high-value secrets. Please do not open a public issue for a vulnerability that could expose vault data, credentials, cryptographic keys, or user privacy.

## Reporting a vulnerability

Use GitHub's private vulnerability reporting feature on this repository. Include:

- the affected OpenWarden version and platform;
- a concise impact statement;
- reproducible steps or a minimal proof of concept;
- the upstream Bitwarden behavior, when relevant;
- any suggested remediation.

Never include a real master password, recovery code, vault export, access token, or personal account data. Use a disposable test account and synthetic secrets.

Please allow a reasonable period for investigation and remediation before public disclosure. During research, avoid denial of service, social engineering, privacy violations, data destruction, and testing against accounts or systems you do not own or have explicit permission to assess.

## Scope

In scope:

- vulnerabilities introduced by OpenWarden patches or packaging;
- regressions in authentication, encryption, vault isolation, autofill, TOTP, local archives, or phishing protection;
- unauthorized network communication or disclosure of sensitive local data;
- release-integrity problems involving the published OpenWarden binaries, checksums, or signing identity.

Out of scope:

- a problem that reproduces unchanged in the pinned upstream Bitwarden client and has already been reported upstream;
- a vulnerability in Bitwarden cloud, an official Bitwarden server, Vaultwarden, or another server implementation;
- vulnerabilities in outdated OpenWarden releases;
- attacks that require prior physical control of an already-unlocked device without crossing an additional security boundary;
- general hardening suggestions with no concrete security impact, which may be filed as normal issues.

If ownership is unclear, report privately to OpenWarden first. The maintainers can help route the finding without exposing it publicly.

## Supported version

Only the latest OpenWarden release receives security fixes. Until the project has an independent audit and deterministic release builds, users with a high-risk threat model should build from the published source patches and review the resulting changes.

