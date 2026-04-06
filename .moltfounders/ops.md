# Operations Setup

Suggested unattended setup for `alvinreal/awesome-openclaw`.

This repo uses two loops only:

1. research loop
2. PR review loop

Issue-management and staleness automation are out of scope.

## Research Loop

Recommended schedule: twice per week.

```bash
openclaw cron add \
  --name "OpenClaw Research Loop" \
  --schedule "15 11 * * 1,4" \
  --agent max \
  --message "Run research loop for alvinreal/awesome-openclaw.

Read:
- .moltfounders/research.md
- .moltfounders/spec.txt
- CONTRIBUTING.md

Target repo: alvinreal/awesome-openclaw
Target branch: main

Rules:
1. Use one global research pass across the whole README, not per-category rotation.
2. Open at most ONE PR per run.
3. If an open trusted-agent research PR already exists, do not open another.
4. Prefer a single-category PR even though discovery is global.
5. Touch README.md only.
6. Keep changes non-structural.
7. Skip ambiguous candidates.
8. Skip exact-overlap items already proposed by an open community PR.
9. Prefer only mechanically safe changes for unattended merge review:
   - broken-link fixes/removals
   - deduplication
   - canonical-source replacement
   - obvious category corrections
   - official OpenClaw resource additions or updates
10. Third-party additions may be proposed, but expect them to require human review unless clearly inside the approved safe lane.
11. Before opening a PR, verify:
   - links resolve
   - badge format is correct where used
   - no unintended duplicate listing is created
   - official claims are directly verifiable
12. If no qualifying change is found, open no PR." \
  --delivery announce \
  --channel telegram \
  --to 1953698775
```

## PR Review Loop

Recommended schedule: twice daily.

```bash
openclaw cron add \
  --name "OpenClaw PR Review Loop" \
  --schedule "20 10,16 * * *" \
  --agent max \
  --message "Run PR review loop for alvinreal/awesome-openclaw.

Read:
- .moltfounders/pr-review.md
- .moltfounders/spec.txt
- .moltfounders/labels.md
- CONTRIBUTING.md

Trusted agent account: alvinreal.

For each open PR:
1. Process agent PRs first, then community PRs.
2. Skip all draft PRs.
3. Agent PRs are re-evaluated every run.
4. Community PRs already reviewed are skipped until meaningful new activity arrives.
5. Community PRs are never auto-merged.
6. Agent PRs may auto-merge only if all are true:
   - authored by alvinreal
   - README.md only
   - single-category only
   - non-structural
   - mechanically safe
   - all required checks pass
7. Initial safe lane is limited to:
   - broken-link fixes/removals
   - deduplication
   - canonical-source replacement
   - obvious category corrections
   - official OpenClaw resource additions or updates
8. Required checks before merging an agent PR:
   - diff still touches README.md only
   - diff stays within one category
   - diff is non-structural
   - links resolve
   - badge format remains correct where used
   - no unintended duplicate listing is created
   - official claims are directly verifiable
9. If an agent PR is valid but outside auto-merge scope, leave it open and apply needs-human.
10. One safe fix attempt is allowed for clearly fixable issues; if still failing, close with a short reason.
11. Community PR outcomes:
   - valid -> comment + labels: agent:reviewed, agent:approved, needs-human
   - needs changes -> comment + label: agent:changes-requested
   - mechanically invalid/out of scope -> close with specific reason + label: agent:rejected
12. Ensure canonical labels exist before proceeding." \
  --delivery announce \
  --channel telegram \
  --to 1953698775
```
