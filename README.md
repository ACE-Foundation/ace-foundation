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
- Certificate and retirement schema  
- Governance and roles  
- Supporting documentation for verification, settlement, and fungibility  

This repository does **not** contain code, algorithms, or proprietary logic.

---

## Repository Structure

### Core Documents
- [0. ACE-Whitepaper-v0.1.md](ACE-Whitepaper-v0.1.md)
- [1. ACE-Ontology.md](ACE-Ontology.md)
- [2. ACE-Metadata-Standard.md](ACE-Metadata-Standard.md)
- [3. ACE_Market_Model.md](ACE_Market_Model.md)

### Methodology
- [ACE-METH-001 (v1.0)](methodology/ACE-METH-001/1.0/ACE-METH-001.md)
  - [Appendix A](methodology/ACE-METH-001/1.0/appendix_A.md) (coming soon, WIP)
  - [Appendix B](methodology/ACE-METH-001/1.0/appendix_B.md) (coming soon, WIP)
  - [Appendix C](methodology/ACE-METH-001/1.0/appendix_C.md) (coming soon, WIP)
  - [Appendix D](methodology/ACE-METH-001/1.0/appendix_D.md) (coming soon, WIP)
  - [Appendix E](methodology/ACE-METH-001/1.0/appendix_E.md) (coming soon, WIP)

### Additional Standards
- [ACE-Certificate-Schema.md](ACE-Certificate-Schema.md) (coming soon, WIP)

### Research
#### 01 – Klimatklivet
- [analysis.md](research/use-cases/01-Klimatklivet/analysis.md)
- [Analysis2.md](research/use-cases/02-Comparative_Analysis_of_Climate_Policy_Evaluation_Models/Analysis2.md)
- (coming soon, WIP)

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
This ensures perfect auditability, institutional consistency, and constitutional integrity.

---

## Status of This Repository

This repository contains:

- **the ACE Ontology (immutable)**  
- **constitutional documents**  
- **governance structure**  
- **public reference materials**

This repository does **not** contain:

- H‑Class implementation  
- ACE Engine code  
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

Documents follow semantic versioning where applicable.

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

For full details, see:  
(ACE_IP_Statement.md)

---

## License

No open-source license is applied.  
All rights are reserved by the originator unless explicitly stated otherwise.

---
**ACE Foundation**

Custodian of the ACE Ontology
info@acefoundation.net

