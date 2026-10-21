# 🚑 CCAR-F · Weak-Areas Deep Dive

**Claude Certified Architect – Foundations** · Only the 20 objectives where you lost points · each one explained from the ground up, with official reading links

> 📌 **What this is:** the companion to `CCARF-STUDY-GUIDE.md`. That file covers *everything* in short form. This one covers **only your weak spots**, in depth: *what the idea is, why the wrong answers look right, what the exam wants, and exactly which official page to read*.
>
> 📊 **Source of your scores:** `docs/score-map.md` (your 5 Oct report): 10 objectives at 0%, 9 at 33–50%, 1 at 75%.
>
> ⚖️ **Golden rule:** when today's product differs from the exam guide (v1.0, July 2026), **answer per the guide**. Every difference is flagged with ⚖️.
>
> 🔗 **Links:** every link below was checked on 21 Oct 2026 and returned HTTP 200. Claude Code docs live at `code.claude.com/docs`, API docs at `platform.claude.com/docs`.
>
> 🚫 No real exam questions appear here. Every scenario and question is original.

---

## 🧭 How to read this file

| Icon | Meaning |
|---|---|
| 🟥 | You scored **0%**: top priority |
| 🟧 | You scored **33–50%**: half-understood, which is the riskiest state |
| 🟨 | You scored **75%**: polish |
| 📘 | **Understand it first:** definition, plain-English explanation, how it works, analogy, key terms |
| 💡 | The rule, in one picture |
| 🤔 | Why you probably got it wrong (the misconception) |
| 🧪 | Worked example |
| 🪤 | Trap: a wrong answer that looks right |
| 🎯 | The exam answer pattern |
| ⚖️ | Guide vs today's docs: answer per the guide |
| 📖 | Official reading: **go read this**, and what to look for there |
| 🔧 | Lab drill in this repo |
| 🧠 | One line to memorize |
| 🏁 | Self-check (guess first, then click ▶) |

**Each weak spot follows the same layout**, so you always know where you are:

```
 🎯 score card
 📘 UNDERSTAND IT FIRST ── 📖 definition · 🧭 what it is · ⚙️ how it works · 🏠 analogy · 🔤 key terms
 💡 the rule, in one picture
 🤔 why you probably got it wrong
 📚 deep explanation → 🧪 worked example → 🪤 traps → 🎯 exam pattern
 📖 official reading → 🔧 lab drill → 🧠 memory line → 🏁 self-check
```

> 💡 **First pass:** read only the 📘 blocks of every section, top to bottom (≈ 90 min). That builds the mental model. **Second pass:** read the rest of each section to turn understanding into exam answers.

---

## 📚 Contents

- **Part 0** · 🗺️ Your gap map, priorities and study plan
- **Part 1** · 🔑 The one idea behind most of your misses
- **Part 2** · 💻 D3 Claude Code: W1–W10 (O16, O14, O8, O12, O13, O15, O11, O30, O17 + O32, O20)
- **Part 3** · 🤖 D1 Agentic: W11–W14 (O1, O2, O3, O4)
- **Part 4** · 🛠️ D2 Tools & MCP: W15–W16 (O37, O33)
- **Part 5** · 📄 D4 Prompting & Output: W17–W19 (O29, O26, O23)
- **Part 6** · 🧩 Neighbor topics your weak spots lean on (gates, structured errors, escalation)
- **Part 7** · 🥊 Confusion pairs: the 18 look-alikes that cost you points
- **Part 8** · 🧪 Weak-spot drill: 36 original questions with explained answers
- **Part 9** · 📖 Official reading library, by objective
- **Part 10** · 🌙 One-page weak-spot cram sheet
- **Appendix A** · ✅ Mastery tracker
- **Appendix B** · 📖 Concept glossary (A–Z), 100+ terms

---

# Part 0 · 🗺️ Your gap map, priorities and study plan

## 0.1 The 20 objectives you need to fix

```
🟥 0%      O1 O2 O8 O12 O13 O14 O15 O16 O29 O37             (10)
🟧 33%     O3 O26                                             (2)
🟧 40%     O17                                                (1)
🟧 50%     O4 O11 O20 O30 O32 O33                             (6)
🟨 75%     O23                                                (1)
```

## 0.2 Where they cluster

| Domain | Weight | Your weak objectives | Verdict |
|---|---|---|---|
| 💻 **D3** Claude Code Config & Workflows | 20% | O8 · O11 · O12 · O13 · O14 · O15 · O16 · O17 · O20 · O30 · O32 | 🚨🚨 **11 of 20 gaps.** Biggest lever. |
| 🤖 **D1** Agentic Architecture | 27% | O1 · O2 · O3 · O4 | 🚨 Mechanics, not design. Your design instincts are 100%. |
| 🛠️ **D2** Tools & MCP | 18% | O33 · O37 | ⚠️ Two specific rules |
| 📄 **D4** Prompting & Output | 20% | O23 · O26 · O29 | ⚠️ One decision tree fixes all three |
| 🧠 **D5** Context & Reliability | 15% | (O20 overlaps) | ✅ Your strongest domain |

> 💡 **The pattern in your misses:** you are strong at *architecture judgment* (decomposition, synthesis, routing, MCP design all 100%). You lose points on **concrete knobs**: *which file, which flag, which `tool_choice` value, which session action, which schema shape*. That's good news. Knobs are memorizable, and once memorized they are the fastest points on the exam.

## 0.3 Priority order and time budget (≈ 9 h total)

| # | Block | Weak spots | Read here | Lab | Time |
|---|---|---|---|---|---|
| 1 | 🔑 The one idea | all | Part 1 | — | 15 min |
| 2 | 💻 Which mechanism | **O16** 🟥 | W1 | `d3` E1–E8 | 90 min |
| 3 | 🍴 Forked skills | **O14** 🟥 | W2 | `d3` E5 | 30 min |
| 4 | 🗺️ Plan vs direct | **O8** 🟥 | W3 | `d3` E9 | 30 min |
| 5 | 🔁 Iterative refinement | **O12** 🟥 | W4 | `d3` E10 | 30 min |
| 6 | 🤖 CI review + flags + false positives | **O13** 🟥 · **O11** 🟧 · **O30** 🟧 | W5, W7, W8 | `d3` E11 | 75 min |
| 7 | 🧪 Test generation | **O15** 🟥 | W6 | `d3` E12 | 20 min |
| 8 | ⚡ Parallel tool calls | **O1** 🟥 | W11 | `d1/02` | 20 min |
| 9 | 🎛️ `tool_choice` ordering | **O37** 🟥 | W15 | `d2/03` | 25 min |
| 10 | 🔁 Sessions | **O2** 🟥 | W12 | `d1/06`, `d3` E13 | 30 min |
| 11 | 📄 Extraction + nullable | **O29** 🟥 · **O26** 🟧 | W17, W18 | `d4/02`, `03`, `04` | 60 min |
| 12 | 🧑‍🤝‍🧑 Subagent context + delegation + tools | **O3** · **O4** · **O33** 🟧 | W13, W14, W16 | `d1/05`, `d2/04`, `d3` E16 | 60 min |
| 13 | 🔍 Exploration + long context | **O17** · **O32** · **O20** 🟧 | W9, W10 | `d3` E14 | 30 min |
| 14 | 📦 Sync vs batch | **O23** 🟨 | W19 | `d4/05 --sla-only` | 15 min |
| 15 | 🧪 Drill + cram | all | Parts 7, 8, 10 | — | 60 min |

> ⏱️ **Method for every block:** read the W-section → open the 📖 links and read the named sections → run the 🔧 drill and **predict before you run** → answer the 🏁 self-check → log any miss as `W# | predicted | saw | rule`.

---

# Part 1 · 🔑 The one idea behind most of your misses

> 💡 **Words lower a failure rate. Mechanisms make a failure impossible.** Roughly half of your 0% objectives come down to picking a *sentence* where the stem demanded a *mechanism*, or the reverse.

```
   📝 WORDS (probabilistic)                       🔒 MECHANISMS (deterministic)
   ───────────────────────────                    ─────────────────────────────────────
   system-prompt instruction                       permission deny rule
   CLAUDE.md line ("NEVER edit migrations")        PreToolUse hook that exits 2
   few-shot examples                               code gate inside the tool
   tool description                                tool_choice forced / any
   "stop after 8 turns" in the prompt              --max-turns 8   /   --max-budget-usd 1
   "be conservative"                               JSON schema, nullable fields, enums
   "only use fetch_url for docs"                   tool not in the allowlist / --tools

   ✅ good for style, judgment, routing hints     ✅ required for money, identity, compliance,
                                                     safety, "must", "always", "never", "guarantee"
```

**How this shows up in your weak spots**

| Weak spot | The "words" distractor you might pick | The mechanism the exam wants |
|---|---|---|
| O16 🟥 | "Add NEVER edit migrations to CLAUDE.md" | `deny: ["Edit(db/migrations/**)"]` |
| O11 🟧 | "Tell Claude to stop after 8 turns" | `--max-turns 8` |
| O13 🟥 | "Ask the reviewer not to edit files" | `--tools "Read,Grep,Glob"` + `dontAsk` |
| O37 🟥 | "Instruct it to always call extract_metadata first" | `tool_choice` forced on turn 1, then `auto` |
| O33 🟧 | "Tell the synthesizer only to verify, not search" | Remove search; give a scoped `verify_fact` |
| O26 🟥 | "Tell it to write N/A when missing" | Nullable field in the schema |

**…and the opposite mistake: heavy machinery where a sentence is the right fix**

| Stem | 🪤 Heavy distractor | ✅ Proportionate fix |
|---|---|---|
| "First step" to fix tool misrouting | Train a routing classifier | Rewrite the tool **descriptions** |
| Review flags accepted patterns | Second "filter" model | **Explicit report / don't-report list** in project CLAUDE.md |
| Spec interpreted differently each run | Fine-tune | **2–3 input → output examples** |

> 🧠 **Read the stem for the deciding word.** *must / never / guarantee / money / compliance* → mechanism. *first step / least effort / most likely to help* → smallest change at the root cause.

