# Superpowers for GitHub Copilot in VSCode

Complete documentation for using the Superpowers skills library with GitHub Copilot in Visual Studio Code.

## Overview

Superpowers is a complete software development workflow built on composable "skills" that teach your AI coding assistant proven techniques for development, testing, debugging, and collaboration.

With GitHub Copilot's new Agent Skills feature (December 2025), you can now use these same battle-tested skills in VSCode!

## What You Get

### Core Skills

**Testing**
- **test-driven-development** - RED-GREEN-REFACTOR cycle with no shortcuts
- **verification-before-completion** - Ensure fixes actually work

**Debugging**
- **systematic-debugging** - 4-phase root cause analysis process
- Includes: root-cause-tracing, defense-in-depth, condition-based-waiting

**Collaboration**
- **brainstorming** - Socratic design refinement before coding
- **writing-plans** - Detailed implementation plans
- **executing-plans** - Batch execution with checkpoints
- **requesting-code-review** - Pre-review checklist
- **receiving-code-review** - Responding to feedback
- **using-git-worktrees** - Parallel development branches
- **finishing-a-development-branch** - Merge/PR decision workflow

**Meta**
- **writing-skills** - Create new skills following best practices
- **using-superpowers** - Introduction to the skills system

## Quick Start

### Installation

```bash
# In your project directory
mkdir -p .github
git clone https://github.com/obra/superpowers.git .github/superpowers-repo
ln -s .github/superpowers-repo/skills .github/skills
```

### Enable in VSCode

Add to your VSCode `settings.json`:

```json
{
  "github.copilot.chat.useSkills": true
}
```

**Full installation guide**: See [INSTALL.md](INSTALL.md)

## How It Works

### Automatic Skill Loading

GitHub Copilot automatically discovers and loads relevant skills based on your conversation:

```
You: "I need to fix this bug where users can submit empty emails"
Copilot: [Loads systematic-debugging and test-driven-development skills]
         "Let's start by writing a test that reproduces the bug..."
```

### Explicit Skill Usage

You can also request specific skills:

```
You: "Use the brainstorming skill to help me design a new authentication system"
Copilot: [Loads brainstorming skill]
         "Let me start by understanding your requirements..."
```

## The Workflow

When you work with Copilot using Superpowers skills, it naturally follows these patterns:

1. **Brainstorming** - Before writing code, refine ideas through questions, explore alternatives, validate design in chunks

2. **Using Git Worktrees** - Create isolated workspace on new branch with clean test baseline

3. **Writing Plans** - Break work into 2-5 minute tasks with exact file paths and verification steps

4. **Test-Driven Development** - Write failing test, watch it fail, write minimal code, watch it pass, refactor

5. **Systematic Debugging** - When issues arise, follow 4-phase root cause analysis

6. **Requesting Code Review** - Review against plan, report issues by severity

7. **Finishing Branch** - Verify tests, decide on merge/PR, clean up

## Philosophy

- **Test-Driven Development** - Write tests first, always
- **Systematic over ad-hoc** - Process over guessing
- **Complexity reduction** - Simplicity as primary goal
- **Evidence over claims** - Verify before declaring success

## Tool Mapping

Superpowers skills reference some Claude Code-specific tools. Here's how they map to GitHub Copilot:

| Skill Reference | GitHub Copilot Approach |
|----------------|------------------------|
| "Invoke Skill tool" | Skills load automatically based on context |
| "Use TodoWrite" | Add TODO comments or use task tracking |
| "Dispatch subagent" | Handle subtasks sequentially in conversation |
| File operations | Use Copilot's native edit capabilities |

The skills gracefully handle these differences - Copilot will adapt the workflows to its available capabilities.

## Example: Bug Fix with TDD

Here's how the test-driven-development skill guides you:

```
You: "Users can submit forms with empty email fields"

Copilot: "Let's write a failing test first.

RED Phase - Write the test:
```typescript
test('rejects empty email', async () => {
  const result = await submitForm({ email: '' });
  expect(result.error).toBe('Email required');
});
```

Now run this test to verify it fails for the right reason..."
```

The skill enforces the RED-GREEN-REFACTOR cycle, preventing shortcuts that lead to untested code.

## Creating Your Own Skills

### Project-Specific Skills

Create custom skills for your project:

