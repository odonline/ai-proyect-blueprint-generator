# AI Allowed Files

## Purpose

This document defines which files the AI is allowed to create or modify during implementation.

The goal is to prevent accidental modification of domain contracts.

---

# Allowed Directories

The AI may modify files inside:

controllers/
services/
repositories/
routes/
tests/
integration_tests/
api/

---

# Conditionally Allowed

DTO and request/response mapping files:

dto/
mappers/

Only if they do not modify domain definitions.

---

# Forbidden Directories

The AI must NOT modify files inside:

domain/
state_machines/
schema/
contracts/
architecture/
specs/

These directories contain the system contracts.

---

# Domain Definition Lock

The following files are **read-only**:

DOMAIN_SOURCE_OF_TRUTH.md  
STATE_MACHINE_SPEC.md  
JSON_SCHEMA.json  
OPENAPI.yaml  
BACKEND_IMPLEMENTATION_CONTRACT.md

Any modification to these requires human approval.