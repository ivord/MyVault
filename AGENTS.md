# AGENTS.md

Agent instructions for this Obsidian vault. Read alongside `CLAUDE.md`.

## Owner

Senior full-stack developer — React Native, Flutter, Next.js, Go + Fiber, Node.js, TypeScript.

## Repository Map

| Project | Repo | Stack | CI |
| ------- | ---- | ----- | -- |
| Work projects | GitLab (private) | RN, Nx monorepo, pnpm | GitLab CI |
| Personal projects | GitHub (private) | Next.js, Go, Node.js | GitHub Actions |

> When referencing code, ask for the repo URL if not provided. Never guess paths.

## Vault ↔ Repo Relationship

This vault documents decisions, patterns, and knowledge that inform the codebase — not the code itself.

- `Resources/Architecture/` — ADRs and system design notes that justify repo structure
- `Resources/Concepts/` — atomic notes on patterns used across repos
- `Projects/` — one note per active repo or feature; tracks goal, status, open questions
- `Areas/Learning/` — skills being developed, mapped to real work in repos

## Agent Permissions in This Vault

| Action | Allowed |
| ------ | ------- |
| Read any `.md` file | Yes |
| Write / create notes | Yes — follow PARA structure and frontmatter schema |
| Delete notes | No — move to `Archive/` instead |
| Access repo code directly | No — vault only; user provides code snippets |
| Run shell commands | No — read/write vault files only |

## Note ↔ Code Linking Convention

When a note references a specific file or function in a repo, use this inline format:

```
`path/to/file.ts:functionName` (repo-name)
```

Example: `apps/mobile/src/screens/HomeScreen.tsx:HomeScreen` (watchlist-frontend)

## Agent Workflow

1. Read `CLAUDE.md` for full context on the owner's stack and preferences
2. Check `Projects/` for the relevant project note before making suggestions
3. When creating any note, apply the correct PARA type and frontmatter schema
4. When a decision is made during a session, offer to write it as a note in `Resources/Architecture/`
