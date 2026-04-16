# TEAM_DEVELOPMENT_WORKFLOW.md

## Purpose

This file documents how the Track 3 team should set up the repository, create branches, push work, and pull the latest course changes from the instructor repository.

## Repository Model

We use a fork-based Git workflow.

- **origin** = each student's personal fork on GitHub
- **upstream** = the main course repository maintained by the instructor

For this team, the main course repository is:

https://github.com/dkirsh/Knowledge_Atlas

Example personal fork:

https://github.com/NeuroBitEngineer/Knowledge_Atlas

## Initial Setup

### 1. Fork the course repository on GitHub

Go to the instructor repository and click **Fork**.

### 2. Clone your fork

```bash
git clone https://github.com/YOUR_GITHUB_HANDLE/Knowledge_Atlas.git
cd Knowledge_Atlas
````

### 3. Add the instructor repository as upstream

```bash
git remote add upstream https://github.com/dkirsh/Knowledge_Atlas.git
```

### 4. Verify remotes

```bash
git remote -v
```

Expected structure:

```bash
origin    https://github.com/YOUR_GITHUB_HANDLE/Knowledge_Atlas.git (fetch)
origin    https://github.com/YOUR_GITHUB_HANDLE/Knowledge_Atlas.git (push)
upstream  https://github.com/dkirsh/Knowledge_Atlas.git (fetch)
upstream  https://github.com/dkirsh/Knowledge_Atlas.git (push)
```

## Important Note About This Repository

This repository uses the branch name:

```bash
master
```

not:

```bash
main
```

So updates must be pulled from:

```bash
upstream/master
```

not:

```bash
upstream/main
```

## Getting the Latest Course Changes

When you want the latest course updates, run:

```bash
git checkout master
git fetch upstream
git merge upstream/master
```

If your local master is clean, this updates your local copy with the newest course changes.

## Starting New Work

Always branch from updated `master`.

Example:

```bash
git checkout master
git fetch upstream
git merge upstream/master
git checkout -b track3/YourGitHubHandle/short-task-name
```

For Track 3, branch names should follow this pattern:

```bash
track3/<GitHubHandle>/<task-name>
```

Example:

```bash
git checkout -b track3/NeuroBitEngineer/team-md
```

## Making Changes

Edit files, then check status:

```bash
git status
```

Stage files:

```bash
git add TEAM.md TEAM_DEVELOPMENT_WORKFLOW.md
```

Commit changes:

```bash
git commit -m "Add Track 3 team and workflow docs"
```

## Pushing Changes to Your Fork

Push your branch to your fork:

```bash
git push -u origin track3/NeuroBitEngineer/team-md
```

After the first push, future pushes can be done with:

```bash
git push
```

## Updating a Working Branch After Course Changes

If the instructor repo changes after you started a branch, update like this:

```bash
git checkout master
git fetch upstream
git merge upstream/master
git checkout track3/NeuroBitEngineer/team-md
git merge master
```

This brings the newest course changes into your working branch.

## Basic Team Rules

1. Do not work directly on `master`.
2. Always create a Track 3 branch for new work.
3. Always pull updates from `upstream/master`, not `upstream/main`.
4. Push changes to your own fork (`origin`).
5. Use clear commit messages.
6. Keep documentation files updated as the team structure changes.