📖 **Official reading**
- [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) (Anthropic Engineering): read *"When (and when not) to use agents"* and the closing principles. The "start simple, add complexity only when it demonstrably helps" stance is the source of the heavy-machinery trap.
- [Claude Code: Permissions](https://code.claude.com/docs/en/permissions) and [Hooks reference](https://code.claude.com/docs/en/hooks): the two enforcement mechanisms. Skim them now, read them properly in W1.

---

# Part 2 · 💻 D3 Claude Code Configuration & Workflows (20%) 🚨🚨

> 🚨 **11 of your 20 gaps live here.** D3 questions are rarely about theory. They ask: *which file? which scope? which flag? which mode?* Learn the map once and these become your most reliable points.

---

## W1 · 🟥 O16 · Choosing CLAUDE.md vs rules vs skills vs hooks vs permissions · you scored 0%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟥 0% | D3 | S2 Code Generation · S4 Dev Productivity · S5 CI | `d3` E1–E8 |

### 📘 Understand it first

> 📖 **Definition · Claude Code configuration mechanisms**
> The set of files and settings that shape what Claude Code *knows* (instructions loaded into the model's context) and what it is *allowed to do* (rules the Claude Code program enforces on every action), at either **project** scope (shared through the repo) or **user** scope (only on your machine).

**🧭 What it is, in plain words**

When you start `claude` in a folder, the program looks for configuration files before you type anything. Some of these files are **text that gets sent to the model**: `CLAUDE.md`, rule files, and (when invoked) skills. The model reads them like a briefing, and it *usually* follows them, the same way it follows any instruction.

Other files are **settings that the Claude Code program itself enforces**: permission rules and hooks. The model never gets a vote on these. When Claude asks to run a tool, the program checks the permission rules and runs any hooks *before* the tool executes. If a rule says no, the action simply doesn't happen.

That split is the heart of O16:

```
 ┌──────────────────────── 🧠 CONTEXT: things Claude READS ────────────────────────┐
 │  📘 CLAUDE.md          always loaded at session start                            │
 │  📐 .claude/rules/     loaded when Claude touches a file that matches `paths`    │
 │  🧰 skills / commands  loaded when the task is invoked (/name) or judged relevant │
 │  ➜ influences behavior · probabilistic · good for conventions and procedures     │
 └──────────────────────────────────────────────────────────────────────────────────┘
 ┌──────────────────────── 🔒 CONTROL: things Claude Code ENFORCES ────────────────┐
 │  ⛔ permissions        allow / ask / deny rules in settings.json                 │
 │  🪝 hooks              your scripts, run at events like PreToolUse / PostToolUse │
 │  ➜ decides what actually happens · deterministic · good for "must" and "never"   │
 └──────────────────────────────────────────────────────────────────────────────────┘
```

Every mechanism also has a **scope**, which answers *who gets it*:
- **Project scope** lives inside the repository (`./CLAUDE.md`, `.claude/…`, `.mcp.json`). It's committed to git, so every teammate who clones the repo gets it.
- **User scope** lives in your home folder (`~/.claude/…`, `~/.claude.json`). It follows *you* into every project, and nobody else ever sees it.
- **Local scope** (`.claude/settings.local.json`) is you, in this project only, not committed.

**⚙️ How one action flows through the layers**
```
 you type a request
      │
      ▼
 🧠 model reads: CLAUDE.md + matching rules + any invoked skill  →  decides "I'll run: rm -rf build"
      │
      ▼
 🪝 PreToolUse hooks run      ── exit 2? → ⛔ blocked, reason sent back to Claude
      │
      ▼
 ⛔ permission rules checked  ── deny? → refused · ask? → prompt you · allow? → silent
      │
      ▼
 🔧 tool executes
      │
      ▼
 🪝 PostToolUse hooks run     ── format, log, give feedback (can't undo)
```

**🏠 Analogy: a new employee at a company**
> 📘 **CLAUDE.md** is the employee handbook: read on day one, followed most of the time.
> 📐 **Rules** are department-specific pages: "if you're working on invoices, also read this".
> 🧰 **Skills** are recipe cards in a drawer: pulled out only when that job comes up.
> ⛔ **Deny rules** are locked doors: it doesn't matter what the handbook says, the door won't open.
> 🪝 **PreToolUse hook** is the security guard who checks each bag on the way in.
> 🪝 **PostToolUse hook** is the cleaning crew that tidies up after the work is done.

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **CLAUDE.md** | A Markdown file of instructions Claude Code loads into context at session start |
| **Memory** | Claude Code's name for CLAUDE.md-style instruction files (and auto memory) |
| **`@import`** | `@path/to/file.md` inside CLAUDE.md: pulls that file in alongside it |
| **Rule** | A Markdown file in `.claude/rules/`; with `paths:` frontmatter it loads only for matching files |
| **Glob** | A path pattern. `*` matches within one folder; `**` matches across any number of folders |
| **Skill** | A reusable, on-demand procedure in `SKILL.md`, invoked as `/name` or picked by Claude from its description |
| **Command** | The older form of a slash command: `.claude/commands/<name>.md` |
| **Frontmatter** | The `---` YAML block at the top of a file that configures it (`paths`, `description`, `context`…) |
| **Permission rule** | `allow` / `ask` / `deny` entry like `Edit(db/migrations/**)` in a settings file |
| **Hook** | A command Claude Code runs automatically at a lifecycle event, receiving the event as JSON on stdin |
| **Exit code** | The number a hook script returns. `0` = continue, `2` = block (PreToolUse), anything else = non-blocking error |
| **Scope** | Who a setting applies to: managed (org), user, project, local |

### 💡 The rule, in one picture
Claude Code has **six places to put guidance**, and each answers a different question:

```
 ❓ "Should Claude ALWAYS know this?"                 → 📘 CLAUDE.md
 ❓ "Only when touching certain FILES?"                → 📐 .claude/rules/*.md with paths:
 ❓ "Only when doing a certain TASK?"                  → 🧰 Skill (or command)
 ❓ "Must it be IMPOSSIBLE for a known path/command?"  → ⛔ Permission deny rule
 ❓ "Must CODE inspect the action before it runs?"     → 🪝 PreToolUse hook (exit 2)
 ❓ "Must something happen AFTER an action?"           → 🪝 PostToolUse hook
```

Then a second question: **who gets it?** → *project scope* (committed, whole team) or *user scope* (`~/.claude/`, only you).

### 🤔 Why you probably got it wrong
1. **Both scopes work on your machine**, so they *feel* the same. The difference only appears for a teammate.
2. **CLAUDE.md feels like enforcement** because it's always loaded. It isn't. It's an instruction Claude *usually* follows.
3. **Rules vs folder CLAUDE.md vs skill** all sound like "scoped instructions". They scope on different things: rules → *file paths*, folder CLAUDE.md → *one directory*, skill → *a task you invoke*.
4. **Hook vs deny** both block. Deny is for **static, known** targets. A hook is for **dynamic inspection** of the content.

### 📚 Deep explanation

#### 1️⃣ CLAUDE.md: always-on memory
- Loaded at **session start**, every session. It costs context every time, so keep it for *conventions that apply nearly always*.
- **Hierarchy** (all of them load and stack):

```
 🏢 Managed / org policy       (admin-deployed; rarely the exam answer)
 👤 ~/.claude/CLAUDE.md        you, every project, never committed
 👥 ./CLAUDE.md                team, committed to the repo
 📁 ./src/api/CLAUDE.md        loads when Claude works with files in src/api/
```

- **`@path` imports** pull another file into a CLAUDE.md (`@../../standards/api.md`). The imported file loads *with* its parent. Use it to keep CLAUDE.md modular or to share one standards document.
- ⚖️ "How do I verify which memory files loaded?" → **guide: `/memory`**. Docs today: `/context` shows what's loaded; `/memory` lists and opens the files.

#### 2️⃣ `.claude/rules/*.md`: conditional, path-scoped instructions
```markdown
---
paths:
  - "**/*.test.ts"
  - "**/*.test.tsx"
---
Tests: use React Testing Library. Query by role, never by test-id.
```
- Loads **only when Claude touches a file that matches** a glob.
- A rule **without** `paths` loads at session start like CLAUDE.md.
- `*` stays within one folder. **`**` crosses folders.** A wrong glob fails *silently*: no error, the rule just never loads.
- 🎯 This is THE answer for *"a convention for one file type spread across many folders"*. It beats one CLAUDE.md per folder (duplication, drift) and one giant root CLAUDE.md (always loaded, wastes context).

#### 3️⃣ Skills and commands: on-demand procedures
- `.claude/skills/<name>/SKILL.md` (team) or `~/.claude/skills/<name>/SKILL.md` (you). `.claude/commands/<name>.md` is the older command form.
- Only the **description** sits in context until the skill is used, so skills are cheap. The description is how Claude decides relevance: write it well.
- Use for repeatable **tasks**: `/pr-review`, `/release-notes`, `/map-module`.
- **Same name in several places:** personal skill > project skill > command (for that user).
- ⚖️ Guide: team commands live in **`.claude/commands/`**; a personal variant gets a **different name** so it doesn't shadow the team's. Docs today: commands are merged into skills, and a same-name personal skill also works.

#### 4️⃣ Permissions: allow / ask / deny
```
 request ─► DENY matches? ──yes──► ⛔ refused (nothing overrides it, from any file)
               │ no
               ▼
            ASK matches?  ──yes──► ❓ prompt
               │ no
               ▼
            ALLOW matches? ─yes──► ✅ runs silently
               │ no
               ▼
            permission mode default
```
- **Deny wins across all files.** An `allow` in `.claude/settings.local.json` can't punch a hole in a team `deny` in `.claude/settings.json`.
- `Edit(...)` deny rules cover every file-writing tool, Write included.
- Settings files: `~/.claude/settings.json` (you) · `.claude/settings.json` (team, committed) · `.claude/settings.local.json` (you in this project, not committed). `/permissions` shows each rule and its source file.

#### 5️⃣ Hooks: code that runs at lifecycle events
| Event | Runs | Can it stop the action? | Typical use |
|---|---|---|---|
| **PreToolUse** | Before the tool runs | ✅ **exit 2** blocks, stderr goes to Claude as the reason | "command contains `rm -rf`", "refund > 500" |
| **PostToolUse** | After the tool ran | ❌ too late; it can only give feedback | Auto-format, log edits, normalize output |
| Others | `SessionStart`, `UserPromptSubmit`, `Stop`, `InstructionsLoaded`, `PreCompact`… | depends | Setup, logging, gating |

- 🧨 **Only exit code 2 blocks.** Exit 1 is a *non-blocking error*: the action still runs.
- A hook returning `"permissionDecision": "allow"` **does not override a deny rule**.

#### 6️⃣ Subagents and MCP (for completeness)
- **Subagent** (`.claude/agents/<name>.md`): a helper role. Its `tools:` field restricts tools **in config**.
- **`.mcp.json`** (committed): a team's external systems, with secrets as `${VAR}`.

### 🧪 Worked example: the same team, six needs
| Need | ✅ Answer | 🪤 Tempting wrong answer |
|---|---|---|
| "All TypeScript must use our Result type" | Project `./CLAUDE.md` | `~/.claude/CLAUDE.md` (only you get it) |
| "Test files anywhere: use RTL, query by role" | `.claude/rules/tests.md` with `paths: ["**/*.test.tsx"]` | A CLAUDE.md in each of 30 test folders |
| "`/release-notes` that drafts notes from git log" | Skill in `.claude/skills/release-notes/` | Paste the procedure into CLAUDE.md (always loaded) |
| "Claude must never read `.env`" | `deny: ["Read(./.env)"]` | "NEVER read .env" in CLAUDE.md |
| "Block any Bash command containing `rm -rf`" | PreToolUse hook on `Bash`, exit 2 | PostToolUse (too late) · a deny rule can't inspect arbitrary command text robustly |
| "Run prettier after every edit" | PostToolUse hook on `Edit\|Write` | PreToolUse (file not written yet) |

### 🪤 Traps
- 🪤 "New hire's Claude ignores the convention" → the convention lives in someone's **user** scope. Move it to project CLAUDE.md and commit it.
- 🪤 `src/api/*.ts` to cover `src/api/v2/orders.ts`. ❌ Needs `src/api/**/*.ts`.
- 🪤 "Exit 1 from the hook blocks it." ❌ Only **2** blocks.
- 🪤 "Allow it in settings.local.json to override the team deny." ❌ Deny always wins.
- 🪤 Invented files: `.claude/config.json` ❌ (it's `.claude/settings.json`).

### 🎯 Exam pattern (recite this)
```
ALWAYS        → CLAUDE.md               team = ./CLAUDE.md · me = ~/.claude/CLAUDE.md
WHERE (files) → .claude/rules + paths + **      one folder → folder CLAUDE.md
WHEN ASKED    → skill / command         verbose → context: fork (W2)
NEVER (known) → permission deny
CHECK BEFORE  → PreToolUse hook, exit 2
AFTER         → PostToolUse hook
HELPER ROLE   → subagent with tools: in config
TEAM SYSTEM   → .mcp.json with ${TOKEN}
```

### 📖 Official reading (do this: ~45 min)
| Page | Read these sections | Look for |
|---|---|---|
| [Memory: CLAUDE.md](https://code.claude.com/docs/en/memory) | *Choose where to put CLAUDE.md files* · *Import additional files* · *How CLAUDE.md files load* · *Organize rules with `.claude/rules/`* | The load order, `@` imports, `paths:` frontmatter |
| [Explore the .claude directory](https://code.claude.com/docs/en/claude-directory) | Whole page (interactive) | Where every file lives, project vs `~/.claude` |
| [Skills](https://code.claude.com/docs/en/skills) | *Choose where skills load* · *Resolve skills that share a name* · *Frontmatter reference* | Personal vs project precedence, frontmatter fields |
| [Permissions](https://code.claude.com/docs/en/permissions) | *Permission system* · *Permission rule syntax* · *Read and Edit* · *Settings precedence* | Deny > ask > allow, rule syntax, which file wins |
| [Hooks reference](https://code.claude.com/docs/en/hooks) | *Hook lifecycle* · *Exit code output* · *PreToolUse* · *PostToolUse* | Exit 2 blocks; what stderr does |
| [Hooks guide](https://code.claude.com/docs/en/hooks-guide) | The examples | Format-after-edit, block-command patterns |
| [Settings](https://code.claude.com/docs/en/settings) | Settings files and scopes | user / project / local / managed |

### 🔧 Lab drill
`cd d3-claude-code/sandbox && claude`, then E1–E8 from `d3-claude-code/README.md`. Before each step, write your prediction. The key "aha" moments:
- **E3:** change `src/api/*.ts` → `src/api/**/*.ts` and watch `.claude/load.log` record `path_glob_match` for `v2/orders.ts`.
- **E7:** add `allow Read(./.env)` to `settings.local.json` → still refused.
- **E8:** move `block_rm.py` from PreToolUse to PostToolUse → `build/x` gets deleted, the hook only complains afterwards.

### 🧠 Memory line
**Always → CLAUDE.md · files → rules + `**` · task → skill · never → deny · check before → PreToolUse exit 2 · after → PostToolUse.**

### 🏁 Self-check
<details><summary>Q1. Your team wants every migration file to be read-only for Claude, with no exceptions. What do you configure?</summary>

**`"deny": ["Edit(db/migrations/**)"]` in the committed `.claude/settings.json`.** It's a known path and the requirement is absolute, so a deny rule is the lightest guarantee. CLAUDE.md text is only a request. A hook works too, but it's heavier than needed for a static path.
</details>

<details><summary>Q2. A hook script that blocks <code>git push --force</code> exits with code 1. What happens when Claude runs <code>git push --force</code>?</summary>

**It runs.** Exit 1 is a non-blocking error. Only **exit 2** blocks a PreToolUse call (and sends stderr to Claude as the reason).
</details>

<details><summary>Q3. Storybook conventions should apply to <code>*.stories.tsx</code> files in 40 folders. Best mechanism?</summary>

**One `.claude/rules/storybook.md` with `paths: ["**/*.stories.tsx"]`.** Path-scoped, loads only when relevant, one file to maintain.
</details>

---

## W2 · 🟥 O14 · `context: fork` · you scored 0%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟥 0% | D3 | S2 · S4 | `d3` E5 (`/map-module`, `/pr-review`) |

### 📘 Understand it first

> 📖 **Definition · `context: fork`**
> A skill frontmatter setting that runs the skill inside a **separate subagent with its own fresh context window**. The skill's text becomes the subagent's task, the subagent does the work in isolation, and only its **final message** comes back to your main conversation.

**🧭 What it is, in plain words**

First, two building blocks:
- A **context window** is everything the model can "see" right now: system prompt, CLAUDE.md, your messages, Claude's replies, and every tool result (every file it read). It has a size limit, and the more it fills with noise, the worse the model gets at finding what matters.
- A **skill**, by default, runs **inline**: its instructions are added to your current conversation, and everything it does (every file read, every long output) piles into *your* context window.

`context: fork` changes where the work happens. Instead of running inline, Claude Code starts a **subagent**: a separate model session with a blank context. That subagent receives the skill's instructions (with `$ARGUMENTS` filled in), does all the noisy reading and thinking in its own window, and returns a short result. Your main conversation only gains that result.

The catch is the flip side of the benefit: because the subagent starts blank, it **doesn't know anything you said earlier**. Isolation keeps the noise out, and it keeps your conversation out too.

**⚙️ How it works**
```
 MAIN CONVERSATION                                  FORKED SUBAGENT (fresh context)
 ─────────────────                                  ───────────────────────────────
 you: /map-module src/api ──── skill text + "src/api" ───►  receives ONLY:
                                                            · the SKILL.md body
                                                            · $ARGUMENTS = "src/api"
                                                            · (CLAUDE.md, unless agent is Explore/Plan ⚖️)
                                                            reads 20 files … 30k tokens of output
 ◄──────────────────────────── final summary (~500 tokens) ─┘
 main context grew by ~500 tokens, not 30k  🙂
```

**🏠 Analogy: sending an assistant to the archive room**
> You hand an assistant a written note: *"Go to the archive, read every file on Project Atlas, bring back a one-page summary."* They spend two hours among the boxes; you get one page. But the note is **all** they know. If the note says "the project we discussed", they have no idea which one you mean, because they weren't in the meeting.

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **Context window** | The model's working memory for a conversation; finite, measured in tokens |
| **Inline skill** | Default: the skill runs inside your current conversation and its output stays there |
| **Forked skill** | `context: fork`: the skill runs in an isolated subagent; only the result returns |
| **Subagent** | A separate model instance with its own context, started to do a delegated task |
| **`$ARGUMENTS`** | Placeholder in a skill replaced by whatever you typed after `/skill-name` |
| **`agent:`** | Optional frontmatter choosing which agent type runs the fork (for example `Explore`) |
| **`argument-hint`** | Frontmatter text describing expected arguments (⚖️ guide: prompts for missing ones) |
| **Self-contained** | The skill text alone holds everything the fork needs; nothing depends on the chat |

### 💡 The rule, in one picture
A skill with **`context: fork`** runs in an **isolated subagent context**. All its verbose work (reading 40 files, long tool output) happens *there*. Your main conversation receives only the **final result**.

```
 WITHOUT context: fork                         WITH context: fork
 ┌─────────── main context ───────────┐        ┌─────────── main context ───────────┐
 │ you: /map-module src/api           │        │ you: /map-module src/api           │
 │ 📄 users.ts (400 lines)            │        │        ┌──── 🍴 isolated fork ────┐ │
 │ 📄 orders.ts (600 lines)           │        │        │ reads all files          │ │
 │ 📄 ... 20 more files ...   😵       │        │        │ prints everything        │ │
 │ summary                            │        │        └──────────┬───────────────┘ │
 └────────────────────────────────────┘        │ ✉️ 15-line summary only      🙂      │
                                                └────────────────────────────────────┘
```

### 🤔 Why you probably got it wrong
- You may have thought the fork *shares* the conversation (it doesn't), or that `context: fork` is about **git** forks or **session** forks (`--fork-session`). Three different "forks":

| "Fork" | What it is | Where |
|---|---|---|
| 🍴 `context: fork` (skill frontmatter) | Skill runs in an isolated subagent context | D3 skills |
| 🌿 `--fork-session` / `fork_session=True` | New session ID branching from an existing session's history | D1 / D3 sessions (W12) |
| 🔀 git fork | Copy of a repository | Not on this exam |

### 📚 Deep explanation
**When to use it:** the skill is **verbose or exploratory** (mapping a module, auditing a folder, independent review), and you want the main context to stay clean.

**Trap 1 · The fork has amnesia.** It sees **only the skill's text plus `$ARGUMENTS`**, not your earlier messages.
```
 you:   The module I care about is src/api.
 you:   /map-module                    ← no argument
 fork:  "Which module?"                ← it never saw your earlier message
```
The lab's `map-module/SKILL.md` contains *"If no path was given, use the module the user mentioned earlier in the conversation."* That line works **without** fork and **breaks** with fork. 🎯 **A forked skill must be self-contained:** require the argument, or state everything it needs in the skill text.

**Trap 2 · Which agent runs the fork.** `agent: Explore` suits read-only discovery. Per today's docs, Explore and Plan forks **skip CLAUDE.md**. So a forked review that must apply the team's *Review standards* from CLAUDE.md uses the **default** agent. That's exactly the lab's `pr-review` skill:

```markdown
---
description: Independent code review of the files given, against the project's Review standards.
argument-hint: [files-or-dir]
context: fork
disallowed-tools: Edit Write
---
You are an independent reviewer. You did not write this code.
Review $ARGUMENTS against the "Review standards" section of CLAUDE.md. ...
```

**Bonus: why a fork is also a better *reviewer*.** The session that wrote the code carries its own reasoning and blind spots. A forked, isolated context reviews with fresh eyes (see W5, "independent reviewer").

> ⚖️ **Guide vs docs**
> - `argument-hint`: guide → **prompts for missing parameters**. Docs today → an autocomplete hint shown while typing. **Exam: the guide.**
> - Docs today: a forked skill also runs **in the background** by default in interactive sessions.

### 🪤 Traps
- 🪤 "Add `context: fork` so the skill can use what we discussed." ❌ The opposite: fork removes access to the discussion.
- 🪤 "Put the long exploration in CLAUDE.md." ❌ Always loaded, and it doesn't isolate output.
- 🪤 "Use `/compact` after every `/map-module`." Works, but loses detail. Fork is the design answer.
- 🪤 Forked review with `agent: Explore` that must apply CLAUDE.md standards. ⚖️ Per docs it won't see them.

### 🎯 Exam pattern
**"Skill floods the main context / verbose / exploratory / should not pollute the conversation"** → **`context: fork`**, and make the skill self-contained.

### 📖 Official reading (~20 min)
| Page | Section | Look for |
|---|---|---|
| [Skills](https://code.claude.com/docs/en/skills#run-skills-in-a-subagent) | *Run skills in a subagent* | `context: fork`, the `agent:` field, what the fork sees |
| [Skills](https://code.claude.com/docs/en/skills#frontmatter-reference) | *Frontmatter reference* · *Pass arguments to skills* | `argument-hint`, `$ARGUMENTS` |
| [Subagents](https://code.claude.com/docs/en/sub-agents#manage-subagent-context) | *Built-in subagents* · *Manage subagent context* | Explore / Plan agents, context isolation |

### 🔧 Lab drill (E5)
1. Run `/context`, note usage. Run `/map-module src/api`. Run `/context` again: it jumped.
2. `/clear`. Add `context: fork` to `map-module/SKILL.md`. Repeat: main context barely moves.
3. Say "the module I care about is src/api", then run `/map-module` with **no argument**. Watch the fork not know.

### 🧠 Memory line
**Verbose skill → `context: fork`. The fork sees only the skill text + `$ARGUMENTS`, so make it self-contained.**

### 🏁 Self-check
<details><summary>Q1. A forked <code>/audit-deps</code> skill keeps asking "which package.json?", even though you named it two messages earlier. Why, and what's the fix?</summary>

The fork **can't see the conversation**. Pass the path as an argument (`/audit-deps apps/web/package.json`) and make the skill require `$ARGUMENTS`, or name the file in the skill text.
</details>

<details><summary>Q2. Which is the better reviewer of a change: the session that wrote it, or a forked skill? Why?</summary>

The **forked skill** (an independent context). The authoring session keeps its own assumptions and blind spots.
</details>

---

## W3 · 🟥 O8 · Plan mode vs direct execution vs multi-phase · you scored 0%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟥 0% | D3 | S2 · S4 | `d3` E9 |

### 📘 Understand it first

> 📖 **Definition · Plan mode, direct execution, multi-phase**
> - **Direct execution:** Claude reads, edits and runs commands straight away to complete the request.
> - **Plan mode:** a *permission mode* in which Claude may read and investigate but **may not modify files**; it ends by presenting a plan that you approve (or revise) before any edits happen.
> - **Multi-phase execution:** a large change split into sequential phases, each with its own plan, execution and verification checkpoint.

**🧭 What it is, in plain words**

Every coding task has two costs: the cost of **thinking** about what to change, and the cost of **undoing** a wrong change. For a small, obvious fix, thinking is cheap and undoing is cheap, so you just do it. For a change that spreads across many files, or where there are several reasonable designs, a wrong start is expensive: you get half-converted code, inconsistent patterns, and rework.

Plan mode separates the two costs. Claude explores the code, works out an approach, and writes it down **while it's physically unable to edit**. You review the plan, which is cheap to change because it's just text, then approve it. Only then does Claude start editing. It's "measure twice, cut once", enforced by the permission system rather than by good intentions.

Multi-phase is plan mode applied repeatedly: for a migration of 120 endpoints, one plan for everything is too big to review. You plan and execute in slices, verifying each before moving on.

The **Explore subagent** solves a different problem: not "should I edit yet?" but "the investigation itself is huge". It does the reading in a separate context and reports back, so your main session isn't flooded.

**⚙️ How plan mode works**
```
 Shift+Tab (or --permission-mode plan)
      │
      ▼
 🔍 Claude reads, greps, explores      ✏️ edits are NOT allowed
      │
      ▼
 📝 Claude presents a plan: files to change, approach, risks
      │
      ├── ✏️ you ask for changes → revised plan
      ▼
 ✅ you approve → mode switches → Claude executes the plan → verify (tests)
```

**🏠 Analogy: home repairs**
> 🔧 **Direct:** a dripping tap. You know the fix; you just do it.
> 📐 **Plan mode:** knocking down a wall. You get an architect's drawing and sign it off *before* anyone picks up a hammer.
> 🪜 **Multi-phase:** renovating the whole house, room by room, with an inspection after each room.
> 🔍 **Explore subagent:** sending a surveyor to measure the house and hand you a report, instead of measuring every room yourself.

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **Permission mode** | A session-wide setting for what Claude may do without asking (`default`, `acceptEdits`, `plan`, `auto`, `dontAsk`, `bypassPermissions`) |
| **Plan mode** | Read-and-investigate only, until you approve a plan |
| **Direct execution** | Normal mode: Claude acts immediately |
| **Multi-phase** | Plan → execute → verify, repeated over slices of a large change |
| **Explore subagent** | Built-in read-only subagent for codebase investigation in a separate context |
| **Shift+Tab** | Keyboard shortcut that cycles permission modes in an interactive session |
| **Sign-off** | A human approval required before changes happen |

### 💡 The rule, in one picture
Pick the workflow from **task size and ambiguity**, not habit.

```
 Can you state the whole diff in ONE sentence, and the cause is clear?
 │
 ├── YES ─► ⚡ DIRECT EXECUTION  (just ask for the change)
 │
 └── NO ──► Multi-file? Architectural? Several valid approaches? Needs sign-off?
            │
            ├── YES ─► 🗺️ PLAN MODE: explore → propose plan → YOU approve → execute
            │            └─ very large? → 🪜 MULTI-PHASE: plan → phase 1 → verify → phase 2 …
            │
            └── Mostly "find out what's there" (verbose discovery)?
                         └─► 🔍 EXPLORE SUBAGENT first, then plan
```

### 🤔 Why you probably got it wrong
- "Plan mode is always safer" feels right, so you over-apply it. For a one-line fix with a stack trace, plan mode is **pure overhead**, and the exam marks it wrong.
- Or the opposite: direct execution for a cross-cutting refactor feels faster, but yields half-done edits and rework.
- Explore subagent vs plan mode: plan mode is about **getting approval before edits**. Explore is about **keeping verbose discovery out of your context**.

### 📚 Deep explanation
**Plan mode** (`claude --permission-mode plan`, or **Shift+Tab** to cycle into it): Claude can read and explore but **doesn't edit files** until you approve the plan. That's ideal when:
- The change touches **many files** (risk of inconsistent half-edits).
- It's **architectural** (introduces a shared client, changes an interface).
- There are **several valid approaches** you want to compare first (webhook vs bot token).
- Someone must **sign off** before code changes.

**Direct execution**: the task is small, well-specified, the cause is known (a stack trace points to the line).

**Multi-phase**: for big migrations, split into phases with **verification checkpoints** between them. It limits blast radius and keeps each phase reviewable.

**Explore subagent**: when the first job is *"find every X and summarize"*, delegate to Explore, so 40 file reads don't land in your main context.

> 💡 Anthropic's own best-practice sequence for non-trivial work: **explore → plan → code → commit**.

### 🧪 Worked example (E9's four tasks)
| Task | ✅ Mode | Why |
|---|---|---|
| "`orderTotal` returns NaN when qty is undefined; default qty to 1." | ⚡ Direct | One sentence, clear cause |
| "Replace every `fetch` in `src/api` with a shared `httpClient` with retries and typed errors." | 🗺️ Plan | Multi-file, architectural |
| "Add Slack notifications for failed orders." | 🗺️ Plan | Several valid approaches: compare first |
| "Find every fetch call and give me a 3-line summary." | 🔍 Explore subagent | Verbose discovery, keep the context small |
| "Migrate 120 endpoints from Express to Fastify." | 🪜 Plan + multi-phase | Too big for one approval; checkpoint per batch |

### 🪤 Traps
- 🪤 Plan mode for a typo or a one-line fix.
- 🪤 Direct execution for a refactor across 15 files.
- 🪤 "Read all 40 files in the main session first, then plan." → use Explore.
- 🪤 Invented: "`/plan` flag in CLAUDE.md". Plan mode is a **permission mode**.

### 🎯 Exam pattern
**One-sentence diff + clear cause → direct. Multi-file / architectural / options / sign-off → plan → approve → execute. Huge → phases. Verbose discovery → Explore.**

### 📖 Official reading (~20 min)
| Page | Section | Look for |
|---|---|---|
| [Common workflows](https://code.claude.com/docs/en/common-workflows#plan-before-editing) | *Plan before editing* · *Delegate research to subagents* | How plan mode works, when to use it |
| [Best practices](https://code.claude.com/docs/en/best-practices#explore-first-then-plan-then-code) | *Explore first, then plan, then code* · *Course-correct early and often* | The explore → plan → code sequence |
| [Permission modes](https://code.claude.com/docs/en/permission-modes) | Plan mode | Reads allowed, edits held until approval |

### 🔧 Lab drill (E9)
For each of the four tasks, **write your mode first**, then run it. In plan mode, notice that Claude explores and proposes but doesn't touch files until you approve.

### 🧠 Memory line
**Small and clear → direct. Big, cross-cutting, or debatable → plan first.**

### 🏁 Self-check
<details><summary>Q1. A stack trace points to <code>parseDate</code> line 42: it doesn't handle a null input. Best workflow?</summary>

**Direct execution.** One-sentence diff, known cause. Plan mode adds overhead with no benefit.
</details>

<details><summary>Q2. The lead wants to approve the approach before Claude restructures the auth layer across 12 files. Best workflow?</summary>

**Plan mode → lead approves → execute** (multi-phase if it's large). Sign-off + multi-file + architectural.
</details>

---

## W4 · 🟥 O12 · Iterative refinement · you scored 0%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟥 0% | D3 (draws on D4) | S2 | `d3` E10 |

### 📘 Understand it first

> 📖 **Definition · Iterative refinement**
> The loop of **prompt → output → evaluate → adjust** that you use to steer Claude from a first attempt to a correct result, choosing *how* to adjust based on *what kind* of problem the output shows.

**🧭 What it is, in plain words**

Claude rarely nails a non-trivial task on the first try, and neither do people. What separates fast progress from frustration is **how you give feedback**. The exam frames this as a set of techniques, each matched to a symptom:

- **Input/output examples.** Words like "clean", "normalized" or "sensible format" mean different things to different readers. A concrete before → after pair has only one meaning. When results *vary between runs*, the instruction is ambiguous; examples remove the ambiguity.
- **Tests first.** A test is an example that runs. If Claude can execute the tests, it can check its own work and keep fixing until they pass, without you eyeballing each attempt.
- **Specific failure feedback.** "Still broken" gives Claude nothing to work with. The failing test name, the expected value and the actual value point straight at the problem.
- **Grouping bugs correctly.** Bugs that *interact* (one fix changes the other's behavior) must be described together, or each fix undoes the last. Bugs that *don't* interact are best handled one at a time, so each change is small and easy to verify.
- **The interview pattern.** When *you* don't fully know the requirements, ask Claude to question you first. Its questions surface edge cases you hadn't considered.

**⚙️ How it works: pick the adjustment from the symptom**
```
 output not right
      │
      ├─ different every run? ────────────► add 2–3 input → output examples
      ├─ can correctness be checked? ─────► write/point to tests, "run them after each change"
      ├─ wrong in a specific way? ────────► paste the exact failure (test, expected, actual)
      ├─ several bugs?
      │     ├─ fixes affect each other ───► ONE message describing all of them + how they relate
      │     └─ unrelated ─────────────────► one at a time, verify each
      └─ requirements unclear to YOU? ────► "interview me before writing code"
```

**🏠 Analogy: at the barber**
> Saying *"a bit shorter, but not too short, kind of modern"* gets a different haircut from every barber. Showing **two photos** gets the same one every time. That's the power of examples over adjectives.

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **Input/output example** | A concrete pair: this input should produce exactly this output |
| **Few-shot** | Including a small number of examples in the prompt (⚖️ guide: 2–4; 2–3 I/O examples in TS 3.5) |
| **Test-driven iteration** | Giving Claude runnable tests as the definition of "done" |
| **Interacting bugs** | Bugs whose fixes change each other's behavior |
| **Independent bugs** | Bugs in unrelated code paths |
| **Interview pattern** | Asking Claude to question you about requirements before it implements |

### 💡 The rule, in one picture
When results aren't right, the fix depends on the **symptom**. Match the symptom to the technique:

| 🩺 Symptom | 💊 Technique |
|---|---|
| A prose spec is interpreted **differently each run** | **2–3 concrete input → output examples** |
| You need correctness you can **check** | **Tests first**: "make these tests pass; run them after each change" |
| Still wrong after a fix | **Iterate on the specific failure**: paste the failing test name + exact error |
| Two bugs that **interact** (fixing one changes the other) | **One detailed message** covering both |
| Several **independent** bugs | **One at a time**: fix, verify, next |
| **Unfamiliar domain**, fuzzy requirements | **Interview pattern**: "ask me questions before writing code" |

### 🤔 Why you probably got it wrong
- "Write a more detailed spec" *sounds* like the fix for inconsistency. But more prose = more interpretations. **Examples remove ambiguity**; prose adds it.
- "Fix bugs one at a time" sounds disciplined, but for **interacting** bugs it causes whack-a-mole: fixing A re-breaks B.
- "Give it all bugs at once" sounds efficient, but for **independent** bugs it makes a noisy diff that's hard to verify.

### 📚 Deep explanation
**1. Examples beat adjectives.** Instead of *"normalize the status and date in a sensible way"*:
```
Input:  {"st": "A", "since": "05/03/24"}
Output: {"status": "active", "since": "2024-03-05"}

Input:  {"st": "X", "since": ""}
Output: {"status": "closed", "since": null}
```
⚖️ Guide: **2–3** input/output examples here (TS 3.5), **2–4** targeted few-shot in general. Docs suggest 3–5. **Use the guide numbers.**

**2. Tests first = a verification loop.** Claude does much better when it can **check its own work**. "Make `py/test_status.py` pass. Run the tests after each change and fix only what fails." This turns a vague goal into a measurable one.

**3. Specific feedback.** ❌ "It's still broken." ✅ "`test_since_blank` fails: expected `None`, got `''`. Fix only that path."

**4. Interacting vs independent.**
```
 INTERACTING                               INDEPENDENT
 date parser ◄──► missing-key handler      header typo      button color
 (the parser's fallback depends on how     (unrelated code, unrelated tests)
  missing keys are treated)
 → ONE message describing both and         → one at a time, verify each
   how they relate
```

**5. Interview pattern.** For an unfamiliar domain: *"Before adding a cache to `getUser`, interview me about invalidation, TTL and failure modes. Don't write code until I've answered."* It surfaces requirements you didn't know you had.

### 🪤 Traps
- 🪤 "Rewrite the spec with more detail" when the stem says *"interpreted inconsistently"*.
- 🪤 "Fix them one at a time" when the stem says the bugs *affect each other*.
- 🪤 "Restart with a new session" as a first move for a wrong output.
- 🪤 "Lower the temperature" for inconsistent spec interpretation. Not a Claude Code knob, and it doesn't fix ambiguity.

### 🎯 Exam pattern
**Inconsistent → examples. Checkable → tests first. Wrong → specific failure. Interacting → together. Independent → apart. Unfamiliar → interview.**

### 📖 Official reading (~20 min)
| Page | Section | Look for |
|---|---|---|
| [Best practices](https://code.claude.com/docs/en/best-practices#give-claude-a-way-to-verify-its-work) | *Give Claude a way to verify its work* · *Provide specific context in your prompts* · *Let Claude interview you* · *Course-correct early and often* | Tests as verification, interview pattern |
| [Common workflows](https://code.claude.com/docs/en/common-workflows#work-with-tests) | *Fix bugs efficiently* · *Work with tests* | Test-driven loops |
| [Prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#use-examples-effectively) | *Use examples effectively* | Why examples beat descriptions |

### 🔧 Lab drill (E10)
Run the prose-only spec twice and compare the outputs. Then add 2 input/output examples and run again: the variation disappears. Then try the tests-first prompt on `py/test_status.py`.

### 🧠 Memory line
**Show, don't tell (examples). Prove it (tests). Be specific (exact failure). Group what interacts. Ask first when it's unfamiliar.**

### 🏁 Self-check
<details><summary>Q1. Claude fixes the timezone bug, which re-breaks the DST handling, and fixing DST re-breaks timezones. Best next prompt?</summary>

**One detailed message describing both bugs and how they interact**, ideally with the failing tests for both. They're interacting bugs, so one-at-a-time causes whack-a-mole.
</details>

<details><summary>Q2. "Format the address the way our CRM expects" gives a different shape each time. Most effective fix?</summary>

**2–3 concrete input → output examples** of the address transformation.
</details>

---

## W5 · 🟥 O13 · Review config: standards, restricted tools, structured output · you scored 0%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟥 0% | D3 (+ D4) | S5 CI | `d3` E11 (`ci/review.sh`, `ci/review-schema.json`, `/team-review`, `pr-review`) |

### 📘 Understand it first

> 📖 **Definition · Automated review configuration**
> The setup that lets Claude review code **without a human in the loop** (typically in CI on every pull request) so that it applies the team's standards consistently, cannot change the code it's reviewing, and returns findings in a machine-readable format a script can post.

**🧭 What it is, in plain words**

**CI (continuous integration)** is the automation that runs on every push or pull request: build, tests, linters. Adding Claude to CI means running Claude Code **headless** (`claude -p`, no interactive terminal) as one of those steps.

Interactive Claude has a human watching: you see what it reads, you approve edits, you read its prose answer. In CI there's nobody watching. So everything a human would normally supply must be **configured up front**:

1. **What counts as a finding?** Your judgment is replaced by written **review standards**. They go in the **project CLAUDE.md**, because every Claude Code run in the repo (CI *and* developers' own `/team-review`) loads it automatically.
2. **What is Claude allowed to touch?** Nobody is there to refuse an edit, so the reviewer must be **unable** to edit: only read-only tools exist (`--tools "Read,Grep,Glob"`), and `dontAsk` turns any would-be prompt into a refusal.
3. **What does the output look like?** A script, not a person, reads it. So the output must follow a **JSON schema** (`--json-schema`), which Claude Code validates and puts in `structured_output`.

Two practices make it trustworthy over time: re-reviews receive the **prior findings** (so fixed or already-reported issues aren't re-posted), and the reviewer is an **independent instance**, not the session that wrote the change.

**⚙️ How it works: the review job**
```
 PR opened / updated
      │
      ▼
 CI runner: claude -p "Review src/ against the Review standards in CLAUDE.md"
            --tools "Read,Grep,Glob" --permission-mode dontAsk          ← can't modify
            --output-format json --json-schema "$(cat review-schema.json)" ← fixed shape
            --max-turns 8 --max-budget-usd 1.00                          ← bounded
      │       │
      │       └─ auto-loads project CLAUDE.md → Review standards          ← consistent criteria
      ▼
 { "structured_output": { "findings": [ {file, line, severity, ...}, ... ] } }
      │
      ▼
 script posts PR comments · saves findings.json for the next push's re-review
```

**🏠 Analogy: a building inspector**
> The inspector works from the **official code book** (standards in CLAUDE.md), carries a **clipboard but no tools** (read-only), fills in a **standard form** (schema), on a re-visit checks **last visit's list** instead of starting over (prior findings), and is **never the builder** (independent reviewer).

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **CI** | Continuous integration: automated jobs on every push or PR |
| **Headless / print mode** | `claude -p`: runs one task non-interactively and prints the result |
| **Review standards** | Written report / don't-report criteria, accepted patterns and severity definitions |
| **Restricted tools** | Limiting which tools exist for the run (`--tools`, `--disallowedTools`) |
| **JSON schema** | A formal description of the required JSON shape (fields, types, enums) |
| **`structured_output`** | The field in the JSON envelope holding the schema-validated result |
| **Re-review** | A review on a later push, given the earlier findings |
| **Independent reviewer** | A fresh instance with no memory of writing the code |

### 💡 The rule, in one picture
A trustworthy automated review rests on **three pillars + two practices**:

```
 ┌────────────────────────┐  ┌────────────────────────┐  ┌────────────────────────┐
 │ 1️⃣ STANDARDS           │  │ 2️⃣ RESTRICTED TOOLS    │  │ 3️⃣ STRUCTURED OUTPUT   │
 │ in PROJECT CLAUDE.md   │  │ read-only:             │  │ --output-format json   │
 │ · report list          │  │ --tools "Read,Grep,    │  │ --json-schema          │
 │ · don't-report list    │  │          Glob"         │  │ file, line, severity,  │
 │ · accepted patterns    │  │ --permission-mode      │  │ category, issue, fix,  │
 │ · severity definitions │  │   dontAsk              │  │ detected_pattern       │
 └────────────────────────┘  └────────────────────────┘  └────────────────────────┘
   ➕ 4️⃣ re-runs receive the PRIOR FINDINGS → report only new or still-unaddressed
   ➕ 5️⃣ an INDEPENDENT reviewer instance, not the session that wrote the code
```

### 🤔 Why you probably got it wrong
- Each pillar has a "words" look-alike: *"tell it our standards in the prompt"* (only that run gets them), *"ask it not to edit"* (not enforced), *"ask for JSON"* (not validated).
- "Re-run the review on every push" sounds complete, but without prior findings you get **duplicate PR comments**.
- "Have Claude review its own change" sounds efficient, but it **shares the author's blind spots**.

### 📚 Deep explanation
**Pillar 1 · Standards in project CLAUDE.md.** CI runs load the project CLAUDE.md, so the standards apply on **every run**, interactive or headless, for everyone. The lab's version:
```markdown
## Review standards (used by /team-review and ci/review.sh)
Report: bugs that change behavior, missing error handling on network calls,
        security issues, broken API contracts.
Do not report: formatting, naming preferences, missing docstrings, TODO comments.
Accepted here, do not flag: `fetch(...).then(r => r.json())` in src/components (demo code).
Severity: blocker = wrong result or data loss; major = unhandled failure path;
          minor = everything else reportable.
```

**Pillar 2 · Restricted tools.** A reviewer must not modify code. Enforce it with **`--tools "Read,Grep,Glob"`** (only these built-ins exist) and **`--permission-mode dontAsk`** (anything that would prompt is denied). In a skill: `disallowed-tools: Edit Write`.

**Pillar 3 · Structured output.** `--output-format json` + `--json-schema '<schema>'` → the validated object arrives in **`structured_output`** in the JSON envelope. No regex parsing. The lab's schema requires per finding: `file`, `line`, `severity` (blocker/major/minor), `category` (bug/error_handling/security/api_contract/other), `issue`, `suggested_fix`, **`detected_pattern`** (what code construct triggered it, which makes false positives traceable, see W8).

**Practice 4 · Prior findings on re-review.** `bash ci/review.sh ci/out/findings.json` feeds the last run's findings back: *"Report only NEW or STILL-UNADDRESSED issues; skip anything already fixed."*

**Practice 5 · Independent reviewer.** `ci/independent_review.sh` reviews with a **fresh instance**, not the session that generated the change.

### 🧪 Worked example: the full job (`ci/review.sh`)
```bash
claude -p "Review the files under src/ against the Review standards in CLAUDE.md." \
  --output-format json \
  --json-schema "$(cat ci/review-schema.json)" \
  --max-turns 8 \
  --max-budget-usd 1.00 \
  --permission-mode dontAsk \
  --tools "Read,Grep,Glob"
# → parse .structured_output.findings[] → post PR comments
```

### 🪤 Traps
- 🪤 Standards pasted into the CI prompt only (interactive `/team-review` runs miss them). → project CLAUDE.md.
- 🪤 "Instruct the reviewer not to modify files." → `--tools` / `dontAsk`.
- 🪤 "Ask for JSON and parse it with a regex." → `--json-schema`.
- 🪤 Re-running without prior findings → duplicate comments.
- 🪤 The authoring session self-reviews → use an independent instance.
- 🪤 Invented flags: `CLAUDE_HEADLESS=1`, `--batch`, `--review-mode`. ❌

### 🎯 Exam pattern
**Standards → project CLAUDE.md · read-only → `--tools` + `dontAsk` · machine-readable → `--json-schema` · re-runs → prior findings · fresh reviewer.**

### 📖 Official reading (~30 min)
| Page | Section | Look for |
|---|---|---|
| [Headless / programmatic](https://code.claude.com/docs/en/headless#get-structured-output) | *Get structured output* · *Auto-approve tools* · *Turn off permission prompts in unattended runs* | `--json-schema` → `structured_output`; `dontAsk` |
| [CLI reference](https://code.claude.com/docs/en/cli-reference) | *CLI flags* table | `--tools`, `--disallowedTools`, `--permission-mode` |
| [GitHub Actions](https://code.claude.com/docs/en/github-actions) | Setup and configuration | How review jobs are wired in CI |
| [Best practices](https://code.claude.com/docs/en/best-practices#add-an-adversarial-review-step) | *Add an adversarial review step* · *Run non-interactive mode* | Independent review |

### 🔧 Lab drill (E11)
From `d3-claude-code/` in Git Bash: run `ci/review.sh`, inspect `ci/out/findings.json`, then run it again **with** the findings file and compare. Then run `ci/independent_review.sh`.
> ⚠️ **On your PC:** these scripts call `python3`, which is a Microsoft Store stub here. Switch them to `python` first (or ask Claude to).

### 🧠 Memory line
**Standards in CLAUDE.md · read-only tools · JSON schema · prior findings · independent reviewer.**

### 🏁 Self-check
<details><summary>Q1. Every push to a PR re-posts the same 6 review comments. Fix?</summary>

Pass the **prior findings** into the re-run and instruct it to report **only new or still-unaddressed** issues.
</details>

<details><summary>Q2. The CI reviewer sometimes "helpfully" fixes code. How do you make that impossible?</summary>

**`--tools "Read,Grep,Glob"`** (Edit/Write don't exist), plus `--permission-mode dontAsk`. A prompt instruction isn't a guarantee.
</details>

---

## W6 · 🟥 O15 · Test generation quality · you scored 0%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟥 0% | D3 | S5 · S2 | `d3` E12 (`ci/testgen.sh`) |

### 📘 Understand it first

> 📖 **Definition · Test generation quality**
> How useful AI-generated tests are: whether they check **real behavior**, cover **edge cases** the existing suite misses, **avoid duplicating** existing tests, and follow the project's **fixture and style conventions**.

**🧭 What it is, in plain words**

A test suite is valuable for what it catches that nothing else does. A generated test that repeats an existing scenario adds maintenance cost and zero protection. A test that asserts on private internals breaks on every refactor and catches nothing about behavior.

Claude can only avoid duplicates **it can see**. If you ask "write tests for `cart.py`" without showing the current test file, it will reasonably start with the obvious cases, which are exactly the ones already written. And if it doesn't know the project's fixture convention, it may invent a helper module that doesn't exist.

So the quality levers are information levers: show the **existing tests** in the request, and keep the **testing standards** (what makes a test valuable, which edge cases matter, how fixtures are built) in project CLAUDE.md, so every request, interactive or CI, gets them automatically.

**⚙️ How it works**
```
 request: "add tests for cart.py"
      │
      ├── + existing test file ("don't duplicate these")      → skips what's covered
      ├── + CLAUDE.md test standards (auto-loaded)             → behavior-level, edge cases,
      │                                                          inline-dict fixtures
      ▼
 new tests that add coverage instead of repeating it
```

**🏠 Analogy**
> Asking someone to "add questions to the exam" without showing them the existing exam: you'll get the same easy questions you already have.

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **Behavior test** | Checks what a public function does for given inputs |
| **Implementation test** | Checks internal details; brittle, low value |
| **Edge case** | Unusual or boundary input: missing key, empty list, negative quantity |
| **Fixture** | The setup data a test uses |
| **Test standards** | The project's written rules for valuable tests, kept in CLAUDE.md |

### 💡 The rule, in one picture
Two rules fix almost every test-generation question:
1. 📋 **Show it the existing tests** and say *"do not duplicate these scenarios"*.
2. 📘 **Put testing standards in project CLAUDE.md**: what makes a test valuable, edge cases to cover, fixture conventions. Every run (CI included) then gets them.

### 🤔 Why you probably got it wrong
- "Ask for *novel* or *more diverse* tests" sounds right, but Claude can't avoid duplicating what it **hasn't seen**.
- "Increase the number of tests requested" adds quantity, not value.
- Fixture invention: without a stated convention, Claude may invent a `factories.py` that doesn't exist.

### 📚 Deep explanation
**What `ci/testgen.sh` shows:**
```
 Prompt A: "Suggest 8 unit test cases for cart.py"
   → repeats add-item, remove-item, empty-total (already tested)        😕

 Prompt B: "Existing tests (do not duplicate these): <test file>
            Testing standards: test behavior via public functions;
            cover edge cases: missing price, negative qty, ..."
   → skips the existing ones, targets the edge cases                    🙂
```

**The lab's standards block** (`sandbox/CLAUDE.md`):
```markdown
## Test generation standards
- Test behavior through the public function, not implementation details.
- Do not duplicate scenarios already in the existing test file.
- Cover edge cases: missing keys, empty values, invalid input.
- Fixture: use plain dicts built inline; there is no factory module.
```
- `--tools ""` (used in `testgen.sh`) disables **all** built-in tools, so Claude sees only what you paste. Useful for a deterministic, cheap CI step.
- **Behavior over implementation:** tests that assert on private helpers break on every refactor and catch nothing.

### 🪤 Traps
- 🪤 "Write tests for cart.py." (no existing tests, no standards)
- 🪤 "Generate 30 tests instead of 8."
- 🪤 "Tell it to be creative."
- 🪤 Standards only in the CI prompt (developers' interactive runs miss them).

### 🎯 Exam pattern
**Duplicated / low-value tests → existing tests in the prompt + test standards in project CLAUDE.md.**

### 📖 Official reading (~10 min)
| Page | Section | Look for |
|---|---|---|
| [Common workflows](https://code.claude.com/docs/en/common-workflows#work-with-tests) | *Work with tests* | Asking for edge cases, following existing patterns |
| [Best practices](https://code.claude.com/docs/en/best-practices#write-an-effective-claude-md) | *Write an effective CLAUDE.md* | What belongs in CLAUDE.md (testing conventions do) |

### 🔧 Lab drill (E12)
Run `ci/testgen.sh` and compare the two lists. Count how many cases in A duplicate the existing tests.

### 🧠 Memory line
**It can't avoid what it can't see: give it the existing tests + standards in CLAUDE.md.**

### 🏁 Self-check
<details><summary>Q1. Generated tests import <code>tests/factories.py</code>, which doesn't exist. Best prevention?</summary>

State the **fixture convention** in the project CLAUDE.md test standards ("plain dicts built inline; there is no factory module").
</details>

---

## W7 · 🟧 O11 · CI flags, permission modes, cost and turn limits · you scored 50%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟧 50% | D3 | S5 CI | `d3` E11 (`ci/flags_demo.sh`) |

### 📘 Understand it first

> 📖 **Definition · CI flags, permission modes and limits**
> Command-line options that configure a **non-interactive** Claude Code run: how it's invoked (`-p`), what format it returns, which tools **exist**, which tools are **pre-approved**, what happens when a permission prompt *would* appear, and hard caps on **turns** and **spend**.

**🧭 What it is, in plain words**

In an interactive session, three things happen through you: you **approve** actions when prompted, you **notice** when Claude is going in circles and stop it, and you **read** the answer. In a CI pipeline, none of that can happen, so each one becomes a flag.

The most tested idea is that tool control has **two independent axes**:
- **Availability:** does the tool *exist* in this run? `--tools` (allow-list of built-ins) and `--disallowedTools` (remove tools, or deny specific patterns) control this.
- **Approval:** if the tool exists, can it run *without asking*? `--allowedTools` pre-approves tools. `--permission-mode` sets the baseline.

In CI there's nobody to answer a prompt, so `--permission-mode dontAsk` says: *anything that would have needed a prompt is denied*. Combine it with `--allowedTools` to pre-approve exactly what the job needs.

**Limits** are a safety net against runaway runs: `--max-turns` stops after N agentic turns and exits with an error; `--max-budget-usd` stops when the estimated spend reaches the cap (it can overshoot slightly).

**⚙️ How it works: the two axes**
```
                         APPROVAL →
                         needs a prompt                  pre-approved (--allowedTools)
 AVAILABILITY ↓     ┌─────────────────────────────┬──────────────────────────────┐
 tool exists        │ interactive: you're asked   │ runs silently ✅              │
                    │ dontAsk (CI): DENIED ⛔      │                              │
                    ├─────────────────────────────┴──────────────────────────────┤
 tool removed       │ can't be called at all 🚫 (--tools without it,              │
 (--tools /         │  or --disallowedTools "Edit")                               │
  --disallowedTools)│                                                             │
                    └─────────────────────────────────────────────────────────────┘
```

**🏠 Analogy: a hotel key card**
> `--tools` decides **which rooms exist on your floor**. `--allowedTools` decides **which doors your card opens without calling reception**. `dontAsk` means **reception is closed**: if your card doesn't open it, you don't get in.

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **`-p` / `--print`** | Run one task non-interactively, print the result, exit |
| **Agentic turn** | One model response in the loop (often: request tools → get results) |
| **Envelope** | The JSON object `--output-format json` returns (`result`, `session_id`, `total_cost_usd`, …) |
| **Pre-approve** | Let a tool run without a permission prompt (`--allowedTools`) |
| **Restrict** | Make a tool unavailable (`--tools`, `--disallowedTools`) |
| **`dontAsk`** | Mode where anything not pre-approved that would prompt is denied |
| **`--bare`** | Minimal run that skips CLAUDE.md, hooks, skills, MCP and auto memory |

### 💡 The rule, in one picture
In CI, **caps and restrictions are flags**, never prompt text. And there are two families of tool flags that sound alike but do opposite things:

```
 ✅ APPROVE  (the tool exists, and runs without a prompt)   --allowedTools "Edit"
 🚫 RESTRICT (what exists at all)                            --tools "Read,Grep,Glob"
                                                             --disallowedTools "Edit"
```

### 🤔 Why you probably got it wrong (the 50% half)
You likely know `-p` and `--output-format json`. The missed half is usually:
- thinking `--allowedTools` **restricts** (it **pre-approves**);
- putting limits in the prompt instead of `--max-turns` / `--max-budget-usd`;
- not knowing `dontAsk`: in a headless run nobody can answer a prompt, so `dontAsk` **denies** anything that would have prompted.

### 📚 Deep explanation: the flag table
| Flag | What it does | Group |
|---|---|---|
| `-p` / `--print` | Non-interactive (headless) run | 🤖 Required for CI |
| `--output-format json` | JSON envelope: `result`, `session_id`, `total_cost_usd`, `num_turns`, `subtype` | 📦 Parse |
| `--json-schema '<schema>'` | Validated object in **`structured_output`** (print mode only) | 📦 Guaranteed shape |
| `--max-turns N` | Caps agentic turns. **Exits with an error** when hit. No limit by default. | 🔒 Cap |
| `--max-budget-usd X` | Stops once estimated spend reaches X. **Can pass the cap slightly**, so leave headroom. Subagent spend counts. | 🔒 Cap |
| `--permission-mode dontAsk` | Anything that would prompt is **denied** | 🔒 Lock down |
| `--allowedTools "Edit"` | **Pre-approves**: runs without prompting | ✅ Approve |
| `--tools "Read,Grep,Glob"` | **Only these built-in tools exist**. `""` = none. | 🚫 Restrict |
| `--disallowedTools "Edit"` | Bare name **removes** the tool. A scoped rule like `Bash(rm *)` denies only matching calls. | 🚫 Restrict |
| `--bare` | Skips CLAUDE.md, hooks, skills, MCP, auto memory. Needs `ANTHROPIC_API_KEY`. | ⚡ Minimal |
| `--append-system-prompt-file F` | Adds a file to the system prompt | 📎 Pass instructions in |
| `-r ID` / `--resume`, `--fork-session` | Resume / branch a session | 🔁 Sessions (W12) |
| `-p "/team-review src/api"` | Runs a command or skill headless | ♻️ Reuse team commands |

**Permission modes** (`--permission-mode <mode>`, or **Shift+Tab** in a session):
| Mode | Runs without asking (per docs) | Best for |
|---|---|---|
| `default` (UI: "Manual") | Reads only | Reviewing every action |
| `acceptEdits` | Reads, file edits, common filesystem commands | Iterating on code you review |
| `plan` | Reads; edits wait for plan approval (W3) | Exploring before changing |
| `auto` | Everything, with background safety checks | Long tasks, fewer prompts |
| `dontAsk` | Reads in working dirs + **pre-approved** tools; anything that would prompt is **denied** | 🔒 Locked-down CI and scripts |
| `bypassPermissions` | Everything | Isolated containers/VMs only |

> 🧨 **Deny rules block in every mode, even `bypassPermissions`.** Modes set the baseline; permission rules layer on top.

**Combos the exam likes**
| Need | Flags |
|---|---|
| No prompts, but edits must work | `--permission-mode dontAsk --allowedTools "Edit"` |
| Reviewer that physically can't edit | `--tools "Read,Grep,Glob"` |
| Bounded cost and length | `--max-turns 8 --max-budget-usd 1.00` |
| Fast, no project config | `--bare` (+ `--append-system-prompt-file` to pass instructions back) |

> ⚖️ The guide names `-p`, `--output-format json` and `--json-schema`. The lab's docs check found `--max-turns`, `--max-budget-usd`, `--permission-mode dontAsk`, `--tools`, `--disallowedTools` and `--bare` are **also real and tested**.

### 🪤 Traps
- 🪤 "Stop after 8 turns" in the prompt. → `--max-turns 8`.
- 🪤 `--allowedTools "Read"` to make the reviewer read-only. ❌ That only pre-approves Read; Edit still exists. → `--tools`.
- 🪤 `CLAUDE_HEADLESS=1`, `--batch`, `--non-interactive`. ❌ Invented.
- 🪤 `bypassPermissions` in CI "so it doesn't hang". ❌ Unsafe; `dontAsk` is the lockdown.

### 🎯 Exam pattern
**Caps → flags. Approve → `--allowedTools`. Restrict → `--tools` / `--disallowedTools`. No prompts in CI → `dontAsk`.**

### 📖 Official reading (~25 min)
| Page | Section | Look for |
|---|---|---|
| [CLI reference](https://code.claude.com/docs/en/cli-reference) | *CLI flags* (search the table for each flag above) | The exact wording of `--allowedTools` vs `--tools` |
| [Headless](https://code.claude.com/docs/en/headless) | *Basic usage* · *Start faster with bare mode* · *Auto-approve tools* · *Turn off permission prompts in unattended runs* | `--bare`, `dontAsk` |
| [Permission modes](https://code.claude.com/docs/en/permission-modes) | The modes list | What each mode does |
| [Costs](https://code.claude.com/docs/en/costs) | Whole page | Budget behavior |

### 🔧 Lab drill (E11 · `ci/flags_demo.sh`)
Predict each step's result before running: step 3 (`--max-turns 1` → non-zero exit), step 5 (`dontAsk` → edit denied), step 6 (`dontAsk + --allowedTools Edit` → allowed), step 7 (`--tools` → Edit doesn't exist).

### 🧠 Memory line
**`allowedTools` = ✅ yes without asking. `tools` / `disallowedTools` = 🚫 what exists. Caps are flags.**

### 🏁 Self-check
<details><summary>Q1. A CI job must not prompt, must be able to edit files, and must not run Bash. Flags?</summary>

`--permission-mode dontAsk --allowedTools "Edit" --disallowedTools "Bash"` (or `--tools "Read,Edit,Grep,Glob"`).
</details>

<details><summary>Q2. What does <code>--max-turns 3</code> do when the task needs 6 turns?</summary>

The run stops at 3 and **exits with an error** (non-zero), so the pipeline can detect it.
</details>

---

## W8 · 🟧 O30 · Reducing false positives via persistent conventions · you scored 50%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟧 50% | D4 (applied in D3) | S5 CI | `d4/01`, `d3` E11 |

### 📘 Understand it first

> 📖 **Definition · False positives and persistent conventions**
> A **false positive** is a reported finding that isn't a real problem. **Persistent conventions** are review criteria stored where *every* run loads them (the project CLAUDE.md), rather than typed into one prompt.

**🧭 What it is, in plain words**

Every reviewer, human or AI, trades off two errors:

```
                          really a problem?
                          YES                     NO
 reported?   YES   ✅ true positive        ❌ FALSE POSITIVE  ← noise, erodes trust
             NO    ❌ false negative       ✅ true negative
                   (missed bug)
```
**Precision** = of everything reported, how much was real. Low precision is deadly for an automated reviewer: after a few weeks of noise, developers stop reading its comments, and then even its true positives are ignored.

Why do false positives happen? Mostly because the reviewer **doesn't know your team's decisions**: that `console.log` is fine in scripts, that demo code is intentionally simple, that naming is not a review topic. Telling it to "be conservative" doesn't supply that knowledge; it just makes it vaguely quieter. What fixes precision is **explicit knowledge**: what to report, what not to report, which patterns are accepted here, and what each severity means, with examples at the boundary.

And because the problem recurs on every run, the knowledge must live somewhere **every run reads**: the project CLAUDE.md.

**🏠 Analogy: a smoke detector**
> A detector that goes off every time you make toast gets its battery removed, and then it can't warn you about a real fire. You don't fix it by asking it to "be less sensitive" in general; you tell it **toast is not fire** (accepted pattern) and you mount it **away from the kitchen** (scope).

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **False positive** | A reported issue that isn't real |
| **Precision** | Share of reported findings that are real |
| **Recall** | Share of real problems that get reported |
| **Accepted pattern** | A construct the team has decided is fine here; "do not flag" |
| **Severity definition** | What blocker / major / minor mean, with examples |
| **`detected_pattern`** | Schema field naming the construct that triggered a finding, for traceability |

### 💡 The rule, in one picture
**Precision comes from explicit criteria, not from caution words.** And conventions that should apply to *every* review belong in a **persistent** place: the project CLAUDE.md.

```
 ❌ "Be conservative."                    ✅ Report:     bugs, unhandled network errors, security, API contracts
 ❌ "Only report if 90% confident."       ✅ Don't report: formatting, naming, docstrings, TODOs
 ❌ "Avoid nitpicks."                     ✅ Accepted here: fetch(...).then(r => r.json()) in src/components
                                          ✅ Severity: blocker = data loss / wrong result; major = unhandled failure...
                                          ✅ + few-shot pair: one acceptable pattern vs one look-alike real issue
```

### 🤔 Why you probably got it wrong (the 50% half)
- Confidence thresholds *sound* scientific. In the lab (`d4/01` exercise 4), "only report findings you're 90% sure about" barely moves false positives. The model's self-reported confidence isn't calibrated.
- Putting the accepted-pattern list in **one** prompt fixes that run only. The next run (or a teammate's `/team-review`) flags it again.

### 📚 Deep explanation
1. **Explicit report / don't-report categories** turn a judgment call into a lookup.
2. **Accepted patterns** ("do not flag X here, because Y") remove repeat false positives at the source.
3. **Severity definitions with examples** stop "everything is major".
4. **Few-shot pairs:** an acceptable pattern next to a genuinely buggy one that *looks* similar teach the boundary.
5. **`detected_pattern` in the output schema** shows *what* triggered each finding, so you can trace and fix noisy rules.
6. **A noisy category is destroying trust?** **Temporarily disable that category**, fix its criteria, then turn it back on. Developers stop reading reviews that cry wolf.
7. **Where:** in **project CLAUDE.md**, so every run (CI, `/team-review`, anyone's session) gets the same conventions.

### 🪤 Traps
- 🪤 "Add 'be conservative'." · 🪤 "Raise the confidence threshold." · 🪤 "Add a second model to filter findings" (heavy machinery). · 🪤 "Put it in your `~/.claude/CLAUDE.md`" (only you).

### 🎯 Exam pattern
**False positives → explicit report/skip lists + accepted patterns + severity examples, in project CLAUDE.md. Noisy category → disable temporarily, fix criteria.**

### 📖 Official reading (~15 min)
| Page | Section | Look for |
|---|---|---|
| [Prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#be-clear-and-direct) | *Be clear and direct* · *Add context to improve performance* · *Use examples effectively* | Explicit criteria, "why" behind rules |
| [Increase output consistency](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/increase-consistency) | Whole page | Specifying output precisely, examples |
| [Memory](https://code.claude.com/docs/en/memory) | *Write effective instructions* | Specific, verifiable instructions in CLAUDE.md |

### 🔧 Lab drill
`python d4-prompting/01_explicit_criteria_fewshot.py`: compare vague vs explicit vs explicit + few-shot. Then do exercise 4 (the 90% confidence prompt).

### 🧠 Memory line
**Lists, not adjectives. Persist them in project CLAUDE.md.**

### 🏁 Self-check
<details><summary>Q1. The review bot keeps flagging the team's intentional <code>any</code> casts in generated GraphQL types. First fix?</summary>

Add an **accepted-pattern entry** in project CLAUDE.md's review standards: "Accepted: `any` in `src/generated/**` (generated code), do not flag."
</details>

---

## W9 · 🟧 O17 (40%) + O32 (50%) · Systematic exploration and picking the right built-in tool

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟧 40% / 50% | D2 · D3 | S4 Dev Productivity · S2 | `d3` E14 |

### 📘 Understand it first

> 📖 **Definition · Built-in tools and systematic exploration**
> Claude Code's **built-in tools** are the actions it can take on your machine: search file contents (**Grep**), find files by name (**Glob**), read (**Read**), change part of a file (**Edit**), create or overwrite a file (**Write**), run shell commands (**Bash**). **Systematic exploration** is using them in a *narrow-then-read* order so the context fills only with what's relevant.

**🧭 What it is, in plain words**

Every file Claude reads costs context. In a 900-file repo, "read everything" is impossible and, even when possible, buries the relevant 20 lines under 50,000 irrelevant ones. So good exploration works like a detective: **search first, read second**.
- **Grep** answers *"where does this text appear?"*: it looks **inside** files. Use it for function names, error strings, config keys.
- **Glob** answers *"which files have names like this?"*: it matches **paths**. Use it for `**/*.test.ts`, `src/**/routes/*.py`.
- **Read** opens a specific file, ideally only the ones the searches pointed at.

**Edit** deserves its own note. It works by **exact string replacement**: you give an `old_string` (the anchor) and a `new_string`. If the anchor appears more than once, Edit can't know which one you mean, so it refuses. The fixes: include more surrounding text so the anchor is unique, or read the file and write the whole corrected version back.

**⚙️ How it works: narrow, then read, then follow**
```
 "How does refundOrder work?"
      │
      ▼
 🔎 Grep "refundOrder"           → 3 files, 7 lines
      ▼
 📖 Read those 3 files            → refundOrder calls validateRefund + paymentsClient.refund
      ▼
 🔎 Grep "validateRefund"         → 1 file            (follow the call chain)
      ▼
 📝 note: "refundOrder → validateRefund (src/refunds/validate.ts:41) → paymentsClient.refund (src/clients/payments.ts:88)"
```

**🏠 Analogy: a library**
> **Glob** is the catalog by title ("all books with *Python* in the title"). **Grep** is the full-text index ("every page that mentions *decorators*"). **Read** is taking the book off the shelf. You don't read the whole library to find one paragraph.

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **Grep** | Search file **contents** for a pattern (regex) |
| **Glob** | Match file **paths/names** against a pattern |
| **Read** | Load a file's content into context |
| **Edit** | Replace an exact, unique `old_string` with `new_string` |
| **Write** | Create a file or overwrite it entirely |
| **Anchor** | The `old_string` Edit searches for; must be unique in the file |
| **Call chain** | The sequence of functions a request passes through |

### 💡 The rule, in one picture
**Narrow first, then read.** And each built-in tool has one job:

| Job | Tool | Example |
|---|---|---|
| 🔎 Find **text inside** files | **Grep** | "Where is `getOrder` called?" |
| 🗂️ Find files by **name pattern** | **Glob** | "Every `*.test.tsx`" |
| 📖 Read a file | **Read** | Only the hits Grep/Glob found |
| ✏️ Change one spot | **Edit** | Needs an anchor that's **unique** in the file |
| 📝 Create or fully replace a file | **Write** | New files; the Edit fallback |
| ⚙️ Run commands or tests | **Bash** | `python -m unittest` |

### 🤔 Why you probably got it wrong
- Grep vs Glob: *names* vs *contents*. They're easy to swap under time pressure. **Glob = file names (g-l-o-b → "global file list"). Grep = inside the text.**
- "Read every file to be thorough" sounds diligent. It floods the context and is the wrong answer.
- Edit failures: retrying the same non-unique Edit, or switching to `sed` via Bash, instead of the guide's fallback.

### 📚 Deep explanation
**Systematic exploration (O17)**
```
 1️⃣ Grep / Glob   → which files and lines matter?          (cheap, precise)
 2️⃣ Read          → only those hits                        (not the whole repo)
 3️⃣ Follow        → Grep the next symbol in the call chain  (getOrder → fetchOrder → db.query)
 4️⃣ Record        → append confirmed facts with file:line to a notes file (W10)
 5️⃣ Too big?      → hand verbose discovery to an Explore subagent
```

**The Edit fallback (O32)**
```
 Edit("retries = 3" → "retries = 5")
        ▼
 ❌ "found 2 matches": the anchor isn't unique
        ├─► ✅ use a LONGER anchor that appears once (include the surrounding line)
        └─► ✅ guide's fallback: READ the file, then WRITE it back with the change
```

- ❌ Don't use Bash `cat` / `grep` / `find` when the built-in exists: the built-ins are permission-aware and context-efficient.

> ⚖️ **Docs today:** on macOS, Linux and WSL the default tool set leaves out `Grep` and `Glob` (search goes through Bash) unless they're named in `--tools` / `--allowedTools`. **Exam: they're standard built-ins. Answer Grep / Glob.**

### 🪤 Traps
- 🪤 Glob for "where is this function called" (that's content → Grep).
- 🪤 Grep for "all files ending in .spec.ts" (that's names → Glob).
- 🪤 "Read the entire `src/` folder first."
- 🪤 Retry the identical failing Edit.

### 🎯 Exam pattern
**Content → Grep. Names → Glob. Read only the hits. Non-unique Edit → longer anchor, or Read + Write.**

### 📖 Official reading (~15 min)
| Page | Section | Look for |
|---|---|---|
| [Tools reference](https://code.claude.com/docs/en/tools-reference) | Grep, Glob, Read, Edit, Write entries; *Glob tool behavior* | Each tool's job, Edit's uniqueness requirement |
| [Common workflows](https://code.claude.com/docs/en/common-workflows#understand-new-codebases) | *Understand new codebases* | Broad → narrow exploration |
| [Best practices](https://code.claude.com/docs/en/best-practices#use-subagents-for-investigation) | *Ask codebase questions* · *Use subagents for investigation* | Delegating verbose exploration |

### 🔧 Lab drill (E14)
Ask Claude to trace `getUser` and `getOrder`. Watch which tools it picks. Then make an Edit with a non-unique anchor and see the error and the fallback.

### 🧠 Memory line
**Grep = guts (content). Glob = global names. Then Read only the hits.**

### 🏁 Self-check
<details><summary>Q1. "Find every place the <code>X-Request-Id</code> header is set." Which tool first?</summary>

**Grep** for `X-Request-Id` (content search), then Read the hits.
</details>

<details><summary>Q2. Edit fails: <code>timeout: 30</code> appears 3 times in the config. Best next step?</summary>

Edit with a **longer, unique anchor** (include the surrounding key or line). If that's impractical: **Read the file, then Write** the whole corrected file.
</details>

---

## W10 · 🟧 O20 · Managing context across long exploration · you scored 50%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟧 50% | D5 (applied in D3) | S4 · S3 | `d3` E14, E16 |

### 📘 Understand it first

> 📖 **Definition · Context management in long sessions**
> The techniques for keeping the **right information** in the model's finite context window over a long task: offloading exact facts to files, isolating verbose work in subagents, summarizing (compacting) the conversation, and persisting progress so work can resume.

**🧭 What it is, in plain words**

The context window is like a desk: everything Claude is working with has to fit on it. During a two-hour investigation, the desk fills with file contents, search results and back-and-forth. Two things then go wrong:
1. **It runs out of space.** Claude Code then **compacts**: it replaces the older conversation with a summary. Summaries keep the gist but can blur exact details: line numbers, values, IDs.
2. **Quality drops before it's full.** Long, cluttered contexts make it harder for the model to find and use the important parts. Information buried in the middle of a long input is the most easily overlooked ("lost in the middle").

The remedies each protect a different kind of information:
- 📝 **A scratchpad file** (for example `notes/exploration.md`): Claude appends confirmed facts *as it goes*. Files aren't summarized, so `/compact` and even `/clear` can't damage them. Read the file back and the exact facts return.
- 🔍 **Subagents**: send verbose reading to a separate context; only the conclusions come back.
- 🗜️ **`/compact <focus>`**: summarize now, telling it what to preserve ("keep the call chains and file paths").
- 🧹 **`/clear`**: start the conversation over (CLAUDE.md reloads), typically followed by reading the scratchpad.
- 💾 **State manifest**: for long multi-agent runs, a file recording which phases are done and pending, so a crash means *resume*, not *restart*.

**⚙️ How it works**
```
 context window over time
 ┌──────────────────────────────────────────────────────────────────┐
 │ CLAUDE.md │ task │ file reads… │ greps… │ more reads… │ ⚠️ nearly full │
 └──────────────────────────────────────────────────────────────────┘
        │                                              │
        │ throughout: append facts ──► 📝 notes/exploration.md (never summarized)
        ▼                                              ▼
 /compact keep call chains ──► │ CLAUDE.md │ summary │ recent turns │   (details may blur)
 /clear ───────────────────────► │ CLAUDE.md │ "read notes/exploration.md first" │ ✅ exact facts back
```

**🏠 Analogy: a detective's case**
> The detective's memory of a long day gets fuzzy (compaction), so they keep a **notebook** with exact names, times and addresses (scratchpad). They send officers to canvass the neighborhood and report back (subagents). And the case file on the wall shows which leads are done and which are pending (manifest).

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **Token** | The unit of text the model processes; context size is measured in tokens |
| **Compaction** | Replacing older conversation with a summary to free space (`/compact`, or automatic) |
| **`/clear`** | Wipe the conversation; CLAUDE.md is reloaded |
| **`/context`** | Show what's using the context window |
| **Scratchpad file** | A notes file of confirmed facts that survives compaction |
| **State manifest** | A file of completed and pending phases for crash recovery |
| **Lost in the middle** | Tendency to under-use information buried mid-way through long input |

### 💡 The rule, in one picture
Long sessions lose detail. You have **five tools**, each for a different problem:

| 🩺 Problem | 🛠️ Tool | What survives |
|---|---|---|
| Exact facts (file:line, values) must survive `/compact` or `/clear` | 📝 **Scratchpad file** (`notes/exploration.md`) | **Everything you wrote, exactly** |
| Discovery is verbose (reading 40 files) | 🔍 **Explore / subagent** | Its summary; the verbose work stays out |
| Context filling up, but the gist matters | 🗜️ **`/compact <focus>`** | A summary guided by your focus. **Exact details can blur.** |
| A long multi-agent run might crash | 💾 **State manifest** (completed + pending phases) | Progress, so you resume |
| Old context is stale (many files changed) | 🆕 **Fresh session + structured summary** | Only what you carry over |

### 🤔 Why you probably got it wrong (the 50% half)
- Trusting `/compact` to keep **exact** line numbers and values. It summarizes, so precision can go.
- Picking "a bigger context window" or "keep everything in the main thread" as the answer.
- Mixing up `/compact` (summarize, keep going) and `/clear` (wipe the conversation; CLAUDE.md reloads).

### 📚 Deep explanation: the E14 pattern
```
 "Trace getUser and getOrder. After each step, append confirmed facts with
  file:line to notes/exploration.md."
        ▼
 /compact keep the call chains and file paths        ← gist kept, details may blur
        ▼
 /clear  →  "Read notes/exploration.md first, then answer: ..."
        ▼
 ✅ exact facts recovered from the file
```
- **Lost in the middle:** in long inputs, put the key findings **first**, with headers.
- **Subagents** keep your main context small: they read, you get the conclusions.
- **Context is a budget.** Every file read costs tokens; `/context` shows where it went.

### 🪤 Traps
- 🪤 "Rely on `/compact`" when the stem needs **exact** values. → scratchpad.
- 🪤 "Re-run the whole multi-agent job after a crash." → manifest + resume.
- 🪤 "Resume the old session" when most prior tool results are stale. → fresh + summary.

### 🎯 Exam pattern
**Exact facts → scratchpad file. Verbose → subagent. Gist → `/compact` with focus. Crash → manifest. Stale → fresh + summary.**

### 📖 Official reading (~25 min)
| Page | Section | Look for |
|---|---|---|
| [Explore the context window](https://code.claude.com/docs/en/context-window) | Interactive page | What fills context and when |
| [Best practices](https://code.claude.com/docs/en/best-practices#manage-context-aggressively) | *Manage context aggressively* · *Use subagents for investigation* | `/clear`, `/compact`, subagents |
| [Sessions](https://code.claude.com/docs/en/sessions#manage-context-within-a-session) | *Manage context within a session* | `/compact` vs `/clear` |
| [Memory](https://code.claude.com/docs/en/memory) | *Instructions seem lost after `/compact`* | What survives compaction |
| [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) | Long-horizon sections (compaction, structured note-taking, sub-agent architectures) | **The exact source of the scratchpad and subagent patterns** |

### 🔧 Lab drill (E14 + E16)
Do the E14 sequence exactly: notes file → `/compact` → `/clear` → recover from notes. Ask for a specific line number after `/compact` *without* the notes and see whether it's still exact.

### 🧠 Memory line
**Write it down (scratchpad) · farm it out (subagent) · squeeze it (/compact) · save progress (manifest).**

### 🏁 Self-check
<details><summary>Q1. After a 2-hour exploration, <code>/compact</code> kept the architecture but lost three exact line numbers you need. What should you have done?</summary>

Append confirmed facts (with `file:line`) to a **scratchpad file** as you went, and read it back after `/compact` or `/clear`.
</details>

---

# Part 3 · 🤖 D1 Agentic Architecture & Orchestration (27%)

> 💪 Your **design** instincts here are excellent (O5–O7, O9, O10 all 100%). The four gaps are **mechanics**: how the API carries parallel calls, how sessions work, and what a subagent can actually see.

---

## W11 · 🟥 O1 · Multiple tool calls in one response · you scored 0%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟥 0% | D1 | S1 Customer Support · S3 Research | `d1/02`, `d1/05` |

### 📘 Understand it first

> 📖 **Definition · Parallel tool use**
> The ability of Claude to request **several tool calls in a single response** (several `tool_use` content blocks in one assistant message), which your application executes and answers with **all corresponding `tool_result` blocks in one user message**.

**🧭 What it is, in plain words**

Claude can't run tools itself. **Tool use** is a conversation protocol between Claude and *your code*:
1. You send messages plus a list of **tool definitions** (name, description, input schema).
2. If Claude wants a tool, it replies with a **`tool_use` block**: the tool's name, the input, and a unique **`id`**. The response's `stop_reason` is `"tool_use"`.
3. *Your code* runs the tool and sends back a **`tool_result` block** carrying the same id (`tool_use_id`) and the output.
4. Claude continues, possibly asking for more tools, until it replies with `stop_reason: "end_turn"`.

That cycle is the **agentic loop**, and each cycle is a **round trip** to the API, with its latency and tokens.

**Parallel tool use** means that in step 2 Claude may include **several** `tool_use` blocks at once, when the calls don't depend on each other. Your code can run them concurrently, then return **all** the results **together** in the next user message. Three independent lookups cost one round trip instead of three.

The rule for *when* is dependency: if call B needs call A's output (an order ID, say), B can't be requested until A's result is back, so they must be sequential.

**⚙️ How it works**
```
 your app ──► API: messages + tools
                     │
                     ▼
 Claude: [text] [tool_use id=A get_customer] [tool_use id=B list_orders]   stop_reason: tool_use
                     │
 your app runs A and B (concurrently, if you like)
                     │
                     ▼
 your app ──► API: user message [tool_result A] [tool_result B]            ← ONE message, both ids
                     │
                     ▼
 Claude: "Ana has 2 open orders…"                                           stop_reason: end_turn
```

**🏠 Analogy: a waiter**
> A good waiter takes the **whole table's order at once**, then brings all the dishes together. A bad waiter takes one order, goes to the kitchen, comes back for the next. But if someone says *"I'll decide on dessert after I see the main course"*, that order has to wait: it **depends** on the first.

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **Tool definition** | Name + description + JSON input schema you send so Claude knows a tool exists |
| **`tool_use` block** | Claude's request to call a tool: `id`, `name`, `input` |
| **`tool_result` block** | Your reply with the output, referencing `tool_use_id` |
| **`stop_reason`** | Why the response ended: `tool_use` (wants tools), `end_turn` (done), `max_tokens` (cut off) |
| **Agentic loop** | Repeat: call API → run requested tools → send results, until `end_turn` |
| **Round trip** | One request/response cycle with the API |
| **Dependent call** | A call that needs another call's output first |
| **`disable_parallel_tool_use`** | Option inside `tool_choice` that limits Claude to one tool call per response |

### 💡 The rule, in one picture
When calls are **independent**, Claude can request **all of them in one assistant turn** (several `tool_use` blocks). You run them, then send **all the results back in ONE user message**, each `tool_result` matched by its `tool_use_id`.

```
 ❌ 3 ROUND TRIPS (slow)                     ✅ 1 ROUND TRIP (fast)

 assistant: tool_use  A                      assistant: tool_use A  ┐
 user:      tool_result A                               tool_use B  ├ ONE assistant turn
 assistant: tool_use  B                                 tool_use C  ┘
 user:      tool_result B                    user:      tool_result A (id_A) ┐
 assistant: tool_use  C                                 tool_result B (id_B) ├ ONE user message
 user:      tool_result C                               tool_result C (id_C) ┘
```

### 🤔 Why you probably got it wrong
- It's a **wire-format** fact, not a design judgment. If you haven't built a tool loop by hand, it's not obvious that one assistant message can hold several `tool_use` blocks, or that all results must go back **together**.
- Distractors sound like engineering: *"build a composite `get_everything` tool"*, *"pre-fetch all data speculatively"*, *"run them as separate agents"*.

### 📚 Deep explanation
**The message shapes**
```json
// assistant turn (stop_reason: "tool_use")
{"role": "assistant", "content": [
  {"type": "text", "text": "Let me pull the customer's details."},
  {"type": "tool_use", "id": "toolu_A", "name": "get_customer",  "input": {"customer_id": "C-88"}},
  {"type": "tool_use", "id": "toolu_B", "name": "list_orders",   "input": {"customer_id": "C-88"}},
  {"type": "tool_use", "id": "toolu_C", "name": "open_tickets",  "input": {"customer_id": "C-88"}}
]}

// your NEXT user message: every result, in one message
{"role": "user", "content": [
  {"type": "tool_result", "tool_use_id": "toolu_A", "content": "..."},
  {"type": "tool_result", "tool_use_id": "toolu_B", "content": "..."},
  {"type": "tool_result", "tool_use_id": "toolu_C", "content": "..."}
]}
```

**Rules**
1. **Independent** → one turn, many `tool_use` blocks. You may execute them concurrently.
2. **All** `tool_result`s go in the **next single user message**. Splitting them across messages teaches the model to stop parallelizing.
3. **Dependent** ("find the latest order, *then* look up its shipment") → **sequence**: the second call needs the first's output.
4. Same idea one level up: a **coordinator spawns independent subagents in one response**, not one per turn.
5. Parallel use is the default. `"disable_parallel_tool_use": true` (inside `tool_choice`) turns it off. The lab uses this to show the slow version.

### 🪤 Traps
- 🪤 One user message per `tool_result`.
- 🪤 A composite "do-everything" tool (heavy machinery; hurts reuse and descriptions).
- 🪤 Speculative pre-execution of every tool "just in case".
- 🪤 Forcing independent calls into sequence "for reliability".
- 🪤 Parallelizing **dependent** calls.

### 🎯 Exam pattern
**"Independent lookups, one per turn, slow" → let Claude emit them in one turn and return all results in one user message.**

### 📖 Official reading (~20 min)
| Page | Section | Look for |
|---|---|---|
| [Parallel tool use](https://platform.claude.com/docs/en/agents-and-tools/tool-use/parallel-tool-use) | *Execution semantics* · *Maximizing parallel tool use* · *Disable parallel tool use* · *Troubleshooting* | The one-message-of-results rule |
| [Handle tool calls](https://platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls) | *Handling results from client tools* | `tool_use_id` matching, result formatting |
| [Prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#optimize-parallel-tool-calling) | *Optimize parallel tool calling* | Prompting for parallelism |

### 🔧 Lab drill
`python d1-agentic/02_parallel_tool_calls.py`: Section A shows N `tool_use` blocks in one turn. Section B sets `disable_parallel_tool_use` and shows the extra round trips. Count the turns.

### 🧠 Memory line
**Independent → one turn → one results message. Dependent → sequence.**

### 🏁 Self-check
<details><summary>Q1. Your loop gets 3 <code>tool_use</code> blocks in one response. You send each result in its own user message. What's wrong?</summary>

All results must go back in **one** user message, each with its `tool_use_id`. Splitting them breaks the expected format and discourages future parallel calls.
</details>

<details><summary>Q2. "Look up the order, then refund it." Parallel or sequential?</summary>

**Sequential.** The refund depends on the lookup's result.
</details>

---

## W12 · 🟥 O2 · Session resumption and targeted re-analysis · you scored 0%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟥 0% | D1 (SDK) + D3 (CLI) | S2 · S4 | `d1/06`, `d3` E13 |

### 📘 Understand it first

> 📖 **Definition · Sessions, resume and fork**
> A **session** is a saved conversation (every message and tool result) identified by a **session ID**. **Resuming** reloads that history and continues it under the *same* ID. **Forking** copies the history into a *new* session with a *new* ID, leaving the original untouched.

**🧭 What it is, in plain words**

Claude Code (and the Agent SDK) save each conversation as a transcript on disk. That lets you close the terminal today and pick up tomorrow without re-explaining everything.

The subtle part is **what's inside the saved history**: not just your words, but **every tool result**, including the content of every file Claude read. Those are **snapshots**: they show the file as it was *when it was read*. If the file changes afterwards, the history still holds the old version, and Claude, seeing it in context, tends to trust it.

That's why the right action depends on how much has changed:
- **Few, known changes** → resume, and **tell Claude exactly which files changed** and how, so it re-reads only those. Everything else in the history is still accurate and reused.
- **Many changes** → the history is now more wrong than right. Start **fresh**, and carry over a short **structured summary** of conclusions that still hold.
- **Two alternatives to compare** → **fork**: both branches share the same starting history, but each continues independently under its own ID.

**⚙️ How it works**
```
                     ┌──────── session abc (orders-review) ────────┐
                     │ msg1 · Read orders.ts (snapshot Mon) · R1–R3 │
                     └──────────────────────┬──────────────────────┘
       ┌────────────────────────────────────┼─────────────────────────────────────┐
       ▼                                    ▼                                     ▼
 🔁 RESUME (-r abc)                   🌿 FORK (-r abc --fork-session)        🆕 FRESH + SUMMARY
 same ID abc                          new ID xyz, copy of history            new ID, empty history
 + "only orders.ts changed:           original abc untouched                 + "Still true: R2, R3.
    re-read it, re-check R1–R3"       try approach B here                       Changed: most of src/"
```

**🏠 Analogy: a lab notebook**
> **Resume** = keep writing in the same notebook, with a note: "page 12's measurement is outdated; re-measured today". **Fork** = photocopy the notebook and try a different experiment in the copy. **Fresh + summary** = the old notebook is mostly wrong now, so start a new one with a one-page summary of what's still valid.

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **Session** | A saved conversation: messages + tool results |
| **Session ID** | The unique identifier of a session |
| **Resume** | `claude --resume <id/name>` / SDK `resume=`: continue the same session |
| **Continue** | `claude -c`: resume the most recent session in this folder |
| **Fork** | `--fork-session` / SDK `fork_session=True`: branch into a new session ID |
| **Named session** | `claude -n <name>`: lets you resume by name |
| **Stale context** | Earlier tool results that no longer match the current files |
| **Targeted re-analysis** | Re-checking only what changed, named explicitly |

### 💡 The rule, in one picture
Three actions, chosen by **how much of the old context is still true**:

```
 What changed since the last session?
 │
 ├─ 🟢 A FEW KNOWN files changed; the rest still holds
 │     └─► 🔁 RESUME, and NAME the changed files
 │          "Only orders.ts changed: orderTotal now takes a discount.
 │           Re-read only that file and re-check R1–R3."
 │
 ├─ 🔴 A LOT changed; old tool results are now wrong
 │     └─► 🆕 FRESH session + a structured summary of what still holds
 │
 └─ 🔀 You want to try TWO approaches from the same starting point
       └─► 🌿 FORK: new session ID, same history up to the fork point
```

| | Session ID | History | Use when |
|---|---|---|---|
| 🔁 **Resume** | **same** | everything so far | Context mostly valid |
| 🌿 **Fork** | **new** | copied up to the fork | Compare approaches from one baseline |
| 🆕 **Fresh + summary** | new | only your summary | Prior tool results are stale |

### 🤔 Why you probably got it wrong
- "Resume and ask it to re-analyze everything" *sounds* thorough. It re-reads the whole codebase: slow and costly. The exam wants **targeted** re-analysis: name what changed.
- "Resume" when the files changed a lot *sounds* efficient, but Claude **trusts its earlier file reads**, which are now stale.
- Fork vs resume: the key testable fact is **fork = new session ID**, resume = same ID.

### 📚 Deep explanation
**Why naming the changed files matters.** A resumed session holds earlier `Read` results in its history. Claude treats them as current. If you don't say what changed, it either reasons on stale content or, if told "files changed", re-reads everything. Naming the files gets the best of both: reuse what's valid, refresh only what isn't.

**Why stale context needs a fresh start.** If most earlier reads are wrong, the history is actively misleading. Start fresh, and pass a **structured summary** of the conclusions that still hold (decisions, constraints, open questions), not the raw transcript.

**Commands**
| Where | Resume | Fork | Name / continue |
|---|---|---|---|
| 🖥️ CLI | `claude --resume orders-review` (`-r`) | `claude -p -r orders-review --fork-session "..."` | `claude -n orders-review` · `claude -c` = most recent here |
| 🐍 Agent SDK | `resume=session_id` | `resume=session_id, fork_session=True` | session ID from the init message |

### 🧪 Worked example (E13)
```bash
claude -n orders-review        # "Read src/api/v2/orders.ts, list risks R1–R3."  then /exit
# ...you edit orderTotal yourself...
claude --resume orders-review  # "Only orders.ts changed: orderTotal now takes a discount.
                               #  Re-read only that file and re-check R1–R3."
claude -p -r orders-review "OK" --output-format json                 # same session_id
claude -p -r orders-review --fork-session "OK" --output-format json  # NEW session_id
```

### 🪤 Traps
- 🪤 Resume + "files changed, re-analyze everything".
- 🪤 Resume when most prior results are stale.
- 🪤 A fresh session with **no** summary (everything lost).
- 🪤 Fork just to "continue" (that's resume).
- 🪤 "A fork keeps the same session ID." ❌ New ID.

### 🎯 Exam pattern
**Mostly valid → resume + name changes. Stale → fresh + structured summary. Two approaches → fork (new ID).**

### 📖 Official reading (~20 min)
| Page | Section | Look for |
|---|---|---|
| [Manage sessions](https://code.claude.com/docs/en/sessions) | *Resume a session* · *What a resumed session restores* · *Name your sessions* · *Branch a session* | `--resume`, `-c`, `-n`, forking |
| [Agent SDK: Sessions](https://code.claude.com/docs/en/agent-sdk/sessions) | Whole page | `resume`, `fork_session`, session IDs |
| [CLI reference](https://code.claude.com/docs/en/cli-reference) | `--fork-session`, `--resume`, `--continue` rows | "create a new session ID instead of reusing the original" |
| [Common workflows](https://code.claude.com/docs/en/common-workflows#resume-previous-conversations) | *Resume previous conversations* | Everyday resume usage |

### 🔧 Lab drill
`python d1-agentic/06_sessions_resume_fork.py`, including exercise 8 (resume + "re-analyze everything" vs resume + named file). Then E13 from the CLI and compare the two `session_id`s.

### 🧠 Memory line
**Resume = same ID, name what changed. Fork = new ID, two paths. Stale = fresh + summary.**

### 🏁 Self-check
<details><summary>Q1. Yesterday's session analyzed 30 files. Overnight, a teammate rewrote 25 of them. Best approach?</summary>

**Fresh session + a structured summary** of the conclusions that still hold. Resuming would make Claude reason over stale file reads.
</details>

<details><summary>Q2. You want to try a Redis cache and an in-memory LRU from the same analysis, and compare. Best approach?</summary>

**Fork** the session twice (each gets a new session ID from the same baseline).
</details>

---

## W13 · 🟧 O3 · Complete context in subagent prompts · you scored 33%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟧 33% | D1 | S3 Research | `d1/05` ex 6, `d3` E16, `d5/03` |

### 📘 Understand it first

> 📖 **Definition · Context passing to subagents**
> In a multi-agent system, a **coordinator** (orchestrator) delegates subtasks to **subagents**. Each subagent starts with **an empty context** and receives **only the prompt the coordinator writes for it**, so that prompt must carry everything the subagent needs: goal, criteria, inputs and their sources.

**🧭 What it is, in plain words**

A **multi-agent system** splits a big job across several model instances: a coordinator that plans and merges, and subagents that each do one part (search a topic, verify a fact, write a section). The main reason to do this is **context isolation**: each subagent works in its own clean window, so no single context gets overloaded.

But isolation cuts both ways. A subagent is a **separate conversation**. It never saw the user's request, the coordinator's reasoning, or the 40 tool results the coordinator collected. The prompt the coordinator writes for it (the **handoff**) is its whole world. If the handoff says "write the paragraph about what we found", the subagent has no idea what was found.

So the quality of a subagent's output is capped by the **completeness of its handoff**: the goal, the quality bar, the actual findings, and the **provenance** of each finding (where it came from), preferably as structured data so nothing gets lost in paraphrase.

**⚙️ How it works**
```
                         🧭 COORDINATOR
            (user request, plan, 40 tool results, findings F1…F9)
                 │                         │
      handoff #1 │ goal + F1–F4 + sources  │ handoff #2: "summarize what we found"
                 ▼                         ▼
        🤖 subagent A                🤖 subagent B
        sees: handoff #1 only        sees: handoff #2 only → "found WHAT?" → "not provided" 😕
                 │
                 ▼
        ✅ cited paragraph
```

**🏠 Analogy: briefing a freelance contractor by email**
> The contractor wasn't in any of your meetings. If your email says *"do the thing we discussed"*, you get nothing useful back. If it says *what* you need, *for whom*, *what good looks like*, and attaches *the source documents*, you get exactly what you need.

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **Coordinator / orchestrator** | The agent that plans, delegates, and merges results |
| **Subagent** | A delegated agent with its own isolated context |
| **Handoff / delegation prompt** | The prompt the coordinator writes for a subagent: its only input |
| **Context isolation** | Each agent's context is separate; nothing is shared implicitly |
| **Provenance** | Where a fact came from: source, page, URL, date, method |
| **Structured handoff** | Passing findings as lists/JSON with sources attached, rather than prose |

### 💡 The rule, in one picture
🧠 **A subagent is a new hire with amnesia.** It sees **only the prompt you write for it** (plus, in Claude Code, CLAUDE.md for non-Explore types). It does **not** see the coordinator's conversation or tool results.

```
  Coordinator's context                           Subagent's context
  ┌──────────────────────────────────┐            ┌──────────────────────────┐
  │ user request                     │            │                          │
  │ F1: refund limit 500 EUR  (S1)   │   prompt   │  ONLY what you wrote     │
  │ F2: manager approval > limit (S2)│ ─────────► │  in the prompt           │
  │ 40 tool results...               │            │                          │
  └──────────────────────────────────┘            └──────────────────────────┘
```

### 🤔 Why you probably got it wrong (33%)
- It's intuitive to assume the helper "knows the context" because it's part of the same system. The exam calls *"subagents inherit history"* an **invented mechanism**.
- A **short summary** feels efficient, but it drops sources, dates and numbers, so the synthesizer can't cite.

### 📚 Deep explanation
**What a complete subagent prompt contains**
| ✅ Element | Why |
|---|---|
| 🎯 **Goal** (what and for whom) | It can't infer intent |
| 📏 **Quality criteria** (cite every claim; flag gaps) | It can't guess your bar |
| 📦 **Complete findings**, not a one-line summary | It has nothing else to work from |
| 🏷️ **Source metadata** per fact: document, page, URL, date, method | So citations survive to the final output |
| 🧱 **Structured** (list / JSON), not prose | Structure keeps the claim → source link |
| 📐 **Output format** | So the coordinator can merge it |

❌ **Bad:** `Write the refund-limit paragraph.` → the subagent writes "not provided" or invents something.

✅ **Good:**
```
Goal: one paragraph on the refund limit, for the policy FAQ.
Facts (use only these; keep each source next to its claim):
  F1: The refund limit is 500 EUR.             Source S1: policy.md, p.3 (May 2026)
  F2: Refunds above the limit need a manager.  Source S2: ops-handbook.md, §4
Quality bar: cite every claim. If something is missing, write "not provided".
Output: one paragraph, at most 80 words.
```

### 🪤 Traps
- 🪤 "The subagent can read the coordinator's history." ❌ Invented.
- 🪤 "Summarize what we found and pass it on." Sources lost.
- 🪤 "Give the synthesizer the search tool so it can find what it needs." That's W16's anti-pattern; it also re-does work.

### 🎯 Exam pattern
**Subagent output vague / uncited / "not provided" → pass complete findings with source metadata, as structured data, in its prompt.**

### 📖 Official reading (~25 min)
| Page | Section | Look for |
|---|---|---|
| [How we built our multi-agent research system](https://www.anthropic.com/engineering/multi-agent-research-system) | The prompt-engineering principles (teaching the orchestrator to delegate: objective, output format, tools, task boundaries) | **Why vague delegation fails** |
| [Agent SDK: Subagents](https://code.claude.com/docs/en/agent-sdk/subagents) | Whole page | What context a subagent gets |
| [Claude Code subagents](https://code.claude.com/docs/en/sub-agents#manage-subagent-context) | *Manage subagent context* · *Choose between subagents and main conversation* | Isolation |
| [Prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#subagent-orchestration) | *Subagent orchestration* | Delegation guidance |

### 🔧 Lab drill
`d3` **E16**: delegate to `synth` with a bare prompt (→ "not provided"), then with F1 + source (→ cited paragraph). `d1/05` exercise 6: swap structured findings for a prose summary and watch citations vanish.

### 🧠 Memory line
**It knows only its prompt. Pass findings + sources, as data.**

### 🏁 Self-check
<details><summary>Q1. The synthesizer's report has claims but no citations, though the search agents returned URLs. Most likely cause?</summary>

The coordinator passed a **prose summary without source metadata**. Pass structured findings with `source`, `date` and so on in the synthesizer's prompt.
</details>

---

## W14 · 🟧 O4 · Goal-oriented vs procedural delegation · you scored 50%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟧 50% | D1 | S3 Research | `d1/05` ex 4 |

### 📘 Understand it first

> 📖 **Definition · Goal-oriented vs procedural delegation**
> **Procedural delegation** tells an agent *which steps to perform*. **Goal-oriented delegation** tells it *what outcome is needed and how quality will be judged* (goal, scope, coverage, quality criteria, output format) and leaves the method to the agent.

**🧭 What it is, in plain words**

A coordinator has to turn a big request into subtasks (**decomposition**) and describe each one to a subagent (**delegation**). There are two styles:

- **Procedural:** "1. Search visual art. 2. Search graphic design. 3. Summarize." The agent does exactly that and stops. Its coverage is capped at what the coordinator happened to think of. If the coordinator forgot music and film, so does the report.
- **Goal-oriented:** "Map how AI is changing the creative industries. Cover every major sector you find. At least two independent sources per sector, with dates. Flag gaps." The agent can discover sectors the coordinator never listed, and knows when it's done.

Neither is always right. **Fixed procedures** suit work whose steps are known in advance (extract → validate → store): a **fixed pipeline**. **Goals with criteria** suit **open-ended** work like research, where what you'll find shapes what to do next.

A related diagnostic skill: when a multi-agent result is wrong, trace the pipeline in order and fix the **first** stage that went wrong. A synthesizer can't summarize sectors nobody searched.

**⚙️ How it works**
```
 PROCEDURAL                                 GOAL-ORIENTED
 coordinator's list ─► [A] [B] ─► report    goal + criteria ─► agent explores ─► [A][B][C][D][E] ─► report
 coverage = what the coordinator imagined   coverage = what actually exists (checked against criteria)
```

**🏠 Analogy: shopping instructions**
> *"Go to shop A, then shop B, and buy the cheaper one"* gets you the best of two shops. *"Find the best price in town for this model; check at least five sellers; tell me if any are out of stock"* gets you the best price in town.

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **Decomposition** | Splitting a task into subtasks |
| **Fixed decomposition** | Steps known in advance; a set pipeline |
| **Dynamic decomposition** | Next steps depend on what's found |
| **Coverage criteria** | What "complete" means (all sectors, all regions…) |
| **Quality criteria** | The bar for each result (sources, dates, gap flags) |
| **Wrong-layer fix** | Fixing a later stage for a problem an earlier stage caused |

### 💡 The rule, in one picture
Tell subagents **what good looks like** (goal, coverage, quality bar), not a numbered list of steps. A step list caps coverage at **what you already thought of**.

```
 ❌ PROCEDURAL                         ✅ GOAL-ORIENTED
 1. Search visual art.                 Goal: map how AI is changing the creative industries.
 2. Search graphic design.             Coverage: every major sector you find, not only
 3. Summarize.                                   the ones named here.
                                       Quality: ≥ 2 independent sources per sector, with dates.
 → covers exactly 2 sectors                     Flag any gaps.
   (music, film, gaming missing)       → finds music, film, gaming, publishing...
```

### 🤔 Why you probably got it wrong (the 50% half)
- Step lists *feel* controllable and deterministic. For **open-ended research**, they're a ceiling.
- The **wrong-layer trap**: when a report misses sectors, the tempting fix is the synthesizer ("make it more thorough"). But the synthesizer can't add sectors that were never searched. **Fix the first component that went wrong: the coordinator's decomposition.**

### 📚 Deep explanation
- **Goal-oriented ≠ vague.** It's specific about *outcomes* (coverage, source count, gap flagging, output format) and leaves *method* to the agent.
- **When procedural *is* right:** fixed, known pipelines (extract → validate → store). That's O7's "fixed decomposition", which you scored 100% on. The difference: **known steps → fixed pipeline; open-ended exploration → goals + criteria.**
- **Debugging a multi-agent result:** walk the pipeline **in order** and find the first broken link.
```
 coordinator decomposition ──► search subagents ──► synthesizer ──► final report
        ▲ fix HERE if topics are missing            ▲ fix here only if inputs were complete
```

### 🪤 Traps
- 🪤 "Improve the synthesizer's prompt" for missing coverage.
- 🪤 "Add more numbered steps" to fix coverage.
- 🪤 "Add a QA agent at the end" (heavy, and the wrong layer).

### 🎯 Exam pattern
**Narrow coverage → coordinator delegated procedurally or too narrowly → give goals + coverage + quality criteria.**

### 📖 Official reading (~20 min)
| Page | Section | Look for |
|---|---|---|
| [How we built our multi-agent research system](https://www.anthropic.com/engineering/multi-agent-research-system) | Prompting principles, especially "teach the orchestrator how to delegate" and "scale effort to query complexity" | Real failure modes of narrow delegation |
| [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) | *Orchestrator-workers* vs *Prompt chaining* | Dynamic vs fixed decomposition |
| [Prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#research-and-information-gathering) | *Research and information gathering* | Success criteria over steps |

### 🔧 Lab drill
`d1/05` exercise 4: replace the goal text with a numbered procedure and compare coverage.

### 🧠 Memory line
**Delegate outcomes, not steps. Fix the first broken layer.**

### 🏁 Self-check
<details><summary>Q1. The final report is beautifully written but misses two of five regions. Which component do you fix first?</summary>

The **coordinator's decomposition / delegation** (it didn't cover those regions). Not the synthesizer.
</details>

---

# Part 4 · 🛠️ D2 Tool Design & MCP Integration (18%)

> 💪 MCP and descriptions are strong (O34–O36 at 100%). Two specific rules to fix.

---

## W15 · 🟥 O37 · `tool_choice` + prerequisite ordering · you scored 0% (O27: 100%)

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟥 0% | D2 | S6 Extraction · S1 | `d2/03`, `d1/03` |

### 📘 Understand it first

> 📖 **Definition · `tool_choice`**
> A Messages API parameter that controls **whether and which tool Claude must call** in a response: `auto` (Claude decides, may answer in text), `any` (must call one of the tools), `tool` (must call the named tool), or `none` (no tools).

**🧭 What it is, in plain words**

By default (`auto`), Claude looks at the request and the tool descriptions and *decides* whether to call a tool. That's what you want most of the time. But sometimes "probably" isn't good enough:
- You need **structured output every time**: a text reply would break your pipeline. → `any` (some tool, any of them) or `tool` (this one).
- A **prerequisite** must happen first, every time: load the schema, extract metadata, verify identity. → force that tool **on the first turn**.

How forcing works: with `any` or `tool`, the API pre-fills the start of Claude's reply so it *must* begin with a tool call. Claude writes no text before it, and a forced call skips thinking.

The trap is the loop. A tool loop ends when Claude replies with `end_turn`. If you force a tool on **every** request, Claude can never give that final answer, and the loop never ends. So for ordering: **force on turn 1, then switch back to `auto`**.

Note the distinction from a **code gate**: `tool_choice` controls *which tool gets called*; a gate inside a tool controls *whether an action is permitted* (for example, refusing a refund until identity is verified).

**⚙️ How it works**
```
 request 1  tool_choice={"type":"tool","name":"extract_metadata"}  → Claude MUST call extract_metadata
 request 2  tool_choice={"type":"auto"}                             → Claude chooses: enrich_topics
 request 3  tool_choice={"type":"auto"}                             → Claude: final answer (end_turn) ✅

 ✗ every request forced → request 3 must call a tool again → no end_turn → loop until your cap 🔁
```

**🏠 Analogy: a checklist pilot**
> Before take-off, the **pre-flight checklist is mandatory**: it's the forced first step. After that, the pilot flies with judgment (`auto`). Forcing the checklist at *every* moment of the flight would mean the plane never lands.

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **`auto`** | Default; Claude may call a tool or reply in text |
| **`any`** | Must call one of the provided tools; Claude picks which |
| **`tool`** (forced) | Must call this specific tool |
| **`none`** | No tool calls allowed |
| **Prerequisite** | A step that must always happen before others |
| **Prefill** | The API starting the assistant reply for Claude (here: with a tool call) |
| **Strict tool use** | `strict: true` on a tool: inputs are guaranteed to match its schema |
| ⚖️ **Model restriction** | Today, Opus 5.5 / Sonnet 5.5 / Fable 5.1 / Mythos 5.1 return 400 on `any`/`tool`; exam answer is unchanged |

### 💡 The rule, in one picture
You already know *that* `tool_choice` guarantees a call (O27: 100%). The gap is **which value, and when to switch it**.

| `tool_choice` | What happens | Use when |
|---|---|---|
| `{"type": "auto"}` (default) | Claude **may** call a tool **or answer in text** | Normal agent turns |
| `{"type": "any"}` | Claude **must call some tool**, its choice | Structured output with several possible schemas, doc type unknown |
| `{"type": "tool", "name": "X"}` | Claude **must call X** | X must run first, or you need exactly that extraction |
| `{"type": "none"}` | No tools | Force a text-only turn |
| 🔀 **Forced on turn 1, then `auto`** | X runs first, then Claude is free | ✅ **Prerequisite ordering** |
| ♾️ Forced on **every** turn | ❌ The loop never reaches `end_turn` | Never |

### 🤔 Why you probably got it wrong
- "Add *always call extract_metadata first* to the system prompt" is the **words-not-mechanism** trap. It lowers the miss rate; it doesn't guarantee order.
- "Force it" without the **switch back to `auto`** traps the loop: every turn must call that tool, so Claude can never finish.
- `any` vs forced: `any` guarantees *a* tool call, not *which*. If **this specific** tool must run, force it by name.

### 📚 Deep explanation: prerequisite ordering, turn by turn (lab `d2/03`)
```
 turn 0   tool_choice = {"type":"tool","name":"extract_metadata"}  → extract_metadata  ✅ guaranteed first
 turn 1   tool_choice = {"type":"auto"}                             → enrich_topics
 turn 2   tool_choice = {"type":"auto"}                             → end_turn  ✅
```
```python
# from d2-tools-mcp/03_tool_choice.py
tool_choice=lambda turn: {"type": "tool", "name": "extract_metadata"} if turn == 0 else {"type": "auto"}
```

**Notes from the official docs worth knowing**
- With `any` or a forced tool, the API **prefills** the assistant turn, so Claude emits **no text before** the `tool_use` block, and a forced call **skips thinking**.
- Changing `tool_choice` between turns **invalidates cached message blocks** (prompt caching): a cost note, not a reason to avoid it.
- `any` + **strict tool use** (`strict: true`) guarantees both a call *and* schema-valid inputs.

**Prerequisite in code (`d1/03`)** is the sister technique: when a rule is about *business state* ("identity must be verified before a refund"), enforce it with a **code gate in the tool** that returns a structured error ("call `get_customer` first"). `tool_choice` controls *which tool is called*; a gate controls *whether an action is allowed*.

> ⚖️ **Guide vs docs:** forced `tool_choice` is the exam answer for guaranteeing a call or an order. Docs today: `any` and forced return **400** on Opus 5.5, Sonnet 5.5, Fable 5.1 and Mythos 5.1. The docs recommend `auto` + strict tool use or structured outputs there. That's why the lab's `LAB_MODEL` is Haiku 5.5. **Keep the guide answer.**

### 🪤 Traps
- 🪤 Prompt text "always call X first".
- 🪤 Forcing the tool on every turn.
- 🪤 `auto` when structured output is **mandatory** (it may reply in text).
- 🪤 `any` when one **specific** tool must run first.

### 🎯 Exam pattern
**Must call some tool → `any`. Must call THIS tool → forced. Must run FIRST → forced on turn 1, then `auto`.**

### 📖 Official reading (~20 min)
| Page | Section | Look for |
|---|---|---|
| [Define tools](https://platform.claude.com/docs/en/agents-and-tools/tool-use/define-tools) | *Controlling Claude's output → Forcing tool use* | The four values, prefill behavior, model restrictions table |
| [Strict tool use](https://platform.claude.com/docs/en/agents-and-tools/tool-use/strict-tool-use) | Whole page | `strict: true` + `any` |
| [Tool use overview](https://platform.claude.com/docs/en/agents-and-tools/tool-use/overview) | The agent loop | Where `tool_choice` sits in the loop |
| [Handling stop reasons](https://platform.claude.com/docs/en/build-with-claude/handling-stop-reasons) | `tool_use` vs `end_turn` | Why forcing every turn never ends |

### 🔧 Lab drill
`python d2-tools-mcp/03_tool_choice.py`. Watch the per-turn `tool_choice`. Add `--newest-model-demo` to see the 400 on a newer model. Then `python d1-agentic/03_prerequisite_gate.py` for the code-gate version.

### 🧠 Memory line
**`any` = some tool. Forced = this tool. Force once, then `auto`.**

### 🏁 Self-check
<details><summary>Q1. You force <code>classify_document</code> on every turn. What breaks?</summary>

Claude must call it on every turn, so it **never reaches `end_turn`**. Force it on turn 1 only, then switch to `auto`.
</details>

<details><summary>Q2. An extractor must always return JSON, but there are three document schemas and the type isn't known ahead of time. Which <code>tool_choice</code>?</summary>

**`{"type": "any"}`** with one tool per schema: it must call one, and it picks the right one.
</details>

---

## W16 · 🟧 O33 · Tool distribution across agents · you scored 50%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟧 50% | D2 (+ D1) | S3 Research | `d2/04`, `d1/05` ex 7, `d3` E16 |

### 📘 Understand it first

> 📖 **Definition · Tool distribution**
> The design decision of **which tools each agent in a system receives**, so each agent has what its role needs, selection stays accurate, and agents can't drift into other roles' work.

**🧭 What it is, in plain words**

Every tool you give an agent is described in its context, and on every step the agent chooses among them. More tools mean more descriptions to compare, more overlap between them, and more chances to pick the wrong one. Tools also shape **behavior**: an agent that holds a search tool will tend to search, even when its job is to write.

So in a multi-agent system you distribute tools by **role**, following **least privilege**: each agent gets the small set (about 4–5) its job requires. Where a role regularly needs a sliver of another role's capability (a synthesizer that sometimes must double-check one figure), you give it **one narrowly scoped tool** (`verify_fact`) rather than the full capability (`search_corpus`).

The strongest form of restriction is **structural**: in config (a subagent's `tools:` field), or in code (replace a generic `fetch_url(url)` with `load_document(doc_id)` that can only load approved documents). Restrictions written as prompt text ("don't search") are just requests.

**⚙️ How it works**
```
 ROLE            NEEDS                         GETS
 🔎 Searcher     find + load sources           search_corpus · load_document · list_sources · cite
 🧪 Synthesizer  combine findings; spot-check  (findings in its prompt) + verify_fact  ← scoped
 ✍️ Writer       format + save                 format_report · save_report
 🧭 Coordinator  plan + spawn + merge          Task (spawn) · read_manifest · write_manifest
```

**🏠 Analogy: a toolbelt**
> An electrician with 60 tools on their belt is slower to grab the right one, and more tempted to "just quickly fix the plumbing". Give them the electrical tools, plus a small torch for looking into the pipes they don't own.

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **Least privilege** | Give each agent only the access its role needs |
| **Tool selection accuracy** | How reliably the agent picks the right tool; drops as tool count and overlap grow |
| **Role drift** | An agent doing another role's work (synthesizer searching) |
| **Scoped cross-role tool** | One narrow tool borrowed from another role (`verify_fact`) |
| **Constrain in code** | Make misuse impossible through the tool's interface, not prompt text |
| **`Task`** | ⚖️ Guide's name for the subagent-spawning tool (`Agent` today; `Task` still an alias) |

### 💡 The rule, in one picture
Give each agent **the 4–5 tools its role needs**, plus at most **one scoped cross-role tool** for a frequent need. **Constrain generic tools in code**, not prompt text.

```
 ❌ 18 tools for every agent              ✅ tools by role
 ┌──────────────────────────────┐         🔎 Searcher:    search_corpus, load_document, list_sources, ...
 │ search, fetch_url, verify,   │         🧪 Synthesizer: verify_fact     ← ONE scoped cross-role tool
 │ load, write, summarize, ...  │         ✍️ Writer:      format_report, save_report
 │ (selection quality drops)    │
 └──────────────────────────────┘
```

### 🤔 Why you probably got it wrong (the 50% half)
- "Give everyone every tool for flexibility" sounds empowering. More tools → **worse selection** and role drift (the synthesizer starts searching).
- "Tell the synthesizer in its prompt not to search" is **words**. Remove the tool instead.
- The middle ground is the tested nuance: not *zero* cross-role tools, but **one narrowly scoped** one (`verify_fact`, not the full search tool).

### 📚 Deep explanation
1. **4–5 tools per role** keeps descriptions distinguishable and choices accurate (lab `d2/04`: 4 role tools vs 18).
2. **Scoped cross-role tool:** the synthesizer often needs to double-check one claim. Give it `verify_fact(claim)` with a narrow contract, **not** `search_corpus`.
3. **Constrain in code:** replace a generic `fetch_url(url)` with `load_document(doc_id)`, so misuse is **impossible**, not merely discouraged.
4. **In Claude Code:** a subagent's `tools:` frontmatter restricts tools in config (the lab's `synth` has `tools: Read`, so it can't Write).
5. **Spawning:** the coordinator needs the spawn tool. ⚖️ Guide: `allowedTools` must include **`Task`**. Docs today: renamed `Agent` in v2.1.63, with `Task` still an alias.

### 🪤 Traps
- 🪤 All tools to all agents. · 🪤 Prompt-only restrictions. · 🪤 Zero verification ability for the synthesizer (forces round trips to the coordinator for every check). · 🪤 Giving the synthesizer the full search tool.

### 🎯 Exam pattern
**Role drift or poor tool choice → 4–5 role tools + one scoped cross-role tool; constrain generic tools in code.**

### 📖 Official reading (~25 min)
| Page | Section | Look for |
|---|---|---|
| [Writing tools for agents](https://www.anthropic.com/engineering/writing-tools-for-agents) | Choosing the right tools; namespacing; returning meaningful context | Fewer, purposeful tools |
| [Define tools](https://platform.claude.com/docs/en/agents-and-tools/tool-use/define-tools) | *Best practices for tool definitions* | Descriptions, consolidation, namespacing |
| [Claude Code subagents](https://code.claude.com/docs/en/sub-agents#control-subagent-capabilities) | *Control subagent capabilities* · *Frontmatter reference* | `tools:` restriction |
| [Agent SDK: Subagents](https://code.claude.com/docs/en/agent-sdk/subagents) | Tool configuration | Per-subagent tools |

### 🔧 Lab drill
`python d2-tools-mcp/04_tool_distribution.py` (4 vs 18 tools). `d1/05` exercise 7: give the synthesizer search and watch it search instead of synthesize. `d3` E16: ask `synth` to write a file; it can't.

### 🧠 Memory line
**Few tools per role. One scoped helper. Enforce in config or code.**

### 🏁 Self-check
<details><summary>Q1. The synthesizer often needs to confirm one statistic, and round trips through the coordinator are slow. Best fix?</summary>

Give the synthesizer a **narrow `verify_fact` tool** (one scoped cross-role tool), not the full search tool.
</details>

---

# Part 5 · 📄 D4 Prompt Engineering & Structured Output (20%)

> 💪 You're strong on output *methods* (O24, O25, O28, O31 at 100%). The gaps are about **what to do when the data itself is messy, missing or ambiguous**, and one API-mode choice. One decision tree fixes W17 and W18 together.

---

## W17 · 🟥 O29 · Extraction accuracy patterns · you scored 0%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟥 0% | D4 | S6 Structured Extraction | `d4/03`, `d4/04` |

### 📘 Understand it first

> 📖 **Definition · Structured extraction accuracy**
> **Structured extraction** turns unstructured documents (invoices, receipts, contracts) into data that fits a **schema**. **Accuracy patterns** are the techniques that fix each specific *kind* of extraction error: normalization rules, per-layout examples, nullable fields, validation-and-retry, and conflict flags.

**🧭 What it is, in plain words**

An extraction pipeline has three parts: a **schema** describing the output (fields, types, allowed values), a **prompt** that tells Claude how to fill it, and **validation** in your code that checks the result. Using a tool schema or structured outputs guarantees the result has the right **shape** (valid JSON, right fields, right types). It does **not** guarantee the **values** are right.

Value errors come in distinct kinds, and each has its own cause:
- **Format errors:** the value was found but written inconsistently (`02/03/24` vs `2024-03-02`). Cause: no stated convention. Fix: **normalization rules**.
- **Layout errors:** the value is missed on certain document types (receipts put the total at the bottom under "AMOUNT DUE"). Cause: Claude hasn't seen that layout. Fix: a **few-shot example for that layout**.
- **Absence:** the value isn't in the document. Cause: the schema demands it anyway. Fix: a **nullable field**.
- **Slips:** occasional invalid dates or bad arithmetic. Fix: **validate in code and retry** with the specific error.
- **Contradictions:** the document disagrees with itself. Fix: record **both values and a conflict flag**, and let a human or rule decide.

A **syntactic** error breaks the shape (missing field, wrong type); the schema prevents those. A **semantic** error has the right shape but the wrong meaning (February 30th, totals that don't add up); only validation catches those.

**⚙️ How it works**
```
 📄 document ─► 🧠 Claude + schema + normalization rules + per-layout examples
                      │
                      ▼
                 { extracted JSON }   ← shape guaranteed by schema
                      │
                      ▼
                 🧪 validation in code (real dates? totals add up? IDs exist?)
                      │
           ┌──────────┴───────────┐
           ▼                      ▼
       ✅ accept            ❌ retry with: document + this output + the exact error
                                 (but never for ABSENT data, and record conflicts instead of "fixing" them)
```

**🏠 Analogy: a data-entry clerk**
> A new clerk copying invoices into a spreadsheet needs a **style guide** ("dates as YYYY-MM-DD"), **one example of each invoice type** ("on supplier X's forms, the total is bottom-left"), permission to **leave a cell blank** when there's nothing to copy, and a **reviewer** who returns the sheet saying "row 14: February 30th doesn't exist".

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **Schema** | Formal spec of output fields, types and allowed values |
| **Normalization** | Converting values to one standard format |
| **Layout** | The visual structure of a document type (where things are on the page) |
| **Few-shot (per layout)** | One worked example per document layout |
| **Syntactic error** | Wrong shape: missing field, wrong type |
| **Semantic error** | Right shape, wrong meaning: impossible date, totals that don't add up |
| **Validation-retry loop** | Check in code; on failure, re-ask with the document, output and error |
| **Conflict flag** | A field recording that the source contradicts itself |

### 💡 The rule, in one picture
**Diagnose the type of error first. Each type has its own fix.**

```
 What's going wrong with the extraction?
 │
 ├─ 📏 Values are THERE, but in MESSY FORMATS
 │     "3rd Feb 2024" · "02/03/24" · "2024.02.03" · "$1,200.00" · "1200 USD"
 │        └──► NORMALIZATION RULES in the prompt, next to the schema
 │
 ├─ 🧩 Wrong or empty only for certain document LAYOUTS
 │     typed invoices fine; scanned receipts miss the total
 │        └──► FEW-SHOT: one example PER LAYOUT
 │
 ├─ ∅  The info is simply NOT in the document
 │        └──► NULLABLE field (W18). A retry can't create it.
 │
 ├─ 🔁 Output sometimes breaks format, structure or arithmetic
 │        └──► VALIDATE + RETRY with: the document + the failed output + the exact error
 │
 └─ ⚖️ The source CONTRADICTS itself (line items ≠ stated total)
          └──► extract BOTH: stated_total + calculated_total + conflict_detected: true
```

### 🤔 Why you probably got it wrong
- All five symptoms look like "the extraction is inaccurate", so one generic fix (*"add more examples"*, *"use a bigger model"*, *"retry"*) feels right. The exam rewards **matching the fix to the error type**.
- The two that get confused most: **normalization rules** (fixes *formats*) vs **few-shot per layout** (fixes *where to find the value*). In the lab, deleting the rules but keeping the few-shot makes the **format** fields break again.

### 📚 Deep explanation
**1. Normalization rules** (formats):
```
Normalization rules:
- Dates → ISO 8601 (YYYY-MM-DD). Read "02/03/24" as DD/MM/YY.
- Amounts → a number without symbols or thousands separators; currency goes in `currency` (ISO 4217).
- "N/A", "—", blank → null.
```
**2. Few-shot per layout** (where the value lives): one short, targeted example for each layout that fails (typed invoice, scanned receipt, handwritten form). Targeted beats random samples.

**3. Validate + retry** (slips): check the output in **code** (schema, date validity, totals add up), then retry with all three ingredients:
```
Here is the document:        <document>
Your previous extraction:    <json>
Validation error:            invoice_date "2024-13-05" is not a valid date (month 13).
Re-read the date in the document and fix only what the error describes.
```

| 🔁 A retry CAN fix | 🚫 A retry CANNOT fix |
|---|---|
| Format slips (bad date format) | Info **absent** from the source → nullable |
| Structure slips (missing field, wrong type) | A source that **contradicts itself** → both values + conflict flag |
| Arithmetic slips | |

> ⚠️ Lab `d4/04` exercise 3: retrying with "stated_total is required" on a document that has none → the model **invents a number**.

**4. Schema ≠ truth.** A tool schema / structured output guarantees the **shape** (syntax), not correct **values** (semantics). Semantic validation (totals, real dates, IDs that exist) is still your job.

### 🪤 Traps
- 🪤 "Add more few-shot examples" for **format** errors. → rules.
- 🪤 "Add normalization rules" for **layout** errors. → per-layout examples.
- 🪤 "Retry until the field appears." → nullable.
- 🪤 "Pick the stated total, it's authoritative." → keep both + flag.
- 🪤 Retry with only "try again" (no document, no failed output, no error).

### 🎯 Exam pattern
**Formats → rules. Layouts → one example each. Absent → null. Slips → retry with doc + output + error. Contradictions → both + flag.**

### 📖 Official reading (~30 min)
| Page | Section | Look for |
|---|---|---|
| [Structured outputs](https://platform.claude.com/docs/en/build-with-claude/structured-outputs) | *Why use structured outputs* · *How it works* · *Important considerations → Invalid outputs* | Shape guaranteed, values not |
| [Prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices#use-examples-effectively) | *Use examples effectively* · *Structure prompts with XML tags* · *Long context prompting* | Diverse, targeted examples; doc-in-XML |
| [Reduce hallucinations](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations) | Whole page | Allowing "I don't know", grounding in quotes |
| [Increase output consistency](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/increase-consistency) | Whole page | Precise format specs, examples |

### 🔧 Lab drill
`python d4-prompting/03_normalization_fewshot.py`: schema only → + rules → + per-layout few-shot. Do exercise 1 (remove rules, keep few-shot). Then `python d4-prompting/04_validation_retry.py`, including exercise 3.

### 🧠 Memory line
**Diagnose, then treat: formats → rules · layouts → examples · absent → null · slips → retry with the error · conflicts → keep both.**

### 🏁 Self-check
<details><summary>Q1. Totals are right on PDFs but missing on phone-photo receipts, where the total sits at the bottom under "AMOUNT DUE". Best fix?</summary>

**A few-shot example for the receipt-photo layout** showing where the total is. It's a layout problem, not a format problem.
</details>

<details><summary>Q2. Dates come back as "3/2/24", "March 2, 2024" and "2024-03-02". Best fix?</summary>

**Normalization rules**: ISO 8601, with an explicit rule for how to read the ambiguous `D/M/YY` form.
</details>

---

## W18 · 🟧 O26 · Nullable fields, `unclear` and `other` enums · you scored 33%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟧 33% | D4 | S6 | `d4/02` |

### 📘 Understand it first

> 📖 **Definition · Nullable fields and catch-all enum values**
> A **nullable** (or optional) field may legitimately have **no value** (`null`). An **enum** restricts a field to a fixed list of values; adding **`unclear`** covers values that are present but can't be classified, and **`other`** (with a detail field) covers clear values that aren't on the list.

**🧭 What it is, in plain words**

A schema is a set of demands. A **required string** says "you must write some text here". When the document genuinely has no due date, Claude still has to satisfy the schema, so it writes *something*: a guess, a placeholder, a plausible-looking date. The schema forced the fabrication.

A **closed enum** has the same effect for categories. If the only options are `net_30`, `net_60` and `on_receipt`, and the contract says "payment due upon mutual agreement", Claude must pick one of the three, all of which are wrong.

The fix is to give the schema **honest exits** that match real-world situations:
- **Absent** → `null` (with a description saying *when* to use it: "null if the document doesn't state one").
- **Present but ambiguous** → `unclear`, plus the raw text in a detail field so a person can resolve it.
- **Clear, but not on the list** → `other`, plus a detail field naming it.

Each exit answers a different question, which is how you tell them apart.

**⚙️ How it works**
```
 Is the value in the document?
 │
 ├─ NO ───────────────────────────────────────► null
 └─ YES → Can you tell which category it is?
          ├─ NO ──────────────────────────────► "unclear"  + terms_detail: "<raw text>"
          └─ YES → Is that category on the list?
                   ├─ YES ────────────────────► that enum value
                   └─ NO ─────────────────────► "other"    + terms_detail: "<what it is>"
```

**🏠 Analogy: a paper form**
> A form with a mandatory "Middle name" box makes people without a middle name write "N/A" or invent one. A good form has **"none"** as an option (null), a **"not sure"** box (unclear), and **"Other: ____"** (other + detail).

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **Required field** | Must be present with a value; forces output even when the source is silent |
| **Nullable field** | Type includes `null`, e.g. `"type": ["string", "null"]` |
| **Optional field** | May be omitted entirely |
| **Enum** | A fixed list of allowed values |
| **Closed-world enum** | Assumes the list is complete |
| **Open-world** | Real values may fall outside any list you write |
| **Detail field** | Free-text companion that stores the raw evidence for `unclear` / `other` |

### 💡 The rule, in one picture
**Required fields make the model invent values.** Give the schema honest exits:

```
 Might the info be ABSENT from the document?       → ∅  nullable / optional field
 Is it PRESENT but AMBIGUOUS?                      → ❓ "unclear"  (+ raw text in a detail field)
 Can the category list never be complete?          → ➕ "other"    (+ a detail string)
```

### 🤔 Why you probably got it wrong (33%)
- "Required = complete data" is a natural instinct for a data engineer. With an LLM, `required` means *"you must output something"*, so it outputs **something plausible**.
- `unclear` vs `other` vs `null` blur together. Separate them by the question each one answers:

| Value | Answers | Example |
|---|---|---|
| `null` | "Is it **in** the document?" → no | No due date anywhere |
| `"unclear"` | "It's there, but **which** category?" → can't tell | "Payment due upon mutual agreement" |
| `"other"` | "It's clear, but **not on my list**" | "Net 45" when the enum has net_30 / net_60 / on_receipt |

### 📚 Deep explanation: the lab invoice
No due date anywhere; the terms say *"Payment due upon mutual agreement"*.

| Schema | Output | Verdict |
|---|---|---|
| **A:** `due_date` required string · `terms` closed enum `[net_30, net_60, on_receipt]` | `due_date: "<UNKNOWN>"` · `terms: "on_receipt"` | 😱 Invented |
| **B:** `due_date` nullable · `terms` enum + `unclear` + `other` · `terms_detail` | `due_date: null` · `terms: "unclear"` · `terms_detail: "Payment due upon mutual agreement"` | ✅ Honest |

```json
"due_date":     { "type": ["string", "null"], "description": "ISO date, or null if the document doesn't state one" },
"terms":        { "type": "string", "enum": ["net_30", "net_60", "on_receipt", "unclear", "other"] },
"terms_detail": { "type": ["string", "null"], "description": "Raw text when terms is unclear or other" }
```
- The **description** of a nullable field should say *when* to use null ("if the document doesn't state one"). That's part of the fix.
- The **detail** field keeps the raw evidence, so a human or downstream rule can resolve it later.

### 🪤 Traps
- 🪤 Required everything + "write N/A if missing" (then "N/A" pollutes typed columns).
- 🪤 Retrying until the model "finds" the field.
- 🪤 A closed enum for open-world categories.
- 🪤 `other` used for *ambiguous* (that's `unclear`).

### 🎯 Exam pattern
**Absent → null. Ambiguous → `unclear` + raw text. Open-ended → `other` + detail.**

### 📖 Official reading (~15 min)
| Page | Section | Look for |
|---|---|---|
| [Structured outputs](https://platform.claude.com/docs/en/build-with-claude/structured-outputs) | *JSON Schema limitations* · *Using a raw JSON schema* | Nullable types, enums supported |
| [Strict tool use](https://platform.claude.com/docs/en/agents-and-tools/tool-use/strict-tool-use) | Whole page | Schema-valid tool inputs |
| [Reduce hallucinations](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations) | "Allow Claude to say I don't know" | The idea behind null / unclear |

### 🔧 Lab drill
`python d4-prompting/02_schema_nullable_enums.py`: run schema A and schema B on the same invoice.

### 🧠 Memory line
**Not there → null. Can't tell → unclear. Not on the list → other.**

### 🏁 Self-check
<details><summary>Q1. A contract says "Governed by the laws of the Isle of Man". Your <code>jurisdiction</code> enum is [US, UK, EU]. Which value?</summary>

**`other`**, with `jurisdiction_detail: "Isle of Man"`. It's clear, just not on the list. (Not `unclear`, and not `UK`.)
</details>

---

## W19 · 🟨 O23 · Sync API vs Message Batches · you scored 75%

### 🎯 Score card
| Score | Domain | Scenarios | Lab |
|---|---|---|---|
| 🟨 75% | D4 | S5 · S6 | `d4/05` |

### 📘 Understand it first

> 📖 **Definition · Synchronous API vs Message Batches API**
> The **synchronous Messages API** answers each request immediately, in seconds. The **Message Batches API** accepts a large set of requests at once, processes them **asynchronously within up to 24 hours**, at **50% of the standard price**, and returns results you match back by each request's **`custom_id`**.

**🧭 What it is, in plain words**

Both APIs run the same models on the same prompts. They differ in **when** you get the answer and **what it costs**:
- **Synchronous:** you send a request, you wait, you get the reply. Use it whenever a person or a process is **waiting** on the answer: a chat, a pre-merge check, a tool loop.
- **Batches:** you submit, say, 80,000 requests in one go and walk away. Anthropic processes them when capacity allows; most batches finish well within a day, but there's **no latency guarantee** beyond the 24-hour window. In exchange, it's half price.

Because results arrive as a set, and **not necessarily in submission order**, every request carries your own **`custom_id`** (a ticket ID, a file name), which is how you join results back to inputs. Some requests in a batch can fail or expire while others succeed; you fix and **resubmit only those**.

One structural limit: a batch request is a single request → single response. A workflow that needs to call tools and feed results back (multi-turn agentic loops) doesn't fit inside one batch request.

**⚙️ How it works**
```
 ⚡ SYNC     request ─► (seconds) ─► response              someone waiting · tool loops
 📦 BATCH    [req custom_id=T1, T2 … T80000] ─► submit ─► ⏳ up to 24 h ─► results (any order)
                                                                         │
                                         join by custom_id ◄─────────────┘
                                         resubmit only errored/expired IDs
```

**🏠 Analogy: post office**
> **Sync** is a courier you stand next to while they deliver. **Batch** is bulk mail: much cheaper, it arrives by tomorrow, not necessarily in the order you posted it, and each envelope has a **reference number** so you know which reply belongs to which letter.

**🔤 Key terms**
| Term | Meaning |
|---|---|
| **Synchronous** | Caller waits for the response |
| **Asynchronous** | Submit now, collect results later |
| **Message Batches API** | Bulk asynchronous processing, ≤ 24 h, 50% discount |
| **`custom_id`** | Your identifier for each batch request; used to match results |
| **Latency SLA** | A guaranteed maximum response time (batches don't offer one beyond the 24 h window) |
| **Partial failure** | Some batch requests error or expire while others succeed |

### 💡 The rule, in one picture
**Someone is waiting → sync. Nobody is waiting and cost matters → batch.**

| | ⚡ Sync Messages API | 📦 Message Batches API |
|---|---|---|
| Latency | Seconds | **Up to 24 h** (most finish sooner), no latency SLA |
| Cost | Standard | **50% off** |
| Use for | **Blocking**: pre-merge checks, a user waiting | **Overnight, weekly**, backfills, evals |
| Result order | n/a | **Not guaranteed** → match by **`custom_id`** |
| Failures | Retry the call | Resubmit **only the failed `custom_id`s**, with a fix |
| Tool use | Multi-turn loops | **No tool round trips** inside one request |

### 🤔 Why you lost the 25%
Most likely one of: (a) choosing batch for a **blocking** check "because it's cheaper"; (b) assuming results return **in order**; (c) resubmitting the **whole** batch; (d) the **SLA math**.

### 📚 Deep explanation
- **SLA math:** you need results by 08:00 and a batch can take up to 24 h → submit by **08:00 the previous day**, or use sync.
- **`custom_id`** is your join key. Every request gets a unique one; results are matched by it, never by position.
- **Partial failure:** a batch can end with some requests `errored` or `expired`. Fix the cause (for example, chunk the oversized document) and resubmit **only those**.
- **Agentic loops don't fit:** a batch request is one request → one response. A workflow that needs tool results fed back needs the sync API, or one batch per round.

### 🪤 Traps
- 🪤 Batch for a pre-merge gate. · 🪤 Results by position. · 🪤 Resubmit everything. · 🪤 `--batch` flag in Claude Code ❌ (Batches is an **API**, not a CLI flag).

### 🎯 Exam pattern
**Blocking → sync. Overnight/weekly/cost → batch, `custom_id`, resubmit only failures.**

### 📖 Official reading (~15 min)
| Page | Section | Look for |
|---|---|---|
| [Batch processing](https://platform.claude.com/docs/en/build-with-claude/batch-processing) | *How the Message Batches API works* · *Batch limitations* · *Pricing* · *Retrieving batch results* · *Best practices for effective batching* | 24 h, 50%, `custom_id`, result types |

### 🔧 Lab drill
`python d4-prompting/05_batches.py --sla-only` (free), then the live run.

### 🧠 Memory line
**Waiting → sync. Overnight → batch. Join on `custom_id`. Resubmit only failures.**

---

# Part 6 · 🧩 Neighbor topics your weak spots lean on

> These have no objective number of their own on your report, but **W1, W13, W15 and W16 lean on them**. Knowing them stops you from picking a half-right answer.

## N1 · 🚧 Prerequisite gates and structured handoffs (TS 1.4) → supports W15

> 📖 **Definition:** a **prerequisite gate** is a check *inside your tool's code* that refuses an action until a required condition holds (identity verified, amount within limit), returning a structured error that tells the model what to do first. A **structured handoff** is the fixed-format summary passed to a human or another agent on escalation.
>
> 🧭 *Why it exists:* a system prompt can make a rule likely; only code makes it certain. The gate sits where the action happens, so no prompt, model mistake or injected text can skip it.

- A rule that must hold **every time** (verify identity before a refund) goes **in code**: a gate inside the tool.
- The gate returns a **structured error** the model can act on: `"Identity not verified: call get_customer first"`.
- An escalation carries a **structured handoff**: `customer_id`, root cause, amount, what was tried, recommended action.
- 🔧 `python d1-agentic/03_prerequisite_gate.py`: count violations in 5 runs with prompt-only vs gate.
- 📖 [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) (guardrails); [Agent SDK: Permissions](https://code.claude.com/docs/en/agent-sdk/permissions)

## N2 · 🪝 Agent SDK hooks (TS 1.5) → supports W1

> 📖 **Definition:** **Agent SDK hooks** are callback functions you register in your agent's code that run at lifecycle events, most importantly **before** a tool runs (PreToolUse: can allow, deny or modify the call) and **after** it returns (PostToolUse: can inspect or reshape the result the model sees).
>
> 🧭 *Why it exists:* the same idea as Claude Code hooks (W1), but in your own application. Hooks are deterministic code, so business rules and data clean-up don't depend on the model remembering an instruction.

- **PreToolUse** blocks a bad call (`permissionDecision: "deny"` + a reason). **PostToolUse** cleans tool output before the model reasons over it (Unix time → ISO date).
- ⚠️ Right matcher: the refund rule matches `process_refund`, not `lookup_order`.
- 🔧 `python d1-agentic/04_sdk_hooks.py` · 📖 [Agent SDK: Hooks](https://code.claude.com/docs/en/agent-sdk/hooks)

## N3 · 🧯 Structured errors (TS 2.2) → supports W17, W13

> 📖 **Definition:** a **structured error** is a tool result that reports failure in a machine-readable form: an error flag (`isError` / `is_error`), a **category** (transient, validation, business, permission), whether it's **retryable**, and a human-readable message.
>
> 🧭 *Why it exists:* the model decides its next move from the tool result. "Operation failed" leaves it guessing; "transient, retryable: backend timed out" tells it to retry, while "business, not retryable: past the return window" tells it to explain and escalate.

| Situation | `errorCategory` | `isRetryable` | Agent should |
|---|---|---|---|
| Backend timeout | transient | ✅ | Retry locally with backoff |
| Bad ID format | validation | ❌ | Fix the input or ask |
| Past the return window | business | ❌ | Explain, offer alternatives, escalate |
| Caller not allowed | permission | ❌ | Escalate |
| Search found nothing | **not an error** | n/a | "No order found" |
- Never return an empty list on a timeout (that **fakes success**). Never kill the whole workflow over one failed subtask: continue and **annotate the coverage gap**.
- 🔧 `python d2-tools-mcp/02_structured_errors.py` · 📖 [Handle tool calls → Handling errors with is_error](https://platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls) · [MCP: Tools spec (error handling)](https://modelcontextprotocol.io/specification/latest/server/tools)

## N4 · 🙋 Escalation (TS 5.2)

> 📖 **Definition:** **escalation** is handing a conversation from the agent to a human, triggered by explicit criteria and accompanied by a structured handoff.
>
> 🧭 *Why it exists:* agents should resolve what they can and recognize what they shouldn't. Clear triggers keep escalation consistent, neither too eager (every annoyed customer) nor too reluctant (ignoring a request for a person).

- ✅ Escalate on: an **explicit request for a human** (immediately), a **policy gap**, **no meaningful progress**.
- ❌ Not on: frustrated **sentiment** alone, or the model's **self-rated confidence**.
- Several matching customers → **ask for another identifier**; never guess.
- 🔧 `python d5-context/02_escalation.py`

---

# Part 7 · 🥊 Confusion pairs: the 18 look-alikes that cost you points

> 💡 Most of your misses are a **pair** of options where both look right. Learn the one-line separator for each pair.

| # | 🅰️ | 🅱️ | ✂️ The separator |
|---|---|---|---|
| 1 | `--allowedTools` | `--tools` / `--disallowedTools` | allowed = **approve** (no prompt). tools/disallowed = **what exists**. |
| 2 | PreToolUse | PostToolUse | Pre can **block** (exit 2). Post is **after the fact**. |
| 3 | Hook exit 1 | Hook exit 2 | Only **2** blocks. 1 = non-blocking error. |
| 4 | Deny rule | PreToolUse hook | Deny = **static known** path/command. Hook = **dynamic** content check. |
| 5 | Project `./CLAUDE.md` | `~/.claude/CLAUDE.md` | Team gets it vs **only you** get it. |
| 6 | `.claude/rules` + `paths` | Folder `CLAUDE.md` | **File type across folders** vs **one folder**. |
| 7 | Skill | CLAUDE.md | **On demand** (task) vs **always on** (convention). |
| 8 | `context: fork` | `--fork-session` | **Isolated skill context** vs **branched session, new ID**. |
| 9 | Resume | Fork | **Same ID**, continue vs **new ID**, try another path. |
| 10 | Resume + name files | Fresh + summary | Context **mostly valid** vs **mostly stale**. |
| 11 | Plan mode | Explore subagent | **Approval before edits** vs **keep verbose discovery out of context**. |
| 12 | `tool_choice: any` | `tool_choice: tool` | **Some** tool vs **this** tool. Ordering = forced on turn 1 → `auto`. |
| 13 | Grep | Glob | **Content** vs **file names**. |
| 14 | `null` / `unclear` / `other` | — | **Absent** / **ambiguous** / **not on the list**. |
| 15 | Normalization rules | Few-shot per layout | **Formats** vs **where the value is**. |
| 16 | Sync | Batch | **Someone waiting** vs **overnight + 50% off**. |
| 17 | Interacting bugs | Independent bugs | **One message, together** vs **one at a time**. |
| 18 | Procedural delegation | Goal-oriented | Known fixed pipeline vs **open-ended research** (goals + criteria). |


---

# Part 8 · 🧪 Weak-spot drill: 36 original questions

> ⏱️ **How:** 2 minutes per question. Read the **last line** of the stem first, find the deciding word, **predict the answer shape**, then read the options. Open ▶ only after you've committed. Log misses as `Q# | W# | my pick | right | rule`.
>
> 🎯 Target: **32/36** before exam day. Below 28 → re-read the W-sections of your misses and run their 🔧 drills again.

## 8.1 💻 D3 Claude Code (Q1–Q18)

**Q1** · W1 · O16
A team's Claude follows the "use `Result<T, E>` for all service functions" convention on the lead's laptop, but not for two new hires. What's the most likely cause and fix?
- A) The new hires need to run `/memory` to load it
- B) The convention is in the lead's `~/.claude/CLAUDE.md`; move it to the project `CLAUDE.md` and commit it
- C) Add it to `.claude/settings.local.json`
- D) Convert it to a skill so it loads on demand

<details><summary>▶ Answer</summary>

**B.** It works for one person only, so it lives in **user** scope. Project CLAUDE.md is committed and reaches everyone. C is a settings file (permissions and hooks, not instructions), and it isn't committed. D makes an always-on convention on-demand.
</details>

**Q2** · W1 · O16
Claude must **never** modify anything under `infra/terraform/`. Which is the most reliable control with the least machinery?
- A) "Never edit infra/terraform" in project CLAUDE.md
- B) `deny: ["Edit(infra/terraform/**)"]` in `.claude/settings.json`
- C) A PostToolUse hook that reverts changes
- D) A skill that explains the policy

<details><summary>▶ Answer</summary>

**B.** Static, known path + "never" → **deny rule**. A is a request. C runs after the damage. D is on-demand text.
</details>

**Q3** · W1 · O16
You want to block any Bash command that pipes `curl` into `sh`, wherever it appears in the command. Best mechanism?
- A) `deny: ["Bash(curl *)"]`
- B) PreToolUse hook on `Bash` that inspects the command and exits 2 with a reason
- C) PostToolUse hook on `Bash` that exits 2
- D) PreToolUse hook that exits 1

<details><summary>▶ Answer</summary>

**B.** A **dynamic content** check before the action → PreToolUse, **exit 2**. A blocks all curl, which is too broad, and doesn't catch other shapes. C is too late. D doesn't block.
</details>

**Q4** · W1 · O16
`settings.json` (team) denies `Read(./secrets/**)`. A developer adds `allow: ["Read(./secrets/dev.json)"]` to `settings.local.json`. Claude tries to read `secrets/dev.json`. Result?
- A) Allowed, because local settings override project settings
- B) Prompted, because the rules conflict
- C) Refused, because deny wins over allow in any file
- D) Allowed, because the more specific rule wins

<details><summary>▶ Answer</summary>

**C.** **Deny beats everything**, from any settings file.
</details>

**Q5** · W1 · O16
Conventions for SQL files should apply only to `*.sql` files, which live in 12 different service folders. Best mechanism?
- A) A `CLAUDE.md` in each of the 12 folders
- B) `.claude/rules/sql.md` with `paths: ["**/*.sql"]`
- C) `.claude/rules/sql.md` with `paths: ["*.sql"]`
- D) Append it to the root CLAUDE.md

<details><summary>▶ Answer</summary>

**B.** File type across folders → rule with `paths` and **`**`**. C only matches the root folder and fails silently. A duplicates. D is always loaded.
</details>

**Q6** · W2 · O14
`/survey-endpoints` reads every route file and prints them, filling the main context. The team still wants the final table in the main conversation. Best change?
- A) Run `/compact` after it
- B) Add `context: fork` to the skill's frontmatter
- C) Move the skill into CLAUDE.md
- D) Add `argument-hint`

<details><summary>▶ Answer</summary>

**B.** Verbose skill → isolated fork; only the result comes back. A loses detail after the fact. C makes it always-on. D doesn't isolate anything.
</details>

**Q7** · W2 · O14
After adding `context: fork`, `/survey-endpoints` now says "No directory specified", although the user named `services/api` earlier in the chat. Why?
- A) Forked skills can't take arguments
- B) The fork sees only the skill text and its arguments, not the conversation
- C) `argument-hint` is missing
- D) The fork's CLAUDE.md is cached

<details><summary>▶ Answer</summary>

**B.** Make the skill self-contained: require `$ARGUMENTS`.
</details>

**Q8** · W3 · O8
"`formatPrice` shows `NaN` when `price` is a string; add `Number()` coercion." Best workflow?
- A) Plan mode, then approve
- B) Direct execution
- C) Explore subagent first
- D) Multi-phase with checkpoints

<details><summary>▶ Answer</summary>

**B.** One-sentence diff, clear cause.
</details>

**Q9** · W3 · O8
"Introduce feature flags across the checkout flow; there are three possible libraries, and the tech lead must agree the approach first." Best workflow?
- A) Direct execution with a detailed prompt
- B) Plan mode: explore, propose, lead approves, then execute
- C) Write it in CLAUDE.md and let Claude decide
- D) An Explore subagent that implements it

<details><summary>▶ Answer</summary>

**B.** Several approaches + sign-off + multi-file.
</details>

**Q10** · W4 · O12
"Convert legacy product codes to the new format" yields a different output style every run. What's most effective?
- A) A longer prose description of the format
- B) 2–3 concrete input → output examples
- C) Run it 3 times and take the majority
- D) Switch to plan mode

<details><summary>▶ Answer</summary>

**B.** Inconsistent interpretation → **examples**.
</details>

**Q11** · W4 · O12
Two bugs: the CSV parser drops quoted commas, and the row validator then rejects the shortened rows. Fixing either alone shifts the other's behavior. Best prompt strategy?
- A) Fix the parser in one session, the validator in another
- B) One detailed message describing both bugs and how they interact
- C) Fix the validator first, since it reports the error
- D) Ask Claude to interview you

<details><summary>▶ Answer</summary>

**B.** Interacting bugs → together.
</details>

**Q12** · W4 · O12
You're asking Claude to build a pharmacy dose-rounding rule, and you're not sure of all the edge cases yourself. Best first step?
- A) Write the code, then add tests
- B) Ask Claude to interview you about requirements and edge cases before writing code
- C) Paste a long spec
- D) Use plan mode

<details><summary>▶ Answer</summary>

**B.** Unfamiliar domain, unclear requirements → **interview pattern**.
</details>

**Q13** · W5 · O13
A CI review must apply the team's standards, must not modify code, and must produce findings a script can post as PR comments. Which combination?
- A) Standards in the CI prompt · "do not edit" in the prompt · ask for JSON
- B) Standards in project CLAUDE.md · `--tools "Read,Grep,Glob"` · `--output-format json --json-schema ...`
- C) Standards in `~/.claude/CLAUDE.md` · `--allowedTools "Read"` · regex the output
- D) Standards in a skill · `--bare` · `--output-format text`

<details><summary>▶ Answer</summary>

**B.** All three pillars as mechanisms. C: user scope doesn't reach CI, and `--allowedTools` approves rather than restricts. D: `--bare` skips CLAUDE.md.
</details>

**Q14** · W5 · O13
Each push re-posts findings that developers already fixed or dismissed. Best fix?
- A) Lower `--max-turns`
- B) Pass prior findings into the re-run and report only new or still-unaddressed issues
- C) Run the review only on the first push
- D) Batch the reviews nightly

<details><summary>▶ Answer</summary>

**B.**
</details>

**Q15** · W6 · O15
Generated unit tests keep repeating the happy-path cases already in `test_cart.py`. Best fix?
- A) Ask for "novel" tests
- B) Include the existing tests with "do not duplicate", and put test standards (edge cases, fixtures) in project CLAUDE.md
- C) Request 3× as many tests
- D) Use `--bare` for speed

<details><summary>▶ Answer</summary>

**B.**
</details>

**Q16** · W7 · O11
A headless job must never wait on a permission prompt, must be able to edit files, and must stop after 10 turns. Flags?
- A) `-p --permission-mode dontAsk --allowedTools "Edit" --max-turns 10`
- B) `-p --dangerously-skip-permissions` and "stop after 10 turns" in the prompt
- C) `-p --tools "Edit" --batch`
- D) `CLAUDE_HEADLESS=1 --max-turns 10`

<details><summary>▶ Answer</summary>

**A.** B bypasses safety and uses words for the cap. C's `--batch` and D's env var are invented.
</details>

**Q17** · W7 · O11
Which flag makes `Write` **not exist** for the run?
- A) `--allowedTools "Read,Grep"`
- B) `--disallowedTools "Write"`
- C) `--permission-mode plan`
- D) `--append-system-prompt "never write"`

<details><summary>▶ Answer</summary>

**B** (or `--tools` without Write). A only pre-approves Read and Grep; Write still exists.
</details>

**Q18** · W8 · O30
The review bot flags every `console.log` in `scripts/`, where it's intentional. Developers have started ignoring the bot. Best approach?
- A) Add "be conservative" to the prompt
- B) Add an accepted-pattern entry and an explicit don't-report category in project CLAUDE.md; temporarily disable the noisy category until the criteria are fixed
- C) Only report findings with confidence ≥ 0.9
- D) Add a second model to filter the findings

<details><summary>▶ Answer</summary>

**B.** Explicit, persistent criteria. A and C don't move precision. D is heavy machinery.
</details>

## 8.2 🔍 Exploration and context (Q19–Q22)

**Q19** · W9 · O32
"List every `*.graphql` file in the monorepo." First tool?
- A) Grep · B) Glob · C) Read · D) Bash `find`

<details><summary>▶ Answer</summary>

**B.** File names → Glob.
</details>

**Q20** · W9 · O17
You need to understand how `refundOrder` flows through a 900-file repo. Most efficient approach?
- A) Read every file in `src/`
- B) Grep for `refundOrder`, Read only the hits, follow callers and callees with more Greps, and note facts with file:line
- C) Glob `**/*.ts` and read them all
- D) Ask Claude to guess from file names

<details><summary>▶ Answer</summary>

**B.**
</details>

**Q21** · W9 · O32
Edit fails: `enabled: false` occurs 4 times in `config.yaml`. Best next step?
- A) Retry the same Edit
- B) Use a longer, unique anchor including the parent key, or Read the file and Write it back
- C) `sed -i` via Bash
- D) Delete the file and recreate it from memory

