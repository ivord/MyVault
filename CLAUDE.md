# MyVault

Obsidian vault. Full read/write on all `.md` files.

## Me

Senior full-stack dev (5+ yrs), frontend-heavy. Mobile-first product team at work; personal SaaS + tools on the side.

- **Mobile:** React Native, Flutter · **Web:** Next.js, React · **Lang:** TypeScript (strict), Dart
- **Backend:** Go + Fiber, Node.js · **DB:** PostgreSQL, MySQL, Prisma · **Infra:** Docker, Nx, pnpm
- **VCS:** GitLab (work), GitHub (personal)

**Style:** trade-offs over best practices · simplicity first · ship then refactor · direct, no filler · show code not prose

**Never:** explain React/TS/Go basics · restate code in comments · abstract one-off code · ask obvious questions

**Focus** *(update when priorities shift)*: Building — · Learning — · Thinking —

## Rules

- Skip all basics — deep fluency in React, TS, Go, hooks, generics, system design
- Default code: TypeScript; Go for backend topics
- New notes: correct PARA folder + frontmatter + wikilinks to related notes
- Always bump `updated:` when editing a note

## PARA Structure

Projects → Areas → Resources → Archive (most → least actionable)

```
Projects/   goal + deadline; done → Archive/
  _inbox/   quick captures, triage first
Areas/      Career/ Health/ Finance/ Learning/   (never done)
Resources/  Concepts/ Frontend/ Backend/ Architecture/ Books/ Articles/
Archive/    completed projects, inactive notes
Templates/
```

## Frontmatter by Type

| field | project | area | resource | archive | concept |
|-------|---------|------|----------|---------|---------|
| type | project | area | resource | archive | concept |
| title | ✓ | ✓ | ✓ | ✓ | ✓ (as a claim) |
| tags | ✓ | ✓ | ✓ | ✓ | ✓ |
| status | active\|on-hold\|done | — | — | — | — |
| goal | ✓ | — | — | — | — |
| deadline | ✓ | — | — | — | — |
| stack | ✓ | — | — | — | — |
| source | — | — | ✓ | — | ✓ (optional) |
| author | — | — | ✓ | — | — |
| archived-from | — | — | — | Projects\|Areas\|Resources | — |
| archived-on | — | — | — | ✓ | — |
| related | ✓ | ✓ | ✓ | ✓ | ✓ |
| created/updated | ✓ | ✓ | ✓ | ✓ | ✓ |

- Wikilinks `[[Note Title]]` for internal links; populate `related:`
- Tags: frontmatter only — `react-native` `nextjs` `typescript` `go` `flutter` `architecture` `performance`
- H1 = filename; no emoji in filenames; language on all code blocks

## Atomic Notes (`Resources/Concepts/`)

One idea · self-contained · own words · **title is a claim** not a topic · linked to ≥1 note · permanent (revise in place)

When writing: reframe title as declarative statement; add wikilinks to existing notes; flag if >1 idea (suggest split)

## Workflows

- **capture X** → `Projects/_inbox/` with frontmatter
- **triage inbox** → move each note to correct PARA folder
- **project note X** → `Projects/X/index.md` (goal, deadline, stack, status, open questions)
- **close project X** → move to `Archive/` with closing summary
- **find notes about X** → search tags + titles + content, return linked list

## MCP

`obsidian` MCP = live search, backlinks, open-in-app. Needs Local REST API plugin + `OBSIDIAN_API_KEY`.
