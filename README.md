# ACE Foundation – Open Standard Repository

ACE Foundation is the public, implementation‑neutral standard layer of the Adaptive Carbon Engine (ACE).  
This repository contains the ontology, metadata model, methodology, certificate schema, and governance framework required to ensure transparent, comparable, and auditable agricultural climate assessment.

ACE Foundation publishes the open standard.  
The exclusive right to implement ACE‑compliant systems is held by the originator.

---

## Purpose

The purpose of this repository is to provide a stable, transparent, and openly accessible specification of the ACE standard, including:

- ACE Ontology  
- ACE Metadata Standard  
- ACE Methodology (ACE‑METH‑001)
- ACE Ledger Model
- ACE Event Model
- ACE Ledger Certificate Model

This repository does **not** contain code, algorithms, or proprietary logic.

---

## Repository Structure

### 1. Core Documents (Start Here)
- [ACE-Whitepaper-v0.1.md](ACE-Whitepaper-v0.1.md)
- [ACE-Ontology.md](ACE-Ontology.md)
- [ACE-Metadata-Standard.md](ACE-Metadata-Standard.md)
- [ACE_Market_Model.md](ACE_Market_Model.md)
- [ACE_Regulatory_Model.md](ACE_Regulatory_Model.md)

### 2. Domain Standards (MRV → Method → Market → Regulation)
- [ACE-MRV.md](ACE-MRV.md)
- [ACE-METH-001 (v1.0)](methodology/ACE-METH-001/1.0/ACE-METH-001.md)
  - [Appendix A](methodology/ACE-METH-001/1.0/appendix_A.md) (coming soon, WIP)
  - [Appendix B](methodology/ACE-METH-001/1.0/appendix_B.md) (coming soon, WIP)
  - [Appendix C](methodology/ACE-METH-001/1.0/appendix_C.md) (coming soon, WIP)
  - [Appendix D](methodology/ACE-METH-001/1.0/appendix_D.md) (coming soon, WIP)
  - [Appendix E](methodology/ACE-METH-001/1.0/appendix_E.md) (coming soon, WIP)


### 3. Ledger Standards (Institutional Blockchain Layer)
These documents define the institutional ledger that governs certificate creation, transfer, retirement, and annual book‑closing:
- [ACE EVENT.md](ACE-EVENT.md)
  Defines CREATION‑TX, TRADING‑TX, REDEMPTION‑TX, and REGISTRATION.
- [ACE LEDGER.md](ACE-LEDGER.md)
  Defines the append‑only, hash‑chained, deterministic ledger model.
- [ACE_Ledger_Certificate.md](ACE_Ledger_Certificate.md)
  Defines the deterministic, cryptographically anchored certificate model.
Together, these form the ACE Core Ledger Protocol.

### 4. Research by ACE Renaissance
https://github.com/ACE-Foundation/ace-renaissance

ACE Renaissance develops analytical frameworks for climate policy, industrial transition, and bio‑based systems. Each use case represents an independent analysis, while together they form a coherent methodology for evaluating climate impact, system effects, and policy design.

01. Klimatklivet  
Assessment of investment support using ACE‑CERT Baseline and Regenerative to quantify emission reductions and system‑level effects.

02. Industriklivet  
Application of ACE‑CERT Industry to evaluate industrial decarbonization projects, cost efficiency, and long‑term climate impact — in combination with the analytical structure established in Use Case 01.

03. Biomass Limit  
System analysis of biomass availability, competition, physical constraints, and policy implications — grounded in the fundamental limits set by photosynthesis and land area.

04. ACE‑CERT  
Use‑case‑specific application of the ACE‑CERT methodology to test, validate, and compare certification logics — providing a unified analytical solution for Use Cases 01–03.

05. Klimatpolitiska Rådet  
Analytical framework aligned with the Swedish Climate Policy Council’s criteria for target fulfilment, policy effectiveness, and system robustness — with ACE providing the quantitative assessment that the Council itself does not perform.

---
## Ledger and Event Domains

ACE defines the following institutional domains:

- **MRV Domain** — verified evidence (measurements, reports, signatures, hashed proofs)  
- **Transaction Domain** — creation, transfer, and redemption of certificates  
- **Clearing Domain** — validation, matching, and locking of positions  
- **Settlement Domain** — irreversible execution of cleared transactions  
- **Ledger Domain** — append‑only event log forming the institutional truth  

The ledger is:

- **append‑only**  
- **immutable**  
- **deterministic**  
- **the single source of institutional truth**

Balances are **never stored**.  
They are deterministically derived from ledger events.  

---

## Status of This Repository

This repository contains:

- **the ACE Ontology (immutable)**  
- **constitutional documents**  
- **governance structure**  
- **methodology and domain standards**
- **ledger and event standards**

This repository does **not** contain:

- ACE Engine implementation  
- H-Class logic
- operational modules  
- any executable logic  

These remain **proprietary** and may only be used under explicit license from the originator.

---

## Implementation Neutrality

ACE defines structure, not code.  
Implementations must:

- follow the ontology  
- follow the flow structure  
- remain deterministic  
- remain auditable  
- remain explainable  

ACE‑METH‑001 contains no algorithms, parameters, or proprietary logic.

---

## Governance

ACE Foundation acts as custodian of:

- the ACE ontology  
- the ACE methodology  
- the metadata model  
- the certificate schema  
- the governance framework  

The originator retains exclusive rights to implement ACE‑compliant systems and may license or transfer these rights.

---

## Versioning

Methodology versions are stored under:

`methodology/ACE-METH-001/<version>/`

For example, the current stable version is:

- [ACE‑METH‑001 v1.0](methodology/ACE-METH-001/1.0/ACE-METH-001.md)

Whitepapers and supporting documents include version identifiers in their filenames.

---

## Intellectual Property & Ontological Protection

The ACE Ontology is protected as original authored work under international copyright law.

GitHub publication provides:

- cryptographic timestamp  
- immutable revision history  
- global transparency  
- legally recognized proof of priority  
- establishment of prior art  

The ontology is:

- free to read  
- free to reference  
- **not free to alter**  
- **not free to fork into derivative ontologies**  
- **not free to implement without licensed H‑Class**

The ontology is public and immutable.  
The implementation (H‑Class) is private and licensable.

See:
- [ACE_IP_Statement.md](ACE_IP_Statement.md)
- [CONTRIBUTIONS.md](CONTRIBUTIONS.md)

---

## License

No open-source license is applied.  
All rights are reserved by the originator unless explicitly stated otherwise.

---
**ACE Foundation**

Custodian of the ACE Ontology
info@acefoundation.net

