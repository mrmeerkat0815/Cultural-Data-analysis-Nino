# Group Miniproject – Group 14

The notebook `Group_Miniproject_2026_Group_14.ipynb` lives on the **`group-miniproject`** branch.
Everyone can work on it, either in **Google Colab** or in a **local Python (3.11+)** environment.

## Rule no. 1: one person edits the notebook at a time

A notebook is one big JSON file. If two people change it at the same time, Git (and Colab) cannot
merge the two versions: the last save wins and the other person's work is lost.
So: **say in the group chat "I'm on the notebook" → pull/open the latest → work → save to GitHub → say "done".**

If several people want to work in parallel, each one works in their **own scratch notebook**
(e.g. `scratch_<name>.ipynb` in this folder) and copies finished cells into the main notebook during their turn.

## Working in Colab

1. Open the notebook from GitHub (always the latest version):
   https://colab.research.google.com/github/mrmeerkat0815/Cultural-Data-analysis-Nino/blob/group-miniproject/Group_Miniproject/Group_Miniproject_2026_Group_14.ipynb
   (or use the "Open in Colab" badge at the top of the notebook).
2. Run the **Setup** cell first. It clones this branch to `/content` so the files in `data/` are there.
3. To save: **File → Save a copy in GitHub** → repository `mrmeerkat0815/Cultural-Data-analysis-Nino`,
   branch **`group-miniproject`**, path `Group_Miniproject/Group_Miniproject_2026_Group_14.ipynb`,
   write a short commit message → OK. This commits and pushes directly.
   - The first time, Colab asks you to authorise GitHub. If the repo is private, tick "Include private repos".
   - Your GitHub account must be a collaborator on the repository (the owner invites you).
4. Data files you create in Colab are **not** saved by "Save a copy in GitHub". Upload them on GitHub
   (Add file → Upload files, into `Group_Miniproject/data/` on the `group-miniproject` branch), or ask
   someone working locally to commit them.

## Working locally (VS Code / Jupyter, Python 3.11+)

```bash
git fetch origin
git switch group-miniproject
git pull
pip install -r Group_Miniproject/requirements.txt
```

Before you open the notebook, always `git pull` (someone may have saved from Colab).
When you are done:

```bash
git add Group_Miniproject
git commit -m "What you did"
git push
```

If `git push` is rejected, someone saved in the meantime: run `git pull` first. If that gives a
conflict in the notebook, do not try to fix the JSON by hand: keep one version
(`git checkout --theirs <file>` or `--ours`), then copy your cells back in.

## API keys

Never put keys in the notebook. Use `get_secret('NAME')` from the Setup cell:
- Colab: add `NAME` under Secrets (key symbol on the left).
- Local: copy `.env.example` to `.env` and add `NAME=...` there (`.env` is ignored by Git).

## Data

Save and load everything through `DATA_DIR` (set in the Setup cell), e.g.
`df.to_csv(DATA_DIR / 'posts.csv')`. Then the same code runs in Colab and locally.