<details><summary>▶ Answer</summary>

**B.**
</details>

**Q22** · W10 · O20
In a long investigation, Claude must keep 15 exact `file:line` references across `/compact` and possibly `/clear`. Best technique?
- A) Trust `/compact` with a focus instruction
- B) Append confirmed facts to a notes file as you go and read it back after compacting or clearing
- C) Use a bigger model
- D) Never compact

<details><summary>▶ Answer</summary>

**B.** Exact facts → scratchpad file.
</details>

## 8.3 🤖 Agentic (Q23–Q29)

**Q23** · W11 · O1
A support agent fetches profile, orders and loyalty status one per turn. All three take only `customer_id`. Best improvement?
- A) A composite `get_all_customer_data` tool
- B) Let Claude emit all three `tool_use` blocks in one turn and return all three results in one user message
- C) Pre-fetch all three before every conversation
- D) Three separate subagents

<details><summary>▶ Answer</summary>

**B.**
</details>

**Q24** · W11 · O1
Your loop receives 2 `tool_use` blocks. How do you send the results?
- A) Two user messages, one per result
- B) One user message with both `tool_result` blocks, each with its `tool_use_id`
- C) One assistant message with both results
- D) Concatenate both into one text block

<details><summary>▶ Answer</summary>

**B.**
</details>

