# APE Operations Hub

Internal operations app for **Exact Check Diagnostic Center, Inc. – Medical Field Operations**.
It tracks Annual Physical Exam (APE) results, the client directory, and client feedback.

> Proprietary and confidential. For internal use only. See [LICENSE](LICENSE).

## Features

| Area | What it does |
|---|---|
| **Sign-in** | Google sign-in. Only accounts on the allowlist can use the app. |
| **Results Tracker** | Add APEs with package, pax count, QC owner, signing doctor, envelope, assessment. Calculates expected release (agreed TAT, working days, holidays excluded) and per-test due dates. Records actual dates per test and actual release. Status workflow with timestamped logs. Summary and demographic report date columns. |
| **Packages** | Configurable package types (e.g., APE, DT only). Each defines which tests apply and whether the overall TAT applies. |
| **TAT conflict check** | Flags APEs where a test is due after the overall expected release. |
| **Feedback** | Nine service aspects rated Excellent / Satisfactory / Needs Improvement per APE in a pop-up. Category totals are calculated automatically. Forms received and companies responded are tracked. |
| **Feedback Analysis** | Summary cards, aspect table, monthly tracker, APEs by month, demographics pie charts. Excel export. |
| **Significant Findings** | Upload lab CSV exports and generate the Summary of Significant Findings per company and patient, following the workbook Instructions tab. Manual entries for serology, pap smear and drug test. Excel export. |
| **Client Directory** | Import CSV, add manually, edit inline, delete by import batch. |
| **Activity Log** | Records every change with date, time, user, old and new values. Searchable, Excel export. |
| **Settings** | Personnel list, holidays, overall TAT per pax tier, per-test TAT, packages, directory data. |
| **Live sync** | Data is stored in Cloud Firestore and shared by all authorized users. |
| **Backup** | Save and load working data as a JSON file. |
| **Excel export** | Results, status logs, feedback, directory, activity log, and demographic data as `.xlsx`. |

## Repository layout

```
ape-operations-hub/
├── index.html          The application (single file, no build step)
├── firestore.rules     Database access rules (paste into Firebase Console)
├── README.md           This file
├── LICENSE             Proprietary license
├── SECURITY.md         Data-handling and security policy
├── CHANGELOG.md        Version history
├── .gitignore          Keeps client data out of the repository
└── docs/
    ├── SETUP.md            GitHub and hosting steps
    └── FIREBASE_SETUP.md   Google sign-in, Firestore, and allowlist steps
```

## Before first use

1. Complete [docs/FIREBASE_SETUP.md](docs/FIREBASE_SETUP.md).
2. Replace the placeholder email in `index.html` (`ALLOWED_EMAILS`) and in `firestore.rules`. Both lists must match.
3. Run the app from a web address, not by double-clicking the file. Google sign-in does not work from a local file.

## Data storage

- Working data is stored in Cloud Firestore (project `ape-operations-hub`), in the `hub/state` record.
- The activity log is stored in the `audit` collection. Entries cannot be edited or deleted.
- Backup files (JSON) are copies of the working data. Keep them in approved, encrypted storage.

## Limitations

- Saving needs an internet connection.
- The working data is saved as one record, so two people editing at the same moment can overwrite each other's most recent change. See the notes in docs/FIREBASE_SETUP.md.
- Firestore records are limited to 1 MB. Monitor the data size as the number of APEs grows.

## Versioning

Changes are listed in [CHANGELOG.md](CHANGELOG.md). Commit each new version with a message that names it, for example `v21: add ...`.

## Third-party software

- [Firebase](https://firebase.google.com) (Authentication and Firestore), Google.
- [SheetJS](https://sheetjs.com) (xlsx), Apache License 2.0, loaded from cdnjs.cloudflare.com.

## Contact

Maintainer: [Mickel18]
