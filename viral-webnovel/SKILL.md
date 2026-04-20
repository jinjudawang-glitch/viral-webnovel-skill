---
name: viral-webnovel
description: Serialized Chinese webnovel creation and continuation workflow for high-click, high-retention Fanqie/Qimao-style fiction. Use when Codex needs to generate or improve viral webnovel premises, titles, synopses, story bibles, xuanhuan cultivation outlines, first-10-chapter trial reads, 5-chapter drafting rounds, rolling memory packages, reader-retention diagnostics, branch decisions, or humanized rewrites that reduce AI-style explanatory prose.
---

# viral-webnovel

Use this skill as a serialized fiction director, not as a one-shot novel generator. The V1 default is Chinese xuanhuan cultivation fiction for an 80-120 chapter short-to-mid serial: waste-to-power opening, abnormal cheat, sect pressure, face-slapping, upgrade, treasure conflict, map escalation, and hard chapter hooks.

Default to Chinese output unless the user asks otherwise.

## Operating Rule

Push the work through controllable stages:

1. Find or invent stronger premises.
2. Ask the user to choose one premise before expanding it.
3. Build the story bible and opening structure.
4. Ask the user to confirm the skeleton before drafting.
5. Draft only 5 chapters per round.
6. Compress memory, diagnose retention, and offer branches after each round.
7. Ask the user to choose the next branch before continuing.
8. Run humanization as a separate pass when prose quality matters.

Do not attempt to write a full 80-120 chapter novel in one response. If the user asks for a full book, create the bible, front-30 outline, front-10 trial plan, and first 5-chapter round, then prepare the next-round context package.

## Mode Selection

- `trend-scan`: Load `references/platform-patterns.md`. Use when the user asks what is hot, what sells, what readers want, or what to avoid. If the user asks for latest or current trends, browse and cite sources; otherwise state that built-in platform patterns are being used.
- `idea-pool`: Load `references/platform-patterns.md` and `references/idea-scoring.md`. Generate 20 premise candidates and stop for Manual Checkpoint A.
- `bible`: Load `references/story-bible-template.md`, plus `references/idea-scoring.md` if the selected premise still feels generic.
- `outline-30`: Load `references/outline-structure.md` and create the front-30-chapter structure. Stop for Manual Checkpoint B before drafting.
- `trial-10`: Load `references/outline-structure.md` and create a detailed first-10-chapter trial-read plan.
- `draft-5`: Load `references/chapter-template.md`, `references/memory-system.md`, and the latest context package. Write 5 chapters, not more, unless the user explicitly asks for fewer. Each drafted chapter must be at least 1000 Chinese characters unless the user explicitly requests a shorter sample.
- `compress`: Load `references/memory-system.md` and create the next-round context package.
- `diagnose`: Load `references/diagnose-loop.md` and produce reader feedback simulation, failure checks, and three branch choices. Stop for Manual Checkpoint C.
- `humanize`: Load `references/rewrite-humanization.md`. Rewrite prose to remove AI texture while preserving plot facts.

## Manual Checkpoints

Manual Checkpoint A: after `idea-pool`, the user selects one main premise and at most one backup. Do not build a full bible for all 20 candidates.

Manual Checkpoint B: after `bible`, `outline-30`, or `trial-10`, the user confirms or revises the story skeleton before drafting.

Manual Checkpoint C: after each `draft-5` plus `diagnose`, the user chooses one of three next branches before the following drafting round.

## Core Constraints

Implement "颠" as story logic, not decorative style:

- Define the world's absurd foundation.
- Give the protagonist a misread of reality that others do not share.
- Give major antagonists a personal obsession, not only stupidity.
- Make upgrades stranger, not only stronger.
- Make shocks surprising but explainable in hindsight.

Retention requirements:

- Start each chapter with pressure or conflict within the first 300 Chinese characters.
- Give the protagonist at least one active choice per chapter.
- Deliver at least one payoff per chapter.
- End each chapter with a concrete unresolved threat, secret, reward, or decision.
- Track repeated face-slapping, reversal, and humiliation patterns so the next round mutates them.

Prose requirements:

- Prefer scene action over explanation.
- Prefer short, sharp dialogue over summary.
- Let the protagonist be selfish, stubborn, paranoid, or willing to make dirty choices when the premise supports it.
- Avoid preaching, forced moral elevation, forced full closure, and generic inspirational endings.

Safety and originality:

- Do not imitate a named living author or specific copyrighted book.
- Do not directly rewrite or continue a copyrighted story unless the user owns it or provides original material.
- Avoid explicit sexual content, sexual content involving minors, real-world targeted abuse, real political incitement, or graphic gore beyond platform-style action.
- If a request asks for "latest trends" or current platform rankings, verify with browsing rather than inventing current data.

## Standard Round Output

For a 5-chapter production round, output:

1. Round target.
2. Five chapter texts, each at least 1000 Chinese characters unless the user explicitly requested a shorter sample.
3. One-line payoff note for each chapter.
4. New hooks.
5. Hooks paid off.
6. Active ledger update.
7. Cold storage update.
8. Reader-retention diagnosis.
9. Three next-branch choices.

If the user asks for final polish, add a separate humanized final version after the diagnostic pass.
