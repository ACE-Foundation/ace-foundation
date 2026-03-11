# **Use Case 01 – Klimatklivet**  
### **Baseline vs Regenerative Scenario Analysis**  
*(ACE Research — Public Documentation)*

---

## **1. Purpose**

This use case evaluates two contrasting cultivation systems for the same field unit:

- **Baseline**: conventional, high‑disturbance system  
- **Regenerative**: no‑till, ecological, low‑disturbance system  

The objective is to quantify:

- soil carbon dynamics  
- nitrogen flows  
- fossil emissions  
- net CO₂e outcome  

…using the ACE v1.0.0 method.  
All certificates are **machine‑readable (`.json`)** and **human‑readable (`.html`)**, with **input embedded directly inside each certificate**.

---

## **2. Method Overview**

ACE is a standardized calculation method that quantifies soil carbon dynamics, nitrogen flows, and fossil emissions.
All input is embedded directly in each certificate and protected with SHA‑256 hashes, ensuring tamper‑proof reproducibility.

The method uses domain profiles and soil parameters to calculate carbon pool changes and net CO₂e.
The same method is applied consistently to both baseline and regenerative scenarios.

ACE certificates include:

- full input data  
- soil parameters  
- biomass flows  
- nitrogen flows  
- domain profile selections  
- carbon pool changes  
- fossil emissions  
- net CO₂e  
- cryptographic SHA‑256 hashes  

This ensures that each certificate is:

- **self‑contained**  
- **auditable**  
- **tamper‑resistant**  
- **reproducible**  

No external input files are required.

---

## **3. Input Description**

### **3.1 Input is embedded inside the certificate**

Each certificate contains a complete `"input"` block, including:

- year, area, cost  
- soil type, humus, density  
- grain yield, biomass flows  
- measured soil nitrogen  
- fertilized nitrogen  
- domain profile selections  
- land use and method  

This design ensures:

- no duplication  
- no missing data  
- full transparency  
- verifiable integrity via SHA‑256 hashes  

### **3.2 Input categories**

| Category | Description |
|---------|-------------|
| General parameters | year, area, cost, method |
| Soil parameters | soil type, humus %, bulk density |
| Biomass flows | grain yield, cover crop biomass |
| Nitrogen parameters | measured N, fertilized N, deposition |
| Domain profile | disturbance, pesticides, fertilizers, hydrology |

---

## **4. Scenario Summary**

### **4.1 Baseline Scenario (Conventional)**  
Certificate ID: **ACE-CERT-2021-a43c58c5**

Characteristics:

- High soil disturbance  
- Medium pesticide impact  
- Low biological complexity  
- High‑impact fertilizer strategy  
- Conventional production system  
- Higher fertilized nitrogen (78 kg N)  
- Fossil‑intensive operations  

### **4.2 Regenerative Scenario (No‑till, Ecological)**  
Certificate ID: **ACE-CERT-2021-09049ae0**

Characteristics:

- Low soil disturbance  
- Low pesticide impact  
- High biological complexity  
- Organic fertilizer strategy  
- Ecological production system  
- Biological N‑fixation (80 kg N)  
- Reduced fossil energy use  

---

## **5. Key Results – Side‑by‑Side Comparison**

### **5.1 Net CO₂e Outcome**

| Scenario | Net CO₂e (kg CO₂e/ha) | Interpretation |
|----------|------------------------|----------------|
| **Baseline** | **+2,286.72** | Strong net emissions |
| **Regenerative** | **−715.99** | Strong net carbon storage |
| **Difference** | **−3,002.71** | Regenerative improves climate impact by ~3.0 t CO₂e/ha |

**This is the core Klimatklivet‑relevant result.**

---

### **5.2 Carbon Pool Changes**

| Pool | Baseline (kg CO₂e) | Regenerative (kg CO₂e) | Difference |
|------|---------------------|--------------------------|------------|
| B1 | +1,779.72 | −443.64 | **−2,223.36** |
| B2 | 0 | −150.86 | −150.86 |
| B3 | 0 | −264.00 | −264.00 |
| **Total** | **+1,779.72** | **−858.50** | **−2,638.22** |

Interpretation:

- Baseline **loses** carbon from the stable humus pool (B1).  
- Regenerative **gains** carbon across all pools.  
- The difference is **over 2.6 t CO₂e/ha** in soil carbon alone.

---

### **5.3 Nitrogen and N₂O Emissions**

| Parameter | Baseline | Regenerative | Difference |
|-----------|----------|--------------|------------|
| N losses (kg N) | 54.33 | 13.99 | −40.34 |
| N₂O emissions (kg CO₂e) | 148.32 | 38.20 | −110.12 |
| Fertilized N (kg N) | 78 | 22 | −56 |

Interpretation:

- Baseline applies **3.5× more nitrogen**, driving higher N₂O emissions.  
- Regenerative relies on **biological N‑fixation**, reducing emissions.

---

### **5.4 Fossil Emissions**

| Scenario | Fossil CO₂e (kg) |
|----------|------------------|
| Baseline | 358.69 |
| Regenerative | 104.31 |
| **Difference** | **−254.38** |

Interpretation:

- No‑till regenerative management reduces machinery passes.  
- Lower fossil emissions reinforce the climate benefit.

---

## **6. Interpretation**

### **6.1 Regenerative system performance**
The regenerative scenario:

- stores **~0.72 t CO₂e/ha**  
- reduces N₂O emissions by **110 kg CO₂e**  
- reduces fossil emissions by **254 kg CO₂e**  
- increases soil carbon in all pools  
- relies on biological nitrogen fixation  
- minimizes disturbance and pesticide impact  

### **6.2 Baseline system performance**
The baseline scenario:

- emits **2.29 t CO₂e/ha**  
- loses carbon from the stable humus pool  
- applies high levels of mineral nitrogen  
- generates high N₂O emissions  
- uses more fossil energy  

### **6.3 Total climate difference**
The regenerative system improves climate performance by:

> **≈ 3.0 tonnes CO₂e per hectare per year**

This is a **substantial, measurable, and verifiable climate benefit**.

---

## **7. Conclusions (Klimatklivet‑ready)**

1. **The regenerative scenario delivers a strong climate benefit**  
   Net result: **−716 kg CO₂e/ha**, compared to **+2,287 kg CO₂e/ha** for the baseline.

2. **The total improvement is approximately 3.0 t CO₂e/ha**  
   This is driven by carbon sequestration, reduced nitrogen emissions, and lower fossil energy use.

3. **ACE certificates provide full transparency**  
   All input is embedded in the certificate and cryptographically hashed.

4. **The method is reproducible and auditable**  
   Both machine‑readable and human‑readable formats are provided.

5. **The use case is directly applicable to Klimatklivet**  
   It demonstrates:

   - baseline vs regenerative comparison  
   - quantifiable climate benefit  
   - verifiable methodology  
   - clear documentation structure  

---

## **8. Notes**

- Additional years or fields can be added without structural changes.  
- Certificates are stored in scenario‑specific folders for clarity.  
- This analysis is part of ACE Research public documentation.
  
