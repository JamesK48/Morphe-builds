# Morphe builds

Automatic Morphe-patched builds of YouTube, YouTube Music, Reddit and Twitter (Piko), signed with my own Morphe Manager key so they install as updates over the apps already on my phone.

## How it works

- **CI** (`.github/workflows/ci.yml`) runs every 6 hours. It checks whether any patch source has a new release, and starts a build if so.
- **Build** (`.github/workflows/build.yml`) downloads the newest app version the patches support (from APKMirror, falling back to an archive.org mirror), verifies the original APK's signature against `sig.txt`, patches it with Morphe CLI, signs it with my key and publishes everything as a GitHub release.
- **Obtainium** on the phone watches the releases and installs each new APK.

## Settings

- Apps and patch sources: `config.toml` (options in `CONFIG.md`).
- Signing key: repository secret `KEYSTORE_BASE64` (the Morphe Manager keystore export, base64-encoded). The build refuses to run without it.
- To build right now: Actions → CI → Run workflow.

## Credits

Based on [j-hc/revanced-magisk-module](https://github.com/j-hc/revanced-magisk-module) (GPL-3.0). Patches by [MorpheApp](https://github.com/MorpheApp/morphe-patches) and [crimera/piko](https://github.com/crimera/piko).
