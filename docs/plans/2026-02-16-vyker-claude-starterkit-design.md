# vyker-claude-starterkit Design

## Overview

A single Claude Code plugin that bundles 17+ skills, 4+ commands, agents, hooks, and a custom `/deploy` pipeline. One install gives you a complete development toolkit for any Claude Code project.

## Approach

Unified plugin bundle — all skills from existing plugins are copied into a single repo with a unified plugin manifest. This provides:
- Single install command
- No network dependencies at runtime
- Full control over what's included
- Easy to add custom skills alongside bundled ones

## Plugin Structure

```
vyker-claude-starterkit/
├── .claude-plugin/
│   └── plugin.json
├── .mcp.json                          # GitHub MCP server
├── skills/
│   ├── brainstorming/                 # From superpowers
│   ├── dispatching-parallel-agents/
│   ├── executing-plans/
│   ├── finishing-a-development-branch/
│   ├── receiving-code-review/
│   ├── requesting-code-review/
│   ├── subagent-driven-development/
│   ├── systematic-debugging/
│   ├── test-driven-development/
│   ├── using-git-worktrees/
│   ├── using-superpowers/
│   ├── verification-before-completion/
│   ├── writing-plans/
│   ├── writing-skills/
│   ├── frontend-design/              # From frontend-design plugin
│   ├── claude-md-improver/           # From claude-md-management
│   ├── vibe-security/                # From VibeSec-Skill
│   └── deploy/                       # Custom: deploy pipeline skill
├── commands/
│   ├── brainstorm.md
│   ├── execute-plan.md
│   ├── write-plan.md
│   ├── revise-claude-md.md
│   └── deploy.md                     # Custom: /deploy command
├── agents/
│   └── code-reviewer.md
├── hooks/
│   ├── hooks.json                    # Merged session-start hooks
│   └── session-start.sh
├── lib/
│   └── skills-core.js
├── README.md
└── LICENSE
```

## Plugin Metadata

```json
{
  "name": "vyker-claude-starterkit",
  "description": "All-in-one Claude Code plugin: superpowers, frontend design, security, CLAUDE.md management, and custom skills",
  "version": "1.0.0",
  "author": { "name": "Vyker" }
}
```

## Bundled Skills (17)

### From superpowers (14 skills)
1. **brainstorming** — Explore requirements and design before implementation
2. **dispatching-parallel-agents** — Handle 2+ independent tasks concurrently
3. **executing-plans** — Execute implementation plans with review checkpoints
4. **finishing-a-development-branch** — Guide completion of development work (merge, PR, cleanup)
5. **receiving-code-review** — Handle code review feedback with technical rigor
6. **requesting-code-review** — Verify work meets requirements before merging
7. **subagent-driven-development** — Execute plans with independent tasks using subagents
8. **systematic-debugging** — Diagnose bugs and test failures methodically
9. **test-driven-development** — Write tests before implementation
10. **using-git-worktrees** — Isolate feature work in git worktrees
11. **using-superpowers** — Skill discovery and bootstrapping
12. **verification-before-completion** — Verify before claiming work is done
13. **writing-plans** — Create implementation plans from specs
14. **writing-skills** — Create and verify new skills

### From other plugins (3 skills)
15. **frontend-design** — Create production-grade frontend interfaces with high design quality
16. **claude-md-improver** — Audit and improve CLAUDE.md files
17. **vibe-security** — Secure coding practices for web applications (XSS, CSRF, SSRF, SQL injection, etc.)

## Custom: `/deploy` Command

Fully automated deployment pipeline that runs sequentially without confirmation prompts.

### Pipeline Steps

1. **Test** — Runs the project's test suite using the test-driven-development skill. If tests fail, invokes systematic-debugging to find and fix root causes automatically. Loops until all tests pass.

2. **Design audit** — If frontend files changed, validates components against the project's design system using the frontend-design skill. Auto-fixes design inconsistencies.

3. **Diff review** — Identifies all changes since last build/commit. Reviews diffs for completeness. Stages and commits with a descriptive message.

4. **PR & push** — Creates a pull request via `gh` CLI. Pushes to the GitHub repo. Includes a summary of all changes.

5. **Build** — Detects the project's tech stack from config files (package.json, pubspec.yaml, Podfile, build.gradle, etc.). Runs the appropriate build commands for iOS, Android, and/or web depending on what changed. Reports build results.

### Stack Detection

The build step is framework-agnostic. It detects the stack by looking for:
- `package.json` → npm/yarn/pnpm build (web, React Native, Expo)
- `pubspec.yaml` → Flutter build
- `Podfile` / `*.xcodeproj` → iOS build (xcodebuild)
- `build.gradle` / `settings.gradle` → Android build (gradle)
- `next.config.*` → Next.js build
- `capacitor.config.*` → Capacitor build
- Other config files as needed

## Hooks

On session start, the merged hook:
1. Injects superpowers skill discovery instructions (how to find and use all skills)
2. Enables explanatory output mode (educational insights on implementation choices)

## MCP Servers

GitHub MCP server for repository management (issues, PRs, code review, search).

## Distribution

Hosted on GitHub. Install via:
```bash
/plugin marketplace add <username>/vyker-claude-starterkit
/plugin install vyker-claude-starterkit
```

## Source Plugins

This bundle incorporates content from:
- [superpowers](https://github.com/obra/superpowers) (MIT License) by Jesse Vincent
- [frontend-design](https://github.com/anthropics/claude-plugins-official) by Anthropic
- [claude-md-management](https://github.com/anthropics/claude-plugins-official) by Anthropic
- [explanatory-output-style](https://github.com/anthropics/claude-plugins-official) by Anthropic
- [github](https://github.com/anthropics/claude-plugins-official) by GitHub
- [VibeSec-Skill](https://github.com/BehiSecc/VibeSec-Skill) by BehiSec
