# 🎓 CCAR-F · The Complete Study Guide

**Claude Certified Architect – Foundations** · all 5 domains · all 6 scenarios · built around **your** score report

> 📌 **Sources:** this lab's READMEs, `docs/score-map.md` (your 5 Oct report), `docs/decision-rules.md`, `docs/guide-vs-docs.md` and the real config files in `d3-claude-code/sandbox/`. The lab maps to exam guide v1.0 (July 2026).
>
> When today's product behaves differently from the guide, **the exam answer follows the guide**. This file shows both, marked ⚖️.
>
> No real exam questions are in here. Every practice question is original.

---

## 🧭 How to use this file

| Icon | Meaning |
|---|---|
| 🚨 | **Your weak spot (0–50%).** Slow down. Read it twice. Say the rule out loud. |
| 🟩 | You scored 100%. Quick refresh only. |
| 🎯 | The exam answer |
| ⚠️ | Exam trap |
| ❌ | Anti-pattern: a wrong answer that looks right |
| ✅ | Do this |
| ⚖️ | Guide vs docs: answer the exam per the guide |
| 🔧 | Try it in the lab |
| 🧠 | One line to remember |

**Reading order (weakest first)**

| Step | Read | Why | Time |
|---|---|---|---|
| 1 | **Part 1** · The master key | One table answers a third of the exam | 15 min |
| 2 | **Part 4** · Claude Code (D3) | 6 of your 10 zeros live here | 60 min |
| 3 | **Part 2** · Agentic (D1) | O1, O2 at 0%, O3 at 33% | 30 min |
| 4 | **Part 3** · Tools & MCP (D2) | O37 at 0%, O17/O32/O33 shaky | 25 min |
| 5 | **Part 5** · Prompting & output (D4) | O29 at 0%, O26 at 33% | 25 min |
| 6 | **Part 6** · Context & reliability (D5) | O20 at 50%, rest strong | 15 min |
| 7 | **Part 7** · Scenario playbooks | How it all shows up in stems | 15 min |
| 8 | **Part 9** · Self-test (48 questions) | Find what didn't stick | 45 min |
| 9 | **Part 10** · Night-before cram sheet | Last read before the exam | 10 min |

**Tips**
- Press **Ctrl+F** and type an objective number (`O16`) to jump to it.
- In VS Code, **Ctrl+Shift+V** opens the formatted preview.
- Click **▶** on folded blocks to reveal answers. Guess first, then open.

## 📚 Contents

- **Part 0** · The exam and your scores
- **Part 1** · The master key: words vs guarantees, stem → answer, six traps, 2-minute method
- **Part 2** · D1 Agentic Architecture & Orchestration (27%)
- **Part 3** · D2 Tool Design & MCP Integration (18%)
- **Part 4** · D3 Claude Code Configuration & Workflows (20%) 🚨🚨
- **Part 5** · D4 Prompt Engineering & Structured Output (20%)
- **Part 6** · D5 Context Management & Reliability (15%)
- **Part 7** · Scenario playbooks S1–S6
- **Part 8** · Guide vs docs, and myths that cost points
- **Part 9** · Self-test: 48 questions with answers
- **Part 10** · Night-before cram sheet
- **Appendix A** · Where to practise each weak objective
- **Appendix B** · Glossary in plain words
- **Appendix C** · Miss log template

---

# Part 0 · The exam and your scores 🗺️

## 0.1 Five domains

```
D1  Agentic Architecture & Orchestration    ███████████████████████████   27%
D2  Tool Design & MCP Integration           ██████████████████            18%
D3  Claude Code Configuration & Workflows   ████████████████████          20%   ← your biggest gap
D4  Prompt Engineering & Structured Output  ████████████████████          20%
D5  Context Management & Reliability        ███████████████               15%
```

## 0.2 Six scenarios (the exam draws 4)

| Scenario | What it's about | Main domains | Read |
|---|---|---|---|
| **S1** Customer Support | An agent that looks up customers and orders, and issues refunds | D1, D2, D5 | Parts 2, 3, 6 |
| **S2** Code Generation with Claude Code | Setting up Claude Code for a team: CLAUDE.md, rules, skills, plan mode | D3 | Part 4 |
| **S3** Multi-Agent Research | A coordinator with subagents, and synthesis with sources | D1, D2, D5 | Parts 2, 3, 6 |
| **S4** Developer Productivity | Exploring code with built-in tools, MCP, sessions | D2, D3, D1 | Parts 3, 4 |
| **S5** Claude Code for CI | Headless review and test generation in pipelines | D3, D4 | Parts 4, 5 |
| **S6** Structured Extraction | Documents → JSON: schemas, validation, batches | D4, D5 | Parts 5, 6 |

> ⚠️ Only 4 of the 6 appear, and you don't know which. Don't skip any scenario.

## 0.3 Your report in one picture

```
🟥 0%      ██████████  10 objectives   O1 O2 O8 O12 O13 O14 O15 O16 O29 O37
🟧 33–50%  █████████    9 objectives   O3 O26 (33) · O17 (40) · O4 O11 O20 O30 O32 O33 (50)
🟨 75%     █            1 objective    O23
🟩 100%    █████████████████ 17 objectives
```

**What the pattern says**
- **6 of your 10 zeros are Claude Code workflow knobs** (O8, O12–O16). You get this knowledge from using Claude Code, not from theory. Part 4 fixes it.
- **The other zeros are API mechanics:** parallel tool calls (O1), sessions (O2), `tool_choice` (O37) and extraction accuracy (O29).
- **Your strengths:** multi-agent design, synthesis with sources, review routing, MCP and structured output. Keep them warm, but don't over-study them.

## 0.4 All 37 objectives

| # | Objective | Score | Read |
|---|---|---|---|
| O1 | Multiple tool calls in one response | 🟥 0% | 2.2 |
| O2 | Session resumption, targeted re-analysis | 🟥 0% | 2.8, 4.15 |
| O3 | Complete context in subagent prompts | 🟧 33% | 2.4, 4.18 |
| O4 | Goal-oriented vs procedural delegation | 🟧 50% | 2.5 |
| O5 | Subagent tools, context scoping, role prompts | 🟩 100% | 2.3 |
| O6 | Diagnose broken subagent spawning | 🟩 100% | 2.3 |
| O7 | Dynamic vs fixed decomposition | 🟩 100% | 2.3 |
| O8 | Plan mode vs direct vs multi-phase | 🟥 0% | 4.11 |
| O9 | State persistence / resume manifest | 🟩 100% | 2.3 |
| O10 | Orchestration patterns | 🟩 100% | 2.3 |
| O11 | CI flags, permission modes, cost/turn limits | 🟧 50% | 4.13 |
| O12 | Iterative refinement | 🟥 0% | 4.12 |
| O13 | Review config: standards, restricted tools, structured output | 🟥 0% | 4.13 |
| O14 | `context: fork` | 🟥 0% | 4.7 |
| O15 | Test generation quality | 🟥 0% | 4.14 |
| O16 | Choose CLAUDE.md / rules / skills / hooks / permissions | 🟥 0% | 4.2–4.10 |
| O17 | Systematic exploration with Grep/Glob/Read | 🟧 40% | 3.7, 4.16 |
| O18 | Subagent output schemas for synthesis | 🟩 100% | 6.5 |
| O19 | Synthesis that preserves uncertainty | 🟩 100% | 6.5 |
| O20 | Context across long exploration | 🟧 50% | 6.4, 4.16 |
| O21 | Context window optimization | 🟩 100% | 6.1 |
| O22 | Human review routing | 🟩 100% | 6.6 |
| O23 | Sync API vs Message Batches | 🟨 75% | 5.7 |
| O24 | Specialized / multi-pass review | 🟩 100% | 5.9 |
| O25 | Most reliable structured output method | 🟩 100% | 5.3 |
| O26 | Nullable fields, "unclear" / "other" enums | 🟧 33% | 5.4 |
| O27 | `tool_choice` to guarantee a call | 🟩 100% | 3.4 |
| O28 | Truncated structured output | 🟩 100% | 5.8 |
| O29 | Extraction accuracy patterns | 🟥 0% | 5.5, 5.6 |
| O30 | False positives via persistent conventions | 🟧 50% | 5.1, 4.13 |
| O31 | Inclusion / exclusion criteria | 🟩 100% | 5.1 |
| O32 | Picking the right built-in tool | 🟧 50% | 3.7 |
| O33 | Tool distribution across agents | 🟧 50% | 3.3, 4.18 |
| O34 | MCP resources vs tools | 🟩 100% | 3.6 |
| O35 | MCP scope, env vars, discovery | 🟩 100% | 3.5 |
| O36 | MCP tool descriptions | 🟩 100% | 3.1 |
| O37 | `tool_choice` + prerequisite ordering | 🟥 0% | 3.4 |

## 0.5 🚨 Weak-spot radar: the 19 to fix

Ordered by priority: zeros first, then the domains with the most weight.

| # | Obj | Score | The one rule to know | Read |
|---|---|---|---|---|
| 1 | **O16** | 🟥 0% | Always → CLAUDE.md · file type across folders → rules with `**` · on demand → skill · must never → deny · check before → PreToolUse exit 2 · after → PostToolUse | 4.2 |
| 2 | **O14** | 🟥 0% | Verbose or exploratory skill → `context: fork`. The skill text must be self-contained. | 4.7 |
| 3 | **O8** | 🟥 0% | One-sentence diff with a clear cause → direct. Multi-file, architectural, several approaches or sign-off → plan mode. | 4.11 |
| 4 | **O12** | 🟥 0% | Inconsistent results → 2–3 I/O examples. Tests first. Interacting bugs in one message, independent ones one at a time. Unfamiliar → interview. | 4.12 |
| 5 | **O13** | 🟥 0% | CI review = standards in project CLAUDE.md + read-only tools + JSON schema + prior findings on re-runs + independent reviewer. | 4.13 |
| 6 | **O15** | 🟥 0% | Give the existing tests ("don't duplicate") and put test standards in project CLAUDE.md. | 4.14 |
| 7 | **O1** | 🟥 0% | Independent calls → one turn, N `tool_use` blocks → all N results in one user message. | 2.2 |
| 8 | **O2** | 🟥 0% | Mostly valid → resume and name the changed files. Stale → fresh + summary. Two approaches → fork. | 2.8 |
| 9 | **O37** | 🟥 0% | `any` = some tool. Forced = this tool. Force on turn 1, then `auto`. Never force every turn. | 3.4 |
| 10 | **O29** | 🟥 0% | Messy formats → normalization rules. Varied layouts → one few-shot per layout. Absent → nullable. | 5.5 |
| 11 | **O3** | 🟧 33% | Subagents see only their prompt. Pass complete findings with sources. | 2.4 |
| 12 | **O26** | 🟧 33% | Absent → nullable. Ambiguous → `unclear`. Open-ended → `other` + detail. | 5.4 |
| 13 | **O17** | 🟧 40% | Grep/Glob to narrow, then Read only the hits. Write facts down as you go. | 3.7 |
| 14 | **O11** | 🟧 50% | Caps are flags (`--max-turns`, `--max-budget-usd`). `--allowedTools` pre-approves; `--tools` and `--disallowedTools` restrict. | 4.13 |
| 15 | **O4** | 🟧 50% | Delegate goals and quality criteria, not step lists. | 2.5 |
| 16 | **O20** | 🟧 50% | Scratchpad file for exact facts, subagents for verbose discovery, manifest for crashes. | 6.4 |
| 17 | **O30** | 🟧 50% | False positives → explicit report/skip lists and accepted patterns in project CLAUDE.md. Not "be conservative". | 5.1 |
| 18 | **O32** | 🟧 50% | Content → Grep. Names → Glob. Non-unique Edit → longer anchor, or Read + Write. | 3.7 |
| 19 | **O33** | 🟧 50% | 4–5 tools per role plus one scoped cross-role tool. Constrain generic tools in code. | 3.3 |

---

# Part 1 · The master key 🔑

> Read this part before anything else. Most exam questions come down to one of these patterns.

## 1.1 The idea behind half the exam: words vs guarantees

```
      "Please never do X"                        "X is impossible"
      ───────────────────                        ─────────────────
      prompt text, CLAUDE.md lines,              deny rule, PreToolUse hook (exit 2),
      few-shot examples, tool descriptions       code gate, forced tool_choice, JSON schema,
                                                 --max-turns, tool not in the allowlist

      LOWERS the failure rate                    makes the failure IMPOSSIBLE
      ✅ good for style and judgment              ✅ needed for money, identity, compliance, safety
```

🧠 **If the stem says *must, always, never, guarantee, money, identity, compliance*, the answer is a mechanism, not a sentence.**

## 1.2 Stem says → answer shape

**Guarantees and control**

| Stem says | Answer shape |
|---|---|
| must, always, never, guarantee, money, identity, compliance | Deterministic: hook, deny rule, prerequisite gate, constrained tool, forced `tool_choice`, schema, `--max-turns` / `--max-budget-usd` |
| block it **before** it happens | PreToolUse hook (**exit 2**) or a deny rule |
| normalize, trim or log **after** a tool runs | PostToolUse hook |
| must call **some** tool, unknown doc type | `tool_choice: any` |
| **this** tool must run first | Force it on turn 1, then `auto` |

**Scope: who gets it**

| Stem says | Answer shape |
|---|---|
| whole team, new hire didn't get it | Project scope, committed: `./CLAUDE.md`, `.claude/`, `.mcp.json` |
| only me, experimental | User scope: `~/.claude/...`, `~/.claude.json` |
| only for these file types, spread across folders | `.claude/rules/` with `paths` and `**` |
| only when doing this task | Skill (on demand). Verbose or exploratory → `context: fork` |
| always-on convention | CLAUDE.md |

**Workflow**

| Stem says | Answer shape |
|---|---|
| one-sentence diff, clear stack trace | Direct execution |
| multi-file, architectural, several approaches, sign-off | Plan mode → approve → execute |
| verbose discovery | Explore subagent / subagent delegation |
| interacting bugs | One detailed message with all of them |
| independent bugs | One at a time |
| unfamiliar domain | Interview pattern first |
| prose interpreted inconsistently | 2–3 concrete input/output examples |
| independent lookups are slow | One turn, several `tool_use` blocks |

**Sessions and context**

| Stem says | Answer shape |
|---|---|
| context mostly valid after edits | Resume + name the changed files |
| prior tool results stale | Fresh session + structured summary |
| compare two approaches from one baseline | Fork |
| long conversation loses numbers and dates | Case-facts block outside the summary |

**API mode and extraction**

| Stem says | Answer shape |
|---|---|
| blocking, pre-merge, someone waiting | Synchronous API |
| overnight, weekly, cost | Message Batches (`custom_id`, resubmit failures only) |
| info may be absent from the source | Nullable or optional field (not a retry) |
| ambiguous or extensible categories | `unclear` / `other` + detail |
| messy formats vs varied layouts | Normalization rules vs one few-shot per layout |
| first step, least effort, quickest | Smallest change at the root cause (often: fix the tool descriptions, add explicit criteria) |

## 1.3 The six traps

| # | Trap | Looks like | Why it's wrong |
|---|---|---|---|
| 1 | **Words where a guarantee is needed** | "Add a bold rule to the system prompt: NEVER refund without verification" | Prompts, few-shot and descriptions are probabilistic. Money needs a gate or hook. |
| 2 | **Heavy machinery** | "Train a classifier", "add a vector store", "build a router", "speculatively pre-run tools" | These win only when the simple fix is ruled out. Look for the description fix or the explicit criteria first. |
| 3 | **Wrong layer** | Fixing the synthesizer when the coordinator only searched two sectors | Fix the **first** component that went wrong. |
| 4 | **Invented mechanisms** | `CLAUDE_HEADLESS=1`, `--batch`, `.claude/config.json`, "subagents inherit the conversation" | These don't exist. If you've never seen it in the lab, be suspicious. |
| 5 | **Error semantics** | "Retry the validation error", "the empty search is an error", "retry until the due date appears" | Transient errors are retryable. Validation, business and permission errors aren't. An empty result is not an error. Absent data can't be retried into existence. |
| 6 | **Habit over constraint** | Picking the "best practice" answer when the stem asks for the "first step" | Re-read the last line: *most effective*, *first step*, *best explains*, *least effort*. |

## 1.4 The 2-minute method

```
 ⏱  10 s   Read the LAST line of the stem       → what are they really asking?
 ⏱  20 s   Find the deciding constraint         → "must", "whole team", "overnight", "first step"...
 ⏱  15 s   Predict the answer SHAPE             → before reading the options (use 1.2)
 ⏱  45 s   Eliminate by trap type               → words? heavy? wrong layer? invented? error semantics?
 ⏱  2 min  Pick, or flag and move on
```

