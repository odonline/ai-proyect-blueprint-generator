# /blueprint-jump Command

Usage: `/blueprint-jump <stage_number>`

Example: `/blueprint-jump 5`

You are executing a **stage jump** in the Blueprint Builder process.

## Step 1 — Validate the argument

The user provided: `$ARGUMENTS`

Extract the stage number from the argument.

Valid stages are 1 through 18.

If the argument is missing or invalid, respond:
```
❌ Invalid usage. Provide a stage number between 1 and 18.
Example: /blueprint-jump 5
```
And stop.

## Step 2 — Warn the user

Before jumping, display:

```
⚠️  You are jumping to Stage <N>.
This will override the current stage tracker.
Any stages between the current stage and Stage <N> will be marked as skipped.
Consistency cannot be guaranteed if prerequisite stages were not completed.

Type CONFIRM to proceed or anything else to cancel.
```

Wait for user confirmation.

## Step 3 — Update state

If the user confirms, update `Specs/.state.md`:

```
current_stage: <N>
completed_stages: <keep existing>
skipped_to: <N>
last_updated: <today's date>
```

## Step 4 — Execute the stage

Read `BLUEPRINT_BUILDER_AGENT.md` and execute Stage N following the same rules as the `/blueprint` command.
