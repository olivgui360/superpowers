# Installing Superpowers for GitHub Copilot in VSCode

Complete guide for using Superpowers skills with GitHub Copilot in Visual Studio Code.

## Prerequisites

- Visual Studio Code (version 1.108 or later)
- GitHub Copilot extension installed and activated
- Git installed

## Quick Install

The easiest way to install Superpowers for GitHub Copilot is to clone this repository directly into the `.github/skills/` directory of your project:

```bash
# In your project directory
mkdir -p .github
git clone https://github.com/obra/superpowers.git .github/superpowers-repo
ln -s .github/superpowers-repo/skills .github/skills
```

## Manual Installation Options

### Option 1: Project-Level Installation (Recommended)

Install skills for a specific project:

```bash
# In your project directory
mkdir -p .github
cd .github
git clone https://github.com/obra/superpowers.git superpowers-repo

# Create symlink to make skills discoverable
ln -s superpowers-repo/skills skills
```

### Option 2: User-Level Installation

Install skills globally for all your projects:

```bash
# Clone superpowers to your user directory
mkdir -p ~/.copilot
git clone https://github.com/obra/superpowers.git ~/.copilot/superpowers

# Create symlink to skills
ln -s ~/.copilot/superpowers/skills ~/.copilot/skills
```

### Option 3: Direct Copy (No Git)

If you prefer not to use Git:

```bash
# Download and extract to .github/skills/
mkdir -p .github/skills
cd .github/skills

# Copy each skill directory from this repository
# Each skill directory contains a SKILL.md file
```

## Enable Agent Skills in VSCode

1. Open VSCode Settings (Ctrl+, or Cmd+,)
2. Search for "copilot agent skills"
3. Enable the setting: `"github.copilot.chat.useSkills": true`

Alternatively, add to your `settings.json`:

```json
{
  "github.copilot.chat.useSkills": true
}
```

## Verify Installation

1. Open VSCode in your project directory
2. Open GitHub Copilot Chat (Ctrl+Shift+I or Cmd+Shift+I)
3. Ask: "What skills do you have available?"
4. Copilot should list the superpowers skills

You should see skills like:
- `brainstorming` - Interactive design refinement
- `test-driven-development` - RED-GREEN-REFACTOR cycle
- `systematic-debugging` - 4-phase root cause process
- And more...

## Using Skills

GitHub Copilot will automatically load relevant skills based on your conversation context. For example:

- When you ask about debugging, the `systematic-debugging` skill loads automatically
- When you start implementing a feature, `test-driven-development` loads
- When you discuss design, `brainstorming` loads

You can also explicitly reference skills in your prompts:
```
"Use the test-driven-development skill to help me add a new feature"
```

## Tool Mapping

Superpowers skills were originally designed for Claude Code, which has different tools than GitHub Copilot. Here's how the tools map:

| Claude Code Tool | GitHub Copilot Equivalent |
|------------------|---------------------------|
| `Skill` tool | Skills auto-load based on context |
| `TodoWrite` | Use VSCode TODO comments or task tracking |
| `Task` (subagent) | Ask Copilot to handle subtasks sequentially |
| File operations | Native VSCode file operations |
| `read`, `edit`, `create` | Use Copilot's edit capabilities |

## Personal Skills

Create your own custom skills:

### Project Skills

```bash
# In your project
mkdir -p .github/skills/my-custom-skill
```

Create `.github/skills/my-custom-skill/SKILL.md`:

```markdown
---
name: my-custom-skill
description: Use when [specific triggering conditions and symptoms]
---

# My Custom Skill

[Your skill content here]
```

### User-Level Skills

```bash
mkdir -p ~/.copilot/skills/my-skill
```

Create `~/.copilot/skills/my-skill/SKILL.md` with the same format.

## Skill Priority

Skills are loaded with this priority:

1. **Project skills** (`.github/skills/`) - Highest priority
2. **Personal skills** (`~/.copilot/skills/`)
3. **Superpowers skills** (from this repository)

## Updating

### If installed via Git

```bash
# For project-level installation
cd .github/superpowers-repo
git pull

# For user-level installation
cd ~/.copilot/superpowers
git pull
```

### Manual update

Re-download or copy the latest skill files from the repository.

## Troubleshooting

### Skills not loading

1. **Check VSCode version**: Ensure you have VSCode 1.108 or later
   ```bash
   code --version
   ```

2. **Verify skill location**: Check that skills are in the correct directory
   ```bash
   ls .github/skills/
   # Should show skill directories like: brainstorming, test-driven-development, etc.
   ```

3. **Check SKILL.md format**: Each skill directory must have a `SKILL.md` file with valid YAML frontmatter

4. **Enable setting**: Verify `github.copilot.chat.useSkills` is set to `true`

5. **Restart VSCode**: Sometimes needed after installing skills

### Copilot doesn't mention skills

- Ask explicitly: "What skills are available?" or "Use the [skill-name] skill"
- Be specific about your task to trigger relevant skills
- Skills load based on context matching their `description` field

### Skills seem outdated

```bash
# Pull latest changes
cd .github/superpowers-repo  # or ~/.copilot/superpowers
git pull origin main
```

## Differences from Claude Code

GitHub Copilot's Agent Skills implementation differs slightly from Claude Code:

1. **Automatic loading**: Copilot loads skills based on context matching, whereas Claude Code requires explicit invocation
2. **No Skill tool**: Skills are discovered automatically from the file system
3. **Tool differences**: Some Claude Code-specific tools don't have direct equivalents
4. **Subagents**: GitHub Copilot handles tasks sequentially rather than dispatching parallel subagents

These differences are handled in the skill content where necessary, with GitHub Copilot using its native capabilities.

## Getting Help

- **Issues**: https://github.com/obra/superpowers/issues
- **Main docs**: https://github.com/obra/superpowers
- **GitHub Copilot docs**: https://docs.github.com/en/copilot
- **VSCode Agent Skills**: https://code.visualstudio.com/docs/copilot/customization/agent-skills

## Contributing

Found an issue with VSCode/Copilot integration? Have improvements?

1. Fork the repository
2. Make your changes
3. Test with GitHub Copilot
4. Submit a pull request

## Note

GitHub Copilot Agent Skills support is a recent feature (released December 2025). If you encounter compatibility issues, please report them on the GitHub repository.
