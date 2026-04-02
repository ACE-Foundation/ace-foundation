# ACE‑EVENT v1.0.0  
Conceptual Event Model for ACE‑Tech

## 1. Purpose and Scope

The ACE Event Model defines the four fundamental event types used in ACE‑Tech:

- **CREATION‑TX**  
- **TRADING‑TX**  
- **REDEMPTION‑TX**  
- **REGISTRATION**

These events form the institutional backbone of the ACE ledger.  
All certificate lifecycles, account states, permissions, and identity updates are derived exclusively from event history.

This document describes the **conceptual logic** of each event type.  
Formal schemas, JSON structures, and validation rules are defined in the ACE‑Ledger‑Model (Steg 1).

---

## 2. Event Principles

### 2.1 Append‑Only  
Events are written to the ledger as immutable entries.  
No event may be modified or deleted.

### 2.2 Hash‑Chained  
Each event contains the hash of the previous event, forming a tamper‑evident chain.

### 2.3 Deterministic  
All system state (accounts, balances, certificate ownership, permissions) must be derivable solely from event history.

### 2.4 Domain‑Agnostic  
Events do not embed domain logic.  
Domain‑specific calculations occur in ACE‑ENGINE and are referenced via hashes.

### 2.5 Separation of Concerns  
- **MRV** describes real‑world data.  
- **ENGINE** performs calculations.  
- **EVENTS** record institutional actions.  
- **LEDGER** stores history.  
- **CERT** is a deterministic view derived from events.

---

## 3. Event Types Overview

| Event Type     | Category        | Purpose |
|----------------|-----------------|---------|
| CREATION‑TX    | Transaction     | Creates a new certificate based on ACE‑ENGINE output |
| TRADING‑TX     | Transaction     | Transfers ownership of an existing certificate |
| REDEMPTION‑TX  | Transaction     | Retires a certificate and matches it against positive emissions |
| REGISTRATION   | Institutional   | Updates identity, permissions, rating, and account state |

---

## 4. CREATION‑TX (Transaction Event)

### 4.1 Purpose  
CREATION‑TX initializes a new certificate lifecycle.  
It represents the creation of negative emissions based on ACE‑ENGINE output.

### 4.2 Trigger  
- Annual reporting (MRV submission).  
- ACE‑ENGINE computes negative CO₂e.  
- ACE‑Tech validates the calculation.

### 4.3 Contents (conceptual)
- Certificate ID  
- Calculation result (hash + metadata)  
- MRV input hash  
- Domain and method version  
- Producer identity  
- Timestamp  
- Previous event hash  
- Event hash  

### 4.4 Rules  
- Must always be followed by a **REGISTRATION** event.  
- Must reference a valid ACE‑ENGINE calculation.  
- Must not embed raw MRV data (only hashes + metadata).  
- Initializes certificate ownership to the Producer.

---

## 5. TRADING‑TX (Transaction Event)

### 5.1 Purpose  
TRADING‑TX transfers ownership of an existing certificate from one entity to another.

### 5.2 Trigger  
- Buyer and Seller agree on a trade.  
- Clearing and settlement are completed.  
- ACE‑Tech validates permissions and balances.

### 5.3 Contents (conceptual)
- Certificate ID  
- Seller ACE‑ID  
- Buyer ACE‑ID  
- Settlement metadata  
- Timestamp  
- Previous event hash  
- Event hash  

### 5.4 Rules  
- Does **not** involve ACE‑ENGINE.  
- Requires Seller to own the certificate.  
- Requires Buyer to have permission to hold certificates.  
- Does not change certificate content — only ownership.  
- Must be followed by a **REGISTRATION** event.

---

## 6. REDEMPTION‑TX (Transaction Event)

### 6.1 Purpose  
REDEMPTION‑TX retires a certificate permanently.  
It represents the matching of positive emissions with purchased negative emissions.

### 6.2 Trigger  
- Annual reporting (MRV submission).  
- ACE‑ENGINE determines that positive emissions must be matched.  
- Entity owns ACE‑CERT eligible for retirement.

### 6.3 Contents (conceptual)
- Certificate ID  
- Redeeming entity (ACE‑ID)  
- Positive emissions being matched (optional metadata)  
- Timestamp  
- Previous event hash  
- Event hash  

### 6.4 Rules  
- Must always be followed by a **REGISTRATION** event.  
- Certificate becomes non‑transferable after redemption.  
- Certificate remains reconstructable but is marked as retired.  
- Updates the entity’s account state (balances, rating, etc.).

---

## 7. REGISTRATION (Institutional Event)

### 7.1 Purpose  
REGISTRATION updates the institutional state of an entity.  
It is the root event type for identity, permissions, rating, and account balances.

### 7.2 Trigger  
REGISTRATION occurs after **every** institutional change:

