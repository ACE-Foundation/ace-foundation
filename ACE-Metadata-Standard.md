# **ACE Metadata Standard (Constitutional Layer)**

## 1. Purpose
The ACE Metadata Standard defines the immutable structure for describing the contextual identity 
of all ACE ledger, settlement, and retirement entries. Metadata provides **meaning**, 
not **computation**. It ensures that all ACE-compliant systems attach the same descriptive information 
to states, flows, and events, regardless of sector, technology, or implementation.

Metadata is **descriptive**, **non-algorithmic**, and **constitutionally required**.

---

## 2. Constitutional Principles

### 2.1 Metadata as Identity 
Metadata defines the identity and context of a ledger entry. 
It does not:
- calculate 
- infer 
- convert 
- substitute 
- determine equivalence 

Metadata describes *what the entry is*, not *what it means*.

### 2.2 No Algorithmic Metadata 
Metadata may never contain:
- coefficients 
- conversion factors 
- lookup tables 
- discount rates 
- algorithmic outputs 
- implementation logic 

Metadata is strictly non-computational.

### 2.3 Universality 
All ACE entries-states, flows, transfers, settlement events, and retirement events-must 
reference metadata. No entry may exist without metadata.

### 2.4 Permanence 
The metadata schema is constitutional and may not be altered by implementations. 
Implementations may add optional fields but may not remove or redefine constitutional fields.

---

## 3. Metadata Entities

Metadata is organized into five constitutional categories:

1. **Spatial Metadata** 
2. **Temporal Metadata** 
3. **Measurement Metadata** 
4. **Technological Metadata** 
5. **Scenario Metadata**

These categories are exhaustive and permanent.

---

## 4. Constitutional Metadata Fields

### 4.1 Spatial Metadata 
Spatial metadata describes where the entry applies.

Required fields:
- **Location ID** - a unique spatial identifier 
- **Jurisdiction** - regulatory or administrative boundary 
- **Spatial Resolution** - field, farm, region, or global 

Spatial metadata may constrain fungibility or settlement but may never expand it.

---

### 4.2 Temporal Metadata 
Temporal metadata describes when the entry applies.

Required fields:
- **Timestamp** - ISO-8601 
- **Temporal Resolution** - instantaneous, daily, seasonal, annual 
- **Reference Period** - the period the entry describes 

Temporal metadata may not be used to infer rates or trends.

---

### 4.3 Measurement Metadata 
Measurement metadata describes how a quantity was obtained.

Required fields:
- **Measurement Method** - laboratory, model, sensor, survey 
- **Measurement Basis** - dry weight, fresh weight, mineral N, etc. 
- **Uncertainty Class** - qualitative uncertainty category 
- **Verification Status** - unverified, verified, certified 

Measurement metadata does not contain numerical uncertainty values.

---

### 4.4 Technological Metadata 
Technological metadata describes the technical context of the entry.

Required fields:
- **Technology Class** - the T-class identifier 
- **Module ID** - the certified module used 
- **Operational Context** - management or system description 

Technological metadata does not contain performance coefficients.

---

### 4.5 Scenario Metadata 
Scenario metadata describes the scenario within which the entry exists.

Required fields:
- **Scenario ID** - unique scenario identifier 
- **Scenario Type** - baseline, intervention, counterfactual 
- **Scenario Boundaries** - spatial, temporal, and system boundaries 

Scenario metadata does not contain scenario logic.

---

## 5. Metadata Structure

### 5.1 Constitutional Columns 
Every metadata object must contain:

- **Metadata ID** 
- **Spatial Metadata** 
- **Temporal Metadata** 
- **Measurement Metadata** 
- **Technological Metadata** 
- **Scenario Metadata** 

These fields are permanent and may not be removed or renamed.

### 5.2 Optional Fields 
Implementations may add optional metadata fields, provided they:
- do not alter ontology 
- do not contain logic 
- do not introduce coefficients 
- do not redefine constitutional fields 

Optional fields must be strictly descriptive.

---

## 6. Metadata and Ontology

### 6.1 Ontological Boundaries 
Metadata may constrain:
- fungibility 
- settlement 
- scenario validity 

Metadata may never:
- redefine ontological classes 
- alter class boundaries 
- change ontological order 

### 6.2 No Cross-Class Metadata 
Metadata cannot cause units to change class. 
For example:
- A B-unit cannot become an M-unit through metadata. 
- A T-unit cannot become a C-unit through metadata. 

Metadata describes; it does not transform.

---

## 7. Metadata and Ledger

### 7.1 Ledger Integration 
Every ledger entry must reference a metadata object. 
The ledger stores:
- quantities 
- classes 
- flows 
- states 

Metadata stores:
- identity 
- context 
- measurement basis 

### 7.2 No Embedded Logic 
Ledger entries may not embed metadata fields directly. 
They must reference metadata objects by ID.

---

## 8. Metadata and Settlement

### 8.1 Settlement Constraints 
Metadata may restrict settlement (e.g., jurisdictional rules). 
Metadata may not:
- expand fungibility 
- override ontological identity 
- redefine settlement classes 

### 8.2 Traceability 
Settlement events must reference metadata to ensure:
- auditability 
- jurisdictional compliance 
- scenario consistency 

---

## 9. Metadata and Retirement

### 9.1 Retirement Context 
Retirement entries must reference metadata describing:
- jurisdiction 
- regulatory context 
- scenario 
- measurement basis 

### 9.2 No Retroactive Metadata 
Metadata cannot be altered after retirement. 
Corrections require a new metadata object.

---

## 10. Custodianship 
The ACE Foundation is the custodian of the metadata standard. 
Custodianship ensures:
- permanence 
- neutrality 
- interoperability 
- auditability 

Implementations may extend metadata but may not alter constitutional fields.

---

## 11. Constitutional Permanence 
The metadata standard is a constitutional component of ACE. 
It may not be amended by implementations, applications, or sectoral modules. 
Its purpose is to guarantee that all ACE systems describe identity and context using the same 
immutable structural grammar.

---
