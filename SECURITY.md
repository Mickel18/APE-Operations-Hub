# Security and Data Handling Policy

## Reporting a vulnerability
Email security contact: [ADD SECURITY EMAIL]
Do not open a public issue for security problems.

## Rules for this repository
1. **Never commit real client, patient, or employee data.** This includes CSV
   exports of the Client Directory, Excel reports, and backup JSON files. The
   `.gitignore` blocks these types, but check `git status` before every commit.
2. **Keep the repository private.** The app is internal to the Company.
3. **Do not hard-code credentials, API keys, or passwords** in `index.html`.
   The app currently has no login; see README "Live deployment" before adding one.

## How the app stores data
- Data is stored in the browser's local storage on the device that uses it.
  It is not sent to any server by this version of the app.
- Anyone with access to a device and its browser profile can read that data.
- Backup files (JSON) contain all data in plain text. Store them only on
  approved, encrypted storage and delete copies you no longer need.

## Compliance
The app holds personal and health-related information about clients. Handling
of this data must comply with the Data Privacy Act of 2012 (Republic Act No.
10173) and the Company's own data-privacy policy. Confirm requirements with the
Company's Data Protection Officer before deploying the app beyond one device.
