# Cue Card — Beyond Vibe Coding

*(Bn)* = Klick · **fett** = Schlüsselphrase wörtlich bringen · Ziel Part 1: **7:00**

---

## 1 · Title — 0:30

- Show of hands: **AI für CAP-Code dieses Jahr?** → Hand oben lassen: **wer nutzt SDD?** → Hände sinken: **"That drop-off you just saw — that's this talk"**
- Plan: Theorie (ich) → **Abdulbasıt baut Bookshop live**
- "Very impressive or very entertaining — **win-win either way**"

## 2 · Reveal — 0:45 (cum. 1:15)

- Confession: slides are **not the love language** here — code is
- *(B1)* → VS Code-Verwandlung: "You're not watching slides, you're **reviewing a repository**"
- *(B2)* Subway Surfer PiP → **~5 Sek. NICHTS sagen** → "You're welcome. It'll be back if I see anyone yawning" *(B3)*
- "Alright — theory. Let's go."

## 3 · Ruining Joy — 0:45 (cum. 2:00)

- Dunkler Keller = **the best part of this job** — Industrie zerstört alles Schöne
- *(B1)* Pair Programming ("8 hours fighting about one line") → *(B2)* TDD → *(B3)* Scrum ("everything except developing")
- *(B4)* SDD-Punchline: Devs hassen Doku noch mehr als Tests → neue Methode = **"write the documentation first"**
- "Stay with me — this one might actually be fun"

## 4 · Vibes — 1:15 (cum. 3:15) ⏱ längster Theorieteil

- Karpathy: prompt, generate, **pray**, repeat
- *(B1)* 100 Runs → 100 Architekturen = **"slot machine with a Git integration"**
- *(B2 — Kurve hoch)* Fair: **the slot machine pays out!** Prototypen/To-do-Apps → Vibe Peak ist real
- *(B3 — Absturz + Problems fluten, Beat warten)* Reales System → **Complexity Trough** (METR-RCT: **19 % langsamer**, gefühlt 20 % schneller): 3 Sek. halluzinieren, **3 Stunden debuggen**
- Root cause: **"English only *feels* precise"** → Last-copy-Beispiel (2 Kunden, letztes Exemplar, Timeout mid-transaction)

## 5 · The Flip — 0:45 (cum. 4:00)

- Spec = **source of truth**, Code = **compilation target**
- *(B1 — Tabelle)* Einwand vorwegnehmen: "PRDs **die in Confluence**" → Unterschied: Spec = **execution contract für den Agenten** (wird nicht müde, überspringt nichts) *(B2 — Problems → 0)*
- Das ist der bekannte SDLC — neu ist nur: **Tasks gehen an den Agenten** statt an den armen Dev

## 6 · Workflow ⭐ — 1:30 (cum. 5:30) — NIE KÜRZEN

- Ein Workflow, **5 Artefakte, alles Markdown, alles reviewed by YOU**
- *(B1)* **Constitution** — non-negotiable laws (CDS only, kein db/-Expose, @requires, Tests) = "3 Jahre Code-Review-Schmerz, explizit gemacht"
- *(B2)* **Specify** — WHAT & WHY, kein Tech-Stack → Last-copy-Fragen VOR den Bugs
- *(B3)* **Plan** — HOW, gegen Constitution validiert → "MongoDB? Constitution says no"
- *(B4)* **Tasks** — atomar, traceable = "Jira tickets, except they're useful"
- *(B5)* **Implement** — "review **small diffs against a contract**, not 3,000 lines against a vibe" → **human gate at every step**, Spec bleibt lebendig
- Tools: Spec Kit / Kiro / OpenSpec — **"don't marry the tool, marry the discipline"**

## 7 · CAP — 1:00 (cum. 6:30)

- **"Now the part where you get to feel smug"** — CAP macht SDD **seit 2018: CDS** → Lacher abwarten!
- *(B1)* CDS **ist** eine Spec: deklarativ, entkoppelt
- *(B2)* `@odata.draft.enabled` = **declaring, not implementing** → "translating one spec into a slightly more formal one" → weniger Halluzination
- *(B3)* Caveat: SDD fixt **intent, nicht knowledge** → "deterministically wrong is not the upgrade you wanted" → **CAP MCP server**, one config entry
- ⏱ **Bei Zeitnot: B3 komplett streichen (–25 s)**

## 8 · Handoff — 0:20 (cum. 6:50)

- "One way to prove it: **live, on conference Wi-Fi**"
- Fake Explorer → jetzt **echt generiert**
- **"Abdulbasıt, the stage is yours."**

## Closing (nach Demo, ~40 s)

- *(B1)* **Vibes don't scale** — Prototypen ja, Enterprise nein
- *(B2)* **Workflow, not the tool** — human gate at every step
- *(B3)* **CAP is SDD-native** — CDS war Spec, bevor es cool war
- *(B4)* **You're still the engineer** — "AI executes the contract. *You* write it." → "boring parts delegated" → **Thank you!**
- ⚠️ Demo im Fallback gelaufen? B4-Opener tauschen: **"what stayed human — even when the Wi-Fi didn't"**

---

### Notfall-Kürzungen (Reihenfolge)
1. Slide 7 MCP-Caveat (–25 s) · 2. Slide 3 auf 1 Satz (–30 s) · 3. Slide 5 Tabelle auf 1 Satz (–30 s)

### Spare Jokes (bei guter Stimmung)
- "Prompt Architect" auf LinkedIn → wait one more hype cycle
- Multi-Agent = **reinvented middle management, except the reports hallucinate**
- Demo = third speaker, nobody knows what it's going to say
- Alte Specs = Museum exhibit
- "AI won't take your job. But a CAP developer with a constitution.md might."