- After CREATION‑TX (annual)  
- After REDEMPTION‑TX (annual)  
- After TRADING‑TX (intra‑year)  
- After identity or permission updates (intra‑year)  
- After annual ACE‑ENGINE calculation (annual)

### 7.3 Contents (conceptual)
- Entity ID  
- Updated rating (ACE‑GRADE)  
- Updated permissions  
- Updated certificate ownership lists (owned, retired)  
- Updated balances (positive/negative emissions)  
- Identity metadata  
- Timestamp  
- Previous event hash  
- Event hash  

### 7.4 Rules  
- REGISTRATION events never go through clearing or settlement.  
- REGISTRATION does not create or modify certificates.  
- REGISTRATION is the **only** event type that contains and updates certificate ownership lists.  
- REGISTRATION ensures that ledger state is always derivable.

---

## 8. Certificate Lifecycle (Derived from Events)

Certificates are **not** stored as standalone objects.  
They are reconstructed deterministically from the event stream associated with a certificate ID.

The certificate lifecycle is driven by **annual reporting**, where ACE‑ENGINE is invoked to process:

- current‑year MRV input  
- historical MRV input  
- certificate ownership (from REGISTRATION state)  
- retired certificates  
- account balances  
- method version  

ACE‑ENGINE produces:

- updated ACE‑GRADE  
- current‑year CO₂e result  
- a flag indicating whether negative emissions require a CREATION‑TX  
- a flag indicating whether positive emissions require a REDEMPTION‑TX  
- a calculation hash  

### 8.1 Lifecycle Events

1. **CREATION‑TX**  
   Generated when ACE‑ENGINE detects negative emissions.  
   Initializes a new certificate and assigns initial ownership.

2. **TRADING‑TX**  
   Updates certificate ownership after clearing and settlement.  
   Does not involve ACE‑ENGINE.

3. **REDEMPTION‑TX**  
   Generated when ACE‑ENGINE determines that positive emissions must be matched  
   *and* the entity owns ACE‑CERT eligible for retirement.  
   Permanently retires the certificate.

4. **REGISTRATION**  
   Updates the institutional state of the entity after CREATION‑TX, REDEMPTION‑TX, or TRADING‑TX.  
   REGISTRATION is the **only** event type that contains and updates certificate ownership lists.

### 8.2 Deterministic Reconstruction

ACE‑CERT is always derived from the event stream.  
The following conceptual functions describe how ACE‑Tech processes events:

- **`build_certificate_json(event_stream)`**  
  Constructs the ACE‑CERT representation from CREATION‑TX and TRADING‑TX events.

- **`retire_certificate_json(event_stream)`**  
  Finalizes the certificate lifecycle after REDEMPTION‑TX.

### 8.3 Continuous Ledger vs Annual Book‑Closing

The ACE ledger operates continuously.  
All institutional changes (trading, permissions, identity updates) generate events that are immediately written to the ledger and followed by a REGISTRATION event.

However, ACE‑ENGINE is invoked **only once per reporting year**.  
This annual cycle functions as a climate “book‑closing”:

1. The entity submits MRV for the reporting year.  
2. ACE‑ENGINE computes the new ACE‑GRADE and CO₂e result.  
3. If negative emissions are detected, a CREATION‑TX is generated.  
4. If positive emissions must be matched, a REDEMPTION‑TX is generated.  
5. A REGISTRATION event finalizes the annual state update.

Intra‑year operations never invoke ACE‑ENGINE and never affect ACE‑GRADE.  
They only update ownership, permissions, and account state through REGISTRATION.

### 8.4 Summary

The certificate lifecycle is therefore:

1. Annual reporting triggers ACE‑ENGINE.  
2. ACE‑ENGINE determines whether CREATION‑TX or REDEMPTION‑TX is required.  
3. TRADING‑TX may occur at any time and does not involve ACE‑ENGINE.  
4. REGISTRATION updates identity, rating, permissions, and certificate ownership.  
5. ACE‑CERT is always reconstructed from events, never stored as a mutable object.

---

## 9. Event Ordering and Determinism

### 9.1 Ordering  
Events are strictly ordered by:

1. Ledger index  
2. Timestamp  
3. Hash chain  

### 9.2 Deterministic Replay  
Given the event stream:

- certificate state  
- ownership  
- balances  
- permissions  
- rating  

…must be exactly reproducible.

---

## 10. Summary

The ACE Event Model defines the institutional logic of ACE‑Tech.  
It ensures that:

- all system state is derived from events  
- certificates are deterministic views  
- ownership is transparent  
- retirement is final  
- identity and permissions are always up‑to‑date  
- the ledger is tamper‑evident and auditable  

This conceptual model forms the foundation for the formal ACE‑Ledger‑Model and the operational ACE‑Tech prototype.
