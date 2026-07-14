# Speaker Notes — Beyond Vibe Coding (Full Script)

**Part 1 target: 7:00** · *(Bn)* = click/build · stage directions in *italics*

---

## Slide 1 — Title (0:30 · cum. 0:30)

> Hi everyone. Quick show of hands: who here has asked an AI to write CAP code this year? *(pause)* Keep your hand up if you used spec-driven development. *(watch the hands drop)* See how many hands just went down? That gap — that's exactly what this talk is about.
>
> Here's the plan for the next 20 minutes: first some theory from me — what spec-driven development is and why it fits CAP so well — and then Abdulbasıt builds a real CAP bookshop application live on stage. That will either be very impressive or very entertaining. Win-win for you either way.

---

## Slide 2 — The Reveal + Emergency Entertainment (0:45 · cum. 1:15)

> Now, before we start, I have to admit something. I know that at this conference, people don't really love slides. They love code. So I did what any reasonable developer would do — *(B1: title slide shrinks into a tab, VS Code chrome slides in)* — I built the whole presentation to look like VS Code. You're not watching slides. You're *reviewing a repository*. Completely different thing.
>
> And for those of you where it's 4 p.m., the coffee has stopped working, and even VS Code is too much right now — I also prepared some professional distraction. *(B2: Subway Surfer PiP fades in — let it run, say nothing for ~5 seconds, then:)* You're welcome. It comes back if I see anyone yawning. *(B3: video out)*
>
> Alright — theory. Let's go.

---

## Slide 3 — A Brief History of Ruining Developers' Joy (0:45 · cum. 2:00)

> Let's be honest. Sitting alone in a dark room, quietly working on your code — *(gesture at image)* — that was the best part of this job. And our industry keeps destroying everything that is quiet, satisfying, and actually makes you happy.
>
> *(B1)* First: pair programming — fighting for eight hours about one unimportant line of code. *(B2)* Then test-driven development — writing tests for code that doesn't exist yet. *(B3)* Then Scrum — standups, refinements, reviews, retros… everything except actual development. *(B4)* And now: Spec-Driven Development. And here's the punchline — the one thing developers hate writing even more than tests is documentation. So the new hot method is: *write the documentation first.*
>
> Stay with me. Because unlike the others — this one might actually be fun.

---

## Slide 4 — Vibe Coding: Honeymoon & Hangover (1:15 · cum. 3:15)

> Quick recap. Vibe coding — the term comes from Karpathy: describe what you want, trust the vibes, never look at the code. *(B1)* The problem: run the same prompt a hundred times, and you get a hundred different architectures. It's a slot machine with a Git integration.
>
> *(B2: curve draws up to the peak)* And to be fair — the slot machine pays out! For prototypes, PoCs, to-do apps, the numbers show massive speed-ups. This is the Vibe Peak, and it's real.
>
> *(B3: curve falls off the cliff, PROBLEMS panel floods — wait a beat)* …and this is what happens when you use the same approach on a real system. Multi-tenancy, draft handling, authorization, an S/4 integration. I call it the Complexity Trough: your productivity drops *below* doing it yourself. And this is not just a feeling — METR did a controlled study: experienced developers on mature codebases were 19% *slower* with AI. And the best part: they *believed* they had been 20% faster. Because the AI writes a hallucination into your codebase in three seconds — and you spend three hours debugging it.
>
> The root cause: English only *feels* precise. 'Customers can order books' — sounds nice. But what happens when two customers order the *last copy* at the same moment — and one request times out in the middle of the transaction? *That's* where real engineering happens. And vibes don't cover it.

---

## Slide 5 — Spec-Driven Development: The Flip (0:45 · cum. 4:00)

> So here's the flip. You don't start with code — you start with a precise, structured document: what you're building, why, the constraints, and what success looks like. And this spec is not documentation *about* the system. It *is* the system's source of truth — the code is just its compilation target.
>
> *(B1: table appears column by column)* I know what you're thinking: 'We've always had specs. They're called PRDs, and they die in Confluence.' True. Traditionally, the spec comes last — you write it, feel good about it, save it somewhere, and nobody ever reads it again. The difference now: the spec is not written for humans to ignore. It's an execution contract for an AI agent. And the agent doesn't get bored, doesn't skip steps, doesn't say 'I'll update the docs later.' *(B2: PROBLEMS panel clears to 0)*
>
> If this sounds like the software development lifecycle you already know — requirements, design, tasks, implementation — that's because it is. The only new thing: the tasks go to an agent instead of the poor developer.

---

## Slide 6 — How SDD Actually Works ⭐ core slide (1:30 · cum. 5:30)

