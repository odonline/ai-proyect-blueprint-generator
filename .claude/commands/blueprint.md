# /blueprint Command

You are executing the **Blueprint Builder Agent**.

## Step 1 — Read the agent instructions

Read the full file: `BLUEPRINT_BUILDER_AGENT.md`

This file contains the complete 18-stage process you must follow.

## Step 2 — Detect and persist user language

Check `Specs/.state.md` for the `language` field.

**If `language` is already set (not null):**
- Use that language for all questions, document content, summaries, and feedback.

**If `language` is null (first run):**
- Detect the language from the user's current message.
- If still ambiguous, ask: "What language should the spec documents be generated in?"
- Once determined, write the language code (e.g. `es`, `en`, `pt`) to the `language` field in `Specs/.state.md`.

The command syntax (`/blueprint`, stage names, file names) always stays in English.

## Step 3 — Detect current state



Check if `Specs/.state.md` exists.

**If it does NOT exist:**
- This is a fresh project
- Start at Stage 1
- Create `Specs/.state.md` with the following content:

```
current_stage: 1
completed_stages: []
last_updated: <today's date>
skipped_to: null
language: <detected language code>
```

**If it DOES exist:**
- Read `Specs/.state.md`
- Read `current_stage` value
- Resume from that stage

## Step 4 — Execute the current stage

Follow the exact instructions for the detected stage from `BLUEPRINT_BUILDER_AGENT.md`.

This means:
1. Ask the structured questions for this stage
2. Wait for user answers
3. Summarize the answers
4. Detect inconsistencies with previously generated documents in `Specs/`
5. Suggest improvements
6. Generate the corresponding document and save it to `Specs/`
7. Ask user confirmation before marking stage as complete

## Step 5 — Update state on completion

After the user confirms the stage is complete:

Update `Specs/.state.md`:
- Increment `current_stage` by 1
- Add the completed stage number to `completed_stages`
- Update `last_updated`

## Step 6 — Confirm and stop

After updating the state, inform the user:

```
✅ Stage N complete — [Document name] saved to Specs/
➡️  Run /blueprint to continue to Stage N+1
```

Do NOT automatically continue to the next stage. Wait for the user to run `/blueprint` again.

## Important Rules

- Never write implementation code
- Never skip stages
- Always check `Specs/` for previously generated documents before starting a stage (for consistency validation)
- If Stage 18 is complete, inform the user to run `/spec-audit`
