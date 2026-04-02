# ACE‑MRV Standard v1.0.0  
Monitoring, Reporting and Verification Requirements for ACE‑Tech

## 1. Purpose and Scope

**Purpose**  
ACE‑MRV defines how data for greenhouse gas emissions and removals must be:

- monitored (data collection)  
- reported (structured, machine‑readable input)  
- verified (independent validation)  

…so that ACE‑ENGINE can compute CO2e outcomes, ACE‑ledger can record events, and ACE‑CERT can be deterministically reconstructed.

**Scope**

- Applies to all ACE domains: biological CDR, industrial emissions, DACCS, BECCS, biochar, long‑lived products, etc.  
- Covers both negative and positive emissions.  
- Fully compatible with **GHG Protocol**, **CRCF**, **CSRD/ESRS E1**, and **IPCC Guidelines**.  
- Implementation‑neutral: can be used with any software stack.

---

## 2. Roles and Responsibilities

### 2.1 Roles

- **Producer**  
  Collects primary data, prepares ACE‑MRV input, initiates CREATION‑TX.

- **Verifier**  
  Independent reviewer validating data, methodology, and ACE‑CERT outputs.

- **Registry Operator (ACE‑Tech)**  
  Runs ACE‑ledger, enforces ACE‑MRV rules, issues ACE‑CERT.

- **Buyer**  
  Purchases ACE‑CERT and may retire them via REDEMPTION‑TX.

- **Regulatory Observer**  
  Public authority or accredited body monitoring compliance.

### 2.2 Responsibility Split

| Function      | Responsible Party |
|---------------|-------------------|
| Monitoring    | Producer          |
| Reporting     | Producer + ACE‑Tech |
| Verification  | Verifier          |
| Ledger Events | ACE‑Tech          |
| Regulatory Alignment | ACE‑Foundation |

---

## 3. ACE‑MRV Data Model

ACE‑MRV uses the ACE‑Metadata‑Standard as its structural foundation.  
All MRV input must be representable as a single JSON object:

```json
{
  "general": {},
  "activity_data": {},
  "emission_factors": {},
  "domain_specific": {},
  "verification": {},
  "provenance": {}
}
```

### 3.1 General

- `entity_id` (ACE‑ID)  
- `reporting_period_start`  
- `reporting_period_end`  
- `domain` (agriculture, forestry, industry, DACCS, etc.)  
- `method_version` (e.g., "ACE‑METH‑001 v1.0.0")  
- `geolocation` (min. field/facility resolution)

Note: MRV input describes real‑world emissions and removals.  
It must not include certificate ownership or ACE‑CERT references.  
Certificate ownership is handled exclusively through REGISTRATION events.

### 3.2 Activity Data

**Biological CDR examples:**

- `area_ha`  
- `soil_type`  
- `bulk_density`  
- `humus_percent`  
- `yield`  
- `biomass_flows`  
- `fertilizer_n`  
- `soil_n_measured`  

**Industrial emissions examples:**

- `fuel_type`  
- `fuel_amount`  
- `process_emissions`  
- `energy_use`  

**DACCS examples:**

- `co2_captured_t`  
- `electricity_use_mwh`  
- `heat_use_mwh`  
- `storage_site_id`  

### 3.3 Emission Factors

- `emission_factor_source` (IPCC, national inventory, peer‑reviewed source)  
- `emission_factor_version`  
- `emission_factors` (structured list with units)

### 3.4 Domain‑Specific Parameters

- `management_practices`  
- `system_boundaries`  
- `disturbance_profile`  
- `technology_parameters` (for DACCS/BECCS)

### 3.5 Verification Block

- `verification_status` (unverified / verified / rejected)  
- `verifier_id`  
- `verification_method`  
- `verification_date`  
- `verification_notes`

### 3.6 Provenance and Integrity

- `input_hash` (SHA‑256 of the entire MRV input)  
- `created_at`  
- `created_by`  
- `data_source` (sensor / manual / system import)

---

## 4. Monitoring Requirements (M)

Monitoring ensures that all data used in ACE‑ENGINE is:

- traceable  
- complete  
- consistent  
- reproducible  

### 4.1 Monitoring Rules

- Every value must have a **source** (measurement, sensor, calculation, estimate).  
- All measurements must include **timestamp** and **location**.  
- All assumptions must be explicitly documented.  
- No black‑box transformations are allowed.  
- All raw data must be retained for audit.

---

## 5. Reporting Requirements (R)

Reporting transforms monitored data into a structured, machine‑readable format.

### 5.1 Reporting Format

- JSON according to ACE‑Metadata‑Standard + ACE‑MRV fields.  
- Must include `input_hash` before ACE‑ENGINE execution.  
- Must be self‑contained (no external dependencies).

