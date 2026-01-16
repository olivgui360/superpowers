# Installing Superpowers for GitHub Copilot

## Prerequisites

- VSCode 1.108+, GitHub Copilot extension, Git

## Installation

### Project-Level (Recommended)

```bash
mkdir -p .github
git clone https://github.com/obra/superpowers.git .github/superpowers-repo
ln -s .github/superpowers-repo/skills .github/skills
```

### User-Level (All Projects)

```bash
mkdir -p ~/.copilot
git clone https://github.com/obra/superpowers.git ~/.copilot/superpowers
ln -s ~/.copilot/superpowers/skills ~/.copilot/skills
```

## Enable in VSCode

Add to VSCode settings:

```json
{
  "github.copilot.chat.useSkills": true
}
```

## Verify

Open Copilot Chat (Ctrl+Shift+I) and ask: "What skills do you have available?"

## Updating

```bash
cd .github/superpowers-repo  # or ~/.copilot/superpowers
git pull
```

## Troubleshooting

**Skills not loading?**
- Check VSCode version: `code --version` (need 1.108+)
- Verify setting: `"github.copilot.chat.useSkills": true`
- Check directory: `ls .github/skills/`

**Copilot not following skills?**
- Ask explicitly: "Use the [skill-name] skill"
- Skills load based on context matching their `description` field

**Need more help?** See [docs/README.vscode.md](../docs/README.vscode.md)
