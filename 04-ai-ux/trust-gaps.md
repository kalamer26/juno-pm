# Trust-Gap Mitigations · Juno

> Module 4 · AI-Native UX. Trust gaps found in my own Lovable prototype (see `01-prompting/lovable-prototype.md` debrief), and how each is mitigated in the design.

## Trust gaps

| Gap | Where it shows up | User cost | Mitigation |
|---|---|---|---|
| Hallucination | The prototype returns the same four hardcoded insight cards whatever transcript is pasted. My Sarah transcript (CSV crash, bright nav bar, dark mode) produced none of its real problems. | High. A PM who notices once stops trusting every card, and one who doesn't notice ships a brief built on insights nobody said. | Wire to a real model with the M1 system prompt. Every insight must cite a source ID and a verbatim quote of max 25 words; the M3 verification gate rejects any card whose quote is not found in the input. Single-source insights carry NEEDS CLARIFICATION. |
| Opacity (no "why") | Insights do not link back to the transcript, so the PM cannot see which sentence produced a card or why it got its priority. | Medium. The PM re-reads the whole transcript to check each card, which removes the time saving. | Clicking an insight highlights the source span in the Raw Input column. Each card shows its source ID, mention count and the strategic pillar that drove its rank. |
| No user control | Nothing is editable, dismissable or reorderable, and the brief cannot be regenerated from the surviving set. | Medium. The PM either accepts Juno's output as-is or abandons the tool. | Every card gets Edit / Dismiss / Re-rank (the M4 Manual Override). The Opportunity Brief regenerates from the cards the PM kept, and each override is logged as a correction signal. |
| Intelligence tax | The 1.5s spinner is fake, and long or multi-source pastes are not handled. | Low to medium. The wait feels like theatre, and real volume would break the layout. | Replace the fake delay with streamed output and the M4 breadcrumb messages. Label each paste as interview / ticket / email so Juno can merge across sources. Target p95 under 10s (M3). |

## Highest-priority fix

**Hallucination.** The canned output is the one gap that makes everything else pointless: a traceable, editable card is worthless if the card was never in the evidence. Close it first by wiring the real model behind the M3 verbatim-quote check, then fix opacity so the PM can verify each card in one click.
