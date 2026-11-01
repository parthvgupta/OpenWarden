# Compatibility policy

OpenWarden follows the Bitwarden client protocol at the exact upstream revisions recorded in this repository. Compatibility is tied to those client baselines, not to a promise that every past or future Bitwarden-compatible server will behave identically.

## v1.0.0 baselines

| OpenWarden client | Upstream client baseline | Source record |
| --- | --- | --- |
| Android | Bitwarden Android 2026.11.0 | [`android/upstream.json`](../android/upstream.json) |
| macOS | Bitwarden Desktop 2026.10.3 | [`macos/upstream.json`](../macos/upstream.json) |
| Brave / Chrome | Bitwarden Browser 2026.10.2 | [`extension/upstream.json`](../extension/upstream.json) |

These values identify the inherited client code and expected API behavior. They are not a certification of every server version or deployment configuration.

## Server expectations

- **Bitwarden cloud:** OpenWarden targets the same service API used by the corresponding upstream client baseline.
- **Official Bitwarden self-hosted:** keep the server current enough to support the client baseline and use a valid HTTPS configuration.
- **Vaultwarden:** compatibility is best-effort because Vaultwarden independently implements the Bitwarden Client API. Use its current stable release before reporting a login or sync problem.
- **Other compatible servers:** they may work, but are not covered until a maintainer can reproduce the behavior.

Bitwarden can change its clients and API before an independent server implements the corresponding behavior. Vaultwarden release notes sometimes identify a minimum Vaultwarden version for newer Bitwarden clients; that server update takes priority over client-side troubleshooting. See the official [Vaultwarden releases](https://github.com/dani-garcia/vaultwarden/releases) and [Bitwarden clients troubleshooting](https://github.com/dani-garcia/vaultwarden/wiki/Bitwarden-clients-troubleshooting) guidance.

## Compatibility reports

When a login, unlock, sync, attachment, organization, Send, or sharing operation fails:

1. record the OpenWarden version and exact server version;
2. update the server to its current stable release;
3. retry after a full logout and fresh login;
4. compare the same action with the matching official Bitwarden client when safe;
5. follow [`SUPPORT.md`](../SUPPORT.md) to report the result.

OpenWarden will not add protocol workarounds that weaken certificate validation, encryption, authentication, or server authorization merely to preserve compatibility with an outdated deployment.
