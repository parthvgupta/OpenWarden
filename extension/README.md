# OpenWarden for Brave and Chrome

OpenWarden's Chromium extension is a Manifest V3 build for Brave, Chrome, and compatible Chromium browsers. It is based on the exact Bitwarden Clients revision in [`upstream.json`](upstream.json).

## Install

1. Download `OpenWarden-1.0.0-chrome-brave.zip` from the latest release.
2. Verify its SHA-256 hash.
3. Extract the ZIP.
4. Open `brave://extensions` or `chrome://extensions`.
5. Enable **Developer mode**.
6. Choose **Load unpacked** and select the extracted directory containing `manifest.json`.

Developer-mode extensions do not update automatically. Inspect and install future versions manually.

## Inspect the changes

Apply the shared patch before the extension patch:

```bash
git clone https://github.com/bitwarden/clients.git
cd clients
git checkout b793bdc6cf15f87814f0b3de26b795afcc7774ec
git apply --check /path/to/OpenWarden/shared/code-changes/openwarden-clients-shared.patch
git apply /path/to/OpenWarden/shared/code-changes/openwarden-clients-shared.patch
git apply --check /path/to/OpenWarden/extension/code-changes/openwarden-extension.patch
git apply /path/to/OpenWarden/extension/code-changes/openwarden-extension.patch
```

## Build

```bash
npm ci
cd apps/browser
npm run dist:chrome
```

The resulting archive is `apps/browser/dist/dist-chrome.zip`.

## Verify the published extension

```bash
shasum -a 256 OpenWarden-1.0.0-chrome-brave.zip
unzip -t OpenWarden-1.0.0-chrome-brave.zip
unzip -p OpenWarden-1.0.0-chrome-brave.zip manifest.json
```

The manifest should report name `OpenWarden`, version `1.0.0`, and manifest version `3`.