**Q25** · W12 · O2
Yesterday's session mapped the payments module. Today only `refund.ts` changed. Best approach?
- A) Resume and say "files changed, re-analyze everything"
- B) Resume and say "Only refund.ts changed (it now supports partial refunds); re-read it and update the risk list"
- C) Start fresh with no context
- D) Fork the session

<details><summary>▶ Answer</summary>

**B.** Mostly valid → resume + **name** the change.
</details>

**Q26** · W12 · O2
What is true of `--fork-session` used with `--resume`?
- A) It reuses the original session ID
- B) It creates a new session ID with the history up to that point
- C) It deletes the original session
- D) It starts with an empty history

<details><summary>▶ Answer</summary>

**B.**
</details>

**Q27** · W13 · O3
A synthesis subagent keeps writing "not provided" for facts the search subagents found. Most likely cause?
- A) The synthesizer's model is too small
- B) The coordinator didn't include those findings (with sources) in the synthesizer's prompt
- C) The synthesizer needs the search tool
- D) The subagents' histories weren't merged

<details><summary>▶ Answer</summary>

**B.** Subagents see only their prompt. D describes an invented mechanism.
</details>

**Q28** · W14 · O4
A market-research system's coordinator sends: "1) search Germany 2) search France 3) summarize." Stakeholders asked for "EU-wide". The report covers 2 countries. Fix?
- A) Improve the summarizer's prompt
- B) Rewrite delegation as a goal with coverage and quality criteria ("all EU markets with material activity; ≥ 2 sources each; flag gaps")
- C) Add a QA agent at the end
- D) Add steps 4–29 for each country

