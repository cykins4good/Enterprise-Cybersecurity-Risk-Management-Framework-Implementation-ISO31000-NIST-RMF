# Phase 0 — Preparation & Scope  
*(ISO 31000:2018 — Context Establishment)*  

## 1. Organizational Overview
I am simulating a mid-sized enterprise called **CyberFort Solutions Ltd.**, a technology company offering managed IT and cloud-security services to corporate clients.  
The goal of this phase is to define the organizational context, regulatory environment, key stakeholders, and critical information assets that will shape the risk management process.

---

## 2. Objectives
- To establish the internal and external context of the simulated organization.  
- To identify and classify information assets.  
- To define the risk management scope, boundaries, and assumptions.  
- To align with ISO 31000:2018 principles and NIST RMF “Categorize” step.

---

## 3. Stakeholders
| Stakeholder | Role | Interest/Expectation |
|--------------|------|----------------------|
| Executive Management | Define risk appetite and approve controls | Protection of reputation and client trust |
| IT Operations | Implement and maintain systems | Ensure service availability |
| Security Team (me) | Identify, assess, and mitigate risks | Maintain confidentiality, integrity, and availability |
| Clients | Consumers of managed services | Expect compliance with data-protection laws |
| Regulators | Compliance oversight | Enforce cybersecurity and privacy requirements |

---

## 4. Critical Assets
| Asset ID | Asset Name | Type | Description | Owner |
|-----------|-------------|------|--------------|--------|
| A01 | Customer Database | Information | Stores sensitive client data and credentials | Security Team |
| A02 | Web Application Portal | System | Main customer interface for service delivery | IT Operations |
| A03 | Internal File Server | Infrastructure | Stores operational documents | IT Department |
| A04 | Network Infrastructure | Network | Firewalls, routers, and VPN gateways | Network Team |

---

## 5. Regulatory & Compliance Context
The organization must comply with:
- **ISO 27001:2022** (Information Security Management System)  
- **GDPR** (for EU clients’ data)  
- **NIST SP 800-37 Rev. 2** for risk management integration  
- **PCI-DSS** (if processing payment data)

---

## 6. Risk Appetite Statement
I will assume that CyberFort Solutions Ltd. has a **moderate risk appetite**, meaning that management is willing to accept limited risk exposure in exchange for agility and innovation, but not at the cost of data breaches or non-compliance.

---

## 7. Scope Definition
The risk assessment will focus on:
- Web-based applications hosted on the enterprise network.  
- Data storage and transmission systems.  
- Access control and authentication mechanisms.  

Out-of-scope: third-party SaaS services and non-production environments.

---

## 8. Deliverables
- Context_Document.md (this file)  
- Organizational overview diagram (to be added later)  
- Stakeholder matrix  
- Asset inventory  
- Defined risk appetite statement

---

*End of Phase 0 — Context definition completed. Next phase: Risk Identification.*
