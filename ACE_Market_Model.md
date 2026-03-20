# **ACE Market Model**  
*Version 0.3 — Clean, Deterministic, Ledger‑Anchored*

## **1. Overview**
The ACE Market Model defines how organisations receive climate grades (A–E), how surplus units (ACE‑CERT) are created and traded, and how invoice‑anchored climate performance propagates through the economy.

ACE is **not** a verifier.  
ACE is **infrastructure**:

- timestamp  
- hash  
- ledger  
- deterministic grade calculation  

Verification is performed by **auditors**, not ACE.

ACE supports two layers:

- **ACE Climate Rating (A–E)** — available to all organisations  
- **ACE‑Registration (A–E)** — audited, ledger‑integrated status  

Only ACE‑Registered organisations can use ACE‑CERT to influence next year’s grade.

---

## **2. ACE‑MRV**
ACE‑MRV is the organisation’s self‑reported, invoice‑anchored climate data.

ACE‑MRV includes:

- cost‑based and invoice‑based emissions  
- energy, transport, machinery and service inputs  
- capital goods  
- **CRCF‑aligned biogenic inputs** (land‑use sectors only)

### **ACE does not verify MRV**
ACE:

- does **not** check correctness  
- does **not** check plausibility  
- does **not** inspect invoices  
- does **not** perform audits  

ACE only:

- timestamps  
- hashes  
- stores  
- makes data immutable  

### **Auditors verify MRV**
Auditors check:

- that MRV matches bookkeeping  
- that invoices exist  
- that ACE‑deductions are correct  
- that ACE‑CERT purchases are correctly recorded  

Auditors get **one new number** to verify:  
**the MRV total the company submitted to ACE.**

---

## **3. ACE Climate Rating (A–E)**
ACE can issue a climate rating to **any organisation**, based on ACE‑engine calculations.

Characteristics:

- external  
- non‑audited  
- not linked to ACE‑CERT  
- not part of the ACE ledger  

ACE Climate Rating is the **public, open layer**.

---

## **4. ACE‑Registration (A–E)**
ACE‑Registration is the **audited, ledger‑integrated** status.

An organisation is ACE‑Registered when:

1. It has submitted ACE‑MRV  
2. It has received an ACE grade (A–E)  
3. It is subject to auditability  

All ACE‑Registered organisations **always** have a grade A–E.

### **Grade definitions**
- **A+** = net‑negative  
- **A** = net‑zero  
- **B–E** = increasing deficit levels  

**A+ is displayed as A**, but A+ organisations receive ACE‑CERT.

---

## **5. ACE‑CERT (Surplus Unit)**
ACE‑CERT is the **only tradable unit** in the ACE system.

ACE‑CERT:

- is created **only** by A+ organisations  
- represents **verified net‑negative surplus**  
- can be **sold to anyone**  
  - ACE‑Registered organisations  
  - non‑registered organisations  
  - investors  
  - public actors  
  - international buyers  

ACE‑CERT is **not** a rating, not a report, not a registration.  
It is a **commodity**.

---

## **6. Invoice‑Anchored Deduction (A–E → 100–0%)**
The deduction applied by the buyer’s auditor is **entirely determined** by the seller’s ACE‑grade:

| Seller ACE‑grade | Deduction for buyer |
|------------------|---------------------|
| **A** | 100% |
| **B** | 75% |
| **C** | 50% |
| **D** | 25% |
| **E** | 0% |

### **ACE does not apply the deduction**  
The deduction is performed by:

- the buyer’s auditor  
- using the seller’s ACE‑grade  
- verified in the ACE ledger  
- anchored in the buyer’s bookkeeping  

ACE only stores:

- the seller’s grade  
- the invoice timestamp  
- the ledger entry  

---

## **7. Year‑to‑Year Logic**

### **Year N — ACE‑Registration**
1. Organisation A submits ACE‑MRV  
2. ACE timestamps + hashes the data  
3. ACE‑engine calculates the climate outcome  
4. Organisation A receives ACE‑grade (A–E)  
5. If A is net‑negative → A+ → receives ACE‑CERT  

ACE does **not** verify MRV.  
Auditors do.

---

### **During Year N+1 — Market Activity**

#### **1. Organisation A sells to Organisation B**
- Invoice includes A’s ACE‑grade  
- Auditor at B checks the grade in the ACE ledger  
- Auditor applies the A–E → 100–0% deduction  

#### **2. Organisation B may buy ACE‑CERT**
- If B is ACE‑Registered  
- Purchases are logged in the ledger  
- They affect **next year’s** grade  

#### **3. ACE does not intervene**
ACE does not:

- check invoices  
- check deductions  
- check MRV correctness  
- check bookkeeping  

ACE only records.

---

### **End of Year N+1 — New ACE‑Registration**

ACE‑engine recalculates B’s grade using:

1. **B’s MRV** (auditor‑verified)  
2. **invoice‑anchored deductions** (100–0%)  
3. **ACE‑CERT purchased**  
4. **CRCF‑aligned biogenic inputs** (if relevant)

ACE outputs a **new ACE‑grade (A–E)**.

---

## **8. Market Dynamics**

### **Supply**
A+ organisations — typically:

- large forest owners (e.g., Sveaskog, SCA)  
- regenerative agriculture  
- high‑biomass land managers  

These actors generate **significant ACE‑CERT supply**.

### **Demand**
B–E organisations — typically:

- industry  
- transport  
- construction  
- energy  
- municipalities  
- service sectors  

These actors buy ACE‑CERT to improve next year’s grade.

### **External demand**
ACE‑CERT can be sold to:

- investors  
- public procurement  
- climate portfolios  
- international buyers  

This creates a **liquid, multi‑sectoral market**.

---

## **9. Summary**

The ACE Market Model operates as follows:

1. **ACE‑MRV** is submitted (ACE records, auditors verify)  
2. **CRCF** provides optional land‑sector inputs  
3. **ACE Climate Rating (A–E)** is available to all  
4. **ACE‑Registration (A–E)** is the audited, ledger‑integrated status  
5. **A+ organisations receive ACE‑CERT**  
6. **ACE‑CERT can be sold to anyone**  
7. **ACE‑Registered organisations can use ACE‑CERT to improve next year’s grade**  
8. **Invoice‑anchored deduction = A–E → 100–0%**  
9. **Auditors verify; ACE records**  
10. **E‑class is automatic; A–D require no extra work from ACE**  

ACE is:

- universal  
- invoice‑anchored  
- CRCF‑compatible  
- auditor‑verified  
- ledger‑based  
- regulator‑ready  
- ontologically clean  

---
