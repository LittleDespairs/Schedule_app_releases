# Schedule App Releases

Public release channel for Schedule App Windows installers.

This repository stores release assets only. Source code remains private.

## 0.15.7_beta - 2026-05-01

- Fixed the hosted employee portal login layout so the call-to-action no longer overlaps the text panel.
- Treated `portal.shiftcare.co.il` as a hosted cloud origin in the auth client.
- Updated Cloud Build defaults to use `https://portal.shiftcare.co.il`.
- Updated installer metadata to `0.15.7_beta`.

Installer asset: `ShiftCare_Setup_0.15.7-beta.exe`

## 0.15.6_beta - 2026-05-01

- Polished the Organization page with a language switcher and complete RU/EN/HE translations.
- Employee portal and invitation links now display as full URLs with open/copy actions.
- Desktop builds now fall back to `https://portal.shiftcare.co.il` for employee portal links.
- Updated installer metadata to `0.15.6_beta`.

Installer asset: `ShiftCare_Setup_0.15.6-beta.exe`

## 0.15.5_beta - 2026-05-01

- Added local license runtime, trial/grace/expiry enforcement, and employee-limit checks.
- Added `Settings -> License & Support` for license status, activation code entry, offline license import, and support diagnostics.
- Added support-issued `.shiftcare-license` and activation-code fallback flow.
- Updated installer metadata to `0.15.5_beta`.

Installer asset: `ShiftCare_Setup_0.15.5-beta.exe`
