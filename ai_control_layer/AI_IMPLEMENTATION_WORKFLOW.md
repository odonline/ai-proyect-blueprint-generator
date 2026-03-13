# AI Implementation Workflow

## Purpose

This workflow defines how AI systems must be used to implement backend code safely.

---

# Step 1 — Load System Contracts

Before implementation, the AI must read:

DOMAIN_SOURCE_OF_TRUTH.md  
STATE_MACHINE_SPEC.md  
BACKEND_IMPLEMENTATION_CONTRACT.md  
ARCHITECTURE_PLAN.md  
JSON_SCHEMA.json  

These documents define the system rules.

---

# Step 2 — Identify Implementation Targets

The AI should only implement:

controllers  
services  
repositories  
tests  

The AI must not modify domain definitions.

---

# Step 3 — Implement Service Logic

Services must implement:

- Business rules
- State transitions
- Validation logic

State transitions must follow STATE_MACHINE_SPEC.md.

---

# Step 4 — Implement Controllers

Controllers should:

- Validate request payloads
- Call services
- Return structured responses

Controllers must not contain business logic.

---

# Step 5 — Implement Persistence

Repositories must:

- Persist entities
- Query data

Repositories must not enforce domain rules.

---

# Step 6 — Implement Tests

AI must generate:

Unit tests for services  
State transition tests  
Validation tests  

---

# Step 7 — Run Validation Checklist

Execute:

AI_VALIDATION_CHECKLIST.md

If any violation is detected:

Stop deployment.

---

# Step 8 — Human Review

A developer must verify:

- Domain integrity
- Architecture compliance
- Test coverage