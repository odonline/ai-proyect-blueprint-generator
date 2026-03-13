# AI Forbidden Changes

## Purpose

This document lists changes that the AI must never perform automatically.

These rules protect system integrity and prevent domain corruption.

---

# Domain Layer

The AI must NOT:

- Add or remove entities
- Change entity attributes
- Modify entity relationships
- Change entity cardinality

---

# State Machines

The AI must NOT:

- Add new states
- Remove existing states
- Change transition conditions
- Change terminal states

State machines are defined in:

STATE_MACHINE_SPEC.md

---

# Database Schema

The AI must NOT:

- Add new tables
- Remove tables
- Modify primary keys
- Modify foreign keys
- Modify unique constraints
- Change ENUM values

---

# Payment Logic

The AI must NOT:

- Change PaymentEvent types
- Modify payment flows
- Change refund logic
- Change currency handling

Payment events are strictly defined.

---

# Event Model

The AI must NOT:

- Add new domain events
- Modify event payload structure
- Change event triggering logic

Events must follow the existing contract.

---

# Violations

If the AI detects that implementation requires any forbidden change:

1. Stop implementation
2. Flag the issue
3. Request human review