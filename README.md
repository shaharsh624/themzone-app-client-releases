# The M Zone app releases

Android APKs of **The M Zone** retailer app. This repository holds no source
code: each version is a [release](../../releases) with the APK attached as
`themzone.apk`.

## Download link used by the app

Admin dashboard → **App settings** → **Download link** (set once):

```
https://github.com/shaharsh624/themzone-app-client-releases/releases/latest/download/themzone.apk
```

It always points to the newest release. The app downloads it in the
background, checks it is a newer build of The M Zone, and shows **Install**.

## Publishing a version

From the app repository (`themzone-app-client`), on an up-to-date `main`
with `version:` raised in `pubspec.yaml`:

```bash
scripts/release-prod.sh "What changed"
```

The script checks everything first, builds the signed and obfuscated APK,
copies it to this folder (`apks/themzone-<version>.apk`), creates release
`v<version>` here with the APK as `themzone.apk`, and downloads it back
through the link above to compare. Then set **Latest version** in the admin
App settings.

Always keep the asset name `themzone.apk`, or the link above stops working.

## This folder on the development computer

Cloned beside the app repository, as `../themzone-app-client-releases`.
`apks/` keeps a local copy of every released APK; APKs are never committed
(see `.gitignore`), because GitHub stores them as release assets.
