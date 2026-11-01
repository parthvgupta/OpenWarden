<p align="center">
  <img src="assets/openwarden.png" width="144" alt="OpenWarden black and gold shield" />
</p>

<h1 align="center">OpenWarden</h1>

<p align="center">
  <strong>Bitwarden compatibility. Community freedom. Client-side premium features without client-side paywalls.</strong>
</p>

<p align="center">
  <a href="https://github.com/parthvgupta/OpenWarden/releases/latest"><img alt="Latest release" src="https://img.shields.io/github/v/release/parthvgupta/OpenWarden?style=flat-square&color=fdb44b"></a>
  <a href="LICENSE"><img alt="GPL-3.0 license" src="https://img.shields.io/badge/license-GPL--3.0-fdb44b?style=flat-square"></a>
  <img alt="Android" src="https://img.shields.io/badge/Android-10%2B-111010?style=flat-square&logo=android">
  <img alt="macOS" src="https://img.shields.io/badge/macOS-Universal-111010?style=flat-square&logo=apple">
  <img alt="Chromium" src="https://img.shields.io/badge/Brave%20%2F%20Chrome-Extension-111010?style=flat-square&logo=brave">
</p>

OpenWarden is an independent, open-source, Bitwarden-compatible community client. It enables personal premium functionality that can run entirely inside the client, while remaining compatible with Bitwarden cloud and self-hosted servers.

It does **not** bypass Bitwarden servers, fabricate server entitlements, or promise server-managed features it cannot deliver. Organizations, server storage, emergency access, sharing policies, Send limits, and other server-owned capabilities remain controlled by the server and account you connect.

## Download v1.0.0

| Platform | Download | Package | Notes |
| --- | --- | --- | --- |
| Android | [OpenWarden APK](https://github.com/parthvgupta/OpenWarden/releases/latest/download/OpenWarden-1.0.0-android.apk) | `org.openwarden.app` | Android 10 or newer; signed release APK |
| macOS | [Universal DMG](https://github.com/parthvgupta/OpenWarden/releases/latest/download/OpenWarden-1.0.0-universal.dmg) | Apple Silicon + Intel | Ad-hoc signed; not Apple-notarized |
| Brave / Chrome | [Chromium extension ZIP](https://github.com/parthvgupta/OpenWarden/releases/latest/download/OpenWarden-1.0.0-chrome-brave.zip) | Manifest V3 | Install unpacked using Developer mode |

Release hashes are published in [`SHA256SUMS`](SHA256SUMS). Never install a binary whose hash does not match.

## What “client-side” means

OpenWarden enables functionality that can be implemented safely on your own device, including built-in authenticator codes, vault-health reporting, password-risk analysis, phishing and suspicious-domain warnings, and a device-local vault archive.

OpenWarden does not operate a replacement cloud, proxy your master password, or upload your vault to an OpenWarden service. Account login, encrypted sync, organizations, sharing, attachments, emergency access, and other server-backed operations continue to use the Bitwarden-compatible server selected in the app.

## Transparency first

A password manager should never ask for blind trust. Every OpenWarden release includes enough public evidence to inspect the changes and rebuild the clients yourself:

- The exact upstream repository and commit are pinned for every platform.
- OpenWarden changes are published as readable Git patches.
- Build and verification commands are documented next to each client.
- Release binaries have public SHA-256 checksums.
- A CI workflow verifies that every patch still applies to its declared upstream commit.
- There is no OpenWarden-operated password backend.

The v1.0.0 binaries were built locally from the patches in this repository. The build process is repeatable, but byte-for-byte reproducibility is not yet guaranteed because upstream Android and Electron packaging embed build-dependent metadata.

## Inspect the code changes

| Component | Upstream | OpenWarden changes |
| --- | --- | --- |
| Android | [`bitwarden/android@262dba3`](https://github.com/bitwarden/android/tree/262dba3e663b2f9a4f2196515331bce9d7b58ad9) | [`android/code-changes`](android/code-changes/) |
| macOS | [`bitwarden/clients@b793bdc`](https://github.com/bitwarden/clients/tree/b793bdc6cf15f87814f0b3de26b795afcc7774ec) | [`macos/code-changes`](macos/code-changes/) + [`shared/code-changes`](shared/code-changes/) |
| Brave / Chrome | [`bitwarden/clients@b793bdc`](https://github.com/bitwarden/clients/tree/b793bdc6cf15f87814f0b3de26b795afcc7774ec) | [`extension/code-changes`](extension/code-changes/) + [`shared/code-changes`](shared/code-changes/) |

Start with the platform guides:

- [Android: install, inspect, build, and verify](android/README.md)
- [macOS: install, inspect, build, and verify](macos/README.md)
- [Brave/Chrome: install, inspect, build, and verify](extension/README.md)

Project guidance:

- [Compatibility with Bitwarden and Vaultwarden](docs/COMPATIBILITY.md)
- [Troubleshooting login, sync, and installation](docs/TROUBLESHOOTING.md)
- [Release and update policy](docs/RELEASES.md)
- [Getting help and reporting bugs](SUPPORT.md)

## Installation

### Android

1. Download the APK from the latest release.
2. Confirm its SHA-256 value against [`SHA256SUMS`](SHA256SUMS).
3. Allow installation from your browser or file manager when Android prompts.
4. Install the APK. Future OpenWarden APKs must be signed with the same release key to update it in place.

### macOS

1. Download and open the universal DMG.
2. Drag OpenWarden into Applications.
3. Because v1.0.0 is not Apple-notarized, macOS may block the first launch. Right-click OpenWarden and choose **Open**, or approve it under **System Settings → Privacy & Security**.
4. Do not disable Gatekeeper globally.

### Brave or Chrome

1. Download and extract the extension ZIP.
2. Open `brave://extensions` or `chrome://extensions`.
3. Enable **Developer mode**.
4. Choose **Load unpacked** and select the extracted folder.

Developer-mode extensions do not update automatically. Review and install each future release yourself.

OpenWarden does not currently include an automatic updater on any platform. Follow this repository's releases and use the verification steps in [`docs/RELEASES.md`](docs/RELEASES.md) before updating.

## Security model

OpenWarden inherits the core encrypted-vault architecture of the pinned upstream Bitwarden clients and adds community features around the local client. That inheritance is not a substitute for an independent security audit. Treat every release—including this one—as security-sensitive software: verify the hash, inspect the patches, and build it yourself when your threat model requires it.

OpenWarden is a client, not a backup service. A device-local archive is not a substitute for a tested server backup or an export you control. Keep a recovery plan appropriate to the Bitwarden-compatible server you use.

Please report vulnerabilities privately using the process in [`SECURITY.md`](SECURITY.md). Do not post secrets, vault exports, master passwords, recovery codes, or live exploit details in a public issue.

## Contributing

Bug reports, code review, build verification, documentation corrections, and independent security analysis are welcome. For a problem, start with [`SUPPORT.md`](SUPPORT.md); for a code change, read [`CONTRIBUTING.md`](CONTRIBUTING.md).

## Independence and trademarks

OpenWarden is an independent community project. It is not affiliated with, sponsored by, or endorsed by Bitwarden, Inc. “Bitwarden” is used only to describe compatibility and upstream origin. Bitwarden trademarks remain the property of Bitwarden, Inc.; see [`NOTICE`](NOTICE).

OpenWarden source modifications are distributed under GPL-3.0. Some upstream files may carry additional license notices; those notices continue to apply.

