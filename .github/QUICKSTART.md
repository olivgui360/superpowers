# Quick Start: Superpowers with GitHub Copilot

Get started with Superpowers skills in VSCode + GitHub Copilot in under 5 minutes.

## 1. Install (2 minutes)

In your project directory:

```bash
mkdir -p .github
git clone https://github.com/obra/superpowers.git .github/superpowers-repo
ln -s .github/superpowers-repo/skills .github/skills
```

## 2. Enable in VSCode (30 seconds)

Open VSCode Settings (Ctrl+, or Cmd+,) and add:

```json
{
  "github.copilot.chat.useSkills": true
}
```

Or via command line:
```bash
code --user-data-dir ~/path/to/vscode/settings --add-setting "github.copilot.chat.useSkills" true
```

## 3. Verify (30 seconds)

Open GitHub Copilot Chat (Ctrl+Shift+I) and ask:

```
What skills do you have available?
```

You should see a list including:
- brainstorming
- test-driven-development
- systematic-debugging
- And more...

## 4. Try It Out (2 minutes)

### Example 1: Add a Feature with TDD

In Copilot Chat, try:

```
I need to add email validation to my signup form
```

Copilot will:
1. Load the **brainstorming** skill
2. Ask questions about your requirements
3. Explore different approaches
4. Present a design for validation

Then when you say "let's implement it":
1. Load the **test-driven-development** skill
2. Guide you to write a failing test first
3. Help write minimal code to pass
4. Ensure proper RED-GREEN-REFACTOR cycle

### Example 2: Debug a Problem

```
My login function fails silently when the password is wrong
```

Copilot will:
1. Load the **systematic-debugging** skill
2. Guide you through 4-phase root cause analysis
3. Help reproduce the problem
4. Trace the root cause
5. Verify the fix works

### Example 3: Plan a Feature

```
Use the brainstorming skill to help me design a new caching system
```

Copilot will:
1. Load the **brainstorming** skill explicitly
2. Ask questions about cache requirements
3. Present 2-3 different approaches with trade-offs
4. Show you the design in digestible sections
5. Save the validated design document

## What Just Happened?

GitHub Copilot automatically:
- Discovered the skills in `.github/skills/`
- Loaded relevant skills based on your conversation
- Followed the skill workflows (brainstorming, TDD, debugging)
- Applied proven development practices

## Key Behaviors

### Skills Are Mandatory
When a skill loads, Copilot MUST follow it completely. Skills enforce:
- Writing tests before code (TDD)
- Asking questions before designing
- Finding root causes before fixing
- Evidence-based completion

### Skills Auto-Load
Skills automatically load based on context:
- "Add a feature" → brainstorming + test-driven-development
- "Fix a bug" → systematic-debugging + test-driven-development
- "Debug this" → systematic-debugging

### Skills Chain Together
Skills naturally sequence:
1. **brainstorming** - Understand requirements
2. **writing-plans** - Break into tasks
3. **test-driven-development** - Implement with tests
4. **verification-before-completion** - Verify it works

## Next Steps

### Learn More
- **Full documentation**: [docs/README.vscode.md](../docs/README.vscode.md)
- **Installation options**: [.github/INSTALL.md](INSTALL.md)
- **Create your own skills**: `skills/writing-skills/SKILL.md`

### Common Workflows
- **New feature**: Brainstorm → Plan → TDD
- **Bug fix**: Systematic debugging → TDD (test reproducing bug)
- **Refactoring**: TDD (tests prevent regressions)
- **Design exploration**: Brainstorming only

### Customization
Create project-specific skills in `.github/skills/your-skill/SKILL.md`:

```markdown
---
name: your-skill
description: Use when [specific conditions]
---

# Your Skill

[Instructions here]
```

## Troubleshooting

**Skills not loading?**
- Check VSCode version (need 1.108+)
- Verify setting: `"github.copilot.chat.useSkills": true`
- Check directory: `ls .github/skills/`

**Copilot not following skills?**
- Skills should auto-load based on context
- Try explicit: "Use the [skill-name] skill"
- Check the skill description matches your task

**Need help?**
- GitHub issues: https://github.com/obra/superpowers/issues
- Full docs: [docs/README.vscode.md](../docs/README.vscode.md)

## Philosophy

Superpowers teaches your AI assistant to:
- **Test first** - Write tests before code, always
- **Design first** - Understand before implementing
- **Systematic approach** - Process over guessing
- **Evidence-based** - Verify before claiming success

This leads to higher quality code, fewer bugs, and faster development.

---

**Time invested**: ~5 minutes  
**Benefits**: Proven workflows, systematic development, higher code quality

Ready to give your AI assistant Superpowers? Follow the steps above!
