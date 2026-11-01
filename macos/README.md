# OpenWarden for macOS

OpenWarden macOS is a universal Electron application for Intel and Apple Silicon Macs. It is based on the exact Bitwarden Clients revision in [`upstream.json`](upstream.json).

## Install

Download `OpenWarden-1.0.0-universal.dmg` from the latest release. The application uses the independent bundle identifier `org.openwarden.desktop` so it does not replace the official Bitwarden client.

The v1.0.0 application is ad-hoc signed and not Apple-notarized. Use Finder's **Open** action or **System Settings → Privacy & Security → Open Anyway** for the first launch. Do not disable Gatekeeper globally.

## Inspect the changes

The clients repository contains shared libraries used by both the desktop and browser clients. Apply the shared patch first:

```bash
git clone https://github.com/bitwarden/clients.git
cd clients
git checkout b793bdc6cf15f87814f0b3de26b795afcc7774ec
git apply --check /path/to/OpenWarden/shared/code-changes/openwarden-clients-shared.patch
git apply /path/to/OpenWarden/shared/code-changes/openwarden-clients-shared.patch
git apply --check /path/to/OpenWarden/macos/code-changes/openwarden-macos.patch
git apply /path/to/OpenWarden/macos/code-changes/openwarden-macos.patch
```

## Build

Use the Node.js and npm versions expected by the pinned upstream revision:

```bash
npm ci
npm --workspace @bitwarden/desktop run build:oss
cd apps/desktop
npx electron-builder --config electron-builder.community.json --mac --universal --dir --publish never
```

The community builder config disables upstream publishing and uses the independent OpenWarden product name and bundle identifier. A public distribution still requires your own Apple Developer certificate and notarization credentials.

## Verify the published DMG

```bash
shasum -a 256 OpenWarden-1.0.0-universal.dmg
hdiutil verify OpenWarden-1.0.0-universal.dmg
codesign --verify --deep --strict --verbose=2 /Applications/OpenWarden.app
lipo -archs /Applications/OpenWarden.app/Contents/MacOS/OpenWarden
```

The expected architectures are `x86_64 arm64`.

