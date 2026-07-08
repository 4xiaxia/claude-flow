---
name: dependency-update-across-monorepo
description: Workflow command scaffold for dependency-update-across-monorepo in claude-flow.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /dependency-update-across-monorepo

Use this workflow when working on **dependency-update-across-monorepo** in `claude-flow`.

## Goal

Updates one or more npm dependencies across multiple packages/directories in a monorepo, including lockfiles and package manifests.

## Common Files

- `package.json`
- `package-lock.json`
- `pnpm-lock.yaml`
- `v*/**/package.json`
- `v*/**/package-lock.json`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Identify outdated dependencies in multiple package.json files.
- Update the version(s) of the dependency in each relevant package.json.
- Update corresponding lockfiles (package-lock.json, pnpm-lock.yaml) in each directory.
- Commit all changed package.json and lockfile(s) together with a detailed changelog in the commit message.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.