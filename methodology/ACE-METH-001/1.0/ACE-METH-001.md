# ACE Methodology (Implementation-Neutral Specification)

## 1. Purpose
The methodology defines how ACE uses the ontology to structure flows, balances, 
and representations. It is transparent, deterministic, and implementation-neutral. 
It does not contain code, algorithms, or proprietary logic.

---

## 2. Scenario Structure
A scenario is a structured description of:
- initial state 
- inputs 
- technology choices 
- flows between classes 
- outputs in N, CO2e, and economic units 

Scenarios must obey the ontology and the Consequence Axiom.

---

## 3. Biological Capital (B)

### 3.1 Definition
B contains all organic nitrogen in the system. 
ACE divides B into three pools:
- **B1** - stabilized organic N 
- **B2** - fresh residues with C/N > 50 
- **B3** - fresh residues with C/N < 50 

### 3.2 N-Balance Sheet
The N-Balance Sheet tracks:
- opening balance 
- mineralization (B to M) 
- internal transfers 
- inflows from residues 
- closing balance 

Only B contains biological N. 
G and O contain none.

---

## 4. Mineral Capital (M)

### 4.1 Definition
M is the **liquidity layer** of the nitrogen system, expressed as mineral N.  
M contains no organic N and no physical capital.  
It is represented through the N‑Income Statement.

---

### 4.2 N‑Income Statement
The N‑Income Statement tracks all **liquidity flows** of mineral N:

- measured mineral N  
- inflows from B (mineralization)  
- inflows from T (fixation, additions)  
- atmospheric deposition  
- plant uptake  
- losses  
- statistical error  

Losses depend on **GOeff**, derived from G and O and modified by T.


---

## 5. Technology Capital (T)

### 5.1 Definition
T acts on B, M, and GOeff. 

### 5.2 Technology Effects
T may influence:
- mineralization (k_modifier) 
- fixation (T to M) 
- soil efficiency (GOeff) 
- residue inputs (T to B) 

Technology parameters define these effects and are listed in Appendix B.

---

## 6. Economic Capital (E)

### 6.1 Definition
E represents monetary values resulting from T acting on GOBM. 
E is ontologically below all physical classes.

### 6.2 Economic Representation
E captures:
- direct technology costs 
- indirect effects via N-flows 
- financing effects (equity, debt, interest) 

---

## 7. Climate Representation (C)

### 7.1 Definition
C is a **representation class**, not a capital class.  
C expresses climate effects in **CO₂e** using:

- C/N ratios  
- 44/12 conversion  
- CO₂e/unit values from T‑tables  

C does **not** store capital.

---

### 7.2 Scope of Representation
C represents climate effects arising from:

- **geological permanence**, via CCS → *(C represents G‑input)*  
- **biological shifts**, via regenerative flows → *(C represents O- or M‑input)*  
- **technology expressed economically**, via E‑flows → *(E → G → O → B)*  
  *(e.g., DAC, pyrolysis, biomass systems)*

C represents **only CO₂e flows**.  
C does **not** store B, M, T, or E.

---

### 7.3 Representation Logic
C is a **pure representation layer**:

- CCS is a physical process in **G**; C represents its permanence.  
- Regenerative systems shift material between **B** and **O**; C represents the climate effect.  
- DAC/pyrolysis/energy enter as **E‑flows** affecting G/O/B; C represents their CO₂e impact.

C is:

- weightless  
- capital‑free  
- non‑material  
- a representation layer only

## 8. Measurement and Overrides
Measured values override theoretical values where applicable (e.g., mineral N tests). 
Measurement does not alter ontology.

---

## 9. Implementation Neutrality
The methodology defines structure, not code. 
Implementations must:
- follow the ontology 
- follow the flow structure 
- remain deterministic 
- remain auditable 
- remain explainable 

ACE Foundation is the custodian of the ACE ontology, methodology, and governance framework.
The exclusive right to implement ACE-compliant systems is currently held by the originator,
who may license or transfer this exclusive right to another party.

---
