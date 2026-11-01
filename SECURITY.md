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

## Supported version

Only the latest OpenWarden release receives security fixes. Until the project has an independent audit and deterministic release builds, users with a high-risk threat model should build from the published source patches and review the resulting changes.

