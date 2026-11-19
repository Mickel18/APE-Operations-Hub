# Firebase Setup: Google Sign-in, Registered Users and Live Data

Do this once in the Firebase project `ape-operations-hub`.

## 1. Enable Google sign-in
1. Open https://console.firebase.google.com and select **ape-operations-hub**.
2. Go to **Build → Authentication → Get started** (if not yet set up).
3. Open **Sign-in method**, choose **Google**, switch it to **Enabled**, pick a support email, and click **Save**.
4. Open **Settings → Authorized domains** and add your hosting domain, for example `your-site.netlify.app` or `YOUR-USERNAME.github.io`. `localhost` is already listed for testing.

You do not need to copy any OAuth client ID into the app. Firebase creates it automatically.

## 2. Create the Firestore database
1. Go to **Build → Firestore Database → Create database**.
2. Choose a location close to the Philippines (for example `asia-southeast1`, Singapore).
3. Start in **production mode**, then click **Create**.

## 3. Set the owner account (once)
The owner is always an admin and is the only account that can make the first changes. Set the same Google address in two places:

1. In `index.html`:
   ```js
   const OWNER_EMAIL = 'owner@company.com';
   ```
2. In `firestore.rules`, in the `isOwner()` function, the same address.

## 4. Publish the rules
1. In Firestore, open the **Rules** tab and delete the existing text.
2. Paste the full contents of `firestore.rules`.
3. Click **Publish**.

## 5. Deploy
Commit and push the updated `index.html`, then deploy it to Netlify or GitHub Pages. Google sign-in does not work when the file is double-clicked; use the hosted address or `python -m http.server 8000` for local testing.

## 6. Register staff in the app
1. Sign in with the owner account. You are the admin.
2. Open **Settings → Registered users (access)**.
3. Enter each person's Google address, choose **Admin** or **User**, and click **Add account**.
4. Each person signs in with exactly that address.

Changes take effect straight away. Removing an account signs that person out the next time the app checks access. Every change is recorded in the Activity Log.

## 7. What each role sees

| Area | Admin | User |
|---|---|---|
| Results Tracker up to Demographic report date | Yes | Yes (users only) |
| Status log, forms received, feedback columns | Yes | No |
| Feedback Analysis tab | Yes | No |
| Activity Log tab | Yes | No |
| Settings: Registered users, packages, client directory data, overall and per-test TAT | Yes | No |
| Settings: personnel and holidays | Yes | Yes |
| Client Directory, backup | Yes | No |
| Billing (phase 2: rosters, billing runs, statements) | Yes | Yes (billers) |
| Billing: prices, letterhead, signatures, deleting companies | Yes | No |

## 8. Limits to know
- **Status log:** Users can't see it on screen, but it is stored in the readable working data. A technical user could see it. Moving status history into the admin document would fix this.
- **TAT settings:** Users need the TAT and package settings to calculate due dates, so these are readable in the data even though the Settings screen hides them.
- **Simultaneous edits:** The working data is saved as one record. If two people save at the same moment, the later save overwrites the earlier one.
- **Stale screens:** A user who keeps an old screen open may save older data over a newer change. Ask users to keep the sidebar sync line visible.
- **Record size:** Firestore limits each record to 1 MB. Check the size as the number of APEs grows.
- **Offline:** Saving needs an internet connection. Without one, the sidebar shows "Save failed".

## Billing module (phases 2–4)
- The billing module lives in `billing/index.html` and runs inside the Billing tab. It uses the same Firebase project and the hub's sign-in.
- Its data is stored in `billing_companies` and `billing_settings`. The hub publishes APE companies to `billing_refs` for billers to link to.
- **Copy from ape-billing (admin, one time):** Data & Storage → Copy data. You sign in to the old project in a pop-up. The old project's Authorized domains must include the hub's address too.
- After the copy is checked, remove the copy card and `LEGACY_CONFIG` from `billing/index.html`, then delete the `ape-billing` Firebase project.
