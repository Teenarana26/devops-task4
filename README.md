# Task 4: Version-Controlled DevOps Project with Git

A small DevOps project used to practice Git best practices: branching, pull requests, tags and a clean repository.

## Project structure
```
.
├── README.md
├── .gitignore
└── scripts/
    └── deploy.sh      # simple deploy script (added on a feature branch)
```

## Branching strategy
| Branch | Purpose |
|--------|---------|
| `main` | Stable, release-ready code |
| `dev` | Integration branch where features are merged first |
| `feature/add-deploy-script` | New work, branched from `dev` |

## Workflow followed
1. Initialized the repo locally and pushed it to GitHub (`main`).
2. Created the `dev` branch from `main`.
3. Created `feature/add-deploy-script` from `dev` and committed the script there.
4. Opened a **pull request** from the feature branch into `dev` and merged it.
5. Opened a **pull request** from `dev` into `main` and merged it.
6. Tagged the release as `v1.0.0`.

## Commands used
```
git init
git add .
git commit -m "message"
git branch -M main
git remote add origin <repo-url>
git push -u origin main
git checkout -b dev
git checkout -b feature/add-deploy-script
git push -u origin <branch>
git tag -a v1.0.0 -m "First release"
git push origin v1.0.0
git log --oneline --graph --all
```

## Commit message style
Short, present-tense messages, for example `Add deploy script`.

## Screenshots
Screenshots of the branches, pull requests and tags are in the `screenshots/` folder.

## Interview Q&A

**1. What is Git?**
A distributed version control system that tracks changes to files, lets many people work on the same code, and keeps a full history that can be reverted.

**2. Difference between merge and rebase?**
`merge` combines two branches with a merge commit and keeps the history as it happened. `rebase` moves your commits on top of another branch to create a straight, linear history. Don't rebase commits that are already shared.

**3. What is a pull request?**
A request on GitHub to merge one branch into another. It lets teammates review the code, comment and run checks before the merge.

**4. How do you resolve merge conflicts?**
Open the conflicted files, look at the `<<<<<<<`, `=======` and `>>>>>>>` markers, keep the correct code, remove the markers, then `git add` the file and finish with `git commit` (or `git merge --continue`).

**5. What are Git tags?**
Named markers on specific commits, usually used for releases such as `v1.0.0`. Annotated tags (`git tag -a`) also store a message and author.

**6. What is Git workflow?**
An agreed way of using branches in a team, for example feature branches merged into `dev` through pull requests, and `dev` merged into `main` for releases.

**7. Explain git stash.**
`git stash` temporarily saves uncommitted changes and cleans the working folder so you can switch branches. `git stash pop` brings the changes back.

**8. What is the use of .gitignore?**
A file that lists files and folders Git should not track, such as `node_modules/`, logs, build output and secrets like `.env`.
