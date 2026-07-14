# Speaker Notes — Beyond Vibe Coding (Full Script)

**Part 1 target: 7:00** · *(Bn)* = click/build · stage directions in *italics*

---

## Slide 1 — Title (0:30 · cum. 0:30)

> Hi everyone. Quick show of hands: who here has asked an AI to write CAP code this year? *(pause)* Keep your hand up if you used spec driven development. *(watch the hands drop)* That drop-off you just saw — that's this talk.
>
> Here's the plan for the next 20 minutes: a bit of theory from me — what spec-driven development actually is and why it matters for CAP — and then Abdulbasıt builds a real CAP bookshop application live on stage. Which will either be very impressive or very entertaining. Win-win for you either way.

---

## Slide 2 — The Reveal + Emergency Entertainment (0:45 · cum. 1:15)

> Now. Before we start, a confession. I know that at this conference, slides are… let's say, *not the love language*. Code is. So I did what any reasonable developer would do — *(B1: title slide shrinks into a tab, VS Code chrome slides in)* — I built the entire presentation to look like VS Code.  You're not watching slides. You're *reviewing a repository*. Completely different thing.
>
> And for those of you where it's 4 p.m., the coffee has worn off, and even VS Code is too much right now — I've also prepared some professional-grade distraction. *(B2: Subway Surfer PiP fades in — let it run, say nothing for ~5 seconds, then:)* You're welcome. It'll be back if I see anyone yawning. *(B3: video out)*
>
> Alright — theory. Let's go.

---

## Slide 3 — A Brief History of Ruining Developers' Joy (0:45 · cum. 2:00)

> Let's be honest. Sitting alone in a dark room, tinkering with your code — *(gesture at image)* — that was the best part of this job. And the industry has this unexplained need to destroy everything that's quiet, satisfying, and can actually make you happy.
>
> *(B1)* First: pair programming — fighting about one unimportant line of code for eight hours. *(B2)* Then test-driven development — writing tests for code that doesn't exist yet. *(B3)* Then Scrum — standups, refinements, reviews, retros… everything except developing. *(B4)* And now: Spec-Driven Development. And here's the punchline — the one thing developers hate writing more than tests is documentation. So the new hot methodology is: *write the documentation first.*
>
> Stay with me. Because unlike the others — this one might actually be fun.

---

## Slide 4 — Vibe Coding: Honeymoon & Hangover (1:15 · cum. 3:15)

> Quick recap. Vibe coding, term coined by Karpathy: describe what you want, surrender to the vibes, never look at the code. *(B1)* The catch: run the same prompt a hundred times, you get a hundred different architectures. It's a slot machine with a Git integration.
>
> *(B2: curve draws up to the peak)* And to be fair — the slot machine pays out! For prototypes, PoCs, to-do apps, the data shows massive speed-ups. This is the Vibe Peak, and it's real.
>
> *(B3: curve falls off the cliff, PROBLEMS panel floods — wait a beat)* …and this is what happens when you point the same approach at a real system. Multi-tenancy, draft handling, authorization, an S/4 integration. I call it the Complexity Trough: productivity drops *below* doing it yourself. This isn't a feeling — METR ran a randomized controlled trial: experienced developers on mature codebases were 19% *slower* with AI. And here's the kicker: they *believed* they'd been 20% faster. Because the AI one-shots a hallucination into your codebase in three seconds — and you debug it for three hours.
>
> The root cause: English only *feels* precise. 'Customers can order books' — lovely. What happens when two customers order the *last copy* at the same moment — and one request times out mid-transaction? *That's* where real engineering lives. And vibes don't cover it.

---

## Slide 5 — Spec-Driven Development: The Flip (0:45 · cum. 4:00)

> So here's the flip. You don't start with code — you start with a precise, structured document: what you're building, why, the constraints, what success looks like. And this spec isn't documentation *about* the system. It *is* the system's source of truth — the code is just its compilation target.
>
> *(B1: table appears column by column)* I hear you: 'We've always had specs. They're called PRDs and they die in Confluence.' True. Traditionally the spec is an afterthought — you write it, feel good about yourself, file it, and it rots. The difference now: the spec isn't for humans to ignore. It's an execution contract for an AI agent. And the agent doesn't get bored, doesn't skip ahead, doesn't say 'I'll update the docs later.' *(B2: PROBLEMS panel clears to 0)*
>
> If this sounds like the software development lifecycle you already know — requirements, design, tasks, implementation — that's because it is. The only new thing: the tasks get handed to an agent instead of the poor dev.

---

## Slide 6 — How SDD Actually Works ⭐ core slide (1:30 · cum. 5:30)