> ⚠️ **Select-N questions:** each pick must satisfy the constraint **on its own**. Don't pick two half-answers.

---

# Part 2 · D1 Agentic Architecture & Orchestration (27%)

> Biggest domain by weight. Your design instincts are strong (O5–O10 all 100%). Your gaps are mechanics: **O1, O2 at 0%**, **O3 at 33%**, **O4 at 50%**.

## 2.1 🟩 The agent loop (TS 1.1)

**In one line:** keep looping while Claude asks for tools. Stop when it says it's done (`end_turn`).

```
       ┌─────────────────────────────────────────────────────────────┐
       ▼                                                             │
  send messages + tool definitions                                   │
       │                                                             │
       ▼                                                             │
  Claude replies ── stop_reason? ──┬─ "tool_use"   ─► run the tools ─► send ALL tool_results back
                                   ├─ "end_turn"   ─► ✅ finished
                                   └─ "max_tokens" ─► ✂️ output was cut off (see 5.8)
```

❌ **Anti-patterns**
- Looking for "I'm done" in the text.
- Using an iteration cap as the stop signal. A cap is fine as a **safety net**, not as the way you finish.
- Treating "the reply has text" as finished. A reply can hold text **and** tool calls.

🔧 `python d1-agentic/01_agent_loop.py`

🧠 **Loop on `tool_use`, stop on `end_turn`.**

---

## 2.2 🚨 Parallel tool calls · O1 · you scored 0%

> 🚨 **WEAK SPOT · O1 · 0%.** Read slowly. This is pure mechanics, so it's easy points once it clicks.

**In one line:** if the calls don't depend on each other, Claude asks for all of them **in one turn**, and you send **all the results back in one message**.

```
 ❌ WRONG: 3 round trips                   ✅ RIGHT: 1 round trip

 assistant: tool_use A                     assistant: tool_use A   ┐
 user:      tool_result A                             tool_use B   ├ one turn
 assistant: tool_use B                                tool_use C   ┘
 user:      tool_result B                  user:      tool_result A ┐
 assistant: tool_use C                                tool_result B ├ ONE message,
 user:      tool_result C                             tool_result C ┘ matched by tool_use_id
```

**The rules**
1. **Independent** calls (customer profile, order history, open tickets) → **one turn**, several `tool_use` blocks.
2. Send **every** `tool_result` back in the **next single user message**. Each one carries the `tool_use_id` it answers.
3. **Dependent** calls ("find Ana's latest order, *then* look it up") → in **sequence**, because the second needs the first one's output.
4. The same idea applies to subagents: a coordinator spawns **independent subagents in one response**, not one per turn.

❌ **Anti-patterns (the distractors)**
- Sending each `tool_result` in its own user message.
- A composite "do-everything" tool (`get_everything`). That's heavy machinery.
- Speculative pre-execution: running every tool "just in case".
- Forcing independent calls into sequence.

🔧 `python d1-agentic/02_parallel_tool_calls.py`. Section B turns parallelism off with `"disable_parallel_tool_use": true` so you can see the slow version.

🎯 **Exam shape:** "The agent makes 3 independent lookups, one per turn, and it's slow" → let it batch them in one turn and return all results in one message.

🧠 **Independent → one turn → one results message. Dependent → sequence.**

---

## 2.3 🟩 Hub-and-spoke multi-agent (O5, O6, O7, O9, O10)

```
                       ┌──────────────────────┐
                       │     COORDINATOR      │  plans · delegates · merges · handles errors
                       └───┬───────┬──────┬───┘
               prompt ▼    │       │      │   ▼ prompt          everything goes through the hub
             ┌───────────┐ │ ┌───────────┐ ┌──────────────┐
             │ Search A  │   │ Search B  │ │ Synthesizer  │
             └───────────┘   └───────────┘ └──────────────┘
             subagents never talk to each other directly
```

| Objective | What to know |
|---|---|
| **O5** Subagent tools and role prompts | Each subagent gets its role's tools and a role prompt. Nothing more. |
| **O6** Broken spawning | The coordinator can't spawn subagents → the spawn tool isn't in `allowedTools`. ⚖️ Guide: `Task`. Docs today: renamed `Agent` in v2.1.63, with `Task` still an alias. **Exam: "allowedTools must include Task".** |
| **O7** Dynamic vs fixed decomposition | **Fixed** pipeline when the steps are known in advance (extract → validate → store). **Dynamic** when later steps depend on what you find (research subtopics). |
| **O9** State manifest | The coordinator saves completed and pending phases to a file, so a crashed run resumes where it stopped (`run_state/manifest.json`). |
| **O10** Orchestration | Route through the coordinator. Spawn independent work in parallel. Merge with sources. |

🔧 `python d1-agentic/05_coordinator_subagents.py` (the most expensive lab; run it once, then do its exercises)

---

## 2.4 🚨 Complete context in subagent prompts · O3 · you scored 33%

> 🚨 **WEAK SPOT · O3 · 33%.** Think of a subagent as a **new hire with amnesia**.

**In one line:** a subagent sees **only the prompt you give it**. It does not see the coordinator's conversation.

```
  Coordinator's context                          Subagent's context
  ┌─────────────────────────────────┐            ┌──────────────────────────┐
  │ user request                    │            │                          │
  │ F1: refund limit 500 EUR (S1)   │   prompt   │  ONLY what you wrote in  │
  │ F2: manager approval > limit    │ ─────────► │  the prompt              │
  │ 40 tool results...              │            │  (+ CLAUDE.md for        │
  └─────────────────────────────────┘            │   non-Explore types in   │
                                                 │   Claude Code)           │
                                                 └──────────────────────────┘
```

❌ **Bad prompt:** `Write the refund-limit paragraph.` → the subagent writes "not provided" or invents something.

✅ **Good prompt:**
```
Goal: one paragraph on the refund limit, for the policy FAQ.
Facts (use only these; keep each source next to its claim):
  F1: The refund limit is 500 EUR.            Source S1: policy.md, p.3 (May 2026)
  F2: Refunds above the limit need a manager.  Source S2: ops-handbook.md, §4
Quality bar: cite every claim. If something is missing, write "not provided".
Output: one paragraph, at most 80 words.
```

**What to pass**
- ✅ The **goal** and the **quality criteria**
- ✅ **Complete findings**, not a one-line summary
- ✅ **Source metadata**: document, page, URL, date, method
- ✅ Prefer **structured** data (lists or JSON) over prose

❌ **Anti-patterns**
- "Summarize what we found" (found where?)
- Assuming the subagent read the chat. "Subagents inherit history" is an **invented mechanism**.
- Passing a prose summary that drops the sources. Citations disappear (lab `d1/05` exercise 6).

🔧 D3 **E16** (bare prompt → "not provided"; with facts and sources → cited paragraph) and `d1/05` exercise 6.

🧠 **The subagent knows only what's in its prompt. Pass findings with sources, as data.**

---

## 2.5 🚨 Goal-oriented vs procedural delegation · O4 · you scored 50%

> 🚨 **WEAK SPOT · O4 · 50%.**

**In one line:** tell subagents **what good looks like**, not a numbered list of steps. A step list caps coverage at what you thought of.

❌ **Procedural:**
```
1. Search visual art.
2. Search graphic design.
3. Summarize.
```
→ The report covers exactly two sectors. Music, film and gaming are missing.

✅ **Goal-oriented:**
```
Goal: map how AI is changing the creative industries.
Coverage: every major sector you find, not only the ones named here.
Quality: at least 2 independent sources per sector, with dates. Flag any gaps.
```

> ⚠️ **Wrong-layer trap.** If the final report misses sectors, the **first** component that went wrong is the coordinator's decomposition. Improving the synthesizer can't add sectors that were never searched.

🔧 `d1/05` exercise 4: replace the goal text with a numbered procedure and watch coverage shrink.

🧠 **Delegate goals and quality criteria, not step lists. Fix the first broken layer.**

---

## 2.6 Prerequisite gates and handoffs (TS 1.4)

**In one line:** if a rule must hold every time (verify identity before a refund), put it **in code**, not in the prompt.

```
 Claude: process_refund(order="A-7731", amount=650)
                 │
                 ▼
      ┌─────────────────────────────┐
      │  CODE GATE inside the tool  │   verified customer?  amount ≤ limit?
      └────────┬───────────┬────────┘
            no │           │ yes
               ▼           ▼
   structured error     ✅ refund runs
   "Identity not verified: call get_customer first"
   (the model can act on it)
```

- A prompt **lowers** the failure rate. It never makes it **zero**. In the lab, count the violations in 5 runs with only a system prompt.
- The gate returns a **structured error**, so the model knows what to do next.
- Escalations carry a **structured handoff**: `customer_id`, root cause, amount, what was tried, recommended action.

🔧 `python d1-agentic/03_prerequisite_gate.py`

🧠 **Money, identity, compliance → enforce in code.**

---

## 2.7 Agent SDK hooks (TS 1.5)

**In one line:** **PreToolUse** stops a bad call before it runs. **PostToolUse** cleans up a tool's output before the model reasons over it.

```python
# from d1-agentic/04_sdk_hooks.py (simplified)
hooks = {
    "PreToolUse":  [HookMatcher(matcher="mcp__support__process_refund", hooks=[block_large_refunds])],
    "PostToolUse": [HookMatcher(matcher="mcp__support__lookup_order",   hooks=[normalize_order])],
}
# block_large_refunds returns permissionDecision "deny" with the reason:
#   "Refunds above 500 require a human. Escalate with customer_id, amount and root cause."
```

| Hook | Use it for | Lab example |
|---|---|---|
| **PreToolUse** | A business rule that must hold | Refund > 500 → deny and escalate |
| **PostToolUse** | Messy formats from tools you don't control | Unix time → ISO date, numeric status → "delivered" |

> ⚠️ **Right tool, right matcher.** Matching `lookup_order` for the refund rule is the **wrong layer** (lab `d1/04` exercise 3).

Same idea as Claude Code hooks: see **4.10**.

🔧 `python d1-agentic/04_sdk_hooks.py`

---

## 2.8 🚨 Sessions: resume, fork or fresh · O2 · you scored 0%

> 🚨 **WEAK SPOT · O2 · 0%.** This shows up in D1 (SDK) **and** D3 (CLI). Learn the tree once.

```
 What changed since the last session?
 │
 ├─ A few KNOWN files changed, the rest is still true
 │      └──► 🔁 RESUME + NAME the changed files
 │            "Only orders.ts changed: orderTotal now takes a discount.
 │             Re-read only that file and re-check R1–R3."
 │
 ├─ A LOT changed, old tool results are now wrong
 │      └──► 🆕 FRESH session + a structured summary of what still holds
 │            (otherwise Claude trusts stale file reads)
 │
 └─ You want to try TWO approaches from the same starting point
        └──► 🍴 FORK  (new session ID, same history up to the fork)
```

| | Session ID | History | Use when |
|---|---|---|---|
| **Resume** | **same** | everything so far | Context mostly valid |
| **Fork** | **new** | copied up to the fork point | Comparing approaches |
| **Fresh + summary** | new | only your summary | Prior tool results are stale |

**Commands**

| Where | Resume | Fork | Name |
|---|---|---|---|
| CLI | `claude --resume orders-review` (or `-r`) | `claude -p -r orders-review --fork-session "..."` | `claude -n orders-review` |
| Agent SDK | `resume=session_id` | `resume=session_id, fork_session=True` | n/a |

`claude -c` continues the most recent session in the current folder.

❌ **Anti-patterns**
- Resume + "files changed, re-analyze everything". That reads everything again and is slow (lab `d1/06` exercise 8).
- Resuming when the old tool results are stale. Claude reasons over outdated reads.
- A fresh session with **no** summary. Everything is lost.
- Forking just to "continue". Use resume.

🔧 `python d1-agentic/06_sessions_resume_fork.py` + D3 **E13**

🧠 **Mostly valid → resume and name the files. Stale → fresh + summary. Two paths → fork (new ID).**

---

## 2.9 Errors across agents (TS 5.3)

Short version here, full version in **6.3**.

- Subagent errors come back **structured**: error type, what was attempted, partial results, alternatives.
- Retry **transient** errors **locally**, inside the subagent.
- **Never** report a failure as an empty success. "Timeout" is not "no results".
- **Never** kill the whole workflow over one failed subtask. Continue, and annotate the coverage gap.
- Two credible sources conflict → keep **both**, with source and date.

---

### 🧠 Part 2 in 8 lines

```
Loop on tool_use, stop on end_turn. A cap is a safety net, not the stop.
Independent calls → ONE turn, N tool_use blocks → ALL results in ONE user message.
Subagents see ONLY their prompt → pass complete findings + sources, as data.
Delegate goals + quality criteria, not numbered steps. Fix the first broken layer.
Spawning broken → allowedTools must include "Task" (guide).
Must hold every time → code gate or hook. Prompts lower the rate, never to zero.
Resume + name changes · stale → fresh + summary · two approaches → fork (new ID).
Errors: structured · retry transient locally · never fake success · don't kill the workflow.
```

---

# Part 3 · D2 Tool Design & MCP Integration (18%)

> Strong on MCP and descriptions (O34–O36 at 100%). Gaps: **O37 at 0%**, **O17 at 40%**, **O32 and O33 at 50%**.

## 3.1 🟩 Tool descriptions (TS 2.1, O36)

**In one line:** Claude picks tools by reading their descriptions. Thin descriptions mean wrong picks.

**A good description says:**
1. What it does
2. When to use it, **and when to use the similar tool instead**
3. Input format, with an example
4. What it returns

```python
# from d2-tools-mcp/mcp_server/server.py
@mcp.tool(description=("Look up ONE order by ID (format A-<digits>, e.g. A-7731). "
                       "Returns status and total. ..."))
```

**Misrouting? Work in this order:**

```
1. Fix the DESCRIPTIONS (first step: lowest effort, root cause)
2. Check the SYSTEM PROMPT for keyword traps
      e.g. "if the message mentions 'account', use get_customer" drags questions to the wrong tool
3. Rename overlapping tools, or split a generic tool into purpose-specific ones
4. Only then: routers, classifiers, consolidation (heavy machinery)
```

> ⚠️ Few-shot routing examples help, but fixing the descriptions is the guide's **"first step"** answer.

🔧 `python d2-tools-mcp/01_tool_descriptions.py`

---

## 3.2 Structured errors (TS 2.2)

**In one line:** a tool error must say **what kind** of error it is and **whether a retry can help**.

```
isError:       true
errorCategory: "transient" | "validation" | "business" | "permission"
isRetryable:   true / false
message:       "Orders backend timed out. Try again."   ← readable by a human and by the model
```

| Situation | Category | Retry? | The agent should |
|---|---|---|---|
| Backend timed out | transient | ✅ yes | Retry locally, with backoff |
| Order ID in the wrong format | validation | ❌ no | Fix the input, or ask the user |
| Order is past the return window | business | ❌ no | Explain the policy, offer alternatives or escalate |
| Caller isn't allowed | permission | ❌ no | Don't retry. Escalate. |
| Search found **nothing** | **not an error** | n/a | "No order found with that number" |

❌ **Anti-patterns**
- A generic `"Operation failed"`. The agent can't recover well.
- Flagging an empty result as an error. The agent then tells the customer "something went wrong" instead of "no order found" (lab `d2/02` exercise 2).
- Returning an empty list on a timeout. That **fakes success**.

🔧 `python d2-tools-mcp/02_structured_errors.py` and `python d2-tools-mcp/mcp_server/server.py --selftest`

🧠 **Transient → retry. Validation, business, permission → don't. Empty → success with zero results.**

---

## 3.3 🚨 Tool distribution across agents · O33 · you scored 50%

> 🚨 **WEAK SPOT · O33 · 50%.**

**In one line:** give each agent the **4–5 tools its role needs**, not everything.

```
 ❌ 18 tools for everyone                   ✅ Tools by role
 ┌─────────────────────────────┐           Searcher:    search_corpus, load_document, ...
 │ search, fetch_url, verify,  │           Synthesizer: verify_fact   ← ONE scoped cross-role tool
 │ load, write, summarize, ... │           Writer:      format_report, save_report
 │ (selection gets worse)      │
 └─────────────────────────────┘
```

**The rules**
- **4–5 tools per role.** Many tools degrade selection (lab `d2/04`: 4 role tools vs 18 tools).
- A **scoped cross-role tool** for a frequent need. The synthesizer gets `verify_fact`, not the full search tool.
- **Constrain generic tools in code.** Replace `fetch_url` with `load_document(doc_id)`, so misuse is **impossible**, not just discouraged.

