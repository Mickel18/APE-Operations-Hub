# Setup: GitHub and Hosting

## 1. Create the repository on GitHub (private)

1. Sign in at https://github.com.
2. Click **+ → New repository**.
3. Repository name: `ape-operations-hub`.
4. Select **Private**.
5. Do **not** add a README, .gitignore, or license on GitHub (this folder already has them).
6. Click **Create repository** and copy the URL, for example `https://github.com/YOUR-USERNAME/ape-operations-hub.git`.

## 2. Push this folder from your PC

Install Git from https://git-scm.com if it is not installed. Then open a terminal in this folder:

```bash
git init
git branch -M main
git add .
git status          # check: no .xlsx, .csv, or backup .json files listed
git commit -m "v19: initial commit of APE Operations Hub"
git remote add origin https://github.com/YOUR-USERNAME/ape-operations-hub.git
git push -u origin main
```

GitHub will ask you to sign in. Use a Personal Access Token as the password, or the GitHub Desktop app.

## 3. Updating the app later

```bash
# after replacing index.html with the new version
git add index.html CHANGELOG.md
git commit -m "v20: describe the change"
git push
```

## 4. Optional: GitHub Pages (hosted link)

GitHub Pages on a **private** repository requires a GitHub Pro, Team, or Enterprise plan. On a free plan, Pages requires a public repository, which exposes the code to everyone. Do not enable Pages on a public repository unless that is acceptable.

1. Repository → **Settings → Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)`. Click **Save**.
4. After a minute, the site appears at `https://YOUR-USERNAME.github.io/ape-operations-hub/`.

Remember: the hosted page has no login, and each browser keeps its own data. See "Live deployment" in the README.

## 5. Recommended next step for shared live use

Shared data and per-user permissions need a backend. Options to evaluate with IT:

- **Supabase** (hosted Postgres with built-in logins and row-level security). The current single-file app can be connected to it with moderate changes.
- **Firebase** (Google, with login and database).
- **Self-hosted** Node.js or Python server with a database, hosted on the Company's network.

Share the requirements (number of users, roles, which data each role can see) and the app can be adapted accordingly.
