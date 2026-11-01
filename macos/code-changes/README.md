# macOS code changes

`openwarden-macos.patch` contains the desktop-specific changes generated against the upstream commit in [`../upstream.json`](../upstream.json). Apply [`../../shared/code-changes/openwarden-clients-shared.patch`](../../shared/code-changes/openwarden-clients-shared.patch) first.

Patch SHA-256:

```text
4fb03e34e0bfceb94061076ebd1d254d731ca78c0eea07a1b1e7e6e77f7eb672  openwarden-macos.patch
```

The patch includes the OpenWarden application identity, community feature wiring, update-policy changes, black-and-gold assets, tests, and packaging configuration. It excludes signing credentials and generated applications or disk images.

