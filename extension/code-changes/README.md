# Extension code changes

`openwarden-extension.patch` contains the Brave/Chrome-specific changes generated against the upstream commit in [`../upstream.json`](../upstream.json). Apply [`../../shared/code-changes/openwarden-clients-shared.patch`](../../shared/code-changes/openwarden-clients-shared.patch) first.

Patch SHA-256:

```text
60c21f8f5a9dad1d32c51108d9045e530c0fa5eb3785409c58a9a2eab99fe9fb  openwarden-extension.patch
```

The patch includes OpenWarden identity and assets, community feature access, local vault-health and archive behavior, premium-promotion removal, tests, and the upstream compatibility-version fix. It excludes generated build output.

