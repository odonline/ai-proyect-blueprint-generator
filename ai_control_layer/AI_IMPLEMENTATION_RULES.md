# AI Implementation Rules

## Purpose

This document defines the rules that any AI-assisted implementation must follow when generating or modifying code for this system.

The objective is to prevent architectural drift, domain corruption, or unauthorized changes to the core business logic.

These rules apply to:

- AI coding agents
- LLM-assisted development
- Automated code generation pipelines

---

# Strict Rules

The AI **must NOT modify or invent**:

- Domain entities
- State machines
- ENUM values
- Database schema
- Financial logic
- Actor model
- Event definitions

These elements are defined in the following documents:

- DOMAIN_SOURCE_OF_TRUTH.md
- STATE_MACHINE_SPEC.md
- JSON_SCHEMA.json
- BACKEND_IMPLEMENTATION_CONTRACT.md

They are considered **immutable system contracts**.

---

# Allowed Implementation Scope

The AI **may implement or modify**:

- Controllers
- Services
- Repositories
- API routes
- DTO mappings
- Unit tests
- Integration tests

The AI may also:

- Add missing validation logic
- Implement service orchestration
- Implement persistence layer access

---

# Prohibited Behaviors

The AI must not:

- Invent new entities
- Add new states
- Change transition rules
- Modify payment logic
- Introduce new event types
- Modify database constraints

If a requirement appears missing, the AI must:

1. Flag it
2. Stop implementation
3. Request clarification

---

# Conflict Resolution

If the AI encounters contradictions between documents:

Priority order:

1. DOMAIN_SOURCE_OF_TRUTH.md
2. STATE_MACHINE_SPEC.md
3. BACKEND_IMPLEMENTATION_CONTRACT.md
4. API specification
5. Implementation code

The higher document always overrides the lower one.