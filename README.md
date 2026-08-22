# Road to Amazon / FAANG — Placement Prep Tracker

A single-page dashboard that stores your daily progress **as commits in your own GitHub repo** — no server, no database. Every checkbox tick writes `progress.json` back to your repo via the GitHub API, straight from your browser.

## 1. Create a repo
Create a new GitHub repo, e.g. `placement-tracker` (private is fine).
Push `index.html` (this folder) into it — that's your whole app.

## 2. (Optional) Host it with GitHub Pages
Repo → Settings → Pages → Deploy from branch → pick `main` → `/ (root)`.
You'll get a URL like `https://<you>.github.io/placement-tracker/`.
You can also just open `index.html` locally in a browser — it works the same way.

## 3. Create a fine-grained access token
GitHub → Settings → Developer settings → Personal access tokens → **Fine-grained tokens** → Generate new token:
- **Repository access:** only this one repo
- **Permissions:** Contents → **Read and write**
- Set an expiry you're comfortable with (you can regenerate later)

Copy the token — GitHub only shows it once.

## 4. Connect the app
Open the page → click **⚙️** → fill in:
- Repo owner (your GitHub username)
- Repo name
- Branch (`main`)
- File path (`progress.json` — created automatically on first save)
- Token (from step 3)

Click **Save & Sync**. It'll create `progress.json` in your repo immediately.

## How it works
- Every tick/untick commits an updated `progress.json` with a message describing what changed (e.g. `Tuesday: checked DSA (2/3 today)`).
- **Reset Week** archives the finished week's completion % into a `history` list inside `progress.json`, then starts a fresh unchecked week. Your streak and achievements carry over.
- Open your repo's commit history any time to see a timeline of your prep — same idea as a LeetCode streak synced to GitHub.

## Security note
Your token is stored **only in this browser's localStorage** and is sent only to `api.github.com`, directly from your device. Nothing goes through any third party. If you ever want to revoke access, just delete the token from GitHub's settings.