<details><summary>▶ Answer</summary>

**B.** Fix the first broken layer, with goals rather than steps. D is still procedural and brittle.
</details>

**Q29** · W16 · O33
The synthesizer has 15 tools, including web search, and often searches instead of writing. Best fix?
- A) Prompt: "do not search"
- B) Restrict it to its role's tools plus a narrow `verify_fact` tool
- C) Remove every tool from the synthesizer
- D) Raise its `max_tokens`

<details><summary>▶ Answer</summary>

**B.** C goes too far: it then can't verify a single claim without a coordinator round trip.
</details>

## 8.4 🛠️ Tools (Q30–Q31)

**Q30** · W15 · O37
`load_schema` must run before any other tool, every time. Then Claude should work freely and finish. Which `tool_choice` strategy?
- A) `auto` with "always call load_schema first" in the system prompt
- B) Forced `{"type":"tool","name":"load_schema"}` on the first turn, then `auto`
- C) Forced `load_schema` on every turn
- D) `any` on every turn

<details><summary>▶ Answer</summary>

**B.** A is words. C never finishes. D guarantees a tool, not *that* tool, and never finishes either.
</details>

**Q31** · W15 · O37
An extractor must always return structured output via a tool, and there are 4 document-type tools. Type is unknown in advance. Which `tool_choice`?
- A) `auto` · B) `any` · C) forced `invoice_tool` · D) `none`

