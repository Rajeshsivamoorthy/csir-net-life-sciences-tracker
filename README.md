# CSIR-NET Life Sciences Study Tracker

A static, responsive study dashboard for the November 2026–April 2027 plan. It works on GitHub Pages with no build step.

## Features
- 26-week topic checklist with month/week navigation and topic search
- Overall, monthly, and subject-level progress indicators
- Daily two-hour routine and a 50-minute focus timer
- Weekly goals checklist, mock-test scores, revision reminders
- Browser-local progress storage and JSON export/import
- Optional GitHub repository sync: load/save progress as `progress.json`

## Publish with GitHub Pages
1. Create a repository, for example `csir-net-life-sciences-tracker`.
2. Upload `index.html` and `README.md` to the repository root and commit to `main`.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select branch `main` and folder `/(root)`, then click **Save**.
6. Your site will appear at `https://YOUR-USERNAME.github.io/csir-net-life-sciences-tracker/` after deployment.

## Enable repository progress sync
The app can store your tracker state in a `progress.json` file in the same repository through the GitHub Contents API.

1. On GitHub, open **Settings → Developer settings → Personal access tokens → Fine-grained tokens** and create a token restricted to this one repository.
2. Give it **Contents: Read and write** repository permission. Do not grant unrelated permissions.
3. In the app's **GitHub repository sync** panel, enter your GitHub owner/username, repository name, and token.
4. Click **Save progress to GitHub** to create/update `progress.json` on the `main` branch.
5. On another device, open the website, enter the same owner/repository and token, then click **Load progress from GitHub**.

### Security notes
- Never hard-code your token in `index.html`, commit it, or share it. The app does not save the token to local storage; it remains only in the current page's memory. Clear the token field and close the tab when finished.
- A fine-grained token with repository Contents write access can change files in the selected repository. Revoke it from GitHub settings if it is no longer needed.
- `progress.json` is publicly readable in a public repository. Do not store sensitive information there. This approach uses a GitHub token in the browser and is suitable only if you understand that the token is exposed to the browser session and its environment. For stronger security, use a backend such as Supabase or a serverless function rather than direct browser-to-GitHub writes.
- GitHub Pages is static hosting; it cannot write repository files without an authenticated API request.
- Save to GitHub manually after study updates. Normal edits are still saved locally in that browser; they are not automatically uploaded.

## Local backup
Use **Export backup** and **Import backup** to transfer a JSON backup without GitHub sync.

## Update the app
Edit `index.html` on GitHub and commit the change. GitHub Pages redeploys automatically.
