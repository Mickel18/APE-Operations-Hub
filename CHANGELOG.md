# Changelog

All notable changes to APE Operations Hub are listed here, newest first.

## v25
- Billing module integrated into the Billing tab (`billing/index.html`), using the hub's sign-in and Firebase project.
- Billers see billing only; prices and company deletion are admin-only in the module.
- Billing companies are linked to APE companies from the Client Directory.
- One-time admin tool copies data from the old ape-billing project.

## v24
- Third role: biller. Billers see only the Billing tab.
- Registered users list has three roles: admin, user, biller.
- Billing rules added (`billing_companies`, `billing_settings`): billers can edit billing data but not prices; only admins can delete companies and change settings.
- Billing tab placeholder, ready for the billing module (phase 2).

## v23
- Significant Findings tab: upload the lab CSV exports (patient master, CBC, CHEM, URINALYSIS, STOOL, X-RAY) together; each file is recognized from its headers.
- Summary per patient in the workbook's Summary Report format: CBC, chemistry, urinalysis, fecalysis, serology, X-ray and ECG, with the significant-findings rules from the workbook Instructions tab.
- Pap smear, drug test and serology entered by hand, saved per patient.
- Excel export in the Summary Report layout.
- Lab reference ranges editable in Settings (admins). Defaults must be confirmed by the laboratory.
- Lab records stored in Firestore (`labs`), readable and writable by listed users.

## v22
- Registered users managed in the app (Settings → Registered users), stored in Firestore (`hub/access`).
- Only the owner account is set in code; everyone else is added, given a role, or removed in the app.
- Role changes and removals take effect without redeploying. Changes are recorded in the Activity Log.

## v21
- Two roles: admin and user, each with its own email list.
- Feedback ratings and forms received stored in an admin-only Firestore document (`hub/admin`).
- Feedback Analysis tab and Activity Log visible to admins only.
- Feedback columns and Status log hidden from users in the Results Tracker.
- Settings for users: personnel and holidays only.
- Released rows highlighted in a lighter green.

## v20
- Google sign-in on a login page with a #96C93D background.
- Access limited to an allowlist of Google accounts (also enforced in Firestore rules).
- Working data stored in Cloud Firestore and shared live by all authorized users.
- Activity Log stores the user email for each change and is kept in its own collection (entries cannot be edited or deleted).
- Browser-only autosave replaced by cloud saving. Google Analytics removed.

## v19
- Summary report date and Demographic report date columns placed after Assessment.

## v18
- Summary report date and Demographic report date columns added to the Results Tracker.
- Report sub-tabs removed.

## v17
- Sidebar shows full names when expanded and icons only when collapsed.
- Collapse button moved into the sidebar header (◀ / ▶).

## v16
- Company name editable in the Results Tracker after entry.

## v15
- Automatic saving in the browser; data reloads when the file is reopened.

## v14
- Excellent / Satisfactory / Needs Improvement totals calculated from per-aspect ratings.

## v13
- Per-aspect feedback entry moved into a pop-up window opened from each row.

## v12
- Category totals made editable per APE (superseded by v14).

## v11
- Activity Log in the sidebar: records changes with date, time, old and new values.

## v10
- Actual release date entered manually; status "Released" no longer fills it in.

## v9
- Forms received per APE; forms and companies responded in Feedback Analysis.
- Demographics view with pie charts (package, pax tier, payment mode).

## v8
- Per-APE feedback tallies by aspect; Feedback Analysis calculated automatically.
- Seeded example feedback figures removed.

## v7
- APE date and Package removed from the Client Directory.

## v6
- Package types (APE, DT only, editable) with per-package tests and TAT rules.

## v5
- Sidebar collapse; manual client entry; directory data deletable by import batch.

## v4
- TAT conflict warning when a test is due after the overall expected release.

## v3
- Overall expected release from agreed working-day TAT (10 / 14 / 21 days).
- Holiday list; per-test actual date columns.

## v2
- Green sidebar with company name; status workflow with timestamped logs.
- Dropdowns for QC owner, envelope, assessment; editable personnel list.
- Client directory CSV import; monthly feedback tracker.

## v1
- First working version: Results Tracker, Client Directory, Feedback Analysis, TAT settings.