<details><summary>▶ Answer</summary>

**B.**
</details>

## 8.5 📄 Extraction and API mode (Q32–Q36)

**Q32** · W17 · O29
Amounts arrive as "€1.200,50", "1,200.50 EUR" and "1200.5". Best fix?
- A) A few-shot example per layout
- B) Normalization rules: plain number, `.` decimal, currency in its own ISO field
- C) Retry until consistent
- D) A bigger model

<details><summary>▶ Answer</summary>

**B.** Formats → rules.
</details>

**Q33** · W17 · O29
Line items sum to 940, but the document states "Total: 960". What should the extraction do?
- A) Output 940, the computed value
- B) Output 960, the stated value
- C) Output `stated_total: 960`, `calculated_total: 940`, `conflict_detected: true`
- D) Retry until they match

<details><summary>▶ Answer</summary>

**C.**
</details>

**Q34** · W17 · O29
Validation finds `invoice_date: "2024-02-30"`. What should the retry prompt contain?
- A) "Try again."
- B) The document, the failed output, and the exact error ("Feb 30 is not a valid date")
- C) Only the error
- D) A larger `max_tokens`

<details><summary>▶ Answer</summary>

**B.**
</details>

**Q35** · W18 · O26
A lease may or may not state a renewal date. Schema design?
- A) `renewal_date` required string; instruct "write NONE if missing"
- B) `renewal_date` nullable, with a description saying when to use null
- C) Retry until a date is found
- D) Drop the field

