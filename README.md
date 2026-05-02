# Rebase and Fix Conflicts

An [agent skill](https://agentskills.io/home) for rebasing the current branch onto `main` and resolving conflicts while preserving branch intent.

## What it does

This skill gives agents a disciplined workflow for pulling in `main` and working through rebase conflicts. It:

- Inspects the current branch and worktree state before rebasing
- Preserves unrelated user changes and avoids ambiguous stashing or committing
- Rebases onto `origin/main` by default
- Resolves conflicts by adapting the branch's intent to the current mainline code
- Runs the smallest relevant validation before reporting back

## Installation

### As a skill

```bash
npx skills add https://github.com/diegopetrucci/rebase-and-fix-conflicts --skill rebase-and-fix-conflicts
```

### As a Claude Code plugin

```shell
/plugin marketplace add diegopetrucci/ai-agents-skills
/plugin install rebase-and-fix-conflicts@diegopetrucci-claude-plugins
```

### As a Codex plugin

```shell
codex plugin marketplace add diegopetrucci/ai-agents-skills
```

Restart Codex, then install `rebase-and-fix-conflicts` from the "Diego Petrucci Agent Skills" marketplace in the plugin directory.

## Usage

Trigger the skill while on a feature branch:

- **Claude Code:** say "rebase this branch onto main" or "fix the rebase conflicts"

The skill will inspect the repo state, fetch `origin/main`, rebase the current branch, resolve conflicts, and run focused validation.

## More Skills Like This

Found this skill useful? Browse all my hand-crafted ones in the [AI Agents skills](https://github.com/diegopetrucci/ai-agents-skills) repo.

## License

MIT
