# Generated-skill template (§0–§7)

Every skill Automation Builder produces follows this shape. **§0, §3's preview-before-acting,
and §7 are mandatory** and identical in spirit across all skills; **§1–§6 are filled** from
`current-state.md` and `automation-plan.md`. Keep the shipped skill lean — only what the agent needs to run, no
extra docs.

- **Frontmatter (name + description).** This is what makes the skill *trigger*, so it matters more than anything in the body. `name`: kebab-case, lowercase letters, numbers, and hyphens only, 64 characters or fewer, matching the folder. `description`: the only thing Claude reads to decide whether to run the skill, so put **what it does and when to use it** here, naming the real phrases and moments the owner would say it. Lean slightly pushy, because skills tend to under-trigger: spell out "use this whenever the owner mentions X, Y, or Z, even if they don't ask for it by name." Keep it under 1024 characters with no `<` or `>`.
- **§0 — Intake.** Before doing anything, interview the client for this run's variables.
  Always confirm the must-have inputs (recorded in the plan) are captured; beyond those, use
  full intelligence to ask whatever this run needs. End with: *"Anything different about this
  run I should know?"* Don't proceed until intake is complete, and confirm it back.
- **§1 — What this does.** One plain-language paragraph stating the goal.
- **§2 — The procedure.** The automated steps in order. Each step: what Claude does, which
  connection/tool it uses, and what it produces. For any step that is deterministic and repetitive (the same transform, the same calculation, a fixed templated output), write it once as a small script in `scripts/` and have the skill call it instead of describing it in prose. Scripts run the same way every time; prose gets re-improvised, and that is where errors creep in.
- **§3 — Human checkpoints.** Two kinds, both stop and wait for the client's call: (a) the
  **judgment moments** (from anchor A4) where the call is the client's gut, not a rule; and
  (b) a **preview before any irreversible action** — before the skill sends, posts, pays, or
  changes a system the client can't easily undo, show exactly what it's about to do and wait
  for a go-ahead. Keep the preview on, especially for the first runs.
- **§4 — The rules / voice.** The standards (from anchor A6) baked in so output is
  authentically theirs.
- **§5 — Output & destination.** What "done" produces and exactly where it lands.
- **§6 — Connections needed.** The MCP servers / APIs / accounts the skill requires, plus any
  steps the build marked blocked or human-in-the-loop. If a connection is missing, follow the
  §7 guardrail — tell them in plain language what to connect and why; never dump a raw error.
- **§7 — Non-coder guardrail.** Include this in every skill: *"The person running this is smart
  but not a coder. Never surface raw errors, stack traces, or jargon. If something breaks,
  explain what it means for them and what they can do — in plain English. And when you're
  unsure — ambiguous input, an unexpected case, or a call the plan didn't cover — stop and ask
  in plain language rather than guess; a pause is cheap, a confident mistake in their business
  is not."*

## Writing the generated skill well
- **Keep it lean (progressive disclosure).** The body carries the common path. Push long detail into `references/` files the skill reads only when needed, and put deterministic work in `scripts/`. Aim to keep the body well under ~500 lines so the automation stays fast and cheap to run.
- **Explain the why, not a wall of MUSTs.** Tell the model *why* a step matters instead of stacking ALL-CAPS rules. Reasoning generalizes; rigid rules break on the first case you did not foresee.
- **Do not overfit to the examples.** The owner gave you a few sample runs, but the skill has to work on next month's data too. Write each step as the general pattern, not as a patch for those specific examples.
