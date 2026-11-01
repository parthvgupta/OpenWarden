# OpenWarden for Android

OpenWarden Android is based on the exact upstream revision recorded in [`upstream.json`](upstream.json). All modifications, including new files and binary launcher assets, are contained in [`code-changes/openwarden-android.patch`](code-changes/openwarden-android.patch).

## Install

Download `OpenWarden-1.0.0-android.apk` from the latest GitHub release. The package identifier is `org.openwarden.app` and Android 10 or newer is required.

The release signing-certificate SHA-256 fingerprint is:

```text
46:DD:F3:2B:E4:5B:DF:B1:EC:59:74:E1:11:21:23:88:60:8A:DE:34:5B:AB:16:3A:C9:5F:CB:9F:08:A7:BA:2E
```

## Inspect the changes

```bash
git clone https://github.com/bitwarden/android.git
cd android
git checkout 262dba3e663b2f9a4f2196515331bce9d7b58ad9
git apply --stat /path/to/OpenWarden/android/code-changes/openwarden-android.patch
git apply --check /path/to/OpenWarden/android/code-changes/openwarden-android.patch
git apply /path/to/OpenWarden/android/code-changes/openwarden-android.patch
```

Review the patch before building:

```bash
git diff --stat
git diff
```

## Build

Install JDK 21 and the Android SDK required by the upstream project. For a locally signed debug build:

```bash
./gradlew :app:assembleFdroidDebug
```

For a release build, create your own Android keystore and pass it to Gradle. Never reuse the public example values as real secrets:

```bash
./gradlew :app:assembleFdroidRelease \
  -Pandroid.injected.signing.store.file=/absolute/path/to/release.jks \
  -Pandroid.injected.signing.store.password="$STORE_PASSWORD" \
  -Pandroid.injected.signing.key.alias="$KEY_ALIAS" \
  -Pandroid.injected.signing.key.password="$KEY_PASSWORD"
```

Your locally signed APK will have a different certificate fingerprint from the official OpenWarden release and cannot update it in place.

## Verify the published APK

```bash
shasum -a 256 OpenWarden-1.0.0-android.apk
apksigner verify --verbose --print-certs OpenWarden-1.0.0-android.apk
aapt2 dump badging OpenWarden-1.0.0-android.apk
```

Expected package: `org.openwarden.app`; expected version: `1.0.0`.

