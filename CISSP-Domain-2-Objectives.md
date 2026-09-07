# [Domain-2](#domain-2-asset-security) **Asset Security**

> 🤖 [AI Tutor](https://edureify.com/certification/exam/cissp) · 🎓 [Training](https://edureify.com/certification/cybersecurity/cissp/training) · 📝 [Practice Test](https://edureify.com/certification/cybersecurity/cissp/practice-test) · 🎯 [Mock Exam](https://edureify.com/certification/cybersecurity/cissp/mock-exam) · 📊 [Readiness Test](https://edureify.com/certification/cybersecurity/cissp/readiness-test) · 📄 [Cheat Sheet](https://edureify.com/certification/cybersecurity/cissp/cheat-sheet) · 📖 [Study Guide](https://edureify.com/certification/cybersecurity/cissp/study-guide)

- Domain 2 carries a **10% weighting** and covers protecting information and assets across their full lifecycle — from creation/collection through destruction
- The domain's throughline: you can't protect what you haven't identified and classified, and different classifications should drive genuinely different handling requirements — not a label that's applied once and ignored

## [2.1](#21-identify-and-classify) Identify and classify information and assets

- **Information and asset ownership**: every asset needs a named owner (typically a business role) accountable for its classification and protection — not IT by default
- **Asset inventory**: must cover both tangible assets (hardware, media) and intangible assets (data, intellectual property, software licenses) — an incomplete inventory undermines every downstream control
- **Asset management**: the ongoing discipline of tracking assets through their lifecycle (additions, changes in owner/sensitivity, decommissioning)
- **Data classification** labels (e.g., Public, Internal, Confidential, Restricted, or government-style Unclassified/Confidential/Secret/Top Secret) should be simple enough for staff to apply consistently and should drive concrete, different handling rules per level
- **Asset classification** applies the same logic to hardware/systems — e.g., a system hosting Restricted data inherits handling requirements even if the hardware itself seems unremarkable

## [2.2](#22-handling-requirements) Establish information and asset handling requirements

- Handling requirements translate classification into concrete rules: how an asset may be stored, transmitted, labeled, copied, and disposed of at each classification level
- **Data roles**:
  - **Owner**: accountable for classification and protection decisions
  - **Controller**: (privacy terminology, e.g., under GDPR) determines the purposes and means of processing personal data
  - **Custodian**: implements the technical protections defined by the owner/policy
  - **Processor**: (privacy terminology) processes data on behalf of a controller, under the controller's instructions
  - **User/Subject**: the individual who uses the data, or (as "data subject") the individual the data is about
- Handling requirements must be practical and enforceable — a rule nobody can realistically follow becomes a rule nobody follows

## [2.3](#23-secure-provisioning) Provision information and assets securely

- Secure provisioning applies protection *from the moment* an asset or dataset is created or acquired, not retroactively after a policy review flags it
- Includes secure baseline configuration, appropriate classification at creation time, and ensuring new assets are captured in inventory/asset management immediately — provisioning gaps (assets that exist "off the books") are a common real-world source of breaches

## [2.4](#24-data-lifecycle) Manage data lifecycle

- **Data collection**: minimize collection to what's actually needed (data minimization) — data you don't hold can't be breached
- **Data location**: track where data physically/logically resides, including cloud regions — critical for data-residency and cross-border transfer compliance (see Domain 1.4)
- **Data maintenance**: keeping data accurate and current, and ensuring protections persist as data moves or is copied
- **Data retention**: retain only as long as legally required or operationally necessary — both under-retention (destroying records you're legally required to keep) and over-retention (holding data past its useful/required life, expanding breach exposure) are risks
- **Data remanence**: residual data that can remain recoverable after normal deletion, especially on flash/SSD media where wear-leveling makes simple deletion unreliable — this is why remanence-aware destruction methods matter
- **Data destruction**: methods should match classification and media type — e.g., cryptographic erasure (destroying the encryption key rather than the data itself), degaussing (magnetic media only — ineffective on SSDs), physical destruction/shredding, and overwriting; certificates of destruction are often required for regulated data

## [2.5](#25-asset-retention) Ensure appropriate asset retention (e.g., End of Life (EOL), End of Support)

- **End of Life (EOL)**: the vendor/manufacturer stops selling or actively developing the product
- **End of Support (EOS)**: the vendor stops providing patches/security updates — running EOS software is a common, heavily-tested audit and risk finding, since new vulnerabilities will never be fixed
- Asset retention planning should proactively track EOL/EOS dates and budget for replacement or compensating controls (e.g., network isolation of unsupported systems) well before support actually ends

## [2.6](#26-data-security-controls) Determine data security controls and compliance requirements

- **Data states**: **at rest** (stored), **in transit** (moving across a network), **in use** (actively being processed in memory) — each state has different exposure and requires different controls (e.g., encryption at rest, TLS in transit, and increasingly, confidential computing/trusted execution environments to protect data in use)
- **Scoping and tailoring**: adapting a security standard's full control set to what's actually applicable to a given system (scoping) and adjusting control parameters to the org's environment (tailoring) — an exam-favorite distinction, since blindly applying every control in a framework is inefficient and sometimes impossible
- **Standards selection**: choosing the right baseline (e.g., NIST SP 800-53, ISO 27002) based on the organization's regulatory environment and risk profile
- **Data protection methods**:
  - **DRM (Digital Rights Management)**: controls how content can be used/copied after distribution
  - **DLP (Data Loss Prevention)**: detects and blocks unauthorized movement of sensitive data (e.g., email exfiltration, USB copying)
  - **CASB (Cloud Access Security Broker)**: sits between users and cloud services to enforce security policy, visibility, and compliance for SaaS/cloud usage — increasingly essential as data spreads across many cloud services outside traditional network perimeters
