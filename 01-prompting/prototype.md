# Prototype · Juno

## Prototype link

https://evidence-lane.lovable.app

## What it demonstrates

Juno PM as a single surface where messy user evidence becomes a PRD: paste raw transcripts on the left, hit Process Transcript, get tagged insights in the middle and a rendered Opportunity Brief on the right. It's a proof of the shape of the workflow, not the intelligence behind it.

## Debrief

- **What worked:** The three-column read is instantly legible: raw → structured → drafted. Priority/sentiment tags plus the pulled quote under each insight make the evidence trail feel real, and the Brief reads like something you'd actually paste into a doc. The dark Linear-style treatment keeps a dense screen calm, and the button sitting between columns 1 and 2 makes the causality obvious without a nav bar.
- **What broke / felt like a toy:** The output is canned: your Sarah transcript (blue nav bar too bright, Export to CSV spinning then crashing, wants dark mode) produced none of those insights — it returned the same four hardcoded cards every time. The 1.5s spinner is theatre. Nothing is editable, savable, or exportable; insights don't link back to the source text; there's no handling of long or multi-source pastes, no empty/error states beyond the placeholder, and the middle column doesn't scroll independently under real volume.
- **What I'd change next pass:** Wire it to a real model so insights are genuinely extracted, with clustering across multiple inputs and a confidence signal. Make each insight click back to the highlighted span in the transcript, let insights be edited/dismissed/reordered, and have the PRD regenerate from the surviving set. Add multi-source ingestion (label each paste as interview/ticket/email), streaming output instead of a fake delay, and a Copy/Export to Markdown action on the Brief.
