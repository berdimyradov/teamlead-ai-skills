# TeamLead AI Skill Suite

Private, evidence-backed team-lead reporting skills for Git and GitHub workflows.

This repo contains `SKILL.md` packages that help a code agent produce useful team-lead reports without asking someone to manually inspect every commit, pull request, review, and CI run. The suite focuses on delivery health, review quality, release readiness, estimation calibration, and coaching signals.

The skills are designed for private team-lead notes. They should help a lead decide what to inspect, ask, or follow up on; they should not automate people-management decisions.

## Skill Catalog

Start with the router when you are not sure which reporter fits:

- [`teamlead-ai-skills`](skills/teamlead-ai-skills/SKILL.md) routes a team-lead reporting request to the right reporter skill.

Use a specific reporter when the request is clear:

| Skill | Use when you need... |
| --- | --- |
| [`task-health-reporter`](skills/task-health-reporter/SKILL.md) | A current view of blocked PRs, stale work, ownership gaps, review bottlenecks, and standup follow-ups. |
| [`velocity-flow-risk-reporter`](skills/velocity-flow-risk-reporter/SKILL.md) | Delivery trend and flow-risk analysis across PR throughput, WIP, batching, cycle-time signals, and review latency. |
| [`code-review-reporter`](skills/code-review-reporter/SKILL.md) | A private review memo for one PR, local diff, or patch, including risks, edge cases, test gaps, and suggested review comments. |
| [`release-readiness-reporter`](skills/release-readiness-reporter/SKILL.md) | Go/no-go release guidance from included PRs, open blockers, CI, migrations, config changes, and rollout risk. |
| [`estimation-calibration-reporter`](skills/estimation-calibration-reporter/SKILL.md) | Estimate-versus-actual analysis, variance drivers, Definition of Done clarity, and future planning calibration. |
| [`team-coaching-prep-reporter`](skills/team-coaching-prep-reporter/SKILL.md) | One-on-one or retro prep notes from evidence-backed strengths, friction points, caveats, and support signals. |

## How To Use

Each skill is a repo-local installable skill package: a directory containing a `SKILL.md` file. To use one in an agent environment that supports local skills, copy the relevant directory from `skills/` into that environment's local skills directory, or point your agent tooling at this repo if it supports loading skills in place.

Typical usage:

```text
Use teamlead-ai-skills to decide what report I need for this sprint.
```

```text
Run task-health-reporter for the current repo and open GitHub PRs.
```

```text
Use release-readiness-reporter for release branch release/1.8.0.
```

```text
Run code-review-reporter on this patch and give me suggested review comments.
```

The skills are intentionally report-oriented. They gather evidence where possible, explain confidence limits, and produce a decision memo for the team lead.

## Inputs And Evidence

The reporters work best with:

- Git commit history, including authors, timestamps, branches, and changed files.
- GitHub pull request metadata, including titles, descriptions, authors, reviewers, review states, timestamps, comments, linked issues, checks, and merge state.
- Local diffs or patch files for code review.
- CI check names, status, and timestamps.
- Optional team context such as sprint goals, release scope, estimates, Definition of Done, capacity notes, incidents, support load, or coaching notes.

Every concrete finding should cite evidence: a PR, commit, file path, timestamp, CI check, review state/comment, or an explicit missing-data note. If a source is unavailable, the report should say what is missing and how that limits confidence.

## Safety And Attribution

These skills produce reports by default. They should not assign tasks, update trackers, post PR comments, merge code, create commits, deploy releases, or make people-management decisions unless the user separately asks for that action outside the reporting task.

Contributor names may appear when attribution helps accountability, coordination, or coaching. The skills should:

- Attribute only observable events.
- Separate facts from interpretation.
- Include workload, ownership, support load, pairing, review load, or data-gap caveats when relevant.
- Avoid ranking people by default.
- Never use commit count, line count, or PR count as direct proof of individual productivity.
- Keep people-related observations factual, private, and coaching-oriented.

## Community Use

This repo is meant to evolve with real team-lead workflows. Issues and PRs are welcome for new reporter ideas, clearer trigger prompts, better evidence rules, safer attribution guidance, and examples that make the skills easier to use.

When proposing changes, keep the core contract intact: private reports, evidence-backed findings, explicit confidence limits, and no automated workflow or people-management actions by default.
