# [Domain-1](#domain-1-security-and-risk-management) **Security and Risk Management**

> 🤖 [AI Tutor](https://edureify.com/certification/exam/cissp) · 🎓 [Training](https://edureify.com/certification/cybersecurity/cissp/training) · 📝 [Practice Test](https://edureify.com/certification/cybersecurity/cissp/practice-test) · 🎯 [Mock Exam](https://edureify.com/certification/cybersecurity/cissp/mock-exam) · 📊 [Readiness Test](https://edureify.com/certification/cybersecurity/cissp/readiness-test) · 📄 [Cheat Sheet](https://edureify.com/certification/cybersecurity/cissp/cheat-sheet) · 📖 [Study Guide](https://edureify.com/certification/cybersecurity/cissp/study-guide)

- Domain 1 carries a **16% weighting** (up from 15% pre-2024) — the largest single domain, and foundational for the other seven; risk and governance decisions made here shape everything downstream
- This domain sets the "manager/owner" lens the whole exam is written from: security exists to serve the business, and decisions should reduce risk to an acceptable, cost-effective level — not chase absolute security

## [1.1](#11-professional-ethics) Understand, adhere to, and promote professional ethics

- **(ISC)² Code of Professional Ethics** — four canons, in priority order:
  1. Protect society, the common good, necessary public trust and confidence, and the infrastructure
  2. Act honorably, honestly, justly, responsibly, and legally
  3. Provide diligent and competent service to principals
  4. Advance and protect the profession
  - Any member of the public can file an ethics complaint under canons I and II; only an employer/contractual party can file under canon III; anyone bound by the code can file under canon IV
  - Full text: [isc2.org/Ethics](https://www.isc2.org/Ethics)
- **Organizational code of ethics**: separate from — and in addition to — the (ISC)² code; a CISSP must uphold both, and where an org's own ethics guidance is silent or unclear the (ISC)² canons still apply

## [1.2](#12-security-concepts) Understand and apply security concepts

- The **5 Pillars of Information Security**: confidentiality, integrity, availability, authenticity, and nonrepudiation
  - **Confidentiality**: preventing unauthorized disclosure of information; confidentiality ≠ secrecy — it's about protecting an asset from disclosure even when it isn't itself secret
  - **Integrity**: data is only modified by authorized parties in authorized ways; includes internal consistency and protection from accidental corruption, not just malicious tampering
  - **Availability**: authorized users get timely, uninterrupted access; supported by redundancy, failover, load balancing, and fault tolerance
  - **Authenticity**: assurance that a message, transmission, or party is genuinely who/what it claims to be
  - **Nonrepudiation**: a party can't credibly deny having performed an action; built from identification + authentication + authorization + accountability/auditing (the **AAA model**)
- **AAA in practice**: Identification (claiming an identity) → Authentication (proving it) → Authorization (what the identity is allowed to do) → Accounting/Auditing (logging what it did)

## [1.3](#13-security-governance) Evaluate and apply security governance principles

- **Security governance**: the policies, roles, and processes an org uses to direct and hold accountable its security efforts, aligned to business strategy
- Planning hierarchy: **Strategic** (multi-year direction) → **Tactical** (mid-term, ~1 year) → **Operational** (short-term, day-to-day execution)
- Key roles: **Senior manager** (ultimate accountability), **Security professional** (writes/implements policy), **Asset owner** (classifies and is accountable for an asset), **Custodian** (implements the technical protection), **Auditor** (verifies the policy is followed)
- **Third-party governance**: oversight of security imposed by law, regulation, industry standard, or contract — often verified via on-site assessment, document review, or third-party audit
- **Security control frameworks** referenced throughout the CBK: ISO 27001/27002, [NIST CSF 2.0](https://www.nist.gov/cyberframework), COBIT, SABSA, PCI DSS, FedRAMP — know what each is *for*, not every control inside it

## [1.4](#14-legal-regulatory-and-compliance) Understand legal, regulatory, and compliance issues that pertain to information security in a holistic context

- **Cybercrimes and data breaches**: understand the categories of computer crime (unauthorized access, data theft, DoS, fraud) and why jurisdiction/attribution is often the hardest part of prosecuting them
- **Licensing and Intellectual Property**: patents, copyrights, trademarks, and trade secrets each protect different things and have different durations/requirements — software is typically protected by copyright (and sometimes patent), while a secret algorithm may be better protected as a trade secret
- **Import/export controls**: cryptographic software/hardware is subject to export control regimes (e.g., items controlled similarly to those under the U.S. Export Administration Regulations) — a real constraint on shipping security products internationally
- **Transborder data flow**: moving data across national borders can trigger conflicting legal obligations — data localization laws in one jurisdiction can conflict with a global business's operational needs
- **Major privacy regimes** to recognize (not memorize verbatim): **GDPR** (EU, broad personal-data protections with extraterritorial reach), **CCPA/CPRA** (California), and other national laws (e.g., PIPL in China, POPIA in South Africa) — know that requirements like consent, data minimization, and breach notification are common threads even though specifics differ
- Security policy must map to whichever contractual, legal, industry-standard, and regulatory requirements actually apply to the organization — a compliance register mapping obligations to owners is standard practice

## [1.5](#15-investigation-types) Understand requirements for investigation types

- **Administrative**: internal, often HR-driven, investigates policy violations; lowest evidentiary bar
- **Criminal**: pursued by law enforcement, "beyond a reasonable doubt" standard, can result in imprisonment
- **Civil**: between private parties, "preponderance of the evidence" standard, results in damages/injunctions rather than jail
- **Regulatory**: conducted by a government regulator to verify compliance with a specific regulation (e.g., a data protection authority investigating a breach)
- **Industry standards**: investigations tied to a specific industry framework's requirements (e.g., a PCI forensic investigation after a card-data breach)
- Evidence handling expectations scale with investigation type — a criminal case demands the strictest chain-of-custody discipline since evidence may be challenged in court

## [1.6](#16-security-policy) Develop, document, and implement security policy, standards, procedures, and guidelines

- Documentation hierarchy:
  - **Policy**: high-level, mandatory, senior-management-approved statement of intent ("what and why")
  - **Standard**: mandatory, specific requirement supporting a policy (e.g., minimum key length)
  - **Procedure**: mandatory, step-by-step instructions
  - **Guideline**: recommended, not mandatory — flexible best practice
- Alignment of the security function to business strategy, goals, mission, and objectives is the anchor point — policy that doesn't trace back to a business objective or risk tends to be ignored in practice
- Organizational roles/responsibilities and processes (acquisitions, divestitures, governance committees) must be reflected in policy — e.g., an acquisition creates due-diligence obligations before integrating an unknown IT environment; a divestiture requires a plan for splitting infrastructure and revoking access
- **Due care vs. due diligence**: due care is acting as a reasonably prudent person would (ongoing, "doing the right thing"); due diligence is the research/investigation done *before* acting (e.g., vetting a vendor before signing a contract) — both matter for demonstrating the org wasn't negligent

## [1.7](#17-business-continuity) Identify, analyze, assess, prioritize, and implement Business Continuity (BC) requirements

- **Business Impact Analysis (BIA)**: identifies critical business functions and the impact of their disruption — the foundation continuity planning is built on; produces RTO (max acceptable downtime), RPO (max acceptable data loss), and MTD (absolute outer limit before the impact is unrecoverable)
- **External dependencies**: BC planning must account for third parties (suppliers, utilities, cloud providers) whose own outage can disrupt the organization even if internal systems are fine — a growing focus given cloud/SaaS dependency
- BC planning at Domain 1 is about *identifying and prioritizing* requirements; the detailed BC/DR plan execution and testing lives in Domain 7

## [1.8](#18-personnel-security) Contribute to and enforce personnel security policies and procedures

- **Candidate screening and hiring**: background checks, reference checks, and role-appropriate vetting (depth should scale with the sensitivity of the position)
- **Employment agreements and policy-driven requirements**: NDAs, acceptable use policies, and security responsibilities documented as part of employment terms
- **Onboarding, transfers, and termination**: access should be provisioned to match role at onboarding, adjusted (not just added to) at transfer, and fully revoked at termination — timely deprovisioning is one of the most commonly tested weak points
- **Vendor, consultant, and contractor agreements and controls**: third-party personnel need the same security obligations as employees, formalized contractually, including access review and offboarding

## [1.9](#19-risk-management) Understand and apply risk management concepts

- **Threat and vulnerability identification**: a threat is a potential cause of harm; a vulnerability is a weakness that could be exploited — risk requires both plus an asset of value
- **Risk analysis, assessment, and scope**: qualitative (descriptive scales, fast, good for communication) vs. quantitative (numeric/financial — **SLE = Asset Value × Exposure Factor**, **ALE = SLE × Annualized Rate of Occurrence**) — quantitative is more objective but needs reliable data
- **Risk response/treatment**: mitigate (reduce), transfer (e.g., cybersecurity insurance), avoid (eliminate the risk-creating activity), or accept (documented, authorized retention of the risk)
- **Types of controls**: preventive, detective, corrective (and deterrent, compensating) — know to match control type to the point in the attack/failure timeline it addresses
- **Control assessments**: verifying controls (security and privacy) are both implemented and operating effectively — two distinct questions
- **Continuous monitoring, measurement, and reporting** (internal/external) close the loop between assessed risk and actual control performance
- **Continuous improvement / risk maturity modeling**: risk management itself should mature over time (e.g., moving from ad hoc to managed to optimized practices), not just the controls it produces
- **Risk frameworks**: ISO 31000/27005, NIST RMF (SP 800-37), COBIT, SABSA, PCI — each gives structure to the process above

## [1.10](#110-threat-modeling) Understand and apply threat modeling concepts and methodologies

- **Threat modeling**: systematically identifying, evaluating, and addressing potential threats to a system, ideally *during design* rather than after deployment
- Common methodologies: **STRIDE** (Spoofing, Tampering, Repudiation, Information disclosure, Denial of service, Elevation of privilege — Microsoft's model, oriented around threat categories) and **DREAD** (Damage, Reproducibility, Exploitability, Affected users, Discoverability — a scoring model for prioritizing identified threats); **PASTA** (Process for Attack Simulation and Threat Analysis) is a more risk-centric, business-aligned alternative
- Attacker-centric approaches (e.g., building attack trees) complement asset-centric and software-centric threat modeling — CISSP expects recognition of these approaches and when each is useful, not deep hands-on modeling skill

## [1.11](#111-supply-chain-risk) Apply supply chain risk management (SCRM) concepts

- Risks associated with acquiring products/services from suppliers: **product tampering, counterfeits, and implants** (malicious hardware/firmware inserted somewhere in the supply chain) are explicit exam topics — supply-chain compromise is treated as a first-class risk category, not an edge case
- Risk mitigations: third-party assessment and ongoing monitoring, minimum security requirements and SLAs written into contracts, and emerging hardware-trust mechanisms like **silicon root of trust** and **physically unclonable functions (PUFs)**
- **Software Bill of Materials (SBOM)**: a machine-readable inventory of a software product's components (including open-source dependencies), used to quickly assess exposure when a vulnerability is disclosed in a widely used library — increasingly required contractually and by regulation
- SCRM extends beyond the direct (first-tier) supplier to sub-tier/fourth-party risk, similar to the third/fourth-party distinction used elsewhere in security management

## [1.12](#112-security-awareness) Establish and maintain a security awareness, education, and training program

- **Awareness** (broad, ongoing reinforcement for all staff) vs. **training** (role-specific, deeper skill-building) — distinct programs with distinct goals
- Methods to increase engagement: social-engineering/phishing simulations, security champions programs, and gamification
- **Periodic content review** must explicitly cover emerging technologies and trends — the outline calls out cryptocurrency, AI, and blockchain by name, reflecting how quickly awareness content can go stale if not refreshed
- **Program effectiveness evaluation**: measure outcomes (e.g., phishing click/report rates over time), not just completion rates — a training program with 100% completion and no behavior change hasn't reduced risk
