# 🛡️ Phase 1 — Risk Identification  
**Enterprise Cybersecurity Risk Management Framework Implementation**  
**Aligned with:** ISO 31000:2018 | NIST SP 800-37 Rev. 2 (RMF Step 1 & 2)

---

## 1. Purpose
This document identifies and describes cybersecurity risks that could affect the confidentiality, integrity, and availability of enterprise information assets.  
The goal is to establish a clear foundation for subsequent phases — *Risk Analysis*, *Risk Treatment*, and *Monitoring* — in line with ISO 31000’s principles and NIST RMF’s Prepare and Categorize steps.

---

## 2. Methodology
The identification process followed a structured approach consistent with:
- **ISO 31000:2018 Clause 6.3.1 – Risk Identification**  
- **NIST RMF Step 1 (Prepare) and Step 2 (Categorize Information Systems)**  
- **Input sources:**  
  - Threat Intelligence Reports (internal & external)  
  - Asset Inventories & Network Diagrams  
  - System Security Plans (SSP)  
  - Incident Records & Vulnerability Scans  
  - Regulatory & Compliance Obligations  

---

## 3. Stakeholders Involved
| Role | Responsibility | Department |
|------|----------------|-------------|
| Chief Information Security Officer (CISO) | Oversight of the risk identification process | Cybersecurity |
| Risk Manager | Coordinates the process and documents identified risks | GRC |
| System Owners | Provide detailed insights on asset exposure | IT Operations |
| Compliance Officer | Maps risks to relevant regulatory requirements | Legal & Compliance |
| Incident Response Team | Shares patterns from prior incidents | SOC |

---

## 4. Asset Inventory Summary
| Asset ID | Asset Name | Type | Owner | Classification | Business Impact |
|-----------|-------------|------|--------|----------------|----------------|
| A-001 | Enterprise Email Server | Hardware/Service | IT Ops | Confidential | High |
| A-002 | Employee Endpoint Devices | Hardware | End Users | Internal | Medium |
| A-003 | Cloud Storage (Azure Blob) | Cloud Service | Cloud Team | Confidential | High |
| A-004 | Active Directory Domain Controller | System | SysAdmin | Critical | Very High |

> **Note:** Asset identification aligns with ISO 27005’s Asset Inventory principle.

---

## 5. Threat Identification
| Threat ID | Threat Category | Description | Potential Source | Likelihood |
|------------|-----------------|--------------|------------------|-------------|
| T-001 | External – Cyberattack | Phishing and credential theft targeting employee email accounts | Cybercriminals | High |
| T-002 | Internal – Negligence | Unintentional data exposure through misconfigured cloud storage | Employees | Medium |
| T-003 | Technology Failure | Outdated software leading to unpatched vulnerabilities | IT Infrastructure | Medium |
| T-004 | Supply Chain | Compromise through third-party vendor integrations | Vendors | Medium |

---

## 6. Vulnerability Identification
| Vulnerability ID | Associated Asset | Description | Detection Source | Severity |
|------------------|------------------|-------------|------------------|-----------|
| V-001 | A-003 | Public read access enabled on sensitive cloud containers | Cloud Security Scan | High |
| V-002 | A-004 | Weak password policies in Active Directory | Internal Audit | High |
| V-003 | A-002 | Unpatched OS versions on endpoints | Vulnerability Management Tool | Medium |

---

## 7. Risk Register (Preliminary)
| Risk ID | Threat | Vulnerability | Asset | Potential Impact | Likelihood | Risk Rating |
|----------|---------|---------------|--------|------------------|-------------|--------------|
| R-001 | T-001 | V-002 | A-004 | Unauthorized system access | High | High |
| R-002 | T-002 | V-001 | A-003 | Data leakage & compliance breach | High | Medium |
| R-003 | T-003 | V-003 | A-002 | Malware infection, downtime | Medium | Medium |

> This preliminary Risk Register will be refined in **Phase 2 – Risk Analysis**.

---

## 8. Key Observations
- Email and Identity Infrastructure remain primary attack vectors.  
- Cloud misconfigurations pose increasing risk due to shared responsibility gaps.  
- Patch management inconsistency highlights process immaturity in IT Operations.

---

## 9. Next Steps (Transition to Phase 2)
1. Evaluate risk likelihood and impact quantitatively.  
2. Prioritize risks using a risk matrix.  
3. Develop contextual mitigation plans aligned with enterprise risk appetite.  
4. Prepare for **Phase 2: Risk Analysis**.

---

## 10. Author & Review
| Name | Role | Date | Status |
|-------|------|------|--------|
| Cypriano Akinwunmi | Cybersecurity GRC & Risk Management Lead | *(Today’s Date)* | Draft |

---

> **Professional Note:**  
> This phase demonstrates Cypriano Akinwunmi’s analytical ability and passion for structured enterprise risk management — translating ISO 31000 principles into actionable cybersecurity governance practice with measurable traceability.