❌ **Anti-patterns**
- Giving the synthesizer the search tool. It searches instead of synthesizing (lab `d1/05` exercise 7).
- Prompt text "only use fetch_url for documents". Words, not a guarantee.

🔧 `python d2-tools-mcp/04_tool_distribution.py`

🧠 **4–5 tools per role + one scoped cross-role tool. Constrain generic tools in code.**

---

## 3.4 🚨 `tool_choice` and prerequisite ordering · O37 · you scored 0% (O27: 100%)

> 🚨 **WEAK SPOT · O37 · 0%.** You know *that* `tool_choice` guarantees a call (O27). The gap is **which setting, and when to switch**.

| `tool_choice` | What happens | Use when |
|---|---|---|
| `{"type": "auto"}` | Claude may call a tool **or answer in text** | Normal agent turns |
| `{"type": "any"}` | Claude **must call some tool**, its choice | You need structured output, there are several schemas, the doc type is unknown |
| `{"type": "tool", "name": "X"}` | Claude **must call X** | X must run first, or you need exactly that extraction |
| Force on turn 1, then `auto` | X runs first, then Claude is free | **Prerequisite ordering** |
| Force on **every** turn | ❌ The loop never reaches `end_turn` | Never |

**Prerequisite ordering, turn by turn** (lab `d2/03`, verified):

```
 turn 0   tool_choice = {"type":"tool","name":"extract_metadata"}  → extract_metadata ✅ guaranteed first
 turn 1   tool_choice = {"type":"auto"}                             → enrich_topics
 turn 2   tool_choice = {"type":"auto"}                             → end_turn ✅
```

```python
# from d2-tools-mcp/03_tool_choice.py
tool_choice=lambda turn: {"type": "tool", "name": "extract_metadata"} if turn == 0 else {"type": "auto"}
```

❌ **Anti-patterns**
- Prompt "always call extract_metadata first". That's guidance, not a guarantee.
- Forcing the tool on every turn. Claude can never finish.
- `auto` when you **must** get structured output. It may reply in text.

> ⚖️ **Guide vs docs:** forced `tool_choice` is the exam answer for guaranteeing a call. Docs today: `any` and forced return a 400 error on Opus 5.5, Sonnet 5.5, Fable 5.1 and Mythos 5.1. That's why the lab's `LAB_MODEL` is Haiku 5.5. **Keep the guide answer.**

🔧 `python d2-tools-mcp/03_tool_choice.py` (add `--newest-model-demo` to see the 400)

🧠 **`any` = some tool. Forced = this tool. Force once, then `auto`.**

---

## 3.5 🟩 MCP: scopes, env vars, discovery (O35)

| Scope | Where it lives | Who gets it | Use for |
|---|---|---|---|
| **Project** | `.mcp.json` at the repo root, **committed** | The whole team | Shared team servers |
| **User** | `~/.claude.json`, via `claude mcp add --scope user ...` | You, in every project | Personal servers |
| Local (the default for `claude mcp add`) | `~/.claude.json`, for this project only | You, in this project | Experiments |

**Secrets never go in the file.** Use env var expansion, as in `d3-claude-code/sandbox/.mcp.json`:

```json
{
  "mcpServers": {
    "orders": {
      "type": "stdio",
      "command": "${LAB_PYTHON:-python3}",
      "args": ["../../d2-tools-mcp/mcp_server/server.py"],
      "env": { "ORDERS_API_TOKEN": "${ORDERS_API_TOKEN:-dev-token}" }
    }
  }
}
```

- `${VAR}` reads an env var. `${VAR:-default}` adds a fallback.
- Project servers need **approval** the first time. The approval lands in `.claude/settings.local.json` as `"enabledMcpjsonServers": ["orders"]`.
- See servers: `claude mcp list` (shell) or `/mcp` (in a session).
- **Prefer community or official servers** for standard systems (GitHub, Jira, databases) over writing your own.

🧠 **Team → committed `.mcp.json` with `${TOKEN}`. Personal → user scope.**

---

## 3.6 🟩 MCP resources vs tools (O34)

| | **Resource** | **Tool** |
|---|---|---|
| What it is | Read-only data the client can load | An action or query with parameters |
| Lab example | `catalog://issues`, `schema://orders` | `lookup_order(order_id)` |
| Use for | Catalogs, schemas, reference lists | Lookups, searches, changes |
| Why | Avoids many exploratory tool calls to learn "what exists" | Does work |

🧠 **Catalogs → resources. Actions → tools.**

---

## 3.7 🚨 Built-in tools · O17 (40%) · O32 (50%)

> 🚨 **WEAK SPOT · O17 · 40% and O32 · 50%.** Easy to fix: memorize one table and one fallback.

| The job | Tool | Example |
|---|---|---|
| Find **text inside** files | **Grep** | "Where is `getOrder` called?" |
| Find files by **name pattern** | **Glob** | "Every `*.test.tsx` file" |
| Read a file | **Read** | After Grep/Glob narrowed it down |
| Change one specific spot | **Edit** | Needs an anchor that is **unique** in the file |
| Create or replace a whole file | **Write** | New files, or the Edit fallback |
| Run commands or tests | **Bash** | `python -m unittest` |

**Systematic exploration (O17)**

```
 1. Grep / Glob    → narrow down: which files and lines matter?
 2. Read           → only those hits, not the whole repo
 3. Write it down  → confirmed facts with file:line in a notes file (see 4.16)
 4. Too big?       → hand verbose discovery to a subagent (Explore)
```

**The Edit fallback (O32)**

```
 Edit("retries = 3" → "retries = 5")
        │
        ▼
 ❌ "found 2 matches", the anchor isn't unique
        │
        ├─► use a longer anchor that appears only once (include the line before)
        └─► or the guide's fallback: Read the file, then Write it back with the change
```

❌ **Anti-patterns**
- Reading every file "to be thorough". It floods the context.
- Grep for file names, or Glob for content.
- Using Bash `cat`, `grep` or `find` when a built-in tool exists.
- Retrying the same non-unique Edit.

> ⚖️ **Docs today:** on macOS, Linux and WSL the default tool set leaves out Grep and Glob unless they're named in `--tools` or `--allowedTools`. **Exam: they're standard built-ins.**

🔧 D3 **E14**

🧠 **Content → Grep. Names → Glob. Then Read only the hits. Non-unique Edit → longer anchor, or Read + Write.**

---

### 🧠 Part 3 in 8 lines

```
Misrouting → fix the DESCRIPTIONS first, then check the system prompt for keyword traps.
Errors: isError + errorCategory + isRetryable + message. Empty result = success, not an error.
4–5 tools per role + one scoped cross-role tool. Constrain generic tools in code.
tool_choice: auto may answer in text · any = some tool · forced = this tool.
Prerequisite order → force on turn 1, then auto. Forcing every turn traps the loop.
MCP: team → committed .mcp.json with ${TOKEN} · personal → user scope (~/.claude.json).
Catalogs → resources. Actions → tools. Prefer community servers for standard systems.
Grep = content · Glob = names · Read the hits · Edit needs a unique anchor, else Read + Write.
```

---

# Part 4 · D3 Claude Code Configuration & Workflows (20%) 🚨🚨

> 🚨🚨 **YOUR BIGGEST GAP.** Six of your ten zeros are here: **O8, O12, O13, O14, O15, O16**, plus O11 at 50%.
> The good news: it's concrete. Every question is "which file, which flag, which mode". Learn the map and the precedence rules, and these become your easiest points.
>
> **Your lab progress:** E1 ✅ · E2 ✅ · E3 ✅ · E4–E16 ⬜

## 4.1 The big map: where everything lives

```
 👤 USER SCOPE: C:\Users\RP32210\.claude\          follows YOU into every project, never committed
 ├── CLAUDE.md                     your personal instructions
 ├── settings.json                 your personal permissions and hooks
 ├── skills/<name>/SKILL.md        your personal skills
 └── agents/<name>.md              your personal subagents
 ~/.claude.json                    your user-scope and local-scope MCP servers

 👥 PROJECT SCOPE: the repo                         committed, every teammate gets it
 ├── CLAUDE.md                     team instructions, always loaded
 ├── src/api/CLAUDE.md             folder instructions, load when Claude works in src/api/
 ├── .mcp.json                     team MCP servers, secrets as ${VAR}
 └── .claude/
     ├── settings.json             team permissions + hooks (committed)
     ├── settings.local.json       YOUR overrides for this project (not committed)
     ├── rules/*.md                conditional rules (paths: globs)
     ├── commands/<name>.md        team slash commands (the guide's location)
     ├── skills/<name>/SKILL.md    team skills
     ├── agents/<name>.md          team subagents
     └── hooks/*.py                hook scripts
```

> There's also an admin-managed organization level. It's rarely the answer.

---

## 4.2 🚨 Which mechanism? · O16 · you scored 0%

> 🚨🚨 **WEAK SPOT · O16 · 0%. THE most important table in this guide.** Most D3 questions are this table in disguise. Read it until you can recite it.

| The need (stem words) | Mechanism | Why not the others |
|---|---|---|
| Always-on team convention: "all code must..." | **Project `CLAUDE.md`** | Always loaded, committed, reaches the team |
| Personal preference, "only me" | **`~/.claude/CLAUDE.md`** | Follows only you |
| Convention for **one folder** | **Folder `CLAUDE.md`** | Loads only when Claude works there |
| Convention for a **file type spread across folders** (tests, `*.tsx`) | **`.claude/rules/*.md` with `paths` + `**`** | One file, loads only on matching files. Beats a CLAUDE.md per folder. |
| Keep CLAUDE.md modular, share a standards doc | **`@import`** (`@../../standards/api.md`) | The imported file loads with its parent |
| Reusable task, on demand (`/review`, `/release-notes`) | **Skill** or **command** | Loads only when used |
| Verbose or exploratory on-demand task | **Skill + `context: fork`** | Keeps the main context clean |
| **Must never** read, edit or run a **known** path or command | **Permission `deny`** | Nothing can override it |
| Ask me first | **Permission `ask`** | Prompts every time |
| Allowed without a prompt | **Permission `allow`** | Runs silently |
| Check **content dynamically before** an action ("command contains `rm -rf`") | **PreToolUse hook, exit 2** | Code decides, blocks, and tells Claude why |
| Do something **after** an action: format, log, normalize | **PostToolUse hook** | Runs after, can't stop it |
| A helper role with limited tools | **Subagent** with `tools:` in its config | Config restricts, prompt text doesn't |
| A team external system | **`.mcp.json`** | Committed, secrets via `${VAR}` |

🧠 **The chant:**
```
ALWAYS        → CLAUDE.md          (team: project file · me: ~/.claude)
WHERE         → folder CLAUDE.md / rules with paths + **
WHEN ASKED    → skill / command    (verbose → context: fork)
NEVER         → deny rule
CHECK BEFORE  → PreToolUse, exit 2
AFTER         → PostToolUse
```

---

## 4.3 ✅ E1 · CLAUDE.md scope: user vs project (O16)

**Status: done.** Your log showed `~/.claude/CLAUDE.md` loading only in the sessions where it existed, and the project `CLAUDE.md` loading every time.

| | User `~/.claude/CLAUDE.md` | Project `./CLAUDE.md` |
|---|---|---|
| Who gets it | Only you | Everyone who clones the repo |
| Applies to | Every project you open | This project |
| Committed? | Never | Yes |

**What you learned:** both work *for you*, so you can't tell them apart on one machine. The difference is **who else** gets the instruction.

🎯 **Exam shape:** "A new teammate's Claude doesn't follow the team convention" → it lives in someone's **user** scope. Move it to the **project** CLAUDE.md and commit it.

> ⚖️ **Verify which memory files loaded:** guide → **`/memory`**. Docs today → `/context` shows what loaded, `/memory` lists and opens the files. **Exam: `/memory`.**

---

## 4.4 ✅ E2 · Folder CLAUDE.md + `@import`

**Status: done.** `read src/api/v1/users.ts` produced `nested_traversal` for `src/api/CLAUDE.md` and `include` for `standards/api.md`.

```
 read src/components/Button.tsx   → nothing new loads (no CLAUDE.md in components/)
 read src/api/v1/users.ts         → src/api/CLAUDE.md   (nested_traversal)
                                    └─ @../../standards/api.md   (include, loads with its parent)
```

**Rules**
- A folder CLAUDE.md loads **only when Claude works in that folder**.
- `@import` keeps files modular, but the imported file loads **together with** its parent.
- Neither one targets "a file type across many folders". That's a rule with `paths` (E3).

---

## 4.5 ✅ E3 · `.claude/rules` with `paths`: `*` vs `**` (O16)

**Status: done.** After the fix, your log showed `path_glob_match` with `"globs": ["src/api/**/*.ts"]` triggered by `v2/orders.ts`.

```markdown
---
paths:
  - "src/api/**/*.ts"
---
API rule: every exported function returns a Result object ({ ok, value } or { ok, error }).
```

| Glob | `src/api/x.ts` | `src/api/v2/orders.ts` |
|---|---|---|
| `src/api/*.ts` | ✅ | ❌ `*` stays in one folder |
| `src/api/**/*.ts` | ✅ | ✅ `**` crosses folders |
| `**/*.test.tsx` | n/a | any test file, anywhere |

- A rule **without** `paths` always loads at session start (`general.md`).
- A wrong glob fails **silently**: no error, the rule just never loads.

🎯 **Exam shape:** "conventions for test files spread across the codebase" → **one** rule file with `paths` and `**`. It beats a CLAUDE.md per folder, a skill, or one giant CLAUDE.md.

---

## 4.6 ⬜ E4 · Command vs skill vs personal skill (O16)

**The precedence ladder for the same name:**

```
 🥇 PERSONAL skill   ~/.claude/skills/team-review/     ← wins, for you only
 🥈 PROJECT skill    .claude/skills/team-review/
 🥉 TEAM COMMAND     .claude/commands/team-review.md   ← loses to a same-name skill
```

**Anatomy of a skill** (`.claude/skills/<name>/SKILL.md`):

```markdown
---
description: Map a module's files and exported functions. Use when asked to explain an unfamiliar module.
argument-hint: [module-path]
context: fork             # optional: run in an isolated context (4.7)
agent: Explore            # optional: which agent runs the fork
allowed-tools: Bash(touch *)
disallowed-tools: Edit Write
---
Map the module at $ARGUMENTS.          ← $ARGUMENTS = whatever the user typed after /map-module
```

- The **description** matters: Claude uses it to decide when a skill is relevant.
- Skills load **on demand**. Until then only the short description sits in context. CLAUDE.md loads **always**.

🎯 **Exam answers**
- A team-wide command → commit it under **`.claude/commands/`**.
- A personal variant → `~/.claude/`, with a **different name**, so it doesn't shadow the team's version.

> ⚖️ Docs today: commands merged into skills, and both create `/name`. A same-name personal skill also works (personal beats project, for that user). **Exam: use a different name.**

🔧 README E4 (it touches `~/.claude/skills/`, so clean up after).

---

## 4.7 🚨 E5 · `context: fork` + `argument-hint` · O14 · you scored 0%

> 🚨 **WEAK SPOT · O14 · 0%.** One idea, two traps. Learn both.

**In one line:** a forked skill runs in its **own isolated context**, so its verbose work doesn't fill your main conversation. You get back a short result.

```
 WITHOUT context: fork                          WITH context: fork
 main conversation                              main conversation
 ├─ you: /map-module src/api                    ├─ you: /map-module src/api
 ├─ 📄 users.ts printed in full                  │     ┌───────────── isolated fork ─────────────┐
 ├─ 📄 orders.ts printed in full     😵 context  │     │ reads every file, prints everything     │
 ├─ 📄 ... every file ...               fills up │     └─────────────────────────────────────────┘
 └─ summary                                     └─ ✉️  short result message          🙂 small
```

**Trap 1: the fork has amnesia.** It sees **only the skill text and its arguments**, not your conversation.

```
 you:   The module I care about is src/api.
 you:   /map-module                 ← no argument
 fork:  ??? which module?           ← it never saw your earlier message
```

> ⚠️ The lab's own `map-module/SKILL.md` says *"If no path was given, use the module the user mentioned earlier in the conversation."* That line **breaks** once you add `context: fork`. That's exactly what E5 step 3 shows. A forked skill must be **self-contained**: require the argument, or state everything it needs.

**Trap 2: which agent runs the fork.** `agent: Explore` is great for read-only discovery. But per the docs, Explore and Plan forks **skip CLAUDE.md**. That's why the lab's `pr-review` skill uses the default agent: it needs the team's Review standards.

