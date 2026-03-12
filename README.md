# Agents.gitignore

A comprehensive `.gitignore` for AI coding agents and assistants.

Every developer on your team uses different AI tools. Claude Code, Cursor, Copilot, Aider, Windsurf — each one drops config files, rules, and caches into your repo. Without a shared `.gitignore`, these files end up in pull requests where they don't belong.

This project maintains a single, well-documented gitignore file that covers **25+ AI coding tools** so you can add it once and forget about it.

## Quick start

**Option A — Copy into your project:**

```bash
# Download and append to your .gitignore
curl -sL https://raw.githubusercontent.com/Fellowship-dev/agents-gitignore/main/Agents.gitignore >> .gitignore
```

**Option B — Copy manually:**

Open [`Agents.gitignore`](./Agents.gitignore), copy the sections you need, and paste them into your project's `.gitignore`.

**Option C — Global gitignore (applies to all repos on your machine):**

```bash
# Set up a global gitignore if you don't have one
git config --global core.excludesfile ~/.gitignore_global

# Download
curl -sL https://raw.githubusercontent.com/Fellowship-dev/agents-gitignore/main/Agents.gitignore >> ~/.gitignore_global
```

## Keeping files you actually want

The gitignore covers everything by default. If your project uses AI config files that should be committed (shared team rules, project instructions, etc.), add exceptions with `!` negation patterns.

For example, if your team shares Cursor rules and Claude Code project instructions:

```gitignore
# Ignore all AI tool configs (paste from Agents.gitignore)
.claude/
CLAUDE.md
.cursor/
.cursorrules
# ... etc

# But keep the ones your team shares
!CLAUDE.md
!.cursor/
!.cursor/rules/
!.cursor/rules/my-team-rules.mdc
```

Or if your team uses [Spec-Kit](https://github.com/Fellowship-dev/spec-kit) and wants to share feature specs as documentation:

```gitignore
# Ignore speckit tooling and generated specs
.specify/
specs/

# But keep specs/ as shared team documentation
!specs/
```

**How negation works:**
- `!filename` un-ignores a specific file
- To un-ignore a file inside an ignored directory, you must first un-ignore the directory itself
- Order matters — put exceptions after the ignore rules
- See [Git docs on negation](https://git-scm.com/docs/gitignore#_pattern_format) for details

## What's covered

| Tool | Developer | Files |
|------|-----------|-------|
| [Claude Code](https://docs.anthropic.com/en/docs/claude-code) | Anthropic | `CLAUDE.md`, `.claude/` |
| [Codex CLI](https://github.com/openai/codex) | OpenAI | `AGENTS.md`, `codex.md`, `.codex/` |
| [Gemini CLI](https://github.com/google-gemini/gemini-cli) | Google | `GEMINI.md`, `.gemini/` |
| [Cursor](https://docs.cursor.com) | Anysphere | `.cursor/`, `.cursorrules`, `.cursorignore` |
| [Windsurf](https://docs.codeium.com/windsurf) | Codeium | `.windsurf/`, `.windsurfrules` |
| [GitHub Copilot](https://docs.github.com/en/copilot) | GitHub | `.copilotignore` |
| [Aider](https://aider.chat) | aider-chat | `.aider*`, `.aiderignore` |
| [Continue](https://docs.continue.dev) | Continue.dev | `.continue/`, `.continuerules` |
| [Cline](https://docs.cline.bot) | Cline | `.cline/`, `.clinerules`, `cline_docs/` |
| [Roo Code](https://docs.roocode.com) | RooCode | `.roo/`, `.roorules`, `.roomodes` |
| [Amazon Q](https://docs.aws.amazon.com/amazonq) | AWS | `.amazonq/` |
| [Tabnine](https://www.tabnine.com) | Tabnine | `.tabnine_root`, `.tabnine/` |
| [Junie](https://www.jetbrains.com/junie) | JetBrains | `.junie/` |
| [Cody](https://sourcegraph.com/cody) | Sourcegraph | `.cody/` |
| [Augment](https://docs.augmentcode.com) | Augment | `.augment/`, `.augmentignore` |
| [Devin](https://docs.devin.ai) | Cognition | `REVIEW.md`, `.cognition/` |
| [Trae](https://www.trae.ai) | ByteDance | `.trae/` |
| [Zed AI](https://zed.dev/docs/ai) | Zed Industries | `.zed/` |
| [Bolt.new](https://bolt.new) | StackBlitz | `.bolt/` |
| [CodeRabbit](https://docs.coderabbit.ai) | CodeRabbit | `.coderabbit.yaml` |
| [Qodo](https://docs.qodo.ai) | Qodo | `.codiumai.toml`, `.pr_agent.toml` |
| [Sweep](https://github.com/sweepai/sweep) | Sweep AI | `sweep.yaml` |
| [Plandex](https://github.com/plandex-ai/plandex) | Plandex | `.plandex/` |
| [GPT Engineer](https://github.com/AntonOsika/gpt-engineer) | AntonOsika | `.gpteng/` |
| [Mentat](https://github.com/AbanteAI/mentat) | AbanteAI | `.mentat-config.json` |
| [Spec-Kit](https://github.com/Fellowship-dev/spec-kit) | Fellowship-dev | `.specify/`, `specs/` |

**Not included** (no local project files): Supermaven, Pieces, Blackbox AI, Lovable, v0, GitHub Copilot Chat.

## Notes on specific tools

- **GitHub Copilot** — instructions live at `.github/copilot-instructions.md` inside the `.github/` directory, which most projects already track. The entry is commented out by default to avoid breaking your GitHub config. Uncomment it if you want to ignore Copilot instructions too.

- **Replit** — `.replit` and `replit.nix` are platform config, not just AI. They're commented out by default. Uncomment if you exported a project from Replit and want to clean it up.

- **Zed** — `.zed/` contains general editor settings alongside AI config. If your team uses Zed for non-AI settings, you may want to be more selective.

- **Spec-Kit** — `.specify/` is tooling (scripts, templates, constitution) and should always be ignored. `specs/` contains generated feature specifications — some teams treat these as throwaway build artifacts, others commit them as living documentation. If your team shares specs, add `!specs/` to your exceptions.

- **AGENTS.md** — this is becoming a cross-tool standard ([Linux Foundation stewardship](https://github.com/anthropics/agents-md-spec)). Codex CLI, Devin, Augment, and Junie all read it. If your project uses `AGENTS.md` as shared documentation, add `!AGENTS.md` to your exceptions.

## FAQ

**Do I need the whole file?**
No. Copy only the sections for tools your team actually uses. The file is organized by tool with clear headers so you can pick and choose.

**Should I use this globally or per-project?**
Both work. Per-project (in `.gitignore`) is better for teams — everyone gets the same rules. Global (`~/.gitignore_global`) is better for personal use across all repos.

**A tool is missing!**
[Open a PR](https://github.com/Fellowship-dev/agents-gitignore/pulls) or [file an issue](https://github.com/Fellowship-dev/agents-gitignore/issues). Include the tool name, a link to its docs, and the file paths it creates.

**Why not just use the GitHub gitignore templates?**
There's an [open PR](https://github.com/github/gitignore/pull/4719) for an `Agents.gitignore` in the official repo, but it's been waiting for review since August 2025. This project exists because developers need a solution now.

## Contributing

PRs welcome. When adding a new tool:

1. Add entries to `Agents.gitignore` in alphabetical order within the file
2. Include a comment header with the tool name, developer, and docs URL
3. Update the table in this README
4. Verify the file paths are accurate (check official docs, not just blog posts)

## License

[CC0 1.0 Universal](./LICENSE) — public domain. Use it however you want.
