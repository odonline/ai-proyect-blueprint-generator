# /blueprint-status Command

You are displaying the current status of the Blueprint process.

## Step 1 — Read state

Read `Specs/.state.md`.

If it does not exist, respond:
```
📋 No blueprint started yet.
Run /blueprint to begin Stage 1.
```
And stop.

## Step 2 — Read Specs folder

List all files currently present in the `Specs/` directory.

## Step 3 — Display status

Display a status table like this:

```
📊 Blueprint Status
═══════════════════════════════════════

Current Stage : <current_stage> / 18
Last Updated  : <last_updated>

Stage Progress:
───────────────────────────────────────
Stage  1 — Problem Definition          [✅ / ⏳ / ⬜]
Stage  2 — Market Scope               [✅ / ⏳ / ⬜]
Stage  3 — Value Proposition          [✅ / ⏳ / ⬜]
Stage  4 — Product Overview           [✅ / ⏳ / ⬜]
Stage  5 — MVP Scope                  [✅ / ⏳ / ⬜]
Stage  6 — User Flows                 [✅ / ⏳ / ⬜]
Stage  7 — Functional Requirements    [✅ / ⏳ / ⬜]
Stage  8 — Domain Model               [✅ / ⏳ / ⬜]
Stage  9 — Entity Definitions         [✅ / ⏳ / ⬜]
Stage 10 — State Machines             [✅ / ⏳ / ⬜]
Stage 11 — Event Matrix               [✅ / ⏳ / ⬜]
Stage 12 — Architecture Plan          [✅ / ⏳ / ⬜]
Stage 13 — Service Layer Spec         [✅ / ⏳ / ⬜]
Stage 14 — Database Schema            [✅ / ⏳ / ⬜]
Stage 15 — Backend Contract           [✅ / ⏳ / ⬜]
Stage 16 — Testing Strategy           [✅ / ⏳ / ⬜]
Stage 17 — Concurrency Rules          [✅ / ⏳ / ⬜]
Stage 18 — Implementation Pack        [✅ / ⏳ / ⬜]
───────────────────────────────────────
✅ = completed  ⏳ = current  ⬜ = pending

Generated Documents in Specs/:
<list all files found in Specs/ directory>

Next Step:
<if stages remain>  → Run /blueprint to continue
<if all complete>   → Run /spec-audit to validate
```

Use `completed_stages` from `.state.md` to determine ✅ vs ⬜.
The `current_stage` gets ⏳.