```markdown
---
description: Independent code review of the files given, against the project's Review standards.
argument-hint: [files-or-dir]
context: fork
disallowed-tools: Edit Write
---
```

> ⚖️ **Guide vs docs**
> - `argument-hint`: guide → **prompts for missing parameters**. Docs today → an autocomplete hint (you see `[module-path]` while typing). **Exam: the guide.**
> - Docs today: a forked skill also runs **in the background** by default in interactive sessions.

🔧 README E5: compare `/context` before and after `/map-module`, with and without `context: fork`.

🧠 **Verbose or exploratory skill → `context: fork`. The fork sees only the skill text + `$ARGUMENTS`, so make it self-contained.**

---

## 4.8 ⬜ E6 · `allowed-tools` vs `disallowed-tools`

| Field | ⚖️ Guide (**exam answer**) | Docs today |
|---|---|---|
| `allowed-tools` | **Restricts** which tools the skill can use | **Pre-approves** the listed tools (no prompt) for that turn |
| `disallowed-tools` | n/a | **Removes** tools while the skill runs |
| `argument-hint` | **Prompts** for missing parameters | Autocomplete hint |

**What E6 shows with `/touch-note`** (`allowed-tools: Bash(touch *)`):

```
 1. With allowed-tools: Bash(touch *)   → runs, NO prompt        (pre-approved)
 2. Line removed                        → PROMPT appears
 3. disallowed-tools: Bash              → no Bash at all, can't run
```

🧠 **Exam: `allowed-tools` restricts. In practice it pre-approves. Know both, answer per the guide.**

---

## 4.9 🚨 E7 · Permissions: deny > ask > allow · O16

> 🚨 **WEAK SPOT · part of O16.** "Tested beyond the guide", so expect detail.

```
 request ──► any DENY rule matches? ──yes──► ⛔ REFUSED  (nothing can override it)
                  │ no
                  ▼
             any ASK rule matches?  ──yes──► ❓ PROMPT you
                  │ no
                  ▼
             any ALLOW rule matches? ──yes──► ✅ runs SILENTLY
                  │ no
                  ▼
             the permission mode's default (usually: prompt)
```

**The lab's team rules** (`sandbox/.claude/settings.json`):

```json
"permissions": {
  "allow": ["Bash(python3 -m unittest *)"],
  "ask":   ["Bash(git push *)"],
  "deny":  ["Read(./.env)", "Edit(db/migrations/**)"]
}
```

| Request | Result | Why |
|---|---|---|
| `show me .env` (or `cat .env`) | ⛔ refused | Read deny. The lab expects it to block `cat` too. |
| `add a column to db/migrations/001_init.sql` | ⛔ refused | Edit deny |
| `create db/migrations/002_email.sql` | ⛔ refused | Edit rules cover **every** file-writing tool, Write included |
| `run git push` | ❓ prompt | ask |
| `run the python tests` | ✅ silent | allow. ⚠️ On this PC Claude may use `python`, not `python3`, and then it prompts. |
| `.env` again, with `allow Read(./.env)` in `settings.local.json` | ⛔ **still refused** | A deny in **any** file beats an allow in **any** file |

**The three settings files**

| File | Scope | Committed? |
|---|---|---|
| `~/.claude/settings.json` | You, every project | n/a |
| `.claude/settings.json` | Team | ✅ yes |
| `.claude/settings.local.json` | You, this project | ❌ no |

`/permissions` shows each rule and **which file it came from**.

**Permission modes:** `default` · `acceptEdits` · `plan` · `dontAsk` (anything that would prompt is denied, which is useful in CI) · `bypassPermissions`. Shift+Tab cycles modes in a session. `--permission-mode <mode>` sets one at start.

🎯 **Exam shape:** "must never" for a known path or command → a **deny rule**. CLAUDE.md text is a **request**, not enforcement.

🧠 **Deny beats everything. A local allow can't punch a hole in a team deny.**

---

## 4.10 🚨 E8 · Hooks: PreToolUse blocks, PostToolUse is after the fact · O16

> 🚨 **WEAK SPOT · part of O16.** The single most testable fact: **only exit code 2 blocks.**

```
 Claude wants to run:  rm -rf build
          │
          ▼
 ┌───────────────────┐   exit 2  ──► ⛔ BLOCKED. stderr is sent to Claude as the reason.
 │ PreToolUse hook   │   exit 0  ──► continue
 │ (matcher: Bash)   │   exit 1  ──► ⚠️ non-blocking error: the command STILL RUNS
 └─────────┬─────────┘
           ▼
   permission rules (deny / ask / allow)
           ▼
   🔧 the tool runs
           ▼
 ┌───────────────────┐
 │ PostToolUse hook  │   can log, format or complain, but it's TOO LATE to stop it
 └───────────────────┘
```

**The lab's hook** (`.claude/hooks/block_rm.py`):

```python
command = json.load(sys.stdin).get("tool_input", {}).get("command", "")
if "rm -rf" in command:
    print("Blocked by project hook: rm -rf is not allowed in this repo. Delete specific files instead.",
          file=sys.stderr)
    sys.exit(2)          # 2 = block. 1 would NOT block.
sys.exit(0)
```

**Wired up in `settings.json`:**

```json
"PreToolUse":  [{ "matcher": "Bash",       "hooks": [{ "type": "command", "command": "python",
                  "args": ["${CLAUDE_PROJECT_DIR}/.claude/hooks/block_rm.py"] }] }],
"PostToolUse": [{ "matcher": "Edit|Write", "hooks": [{ "type": "command", "command": "python",
                  "args": ["${CLAUDE_PROJECT_DIR}/.claude/hooks/log_edits.py"] }] }]
```

| Exit code | PreToolUse | PostToolUse |
|---|---|---|
| **0** | Proceed | Fine |
| **2** | **Block**. stderr goes to Claude. | The tool already ran. stderr goes to Claude as feedback. |
| Other (1...) | **Non-blocking** error. The action proceeds. | Non-blocking error |

**What E8 shows**

| Setup | Result |
|---|---|
| PreToolUse `block_rm.py` | Blocked before any prompt. Claude reads your reason. `build/x` survives. |
| Same script as **PostToolUse** | The command ran first. The hook only complains afterwards. `build/x` is gone. |
| PreToolUse hook that returns `"permissionDecision": "allow"` for Read, plus the `.env` deny rule | **Still refused.** A hook's allow doesn't bypass a deny rule. |

**Which one to pick**

```
 Static, known path or command ("never read .env")       → deny rule  (lighter, simplest guarantee)
 Dynamic check on the content ("contains rm -rf",
   "refund amount > 500")                                → PreToolUse hook, exit 2
 After the action (format, log, normalize)               → PostToolUse hook
```

