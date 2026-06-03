# gald3r Readiness Report — Claude Code

> An honest accounting of how much of the gald3r framework installs natively on this
> platform, what degrades to an approximation, and what has no native home yet.
> Generated from a live documentation crawl on 2026-06-02.

**Overall readiness: ✅ Full.** Claude Code is Anthropic's own agentic coding harness, and
gald3r was authored against it. Every C.R.A.S.H. layer — commands, rules, agents, skills,
hooks — maps onto a first-class native mechanism, and MCP is native too. gald3r installs
without compromise.

## C.R.A.S.H. capability grid

| | Capability | Native? | What gald3r gets here | The gap |
|---|---|:---:|---|---|
| **C** | Commands | ✅ | Custom slash commands (`.claude/commands/*.md`, now merged into Skills) — gald3r's `@g-*` set installs as real `/<name>` commands | None — legacy `commands/` and `skills/SKILL.md` both create native slash commands |
| **R** | Rules | ✅ | `CLAUDE.md` persistent instructions + `.claude/rules/*.md` (path-scoped) + auto memory (`MEMORY.md`) | CLAUDE.md is context, not enforcement — for guaranteed constraints gald3r pairs it with a `PreToolUse` hook |
| **A** | Agents | ✅ | Subagents (own context window, system prompt, tool access, permissions) — gald3r's `g-agnt-*` roles install as native `.claude/agents/*.md` | None — custom subagents are first-class; built-in Explore/Plan/general-purpose alongside |
| **S** | Skills | ✅ | Agent Skills (`SKILL.md`, agentskills.io open standard) — gald3r's `g-skl-*` library loads directly, invoke via `/skill-name` | None — progressive disclosure, subagent execution, and dynamic context injection all supported |
| **H** | Hooks | ✅ | Lifecycle hooks (shell / HTTP / LLM prompt) wired in `settings.json` — gald3r's `g-hk-*` session-start / pre-tool / pre-commit wiring all fire | None — 30+ events incl. SessionStart, PreToolUse (can block), PostToolUse, Stop, FileChanged |

_Legend: ✅ native · ⚠️ partial / approximated · ❌ no native mechanism · ❓ unverified_

**Beyond C.R.A.S.H. — MCP: ✅** Native MCP client (stdio / streamable-http / SSE / WebSocket),
OAuth 2.0, `.mcp.json` project config, MCP resources via `@` mentions, prompts as
`/mcp__server__prompt`, and Tool Search — gald3r's MCP backend connects directly. Claude Code
can even run *as* an MCP server (`claude mcp serve`).

## Adoptable extras (non-C.R.A.S.H.)

Platform-native strengths gald3r can lean on, and which need wiring:

| Feature | Status | gald3r fit |
|---|:---:|---|
| Plugins (bundle skills + agents + hooks + MCP, install from marketplaces) | ✅ present | A native packaging path — gald3r could ship its `g-*` suite as one installable plugin |
| Agent SDK (TypeScript + Python, full orchestration control) | ✅ present | A real automation entry point for gald3r tooling and `g-go` pipelines |
| Scheduling (`/schedule` cron routines, desktop tasks, `/loop`) | ⚙️ needs customization | Could drive gald3r heartbeat / scheduled curator + monitor runs |
| Channels (push Telegram / Discord / CI / webhook events into a session) | ⚙️ needs customization | An eventing surface for gald3r WPAC notifications and async handoff |
| Unix-style CLI (`-p` headless, pipe, `--append-system-prompt`, `--add-dir`) | ✅ present | Composes cleanly with gald3r headless / CI invocation |
| Multi-surface parity (CLI, VS Code, JetBrains, Desktop, Web, iOS, Slack, Chrome) | ✅ present | CLAUDE.md / settings / MCP carry across — gald3r install travels with the user |

## The ceiling, and what's beyond it

gald3r runs at full strength on this platform — commands, rules, agents, skills, and hooks all map onto native mechanisms, so the framework installs without compromise. As third-party adaptation goes, this is the high end: nothing here has to be approximated.

But adaptation, however clean, is still gald3r living as a guest inside someone else's tool. The native build goes further — **gald3r_agent**, running on the **gald3r throne** over the **gald3r_world_tree** — where these primitives aren't mapped onto a host, they *are* the substrate. Same framework, no host in between.

> ### gald3r_agent — coming soon. 🌳

---

<sub>Capabilities verified against the platform's official documentation on 2026-06-02, and
re-verified each release via the gald3r platform-docs crawl. This report describes gald3r's
third-party adaptation surface; it is not an endorsement or critique of the platform itself.</sub>
