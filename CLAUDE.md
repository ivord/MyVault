# MyVault

Obsidian vault. Claude has full read/write access to all `.md` files.

## Stack

Senior full-stack dev, frontend-focused.

- **Mobile:** React Native, Flutter
- **Web:** Next.js (App Router), React
- **Language:** TypeScript (strict), Dart
- **Backend:** Go + Fiber (APIs/microservices), Node.js (BFF/tooling)
- **DB:** PostgreSQL, MySQL, Prisma ORM
- **Infra:** Docker, Nx monorepo, pnpm workspaces, REST + BFF + API Gateway
- **CI/CD:** GitLab CI (work), GitHub Actions (personal)

## Memory

What Claude should carry across every session — not the vault structure, but the person.

**Who I am**
- Senior full-stack dev, 5+ yrs, frontend-heavy
- Work: mobile-first product team (React Native, Flutter), monorepo
- Side projects: Next.js SaaS, Go microservices, personal tools

**How I think**
- Prefer trade-offs over "best practices" — context always matters
- Bias toward simplicity; abstraction must earn its place
- Ship first, refactor when the pattern is clear
- Strong opinions, loosely held — challenge me with evidence

**How I communicate**
- Direct, no filler — skip "great question" and preambles
- Short answers unless depth is needed
- Show code, not just describe it
- If I'm wrong, say so plainly

**What Claude should never do**
- Explain what React, TypeScript, Go, or hooks are
- Add comments that restate what the code already says
- Suggest abstractions for one-off code
- Ask clarifying questions when context is obvious

**Current focus** *(update this when priorities shift)*
- Building: —
- Learning: —
- Thinking about: —

---

## Claude Rules

- Senior level — skip all basics, assume deep fluency in React, TS, Go, hooks, generics, system design
- Code examples: TypeScript by default, Go for backend
- New notes: add frontmatter, correct folder, wikilinks to related notes
- Project notes must include: stack, status, open questions
- Tag all notes with relevant tech tags

## Structure (PARA)

PARA: Projects → Areas → Resources → Archive.

```text
Projects/          → active work with a goal & deadline (one subfolder each)
  _inbox/          → quick captures, triage here first
Areas/             → ongoing responsibilities, no end date
  Career/          → growth, performance, interviews
  Health/          → habits, fitness
  Finance/         → budget, investments
  Learning/        → courses, skills in progress
Resources/         → reference material, no action needed
  Concepts/        → atomic notes — one idea per note, permanent
  Frontend/        → React, RN, Flutter, Next.js notes
  Backend/         → Go, Node.js, API design
  Architecture/    → system design, patterns, decisions
  Books/           → book notes & highlights
  Articles/        → saved articles & summaries
Archive/           → completed projects, inactive areas, old resources
Templates/         → note templates
```

**PARA rules:**
- A note belongs to the most actionable bucket — Projects first, Archive last
- Projects must have a clear goal and end state; when done, move to `Archive/`
- Areas never finish — career, health, finance are permanent responsibilities
- Resources = knowledge you might need later, no current action

## Note Format

Every note must have frontmatter. Use the schema for its PARA type:

**Projects**
```yaml
---
type: project
title: ""
tags: []
status: active        # active | on-hold | done
goal: ""
deadline: YYYY-MM-DD
stack: []
related: []
created: YYYY-MM-DD
updated: YYYY-MM-DD
---
```

**Areas**
```yaml
---
type: area
title: ""
tags: []
related: []
created: YYYY-MM-DD
updated: YYYY-MM-DD
---
```

**Resources**
```yaml
---
type: resource
title: ""
tags: []
source: ""            # URL, book title, course name
author: ""
related: []
created: YYYY-MM-DD
updated: YYYY-MM-DD
---
```

**Archive**
```yaml
---
type: archive
title: ""
tags: []
archived-from: ""     # Projects | Areas | Resources
archived-on: YYYY-MM-DD
related: []
created: YYYY-MM-DD
updated: YYYY-MM-DD
---
```

- Wikilinks: `[[Note Title]]` for all internal links; populate `related:` with key links
- Tags: frontmatter only — `react-native` `nextjs` `typescript` `go` `nodejs` `flutter` `architecture` `performance`
- H1 = filename; no emoji in filenames; always name language in code blocks
- When updating a note always bump `updated:` to today

## Atomic Notes

Atomic notes live in `Resources/Concepts/`. Rules:

1. **One idea** — one note = one concept, pattern, or insight. Split if it grows.
2. **Self-contained** — readable without any other context. No "as mentioned above."
3. **Your own words** — never copy-paste; restate to prove you understood it.
4. **Title is a claim** — not a topic. Bad: `Memoization`. Good: `Memoization prevents redundant renders in React`.
5. **Always linked** — every atomic note links to at least one other note via `related:` or wikilinks in the body.
6. **Permanent** — written to last. Revise in place; bump `updated:`.

Frontmatter for atomic notes:

```yaml
---
type: concept
title: ""              # written as a claim/statement
tags: []
related: []
source: ""             # where the idea came from (optional)
created: YYYY-MM-DD
updated: YYYY-MM-DD
---
```

When writing an atomic note, Claude will:
- Reframe the title as a declarative statement if it isn't already
- Add wikilinks to related concepts that already exist in the vault
- Flag if the note contains more than one distinct idea (suggest splitting)

## Workflows

- **"capture X"** — create note in `Projects/_inbox/`, add frontmatter
- **"triage inbox"** — move each `_inbox/` note to correct PARA folder
- **"project note for X"** — create `Projects/X/index.md` with goal, deadline, stack, status, open questions
- **"close project X"** — move `Projects/X/` to `Archive/` with a closing summary
- **"find notes about X"** — search tags + titles + content, return linked list

## MCP

`obsidian` MCP server = live search, backlinks, open-in-app. Needs Local REST API plugin + `OBSIDIAN_API_KEY` env var.
