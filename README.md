# Juno PM

> Juno PM turns messy interview transcripts, support tickets and exec emails into one evidence-backed Opportunity Brief, so RocketShip PMs can defend every priority with a source ID.

Khaled Alamer · AI PM Cohort · September 2026

This repo is my final project for the **AI Product Management Certification**. Each module's artefact lives in its own folder; this README is the dashboard and the pitch. The presentation is [`pitch.html`](pitch.html).

---

## Module artefacts

### M1 · Prompting
- **System prompt** — [`01-prompting/system-prompt.md`](01-prompting/system-prompt.md)
- **Lovable prototype** — https://evidence-lane.lovable.app · debrief in [`01-prompting/lovable-prototype.md`](01-prompting/lovable-prototype.md)

### M2 · Strategy
- **Decision matrix** — [`02-strategy/decision-matrix.md`](02-strategy/decision-matrix.md)
- **AI Strategy one-pager** — [`02-strategy/strategy-one-pager.md`](02-strategy/strategy-one-pager.md)

### M3 · RAG / AI PRD
- **AI PRD** — [`03-rag-prd/prd.md`](03-rag-prd/prd.md)

### M4 · AI-Native UX
- **AI user flow** — [`04-ai-ux/user-flow.md`](04-ai-ux/user-flow.md) · diagram [`04-ai-ux/user-flow.png`](04-ai-ux/user-flow.png)
- **Trust-gap mitigations** — [`04-ai-ux/trust-gaps.md`](04-ai-ux/trust-gaps.md)

### M5 · Agentic Workflows
- **Agent Workflow Spec (AWSpec)** — [`05-agentic-workflows/awspec.md`](05-agentic-workflows/awspec.md)
- **Agent Control Panel** — [`05-agentic-workflows/agent-control-panel.md`](05-agentic-workflows/agent-control-panel.md)

### M6 · Evals & Guardrails
- **Eval stack** — [`06-evals/eval-stack.md`](06-evals/eval-stack.md)
- **Human evaluation rubric** — [`06-evals/human-rubric.md`](06-evals/human-rubric.md)

---

## PM Execution Plan

### Where Juno is today
Pre-pilot and specification-complete. The system prompt, strategy, PRD, user flow, trust-gap mitigations, agent spec and eval stack are defined and consistent with each other. The Lovable prototype proves the shape of the workflow (raw evidence → tagged insights → Opportunity Brief), but its output is still canned: it returns the same cards whatever transcript is pasted. Closing that gap is the first job.

### What ships next (next 2 sprints)
**Sprint 1 · Make the output real.** Wire the prototype to a real model running the M1 system prompt. Add the M3 verification gate (every insight cites a source ID and a verbatim quote found in the input), click-through from each insight to its source span, and Edit / Dismiss / Re-rank on every card. Seed the 150-thread golden set.

**Sprint 2 · Shadow pilot.** Run Juno alongside PMs with no roadmap writes. Grade 40 runs a week against `06-evals/human-rubric.md`, including every hand-off case, and log every override as a correction signal. Make the go / no-go call against the red lines below.

### What I watch (dashboards)
- **Value:** thumbs-up rate, regenerate rate, and time to turn a week of evidence into a brief (target 3 hours → 45 minutes).
- **Grounding:** citation-check pass rate and the share of briefs with at least 2 sources per item.
- **Trust:** confidence distribution, low-confidence hand-off rate, and PM override rate.
- **Quality:** weekly human-eval scores and grader disagreement.
- **Operations:** p95 latency, cost per run, and tool-failure aborts.

### Red lines (what blocks shipping — numbers, not feelings)
- Any citation-check failure or any PII leak blocks release.
- Any Safety score of 1 in human eval blocks release.
- Human-eval mean below 4.2/5 on accuracy + safety fails the week.
- Golden-set accuracy below 92% blocks the PR.
- Any output that ranks churn risk without the ARR sheet, or drafts customer-facing comms, blocks release.
- Thumbs-up below 75% in the pilot pauses expansion.
- p95 latency above 10s or cost above $0.08 per run needs a fix before scaling.

### Governance
- **Compliance:** Juno reads no CRM, ARR, contract or billing data, never persists PII or customer contracts, and routes anything touching contracts, legal or pricing to a human PM.
- **Safety:** Juno drafts and never ships. Roadmap writes need PM confirmation, sends are blocked in V1, and below 75% confidence the PM decides.
- **Reliability:** failures stop the run instead of guessing: 6-step ceiling, 60s timeout, abort after 3 consecutive tool failures, and "no strategy source available" instead of a cached copy.
- **Reputation:** every claim is traceable to a source ID, inference is labelled as inference, single-source items carry NEEDS CLARIFICATION, and nothing is attributed to a named customer unless the name is in the artefact.

---

## Build Insights

- **Friction point.** My Lovable prototype looked finished, but its output was canned: whatever transcript I pasted, it returned the same four cards. Making something look real was easy; making its output real is the actual work.
- **Key learning.** Decide what the AI cannot do before deciding what it can. Juno's limits (no ARR access, no customer-facing comms, no brief from a single source) shaped every later module more than its features did.
- **Aha moment.** My job as a PM shifts from writing specs to setting limits. The thresholds, stop lines and hand-offs are the real product decisions; the model fills in the rest.

---

## Repo structure

```
juno-pm/
├── README.md                          ← this dashboard + pitch
├── pitch.html                         ← final presentation (Final Project Deliverables Builder)
├── 01-prompting/
│   ├── system-prompt.md               ← M1: Juno's system prompt
│   ├── lovable-prototype.md           ← M1: prototype link + debrief
│   └── prototype.md                   ← M1: original prototype notes
├── 02-strategy/
│   ├── decision-matrix.md             ← M2: build / buy / fine-tune call
│   └── strategy-one-pager.md          ← M2: AI strategy one-pager
├── 03-rag-prd/
│   └── prd.md                         ← M3: AI PRD with retrieval requirements
├── 04-ai-ux/
│   ├── user-flow.md                   ← M4: AI-native user flow
│   ├── user-flow.png                  ← M4: flow diagram
│   └── trust-gaps.md                  ← M4: trust-gap mitigations
├── 05-agentic-workflows/
│   ├── awspec.md                      ← M5: Agent Workflow Spec
│   ├── agent-control-panel.md         ← M5: Agent Control Panel
│   └── Juno Agent.json                ← M5: Langflow starter
└── 06-evals/
    ├── eval-stack.md                  ← M6: layered eval stack
    └── human-rubric.md                ← M6: human evaluation rubric
```

---

_Certification submission — AI Product Management Certification._