### 5.2 Reporting Rules

- Each reporting unit (e.g., 1 ha, 1 facility, 1 year) must have its own MRV block.  
- All emission factors must include source and version.  
- All domain‑specific parameters must be explicitly stated.

---

## 6. Verification Requirements (V)

Verification ensures that ACE‑CERT is trustworthy, reproducible, and compliant with CRCF and GHG Protocol.

### 6.1 Verification Steps

1. **Input Validation**  
   - Completeness, plausibility, source integrity.  
   - Check that ACE‑MRV fields are correctly populated.

2. **Method Validation**  
   - Confirm correct `method_version`.  
   - Confirm ACE‑METH‑001 rules are followed.

3. **Recalculation**  
   - Verifier re‑runs ACE‑ENGINE using the same MRV input.  
   - Output must match ACE‑CERT exactly (ACE is deterministic).

4. **Ledger Validation**  
   - Verify hash chain integrity.  
   - Verify that ACE‑CERT can be reconstructed from event history.

5. **Verification Record**  
   - Update `verification` block.  
   - Trigger REGISTRATION event if required.

---

## 7. End‑to‑End MRV Flow

1. **Monitoring**  
   The Producer collects all required data according to ACE‑MRV.

2. **Reporting**  
   The Producer prepares the ACE‑MRV JSON input and computes the `input_hash` (SHA‑256 over the entire MRV block).

3. **Calculation (ACE‑ENGINE)**  
   ACE‑ENGINE processes the MRV input, applies ACE‑METH‑001, and produces a deterministic CO₂e calculation result.

4. **Creation Event**  
   ACE‑Tech generates a **CREATION‑TX** event containing:  
   – the calculation result  
   – the MRV metadata  
   – the `input_hash`  
   – certificate identifiers  
   This event initializes the certificate lifecycle.

5. **Registration**  
   ACE‑Tech issues a **REGISTRATION** event updating identity, rating, permissions, and account state.  
   (Every CREATION‑TX must be followed by a REGISTRATION event.)

6. **Verification**  
   The Verifier validates:  
   – MRV input completeness and integrity  
   – correct application of ACE‑METH‑001  
   – deterministic reproducibility of ACE‑ENGINE output  
   – ledger hash‑chain integrity  
   – certificate lifecycle consistency

7. **Certificate Reconstruction**  
   ACE‑CERT is deterministically reconstructed from the ledger by applying `build_certificate_json(event_stream)` to all events associated with the certificate ID.

8. **Trading**  
   Ownership transfers follow the ACE‑Market‑Model.  
   A **TRADING‑TX** event is created after successful clearing and settlement.  
   (Trading does not involve ACE‑ENGINE.)

9. **Retirement**  
   A **REDEMPTION‑TX** event retires the certificate.  
   This represents the matching of positive emissions with purchased negative emissions.

10. **Post‑Retirement Registration**  
    A final **REGISTRATION** event updates identity, rating, permissions, and account balances after retirement.  
    (Every REDEMPTION‑TX must be followed by a REGISTRATION event.)


---

## 8. Compliance and Interoperability

ACE‑MRV is designed to be interoperable with:

- **GHG Protocol (Scopes 1–3)**  
- **CRCF (EU Carbon Removal Certification Framework)**  
- **CSRD / ESRS E1**  
- **IPCC Guidelines**  
- **ISO 14064‑1/2/3**  

ACE‑MRV ensures that:

- ACE‑CERT can be used in corporate climate reporting.  
- ACE‑CERT can be audited by third parties.  
- ACE‑CERT can be integrated into national and EU‑level systems.

---

## 9. Versioning and Governance

- Maintained by **ACE‑Foundation**.  
- Semantic versioning: MAJOR.MINOR.PATCH.  
- Changes require public review and governance approval.  
- Backwards compatibility is maintained whenever possible.

---

## 10. Summary

ACE‑MRV provides the structured, verifiable, and deterministic foundation required for:

- ACE‑ENGINE calculations  
- ACE‑ledger events  
- ACE‑CERT reconstruction  
- CRCF‑aligned certification  
- GHG‑compliant reporting  
- Independent verification  

It is the compatibility layer that connects real‑world data to ACE’s cryptographically verifiable certificate architecture.
```

---

If you want, I can now:

- generate **ACE_Ledger_Model.md**  
- generate **ACE_Event_Model.md**  
- generate **ACE‑MRV JSON schema**  
- generate **ACE‑MRV → ACE‑ENGINE mapping tables**  
- or integrate ACE‑MRV into the Steg 0/Steg 1 project plan  

Just tell me where you want to go next.
