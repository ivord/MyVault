# MyVault Setup

Obsidian vault + Claude Code integration. Follow these steps on a new Mac.

---

## 1. Obsidian

### Install

**Option A — Homebrew (recommended)**

```bash
brew install --cask obsidian
```

**Option B — Direct download**

1. Go to [obsidian.md](https://obsidian.md) → Download for Mac
2. Open the `.dmg` and drag Obsidian to `/Applications`

### Open the vault

1. Launch Obsidian
2. Click **Open folder as vault**
3. Select this `MyVault/` folder

### Install community plugins

1. Settings → **Community plugins** → turn off Restricted mode
2. Click **Browse** and install:
   - **Templater** — template engine for `Templates/`
   - **Local REST API** — exposes Obsidian to Claude via MCP
3. Enable both plugins after installing

### Get the API key

1. Obsidian Settings (`⌘ ,`) → Community plugins
2. Under **Enabled plugins**, click **Local REST API**
3. The **API Key** field is at the top — click the copy icon beside it

---

## 2. Claude Code

```bash
npm install -g @anthropic/claude-code
```

Open vault in Claude Code:

```bash
cd ~/Documents/MyVault
claude
```

---

## 3. Obsidian API Key

### Get the key

1. Open Obsidian → Settings (`⌘ ,`)
2. Community plugins → **Local REST API** → click the plugin name to open its settings
3. Find **API Key** — click the copy icon next to it

### Add to shell

```bash
echo 'export OBSIDIAN_API_KEY="paste-your-key-here"' >> ~/.zshrc && source ~/.zshrc
```

Verify:

```bash
echo $OBSIDIAN_API_KEY
```

---

## 4. MCP — Obsidian Server

Already configured in `.claude/settings.json`. Requires:

- Obsidian running with **Local REST API** plugin enabled
- `OBSIDIAN_API_KEY` set in environment (step 3)
- `npx` available (comes with Node.js)

Verify it connects:

```bash
npx mcp-obsidian --version
```

---

## 5. RTK (Token Optimizer)

Install [RTK](https://github.com/reach/rtk) — Claude Code hook that reduces token usage:

```bash
cargo install rtk
```

Verify:

```bash
rtk --version
rtk gain
```

The hook is already configured in `~/.claude/settings.json` (`PreToolUse → Bash → rtk hook claude`).

---

## 6. Global Claude Settings

Copy `~/.claude/` from old Mac or recreate:

- `~/.claude/CLAUDE.md` — global identity file (12 tokens, minimal)
- `~/.claude/RTK.md` — RTK usage reference
- `~/.claude/settings.json` — permissions, hooks, MCP servers, plugins

Key plugins enabled in settings:

```json
"enabledPlugins": {
  "clangd-lsp@claude-plugins-official": true,
  "gopls-lsp@claude-plugins-official": true,
  "claude-mem@thedotmack": true
}
```

---

## 7. Vault Structure

```
MyVault/
├── Projects/     → active work (one subfolder per project)
│   └── _inbox/  → quick captures
├── Areas/        → Career/ Health/ Finance/ Learning/
├── Resources/    → Concepts/ Frontend/ Backend/ Architecture/ Books/ Articles/
├── Archive/      → completed/inactive
├── Templates/    → Note.md, Project.md, Area.md, Resource.md, Concept.md
├── CLAUDE.md     → Claude context (loaded every session)
├── AGENTS.md     → agent instructions and repo map
└── README.md     → this file
```

---

## 8. Note Templates

Templates live in `Templates/`. In Obsidian: Settings → Templater → set template folder to `Templates/`.

| Template | Use for |
| -------- | ------- |
| `Note.md` | Generic capture |
| `Project.md` | New project |
| `Area.md` | New area of responsibility |
| `Resource.md` | Article, book, reference |
| `Concept.md` | Atomic note (`Resources/Concepts/`) |

---

## 9. Work Projects (GitLab)

Each project in `~/Documents/workspace/` has a local-only `AGENTS.md` and `CLAUDE.md` excluded via `.git/info/exclude`. To recreate on a new Mac, run Claude Code in this vault and ask it to regenerate them.

Personal projects (`~/Documents/pp/`) have `AGENTS.md` tracked in git normally.

---

## Checklist

- [ ] Obsidian installed and vault opened
- [ ] Local REST API plugin installed and enabled
- [ ] `OBSIDIAN_API_KEY` in `~/.zshrc`
- [ ] Claude Code installed (`npm install -g @anthropic/claude-code`)
- [ ] RTK installed (`cargo install rtk`)
- [ ] `~/.claude/settings.json` copied/restored
- [ ] `npx mcp-obsidian --version` works
- [ ] Open vault with `claude` and verify `CLAUDE.md` loads
