# Research Loop Rules

## Purpose

Periodically discover useful OpenClaw resources across the whole ecosystem and open at most one candidate PR per run.

This loop is global across all README categories. It does **not** rotate category-by-category.

## Clean Start Requirement

Before doing research, edits, branch creation, or PR work, the runner/agent must start from a clean, current base:

1. Check out `main`
2. Sync to the latest remote state (`origin/main`)
3. If the local branch is dirty or diverged, reset to the latest `origin/main` before proceeding
4. Only then create or switch to the working branch for the current PR

## Run Model

- One global research pass per run
- At most **one PR** opened per run
- Prefer a **single-category** PR even though discovery is global
- If an open trusted-agent research PR already exists, do not open another

## Sources to Check

1. **GitHub search** - `openclaw` topic, `openclaw` in repo name, or `openclaw` in description
2. **ClawHub** - https://clawhub.com for published skills and related ecosystem resources
3. **GitHub search** - `openclaw skill`, `openclaw plugin`, `openclaw integration`, `openclaw dashboard`, `openclaw deploy`
4. **Official OpenClaw channels** - docs, org repos, and linked ecosystem pages
5. **Community discovery** - Discord, Reddit, HN, blog posts, and release announcements when they point to concrete resources

## Qualification Criteria

A resource qualifies only if all of these are true:

- clear OpenClaw relevance
- working repo, page, or documentation
- not already in the README
- fits an existing README category
- actively maintained **or** useful as a durable reference

Prefer:

- canonical sources over mirrors and forks
- focused tools over low-signal directories
- concise, factual README entries

Skip:

- ambiguous relevance
- obvious duplicates
- thin landing pages with little substance
- generic AI projects with only passing OpenClaw mention

## Output Rules

- At most **one PR per run**
- PRs should stay **single-category** whenever possible
- PRs must touch **`README.md` only**
- PRs must be **non-structural**
- PRs must stay within the auto-merge-safe lane if they are intended for unattended merge
- If a candidate overlaps exactly with an open community PR, skip that item
- If no qualifying project or cleanup is found, open no PR

## Safe Lane for Unattended Research PRs

The research loop should prefer changes that are safe for later unattended merge review:

- official OpenClaw resource additions or updates
- broken-link fixes or removals
- duplicate cleanup
- canonical-source replacement
- obvious category correction

Third-party additions may still be proposed, but if they are not clearly within the safe lane, they should be expected to require human review.

## PR Format

Use a single PR with a clear title such as:

`[Research] Update README - <short summary>`

PR body should briefly list each change and why it qualifies:

- name
- link
- category
- OpenClaw relevance
- why it is safe or why human review is still warranted

## Edge Cases

- **Brand new project:** may still qualify if relevance and usefulness are already clear
- **Inactive but high-value guide/resource:** may remain valid if it still has durable reference value
- **Ambiguous official claim:** do not auto-merge; leave for human review