Other events exist (the lab's load log uses `InstructionsLoaded`). `/hooks` lists what's configured.

🧠 **Block before → PreToolUse, exit 2 (exit 1 doesn't block). After → PostToolUse. A hook's allow can't beat a deny.**

---

## 4.11 🚨 E9 · Plan mode vs direct vs multi-phase · O8 · you scored 0%

> 🚨 **WEAK SPOT · O8 · 0%.** Pick the mode from the **size and ambiguity** of the task, not from habit.

```
 Can you describe the whole diff in ONE sentence, and the cause is clear (e.g. a stack trace)?
 │
 ├─ YES ──► ⚡ DIRECT EXECUTION: just ask for the fix
 │
 └─ NO ───► Multi-file? Architectural? Several valid approaches? Someone must sign off?
            │
            ├─ YES ──► 🗺️ PLAN MODE: explore → propose a plan → YOU approve → execute
            │
            └─ Huge, and you don't know the codebase yet?
                   └──► 🔍 Explore subagent first (keeps your context clean), then plan
```

**Multi-phase:** for big changes, split the work into phases with a checkpoint after each. Plan → do phase 1 → verify → approve → phase 2.

**How to get into plan mode:** `claude --permission-mode plan`, or **Shift+Tab** in a session. In plan mode Claude reads and explores but **doesn't edit** until you approve.

**E9's four tasks**

| Task | Mode | Why |
|---|---|---|
| "`orderTotal` returns NaN when qty is undefined; default qty to 1." | ⚡ **Direct** | One sentence, clear cause |
| "Replace every fetch in `src/api` with a shared `httpClient` with retries and typed errors." | 🗺️ **Plan** | Multi-file, architectural |
| "Add Slack notifications for failed orders." | 🗺️ **Plan** | Several valid approaches (webhook vs bot token): see options first |
| "Find every fetch call and give a 3-line summary." | 🔍 **Explore subagent** | Verbose discovery, and your context stays small |

❌ **Anti-patterns**
- Plan mode for a typo fix. Pure overhead.
- Direct execution for a cross-cutting refactor. You get half-done edits and rework.
- Reading 40 files in the main context instead of using Explore.

🧠 **One-sentence diff → direct. Multi-file, architectural, several approaches or sign-off → plan → approve → execute. Verbose discovery → Explore.**

---

## 4.12 🚨 E10 · Iterative refinement · O12 · you scored 0%

> 🚨 **WEAK SPOT · O12 · 0%.** Match the **symptom** to the **technique**.

| Symptom | Technique | Example |
|---|---|---|
| A prose spec gets interpreted differently each time | **2–3 concrete input → output examples** | `{"st":"A","since":"05/03/24"}` → `{"status":"active","since":"2024-03-05"}` |
| You need correctness you can check | **Tests first** | "Make `py/test_status.py` pass. Run the tests after each change and fix only what fails." |
| Something is still wrong | **Iterate on the specific failure** | Paste the failing test name and the exact error, not "it's still broken" |
| Two bugs that **interact** (fixing one changes the other) | **One detailed message** covering both | Date parsing + missing-key handling |
| **Independent** bugs | **One at a time** | Fix, verify, next |
| Unfamiliar domain, unclear requirements | **Interview pattern** | "Before adding a cache to getUser, interview me about invalidation and failure modes. No code until I answer." |

```
 Interacting bugs                         Independent bugs
 ┌─────────┐     ┌─────────┐              ┌─────────┐   ┌─────────┐
 │ parser  │ ◄─► │ missing │              │ typo in │   │ wrong   │
 │ bug     │     │ keys    │              │ header  │   │ color   │
 └─────────┘     └─────────┘              └─────────┘   └─────────┘
 fix one → the other changes              fixing one doesn't touch the other
 → ONE message with both                  → one at a time
```

❌ **Anti-patterns**
- "It's still broken, fix it." Too vague.
- Fixing interacting bugs one per turn. You get whack-a-mole.
- One giant prompt for many independent bugs.
- Writing a longer prose spec when examples would settle it.

> ⚖️ The guide says **2–3** input/output examples here (TS 3.5), and 2–4 targeted few-shot examples in general. Docs suggest 3–5. **Keep the guide numbers.**

🧠 **Inconsistent → examples. Checkable → tests first. Interacting → one message. Independent → one at a time. Unfamiliar → interview.**

---

## 4.13 🚨 E11 · Claude Code in CI · O11 (50%) · O13 (0%) · O30 (50%)

> 🚨🚨 **WEAK SPOT · three objectives in one exercise.** Learn the flag table and the three pillars of review config.

**A CI review job, end to end** (this is `ci/review.sh`):

```
 PR opened
    │
    ▼
 claude -p "Review the files under src/ against the Review standards in CLAUDE.md." \
   --output-format json \
   --json-schema "$(cat ci/review-schema.json)" \
   --max-turns 8 \
   --max-budget-usd 1.00 \
   --permission-mode dontAsk \
   --tools "Read,Grep,Glob"
    │
    ▼
 JSON envelope ──► structured_output.findings[] ──► post PR comments
    │
    ▼
 next push: pass the prior findings in ──► only NEW or STILL-UNADDRESSED issues
```

### The flag table (O11)

| Flag | What it does | Group |
|---|---|---|
| `-p` / `--print` | Non-interactive (headless) run | Required for CI |
| `--output-format json` | JSON envelope: `result`, `session_id`, `total_cost_usd`, `subtype`, `num_turns` | Parse it |
| `--json-schema '<schema>'` | The validated object arrives in **`structured_output`** | Guaranteed shape |
| `--max-turns N` | Caps turns. **Non-zero exit** when the cap is hit. | 🔒 Cap (a flag, not prompt text) |
| `--max-budget-usd X` | Stops near the spend cap (can pass it slightly) | 🔒 Cap |
| `--permission-mode dontAsk` | Anything that would prompt is **denied** | 🔒 Lock down |
| `--allowedTools "Edit"` | **Pre-approves**: runs without a prompt | ✅ Approve |
| `--tools "Read,Grep,Glob"` | **Only these built-in tools exist** | 🚫 Restrict |
| `--disallowedTools "Edit"` | **Removes** tools | 🚫 Restrict |
| `--bare` | Skips CLAUDE.md, hooks, skills and MCP. Needs `ANTHROPIC_API_KEY`. | Minimal run |
| `--append-system-prompt-file F` | Adds a file to the system prompt | Pass instructions back in |
| `-r ID`, `--fork-session` | Resume or fork a session | Sessions |
| `-p "/team-review src/api"` | Runs a command or skill headless | Reuse team commands |

> 🧠 **Memory hook:** `--allowedTools` = ✅ **yes, without asking**. `--tools` / `--disallowedTools` = 🚫 **what exists at all**.

**What each `flags_demo.sh` step shows**

| Step | Flags | What happens |
|---|---|---|
| 1 | `-p --output-format json` | The envelope has `result`, `session_id`, `total_cost_usd` |
| 2 | `+ --json-schema` | The validated object is in `structured_output` |
| 3 | `--max-turns 1` on a multi-step task | Non-zero exit when the cap is hit |
| 4 | `--max-budget-usd 0.05` | Stops near the cap |
| 5 | `--permission-mode dontAsk` | The edit is **denied** |
| 6 | `dontAsk + --allowedTools "Edit"` | The edit is **allowed** (pre-approved) |
| 7 | `--tools "Read,Grep,Glob"` | Edit **doesn't exist** |
| 8 | `--bare` | No project instructions, until you pass the file back with `--append-system-prompt-file` |
| 9 | `-p "/team-review src/api"` | Runs the team command headless |

### The three pillars of review config (O13)

```
 ┌────────────────────────┐  ┌────────────────────────┐  ┌────────────────────────┐
 │ 1. STANDARDS           │  │ 2. RESTRICTED TOOLS    │  │ 3. STRUCTURED OUTPUT   │
 │ in project CLAUDE.md   │  │ read-only:             │  │ --json-schema with     │
 │ report / don't report  │  │ --tools "Read,Grep,    │  │ file, line, severity,  │
 │ accepted patterns      │  │          Glob"         │  │ category, issue, fix,  │
 │ severity definitions   │  │ --permission-mode      │  │ detected_pattern       │
 │ (every run loads it)   │  │   dontAsk              │  │                        │
 └────────────────────────┘  └────────────────────────┘  └────────────────────────┘
          + re-review with the prior findings      + an independent reviewer instance
```

**Pillar 1: the standards** (`sandbox/CLAUDE.md`, loaded by every CI run):

```markdown
## Review standards (used by /team-review and ci/review.sh)
Report: bugs that change behavior, missing error handling on network calls, security issues, broken API contracts.
Do not report: formatting, naming preferences, missing docstrings, TODO comments.
Accepted here, do not flag: `fetch(...).then(r => r.json())` in src/components (demo code).
Severity: blocker = wrong result or data loss; major = unhandled failure path; minor = everything else reportable.
```

**Pillar 3: the schema** (`ci/review-schema.json`): each finding requires `file`, `line`, `severity` (blocker/major/minor), `category` (bug/error_handling/security/api_contract/other), `issue`, `suggested_fix` and **`detected_pattern`**, the code construct that triggered it. That makes false positives traceable.

**Re-review:** `bash ci/review.sh ci/out/findings.json` passes the prior findings in: *"Report only NEW or STILL-UNADDRESSED issues; skip anything already fixed."* → no duplicate PR comments.

**Independent reviewer** (`ci/independent_review.sh`): the session that **wrote** the change keeps its own reasoning and blind spots. A **fresh instance** reviews better.

### False positives via persistent conventions (O30)

> 🚨 **WEAK SPOT · O30 · 50%.**

- Put **accepted patterns** in project CLAUDE.md ("Accepted here, do not flag: ..."), so **every** run gets them.
- Use **explicit report / don't-report categories** and severity definitions with examples.
- `detected_pattern` shows **what** triggered each finding.
- A noisy category destroying trust? **Temporarily disable it**, fix the criteria, then turn it back on.
- ❌ "Be conservative" or "only report findings you're 90% sure about" does **not** fix precision.

❌ **CI anti-patterns**
- "Stop after 8 turns" in the prompt. That's not a cap. Use `--max-turns`.
- `CLAUDE_HEADLESS=1`, `--batch`, `.claude/config.json`. **These don't exist.**
- Parsing free-text output with a regex instead of `--json-schema`.
- Giving the CI reviewer Edit or Write.
- Re-running without the prior findings, which duplicates comments.
- The generating session reviewing its own change.

> ⚖️ The guide names `-p`, `--output-format json` and `--json-schema`. The lab's docs check found that `--max-turns`, `--max-budget-usd`, `--permission-mode dontAsk`, `--tools`, `--disallowedTools` and `--bare` are **also real, and tested on your exam**.

🔧 README E11, from `d3-claude-code/` in Git Bash.
> ⚠️ **On this PC:** `ci/flags_demo.sh`, `ci/review.sh` and `ci/independent_review.sh` call `python3`, which is only a Microsoft Store stub here. Those steps will fail until the scripts use `python`. Ask Claude to switch them before you run E11.

🧠 **CI = `-p` + JSON + schema. Caps are flags. `allowedTools` pre-approves, `tools`/`disallowedTools` restrict. Standards in project CLAUDE.md. Prior findings on re-runs. Independent reviewer.**

---

## 4.14 🚨 E12 · Test generation quality · O15 · you scored 0%

> 🚨 **WEAK SPOT · O15 · 0%.** Two rules. That's it.

**What `ci/testgen.sh` shows:**

```
 WITHOUT existing tests                     WITH existing tests + standards
 "Suggest 8 unit test cases"                "Existing tests (do not duplicate these): ...
                                             Testing standards: behavior via public functions;
                                             cover edge cases (missing price, negative qty, ...)"
 → repeats add, remove, empty-total  😕     → avoids them, targets edge cases  🙂
```

**The two rules**
1. **Give it the existing tests** ("do not duplicate these scenarios").
2. **Put testing standards in project CLAUDE.md**, so every run (CI included) loads them: valuable-test criteria, edge cases to cover, fixture conventions.

```markdown
## Test generation standards   (sandbox/CLAUDE.md)
- Test behavior through the public function, not implementation details.
- Do not duplicate scenarios already in the existing test file.
- Cover edge cases: missing keys, empty values, invalid input.
- Fixture: use plain dicts built inline; there is no factory module.
```

❌ **Anti-patterns**
- "Write tests for cart.py" with nothing else.
- Testing implementation details instead of behavior.
- Claude inventing a fixture factory that doesn't exist. Prevent it by stating the fixture convention.
- "Generate novel tests" without showing what exists.

`--tools ""` (used in `testgen.sh`) disables all built-in tools, so Claude sees only what you paste.

🧠 **Existing tests in the prompt + test standards in project CLAUDE.md.**

---

## 4.15 ⬜ E13 · Sessions from the CLI · O2

The theory is in **2.8**. Here's the CLI drill:

```bash
claude -n orders-review                  # 1. name the session, then: "Read src/api/v2/orders.ts, list risks R1 to R3."
# ... /exit, edit orderTotal yourself ...
claude --resume orders-review            # 2. "Only orders.ts changed: orderTotal now takes a discount.
                                         #     Re-read only that file and re-check R1 to R3."
claude -p -r orders-review "OK" --output-format json                 # same session_id
claude -p -r orders-review --fork-session "OK" --output-format json  # NEW session_id
```

🎯 **The fork gets a new ID. Resume keeps the same one.**

---

## 4.16 🚨 E14 · Built-in tools, Edit fallback, scratchpad, `/compact` · O17 · O32 · O20

> 🚨 **WEAK SPOT · O17 (40%), O32 (50%), O20 (50%).** Tool picking is in **3.7**. Here: keeping facts alive over a long exploration.

| Action | What survives | Use it for |
|---|---|---|
| `/compact keep the call chains and file paths` | A summary guided by your focus. **Exact details can blur.** | Making room while keeping the gist |
| `/clear` | Nothing from the conversation. CLAUDE.md reloads. | A fresh start |
| 📝 Scratchpad file (`notes/exploration.md`) | **Everything you wrote, exactly** (file:line) | Exact facts across `/compact` and `/clear` |
| Explore / subagent | Its verbose work stays out. You get the summary. | Verbose discovery |

**The E14 pattern:**

```
 "Trace getUser and getOrder; after each step append confirmed facts with file:line to notes/exploration.md."
        │
        ▼
 /compact keep the call chains and file paths      (some details may blur)
        │
        ▼
 /clear  →  "Read notes/exploration.md first, then answer..."   ✅ exact facts recovered
```

🧠 **Scratchpad file for exact facts. Subagents for verbose discovery. `/compact` with a focus, and don't trust it for line numbers.**

---

## 4.17 ⬜ E15 · MCP in Claude Code · O34 · O35 🟩

The theory is in **3.5** and **3.6**. What E15 shows:

| Lookup | Result | Retry? |
|---|---|---|
| `A-503` | Transient error | ✅ retryable |
| `A-OLD` | Business error | ❌ not retryable |
| `A-999` with `find=true` | **Empty result, not an error** | n/a |

Resources: `catalog://issues` and `schema://orders`.

> ⚠️ **On this PC:** `.mcp.json` falls back to `python3` (a Store stub). Set `LAB_PYTHON` to the venv python **in the shell where you start `claude`**.

---

## 4.18 🚨 E16 · Subagent isolation and tool scoping · O3 · O33

> 🚨 **WEAK SPOT · O3 (33%), O33 (50%).**

**A subagent file** (`.claude/agents/synth.md`):

```markdown
---
name: synth
description: Writes a short cited paragraph from findings given in its prompt. Synthesis only.
tools: Read                       ← config restricts tools: no Write, no Edit
---
Use only facts that appear in your task prompt. Keep the source next to every claim.
If a fact you need is not in the prompt, write "not provided". Never invent sources.
```

| You do | synth does | Lesson |
|---|---|---|
| Delegate with a bare prompt: "Write one paragraph on the refund limit." | Writes **"not provided"** | It sees only its prompt |
| Delegate with F1 + its source in the prompt | Writes a **cited paragraph** | Pass complete findings with sources |
| "Ask synth to create notes/x.txt" | **Can't**. It has no Write or Edit. | Restrict tools in **config**, not prompt text |

🧠 **The subagent sees only its prompt (plus CLAUDE.md for non-Explore types). Restrict tools in config.**

---

## 4.19 Quick reference: commands you must recognize

| In a session | Does |
|---|---|
| `/context` | Context usage and loaded memory files |
| `/memory` | Lists and opens memory files (⚖️ the guide's "verify what loaded" answer) |
| `/permissions` | Rules, and which file each came from |
| `/hooks` | Configured hooks |
| `/mcp` | MCP server status |
| `/agents` | Manage subagents |
| `/compact <focus>` | Summarize the conversation, keeping your focus |
| `/clear` | Wipe the conversation |
| `/exit` | End the session |
| **Shift+Tab** | Cycle permission modes (includes plan mode) |

| In the shell | Does |
|---|---|
| `claude -n NAME` | Start a named session |
| `claude --resume NAME` / `-r` | Resume a session |
| `claude -c` | Continue the most recent session here |
| `claude --permission-mode plan` | Start in plan mode |
| `claude -p "..."` | Headless run (CI) |
| `claude mcp list / add / remove` | Manage MCP servers |

---

### 🧠 Part 4 in 12 lines

```
Always → CLAUDE.md (team: project · me: ~/.claude). Teammate missing it → it's in user scope.
Folder CLAUDE.md loads when Claude works there. @import loads with its parent.
File type across folders → .claude/rules with paths + **  (* stays in one folder, fails silently).
Team command → .claude/commands/. Personal variant → ~/.claude with a DIFFERENT name.
Precedence for one name: personal skill > project skill > command.
Verbose skill → context: fork. The fork sees only skill text + $ARGUMENTS → self-contained.
Permissions: deny > ask > allow. A local allow never beats a team deny.
Hooks: PreToolUse exit 2 blocks (exit 1 doesn't). PostToolUse is after the fact. A hook allow ≠ beat deny.
One-sentence diff → direct. Multi-file / architectural / options / sign-off → plan → approve → execute.
Refinement: examples · tests first · specific failures · interacting together · independent apart · interview.
CI: -p + --output-format json + --json-schema · caps = flags · allowedTools approves · tools restricts.
Reviews: standards in project CLAUDE.md · prior findings · independent instance. Tests: give existing tests.
```

---

# Part 5 · D4 Prompt Engineering & Structured Output (20%)

> Strong on output methods (O24, O25, O28, O31 at 100%). Gaps: **O29 at 0%**, **O26 at 33%**, **O30 at 50%**, O23 at 75%.

## 5.1 Explicit criteria vs vague instructions · O31 🟩 · O30 🚨 50%

**In one line:** "be conservative" doesn't fix precision. **Explicit categories** do.

❌ **Vague:**
```
Review this code. Be conservative and only report high-confidence issues.
```

✅ **Explicit:**
```
Report:      bugs that change behavior · missing error handling on network calls ·
             security issues · broken API contracts
Don't report: formatting · naming preferences · missing docstrings · TODO comments
Accepted:    fetch(...).then(r => r.json()) in src/components (demo code)
Severity:    blocker = wrong result or data loss · major = unhandled failure path · minor = the rest
```
Add **few-shot pairs**: one acceptable pattern next to one genuine issue that looks similar.

- Persistent conventions belong in **project CLAUDE.md**, so every review run gets them (see 4.13).
- ❌ "Only report findings you're 90% sure about" → false positives barely move (lab `d4/01` exercise 4).

🔧 `python d4-prompting/01_explicit_criteria_fewshot.py`

---

## 5.2 Few-shot examples: how many, which ones

- ⚖️ **Guide: 2–4 targeted examples** (2–3 input/output examples in TS 3.5). Docs suggest 3–5. **Keep the guide.**
- **Targeted** means they cover the confusing cases: edge cases, look-alikes, each document layout. Not random samples.

---

## 5.3 🟩 The most reliable structured output · O25

**In one line:** use a **tool schema** (`tool_use`) with `tool_choice` `any` or forced. It guarantees the **shape**, not the **truth**.

```
 tool schema  ──►  ✅ valid JSON, right fields, right types      (syntax)
              ──►  ❌ does NOT guarantee correct values           (semantics)
                     → add semantic validation: totals add up, dates are real, IDs exist
```

---

## 5.4 🚨 Nullable fields, `unclear`, `other` · O26 · you scored 33%

> 🚨 **WEAK SPOT · O26 · 33%.** Required fields make the model **invent** values.

**The lab invoice:** no due date anywhere. The terms say *"Payment due upon mutual agreement"*.

| Schema | Output | Verdict |
|---|---|---|
| **A:** `due_date` required string · `terms` closed enum `[net_30, net_60, on_receipt]` | `due_date: "<UNKNOWN>"` · `terms: "on_receipt"` | 😱 Invented values |
| **B:** `due_date` nullable · `terms` enum + `unclear` + `other` · `terms_detail` string | `due_date: null` · `terms: "unclear"` · `terms_detail: "Payment due upon mutual agreement"` | ✅ Honest |

```json
"due_date":     { "type": ["string", "null"], "description": "ISO date, or null if the document doesn't state one" },
"terms":        { "type": "string", "enum": ["net_30", "net_60", "on_receipt", "unclear", "other"] },
"terms_detail": { "type": ["string", "null"], "description": "Raw text when terms is unclear or other" }
```

**The decision**

```
 Might the info be ABSENT from the document?        → nullable / optional field
 Is it PRESENT but AMBIGUOUS?                       → "unclear"
 Can the category list never be complete?           → "other" + a detail string
```

❌ **Anti-patterns**
- Required everything, plus "write N/A if missing".
- Retrying until the model "finds" the missing field.
- A closed enum for open-world categories.

🔧 `python d4-prompting/02_schema_nullable_enums.py`

🧠 **Absent → null. Ambiguous → `unclear`. Open-ended → `other` + detail.**

---

## 5.5 🚨 Extraction accuracy patterns · O29 · you scored 0%

> 🚨 **WEAK SPOT · O29 · 0%.** The trick is to **diagnose the type of error first**. Each type has its own fix.

```
 What's going wrong with the extraction?
 │
 ├─ Values are there, but in MESSY FORMATS
 │    "3rd Feb 2024" · "02/03/24" · "2024.02.03" · "$1,200.00" · "1200 USD"
 │       └──► 📏 NORMALIZATION RULES in the prompt, next to the schema
 │
 ├─ Fields come back empty or wrong only for certain document LAYOUTS
 │    typed invoices OK, scanned receipts miss the total
 │       └──► 🧩 FEW-SHOT: one example PER LAYOUT
 │
 ├─ The info is simply NOT in the document
 │       └──► ∅ NULLABLE field. A retry can't create it.
 │
 ├─ Output sometimes breaks format or arithmetic
 │       └──► 🔁 VALIDATE + RETRY with the document, the failed output and the exact error (5.6)
 │
 └─ The source contradicts itself (line items ≠ stated total)
         └──► ⚖️ extract BOTH: stated_total + calculated_total + conflict_detected
```

**Normalization rules, an example:**
```
Normalization rules:
- Dates → ISO 8601 (YYYY-MM-DD). Read "02/03/24" as DD/MM/YY.
- Amounts → a number without symbols or separators; the currency goes in a separate ISO code field.
- "N/A", "—", blank → null.
```

**What the lab shows** (`d4/03`): schema only → errors. + rules → the format errors go. + one example per layout → the layout errors go. Delete the rules but keep the few-shot (exercise 1) → the **format** fields break again.

🔧 `python d4-prompting/03_normalization_fewshot.py`

🧠 **Formats → rules. Layouts → one example each. Absent → null. Slips → retry with the error. Contradictions → both values + a conflict flag.**

---

## 5.6 Validation and retry (TS 4.4)

**In one line:** a retry must carry the **document**, the **failed output** and the **specific error**.

```
Here is the document:            <document>
Your previous extraction:        <json>
Validation error:                invoice_date "2024-13-05" is not a valid date (month 13).
Re-read the date in the document and fix only what the error describes.
```

| A retry CAN fix | A retry CANNOT fix |
|---|---|
| Format slips (bad date format) | Info that's **absent** from the source → nullable |
| Structure slips (missing bracket, wrong type) | A source that contradicts itself → `stated_total` + `calculated_total` + `conflict_detected` |
| Arithmetic slips | |

> ⚠️ Lab `d4/04` exercise 3: retry with "stated_total is required" when the document has none → the model **invents a number**.

🔧 `python d4-prompting/04_validation_retry.py`

---

## 5.7 🟨 Sync API vs Message Batches · O23 · 75%

| | ⚡ Sync Messages API | 📦 Message Batches |
|---|---|---|
| Latency | Seconds | **Up to 24 h**, no latency SLA |
| Cost | Normal | **50% cheaper** |
| Use for | **Blocking** work: pre-merge checks, a user waiting | **Overnight, weekly**, backfills |
| Result order | n/a | **Not guaranteed** → correlate by **`custom_id`** |
| Failures | Retry the call | Resubmit **only the failed `custom_id`s**, with a fix (e.g. chunk the oversized doc) |
| Tool use | Multi-turn loops | **No tool round trips** inside one request |

**SLA math:** you need results by 08:00 and a batch can take 24 h → submit by **08:00 the day before**, or use sync.

❌ **Anti-patterns:** a batch for a pre-merge check ("it's cheaper"). Assuming results come back in order. Resubmitting the whole batch.

🔧 `python d4-prompting/05_batches.py --sla-only` (free), then the live run.

🧠 **Blocking → sync. Overnight or weekly → batch. Match by `custom_id`. Resubmit only failures.**

---

## 5.8 🟩 Truncated structured output · O28

`stop_reason: "max_tokens"` → the output was cut off and the JSON is incomplete.
- ✅ **Split** into scoped calls (per section, per page) and **merge in code**.
- ❌ Just raising `max_tokens` is the weak fix.

🔧 `python d4-prompting/06_truncation_split.py`

---

## 5.9 🟩 Multi-pass review · O24

```
 ❌ one pass over 30 files            ✅ per-file passes + an integration pass
    attention spreads thin               file 1 ┐
    cross-file bugs missed               file 2 ├─► local issues
                                         file 3 ┘
                                         integration pass ──► cross-file data flow
```
- Distractors: "a bigger context window", "a consensus of 3 runs".
- Self-review in the generating session is weaker than an **independent instance**.

🔧 `python d4-prompting/07_multipass_review.py`

---

### 🧠 Part 5 in 8 lines

```
Precision → explicit report/skip categories + severity examples + few-shot pairs. Not "be conservative".
Few-shot: 2–4 targeted (guide), 2–3 I/O examples in TS 3.5.
Tool schema = guaranteed SHAPE, not truth → add semantic validation.
Absent → nullable · ambiguous → "unclear" · open-ended → "other" + detail.
Formats → normalization rules · layouts → one few-shot per layout.
Retry = document + failed output + exact error. It can't create missing data. Contradiction → both values + conflict flag.
Blocking → sync · overnight → batch (50% off, ≤24 h, custom_id, resubmit only failures).
Truncated → split and merge in code. Many files → per-file passes + integration pass.
```

---

# Part 6 · D5 Context Management & Reliability (15%)

> Your strongest domain (O18, O19, O21, O22 at 100%). One gap: **O20 at 50%**.

## 6.1 🟩 Case-facts block and trimming · O21

**In one line:** summaries lose numbers. Keep the hard facts in a **separate block that's never summarized**.

```
 ┌──────────────────────── every prompt ─────────────────────────┐
 │ 📌 CASE FACTS (never summarized)                               │
 │    order A-7731 · refund 15% · promised by 14 Nov · C-88       │
 ├────────────────────────────────────────────────────────────────┤
 │ 📝 summary of older turns                                      │
 ├────────────────────────────────────────────────────────────────┤
 │ 💬 recent turns, word for word                                 │
 ├────────────────────────────────────────────────────────────────┤
 │ 🔧 tool results TRIMMED to the fields you need                 │
 └────────────────────────────────────────────────────────────────┘
```

- In the lab, a plain summary loses "15%" and "14 November". The case-facts block keeps them.
- Facts that belong there: amounts, percentages, dates, IDs, promises made.
- **Lost in the middle:** put key findings **first**, with section headers.

🔧 `python d5-context/01_case_facts_and_trimming.py`

---

## 6.2 Escalation (TS 5.2)

| ✅ Escalate | ❌ Don't escalate on |
|---|---|
| The customer **explicitly asks for a human** → **immediately**, don't try to solve it first | The customer **sounds frustrated** (sentiment). Acknowledge it and keep helping, unless they ask for a human. |
| A **policy gap** or exception the rules don't cover | The model's **self-rated low confidence** |
| **No meaningful progress** after real attempts | |

- **Several matching customers** → ask for **another identifier**. Never pick one with a heuristic.
- Put the criteria in the prompt **explicitly**, with few-shot examples.

🔧 `python d5-context/02_escalation.py`

---

## 6.3 Error propagation across agents (TS 5.3)

```
 Subagent search times out on one subtopic
        │
        ▼
 ✅ return: { type: "transient", attempted: "search 'AI in music'",
             partial_results: [...], alternatives: ["retry later", "use cached index"] }
        │
        ▼
 Coordinator: retry locally? continue the others? → final report annotates:
             "Coverage gap: music sector, search timed out"
```

- **Structured** context: type, what was attempted, partial results, alternatives.
- An **access failure is not an empty result**.
- Retry **transient** errors locally.
- **Never** mark a failure as success. **Never** kill the whole workflow over one failure.

---

## 6.4 🚨 Context across long exploration · O20 · you scored 50%

> 🚨 **WEAK SPOT · O20 · 50%.** Four tools. Know when each one fits.

| Problem | Tool |
|---|---|
| Exact facts (file:line) must survive `/compact` or `/clear` | 📝 **Scratchpad file** of confirmed facts |
| Discovery is verbose (reading 40 files) | 🔍 **Subagent / Explore**. The main context gets a summary. |
| The context is filling up, but the gist matters | 🗜️ **`/compact` with a focus** ("keep call chains and file paths") |
| A long multi-agent run might crash | 💾 **State manifest**: completed and pending phases, so the run resumes |
| The old context is stale | 🆕 **Fresh session + structured summary** |

❌ **Anti-patterns**
- Keeping everything in the main context until it overflows.
- Trusting `/compact` to keep exact line numbers.
- Re-running everything after a crash instead of resuming from a manifest.

🔧 D3 **E14** and **E16**

🧠 **Scratchpad for exact facts. Subagents for verbose work. Manifest for crashes.**

---

## 6.5 🟩 Provenance and uncertainty in synthesis · O18 · O19

**Subagents return structured claims:**

```json
{ "claim": "AI tools are used by 40% of studios",
  "source": "Industry Survey 2025, p.12",
  "date": "2025-06",
  "method": "survey, n=2,000" }
```

**Synthesis rules**
- Keep the **claim → source → date** mapping all the way to the final output.
- Two credible sources conflict? Show **both side by side** with attribution. Don't pick one silently.
  `Survey A (2025): 40% · Report B (2023): 12%`. The dates may explain the difference: that's change over time, not a contradiction.
- Annotate **coverage gaps**: "No data found for APAC (search timed out)".
- Render by **content type**: tables for numbers, prose for narrative.
- ❌ A prose handoff loses attribution. In the lab, the structured handoff keeps "40% vs 12%" with sources and the prose one doesn't.

🔧 `python d5-context/03_provenance_synthesis.py`

---

## 6.6 🟩 Human review routing · O22

**A high overall accuracy can hide a failing document type.**

```
 Overall accuracy: 98.2%  ✅ looks great...

   typed_invoice      99.8%  ████████████████████  → threshold OK, reduce review
   receipt_photo      95.2%  ███████████████████   → calibrated threshold
   handwritten_form   56.0%  ███████████           → threshold NONE: keep human review 🚨
```

**Before cutting human review**
1. Measure accuracy **by document type AND by field**.
2. Calibrate confidence thresholds on a **labeled validation set**.
3. Keep a **stratified random sample** of **high-confidence** output. In the lab it shows 10% errors in confident handwritten output.
4. Route low-confidence or contradictory output to humans.

❌ The model's **self-reported confidence**, uncalibrated, is not a routing signal.

🔧 `python d5-context/04_review_routing.py` (offline, free)

---

### 🧠 Part 6 in 6 lines

```
Case facts (amounts, %, dates, IDs, promises) in a block OUTSIDE the summary. Trim tool output. Key facts first.
Escalate on: explicit human request (now) · policy gap · no progress. NOT sentiment, NOT self-confidence.
Several customer matches → ask for another identifier.
Errors: structured · access failure ≠ empty · retry transient locally · never fake success · annotate gaps.
Long exploration: scratchpad (exact facts) · subagents (verbose) · /compact (gist) · manifest (crashes).
Synthesis: claim-source-date, conflicts side by side, gaps marked. Routing: by type + field, calibrated, stratified audit.
```

---

# Part 7 · Scenario playbooks 🎬

> Each scenario is a story the questions hang on. Learn the cast and the usual twists.

## 🎧 S1 · Customer Support

**Setup:** an agent with `get_customer`, `lookup_order`, `process_refund`. Policies on identity and refund limits.

| Stem → | Answer |
|---|---|
| Refund issued without identity verification, sometimes | **Code gate** in the refund tool (2.6) |
| Refunds above 500 must go to a human | **PreToolUse hook** deny + structured handoff (2.7) |
| Dates and statuses from the order API confuse the model | **PostToolUse** normalization (2.7) |
| The agent picks `get_customer` for order questions | Fix the **descriptions** first, then check the system prompt keywords (3.1) |
| "Something went wrong" when no order exists | An empty result **is not an error** (3.2) |
| The customer asks for a human | Escalate **immediately** (6.2) |
| Two customers match the name | Ask for **another identifier** (6.2) |
| A long chat forgets the promised refund % | **Case-facts block** (6.1) |
| Profile, orders and tickets fetched one per turn | **Parallel tool calls** in one turn (2.2) 🚨 |

## 💻 S2 · Code Generation with Claude Code

**Setup:** a team adopting Claude Code. Conventions, safety, workflows.

| Stem → | Answer |
|---|---|
| A new hire's Claude ignores the conventions | Move to **project CLAUDE.md** (4.3) 🚨 |
| Test conventions across 30 folders | **Rule with `paths` + `**`** (4.5) 🚨 |
| Never touch migrations | **Deny** `Edit(db/migrations/**)` (4.9) 🚨 |
| Block `rm -rf` anywhere in a command | **PreToolUse, exit 2** (4.10) 🚨 |
| Auto-format after every edit | **PostToolUse** on `Edit\|Write` (4.10) |
| A verbose `/map-module` floods the context | **`context: fork`** (4.7) 🚨 |
| A cross-cutting refactor needs the lead's approval | **Plan mode** (4.11) 🚨 |
| A one-line bug with a stack trace | **Direct** (4.11) 🚨 |
| The spec is misread each time | **2–3 I/O examples** (4.12) 🚨 |
| Yesterday's analysis; one file changed | **Resume + name the file** (2.8) 🚨 |

## 🔬 S3 · Multi-Agent Research

**Setup:** a coordinator with search subagents and a synthesizer.

| Stem → | Answer |
|---|---|
| The report misses whole sectors | Coordinator delegation was **too narrow** → goal + coverage criteria (2.5) 🚨 |
| The synthesizer writes "not provided" or hallucinates | **Pass findings + sources** in its prompt (2.4) 🚨 |
| The synthesizer searches instead of synthesizing | Remove search, give it a **scoped `verify_fact`** (3.3) 🚨 |
| Subagents spawned one per turn | Spawn independent ones **in one response** (2.2) 🚨 |
| The coordinator can't spawn at all | **`allowedTools` must include `Task`** (2.3) |
| One search times out | **Structured error + partial results**, continue, annotate the gap (6.3) |
| Two sources disagree | **Both, side by side, with dates** (6.5) |
| A crashed run starts over | **State manifest** (2.3) |

## 🛠️ S4 · Developer Productivity

**Setup:** exploring an unfamiliar codebase, connecting team systems.

| Stem → | Answer |
|---|---|
| "Where is X called?" | **Grep** (3.7) 🚨 |
| "All files named *.test.tsx" | **Glob** (3.7) 🚨 |
| Edit fails: the anchor isn't unique | **Longer anchor, or Read + Write** (3.7) 🚨 |
| The exploration loses exact facts after `/compact` | **Scratchpad file** (4.16) 🚨 |
| Verbose discovery floods the context | **Explore subagent** (4.11) |
| A team needs a shared Jira/GitHub server | **Community server** in committed **`.mcp.json`** with `${TOKEN}` (3.5) |
| A personal experimental server | **User scope** (3.5) |
| The agent keeps calling tools to list issues | Expose the catalog as a **resource** (3.6) |

## 🤖 S5 · Claude Code for CI

**Setup:** PR review and test generation in a pipeline.

| Stem → | Answer |
|---|---|
| Run in CI | **`-p`** (4.13) 🚨 |
| Machine-readable findings | **`--output-format json` + `--json-schema`** (4.13) 🚨 |
| Cap the cost and turns | **`--max-budget-usd`, `--max-turns`** flags (4.13) 🚨 |
| The reviewer must not modify code | **`--tools "Read,Grep,Glob"`** (4.13) 🚨 |
| No prompts allowed, but Edit must work | **`dontAsk` + `--allowedTools "Edit"`** (4.13) 🚨 |
| Duplicate PR comments on each push | **Pass prior findings**: only new or unaddressed (4.13) 🚨 |
| Accepted patterns keep getting flagged | **"Accepted here" list in project CLAUDE.md** (4.13) 🚨 |
| The author-session self-review misses bugs | **Independent instance** (4.13) |
| Generated tests duplicate existing ones | **Existing tests + standards in CLAUDE.md** (4.14) 🚨 |
| A pre-merge check, cheaper via batch? | **No: blocking → sync** (5.7) |

## 📄 S6 · Structured Extraction

**Setup:** invoices, receipts and forms → JSON.

| Stem → | Answer |
|---|---|
| Guaranteed JSON shape | **Tool schema** + `any` / forced (5.3) |
| The model invents a missing due date | **Nullable field** (5.4) 🚨 |
| Ambiguous payment terms | **`unclear`** + raw detail (5.4) 🚨 |
| Dates in five different formats | **Normalization rules** (5.5) 🚨 |
| Only receipts miss the total | **Few-shot per layout** (5.5) 🚨 |
| The output fails validation sometimes | **Retry with doc + output + exact error** (5.6) |
| Line items don't add up to the stated total | **`stated_total` + `calculated_total` + `conflict_detected`** (5.6) |
| 200k archived documents, weekly | **Batches**, `custom_id`, resubmit only failures (5.7) |
| JSON cut off on long documents | **Split + merge in code** (5.8) |
| 98% accuracy, cut human review? | **By type + field, calibrated, stratified audit** (6.6) |

---

# Part 8 · Guide vs docs, and myths that cost points ⚖️

## 8.1 Where today's product differs (answer per the guide)

| Topic | 🎯 Exam answer (guide) | Docs today |
|---|---|---|
| Subagent spawn tool | `Task`; `allowedTools` must include it | Renamed `Agent` in v2.1.63; `Task` still an alias |
| Team slash commands | `.claude/commands/` | Commands merged into skills; both create `/name` |
| Skill `allowed-tools` | **Restricts** tools during the skill | Pre-approves listed tools; `disallowed-tools` removes tools |
| Skill `argument-hint` | **Prompts** for missing parameters | An autocomplete hint |
| Verify loaded memory files | **`/memory`** | `/context` shows what loaded; `/memory` lists and opens files |
| Personal skill variant | **A different name**, so teammates aren't affected | The same name also works: personal beats project, for that user |
| Forced `tool_choice` | A valid way to guarantee a call or an order | `any` / forced return 400 on Opus 5.5, Sonnet 5.5, Fable 5.1, Mythos 5.1 |
| `context: fork` skill | An isolated subagent context | Also runs in the background by default; Explore/Plan forks skip CLAUDE.md |
| Grep / Glob | Standard built-ins | Not in the default set on macOS/Linux/WSL unless named in `--tools` / `--allowedTools` |
| CI flags | `-p`, `--output-format json`, `--json-schema` | Also real and tested: `--max-turns`, `--max-budget-usd`, `--permission-mode dontAsk`, `--tools`, `--disallowedTools`, `--bare` |
| Hook exit codes | Hooks give deterministic enforcement | Only **exit 2** blocks a PreToolUse call; exit 1 is non-blocking |
| Few-shot count | 2–4 targeted (2–3 I/O in TS 3.5) | Docs suggest 3–5 |

## 8.2 🚫 Invented mechanisms (they don't exist)

```
 ❌ CLAUDE_HEADLESS=1                    ✅ use -p
 ❌ --batch flag                         ✅ Message Batches is an API, not a Claude Code flag
 ❌ .claude/config.json                  ✅ .claude/settings.json
 ❌ "subagents inherit the history"      ✅ they see only their prompt
 ❌ "turn limit in the prompt text"      ✅ --max-turns
```

## 8.3 💣 Myths that cost points

| Myth | Truth | See |
|---|---|---|
| "Exit 1 blocks the tool" | Only **exit 2** blocks | 4.10 |
| "A local allow can override the team deny" | **Deny always wins** | 4.9 |
| "A hook returning allow bypasses a deny rule" | It **doesn't** | 4.10 |
| "Writing NEVER in CLAUDE.md enforces it" | It's a request. Use deny or a hook. | 1.1 |
| "`src/api/*.ts` covers subfolders" | No. You need `**`. | 4.5 |
| "A forked skill knows what we discussed" | It sees only skill text + arguments | 4.7 |
| "`--allowedTools` restricts tools" | It **pre-approves**. `--tools` restricts. | 4.13 |
| "Subagents see the coordinator's conversation" | Only their prompt | 2.4 |
| "Resume and re-analyze everything" | **Name** the changed files | 2.8 |
| "A fork keeps the same session ID" | A fork gets a **new** ID | 2.8 |
| "A composite tool fixes slow independent lookups" | One turn, several `tool_use` blocks | 2.2 |
| "Prompt 'always call X first' guarantees order" | Force X on turn 1, then `auto` | 3.4 |
| "Force the tool on every turn to be safe" | The loop never ends | 3.4 |
| "An empty search result is an error" | It's a success with zero matches | 3.2 |
| "Retry until the model finds the due date" | Absent → nullable | 5.4 |
| "Be conservative fixes false positives" | Explicit criteria + accepted patterns | 5.1 |
| "A bigger context window fixes missed cross-file bugs" | Per-file passes + integration pass | 5.9 |
| "Batch the pre-merge check, it's cheaper" | Blocking → sync | 5.7 |
| "Escalate when the customer sounds angry" | Explicit request, policy gap, no progress | 6.2 |
| "98% overall means we can drop human review" | Check by type and field first | 6.6 |
| "Fix the synthesizer when coverage is narrow" | Fix the coordinator's decomposition | 2.5 |

---

# Part 9 · Self-test: 48 questions 🧪

> **How to use:** answer each question **before** opening ▶. Questions marked 🚨 hit your weak spots. If you miss one, log it (Appendix C) and re-read the section listed in the answer.
>
> All questions are original, built from the lab's scenarios.

## 9.1 D3 · Claude Code (Q1–Q21)

**Q1 · 🚨 O16** Your team wants Claude Code to use named exports in all code. A new hire says Claude ignores this. The line is in the tech lead's `~/.claude/CLAUDE.md`. What's the best fix?
- A) Ask the new hire to add the line to their own `~/.claude/CLAUDE.md`
- B) Add a PreToolUse hook that rejects files with default exports
- C) Move the line to the project `CLAUDE.md` and commit it
- D) Turn it into a `/named-exports` skill

