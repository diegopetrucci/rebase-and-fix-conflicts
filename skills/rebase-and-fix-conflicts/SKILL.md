---
name: rebase-and-fix-conflicts
description: Rebase the current branch onto main and resolve conflicts. Use this skill whenever the user asks to rebase or update a branch with main, pull in main changes, resolve rebase conflicts, continue a blocked rebase, or fix conflicts after upstream drift.
license: MIT
metadata:
  author: Diego Petrucci
  version: "1.1"
---

# Rebase and Fix Conflicts

Rebase the current branch onto `main` and resolve conflicts without losing the branch's intent or unrelated user work.

## Workflow

1. Inspect the repo state with `git status --short --branch` and identify the current branch. If a rebase is already in progress, continue from that state instead of starting over.
2. Preserve unrelated user changes. Do not stash, commit, discard, or rewrite ambiguous work unless the user explicitly asks for that operation.
3. Fetch main with `git fetch origin main`, then rebase onto `origin/main` unless repository instructions specify a different mainline target.
4. For each conflict:
   - List unresolved files with `git diff --name-only --diff-filter=U`.
   - Read the conflicted files and relevant nearby code before editing.
   - Keep the feature branch's intended behavior, adapting it to `main`'s current structure and APIs.
   - Remove conflict markers, stage the resolved files, and run `git rebase --continue`.
5. Repeat until the rebase completes. If blocked by missing context, failing generated commands, or an ambiguous semantic conflict, leave the repository in a clear state and report the exact file and conflict.
6. Run the smallest relevant validation for the touched area. Do not push or force-push unless the user explicitly asks.

## Reporting

When finished, summarize:

- The branch and mainline target rebased onto
- The conflict files resolved
- The validation command and result
- Any remaining risks or follow-up needed
