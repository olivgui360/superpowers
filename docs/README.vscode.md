# Superpowers for GitHub Copilot in VSCode

Complete usage guide for Superpowers skills with GitHub Copilot.

## Quick Start

**Installation**: See [../.github/QUICKSTART.md](../.github/QUICKSTART.md) (5 minutes)

## Available Skills

**Testing**
- `test-driven-development` - RED-GREEN-REFACTOR cycle
- `verification-before-completion` - Ensure fixes work

**Debugging**
- `systematic-debugging` - 4-phase root cause analysis

**Collaboration**
- `brainstorming` - Design refinement before coding
- `writing-plans` - Break work into tasks
- `requesting-code-review` - Pre-review checklist
- `using-git-worktrees` - Isolated workspace
- `finishing-a-development-branch` - Merge/PR workflow

## How Skills Work

Skills auto-load based on conversation context:

```
You: "Fix bug where users submit empty emails"
→ Loads: systematic-debugging, test-driven-development
→ Guides: write test reproducing bug, watch fail, fix, watch pass
```

## Philosophy

- **Test-Driven Development** - Tests first, always
- **Systematic over ad-hoc** - Process over guessing  
- **Complexity reduction** - Simplicity as goal
- **Evidence over claims** - Verify before declaring success

## Creating Custom Skills

Project skills in `.github/skills/my-skill/SKILL.md`:

```markdown
---
name: my-skill
description: Use when [triggering conditions]
---

# My Skill
[Instructions]
```

**Skill priority**: Project → Personal (`~/.copilot/skills/`) → Superpowers

## Tool Mapping

| Claude Code | GitHub Copilot |
|-------------|----------------|
| Skill tool | Auto-discovery |
| TodoWrite | TODO comments |
| Task (subagent) | Sequential conversation |

## Troubleshooting

**Skills not loading?**
- VSCode 1.108+ required
- Enable: `"github.copilot.chat.useSkills": true`
- Check: `ls .github/skills/`

**Installation issues?** See [../.github/INSTALL.md](../.github/INSTALL.md)

## Resources

- **Installation**: [../.github/INSTALL.md](../.github/INSTALL.md)
- **Quick start**: [../.github/QUICKSTART.md](../.github/QUICKSTART.md)
- **Creating skills**: `../skills/writing-skills/SKILL.md`
- **Issues**: https://github.com/obra/superpowers/issues
