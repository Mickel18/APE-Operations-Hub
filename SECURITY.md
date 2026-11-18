# Security and Data Handling Policy

## Reporting a vulnerability
Email security contact: [ADD SECURITY EMAIL]
Do not open a public issue for security problems.

## Rules for this repository
1. **Never commit real client, patient, or employee data.** This includes CSV and Excel exports, and backup JSON files. The `.gitignore` blocks these types, but check `git status` before every commit.
2. **Keep the repository private.**
3. **Firebase web configuration values are not secrets**, but access must be controlled with Firebase Authentication and Firestore rules. Never add service-account keys or admin credentials to this repository.

## Access control
- Users sign in with Google. Access is granted only to the owner account (`OWNER_EMAIL`) and to accounts in the registered-users list, stored in `hub/access` in Firestore.
- Admins manage the list in Settings → Registered users. The rules enforce the same list, so a change in the app is also a change in the database rules.
- **Admins** see every tab, feedback ratings, forms received, the activity log and all settings.
- **Users** see the Results Tracker up to the Demographic report date, plus personnel and holiday settings.
- The activity log records each user's email. Entries cannot be edited or deleted.
- Remove former staff from the registered-users list as soon as they leave.

## Data storage
- Working data is stored in Cloud Firestore in the `hub/state` record.
- The activity log is stored in the `audit` collection. Its rules deny editing and deleting.
- The app does not store client data in the browser's local storage.

## Laboratory data
Lab results (CBC, chemistry, urinalysis, stool, X-ray, ECG) and the summaries built from them are health information. They are stored in the `labs` collection, readable by listed users. Do not commit lab files to the repository.

## Compliance
The app holds personal and health-related information about clients. Handling must comply with the Data Privacy Act of 2012 (Republic Act No. 10173) and the Company's data-privacy policy. Confirm requirements with the Company's Data Protection Officer before use, and review the Firebase data location and retention settings with them.
