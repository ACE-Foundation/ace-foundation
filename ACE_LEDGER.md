# ACE‑LEDGER v1.0.0  
Formal Ledger Model for ACE‑Tech

## 1. Purpose and Scope

The ACE Ledger Model defines how ACE‑Tech stores, orders, validates, and reconstructs all institutional state.  
The ledger is the **single source of truth** for:

- certificate ownership  
- certificate retirement  
- account balances  
- permissions  
- identity metadata  
- ACE‑GRADE  
- event history  

The ledger is append‑only, hash‑chained, and fully deterministic.  
All system state must be derivable solely from the ledger.

This document describes the **formal ledger logic**.  
Event semantics are defined in ACE‑EVENT.md.

---

## 2. Ledger Principles

### 2.1 Append‑Only  
No event may be modified or deleted.  
Corrections are made by appending new events.

### 2.2 Hash‑Chained  
Each event contains the hash of the previous event.  
This ensures tamper‑evidence and chronological integrity.

### 2.3 Deterministic Replay  
Given the event stream, the ledger must be able to reconstruct:

- certificate state  
- ownership  
- balances  
- permissions  
- rating  
- identity metadata  

…with no ambiguity.

### 2.4 Event‑Driven  
The ledger stores **events**, not objects.  
Certificates, accounts, and ratings are **derived views**.

### 2.5 Domain‑Agnostic  
The ledger does not embed domain logic.  
Domain calculations occur in ACE‑ENGINE and are referenced via hashes.

### 2.6 Institutional Blockchain Architecture

The ACE ledger is an institutional blockchain.  
It uses the architectural principles of blockchain technology—append‑only storage, hash‑chaining, and deterministic replay—but operates in a permissioned, regulated environment.

Key characteristics:

- **Permissioned**: Only authorized entities may submit events.  
- **Institutional**: Events represent legally relevant actions (creation, trading, retirement, registration).  
- **Non‑speculative**: The ledger does not store tokens, balances, or cryptocurrency.  
- **Event‑Driven**: The ledger records institutional events, not financial transactions.  
- **Deterministic**: All system state is derived from the event stream.  
- **Tamper‑Evident**: Hash‑chaining ensures integrity and auditability.  

The ACE ledger is therefore a blockchain in structure and guarantees,  
but not a public or permissionless chain.  
It is designed for regulatory compliance, auditability, and long‑term institutional trust.

---

## 3. Ledger Structure

The ledger is an ordered sequence of events:

```
[ Event_0, Event_1, Event_2, ... Event_N ]
```

Each event contains:

- event_type  
- event_payload  
- timestamp  
- previous_event_hash  
- event_hash  
- ledger_index  

The ledger_index is the canonical ordering.

---

## 4. Event Validation

Before an event is written to the ledger, ACE‑Tech performs validation:

### 4.1 Structural Validation  
- event_type is valid  
- required fields are present  
- payload schema matches event type  

### 4.2 Referential Validation  
- referenced certificate IDs exist  
- referenced entity IDs exist  
- referenced calculation hashes exist  

### 4.3 Permission Validation  
- seller owns certificate (TRADING‑TX)  
- entity has permission to hold certificates  
- entity has permission to retire certificates  

### 4.4 Engine Validation (Annual Only)  
For CREATION‑TX and REDEMPTION‑TX:

- event references a valid ACE‑ENGINE calculation  
- calculation hash matches MRV input hash  
- calculation is within method version constraints  

---

## 5. Ledger Write Logic

All events are written using the same procedure:

```
function write_event_to_ledger(event):
    validate(event)
    event.previous_event_hash = hash(last_event)
    event.event_hash = hash(event)
    append(event)
```

This ensures:

- immutability  
- hash‑chain integrity  
- deterministic ordering  

---

## 6. Ledger State Reconstruction

Ledger state is not stored directly.  
It is reconstructed by replaying events in order.

### 6.1 Certificate Reconstruction

```
function build_certificate_json(event_stream):
    apply CREATION‑TX
    apply TRADING‑TX
    apply REDEMPTION‑TX
    return certificate_view
```

### 6.2 Account State Reconstruction

```
function build_account_state(entity_id, event_stream):
    start with empty state
    apply REGISTRATION events in order
    return final_state
```

### 6.3 ACE‑GRADE Reconstruction

ACE‑GRADE is stored in REGISTRATION events.  
Reconstruction is trivial:

```
ACE_GRADE = last(REGISTRATION.ACE_GRADE)
```

---

## 7. Continuous Ledger vs Annual Book‑Closing

The ledger operates continuously.  
Events are written whenever institutional changes occur.

### 7.1 Continuous (Intra‑Year)

Triggered by:

- TRADING‑TX  
- identity updates  
- permission changes  

Sequence:

```
TRADING‑TX → REGISTRATION → ledger write
```

ACE‑ENGINE is **not** invoked.  
ACE‑GRADE does **not** change.

### 7.2 Annual (Book‑Closing)

Triggered once per reporting year:

```
MRV → ACE‑ENGINE → (CREATION‑TX or REDEMPTION‑TX) → REGISTRATION → ledger write
```

This is the only time when:

- ACE‑GRADE is updated  
- CREATION‑TX may occur  
- REDEMPTION‑TX may occur  

---

## 8. Certificate Lifecycle in the Ledger

The ledger stores the certificate lifecycle as:

```
CREATION‑TX → TRADING‑TX → TRADING‑TX → ... → REDEMPTION‑TX
```

ACE‑CERT is a **derived view**, not a stored object.

---

## 9. Ledger Ordering and Indexing

### 9.1 Ordering  
Events are ordered by:

1. ledger_index  
2. timestamp  
3. hash chain  

### 9.2 Indexing  
The ledger maintains indexes for:

- certificate_id → event_stream  
- entity_id → registration_stream  
- method_version → creation_stream  

These indexes accelerate reconstruction but are not authoritative.  
The event stream is the source of truth.

---

## 10. Ledger Guarantees

The ACE ledger guarantees:

- **immutability** (append‑only)  
- **integrity** (hash‑chain)  
- **determinism** (replayable state)  
- **auditability** (full history)  
- **domain separation** (ENGINE vs EVENTS)  
- **institutional correctness** (REGISTRATION as root state)  

---

## 11. Summary

The ACE Ledger Model defines how ACE‑Tech stores and reconstructs all institutional state.  
It ensures that:

- certificates are deterministic views  
- ownership is transparent and auditable  
- retirement is final  
- ACE‑GRADE is reproducible  
- ledger state is always derivable  
- the system is tamper‑evident and regulator‑ready  

This model forms the foundation for the operational ACE‑Tech prototype and all future implementations.
