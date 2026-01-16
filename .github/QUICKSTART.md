# Quick Start: Superpowers with GitHub Copilot

Get started in 5 minutes.

## 1. Install

```bash
mkdir -p .github
git clone https://github.com/obra/superpowers.git .github/superpowers-repo
ln -s .github/superpowers-repo/skills .github/skills
```

## 2. Enable in VSCode

Add to settings:

```json
{
  "github.copilot.chat.useSkills": true
}
```

## 3. Verify

Open Copilot Chat (Ctrl+Shift+I):

```
What skills do you have available?
```

## 4. Try It

Ask Copilot:

```
I need to add email validation to my signup form
```

Copilot will:
1. Load **brainstorming** - ask about requirements
2. Load **test-driven-development** - guide you to write test first
3. Enforce RED-GREEN-REFACTOR cycle

## What's Happening?

- **Skills auto-load** based on your conversation
- **TDD enforced** - tests before code, always
- **Systematic debugging** - root cause before fixes
- **Design first** - questions before implementation

## Next Steps

- **Full docs**: [docs/README.vscode.md](../docs/README.vscode.md)
- **Installation options**: [INSTALL.md](INSTALL.md)
- **Issues**: https://github.com/obra/superpowers/issues
