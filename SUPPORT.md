# OpenWarden support

OpenWarden is an independent client. Please report OpenWarden-specific problems here rather than to Bitwarden or Vaultwarden maintainers.

## Before asking for help

1. Confirm that you installed the latest OpenWarden release from this repository.
2. Check the package hash against [`SHA256SUMS`](SHA256SUMS).
3. Read the [compatibility policy](docs/COMPATIBILITY.md) and [troubleshooting guide](docs/TROUBLESHOOTING.md).
4. Search both open and closed [issues](https://github.com/parthvgupta/OpenWarden/issues) and [discussions](https://github.com/parthvgupta/OpenWarden/discussions).
5. If you use a self-hosted server, update it to its current stable release and record its exact version.

Use [GitHub Discussions](https://github.com/parthvgupta/OpenWarden/discussions) for setup questions and ideas. Use the [bug report form](https://github.com/parthvgupta/OpenWarden/issues/new?template=bug_report.yml) for a reproducible defect.

## Work out where the problem lives

The client and server can fail independently. These comparisons help route a report without sending community-client problems to unrelated maintainers:

| Result | Best first report |
| --- | --- |
| Fails only in OpenWarden | OpenWarden issue |
| Fails in OpenWarden and the matching official client against Bitwarden cloud | Bitwarden may be the upstream owner; describe the official-client reproduction, not OpenWarden |
| Fails only against a self-hosted Bitwarden server | That server deployment's administrator or official Bitwarden self-host support |
| Fails only against Vaultwarden | Update Vaultwarden first, then use Vaultwarden's client-troubleshooting process if the current release still fails |
| Unsure, or unable to test safely | OpenWarden Discussion |

Do not create or use a real vault merely to reproduce a bug. Use a disposable account with synthetic entries whenever possible.

## Information a useful report includes

- OpenWarden version and platform;
- operating system and, for the extension, browser version;
- installation source and whether the published hash matched;
- server type and exact server version, without revealing a private hostname;
- exact steps, expected result, and actual result;
- whether the same action works in the matching official Bitwarden client;
- the smallest relevant log excerpt after redaction.

Logs and screenshots can expose email addresses, server URLs, item names, form contents, and other private data. Remove those values before posting. Never attach a vault export, database, master password, API key, access token, recovery code, encryption key, or full unreviewed diagnostic capture.

Potential vulnerabilities belong in [private vulnerability reporting](https://github.com/parthvgupta/OpenWarden/security/advisories/new), not in an issue or Discussion.
