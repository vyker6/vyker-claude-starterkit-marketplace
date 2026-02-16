# vyker-claude-starterkit

All-in-one Claude Code plugin that bundles essential skills, commands, and tools for productive development.

## Installation

```bash
# Add as a marketplace
/plugin marketplace add <username>/vyker-claude-starterkit

# Install
/plugin install vyker-claude-starterkit
```

Or clone directly:
```bash
git clone https://github.com/<username>/vyker-claude-starterkit ~/.claude/skills/vyker-claude-starterkit
```

## What's Included

### Skills (18)

| Skill | Description |
|-------|-------------|
| brainstorming | Explore requirements and design before implementation |
| dispatching-parallel-agents | Handle 2+ independent tasks concurrently |
| executing-plans | Execute implementation plans with review checkpoints |
| finishing-a-development-branch | Guide completion of development work |
| receiving-code-review | Handle code review feedback with rigor |
| requesting-code-review | Verify work meets requirements |
| subagent-driven-development | Execute plans with subagents |
| systematic-debugging | Diagnose bugs methodically |
| test-driven-development | Write tests before implementation |
| using-git-worktrees | Isolate feature work |
| using-superpowers | Skill discovery and bootstrapping |
| verification-before-completion | Verify before claiming done |
| writing-plans | Create implementation plans |
| writing-skills | Create and verify new skills |
| frontend-design | Production-grade frontend interfaces |
| claude-md-improver | Audit and improve CLAUDE.md files |
| vibe-security | Secure coding practices (OWASP) |
| deploy | Automated deploy pipeline |

### Commands

| Command | Description |
|---------|-------------|
| /brainstorm | Explore requirements before building |
| /execute-plan | Execute a saved implementation plan |
| /write-plan | Create a detailed implementation plan |
| /revise-claude-md | Update CLAUDE.md with session learnings |
| /deploy | Full deploy pipeline: test, debug, audit, PR, build |

### Other Features

- **Code Reviewer Agent** — Automated code review against plans and standards
- **GitHub MCP Server** — Repository management via MCP
- **Explanatory Mode** — Educational insights during coding
- **Session Bootstrap** — Automatic skill discovery on startup

## Credits

This plugin bundles content from:
- [superpowers](https://github.com/obra/superpowers) (MIT) by Jesse Vincent
- [frontend-design](https://github.com/anthropics/claude-plugins-official) by Anthropic
- [claude-md-management](https://github.com/anthropics/claude-plugins-official) by Anthropic
- [explanatory-output-style](https://github.com/anthropics/claude-plugins-official) by Anthropic
- [github](https://github.com/anthropics/claude-plugins-official) by GitHub
- [VibeSec-Skill](https://github.com/BehiSecc/VibeSec-Skill) by BehiSec

## License

MIT
