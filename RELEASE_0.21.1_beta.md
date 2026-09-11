# ShiftCare 0.21.1 Beta

A beta update for the Windows scheduling application and employee portal integration.

**Windows signing:** this beta installer and application are unsigned (`NotSigned`). The in-app updater continues to require a trusted publisher signature and will reject this installer. Automatic installation through the updater is therefore unavailable for this build. No signature checks have been disabled.

## Changes

- Synchronization polls incoming portal requests even without outgoing changes, merges independent edits, and preserves both copies on conflicts. Startup normalization no longer queues unchanged preferences.
- Repeated sign-in and delayed server responses preserve pending preferences, deletions, department access restrictions, and stable record identifiers.
- Organization settings and scheduling constraints are isolated by organization; database migrations upgrade the schema to version 26.
- SQLite backup includes committed WAL data. Restore coordinates open connections and recovers the previous database if migration fails. Portable backups remove sessions and tokens and require sign-in again.
- Multi-position generation handles shared employees before assigning days off. Portal settings handle loading, retry, save, and network errors.
- Updated RU/EN/HE interface, mobile RTL, and PWA caching. The application is organized into a modular `shiftcare` package.

## Before updating

Keep a full recovery backup of the existing database. This version requires the matching 0.21.1 cloud service for synchronization. Matching local/cloud data establish a shared baseline. A legacy installation without a baseline can also accept proven new weekly preferences or requests created after its last successful push when all shared records still match; ambiguous differences require reconciliation. Old synchronization import protocol requests are rejected.

Schema 26 changes organization settings keys. Rolling back requires a matched application and database backup from before migration; switching only the application version is insufficient.

## Verification

- Local Python suite: 223 tests passed with no skips, including real PostgreSQL 16.15 and temporary SQLite databases.
- Twelve Node interface/PWA checks, metadata consistency, and browser RU/EN/HE and narrow RTL checks passed.
- Windows payload inspected: 847 files; all 63 `shiftcare` modules and 48 static/template resources match the final source. No working databases, `.env`, private directories, or backup files are included.
- Installation on a clean Windows machine and a signed updater installation have not been validated.

## Windows installer

`ShiftCare_Setup_0.21.1-beta.exe` — 31,578,616 bytes.

SHA256: `c85d28b6161b5421c7eab309514591370ec833e8442a0c8d6e8a00af688998a1`

Download `SHA256SUMS.txt` alongside the installer to check the downloaded file. The app executable relies on its accompanying runtime directory; the installer is the distributable package.

## Android tablet debug build

`ShiftCare_Android_0.21.1-beta-tablet-debug.apk` — 25,114,591 bytes; arm64-v8a, Android 8.0/API 26 or newer. Version name `0.21.1-beta-tablet-current`, version code 17.

This is a debug-signed tablet test build, not a production APK. A physical-device installation has not been validated. All 114 bundled application/resource files were compared with the final source; no working databases or private files are included.

SHA256: `f4fe8239f5242ab82a3b55529209e54b44e4280803f90ce073f7687f2e2b6f51`

## Publication status

Published on 2026-09-11 as an explicitly approved unsigned Windows beta for manual distribution. The updater's trusted-signature requirement remains enabled; this release does not enable automatic installation of unsigned files. The Android asset in the standard release is explicitly labeled as a debug tablet build.

The live employee portal at [portal.shiftcare.co.il](https://portal.shiftcare.co.il/login) and [schedule-app-beta.web.app](https://schedule-app-beta.web.app/login) was upgraded to `0.21.1_beta` before the installers were published. Liveness, readiness, and PostgreSQL connectivity checks passed.

[Original tagged source CI](https://github.com/LittleDespairs/ShiftCare-Demo-Beta/actions/runs/34632678203) passed for commit `ac95bf63bd397a9035fa5884b2320b53697e1af1`: Linux Python 3.12 and 3.13, plus Windows. The existing release tag retains the original snapshot; the current `main` branch contains the synchronization correction used by the refreshed Windows installer. The version and asset URLs are unchanged, and the Android debug APK retains its original checksum.
