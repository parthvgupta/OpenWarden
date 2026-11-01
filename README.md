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

## Install and documentation

| Platform | Install | Full guide |
| --- | --- | --- |
| Android | Open the verified APK | [Install, inspect, build, and verify](android/README.md) |
| macOS | Open the DMG, drag OpenWarden to Applications, then right-click **Open** on first launch | [Install, inspect, build, and verify](macos/README.md) |
| Brave / Chrome | Extract the ZIP, enable Developer mode, and choose **Load unpacked** | [Install, inspect, build, and verify](extension/README.md) |

**Project docs:** [Compatibility](docs/COMPATIBILITY.md) · [Troubleshooting](docs/TROUBLESHOOTING.md) · [Release policy](docs/RELEASES.md) · [Help and bug reports](SUPPORT.md)

Updates are manual. Verify every download against [`SHA256SUMS`](SHA256SUMS).

## What “client-side” means

OpenWarden enables functionality that can be implemented safely on your own device, including built-in authenticator codes, vault-health reporting, password-risk analysis, phishing and suspicious-domain warnings, and a device-local vault archive.

OpenWarden does not operate a replacement cloud, proxy your master password, or upload your vault to an OpenWarden service. Account login, encrypted sync, organizations, sharing, attachments, emergency access, and other server-backed operations continue to use the Bitwarden-compatible server selected in the app.

## Bitwarden Free vs OpenWarden

This is the practical difference when both clients connect to the same free Bitwarden-compatible account:

| Capability | Official Bitwarden Free | OpenWarden v1.0.0 | How OpenWarden provides it |
| --- | --- | --- | --- |
| Unlimited vault items, device sync, generator, and autofill | Included | Included | Inherited from Bitwarden |
| Integrated authenticator codes (TOTP) | Not included | **Unlocked** on Android, macOS, and Brave/Chrome | Generated on your device |
| Full vault-health details | Limited | **Unlocked** on Android, macOS, and Brave/Chrome | Scanned on your device |
| Weak, reused, exposed, and old-password checks | Not included as a complete local report | **Unlocked** | Local analysis; exposed-password checks use a privacy-preserving range query |
| Duplicate logins, missing saved 2FA, and unsecured-site checks | Not included as a combined report | **Unlocked** | Local analysis |
| Phishing and suspicious-domain protection | Not included in Free | **Unlocked** | Browser phishing blocker plus local suspicious-domain checks |
| Item archive | Premium-gated | **Unlocked** | Device-local archive overlay |
| Encrypted file attachments | Not included | Not unlocked | Requires server storage and entitlement |
| File Send | Text only | Text only without server entitlement | File storage and limits remain server-controlled |
| Emergency access | Not included | Not unlocked | Requires server workflows and authorization |
| Yubico OTP and Duo account login | Not included | Not unlocked | Authentication is enforced by the server |
| Family sharing and unlimited collections | Free organization: 2 users and 2 collections | Same server limits | Organizations and sharing remain server-controlled |

OpenWarden unlocks the personal premium features that can genuinely run inside the client. It does **not** turn a free server account into a paid Bitwarden account or fake server entitlements.

Bitwarden plan details change over time; the official [Password Manager plans](https://bitwarden.com/help/password-manager-plans/) page is the source for current Free and Premium limits. OpenWarden-specific behavior is defined by the public patches in this repository.

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

## Security model

OpenWarden inherits the core encrypted-vault architecture of the pinned upstream Bitwarden clients and adds community features around the local client. That inheritance is not a substitute for an independent security audit. Treat every release—including this one—as security-sensitive software: verify the hash, inspect the patches, and build it yourself when your threat model requires it.

OpenWarden is a client, not a backup service. A device-local archive is not a substitute for a tested server backup or an export you control. Keep a recovery plan appropriate to the Bitwarden-compatible server you use.

Please report vulnerabilities privately using the process in [`SECURITY.md`](SECURITY.md). Do not post secrets, vault exports, master passwords, recovery codes, or live exploit details in a public issue.

## Contributing

Bug reports, code review, build verification, documentation corrections, and independent security analysis are welcome. For a problem, start with [`SUPPORT.md`](SUPPORT.md); for a code change, read [`CONTRIBUTING.md`](CONTRIBUTING.md).

## Independence and trademarks

OpenWarden is an independent community project. It is not affiliated with, sponsored by, or endorsed by Bitwarden, Inc. “Bitwarden” is used only to describe compatibility and upstream origin. Bitwarden trademarks remain the property of Bitwarden, Inc.; see [`NOTICE`](NOTICE).

OpenWarden source modifications are distributed under GPL-3.0. Some upstream files may carry additional license notices; those notices continue to apply.