> So how does it work concretely? One workflow, five artifacts — all markdown files in your repo, all versioned, all reviewed by you before anything moves on.
>
> *(B1: `/constitution` → memory/constitution.md pops in)* Step zero, once per project: the **constitution**. Your team's non-negotiable laws. Everything is CDS, no ORMs. The domain model is never exposed directly. Every service requires a role. No handler without a test. This is the implicit knowledge you normally transfer through three years of code-review pain — made explicit. Every later step is checked against it.
>
> *(B2: `/specify` → spec.md pops in)* Then, per feature: **specify**. What and why — user stories, acceptance criteria, edge cases. Deliberately no tech stack yet. This is where you catch the last-copy questions *before* they're bugs.
>
> *(B3: `/plan` → plan.md pops in)* **Plan**: now the how. Entities, service projections, annotations — and the agent validates its own plan against the constitution. If the plan says 'let's add MongoDB', the constitution says no.
>
> *(B4: `/tasks` → tasks.md pops in, badge 47)* **Tasks**: the plan gets shredded into atomic work items, each traceable back to a requirement, each independently verifiable. These are basically Jira tickets — except they're useful, in markdown, and nobody has to groom them on a Tuesday afternoon.
>
> *(B5: `/implement` → db/, srv/, test/ cascade in)* And only now: **implement**. The agent executes task by task, and you review small diffs against a contract — instead of 3,000 lines against a vibe. And the crucial part: at every step there's a *human gate*. You edit the spec, you correct the plan, you reorder the tasks. It's not waterfall — if reality disagrees, you update the spec and keep going. The spec stays alive.
>
> By the way — the step names vary by tool. Spec Kit, which we'll use in the demo, Kiro, OpenSpec — different commands, same workflow. Don't marry the tool, marry the discipline.

---

## Slide 7 — Why CAP Was Born for This (+ the one caveat) (1:00 · cum. 6:30)

> Now the part where you get to feel smug. While the JavaScript world is having an existential crisis about specs — you've been writing them since 2018. It's called CDS. *(pause for the laugh)*
>
> *(B1: three CDS bullets type in)* Think about it: a CDS model *is* a specification. Declarative. Entities, services, authorization, UI behavior — decoupled from database and protocol. *(B2: CDS snippet slides in)* When you write `@odata.draft.enabled`, you're not implementing draft handling — you're *declaring* it. In most stacks there's a huge gap between spec-in-English and code-in-imperative-logic. In CAP, the spec and half the implementation are structurally the same artifact. An AI generating CDS isn't coding from a spec — it's translating one spec into a slightly more formal one. Much shorter jump, much less to hallucinate.
>
> *(B3: caveat block + 1 problem in panel)* One honest caveat, and then we build: SDD fixes *intent* — it does not fix *knowledge*. A perfect spec plus a model that barely knows CAP still gives you a very well-organized pile of wrong code. Deterministically wrong instead of randomly wrong — not the upgrade you wanted. The fix: give the agent live context. SAP ships an official CAP MCP server — the agent queries your *actual* compiled CDS model and the *current* capire docs instead of its 2023 memories. One config entry. Do it before you do anything else.

⏱️ *If behind schedule: cut B3 + last paragraph (–25 s).*

---

## Slide 8 — Demo Handoff (0:20 · cum. 6:50)

> Enough theory. There's exactly one way to prove any of this works, and that's doing it live, in front of all of you, on conference Wi-Fi. Every file you just saw appear in this fake explorer — you'll now see generated for real. Abdulbasıt, the stage is yours.

---

## Closing — Key Takeaways (after demo, ~40 sec, either speaker)

> Four things to take home. *(B1)* Vibes don't scale — great for prototypes, fatal for enterprise. *(B2)* It's the workflow that matters, not the tool — constitution, specify, plan, tasks, implement, with a human gate at every step. *(B3)* CAP is uniquely positioned, because CDS has been a machine-readable spec all along. *(B4)* And finally: notice what stayed human in that demo — understanding the problem, defining the constraints, reviewing the plan. The AI executes the contract. *You* write it. That's not the death of software engineering — that's software engineering with the boring parts delegated. Thank you!

⚠️ *If the demo had to fall back to the prepared repo, swap the opener of takeaway 4: "notice what stayed human — even when the Wi-Fi didn't: understanding the problem, defining the constraints, reviewing the plan."*

---

## Appendix — Spare jokes (drop in where the room responds)

- **Job titles:** "If your LinkedIn already says 'Prompt Architect' — no judgment. But maybe wait one more hype cycle before printing business cards."
- **Multi-agent hype:** "There are frameworks where you orchestrate a whole team of AI agents talking to each other through markdown files while you sit in the middle making sure they don't lose the plot. Congratulations — you've reinvented middle management, except the reports hallucinate."
- **The demo:** "A live demo with AI and conference Wi-Fi — we've essentially added a third speaker, and nobody knows what it's going to say."
- **Specs rotting:** "Our old specs weren't 'living documents.' They were documents the way a museum exhibit is an animal."
- **Closing alt:** "AI won't take your job. But a CAP developer with a constitution.md might."
- **VS Code design:** "Yes, the file tree on the left is real. Well — emotionally real."

## Appendix — Cut order if running long

1. Slide 7 B3 / MCP caveat (–25 s)
2. Slide 3 down to headline + image + one sentence (–30 s)
3. Slide 5 table to a single sentence (–30 s)

**Never cut Slide 6** — it's the abstract's promise and the demo's setup.
