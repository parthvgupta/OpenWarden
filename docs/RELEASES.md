# Release and update policy

The only official OpenWarden downloads are assets attached to releases in [`parthvgupta/OpenWarden`](https://github.com/parthvgupta/OpenWarden/releases). Mirrors, reposted APKs, repackaged extensions, and similarly named applications are not endorsed by this project.

## What every release must publish

- a versioned Git tag and release notes;
- the exact upstream repositories, commits, and inherited client versions;
- readable patches for every OpenWarden modification;
- platform build and inspection instructions;
- SHA-256 hashes for all distributed binaries;
- the Android signing-certificate fingerprint when an APK is included;
- automated confirmation that each patch applies to its pinned upstream commit.

If any item is missing or inconsistent, do not install the release; open a Discussion so it can be investigated.

## Updates

OpenWarden currently has no automatic update channel:

- Android updates must come from a newer APK signed by the same OpenWarden release key.
- macOS updates are installed manually from a verified DMG.
- Brave and Chrome developer-mode extensions are replaced and reloaded manually.

Review the release notes before updating. Keep the current server release compatible with the new upstream client baseline, especially when using Vaultwarden. Only the latest OpenWarden release receives security fixes.

## Verification

Download the release asset and the repository's [`SHA256SUMS`](../SHA256SUMS), then calculate the asset hash locally. Platform-specific commands and identity checks are documented in the [Android](../android/README.md), [macOS](../macos/README.md), and [extension](../extension/README.md) guides.

A matching hash proves that the file matches the published release record. It does not replace source review, an independent audit, or platform code signing and notarization.
