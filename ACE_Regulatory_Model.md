# ACE Regulatory Model

## 1. Purpose
This document defines the institutional and regulatory architecture that connects the major components of the European climate system:

- **EU ETS (Directive 2003/87/EC)** – Monitoring, Reporting and Verification (MRV) for positive emissions  
- **CRCF (COM(2022) 672 final; 2022/0394(COD))** – MRV and certification for carbon dioxide removal (CDR)  
- **ACE** – Neutral infrastructure layer providing ledger, certificate engine, and registry  
- **A+ Producers** – Entities generating permanent CDR and eligible for ACE‑CERT issuance  
- **Carbon Floor Authority** – Optional public stabilisation mechanism that may purchase or sell ACE‑CERT to reduce market volatility  

The purpose of the ACE Regulatory Model is to describe how these layers interact, how responsibilities are separated, and how ACE completes the operational architecture required for a functional, integrated European climate system.

---

## 2. System Layers

### 2.1 EU ETS (Directive 2003/87/EC)
**Role:**  
The EU Emissions Trading System regulates positive emissions through a cap‑and‑trade mechanism. It defines:

- emission caps  
- allocation and auctioning of EUAs  
- MRV requirements for emitters  
- compliance and enforcement  

**Scope:**  
ETS covers major industrial sectors and power generation. It provides the regulatory framework for reducing positive emissions.

**Limitations:**  
ETS is not designed to:

- handle negative emissions  
- issue or track CDR certificates  
- manage permanence  
- integrate with CDR methodologies  
- operate a ledger or registry for CDR  

ETS requires a complementary system to incorporate permanent removals.

---

### 2.2 CRCF (COM(2022) 672 final; 2022/0394(COD))
**Role:**  
The Carbon Removal Certification Framework defines:

- quality criteria for CDR  
- methodological requirements  
- verification and MRV standards  
- permanence and liability rules  

**Scope:**  
CRCF ensures that CDR activities meet minimum quality thresholds and are verifiable, additional, and durable.

**Limitations:**  
CRCF is not:

- a market  
- a registry  
- a ledger  
- a certificate engine  
- a transaction system  

CRCF defines *what* qualifies as CDR, but not *how* CDR is operationalised or transacted.

---

### 2.3 ACE
**Role:**  
ACE provides the missing operational layer required to integrate ETS and CRCF. ACE is a neutral, privately operated infrastructure that offers:

- a **ledger** for all CDR‑related transactions  
- a **certificate engine** for issuing ACE‑CERT  
- a **registry** for tracking ownership and retirement  
- **MRV integration** with CRCF methodologies  
- a **full audit trail** for transparency and compliance  

**Scope:**  
ACE enables:

- issuance of ACE‑CERT based on verified CRCF‑compliant CDR  
- transfer and retirement of certificates  
- interoperability with ETS and CRCF  
- transparent, deterministic, and audit‑ready data flows  

**Limitations:**  
ACE does **not**:

- set prices  
- participate in trading  
- act as a market maker  
- influence supply or demand  
- create CDR  

ACE is infrastructure, not a market actor.

---

### 2.4 A+ Producers
**Role:**  
A+ producers generate permanent carbon dioxide removal using CRCF‑compliant methodologies. They are the only entities eligible for ACE‑CERT issuance.

**Scope:**  
A+ producers include:

- regenerative farming (when generating measurable, durable soil carbon increases)
- forestry (long‑lived biogenic carbon storage, harvested wood products)
- BECCS operators  
- DACCS operators  
- biochar producers  
- long‑lived biogenic material producers  
- geological storage operators


**Responsibilities:**

- conduct CDR activities  
- comply with CRCF methodologies  
- undergo verification  
- submit MRV data to ACE  

**Limitations:**  
A+ producers do not:

- operate the ledger  
- issue certificates  
- regulate markets  

They supply CDR; ACE operationalises it.

---

### 2.5 Carbon Floor Authority
**Role:**  
A public authority may optionally act as a stabilisation mechanism by:

- purchasing ACE‑CERT when prices are low  
- selling ACE‑CERT when prices are high  
- maintaining a small strategic reserve  

This function corresponds to the type of market‑stabilisation role sometimes discussed in EU policy circles under concepts such as a “carbon bank”, but implemented here in a legally and operationally feasible form.

**Scope:**  
The authority provides:

- long‑term investment certainty  
- reduced market volatility  
- a minimum price signal for high‑capex CDR technologies  

**Limitations:**  
The authority does **not**:

- issue certificates  
- operate the ledger  
- regulate supply  
- replace market price formation  

It is a buffer, not a system operator.

---

## 3. Interactions

### MRV Flows
- A+ producers submit MRV data according to CRCF methodologies.  
- Verifiers confirm compliance.  
- ACE ingests verified MRV data into the ledger.

### Certificate Issuance
- ACE issues ACE‑CERT only after verified MRV.  
- Each certificate is uniquely identified and traceable.

### Registry Logic
- ACE maintains ownership records.  
- Transfers are recorded on the ledger.  
- Retirements are final and irreversible.

### Transaction Flows
- Market participants trade ACE‑CERT bilaterally or via marketplaces.  
- ACE records transfers but does not participate in trading.

### Retirement Logic
- Certificates are retired to claim climate benefit.  
- Retirement is recorded in the ACE ledger and cannot be reversed.

---

## 4. Governance Principles

### Neutrality
ACE does not participate in markets, set prices, or influence supply or demand.

### Auditability
All data, transactions, and certificate events are fully traceable and audit‑ready.

### Non‑Participation in Markets
ACE is infrastructure only.  
It does not buy, sell, or hold ACE‑CERT.

### Compatibility with EU Law
ACE is designed to:

- complement ETS  
- operationalise CRCF  
- remain compliant with EU competition and market rules  
- avoid conflicts of interest  

ACE provides the infrastructure that EU institutions cannot operate directly.

---

## 5. Summary
ACE completes the European climate architecture by providing the operational layer required to integrate ETS and CRCF. It enables issuance, tracking, transfer, and retirement of permanent CDR certificates (ACE‑CERT) while maintaining neutrality, auditability, and regulatory compatibility.

ACE does not replace existing systems.  
It connects them.

