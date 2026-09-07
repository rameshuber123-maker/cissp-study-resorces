# [Domain-6](#domain-6-security-assessment-and-testing) **Security Assessment and Testing**

> 🤖 [AI Tutor](https://edureify.com/certification/exam/cissp) · 🎓 [Training](https://edureify.com/certification/cybersecurity/cissp/training) · 📝 [Practice Test](https://edureify.com/certification/cybersecurity/cissp/practice-test) · 🎯 [Mock Exam](https://edureify.com/certification/cybersecurity/cissp/mock-exam) · 📊 [Readiness Test](https://edureify.com/certification/cybersecurity/cissp/readiness-test) · 📄 [Cheat Sheet](https://edureify.com/certification/cybersecurity/cissp/cheat-sheet) · 📖 [Study Guide](https://edureify.com/certification/cybersecurity/cissp/study-guide)

- Domain 6 carries a **12% weighting** and covers how an organization verifies its controls actually work — through testing, data collection, analysis, and formal audit
- Core distinction to hold onto throughout: *testing* verifies controls at a point in time; *auditing* independently verifies the overall program/process, often for compliance purposes

## [6.1](#61-assessment-strategies) Design and validate assessment, test, and audit strategies

- Strategies should specify **who performs the assessment**:
  - **Internal**: performed by staff within the organization's control — fastest, most context-aware, but less independent
  - **External**: performed by a party outside the organization but engaged directly (e.g., a hired pentest firm) — more independence than internal
  - **Third-party**: performed by a party fully outside enterprise control (e.g., a customer's auditor, or a regulator) — highest independence
- And **where the assessed environment lives**: on-premises, cloud, or hybrid — cloud environments often require coordinating with the provider (permitted testing windows, shared-responsibility scoping) before testing

## [6.2](#62-security-control-testing) Conduct security control testing

- **Vulnerability assessment**: identifies known weaknesses (often via automated scanning) — breadth-focused, doesn't typically exploit findings
- **Penetration testing**: actively attempts to exploit weaknesses to demonstrate real-world impact
  - **Red team**: offense, simulating an attacker
  - **Blue team**: defense, detecting/responding to the red team
  - **Purple team**: collaborative exercise where red and blue actively share findings in real time to improve detection, rather than working in isolation
- **Log reviews**: manual or automated examination of system/security logs for anomalies or evidence of compromise
- **Synthetic transactions/benchmarks**: scripted, simulated user activity used to continuously validate that a system/application is behaving (and performing) as expected
- **Code review and testing**: manual or automated examination of source code for security flaws (ties to Domain 8's SAST/DAST)
- **Misuse case testing**: deliberately testing how a system behaves under *intended misuse* (the inverse of a normal "use case"), to validate it fails safely
- **Coverage analysis**: measures how much of a system/codebase was actually exercised by testing — low coverage means real gaps may remain untested
- **Interface testing**: validating security across UI, network interfaces, and APIs — API testing has grown significantly as microservice architectures expose far more programmatic interfaces (see Domain 3.5)
- **Breach attack simulations**: automated, repeatable simulation of real attacker techniques (often mapped to frameworks like MITRE ATT&CK) to continuously validate detection/response capability, rather than a one-time annual pentest
- **Compliance checks**: automated or manual verification against a specific regulatory/framework baseline

## [6.3](#63-collect-security-process-data) Collect security process data (e.g., technical and administrative)

- **Account management data**: creation, modification, and review records that support access-review assessments (Domain 5.5)
- **Management review and approval**: documented evidence that leadership actually reviewed and approved security decisions — auditors look for this paper trail as much as for the underlying control
- **Key Performance Indicators (KPIs) and Key Risk Indicators (KRIs)**: KPIs measure how well the program is performing against its goals; KRIs provide early warning of rising risk — both should be collected continuously, not just at audit time
- **Backup verification data**: evidence that backups aren't just being taken but have actually been successfully *restored/tested* — an untested backup is not a reliable control
- **Training and awareness data**: completion rates and effectiveness metrics (Domain 1.12)
- **Disaster Recovery (DR) and Business Continuity (BC) data**: results from DR/BC tests (Domain 7) feed directly into this domain's assessment process

## [6.4](#64-analyze-test-output) Analyze test output and generate report

- **Remediation**: findings should be tracked to actual fix, with clear ownership and timelines proportional to severity
- **Exception handling**: when a finding can't be remediated on the standard timeline, a formal, time-bound, approved exception process should apply — undocumented, indefinite exceptions are a common audit failure
- **Ethical disclosure**: when testing (especially external/third-party) uncovers a vulnerability, findings should be disclosed responsibly — to the affected organization first, with a reasonable remediation window before any broader disclosure, following the tester's/organization's coordinated disclosure policy

## [6.5](#65-security-audits) Conduct or facilitate security audits

- Same internal/external/third-party and on-premises/cloud/hybrid framing as 6.1 applies to formal audits — an audit's credibility and applicability depend heavily on who performed it and its scope
- The security team's role is often to *facilitate* audits (providing evidence, coordinating access for auditors) as much as to conduct them directly, especially for external/third-party and regulatory audits where independence from the audited function is required