<details><summary>▶ Answer</summary>

**C.** It's in user scope, so only the tech lead gets it. A team convention belongs in the committed project file.
⚠️ A works for one person and doesn't scale. B is heavy machinery for a style convention. D needs someone to invoke it. → **4.3**

</details>

**Q2 · 🚨 O16** Test files (`*.test.ts`) are spread across 30 folders. Their conventions should load only when Claude works on tests. Where do they go?
- A) `.claude/rules/tests.md` with `paths: ["**/*.test.ts"]`
- B) A `CLAUDE.md` in each of the 30 folders
- C) A section in the root `CLAUDE.md`
- D) A `/test-conventions` skill

<details><summary>▶ Answer</summary>

**A.** One rule file, loaded only when a matching file is touched, and `**` crosses folders.
⚠️ B is 30 copies to maintain. C always loads, everywhere. D waits to be invoked. → **4.5**

</details>

**Q3 · 🚨 O16** `.claude/rules/api.md` has `paths: ["src/api/*.ts"]`. Claude edits `src/api/v2/orders.ts` and ignores the API rule. Most likely cause?
- A) Rules only load at session start
- B) Rule files must be named `CLAUDE.md`
- C) Claude needs `/memory` to reload the rules
- D) `*` doesn't cross folders; the glob should be `src/api/**/*.ts`

