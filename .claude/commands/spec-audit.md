# /spec-audit Command

You are executing the **Spec Auditor Agent**.

## Step 1 — Read the auditor instructions

Read the full file: `SPEC_AUDITOR_AGENT.md`

This file defines all validation rules you must apply.

## Step 2 — Verify prerequisites

Check that the following documents exist in `Specs/`:

- DOMAIN_SOURCE_OF_TRUTH.md
- ENTITY_DEFINITIONS.md
- STATE_MACHINE_SPEC.md
- EVENT_MATRIX.md
- DB_SCHEMA.sql
- ARCHITECTURE_PLAN.md
- SERVICE_LAYER_SPEC.md
- BACKEND_IMPLEMENTATION_CONTRACT.md

If any are missing, list them and respond:

```
❌ Audit cannot proceed. The following required documents are missing:
- <list missing files>

Complete the blueprint stages first by running /blueprint.
```

And stop.

## Step 3 — Read all documents

Read every document listed in Step 2 in full.

## Step 4 — Run all validation rules

Apply every validation rule defined in `SPEC_AUDITOR_AGENT.md`:

- Domain Consistency
- Entity Consistency
- State Machine Validation
- Event Validation
- Database Validation
- Architecture Validation
- Backend Contract Validation

## Step 5 — Generate the audit report

Save the result to `Specs/SPEC_AUDIT_REPORT.md`.

The report must follow this structure:

```markdown
# Spec Audit Report

Generated: <date>

## Summary
- Total issues found: N
- Blocking issues: N
- Warnings: N

## ✅ Passed Validations
<list what passed>

## ❌ Blocking Issues
<contradictions, missing definitions, invalid transitions, schema mismatches>

## ⚠️ Warnings
<non-blocking inconsistencies worth reviewing>

## Recommendations
<prioritized list of fixes>
```

## Step 6 — Report to user

After saving the report, display the summary section and inform the user:

```
📄 Full report saved to: Specs/SPEC_AUDIT_REPORT.md

<if blocking issues>
❌ Fix blocking issues before proceeding to implementation.

<if no blocking issues>
✅ Spec pack is valid. Ready for implementation.
```
