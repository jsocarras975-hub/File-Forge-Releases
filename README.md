# APK Bench

**The offline file manager and APK editor for Android.** Browse and manage files, inspect and edit APKs, decompile apps to readable code, rebuild and re-sign them — all on your phone, with no internet, no account, and no ads.

## Download

Grab the APK from the [latest release](https://github.com/jsocarras975-hub/APK-Bench-Releases/releases/latest). It installs over older versions — same signing key since v1.1.

- **Android 8.0 or newer** (minSdk 26)
- Also available through **Obtainium** (GitHub Releases source)
- **Not on the Play Store** — APK-modding features don't fit the Play Store's policies, so releases live here

## Current version

**v2.8.2** — Ghost rows clean themselves, and Trash loads in the background (4,971 tests passing)

- Lists check every entry against what's actually on the phone and quietly drop files that are already gone — no more "ghost" rows that refuse to delete.
- Deleting a ghost row drops it on the spot and says plainly that the file is already gone.
- Opening Trash no longer freezes the screen: it loads in the background with a "Loading Trash…" state, even with a huge Trash.
- Full changelog is in each release's notes.

## About APK Bench

APK Bench started as a hand-written, offline file manager and grew into a full APK workbench. Everything runs on-device. The app has no internet permission: it never uploads, syncs, or phones home. There is no account, no sign-in, and no tracking. Crash reports and error logs stay on your phone (`ArcForge/Diagnostics/crash-log.txt`), where you can read or share them yourself.

### File management

- **Browse everything** — internal storage and SD card, with list and grid views, sorting, and a dual-pane mode for two folders side by side.
- **Batch tools** — select many files at once to copy, move, delete, rename, share, or zip. Long-press a file or folder for the full menu.
- **Search** — find files by name, and deep-search inside folders. Recents, Downloads, and Favorites keep the files you come back to.
- **Archives** — create and open ZIP files. Unpacking is capped at 10,000 entries per archive as a safety limit against zip bombs; the copy-style Extract (from Installed Apps) has no cap.
- **Organizer** — long-press a folder and choose "Tidy this folder…" to auto-sort its files into Images, Videos, APKs, Documents, Audio, Archives, and Other, with optional Year-Month grouping and your own extension/name rules. Every tidy run shows a preview first, runs as a background job with progress and cancel, and can be undone with one tap ("Undo last tidy"). **Tags** (8 colours, on-device) and **smart folders** (live rules on tag, type, name, size, or date) keep things findable.
- **Trash** — deleting moves files to Trash instead of erasing them. Files stay 30 days, then are deleted for good; the Trash holds up to 1 GB. Restore anything from ☰ → BROWSE → Trash, or empty it from there.
- **Background jobs** — long work (copies, zips, decompiles, tidies) runs as a job with progress and cancel, from ☰ → TOOLS → Background jobs.
- **91 in-app tutorials** — every tool ships with a detailed, plain-language tutorial explaining what it does and how to use it.

### APK tools

- **Inspect any APK** — manifest, permissions, components, signatures, and certificates, plus what's inside the file (resources, assets, native libraries, DEX files).
- **Compare two APKs** — see what changed between versions, including tracker and framework detection.
- **Decompile to project** — long-press an APK → "Decompile to project…" and get a folder in `ArcForge/Decompiled/<app name>/` with a readable `AndroidManifest.xml`, `res/` (values as XML), `assets/`, `lib/`, and `smali/` (one `.smali` file per class). A `README.txt` explains what was left out (no `apktool.yml` — this is not an apktool project, and `META-INF` is left out on purpose). To edit, change a `.smali` file, then rebuild from the DEX screen. The original APK is never changed.
- **Smali and DEX** — view DEX files, search Smali, convert Smali to Java, edit and rebuild DEX. DEX version 035 is supported; 036 is not. SigStrip patches method signatures, with correct handling of `.registers` counts.
- **Rebuild and re-sign** — modify an APK (for example, strip a signature check) and rebuild a signed copy with the on-device key. The rebuild keeps the manifest and every entry intact; only the DEX and the signature change.
- **Split APK merge** — merge split bundles (`.apks` / `.xapk`: base + config splits) into one installable APK. A base APK alone often won't install — the native code for your chip lives in the config split, so the merged file is the one to install.
- **Install with Shizuku** — open an APK → ⋮ menu → "Install with Shizuku…". Shizuku gives shell (ADB-level) powers, not root: it can install and manage apps, but it can't read other apps' private data, write the system partition, or fake signatures.
- **Clone an app** — make an installable copy under a new package name.
- **Installed apps** — list installed apps, extract their APKs (base + splits), and back them up.

### Signing ledger and Vault

- **Signing ledger** — every key and every signature the app makes is recorded automatically, so you can always tell which key signed which APK.
- **Vault** — device-bound storage for keys and sensitive files, protected by the on-device Keystore, with virtual folders and a Duress PIN. AI code explain and edit are Premium features; Premium is a separate app, and the base app stays offline-only.
- **Remote Management** — manage files from another device on the same Wi-Fi (port 8080). It is LAN-only and has no password, so anyone on the same Wi-Fi can read and write while it runs; it stops the moment you leave the screen.

### Extras

- **Terminal** — run shell commands on the phone.
- **Screen Color Picker** — pick a colour from anything on screen.
- **Activity Record** — see the activity trail behind an app's screens.
- **Smali Instructions** — reference for Smali opcodes.
- **TSV export/import** — move lists and data in and out as tab-separated files.
- **Media** — built-in players for audio and video, a full-screen PDF viewer, and an image viewer.
- **Measure apps** — see how much space apps and folders use.

### What APK Bench is not

- **Not a root app.** It works without root. Shizuku adds shell-level powers on supported phones, but root-only things (other apps' private data, system writes) stay out of reach.
- **Not a store app.** There is no store, no in-app purchases in the base app, and no ads.
- **Not a backup service.** Everything lives on your phone unless you copy it somewhere yourself.

## Installing and updating

1. Download the APK from the latest release above.
2. Open it on your phone and allow "Install unknown apps" for your browser or file manager when asked.
3. Updates install right over the old version — your settings, Trash, Vault, and tags carry over. If an update ever refuses to install, check that it is signed with the same key (all releases here are) and that no split or modded copy with a different signature is in the way.

## Source code

Source code is kept private; this repo only hosts releases. The source lives in a private repository — the auto-generated "Source code" archives attached to each release here contain only this README.
