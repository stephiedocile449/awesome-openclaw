# .moltfounders/

This directory defines how AI agents maintain this repository.

Agents participating in the [MoltFounders](https://moltfounders.com) workspace for this repo read these files on every run and follow them exactly. Rules are versioned here like code - propose changes via PR.

## Files

| File | Purpose |
|------|---------|
| `labels.md` | Canonical GitHub label definitions |
| `ops.md` | Suggested cron/job setup for this repo |
| `pr-review.md` | How to review pull requests |
| `research.md` | How to discover and suggest new OpenClaw resources |
| `spec.txt` | Operating decisions and edge-case answers |

## Repository Validation

- This repo currently uses policy-based review rather than a dedicated validator script
- Agents should verify only mechanically checkable facts before auto-merging agent PRs
- Research and PR-review runners should begin from a clean, current `main` / `origin/main` state before creating or updating working branches

## Principles

- **Trusted agent identity:** PRs authored by GitHub user `alvinreal` are treated as agent PRs.
- **Scoped autonomy:** The trusted agent may auto-merge only eligible README-only, single-category, non-structural, mechanically safe PRs that pass required checks.
- **Human control on governance:** Changes to `.moltfounders/` and other governance/process rules never auto-merge.
- **Idempotent by default:** Community PRs are not re-reviewed unless new activity arrives. Agent PRs are re-evaluated each review cycle.
- **OpenClaw-focused.** This list is specifically about the OpenClaw ecosystem — not general AI tools.
- **Transparent.** Anyone can read exactly how automation behaves by reading this directory.
- **Community-editable.** Want to change how the repo is maintained? Open a PR against these files.

## Note on quality criteria

This list differs from a general OSS list - it does not require OSI-approved licenses or star thresholds. The primary bar is: **clear OpenClaw relevance + active or durable usefulness**. See `CONTRIBUTING.md` for contributor-facing criteria and `.moltfounders/spec.txt` for automation decisions.
