# Troubleshooting OpenWarden

Start with the least destructive step and stop when the problem is resolved. Before clearing application data, confirm that the vault is synchronized and that you can sign in through another trusted client or the web vault. Unsynchronized local changes can be lost.

## Login or sync fails

1. Confirm the selected server region or self-hosted URL. A correct email and master password will still fail against the wrong server.
2. For a self-hosted server, confirm that its HTTPS certificate is valid on the affected device. Do not disable certificate validation.
3. Update OpenWarden and the server to their current stable releases. Vaultwarden can require a server update when newer client protocols ship.
4. Check that the server is reachable in a browser and that its administrator reports no outage.
5. Fully log out, close OpenWarden, reopen it, and sign in again.
6. If safe, compare the same login or operation in the corresponding official Bitwarden client.

Repeated login prompts, malformed sync data, or a failure shared by multiple clients can be server-side. A failure limited to OpenWarden is likely client-side; use the routing table in [`SUPPORT.md`](../SUPPORT.md).

## Android

- OpenWarden uses the independent package ID `org.openwarden.app`; it can coexist with official Bitwarden.
- If Android reports that an update is incompatible, compare the installed signing certificate with the fingerprint in [`android/README.md`](../android/README.md). A locally built APK cannot update the published build in place.
- Clear cache first. Clear storage or reinstall only after confirming the vault is synchronized, because both actions remove local state.
- After a reinstall, select the correct server before entering credentials.

## macOS

- v1.0.0 is ad-hoc signed and not Apple-notarized. Use Finder's **Open** command or **System Settings → Privacy & Security → Open Anyway**; never disable Gatekeeper globally.
- OpenWarden may ask macOS Keychain for access when it stores or retrieves protected local state. Confirm that the dialog names OpenWarden and macOS Keychain; do not enter credentials into an in-app imitation.
- If prompts repeat, quit duplicate OpenWarden processes, install the latest release in `/Applications`, and reopen it. Do not delete Keychain items unless you understand that local sessions and biometric unlock state may be reset.

## Brave or Chrome

- Extract the ZIP before choosing **Load unpacked**; select the directory that directly contains `manifest.json`.
- Developer-mode extensions do not update automatically. Replace the extracted directory with a verified new release, then press **Reload** on the extensions page.
- Browser profile policies, private-window permissions, and disabled background activity can affect autofill and unlock behavior.
- A new unpacked directory can receive a different local extension identity. Keep the same verified directory when updating if browser-local settings matter.

## Safe diagnostics

Record only the shortest sequence needed to reproduce the problem. Before sharing a screenshot or log, remove email addresses, server hostnames, item names, usernames, form contents, access tokens, and request or response bodies. Even encrypted payloads can reveal metadata.

Never post a vault export, database, master password, recovery code, API key, encryption key, session token, or an unreviewed full diagnostic capture. Use [private vulnerability reporting](https://github.com/parthvgupta/OpenWarden/security/advisories/new) if the problem may expose secrets or cross an authorization boundary.
