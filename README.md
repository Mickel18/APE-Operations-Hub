# APE Operations Hub

Internal operations app for **Exact Check Diagnostic Center, Inc. – Medical Field Operations**.
It tracks Annual Physical Exam (APE) results, client directory, and client feedback.

> Proprietary and confidential. For internal use only. See [LICENSE](LICENSE).

## Features

| Area | What it does |
|---|---|
| **Results Tracker** | Add APEs with package, pax count, QC owner, signing doctor, envelope, assessment. Calculates expected release (agreed TAT, working days, holidays excluded) and per-test due dates. Records actual dates per test and actual release. Status workflow: In Process → For QC → On QC → For Signing → For Envelope → Released, with timestamped logs. |
| **Packages** | Configurable package types (e.g., APE, DT only). Each defines which tests apply and whether the overall TAT applies. |
| **TAT conflict check** | Flags APEs where a test is due after the overall expected release. |
| **Feedback** | Nine service aspects rated Excellent / Satisfactory / Needs Improvement per APE in a pop-up. Category totals are calculated automatically. Forms received and companies responded are tracked. |
| **Feedback Analysis** | Summary cards, aspect table, monthly tracker, APEs by month, demographics pie charts. Excel export. |
| **Client Directory** | Import CSV, add manually, edit inline, delete by import batch. Used for company suggestions and payment-mode demographics. |
| **Activity Log** | Records every change with date, time, old and new values. Searchable, Excel export. |
| **Settings** | Personnel list, holidays, overall TAT per pax tier, per-test TAT, packages, directory data. |
| **Backup** | Save and load everything as a JSON file. |
| **Auto-save** | Data is saved in the browser automatically and restored on reopen. |
| **Excel export** | Results, status logs, feedback, directory, activity log, and demographic data as `.xlsx`. |

## Repository layout

```
ape-operations-hub/
├── index.html        The complete application (single file, no build step)
├── README.md         This file
├── LICENSE           Proprietary license
├── SECURITY.md       Data-handling and security policy
├── CHANGELOG.md      Version history
├── .gitignore        Keeps client data out of the repository
└── docs/
    └── SETUP.md      Step-by-step GitHub and hosting setup
```

## Running the app

No installation is needed.

1. Download or clone this repository.
2. Open `index.html` in a current browser (Chrome, Edge, or Firefox).
3. Internet access is needed the first time you use **Download Excel** (the Excel library loads from cdnjs.cloudflare.com). Everything else works offline.

## Data storage

- **Auto-save:** Data is kept in the browser's local storage on that device and profile.
- **Backups:** Use **Save backup (JSON)** regularly and keep copies in approved, encrypted storage.
- **Moving to another PC:** Copy `index.html` and a backup file, open `index.html`, then click **Load backup**.
- **Clearing browser data erases the auto-saved data.** Keep backups.

## Live deployment

Read this before publishing.

- **GitHub Pages** can host `index.html` as a website. It serves the app only.
- **It does not share data between users.** Each browser keeps its own data.
- **It does not restrict access.** Anyone with the link can open the app. Use a private repository and keep the Pages site private, or do not publish it.
- **Shared, role-based, online use requires a backend** (for example, Supabase, Firebase, or a server-side application with user logins, roles, and a database). Plan this with the Company's IT and Data Protection Officer before storing client data online.

See [docs/SETUP.md](docs/SETUP.md) for the GitHub steps.

## Versioning

The app is a single file. Changes are listed in [CHANGELOG.md](CHANGELOG.md). Commit each new version with a message that names the version, for example `v20: add ...`.

## Third-party software

- [SheetJS](https://sheetjs.com) (xlsx), Apache License 2.0, loaded from cdnjs.cloudflare.com.

## Contact

Maintainer: [ADD NAME AND EMAIL]