<details><summary>▶ Answer</summary>

**B.**
</details>

**Q36** · W19 · O23
Nightly re-scoring of 80,000 support tickets; results are needed by 09:00 tomorrow; cost matters. Approach?
- A) Sync API with high concurrency
- B) Message Batches with a `custom_id` per ticket, submitted early enough for the 24 h window; resubmit only failures
- C) Message Batches, matching results by position
- D) Claude Code `--batch`

<details><summary>▶ Answer</summary>

**B.** C is wrong because order isn't guaranteed. D is invented.
</details>

### 📊 Score yourself
| Score | Meaning | Do next |
|---|---|---|
| 34–36 | 🟢 Ready on your weak spots | Cram sheet (Part 10) only |
| 30–33 | 🟡 Nearly there | Re-read the W-sections of your misses |
| < 30 | 🔴 Not yet | Re-run the 🔧 drills for each missed W, then retake in 48 h |

---

# Part 9 · 📖 Official reading library, by objective

> 🎯 **How to read:** open the page, jump to the named section, and read with the question *"what would the exam test here?"* Don't read whole doc sites. ⏱️ Total ≈ 5 h if you do it all.

## 💻 Claude Code (code.claude.com/docs)
| Objective | Page | Sections to read |
|---|---|---|
| O16 · O15 · O30 | [Memory (CLAUDE.md)](https://code.claude.com/docs/en/memory) | Choose where to put CLAUDE.md files · Import additional files · How CLAUDE.md files load · Organize rules with `.claude/rules/` · Write effective instructions · Troubleshoot memory issues |
| O16 | [Explore the .claude directory](https://code.claude.com/docs/en/claude-directory) | Interactive map of every file |
| O16 · O14 | [Skills](https://code.claude.com/docs/en/skills) | Choose where skills load · Resolve skills that share a name · Frontmatter reference · Pre-approve tools for a skill · Pass arguments to skills · Run skills in a subagent |
| O16 | [Permissions](https://code.claude.com/docs/en/permissions) | Permission system · Permission rule syntax · Read and Edit · Bash · Extend permissions with hooks · Settings precedence |
| O11 · O8 | [Permission modes](https://code.claude.com/docs/en/permission-modes) | All modes, especially plan and dontAsk |
| O16 | [Hooks reference](https://code.claude.com/docs/en/hooks) | Hook lifecycle · Matcher patterns · Exit code output · JSON output · PreToolUse · PostToolUse |
| O16 | [Hooks guide](https://code.claude.com/docs/en/hooks-guide) | Worked examples |
| O16 | [Settings](https://code.claude.com/docs/en/settings) | Settings files and scope |
| O11 · O13 | [CLI reference](https://code.claude.com/docs/en/cli-reference) | CLI flags table: `-p`, `--output-format`, `--json-schema`, `--max-turns`, `--max-budget-usd`, `--permission-mode`, `--tools`, `--allowedTools`, `--disallowedTools`, `--bare`, `--resume`, `--fork-session` |
| O11 · O13 | [Headless / programmatic](https://code.claude.com/docs/en/headless) | Basic usage · Start faster with bare mode · Get structured output · Auto-approve tools · Turn off permission prompts in unattended runs · Continue conversations |
| O13 | [GitHub Actions](https://code.claude.com/docs/en/github-actions) | Setup and configuration |
| O8 · O12 · O15 · O17 | [Common workflows](https://code.claude.com/docs/en/common-workflows) | Understand new codebases · Fix bugs efficiently · Work with tests · Resume previous conversations · Plan before editing · Delegate research to subagents |
| O8 · O12 · O13 · O20 | [Best practices](https://code.claude.com/docs/en/best-practices) | Give Claude a way to verify its work · Explore first, then plan, then code · Let Claude interview you · Manage context aggressively · Use subagents for investigation · Add an adversarial review step |
| O2 | [Manage sessions](https://code.claude.com/docs/en/sessions) | Resume a session · What a resumed session restores · Name your sessions · Branch a session · Manage context within a session |
| O3 · O14 · O33 | [Subagents](https://code.claude.com/docs/en/sub-agents) | Built-in subagents · Frontmatter reference · Control subagent capabilities · Manage subagent context · Choose between subagents and main conversation |
| O17 · O32 | [Tools reference](https://code.claude.com/docs/en/tools-reference) | Grep, Glob, Read, Edit, Write; Glob tool behavior |
| O20 | [Explore the context window](https://code.claude.com/docs/en/context-window) | Interactive simulation |
| O11 | [Costs](https://code.claude.com/docs/en/costs) | Budget and usage |

## 🐍 Agent SDK (code.claude.com/docs/en/agent-sdk)
| Objective | Page | Read |
|---|---|---|
| O2 | [Sessions](https://code.claude.com/docs/en/agent-sdk/sessions) | `resume`, `fork_session`, session IDs |
| O3 · O33 | [Subagents](https://code.claude.com/docs/en/agent-sdk/subagents) | Context and tools per subagent |
| N2 | [Hooks](https://code.claude.com/docs/en/agent-sdk/hooks) | PreToolUse deny, PostToolUse |
| N1 | [Permissions](https://code.claude.com/docs/en/agent-sdk/permissions) | `allowedTools`, permission modes |
| — | [Overview](https://code.claude.com/docs/en/agent-sdk/overview) | Orientation |

## 🔌 Claude API (platform.claude.com/docs)
| Objective | Page | Read |
|---|---|---|
| O1 | [Parallel tool use](https://platform.claude.com/docs/en/agents-and-tools/tool-use/parallel-tool-use) | Execution semantics · Maximizing parallel tool use · Disable parallel tool use · Troubleshooting |
| O1 · N3 | [Handle tool calls](https://platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls) | Handling results from client tools · Handling errors with is_error |
| O37 · O33 | [Define tools](https://platform.claude.com/docs/en/agents-and-tools/tool-use/define-tools) | Best practices for tool definitions · Forcing tool use |
| O37 · O26 | [Strict tool use](https://platform.claude.com/docs/en/agents-and-tools/tool-use/strict-tool-use) | Whole page |
| O37 | [Tool use overview](https://platform.claude.com/docs/en/agents-and-tools/tool-use/overview) | The loop |
| O37 | [Handling stop reasons](https://platform.claude.com/docs/en/build-with-claude/handling-stop-reasons) | `tool_use`, `end_turn`, `max_tokens` |
| O26 · O29 | [Structured outputs](https://platform.claude.com/docs/en/build-with-claude/structured-outputs) | How it works · JSON Schema limitations · Invalid outputs |
| O23 | [Batch processing](https://platform.claude.com/docs/en/build-with-claude/batch-processing) | How it works · Limitations · Pricing · Retrieving results · Best practices |
| O12 · O29 · O30 · O3 · O4 | [Prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) | Be clear and direct · Use examples effectively · Structure prompts with XML tags · Long context prompting · Optimize parallel tool calling · Research and information gathering · Subagent orchestration |
| O26 · O29 | [Reduce hallucinations](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations) | Whole page |
| O29 · O30 | [Increase output consistency](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/increase-consistency) | Whole page |

## 🧠 Anthropic Engineering essays (the "why" behind the guide)
| Objective | Essay | Why read it |
|---|---|---|
| Part 1 · O4 | [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) | Workflows vs agents; orchestrator-workers; start simple |
| O3 · O4 · O1 | [How we built our multi-agent research system](https://www.anthropic.com/engineering/multi-agent-research-system) | Delegation failures, parallel subagents, scaling effort |
| O33 · N3 | [Writing tools for agents](https://www.anthropic.com/engineering/writing-tools-for-agents) | Tool selection, scoping, descriptions, error messages |
| O20 · O3 | [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) | Compaction, note-taking, sub-agent context isolation |

## 🔗 MCP and courses
| Topic | Link |
|---|---|
| MCP server concepts (tools, resources, prompts) | [modelcontextprotocol.io: Server concepts](https://modelcontextprotocol.io/docs/learn/server-concepts) |
| MCP tools spec (incl. error results) | [Specification: Tools](https://modelcontextprotocol.io/specification/latest/server/tools) |
| Claude Code + MCP | [Connect Claude Code to tools via MCP](https://code.claude.com/docs/en/mcp) |
| Free courses (Claude Code 101, Claude Code in Action, …) | [Anthropic Academy](https://academy.claude.com/) |

---

# Part 10 · 🌙 One-page weak-spot cram sheet

```
💻 D3 ─────────────────────────────────────────────────────────────────────────────
O16  ALWAYS→CLAUDE.md (team ./ · me ~/.claude) · FILE TYPE→rules+paths+** · TASK→skill
     NEVER→deny (beats any allow, any file) · CHECK BEFORE→PreToolUse EXIT 2 (1 ≠ block)
     AFTER→PostToolUse · hook "allow" can't beat deny · new hire missing it → user scope
O14  verbose skill → context: fork · fork sees ONLY skill text + $ARGUMENTS → self-contained
     ⚖️ argument-hint = prompts for missing params (guide) · Explore/Plan forks skip CLAUDE.md
O8   one-sentence diff + clear cause → DIRECT · multi-file/architectural/options/sign-off
     → PLAN → approve → execute · huge → phases · verbose discovery → Explore subagent
O12  inconsistent → 2–3 I/O examples · checkable → tests first · wrong → exact failure
     interacting → ONE message · independent → one at a time · unfamiliar → interview
O13  standards in PROJECT CLAUDE.md · --tools "Read,Grep,Glob" + dontAsk · --json-schema
     → structured_output · prior findings on re-run · independent reviewer instance
O15  existing tests in prompt ("don't duplicate") + test standards in project CLAUDE.md
O11  -p · --output-format json · --max-turns (exits with error) · --max-budget-usd
     dontAsk = prompts become denials · --allowedTools APPROVES · --tools/--disallowedTools RESTRICT
O30  explicit report/skip lists + accepted patterns + severity examples, PERSISTED in
     project CLAUDE.md · noisy category → disable temporarily · NOT "be conservative"
O17  Grep/Glob → Read only hits → follow the chain → note file:line → Explore if huge
O32  content→Grep · names→Glob · non-unique Edit → longer anchor, or Read + Write
O20  exact facts→scratchpad file · verbose→subagent · gist→/compact <focus> · crash→manifest

🤖 D1 ─────────────────────────────────────────────────────────────────────────────
O1   independent → ONE turn, N tool_use → ALL tool_results in ONE user message (by id)
     dependent → sequence · coordinator spawns independent subagents in one response
O2   mostly valid → RESUME + name changed files · stale → FRESH + structured summary
     two approaches → FORK (NEW session id) · resume keeps the SAME id
O3   subagent sees ONLY its prompt → goal + criteria + complete findings + sources, as data
O4   delegate GOALS + coverage + quality bar, not steps · missing topics → fix coordinator

🛠️ D2 ─────────────────────────────────────────────────────────────────────────────
O37  auto = may answer in text · any = SOME tool · tool = THIS tool
     run X first → forced on turn 1, then auto · forced every turn → never ends
     ⚖️ newest models 400 on forced; exam answer is still forced tool_choice
O33  4–5 tools per role + ONE scoped cross-role tool (verify_fact) · constrain in code/config
     ⚖️ coordinator can't spawn → allowedTools must include "Task"

📄 D4 ─────────────────────────────────────────────────────────────────────────────
O29  formats→normalization rules · layouts→one few-shot each · absent→null
     slips→retry with doc + failed output + exact error · conflict→stated + calculated + flag
O26  absent→null · present but ambiguous→"unclear"+raw · not on list→"other"+detail
O23  someone waiting→sync · overnight/weekly→batch (50% off, ≤24 h, custom_id,
     resubmit only failures, no tool round trips)

🚫 INVENTED: CLAUDE_HEADLESS · --batch · .claude/config.json · "subagents inherit history"
             · "turn limit in the prompt"
```

---

# Appendix A · ✅ Mastery tracker

> Tick a box only when you can **explain the rule out loud without looking** *and* you got the drill question right.

| W | Obj | Topic | Read W | 📖 Docs read | 🔧 Lab done | 🏁 Self-check | 🧪 Drill Qs right |
|---|---|---|---|---|---|---|---|
| W1 | O16 | Which mechanism | ⬜ | ⬜ | ⬜ E1–E8 | ⬜ | Q1–Q5 ⬜ |
| W2 | O14 | `context: fork` | ⬜ | ⬜ | ⬜ E5 | ⬜ | Q6–Q7 ⬜ |
| W3 | O8 | Plan vs direct | ⬜ | ⬜ | ⬜ E9 | ⬜ | Q8–Q9 ⬜ |
| W4 | O12 | Iterative refinement | ⬜ | ⬜ | ⬜ E10 | ⬜ | Q10–Q12 ⬜ |
| W5 | O13 | Review config | ⬜ | ⬜ | ⬜ E11 | ⬜ | Q13–Q14 ⬜ |
| W6 | O15 | Test generation | ⬜ | ⬜ | ⬜ E12 | ⬜ | Q15 ⬜ |
| W7 | O11 | CI flags | ⬜ | ⬜ | ⬜ E11 flags | ⬜ | Q16–Q17 ⬜ |
| W8 | O30 | False positives | ⬜ | ⬜ | ⬜ d4/01 | ⬜ | Q18 ⬜ |
| W9 | O17 · O32 | Exploration + tools | ⬜ | ⬜ | ⬜ E14 | ⬜ | Q19–Q21 ⬜ |
| W10 | O20 | Long context | ⬜ | ⬜ | ⬜ E14, E16 | ⬜ | Q22 ⬜ |
| W11 | O1 | Parallel tool calls | ⬜ | ⬜ | ⬜ d1/02 | ⬜ | Q23–Q24 ⬜ |
| W12 | O2 | Sessions | ⬜ | ⬜ | ⬜ d1/06, E13 | ⬜ | Q25–Q26 ⬜ |
| W13 | O3 | Subagent context | ⬜ | ⬜ | ⬜ E16, d1/05 ex 6 | ⬜ | Q27 ⬜ |
| W14 | O4 | Goal delegation | ⬜ | ⬜ | ⬜ d1/05 ex 4 | ⬜ | Q28 ⬜ |
| W15 | O37 | `tool_choice` ordering | ⬜ | ⬜ | ⬜ d2/03, d1/03 | ⬜ | Q30–Q31 ⬜ |
| W16 | O33 | Tool distribution | ⬜ | ⬜ | ⬜ d2/04, d1/05 ex 7 | ⬜ | Q29 ⬜ |
| W17 | O29 | Extraction accuracy | ⬜ | ⬜ | ⬜ d4/03, d4/04 | ⬜ | Q32–Q34 ⬜ |
| W18 | O26 | Nullable / unclear / other | ⬜ | ⬜ | ⬜ d4/02 | ⬜ | Q35 ⬜ |
| W19 | O23 | Sync vs batch | ⬜ | ⬜ | ⬜ d4/05 | ⬜ | Q36 ⬜ |

**Miss log**
```
Q#  | W#  | my pick | right | the rule I'll remember
----|-----|---------|-------|--------------------------------------------
    |     |         |       |
```

> 🏁 **When every row is ticked, your weak spots are no longer weak.** Go back to `CCARF-STUDY-GUIDE.md` Part 9 for the full 48-question mixed self-test, then Part 10 the night before. Good luck! 🍀

---

# Appendix B · 📖 Concept glossary (A–Z)

> 🔎 Every term used in this guide, defined in one or two plain sentences. **W#** points to the section that explains it in depth.

| Term | Definition | See |
|---|---|---|
| **Accepted pattern** | A code construct the team has decided is fine in a given place; listed in review standards as "do not flag". | W8 |
| **Agent SDK** | Anthropic's library for building your own agents on the Claude Code engine (tools, hooks, sessions, subagents) in Python or TypeScript. | W12, N2 |
| **Agentic loop** | Call the model → run any tools it requests → send results back → repeat until `stop_reason` is `end_turn`. | W11 |
| **Agentic turn** | One model response within the loop. `--max-turns` caps how many happen. | W7 |
| **`allowedTools` / `--allowedTools`** | Tools that may run **without a permission prompt**. Pre-approves; does not restrict. | W7 |
| **Anchor (`old_string`)** | The exact text Edit searches for and replaces. Must occur exactly once in the file. | W9 |
| **`any` (tool_choice)** | Claude must call one of the provided tools, choosing which. | W15 |
| **`argument-hint`** | Skill frontmatter describing expected arguments. ⚖️ Guide: prompts for missing parameters. | W2 |
| **`$ARGUMENTS`** | Placeholder in a skill replaced with the text typed after `/skill-name`. | W2 |
| **`auto` (tool_choice)** | Default: Claude decides whether to call a tool or answer in text. | W15 |
| **Bare mode (`--bare`)** | A minimal headless run that skips CLAUDE.md, hooks, skills, MCP and auto memory. | W7 |
| **Batch (Message Batches API)** | Asynchronous bulk processing: ≤ 24 h, 50% cheaper, results matched by `custom_id`. | W19 |
| **Built-in tools** | Claude Code's own tools: Read, Edit, Write, Grep, Glob, Bash, and others. | W9 |
| **CI (continuous integration)** | Automated jobs that run on each push or pull request. | W5 |
| **CLAUDE.md** | Instruction file loaded into context at session start; project, user, or folder level. | W1 |
| **Closed / open-world enum** | A closed enum assumes its list is complete; open-world data can fall outside any list, so add `other`. | W18 |
| **Code gate** | A check inside a tool's code that refuses an action until a condition holds. | N1 |
| **Compaction (`/compact`)** | Replacing older conversation with a summary to free context space; exact details can blur. | W10 |
| **Context isolation** | Each agent or fork has its own context; nothing is shared unless passed explicitly. | W13, W2 |
| **Context window** | Everything the model can see for the current request; finite, measured in tokens. | W2, W10 |
| **`context: fork`** | Skill frontmatter that runs the skill in an isolated subagent; only the result returns. | W2 |
| **Coordinator / orchestrator** | The agent that plans, delegates to subagents, and merges their results. | W13 |
| **Coverage criteria** | The definition of "complete" given to an agent (all sectors, all regions). | W14 |
| **`custom_id`** | Your identifier on each batch request, used to join results to inputs. | W19 |
| **Decomposition (fixed / dynamic)** | Splitting a task into subtasks: a known pipeline (fixed), or steps that depend on findings (dynamic). | W14 |
| **Deny rule** | Permission rule that refuses an action; wins over ask and allow from any settings file. | W1 |
| **Deterministic vs probabilistic** | Deterministic controls (rules, hooks, schemas, flags) always behave the same; prompts only make behavior likely. | Part 1 |
| **`detected_pattern`** | Review-schema field naming the construct that triggered a finding. | W5, W8 |
| **Direct execution** | Claude acts on the request immediately, without a separate planning approval. | W3 |
| **`disallowedTools` / `--disallowedTools`** | Removes tools (bare name) or denies matching calls (scoped rule). | W7 |
| **`dontAsk`** | Permission mode in which anything that would prompt is denied; used for CI. | W7 |
| **Edge case** | An unusual or boundary input (empty, missing, negative, malformed). | W6 |
| **Edit** | Built-in tool that replaces a unique `old_string` with `new_string`. | W9 |
| **`end_turn`** | `stop_reason` meaning Claude finished its answer; ends the loop. | W11, W15 |
| **Enum** | A field restricted to a fixed list of allowed values. | W18 |
| **Escalation** | Handing the case to a human on explicit criteria, with a structured handoff. | N4 |
| **Exit code (hooks)** | `0` continue · `2` block (PreToolUse; stderr goes to Claude) · other = non-blocking error. | W1 |
| **Explore subagent** | Built-in read-only subagent for codebase investigation in a separate context. | W3 |
| **False positive** | A reported finding that isn't a real problem. | W8 |
| **Few-shot examples** | A small number of worked examples in the prompt. ⚖️ Guide: 2–4 (2–3 I/O in TS 3.5). | W4, W17 |
| **Fixture** | The setup data a test uses. | W6 |
| **Fork (session)** | `--fork-session` / `fork_session=True`: branch a session's history into a **new** session ID. | W12 |
| **Frontmatter** | The `---` YAML block at the top of a skill, rule or agent file. | W1 |
| **Glob (pattern)** | Path pattern. `*` = within one folder; `**` = across folders. | W1 |
| **Glob (tool)** | Built-in tool that finds files by **name/path** pattern. | W9 |
| **Goal-oriented delegation** | Delegating outcome, coverage and quality criteria rather than a step list. | W14 |
| **Grep (tool)** | Built-in tool that searches file **contents**. | W9 |
| **Handoff** | The prompt or payload passed to a subagent or human; its only knowledge of the task. | W13, N1 |
| **Headless / print mode (`-p`)** | Non-interactive run that executes one task and prints the result. | W5, W7 |
| **Hook** | A command Claude Code runs automatically at a lifecycle event. | W1 |
| **`@import`** | `@path` in CLAUDE.md that loads another file with it. | W1 |
| **Independent reviewer** | A fresh instance that didn't write the code under review. | W5 |
| **Interacting vs independent bugs** | Interacting bugs change each other's behavior (fix together); independent ones don't (fix one at a time). | W4 |
| **Interview pattern** | Asking Claude to question you about requirements before implementing. | W4 |
| **Least privilege** | Give each agent only the tools its role needs. | W16 |
| **Lost in the middle** | Information buried mid-way through long input is used less reliably. | W10 |
| **`--max-budget-usd`** | Stops a headless run once estimated spend reaches the cap (may slightly overshoot). | W7 |
| **`--max-turns`** | Caps agentic turns; exits with an error when reached. | W7 |
| **MCP (Model Context Protocol)** | Open standard for connecting Claude to external tools and data through servers. | — |
| **Multi-phase execution** | A large change done as plan → execute → verify, slice by slice. | W3 |
| **Normalization rules** | Instructions that convert values into one standard format (dates, amounts). | W17 |
| **Nullable field** | A field whose type allows `null` for "not in the source". | W18 |
| **`other` + detail** | Enum value for a clear category that isn't on the list, with free text naming it. | W18 |
| **Parallel tool use** | Several `tool_use` blocks in one response; all results returned in one message. | W11 |
| **Permission mode** | Session-wide baseline for what runs without asking (`default`, `acceptEdits`, `plan`, `auto`, `dontAsk`, `bypassPermissions`). | W3, W7 |
| **Permission rule** | `allow` / `ask` / `deny` entry in a settings file, e.g. `Edit(db/migrations/**)`. | W1 |
| **Plan mode** | Permission mode where Claude investigates but can't edit until you approve its plan. | W3 |
| **PostToolUse** | Hook event after a tool ran; for formatting, logging, normalizing. Can't stop the action. | W1 |
| **Precision / recall** | Share of reported findings that are real / share of real problems that get reported. | W8 |
| **PreToolUse** | Hook event before a tool runs; exit 2 (or a deny decision) blocks it. | W1 |
| **Prefill** | The API starting Claude's reply; forced `tool_choice` prefills a tool call. | W15 |
| **Prerequisite ordering** | Making a step always run first: forced `tool_choice` on turn 1, then `auto`. | W15 |
| **Prior findings** | Earlier review results fed into a re-review so only new or unaddressed issues are reported. | W5 |
| **Procedural delegation** | Delegating a fixed list of steps. | W14 |
| **Project / user / local scope** | Committed for the team / in `~/.claude` for you / `settings.local.json` for you in one project. | W1 |
| **Provenance** | Where a fact came from: source, page, URL, date, method. | W13 |
| **Resume** | Continue a saved session under the **same** session ID. | W12 |
| **Review standards** | Written report / don't-report lists, accepted patterns and severity definitions. | W5, W8 |
| **Role drift** | An agent doing another role's work because it holds that role's tools. | W16 |
| **Round trip** | One request/response cycle with the API. | W11 |
| **Rule (`.claude/rules/`)** | Instruction file that, with `paths:`, loads only when Claude touches matching files. | W1 |
| **Schema (JSON Schema)** | A formal spec of required output fields, types and allowed values. | W5, W17 |
| **Scoped cross-role tool** | One narrow tool borrowed from another role, e.g. `verify_fact`. | W16 |
| **Scratchpad file** | A notes file of confirmed facts that survives compaction and `/clear`. | W10 |
| **Semantic vs syntactic error** | Wrong meaning with the right shape vs wrong shape. Schemas stop syntactic errors only. | W17 |
| **Session / session ID** | A saved conversation (messages + tool results) and its unique identifier. | W12 |
| **Skill** | On-demand procedure in `SKILL.md`, invoked as `/name` or chosen from its description. | W1 |
| **Stale context** | Earlier tool results (file reads) that no longer match the current files. | W12 |
| **State manifest** | A file of completed and pending phases, used to resume a crashed run. | W10 |
| **`stop_reason`** | Why a response ended: `tool_use`, `end_turn`, `max_tokens`, … | W11 |
| **Strict tool use** | `strict: true`: tool inputs are guaranteed to match the schema. | W15 |
| **Structured error** | Machine-readable failure: flag, category, retryable, message. | N3 |
| **Structured output** | Output guaranteed to follow a schema; in Claude Code, `--json-schema` → `structured_output`. | W5 |
| **Subagent** | A delegated model instance with its own isolated context. | W13 |
| **Synchronous API** | The caller waits for each response (seconds). | W19 |
| **`Task`** | ⚖️ Guide's name for the subagent-spawning tool (`Agent` today; `Task` still an alias). | W16 |
| **Token** | The unit of text a model processes; context and cost are measured in tokens. | W10 |
| **`tool` (forced tool_choice)** | Claude must call the named tool. | W15 |
| **`tool_choice`** | API parameter controlling whether and which tool must be called. | W15 |
| **`tool_result`** | Block you send back with a tool's output, referencing `tool_use_id`. | W11 |
| **`tool_use`** | Block in Claude's reply requesting a tool call (`id`, `name`, `input`). | W11 |
| **`--tools`** | Restricts which built-in tools exist for a run (`""` = none). | W7 |
| **`unclear` (enum value)** | For a value that's present but can't be classified; pair it with the raw text. | W18 |
| **Validation-retry loop** | Check output in code; on failure, retry with the document, the output and the exact error. | W17 |
| **Write** | Built-in tool that creates or fully overwrites a file; the Edit fallback. | W9 |
