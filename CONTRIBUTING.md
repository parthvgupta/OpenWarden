# Contributing to OpenWarden

OpenWarden welcomes focused, reviewable contributions that preserve compatibility and user trust.

## Before opening a pull request

1. Open an issue describing the problem or proposed feature.
2. Keep client-only functionality separate from server-managed capabilities.
3. Do not add telemetry, advertising, alternate vault backends, or network services without explicit public design review.
4. Add or update tests for behavior changes.
5. Document every new network destination and permission.
6. Never commit signing keys, credentials, tokens, production vault data, or generated release binaries.

Changes should remain easy to compare with the pinned upstream Bitwarden repositories. Prefer small commits and explain any cryptographic or authentication impact directly in the pull request.

Security vulnerabilities must follow [`SECURITY.md`](SECURITY.md), not the public issue tracker.

