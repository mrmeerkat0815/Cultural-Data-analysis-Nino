# Group Miniproject – Group 14

This branch (`group-miniproject`) holds our group notebook:
[`Group_Miniproject/Group_Miniproject_2026_Group_14.ipynb`](Group_Miniproject/Group_Miniproject_2026_Group_14.ipynb)

You can work on it in **Google Colab** (nothing to install) or in a **local Python environment** (3.11 or newer).
This page explains both, and what "commit", "push" and "pull" mean.

**Open in Colab:**
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mrmeerkat0815/Cultural-Data-analysis-Nino/blob/group-miniproject/Group_Miniproject/Group_Miniproject_2026_Group_14.ipynb)

---

## The most important rule: one person edits the notebook at a time

A notebook is one big file. If two people change it at the same time, the two versions cannot be
combined automatically: whoever saves last overwrites the work of the other.

So before you start:

1. Write in the group chat: **"I'm on the notebook."**
2. Open the **latest** version from GitHub (see below).
3. Work, then save it back to GitHub.
4. Write: **"Done, pushed."**

Want to try something while someone else has the notebook? Work in your own copy
(e.g. `scratch_<yourname>.ipynb`) and paste the finished cells into the main notebook when it's your turn.

---

## Git in 1 minute: commit, push, pull

GitHub keeps the shared, official version of our files. Everyone else has a copy.

| Word | What it means |
| --- | --- |
| **commit** | Save a snapshot of your changes with a short message ("Add sentiment analysis"). Like a save point in a game. |
| **push** | Upload your commits to GitHub, so the others get them. |
| **pull** | Download the newest commits from GitHub to your copy. |
| **branch** | A separate line of work in the repository. Ours is called `group-miniproject`. Always use this one. |

In Colab, *commit* and *push* happen in one step ("Save a copy in GitHub"). Locally, they are two commands.

---

## Working in Google Colab

### Once: get access

1. Send your GitHub username to the repository owner, who adds you as a collaborator
   (GitHub → repository → *Settings → Collaborators*). Accept the invitation you get by email.
2. The first time you save to GitHub from Colab, Colab asks you to authorise GitHub. Allow it.
   If the repository is private, tick **"Include private repos"**.

### Every time

1. **Open** the notebook with the *Open in Colab* button above. It always loads the latest version
   from GitHub. (Don't reuse an old Colab tab or a copy in your Drive: it may be out of date.)
2. **Run the Setup cell** (section 0) first. It copies the branch into Colab so the files in
   `Group_Miniproject/data/` are there, and it installs missing packages.
3. Work on the notebook.
4. **Save to GitHub** (this commits and pushes):
   **File → Save a copy in GitHub**, then fill in:
   - Repository: `mrmeerkat0815/Cultural-Data-analysis-Nino`
   - Branch: **`group-miniproject`**
   - File path: `Group_Miniproject/Group_Miniproject_2026_Group_14.ipynb`
   - Commit message: what you did, e.g. `Add word frequency plot`
   - Leave "Include a link to Colaboratory" ticked → **OK**

> ⚠️ **Ctrl+S / ⌘+S in Colab does *not* save to GitHub.** It only saves to your Google Drive.
> Only *File → Save a copy in GitHub* puts your work where the others can see it.

### Data files from Colab

"Save a copy in GitHub" only saves the notebook, not CSV/JSON/image files you created.
To share them: download them from Colab's file panel (folder symbol on the left), then on GitHub
open `Group_Miniproject/data/` on the `group-miniproject` branch → **Add file → Upload files** → **Commit changes**.

### API keys in Colab

Never type a key into a notebook cell. Add it under **Secrets** (key symbol on the left) and read it with
`get_secret('NAME')`, which the Setup cell defines.

---

## Working locally (VS Code / Jupyter, Python 3.11+)

### Once: set up

```bash
git clone https://github.com/mrmeerkat0815/Cultural-Data-analysis-Nino.git
cd Cultural-Data-analysis-Nino
git switch group-miniproject
pip install -r Group_Miniproject/requirements.txt
```

(Already have the repository? Then just `git fetch origin` and `git switch group-miniproject`.)

### Every time

**Before** you open the notebook, get the latest version (someone may have saved from Colab):

```bash
git switch group-miniproject
git pull
```

**After** you are done, save the notebook in VS Code/Jupyter, then commit and push:

```bash
git add Group_Miniproject
git commit -m "What you did"
git push
```

VS Code can do the same with buttons: *Source Control* panel → **+** (stage) → type a message →
**Commit** → **Sync Changes**.

### API keys locally

Copy `Group_Miniproject/.env.example` to `Group_Miniproject/.env` and add your keys there
(`NAME=value`). `.env` is never uploaded to GitHub. `get_secret('NAME')` reads it.

---

## When something goes wrong

- **Colab says it can't save / the branch is missing:** check that the branch is
  `group-miniproject` and that you accepted the collaborator invitation.
- **`git push` is rejected ("fetch first" / "non-fast-forward"):** someone pushed in the meantime.
  Run `git pull`, then `git push` again.
- **`git pull` reports a conflict in the notebook:** don't edit the file by hand. Keep the version
  from GitHub with `git checkout --theirs Group_Miniproject/Group_Miniproject_2026_Group_14.ipynb`,
  then `git add` it, `git commit`, and paste your own cells back in. Then tell the group.
- **Someone overwrote your work:** every commit is kept. On GitHub open the notebook →
  **History** to see and download older versions.

---

## Before we hand in

- **Runtime → Restart session and run all** in Colab (or *Restart & Run All* locally), and check
  that every cell runs. Only cells that collect data may stay un-run.
- No API keys or personal data in the notebook.
- Data files are in `Group_Miniproject/data/`.
