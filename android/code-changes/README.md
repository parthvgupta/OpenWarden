# Android code changes

`openwarden-android.patch` is a complete binary-capable Git patch generated against the upstream commit in [`../upstream.json`](../upstream.json). It includes tracked edits and all new OpenWarden source files required to build Android v1.0.0.

Patch SHA-256:

```text
2959aa9eaab52e8093e68ef7e15f7cda46e7c83e8aa83b1c85ae7cc9db26b082  openwarden-android.patch
```

Use `git apply --check` before applying it. The patch intentionally excludes local build output, the private release keystore, credentials, and machine-specific configuration.