<details><summary>▶ Answer</summary>

**D.** `*` matches one folder level. You fixed exactly this in E3. → **4.5**

</details>

**Q4 · 🚨 O16** Policy: Claude must never read `secrets/prod.env`, with no exceptions. Best mechanism?
- A) A CLAUDE.md line: "Never read secrets/prod.env"
- B) A deny rule `Read(./secrets/prod.env)` in the committed `.claude/settings.json`
- C) A PostToolUse hook that hides the output after it's read
- D) An allow list that leaves the file out

<details><summary>▶ Answer</summary>

**B.** "Must never" for a known path → deny. Nothing overrides it.
⚠️ A is words. C acts after the read. D just means a prompt, not a refusal. → **4.9**

</details>

**Q5 · 🚨 O16** You want to block any Bash command that contains `rm -rf` anywhere, including chained commands, and tell Claude why. What do you set up?
- A) A PreToolUse hook on Bash that exits **2** with the reason on stderr
- B) A PreToolUse hook on Bash that exits **1** with the reason on stderr
- C) A PostToolUse hook on Bash that exits 2
- D) A CLAUDE.md line: "never run rm -rf"

<details><summary>▶ Answer</summary>

**A.** It's a dynamic content check, done before the action. Only exit 2 blocks, and stderr goes to Claude.
⚠️ B: exit 1 is non-blocking, so the command runs. C: too late. D: words. → **4.10**

</details>

**Q6 · 🚨 E7** The team's `.claude/settings.json` denies `Read(./.env)`. A developer adds `allow: Read(./.env)` to their `.claude/settings.local.json`. What happens when Claude tries to read `.env`?
- A) The local allow wins and Claude reads it silently
- B) Claude prompts the developer
- C) Still refused: a deny in any file beats an allow
- D) Whichever file loaded last wins

<details><summary>▶ Answer</summary>

**C.** Deny > ask > allow, across all settings files. → **4.9**

</details>

**Q7 · 🚨 O14** A `/map-module` skill prints every file in full and floods the main conversation. How do you keep the main context clean?
- A) Tell users to run `/compact` after the skill
- B) Shorten the skill's description
- C) Move the instructions into CLAUDE.md
- D) Add `context: fork` to the skill's frontmatter

<details><summary>▶ Answer</summary>

**D.** The fork does the verbose work in its own context and returns a short result.
⚠️ A cleans up after the damage. C would load it always. → **4.7**

</details>

**Q8 · 🚨 O14** After adding `context: fork`, running `/map-module` with no argument maps the wrong module, even though the user named the module earlier in the chat. Why?
- A) Forking is buggy; remove `context: fork`
- B) A forked skill sees only the skill text and its arguments, so the skill must be self-contained
- C) It needs `agent: Plan`
- D) `argument-hint` is missing

<details><summary>▶ Answer</summary>

**B.** The fork has no access to the conversation. Require the path, or state everything in the skill.
⚠️ A "works" but throws away the benefit. → **4.7**

</details>

**Q9 · O16 / E4** You want a personal tweak of the team's `/team-review` without affecting teammates. What's the guide's answer?
- A) A personal skill in `~/.claude/skills/` with a **different** name
- B) Edit `.claude/commands/team-review.md` directly
- C) A personal skill in `~/.claude/skills/` with the **same** name
- D) Put the tweak in `.claude/settings.local.json`

<details><summary>▶ Answer</summary>

**A.** Personal scope, different name, so it doesn't shadow the team's version.
⚖️ C works today (personal beats project, for you), but the guide says use a different name. B changes it for everyone. → **4.6**

</details>

**Q10 · 🚨 O8** "`orderTotal` returns NaN when qty is undefined; default qty to 1." Which mode?
- A) Plan mode, then approve
- B) An Explore subagent first
- C) Direct execution
- D) Fork the session first

<details><summary>▶ Answer</summary>

**C.** One-sentence diff, clear cause. → **4.11**

</details>

**Q11 · 🚨 O8** Migrate all 25 API modules from `fetch` to a shared HTTP client with retries and typed errors. The tech lead wants to approve the approach first. Which mode?
- A) Direct execution, then review the diff
- B) Tell Claude to be careful and go file by file
- C) `/compact`, then direct execution
- D) Plan mode: explore, propose, get sign-off, then execute

<details><summary>▶ Answer</summary>

**D.** Multi-file, architectural, and needs sign-off. → **4.11**

</details>

**Q12 · 🚨 O12** Claude keeps interpreting your prose spec ("DD/MM/YY to ISO, A/S to active/suspended") differently on each attempt. Most effective next step?
- A) Give 2–3 concrete input → output examples
- B) Rewrite the prose spec in more detail
- C) Switch to plan mode
- D) Ask for three versions and pick the best

<details><summary>▶ Answer</summary>

**A.** Prose read inconsistently → concrete examples.
⚠️ B is more of the thing that already failed. → **4.12**

</details>

**Q13 · 🚨 O12** Two bugs: date parsing gets the year wrong, and missing-key handling crashes. Fixing the parser changes which keys end up missing. How do you ask for the fixes?
- A) One bug per turn, so each fix is small
- B) A new session per bug
- C) One detailed message describing both bugs and how they interact
- D) Fork the session and fix one bug in each fork

<details><summary>▶ Answer</summary>

**C.** Interacting bugs → one message. Independent bugs → one at a time. → **4.12**

</details>

**Q14 · 🚨 O12** You need a cache for `getUser`, but you're unsure about invalidation rules and failure modes. Best first move?
- A) "Add a cache to getUser" and iterate on what comes back
- B) Ask Claude to interview you about invalidation and failure modes before writing any code
- C) Write the cache yourself and ask Claude to review it
- D) Ask Claude to generate tests for a cache first

<details><summary>▶ Answer</summary>

**B.** Unfamiliar domain, unclear requirements → interview pattern first. You can't write good tests (D) before you know the requirements. → **4.12**

</details>

**Q15 · 🚨 O11** A CI review job must stop after at most 8 agent turns and $1 of spend. How?
- A) Put "stop after 8 turns and spend at most $1" in the prompt
- B) Set `CLAUDE_HEADLESS=1` and put the limits in `.claude/config.json`
- C) Use `--batch` mode
- D) `--max-turns 8 --max-budget-usd 1.00`

<details><summary>▶ Answer</summary>

**D.** Caps come from flags, not prompt text.
⚠️ B and C are invented mechanisms. → **4.13**

</details>

**Q16 · 🚨 O11** A CI job runs with `--permission-mode dontAsk`. Claude must be able to edit files without prompting, and anything else that would prompt stays denied. Which flag do you add?
- A) `--tools "Edit"`
- B) `--allowedTools "Edit"`
- C) `--disallowedTools "Bash"`
- D) Drop `dontAsk` and let it prompt

<details><summary>▶ Answer</summary>

**B.** `--allowedTools` pre-approves Edit. `dontAsk` denies everything else that would prompt (flags_demo step 6).
⚠️ A restricts which tools exist (and would remove Read); it doesn't pre-approve. D: nobody can answer prompts in CI. → **4.13**

</details>

**Q17 · 🚨 O11 / O13** A CI reviewer must not be able to modify code at all. Most reliable?
- A) Prompt: "Do not modify any files"
- B) `--allowedTools "Read"`
- C) `--tools "Read,Grep,Glob"`
- D) `--max-turns 1`

<details><summary>▶ Answer</summary>

**C.** Only those tools exist, so Edit and Write are impossible.
⚠️ A is words. B pre-approves Read but doesn't remove Edit. → **4.13**

</details>

**Q18 · 🚨 O13** A CI review posts PR comments. On every push, it re-posts comments about issues it already reported. Fix?
- A) Feed the previous findings into the re-run, and ask only for new or still-unaddressed issues
- B) Lower the temperature
- C) Run with `--bare`
- D) Switch to the Batches API

<details><summary>▶ Answer</summary>

**A.** That's `bash ci/review.sh ci/out/findings.json`. → **4.13**

</details>

**Q19 · 🚨 O13 / O30** The reviewer keeps flagging `fetch(...).then(r => r.json())` in demo components, which the team accepts. Durable fix for every run?
- A) Add "be conservative" to the CI prompt
- B) Ask developers to ignore those comments
- C) Lower `--max-turns`
- D) Add it to an "Accepted here, do not flag" list in the Review standards in project CLAUDE.md

<details><summary>▶ Answer</summary>

**D.** A persistent convention in project CLAUDE.md, which every run loads.
⚠️ A doesn't fix precision. → **4.13**, **5.1**

</details>

**Q20 · 🚨 O13** The same session that wrote a change also reviews it, and misses issues. Better approach?
- A) Ask the same session to "review harder"
- B) Review with an independent, fresh instance that didn't write the code
- C) Use a model with a bigger context window
- D) Run the self-review 3 times and keep the consensus

<details><summary>▶ Answer</summary>

**B.** The author session keeps its own reasoning and blind spots.
⚠️ C and D are classic distractors. → **4.13**

</details>

**Q21 · 🚨 O15** Generated tests keep repeating scenarios already in `test_cart.py`. Fix?
- A) Ask for "novel tests"
- B) Ask for more tests, so some are new
- C) Include the existing test file ("don't duplicate these") and keep the testing standards in project CLAUDE.md
- D) Raise `max_tokens`

<details><summary>▶ Answer</summary>

**C.** Show what exists, and make the standards persistent. → **4.14**

</details>

## 9.2 D1 · Agentic (Q22–Q30)

**Q22 · 🚨 O2** Yesterday a session reviewed the orders module. Today only `orders.ts` changed (`orderTotal` takes a discount). Most efficient way to continue?
- A) A fresh session that re-reviews the whole module
- B) Fork yesterday's session
- C) Resume and say "files changed, re-analyze everything"
- D) Resume and name the changed file: "Only orders.ts changed: orderTotal now takes a discount. Re-check R1–R3."

<details><summary>▶ Answer</summary>

**D.** Context mostly valid → resume and name the changes.
⚠️ C re-reads everything. → **2.8**

</details>

**Q23 · 🚨 O2** You want to compare two refactoring approaches, both starting from the same analysis. How?
- A) Resume the same session twice
- B) Fork the session (each fork gets a new session ID)
- C) `/clear` between the two attempts
- D) Copy the transcript into two new sessions by hand

<details><summary>▶ Answer</summary>

**B.** Two approaches from one baseline → fork. → **2.8**

</details>

**Q24 · 🚨 O2** A large refactor merged overnight. Most of yesterday's file reads are now outdated. How do you continue?
- A) Resume and continue
- B) Fork and continue
- C) Start fresh, with a structured summary of the conclusions that still hold
- D) `/compact` and continue

<details><summary>▶ Answer</summary>

**C.** Stale tool results → fresh session + summary. Resuming would make Claude trust outdated reads. → **2.8**

</details>

**Q25 · 🚨 O1** A support agent needs a customer's profile, order history and open tickets. The three lookups are independent, but they take three round trips. Best fix?
- A) Let the model emit all three `tool_use` blocks in one turn, and return all three results in one user message
- B) Build a composite `get_everything` tool
- C) Pre-execute every tool speculatively at the start of each turn
- D) Spawn one subagent per lookup

<details><summary>▶ Answer</summary>

**A.** Independent → one turn.
⚠️ B, C and D are heavy machinery. → **2.2**

</details>

**Q26 · 🚨 O1** The model returned three `tool_use` blocks in one turn. How do you send the results?
- A) Three user messages, one result each
- B) Only the first result, then ask the model to repeat the others
- C) Merge the three results into one text block
- D) One user message with three `tool_result` blocks, each with its matching `tool_use_id`

<details><summary>▶ Answer</summary>

**D.** All results in one message, matched by ID. → **2.2**

</details>

**Q27 · 🚨 O3** A coordinator delegates: "Write the section on refund limits." The subagent returns "not provided". Root cause?
- A) The subagent's model is too small
- B) The subagent sees only its prompt; the findings and their sources must be in the prompt
- C) The subagent needs the Write tool
- D) `max_tokens` is too low

<details><summary>▶ Answer</summary>

**B.** It never saw the coordinator's findings. That's E16. → **2.4**

</details>

**Q28 · 🚨 O4** A research system on "AI in creative industries" misses music and film. The coordinator's prompt to the searchers is "1. search visual art 2. search graphic design". Fix?
- A) Improve the synthesizer's prompt
- B) Add more search tools
- C) Rewrite the coordinator's delegation as a goal with coverage criteria, not a fixed list
- D) Use a bigger model for synthesis

<details><summary>▶ Answer</summary>

**C.** Fix the first broken layer: the narrow decomposition.
⚠️ A is the wrong layer. → **2.5**

</details>

**Q29 · 🚨 O33** The synthesizer subagent keeps searching instead of synthesizing. It has the full search tool. Fix?
- A) Remove the search tool, and give it a scoped `verify_fact` tool for the checks it needs often
- B) Prompt: "Don't search, just synthesize"
- C) Give it every tool, so it can choose
- D) Add a router in front of it

<details><summary>▶ Answer</summary>

**A.** Role tools plus one scoped cross-role tool, enforced in config.
⚠️ B is words. → **3.3**

</details>

**Q30 · TS 1.4** A refund must **never** be issued before identity is verified. Most reliable?
- A) A bold rule in the system prompt
- B) A code gate in the refund tool that refuses without a verified customer ID and returns a structured error
- C) Few-shot examples of correct ordering
- D) The refund tool's description says "verify first"

<details><summary>▶ Answer</summary>

**B.** Money + "never" → code. A, C and D lower the rate but never to zero. → **2.6**

</details>

## 9.3 D2 · Tools & MCP (Q31–Q37)

**Q31 · 🚨 O37** A pipeline must run `extract_metadata` before anything else, then let the model continue freely. How?
- A) Prompt: "Always call extract_metadata first"
- B) `tool_choice: {"type": "any"}`
- C) Force `extract_metadata` on every turn
- D) Force `extract_metadata` on the first turn, then switch to `auto`

<details><summary>▶ Answer</summary>

**D.** Forced-then-auto.
⚠️ A is guidance. B lets it pick any tool. C traps the loop. → **3.4**

</details>

