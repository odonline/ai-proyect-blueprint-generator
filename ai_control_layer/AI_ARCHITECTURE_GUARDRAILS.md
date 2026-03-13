# AI Architecture Guardrails

## Purpose

This document defines the architectural boundaries that AI-generated code must respect.

These guardrails prevent architecture degradation.

---

# Architecture Layers

The system must follow this layered architecture:

Controller Layer  
Service Layer  
Repository Layer  
Database Layer

Dependencies must flow downward only.

---

# Controller Layer

Controllers may:

- Validate input
- Call services
- Return responses

Controllers must NOT:

- Access the database directly
- Implement business logic
- Modify domain state

---

# Service Layer

Services implement:

- Business rules
- State transitions
- Domain orchestration

Services must:

- Validate state transitions
- Enforce domain constraints

---

# Repository Layer

Repositories are responsible for:

- Database access
- Persistence operations

Repositories must NOT:

- Implement business rules
- Modify state machines

---

# Domain Layer

The domain layer contains:

- Entities
- State machines
- Domain invariants

This layer is **read-only for AI implementations**.

---

# Scheduler Layer

Background jobs may perform:

- Expiration logic
- Retry logic
- Notifications

Schedulers must trigger events but not bypass state machines.

---

# Event System

All state changes must occur via events.

Direct state modification is forbidden.

Example:

Incorrect:

jobRequest.status = "PLACED"

Correct:

emit JobRequestPlaced event