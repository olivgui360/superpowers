# Superpowers Bootstrap for GitHub Copilot

## Core Rule

Skills are **mandatory workflows**, not suggestions. When loaded, you MUST follow them completely.

## Available Skills

**Core Workflows**
- `brainstorming` - Before any creative work
- `test-driven-development` - Before writing implementation code
- `systematic-debugging` - When encountering bugs

**Collaboration**
- `writing-plans` - Break work into tasks
- `executing-plans` - Execute plans in batches
- `requesting-code-review` - Pre-review checklist
- `receiving-code-review` - Respond to feedback
- `using-git-worktrees` - Isolated workspace
- `finishing-a-development-branch` - Merge/PR workflow

**Meta**
- `using-superpowers` - How to use skills
- `writing-skills` - Create new skills
- `verification-before-completion` - Verify fixes work

## Test-Driven Development (Iron Law)

```
NO PRODUCTION CODE WITHOUT A FAILING TEST FIRST
```

- Code before test? Delete it. Start over.
- "I'll test after"? No. Test FIRST.
- **Violating the letter is violating the spirit.**

## Tool Mapping

| Claude Code | GitHub Copilot |
|-------------|----------------|
| Skill tool | Auto-load based on context |
| TodoWrite | TODO comments |
| Task (subagent) | Handle sequentially |

## Workflow Example

```
User: "Add email validation"
→ Load brainstorming: ask questions, explore approaches
→ Load test-driven-development: write test, watch fail, minimal code, watch pass
```

## Red Flags

- "Skip TDD just this once"
- "Test after to verify"
- "Already manually tested"
- "Too simple for [skill]"
- "This is different because..."

**All mean: Stop. Use the skill.**
