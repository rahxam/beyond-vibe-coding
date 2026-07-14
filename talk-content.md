# Beyond Vibe Coding: Engineering Deterministic CAP Applications with SDD

**SAP CodeConnect 2026 Recap — 16:00–16:20, Audimax**
**Format:** ~7 min talk (Part 1, this document) + live demo (Part 2, co-speaker) + buffer
**Audience:** Experienced CAP developers. AI is the hype topic — they've heard the buzzwords, many are skeptical. Lean into the skepticism, then flip it.
**Tone:** Funny but substantive. The jokes are the hook; the CAP specifics are the payoff.
**Tooling note:** Kept tool-agnostic. The workflow (constitution → specify → plan → tasks → implement) is described as *the* SDD workflow; GitHub Spec Kit is mentioned once as "the tool we'll use in the demo" — if the co-speaker switches tools, only that one sentence changes.

---

## THE DESIGN SYSTEM (applies to all slides from Slide 2 on)

The presentation is an HTML page styled as a **VS Code window**:

- **Left — Explorer sidebar:** a project tree (`BOOKSHOP-TALK`) that *grows during the talk*. Files appear in the tree exactly when they're introduced on stage. By the demo handoff, the tree looks like a real SDD project. This is the visual backbone of the whole talk.
- **Top — Editor tabs:** each slide is an "open file". The active tab names the slide (e.g. `vibe-coding.md`). Previously visited tabs stay open — the tab row doubles as a progress indicator.
- **Center — Editor:** the actual slide content, rendered like a Markdown preview (or raw md with syntax highlighting where that's funnier).
- **Bottom — Panel:** switches between **PROBLEMS**, **TERMINAL** and **OUTPUT** per slide. This is the running-gag surface: Problems shows AI hallucinations as warnings, Terminal shows fake prompt runs.
- **Status bar (bottom edge):** persistent micro-gags, changes per slide (branch name, "Ln 42, Col 0", language mode).

**Animation notation:** every slide lists **Builds** as `[B1]`, `[B2]`… = one click/keypress each. Anything not in a build is visible when the slide opens. Suggested build mechanics: new bullet lines "type themselves" (typewriter effect, fast), files pop into the explorer with the VS Code "new file" flash, panel entries scroll in like real log output.

**Asset list (AI-generate):** collected in the appendix.

---

## PART 1 — THE TALK (~7 min)

---

### Slide 1 — Title (0:30)

**Design:** NOT VS Code yet. A normal, clean conference title slide — deliberately conventional (this makes the Slide-2 reveal land).

**On the slide:**

> **Beyond Vibe Coding**
> Engineering Deterministic CAP Applications with Spec-Driven Development
>
> Abdulbasıt Gülşen  Maximilian Hartig — CodeConnect 2026

**Builds:** none. Static slide.

**What you say:**

> "Hi everyone. Quick show of hands: who here has asked an AI to write CAP code this year? *(pause)* Keep your hand up if you used spec driven development. *(watch the hands drop)* That drop-off you just saw — that's this talk.
>
> Here's the plan for the next 20 minutes: a bit of theory from me — what spec-driven development actually is and why it matters for CAP — and then Abdulbasıt builds a real CAP bookshop application live on stage. Which will either be very impressive or very entertaining. Win-win for you either way."

---

### Slide 2 — The Reveal + Emergency Entertainment (0:45)

**Design:** starts as the title slide, then transforms.

**On the slide (after transformation):** the full VS Code window appears. Explorer shows a nearly empty project:

```
BOOKSHOP-TALK
├── .theory/
│   └── (empty)
└── README.md
```

Active tab: `README.md`, content:

> `# no slides were harmed in the making of this talk`

Bottom panel: **TERMINAL**, showing a fake prompt: `$ specify talk --audience "cap-devs" --slides false`

**Builds:**

- **[B1]** The title slide "breaks": the plain slide shrinks into an editor tab, the VS Code chrome (sidebar, panel, status bar) slides in around it. One smooth transformation animation — this is the moment, invest in it.
- **[B2]** The Subway-Surfer video fades in as a **picture-in-picture player in the bottom-right corner** (like a floating video call window / brainrot overlay), plays ~10 sec with sound off or subtle sound. Status bar during video: `⚠ attention span: reconnecting…`
- **[B3]** Video fades out. Status bar: `attention span: restored ✔`

**Assets:** the CAP-styled Subway Surfer video (you have this generated already).

**What you say:**

> "Now. Before we start, a confession. I know that at this conference, slides are… let's say, *not the love language*. Code is. So I did what any reasonable developer would do — *(B1)* — I built the entire presentation to look like VS Code. Left side file explorer, terminal at the bottom, everything's a markdown file. You're not watching slides. You're *reviewing a repository*. Completely different thing.
>
> And for those of you where it's 4 p.m., the coffee has worn off, and even VS Code is too much right now — I've also prepared some professional-grade distraction. *(B2 — let the video run, say nothing for ~5 seconds, then:)* You're welcome. It'll be back if I see anyone yawning. *(B3)*
>
> Alright — theory. Let's go."

---

### Slide 3 — A Brief History of Ruining Developers' Joy (0:45)

**VS Code chrome:**
- Explorer: `.theory/01-history.md` pops in (with new-file flash) when the slide opens.
- Active tab: `01-history.md`
- Bottom panel: **OUTPUT**, channel "Industry", one line per build (scrolls in with each build): `[1999] joy –20%` → `[2003] joy –35%` → `[2011] joy –50%` → `[2026] joy: null`

**On the slide:**

> **The software industry has a hobby: destroying everything developers love.**
>
> - 🧑‍🤝‍🧑 **Pair Programming** — two people negotiating every semicolon as if their life depends on it
> - 🧪 **TDD** — writing code for code that doesn't exist yet
> - 🏃 **Scrum** — slicing your work into fragments management can manage
> - 📄 **2026: Spec-Driven Development** — the new thing every vibe coder and wannabe product manager is excited about

**Builds:**

- Slide opens with **only the headline** + the AI image of a happy developer alone in a dark basement, lit by monitor glow (right half of the editor).
- **[B1]** Pair Programming bullet types in; basement image dims slightly.
- **[B2]** TDD bullet types in.
- **[B3]** Scrum bullet types in.
- **[B4]** SDD bullet types in **in red, styled like a Git merge-conflict marker** (`>>>>>>> incoming: SDD`); basement image now almost fully dark.

**Assets:** AI image — *"developer alone at night in a cozy dark basement, face lit only by monitor glow, visibly content, retro-nostalgic mood"*.

**What you say:**

> "Let's be honest. Sitting alone in a dark room, tinkering with your code — *(gesture at image)* — that was the best part of this job. And the industry has this unexplained need to destroy everything that's quiet, satisfying, and can actually make you happy.
>
> *(B1)* First: pair programming — fighting about one unimportant line of code for eight hours. *(B2)* Then test-driven development — writing tests for code that doesn't exist yet. *(B3)* Then Scrum — standups, refinements, reviews, retros… everything except developing. *(B4)* And now: Spec-Driven Development. And here's the punchline — the one thing developers hate writing more than tests is documentation. So the new hot methodology is: *write the documentation first.*
>
> Stay with me. Because unlike the others — this one might actually be fun"

---

### Slide 4 — Vibe Coding: Honeymoon & Hangover (1:15)

**VS Code chrome:**
- Explorer: `.theory/02-vibes.md` pops in.
- Active tab: `02-vibes.md`
- Bottom panel: **PROBLEMS** — starts empty ("No problems detected 🎉"), then fills during the builds (see below). This panel is the joke engine of the slide.
- Status bar: `branch: yolo-main*` · language mode: `Vibes`

**On the slide:**

> **Vibe Coding** *(Karpathy, Feb 2025)* — prompt, generate, pray, repeat
>
> Same prompt, 100 runs → **100 different architectures.**
> A slot machine with a Git integration. 🎰
>
> ```
> productivity
>     ▲
>     │  🏔️ Vibe Peak (to-do apps: +80%!)
>     │       \
>     │        \
> ────┼─────────\──────────────── baseline
>     │          \____
>     │        💀 Complexity Trough
>     │        (your CAP project lives here)
>     └──────────────────────────▶ complexity
> ```

**Builds:**

- Slide opens with headline + "prompt, generate, pray, repeat" line only.
- **[B1]** "Same prompt, 100 runs…" + slot machine line appear.
- **[B2]** The U-curve **draws itself left to right** (animated SVG path), stopping at the top of the Vibe Peak. Pause here while you praise vibe coding.
- **[B3]** The curve continues drawing — *falls off the cliff* into the trough. Simultaneously the **PROBLEMS panel floods** (entries scroll in rapidly, ~8 lines):
  `⚠ srv/service.js — OData V2 syntax (deprecated since forever)`
  `⚠ db/schema.cds — entity 'Bookz' does not match any naming convention known to humanity`
  `✖ srv/handler.js — imports 'express' inside a CAP project`
  `✖ auth.js — endpoint public. all of them. everywhere.`
  …plus a red problems-counter badge in the status bar counting up: `⚠ 247`.

**What you say:**

> "Quick recap. Vibe coding, term coined by Karpathy: describe what you want, surrender to the vibes, never look at the code. *(B1)* The catch: run the same prompt a hundred times, you get a hundred different architectures. It's a slot machine with a Git integration.
>
> *(B2)* And to be fair — the slot machine pays out! For prototypes, PoCs, to-do apps, the data shows massive speed-ups. This is the Vibe Peak, and it's real.
>
> *(B3 — let the problems flood in, wait a beat)* …and this is what happens when you point the same approach at a real system. Multi-tenancy, draft handling, authorization, an S/4 integration. I call it the Complexity Trough: productivity drops *below* doing it yourself. This isn't a feeling — METR ran a randomized controlled trial: experienced developers on mature codebases were 19% *slower* with AI. And here's the kicker: they *believed* they'd been 20% faster. Because the AI one-shots a hallucination into your codebase in three seconds — and you debug it for three hours.
>
> The root cause: English only *feels* precise. 'Customers can order books' — lovely. What happens when two customers order the *last copy* at the same moment — and one request times out mid-transaction? *That's* where real engineering lives. And vibes don't cover it."

---

### Slide 5 — Spec-Driven Development: The Flip (0:45)

**VS Code chrome:**
- Explorer: `.theory/03-the-flip.md` pops in.
- Active tab: `03-the-flip.md`
- Bottom panel: **PROBLEMS** — the 247 problems from the previous slide are still there. They get "fixed" in B2 (see builds).
- Status bar: branch changes to `branch: spec/001-sanity`

**On the slide:**

> **The flip: the spec is the source of truth. Code is the compilation target.**
>
> | | Traditional | Vibe Coding | SDD |
> |---|---|---|---|
> | Source of truth | the code | the chat history 💀 | **the spec** |
> | Docs | written after, rots in Confluence | what docs? | **written first, stays alive** |
> | AI's role | autocomplete | unsupervised creative genius | **executor of a contract** |

**Builds:**

- Slide opens with the headline only.
- **[B1]** Table appears **column by column**: Traditional → click → Vibe Coding → click → SDD column slams in bold. (Counts as B1 with 2 sub-clicks, or merge into one if you're pressed for time.)
- **[B2]** On the SDD column appearing: the **PROBLEMS panel visibly clears** — entries fade out, badge counts down to `⚠ 0`, panel shows "No problems detected 🎉".

**What you say:**

> "So here's the flip. You don't start with code — you start with a precise, structured document: what you're building, why, the constraints, what success looks like. And this spec isn't documentation *about* the system. It *is* the system's source of truth — the code is just its compilation target.
>
> *(B1)* I hear you: 'We've always had specs. They're called PRDs and they die in Confluence.' True. Traditionally the spec is an afterthought — you write it, feel good about yourself, file it, and it rots. The difference now: the spec isn't for humans to ignore. It's an execution contract for an AI agent. And the agent doesn't get bored, doesn't skip ahead, doesn't say 'I'll update the docs later.' *(B2)*
>
> If this sounds like the software development lifecycle you already know — requirements, design, tasks, implementation — that's because it is. The only new thing: the tasks get handed to an agent instead of the poor dev."

---

### Slide 6 — How SDD Actually Works (1:30) ⭐ core slide

**VS Code chrome — this slide IS the explorer animation:**
- Active tab: `04-workflow.md`
- The star of this slide is the **file tree growing on the left**, in sync with the builds. This is where the VS Code design pays for itself.
- Bottom panel: **TERMINAL**, one fake command per build (typed with typewriter effect, then a brief "✔ done").

**On the slide (editor, final state — appears step by step):**

> **One workflow, five artifacts. All markdown. All versioned. All reviewed by YOU.**
>
> **0 · Constitution** — your project's immutable laws
> &nbsp;&nbsp;&nbsp;&nbsp;*"Everything is CDS. Never expose db/ directly. @requires on every service. No handler without a test."*
>
> **1 · Specify** — WHAT & WHY, no tech: user stories, acceptance criteria, edge cases
>
> **2 · Plan** — HOW: data model, service design, annotations — checked against the constitution
>
> **3 · Tasks** — the plan, shredded into atomic, verifiable work items
>
> **4 · Implement** — the agent executes task by task. You review diffs, not vibes.
>
> *Names vary by tool (Spec Kit, Kiro, OpenSpec…) — the workflow doesn't.*

**Builds (each build = one workflow step; explorer + terminal + editor move together):**

- Slide opens with the headline only. Explorer unchanged.
- **[B1] Constitution:** terminal types `> /constitution` → explorer: `memory/constitution.md` pops in → editor shows step 0 incl. the four example "laws" (styled like a law paragraph, § symbol).
- **[B2] Specify:** terminal `> /specify "a bookshop with catalog & orders"` → explorer: `specs/001-bookshop/spec.md` pops in → editor shows step 1.
- **[B3] Plan:** terminal `> /plan` → explorer: `specs/001-bookshop/plan.md` pops in → editor shows step 2.
- **[B4] Tasks:** terminal `> /tasks` → explorer: `specs/001-bookshop/tasks.md` pops in → editor shows step 3. Optional gag: the file gets a badge `47` like unread notifications.
- **[B5] Implement:** terminal `> /implement` → explorer: `db/schema.cds`, `srv/cat-service.cds`, `srv/cat-service.js`, `test/` pop in *as a rapid cascade* → editor shows step 4 + the tool-agnostic footnote.

**What you say:**

> "So how does it work concretely? One workflow, five artifacts — all markdown files in your repo, all versioned, all reviewed by you before anything moves on.
>
> *(B1)* Step zero, once per project: the **constitution**. Your team's non-negotiable laws. Everything is CDS, no ORMs. The domain model is never exposed directly. Every service requires a role. No handler without a test. This is the implicit knowledge you normally transfer through three years of code-review pain — made explicit. Every later step is checked against it.
>
> *(B2)* Then, per feature: **specify**. What and why — user stories, acceptance criteria, edge cases. Deliberately no tech stack yet. This is where you catch the last-copy questions *before* they're bugs.
>
> *(B3)* **Plan**: now the how. Entities, service projections, annotations — and the agent validates its own plan against the constitution. If the plan says 'let's add MongoDB', the constitution says no.
>
> *(B4)* **Tasks**: the plan gets shredded into atomic work items, each traceable back to a requirement, each independently verifiable. These are basically Jira tickets — except they're useful, in markdown, and nobody has to groom them on a Tuesday afternoon.
>
> *(B5)* And only now: **implement**. The agent executes task by task, and you review small diffs against a contract — instead of 3,000 lines against a vibe. And the crucial part: at every step there's a *human gate*. You edit the spec, you correct the plan, you reorder the tasks. It's not waterfall — if reality disagrees, you update the spec and keep going. The spec stays alive.
>
> By the way — the step names vary by tool. Spec Kit, which we'll use in the demo, Kiro, OpenSpec — different commands, same workflow. Don't marry the tool, marry the discipline."

---

### Slide 7 — Why CAP Was Born for This (+ the one caveat) (1:00)

**VS Code chrome:**
- Explorer: unchanged (the grown tree from Slide 6 stays visible — it's the proof).
- Active tab: `05-cap.md` — gag: the tab icon is the CDS file icon although it's an .md.
- Bottom panel: starts on **OUTPUT** ("capire"), switches to **PROBLEMS** at B3 (see builds).
- Status bar: language mode `CDS ❤ Markdown`

**On the slide:**

> **Plot twist: CAP developers have been doing SDD since 2018.**
>
> - CDS **is** a spec: declarative domain model, services, annotations
> - `@readonly` · `@requires: 'Admin'` · `@odata.draft.enabled` → behavior as metadata
> - Spec and code are *structurally the same artifact* → minimal semantic gap
>
> **One caveat:** SDD fixes *intent* — not *knowledge*.
> Generic LLMs barely know CAP → give the agent live context: **CAP MCP server** (queries your real CDS model + current capire docs) instead of 2023 memories.

**Builds:**

- Slide opens with the plot-twist headline only. *(Pause for the laugh — this is the audience-flattery beat.)*
- **[B1]** The three CDS bullets type in one by one (one click, staggered auto-animation).
- **[B2]** A CDS snippet slides in on the right half of the editor: `entity Books { key ID: UUID; title: String; author: Association to Authors; }` with `@odata.draft.enabled` highlighted — visual proof that CDS reads like a spec.
- **[B3]** The caveat block appears **and** the bottom panel flips to PROBLEMS with exactly one warning: `⚠ agent knowledge — 'CAP' resolved to training data from 2023. Suggest: MCP server.` Status-bar badge: `⚠ 1`.

**What you say:**

> "Now the part where you get to feel smug. While the JavaScript world is having an existential crisis about specs — you've been writing them since 2018. It's called CDS.
>
> *(B1)* Think about it: a CDS model *is* a specification. Declarative. Entities, services, authorization, UI behavior — decoupled from database and protocol. *(B2)* When you write `@odata.draft.enabled`, you're not implementing draft handling — you're *declaring* it. In most stacks there's a huge gap between spec-in-English and code-in-imperative-logic. In CAP, the spec and half the implementation are structurally the same artifact. An AI generating CDS isn't coding from a spec — it's translating one spec into a slightly more formal one. Much shorter jump, much less to hallucinate.
>
> *(B3)* One honest caveat, and then we build: SDD fixes *intent* — it does not fix *knowledge*. A perfect spec plus a model that barely knows CAP still gives you a very well-organized pile of wrong code. Deterministically wrong instead of randomly wrong — not the upgrade you wanted. The fix: give the agent live context. SAP ships an official CAP MCP server — the agent queries your *actual* compiled CDS model and the *current* capire docs instead of its 2023 memories. One config entry. Do it before you do anything else."

*(⏱️ If you're behind schedule: cut B3 and the last paragraph — 25 sec saved. The abstract promise on MCP is then covered only if the co-speaker shows the config in the demo. If you're comfortably on time, keep it.)*

---

### Slide 8 — Demo Handoff (0:20)

**VS Code chrome:**
- Explorer: the full grown tree, all files visible.
- Active tab: `06-demo.md`
- Bottom panel: **TERMINAL**, blinking cursor after: `$ specify init bookshop_` — as if waiting for the co-speaker to press Enter.
- Status bar: `⚠ 0 problems` · `branch: spec/001-bookshop` · `Live Share: [co-speaker name] joined 👋`

**On the slide:**

> **Enough theory. Let's build a bookshop.**
>
> constitution → specify → plan → tasks → implement
> Live. On conference Wi-Fi. **What could possibly go wrong?** 🎲

**Builds:**

- **[B1]** (optional, if it gets a laugh:) the Subway-Surfer PiP window flashes in for 1 second and gets closed with a visible ✕ click — "not yet".

**What you say:**

> "Enough theory. There's exactly one way to prove any of this works, and that's doing it live, in front of all of you, on conference Wi-Fi. Every file you just saw appear in this fake explorer — you'll now see generated for real. [Co-speaker name], the stage is yours."

---

## PART 2 — LIVE DEMO (co-speaker)

*Content prepared by the co-speaker. Suggested skeleton so both parts click together — the talk's Slide 6 builds (B1–B5) mirror the demo steps 1:1, so the audience recognizes each artifact. Keep the VS Code presentation open as fallback: each Slide-6 build doubles as a "here's one I prepared earlier" screenshot.*

| Step | Action (Spec Kit naming — adapt if tooling differs) | Run live? | Show afterwards |
|---|---|---|---|
| 0 | initialize project | ✅ fast | `.specify/` structure: templates, scripts, agent prompts |
| 1 | constitution | ✅ | `memory/constitution.md` — the CAP laws from Slide 6 |
| 2 | specify | ✅ | `specs/001-bookshop/spec.md` — user stories, acceptance criteria, edge cases |
| 3 | plan | ✅ | `plan.md` — `db/schema.cds` entities, `srv/` projections, annotation strategy |
| 4 | tasks | ✅ | `tasks.md` — atomic tasks, traceable to requirements |
| 5 | implement | ⚠️ long-running → start live, switch to pre-baked result | generated `db/`, `srv/`, tests → `cds watch` 🎉 |

**Demo insurance:** finished repo in a second folder + screenshots of every generated file. If the live run stalls: *"and here's one I prepared earlier."*

---

## CLOSING — Key Takeaways (after demo, ~40 sec, either speaker)

**VS Code chrome:** active tab `TAKEAWAYS.md`, explorer fully grown, PROBLEMS: 0. Status bar: `session: 20:00 → done ✔`

**On the slide:**

> 1. **Vibes don't scale.** The complexity trough is real — enterprise CAP lives at the bottom of it.
> 2. **The workflow, not the tool:** constitution → specify → plan → tasks → implement. Human gate at every step.
> 3. **CAP is SDD-native.** CDS was a machine-readable spec before it was cool.
> 4. **You're still the engineer.** The AI executes the contract. *You* write it.

**Builds:** **[B1–B4]** one takeaway per click. Optional **[B5]**: Subway-Surfer video returns full-screen for 2 seconds, gets closed, replaced by "Thank you / Questions?".

**What you say:**

> "Four things to take home. Vibes don't scale — great for prototypes, fatal for enterprise. It's the workflow that matters, not the tool — constitution, specify, plan, tasks, implement, with a human gate at every step. CAP is uniquely positioned, because CDS has been a machine-readable spec all along. And finally: notice what stayed human in that demo — understanding the problem, defining the constraints, reviewing the plan. The AI executes the contract. *You* write it. That's not the death of software engineering — that's software engineering with the boring parts delegated. Thank you!"

*(⚠️ If the demo had to fall back to the prepared repo, swap the opener of takeaway 4: "notice what stayed human — even when the Wi-Fi didn't: understanding the problem, defining the constraints, reviewing the plan.")*

---

## APPENDIX

### Timing budget (Part 1 target: 7:00 — you're a fast speaker, this is written for normal pace, so you have margin)

| Slide | Time | Cumulative |
|---|---|---|
| 1 Title | 0:30 | 0:30 |
| 2 VS Code reveal + video | 0:45 | 1:15 |
| 3 Ruining joy | 0:45 | 2:00 |
| 4 Vibes: honeymoon & hangover | 1:15 | 3:15 |
| 5 The flip | 0:45 | 4:00 |
| 6 How SDD works ⭐ | 1:30 | 5:30 |
| 7 CAP + caveat | 1:00 | 6:30 |
| 8 Handoff | 0:20 | 6:50 |

**Cut order if running long:** (1) Slide 7 B3/MCP caveat (–25 s), (2) Slide 3 down to headline + image + one sentence (–30 s), (3) Slide 5 table to a single sentence (–30 s). **Never cut Slide 6** — it's the abstract's promise and the demo's setup.

### Assets to generate (AI images/video)

| Asset | Used in | Prompt sketch |
|---|---|---|
| Subway Surfer video, CAP optics | Slide 2 (PiP), optional Closing | ✅ already generated |
| Happy developer, dark basement, monitor glow | Slide 3 | "developer alone at night in a cozy dark basement, face lit only by monitor glow, visibly content, warm retro mood" |
| (optional) Slot machine with git commit symbols on the reels | Slide 4 | "casino slot machine, reels showing git branch/commit icons, jackpot light, flat illustration" |
| (optional) Stone tablet "constitution" with § and CDS keywords | Slide 6 B1 | "stone law tablet engraved with paragraphs symbol and code keywords, dramatic light, slightly comic" |

### Spare jokes (drop in where the room responds)

- On job titles: *"If your LinkedIn already says 'Prompt Architect' — no judgment. But maybe wait one more hype cycle before printing business cards."*
- On multi-agent hype: *"There are frameworks where you orchestrate a whole team of AI agents talking to each other through markdown files while you sit in the middle making sure they don't lose the plot. Congratulations — you've reinvented middle management, except the reports hallucinate."*
- On the demo: *"A live demo with AI and conference Wi-Fi — we've essentially added a third speaker, and nobody knows what it's going to say."*
- On specs rotting: *"Our old specs weren't 'living documents.' They were documents the way a museum exhibit is an animal."*
- Closing alt: *"AI won't take your job. But a CAP developer with a constitution.md might."*
- On the VS Code design (if someone smiles at the reveal): *"Yes, the file tree on the left is real. Well — emotionally real."*

**Sources:** session abstract (topic.md), talk transcripts 1–3, research.md (constitution, Spec-Kit-phases, CAP MCP server, SAP MCP dilemma), METR RCT on AI & experienced developers (metr.org, July 2025: 19% slower on mature codebases, perceived 20% faster).
