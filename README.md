# Handoff: Publish the AI Policy Matrix webpage

## Overview
This folder contains **`index.html`** — a finished, single-file interactive webpage
("The AI Policy in Practice" matrix, with live toggles for columns and owners). It is
shown to a live audience during a workshop. The task is simply to **publish it to GitHub
Pages** and return a live URL.

## About the design file
`index.html` is a complete, self-contained webpage — all CSS, JavaScript, and fonts are
inlined. There is **no build step and no other files are required**. Do not refactor it,
add a framework, or split it up. Serve it exactly as-is.

## What to do
You are Claude Code, running in the folder that contains `index.html`.

1. Run `ls` and confirm `index.html` is present. If not, stop and say so.
2. Run `gh auth status`. If `gh` is not authenticated, run `gh auth login` and walk me through it.
3. Initialise git on `main`, commit the file:
   ```bash
   git init -b main
   git add index.html
   git commit -m "AI Policy Matrix"
   ```
4. Create a **public** repo and push:
   ```bash
   gh repo create ai-policy-matrix --public --source=. --remote=origin --push
   ```
5. Enable GitHub Pages from the `main` branch, root folder:
   ```bash
   gh api -X POST repos/$(gh api user -q .login)/ai-policy-matrix/pages \
     -f "source[branch]=main" -f "source[path]=/"
   ```
6. Print the live URL: `https://<my-username>.github.io/ai-policy-matrix/`
7. Poll that URL until it returns HTTP 200 (Pages can take 1–2 minutes), then confirm it's live.

## Notes
- If the repo name `ai-policy-matrix` is taken, append `-2` and tell me the new URL.
- The site is just `index.html` — nothing else to deploy.
- After it's live, I'll bookmark the URL in Chrome myself (next to my "Readiness Snapshot" bookmark).