> So how does it work in practice? One workflow, five artifacts — all markdown files in your repo, all versioned, all reviewed by you before the next step starts.
>
> *(B1: `/constitution` → memory/constitution.md pops in)* Step zero, once per project: the **constitution**. Your team's fixed rules — not up for discussion. Everything is CDS. The domain model is never exposed directly. Every service needs a role. No handler without a test. This is the knowledge you normally teach through three years of painful code reviews — now written down. Every later step is checked against it.
>
> *(B2: `/specify` → spec.md pops in)* Then, for each feature: **specify**. What and why — user stories, acceptance criteria, edge cases. On purpose: no tech stack yet. This is where you catch the last-copy questions *before* they become bugs.
>
> *(B3: `/plan` → plan.md pops in)* **Plan**: now the how. Entities, service projections, annotations — and the agent checks its own plan against the constitution. If the plan says 'let's add MongoDB', the constitution says no.
>
> *(B4: `/tasks` → tasks.md pops in, badge 47)* **Tasks**: the plan gets broken down into small, atomic work items — each one linked to a requirement, each one you can verify on its own. Basically Jira tickets — except they're useful, they're in markdown, and nobody has to groom them on a Tuesday afternoon.
>
> *(B5: `/implement` → db/, srv/, test/ cascade in)* And only now: **implement**. The agent works through the tasks one by one, and you review small diffs against a contract — instead of 3,000 lines against a vibe. And the important part: at every step there's a *human gate*. You edit the spec, you correct the plan, you reorder the tasks. It's not waterfall — if reality turns out different, you update the spec and keep going. The spec stays alive.
>
> By the way — the step names are different in every tool. Spec Kit, which we'll use in the demo, Kiro, OpenSpec — different commands, same workflow. Don't marry the tool, marry the discipline.

---

## Slide 7 — Why CAP Was Born for This (+ the one caveat) (1:00 · cum. 6:30)

> And now the part where you can feel a little proud of yourselves. While the JavaScript world is having an existential crisis about specs — you've been writing specs since 2018. It's called CDS. *(pause for the laugh)*
>
> *(B1: three CDS bullets type in)* Think about it: a CDS model *is* a specification. Declarative. Entities, services, authorization, UI behavior — independent of database and protocol. *(B2: CDS snippet slides in)* When you write `@odata.draft.enabled`, you're not implementing draft handling — you're *declaring* it. In most stacks, there's a big gap between the spec in English and the code in imperative logic. In CAP, the spec and half of the implementation are structurally the same artifact. An AI that generates CDS is not coding from a spec — it's translating one spec into a slightly more formal one. A much shorter jump, and much less room to hallucinate.
>
> *(B3: caveat block + 1 problem in panel)* One honest warning, and then we build: SDD fixes *intent* — it does not fix *knowledge*. A perfect spec plus a model that barely knows CAP still gives you a very well-organized pile of wrong code. Deterministically wrong instead of randomly wrong — not the upgrade you wanted. The fix: give the agent live context. SAP ships an official CAP MCP server — the agent reads your *actual* compiled CDS model and the *current* capire docs, instead of its memories from 2023. One config entry. Do this before anything else.

⏱️ *If behind schedule: cut B3 + last paragraph (–25 s).*

---

## Slide 8 — Demo Handoff (0:20 · cum. 6:50)

> Enough theory. There's exactly one way to prove that any of this works: live, in front of all of you, on conference Wi-Fi. Every file you just saw appear in this fake explorer — you will now see generated for real. Abdulbasıt, the stage is yours.

---

## Closing — Key Takeaways (after demo, ~40 sec, either speaker)

> Four things to take home. *(B1)* Vibes don't scale — great for prototypes, fatal for enterprise. *(B2)* The workflow matters, not the tool — constitution, specify, plan, tasks, implement, with a human gate at every step. *(B3)* CAP is in a perfect position, because CDS has been a machine-readable spec all along. *(B4)* And finally: look at what stayed human in this demo — understanding the problem, defining the constraints, reviewing the plan. The AI executes the contract. *You* write it. That's not the end of software engineering — that's software engineering with the boring parts delegated. Thank you!

⚠️ *If the demo had to fall back to the prepared repo, swap the opener of takeaway 4: "look at what stayed human — even when the Wi-Fi didn't: understanding the problem, defining the constraints, reviewing the plan."*

---

## Appendix — Spare jokes (drop in where the room responds)

- **Job titles:** "If your LinkedIn already says 'Prompt Architect' — no judgment. But maybe wait one more hype cycle before printing business cards."
- **Multi-agent hype:** "There are frameworks where you orchestrate a whole team of AI agents talking to each other through markdown files while you sit in the middle making sure they don't lose the plot. Congratulations — you've reinvented middle management, except the reports hallucinate."
- **The demo:** "A live demo with AI and conference Wi-Fi — we've basically added a third speaker, and nobody knows what it's going to say."
- **Specs rotting:** "Our old specs weren't 'living documents.' They were documents the way a museum exhibit is an animal."
- **Closing alt:** "AI won't take your job. But a CAP developer with a constitution.md might."
- **VS Code design:** "Yes, the file tree on the left is real. Well — emotionally real."

## Appendix — Cut order if running long

1. Slide 7 B3 / MCP caveat (–25 s)
2. Slide 3 down to headline + image + one sentence (–30 s)
3. Slide 5 table to a single sentence (–30 s)

**Never cut Slide 6** — it's the abstract's promise and the demo's setup.