```bash
mkdir -p .github/skills/my-skill
```

Create `.github/skills/my-skill/SKILL.md`:

```markdown
---
name: my-skill
description: Use when [specific triggering conditions]
---

# My Skill

## Overview
Core principle in 1-2 sentences.

## When to Use
- Specific situation 1
- Specific situation 2

## The Process
Step-by-step instructions...
```

**Detailed guide**: See `skills/writing-skills/SKILL.md`

### Skill Priority

1. Project skills (`.github/skills/`) override
2. Personal skills (`~/.copilot/skills/`) override  
3. Superpowers skills (this repository)

This lets you customize or extend any skill for your needs.

## Differences from Claude Code

GitHub Copilot's implementation has some differences:

1. **Automatic discovery**: Skills load based on context, no manual invocation needed
2. **Sequential processing**: Tasks handled in conversation flow rather than parallel subagents
3. **Native tools**: Uses VSCode's built-in capabilities instead of Claude Code tools
4. **Context windows**: Different context management but skills still work effectively

The skills are designed to work well with these differences.

## Architecture

### Skills Structure

Each skill lives in its own directory:

```
skills/
  brainstorming/
    SKILL.md              # Main skill definition
  test-driven-development/
    SKILL.md
    testing-anti-patterns.md  # Supporting reference
  ...
```

### SKILL.md Format

```markdown
---
name: skill-name
description: Use when [triggering conditions]
---

# Skill Title

[Markdown content with instructions, examples, flowcharts]
```

The YAML frontmatter is required. The `description` field is critical - it determines when Copilot loads the skill.

### Shared Core

The skills system uses a shared core module (`lib/skills-core.js`) for skill discovery and parsing, ensuring consistency across platforms.

## Updating

```bash
# Pull latest skills
cd .github/superpowers-repo  # or ~/.copilot/superpowers
git pull origin main
```

Skills are updated immediately - no need to restart VSCode.

## Troubleshooting

### "I don't see any skills loading"

1. Check VSCode version (need 1.108+)
2. Verify `github.copilot.chat.useSkills` is enabled
3. Check skills directory exists: `ls .github/skills/`
4. Ask Copilot: "What skills are available?"

### "Skills seem to be ignored"

1. Be specific in your prompts to trigger relevant skills
2. Skills load based on description matching
3. Try explicitly: "Use the [skill-name] skill"

### "Skill content seems outdated"

```bash
cd .github/superpowers-repo
git pull
```

**Full troubleshooting**: See [INSTALL.md](INSTALL.md)

## Platform Comparison

| Feature | Claude Code | GitHub Copilot | Codex | OpenCode |
|---------|-------------|----------------|-------|----------|
| Skills format | SKILL.md | SKILL.md | CLI tool | Plugin |
| Skill location | Built-in | .github/skills/ | ~/.codex/ | ~/.config/opencode/ |
| Loading | Explicit | Automatic | CLI command | Tool call |
| Subagents | Yes | Sequential | No | Yes |
| Installation | Plugin | Directory | Clone + setup | Plugin |

All platforms use the same skill content with appropriate tool mappings.

## Resources

- **Installation**: [INSTALL.md](INSTALL.md)
- **Creating skills**: `skills/writing-skills/SKILL.md`
- **Main repository**: https://github.com/obra/superpowers
- **GitHub Copilot docs**: https://docs.github.com/en/copilot
- **VSCode Agent Skills**: https://code.visualstudio.com/docs/copilot/customization/agent-skills
- **Blog post**: https://blog.fsck.com/2025/10/09/superpowers/

## Contributing

Skills contributions welcome! 

1. Fork the repository
2. Create a skill following `skills/writing-skills/SKILL.md`
3. Test with GitHub Copilot, Claude Code, or both
4. Submit a pull request

See [CONTRIBUTING.md](../CONTRIBUTING.md) for details.

## License

MIT License - see [LICENSE](../LICENSE) file for details

## Support

- **Issues**: https://github.com/obra/superpowers/issues
- **Discussions**: https://github.com/obra/superpowers/discussions

## Acknowledgments

Originally designed for Claude Code by Jesse Vincent. Adapted for GitHub Copilot, Codex, and OpenCode through community contributions.

---

**Note**: GitHub Copilot Agent Skills is a recent feature (December 2025). Report any issues to help improve the integration.
