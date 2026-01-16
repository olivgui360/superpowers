# GitHub Copilot Instructions

You have **Superpowers** - a skills library that teaches proven development workflows.

## Core Principle

<EXTREMELY-IMPORTANT>
Skills in the `.github/skills/` directory are MANDATORY workflows, not suggestions.

When a skill loads (automatically or explicitly), you MUST follow it completely.

If you think there is even a 1% chance a skill applies, it APPLIES. You must use it.
</EXTREMELY-IMPORTANT>

## Available Skills

Skills automatically load based on context. Key skills include:

- **brainstorming** - REQUIRED before any creative work (features, components, functionality). Explores requirements through questions before coding.
- **test-driven-development** - REQUIRED when implementing features or fixes. Enforces RED-GREEN-REFACTOR: write test, watch fail, minimal code, watch pass.
- **systematic-debugging** - Use when investigating bugs. 4-phase root cause analysis.
- **writing-plans** - Use with approved design. Creates detailed implementation plans.
- **requesting-code-review** - Use when completing tasks. Pre-review quality checks.
- **using-git-worktrees** - Use after design approval. Creates isolated workspace.
- **verification-before-completion** - Use before marking work complete.

## Non-Negotiable Rules

### Test-Driven Development

```
NO PRODUCTION CODE WITHOUT A FAILING TEST FIRST
```

- Code before test? Delete it. Start over.
- "I'll test after"? No. Test FIRST.
- "Tests after achieve same goals"? No. Tests-first prevents different problems.

### Systematic Workflows

- New feature? Brainstorm → Plan → TDD
- Bug fix? TDD (write test reproducing bug first)
- Debugging? Systematic-debugging process
- Completion? Verification-before-completion

### Red Flags - Stop Immediately

If you think these, you're rationalizing:
- "Skip TDD just this once"
- "Too simple to need [skill]"
- "Already manually tested"
- "Keep code as reference"
- "This is different because..."

**Stop. Load and follow the skill.**

## Workflow Pattern

1. **Before coding**: Use brainstorming to explore requirements
2. **Before implementing**: Use test-driven-development
3. **Before completing**: Use verification-before-completion

Skills chain naturally: process skills first (how to approach), then implementation skills (how to execute).

## Evidence Over Claims

- "It works" requires proof (tests passing)
- Tests must be watched failing first
- Manual testing doesn't count as systematic verification

## Tool Adaptation

Skills reference some Claude Code tools. Adapt to GitHub Copilot:
- "Invoke Skill tool" → Skills auto-load based on context
- "Use TodoWrite" → Add TODO comments
- "Dispatch subagent" → Handle subtasks sequentially

Adapt the tool, maintain the skill's intent.

---

For complete details, see `.github/copilot-bootstrap.md` and `docs/README.vscode.md`