**Q32 · 🚨 O37** The document type is unknown, and there are three extraction schemas (one tool each). You must always get structured output from one of them. Which `tool_choice`?
- A) `{"type": "auto"}`
- B) `{"type": "any"}`
- C) Force the invoice schema
- D) Prompt: "Always reply with JSON"

<details><summary>▶ Answer</summary>

**B.** It must call some tool, and the model picks the right schema.
⚠️ A may answer in text. C picks the wrong schema for non-invoices. → **3.4**

</details>

**Q33 · 🚨 O17 / O32** "Find every `*.test.tsx` file" and "find where `getOrder` is called". Which tools?
- A) Grep for both
- B) Read every file and look
- C) Glob for the file names, Grep for the content
- D) Bash `find` and `grep`

<details><summary>▶ Answer</summary>

**C.** Names → Glob. Content → Grep. → **3.7**

</details>

**Q34 · 🚨 O32** An Edit fails because `retries = 3` appears twice in the file. Only the second one should change. What should Claude do?
- A) Use a longer, unique anchor, or Read the file and Write it back (the guide's fallback)
- B) Retry the same Edit
- C) Run `sed` through Bash
- D) Ask the user to edit it

<details><summary>▶ Answer</summary>

**A.** → **3.7**

</details>

**Q35 · TS 2.2** An order lookup returns zero matches for the number the customer gave. What should the tool return?
- A) `isError: true`, transient, retryable
- B) `isError: true`, business
- C) A normal success with zero results, so the agent says "no order found with that number"
- D) `"Operation failed"`

<details><summary>▶ Answer</summary>

**C.** An empty result is not an error. → **3.2**

</details>

**Q36 · TS 2.1** The agent picks `get_customer` for order questions. Both tools have one-line descriptions. First step?
- A) Add a routing classifier
- B) Rewrite both descriptions: purpose, input format with an example, and when to use the other tool
- C) Merge both tools into one
- D) Add 20 few-shot routing examples

<details><summary>▶ Answer</summary>

**B.** Lowest effort, at the root cause. → **3.1**

</details>

**Q37 · O35** The team needs a shared MCP server that uses an API token. Best setup?
- A) Each developer runs `claude mcp add --scope user`
- B) Commit `.mcp.json` with the token pasted in
- C) Commit `.mcp.json` using `${ORDERS_API_TOKEN}`; each developer sets the env var
- D) Put the server details in CLAUDE.md

<details><summary>▶ Answer</summary>

**C.** Team → project scope, committed. Secrets come from env vars. → **3.5**

</details>

## 9.4 D4 · Prompting & output (Q38–Q44)

**Q38 · 🚨 O26** Some invoices have no due date. How should the schema handle `due_date`?
- A) A required string, with the prompt "write N/A if missing"
- B) Retry until the model finds it
- C) Nullable / optional `due_date`
- D) A closed enum of common due dates

<details><summary>▶ Answer</summary>

**C.** Absent → nullable. → **5.4**

</details>

**Q39 · 🚨 O26** The list of payment-term categories can never be complete, and some documents are ambiguous. Schema design?
- A) A closed enum of the 5 known terms
- B) Free text only
- C) Required, with a default of `net_30`
- D) An enum + `"unclear"` + `"other"`, with a `terms_detail` string

<details><summary>▶ Answer</summary>

**D.** Ambiguous → `unclear`. Open-ended → `other` + detail. → **5.4**

</details>

**Q40 · 🚨 O29** Dates arrive as "3rd Feb 2024", "02/03/24" and "2024.02.03", and the extracted dates are inconsistent. Fix?
- A) One few-shot example per layout
- B) Normalization rules next to the schema (output ISO 8601; read "02/03/24" as DD/MM/YY)
- C) Retry with the error
- D) A bigger model

<details><summary>▶ Answer</summary>

**B.** Messy formats → normalization rules. → **5.5**

</details>

**Q41 · 🚨 O29** Extraction works on typed invoices, but `total` comes back empty for scanned receipts, even though the total is clearly printed at the bottom. Fix?
- A) Add a few-shot example for the receipt layout
- B) Add normalization rules
- C) Make `total` nullable
- D) Retry each receipt until `total` is filled

<details><summary>▶ Answer</summary>

**A.** The data is present, but the layout is different → one example per layout.
⚠️ C would hide data that **is** there. → **5.5**

</details>

**Q42 · O23** Which job belongs on Message Batches?
- A) A pre-merge PR check that blocks the merge
- B) A live customer chat
- C) A weekly re-scan of 200,000 archived contracts
- D) A check a developer waits for in their IDE

<details><summary>▶ Answer</summary>

**C.** Not urgent, high volume, cost matters. A, B and D are blocking → sync. → **5.7**

</details>

**Q43 · O24** A single review pass over 30 files misses a bug in the data flow between two files. Fix?
- A) A model with a bigger context window
- B) A consensus of 3 runs
- C) Per-file passes, plus an integration pass for cross-file data flow
- D) Add "be thorough" to the prompt

<details><summary>▶ Answer</summary>

**C.** → **5.9**

</details>

**Q44 · O28** Long contracts return truncated JSON with `stop_reason: "max_tokens"`. Most robust fix?
- A) Only raise `max_tokens`
- B) Split into scoped calls (per section) and merge in code
- C) Retry the same call
- D) Ask the model to be brief

<details><summary>▶ Answer</summary>

**B.** → **5.8**

</details>

## 9.5 D5 · Context & reliability (Q45–Q48)

**Q45 · TS 5.2** The customer writes "Just get me a human." The agent is one step away from solving the issue. What should it do?
- A) Escalate now
- B) Finish solving first, then offer a human
- C) Ask why they want a human
- D) Escalate only if their sentiment gets worse

<details><summary>▶ Answer</summary>

**A.** An explicit request → escalate immediately. → **6.2**

</details>

**Q46 · 🚨 O20** During a long exploration, Claude lost the exact line numbers after `/compact`. How do you prevent that?
- A) Never use `/compact`
- B) Keep a scratchpad file of confirmed facts with file:line, and re-read it after `/compact` or `/clear`
- C) Use a model with a bigger context window
- D) Fork before compacting

<details><summary>▶ Answer</summary>

**B.** → **4.16**, **6.4**

</details>

**Q47 · O19** Two credible sources disagree: 40% (2025 survey) vs 12% (2023 report). What does the synthesis do?
- A) Shows both side by side, with sources and dates
- B) Picks the newer one
- C) Averages them
- D) Drops the claim

<details><summary>▶ Answer</summary>

**A.** The dates may explain the difference. Never pick one silently. → **6.5**

</details>

**Q48 · O22** Extraction is 97% accurate overall. The team wants to cut human review. What first?
- A) Cut human review everywhere; 97% is high
- B) Route by the model's self-reported confidence ≥ 0.9
- C) Review a random 1% of everything
- D) Measure accuracy by document type and field, calibrate thresholds on labeled data, and keep a stratified sample of high-confidence output

<details><summary>▶ Answer</summary>

**D.** A high aggregate can hide a failing document type. → **6.6**

</details>

## 9.6 Score yourself

| 🚨 questions right (of 37) | What to do |
|---|---|
| 33–37 | 🟢 Ready. Run timed drills only. |
| 26–32 | 🟡 Re-read the sections of the ones you missed, then run those lab exercises. |
| under 26 | 🔴 Do Part 4 hands-on (E4–E14) before your next attempt. |

---

# Part 10 · Night-before cram sheet 🌙

> One screen. Read it twice. Sleep.

**Guarantees**
- Must, never, money, identity → **code**: gate, hook, deny rule, schema, forced `tool_choice`, flags. Prompts only lower the rate.

**Claude Code config (O16)** 🚨
- Team → project `CLAUDE.md`, `.claude/`, `.mcp.json` (committed). Me → `~/.claude/`.
- Folder CLAUDE.md loads when Claude works there. `@import` loads with its parent.
- File type across folders → `.claude/rules` + `paths` + `**`. `*` stays in one folder.
- Team command → `.claude/commands/`. Personal variant → **different name**.
- Same name: personal skill > project skill > command.
- **Deny > ask > allow.** A local allow never beats a deny. A hook allow never beats a deny.
- **PreToolUse exit 2** blocks. Exit 1 doesn't. PostToolUse is after the fact.
- Verify loaded memory → `/memory` (guide).

**Skills (O14)** 🚨
- Verbose → `context: fork`. The fork sees only skill text + `$ARGUMENTS` → self-contained.
- Guide: `allowed-tools` restricts, `argument-hint` prompts for missing parameters.

**Workflows (O8, O12)** 🚨
- One-sentence diff → direct. Multi-file, architectural, options, sign-off → **plan → approve → execute**.
- Verbose discovery → Explore subagent.
- Inconsistent → 2–3 I/O examples. Tests first. Specific failures. Interacting → one message. Independent → one at a time. Unfamiliar → interview.

**CI (O11, O13, O15)** 🚨
- `-p` + `--output-format json` + `--json-schema` → `structured_output`.
- Caps: `--max-turns`, `--max-budget-usd` (flags, not prompt text).
- `dontAsk` denies prompts. `--allowedTools` **pre-approves**. `--tools` / `--disallowedTools` **restrict**.
- Standards in project CLAUDE.md. Prior findings on re-runs. Independent reviewer.
- Tests: give the existing tests + standards in CLAUDE.md.
- Doesn't exist: `CLAUDE_HEADLESS`, `--batch`, `.claude/config.json`.

**Agents (O1, O2, O3, O4)** 🚨
- Loop on `tool_use`, stop on `end_turn`.
- Independent → one turn, N `tool_use` → all results in **one** user message.
- Subagent sees only its prompt → complete findings + sources. Spawning needs `Task` in `allowedTools`.
- Delegate goals + quality criteria, not step lists. Fix the first broken layer.
- Mostly valid → resume + name the files. Stale → fresh + summary. Two paths → fork (new ID).

**Tools (O17, O32, O33, O37)** 🚨
- Grep = content. Glob = names. Read the hits. Non-unique Edit → longer anchor, or Read + Write.
- 4–5 tools per role + a scoped cross-role tool. Constrain generic tools in code.
- `auto` may answer in text · `any` = some tool · forced = this tool · force once, then `auto`.
- Misrouting → fix the descriptions first.
- Errors: transient → retry. Validation, business, permission → don't. Empty = success.
- MCP: team `.mcp.json` + `${TOKEN}` · personal = user scope · catalogs = resources.

**Extraction (O26, O29)** 🚨
- Absent → nullable · ambiguous → `unclear` · open-ended → `other` + detail.
- Formats → normalization rules · layouts → one few-shot per layout.
- Retry = doc + failed output + exact error. It can't create missing data. Contradiction → both values + conflict flag.
- Schema = shape, not truth. Precision → explicit criteria, not "be conservative".
- Blocking → sync. Overnight → batch (`custom_id`, resubmit only failures).

**Context (O20)** 🚨
- Case facts outside the summary. Scratchpad for exact facts. Subagents for verbose work. Manifest for crashes.
- Escalate: explicit request (now), policy gap, no progress. Not sentiment, not self-confidence.
- Synthesis keeps claim-source-date; conflicts side by side. Routing: by type + field, calibrated, stratified audit.

---

# Appendix A · Where to practise each weak objective 🔧

| Obj | Score | Practise | Command / place |
|---|---|---|---|
| O16 | 🟥 0% | D3 E1–E8 | `d3-claude-code/sandbox` (E1–E3 ✅) |
| O14 | 🟥 0% | D3 E5 | `/map-module` with and without `context: fork` |
| O8 | 🟥 0% | D3 E9 | `claude --permission-mode plan` |
| O12 | 🟥 0% | D3 E10 | `py/status.py` + `test_status.py` |
| O13 | 🟥 0% | D3 E11 | `bash ci/review.sh` ⚠️ fix `python3` first |
| O15 | 🟥 0% | D3 E12 | `bash ci/testgen.sh` |
| O1 | 🟥 0% | D1 | `python d1-agentic/02_parallel_tool_calls.py` |
| O2 | 🟥 0% | D1 + D3 E13 | `python d1-agentic/06_sessions_resume_fork.py` |
| O37 | 🟥 0% | D2 | `python d2-tools-mcp/03_tool_choice.py` |
| O29 | 🟥 0% | D4 | `python d4-prompting/03_normalization_fewshot.py`, then `04` |
| O3 | 🟧 33% | D1 ex 6 + D3 E16 | `d1-agentic/05_coordinator_subagents.py` |
| O26 | 🟧 33% | D4 | `python d4-prompting/02_schema_nullable_enums.py` |
| O17 | 🟧 40% | D3 E14 | `claude --tools "Read,Edit,Write,Grep,Glob,Bash"` |
| O4 | 🟧 50% | D1 ex 4 | `d1-agentic/05_coordinator_subagents.py` |
| O11 | 🟧 50% | D3 E11 | `bash ci/flags_demo.sh 1` … `9` ⚠️ fix `python3` first |
| O20 | 🟧 50% | D3 E14, E16 | scratchpad + `/compact` |
| O30 | 🟧 50% | D4 + D3 E11 | `python d4-prompting/01_explicit_criteria_fewshot.py` |
| O32 | 🟧 50% | D3 E14 | the non-unique Edit in `py/retry_config.py` |
| O33 | 🟧 50% | D2 + D1 ex 7 | `python d2-tools-mcp/04_tool_distribution.py` |

Python labs: run from the repo root with the venv active (`source .venv/Scripts/activate` in Git Bash). D3 exercises: run `claude` inside `d3-claude-code/sandbox/`.

---

# Appendix B · Glossary in plain words 📖

| Term | Plain meaning |
|---|---|
| **Agent loop** | Send → Claude asks for tools → you run them → send results → repeat until `end_turn` |
| **`stop_reason`** | Why Claude stopped: `tool_use` (wants tools), `end_turn` (done), `max_tokens` (cut off) |
| **`tool_use` / `tool_result`** | Claude's request to run a tool / your answer, matched by `tool_use_id` |
| **`tool_choice`** | Whether Claude may, must, or must use one specific tool |
| **Coordinator / subagent** | The boss agent that delegates / a helper with its own prompt and tools |
| **Hub-and-spoke** | All communication goes through the coordinator |
| **Prerequisite gate** | Code inside a tool that refuses to act until a condition is met |
| **Hook** | Your script that runs before (PreToolUse) or after (PostToolUse) a tool call |
| **CLAUDE.md** | Instructions Claude Code loads automatically |
| **Rule (`.claude/rules`)** | An instruction file that loads only for matching file paths |
| **Skill** | A reusable instruction pack, run with `/name` or picked up by Claude when relevant |
| **`context: fork`** | Run a skill in its own isolated context |
| **Explore subagent** | A built-in read-only helper for searching code |
| **Plan mode** | Claude explores and proposes, but makes no edits until you approve |
| **Permission rule** | deny / ask / allow for a tool + path or command pattern |
| **Headless (`-p`)** | Run Claude Code without the interactive UI, e.g. in CI |
| **Session resume / fork** | Continue the same session / branch a copy with a new ID |
| **MCP** | A standard way to plug external tools and data into Claude |
| **MCP resource** | Read-only data a server exposes (catalogs, schemas) |
| **`.mcp.json`** | The project's committed list of MCP servers |
| **Schema** | The required shape of a JSON output |
| **Nullable** | A field that's allowed to be `null` (empty) |
| **Few-shot** | Example input → output pairs in the prompt |
| **Normalization rules** | Instructions for turning messy formats into one standard format |
| **Message Batches** | Async API: up to 24 h, 50% cheaper, results matched by `custom_id` |
| **Case-facts block** | Key numbers and dates kept outside the summary, in every prompt |
| **Scratchpad file** | A notes file where Claude writes confirmed facts during long work |
| **Manifest** | A state file that lets a crashed run resume |
| **Provenance** | Where each claim came from: source, date, method |
| **Stratified sampling** | Checking a random sample from **each** group, not just overall |

---

# Appendix C · Miss log template 📝

Every time you miss a self-test question or a lab prediction, add one line. Re-read this list the day before the exam.

```
Q/Ex | I predicted        | Truth              | The rule                                  | Obj
-----|--------------------|--------------------|-------------------------------------------|-----
E1   | only user file     | both work for me   | difference = who else gets it (team)      | O16
     |                    |                    |                                           |
     |                    |                    |                                           |
```

You can also tell Claude in the repo root: *"log a miss: ..."* and it writes to `notes/miss-log.md`.

---

> 🏁 **You've got this.** Your design instincts are already at 100% in most of D1, D5 and MCP. The gap is concrete knobs: files, flags, exit codes and modes. Those are the easiest points to win back, because every one has a single right answer.
