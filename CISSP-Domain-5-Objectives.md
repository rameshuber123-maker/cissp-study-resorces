# [Domain-5](#domain-5-identity-and-access-management) **Identity and Access Management (IAM)**

> 🤖 [AI Tutor](https://edureify.com/certification/exam/cissp) · 🎓 [Training](https://edureify.com/certification/cybersecurity/cissp/training) · 📝 [Practice Test](https://edureify.com/certification/cybersecurity/cissp/practice-test) · 🎯 [Mock Exam](https://edureify.com/certification/cybersecurity/cissp/mock-exam) · 📊 [Readiness Test](https://edureify.com/certification/cybersecurity/cissp/readiness-test) · 📄 [Cheat Sheet](https://edureify.com/certification/cybersecurity/cissp/cheat-sheet) · 📖 [Study Guide](https://edureify.com/certification/cybersecurity/cissp/study-guide)

- Domain 5 carries a **13% weighting** and covers the full identity lifecycle: proving who someone (or something) is, deciding what they can do, and managing that relationship over time
- Increasingly, "identity" extends beyond people to devices and services — a theme woven throughout this domain

## [5.1](#51-control-physical-and-logical-access) Control physical and logical access to assets

- Access control applies uniformly across asset types: **information, systems, devices, facilities, applications, and services** — the same identification/authentication/authorization discipline should govern a server room door as much as a database record
- **Groups and Roles**: assigning access via groups/roles rather than per-individual simplifies management and audit, and is foundational to RBAC (below)

## [5.2](#52-authentication-strategy) Design identification and authentication strategy (e.g., people, devices, and services)

- **AAA (Authentication, Authorization, and Accounting)**: the umbrella framework — note this reuses the same AAA concept from Domain 1.2, now applied architecturally
- **Multi-factor authentication (MFA)**: combines two or more factor categories — something you know (password), something you have (token/device), something you are (biometric); using two passwords is *not* MFA since both come from the same category
- **Passwordless authentication**: replaces passwords with possession/biometric-based factors (e.g., passkeys/FIDO2 hardware or platform authenticators) — reduces phishing and credential-stuffing risk since there's no shared secret to steal
- **Session management**: securely establishing, maintaining, and terminating an authenticated session (timeout policies, secure session tokens, protection against session hijacking/fixation)
- **Registration, proofing, and establishment of identity**: verifying a claimed identity is genuine *before* issuing credentials — identity proofing rigor should scale with the sensitivity of what the identity will access
- Authentication strategy must explicitly cover non-human identities — **devices** (e.g., certificate-based device authentication) and **services** (e.g., service-to-service authentication via API keys, mutual TLS, or workload identity) — not just human users

## [5.3](#53-federated-identity) Federated identity with a third-party service

- **Federated Identity Management (FIM)**: allows a user authenticated by one organization (the identity provider) to access resources at another organization (the relying party) without a separate set of credentials — common protocols include SAML, OAuth 2.0, and OpenID Connect
- Federation shifts authentication trust to the identity provider, which reduces password sprawl but also means a compromise at the identity provider can cascade to every relying party that trusts it — a key risk trade-off to recognize

## [5.4](#54-authorization-mechanisms) Implement and manage authorization mechanisms

- **Role-Based Access Control (RBAC)**: access tied to a role, not an individual — efficient at scale, but can suffer from "role explosion" or role/permission creep if not periodically reviewed
- **Rule-based access control**: access decisions driven by predefined rules (e.g., firewall ACLs, time-of-day restrictions) rather than roles or identity attributes directly
- **Mandatory Access Control (MAC)**: access decisions are made centrally based on classification/clearance labels; users can't alter permissions themselves — used in high-security/government contexts (ties back to Bell-LaPadula/Biba in Domain 3.2)
- **Discretionary Access Control (DAC)**: the resource owner decides who gets access — flexible, but harder to enforce consistent policy at scale
- **Attribute-Based Access Control (ABAC)**: access decisions evaluate multiple attributes (user, resource, environment, action) via policy — the most flexible/fine-grained model, well suited to zero-trust and dynamic cloud environments
- **Risk-based access control**: adjusts access decisions dynamically based on real-time risk signals (e.g., unusual location, device posture) — commonly paired with adaptive/step-up MFA
- **Access policy enforcement**: the **Policy Decision Point (PDP)** evaluates whether a request should be allowed based on policy; the **Policy Enforcement Point (PEP)** is where that decision is actually enforced — a core architectural pattern in modern zero-trust and ABAC implementations

## [5.5](#55-provisioning-lifecycle) Manage the identity and access provisioning lifecycle

- **Account access review**: periodic recertification of user, system, and service account access to confirm it's still appropriate — a key detective control against privilege creep
- **Provisioning and deprovisioning**: on/offboarding and transfers should trigger access changes automatically where possible; deprovisioning delay is one of the most commonly exploited real-world gaps (echoes Domain 1.8)
- **Role definition and transition**: as people move to new roles, old access should be actively removed, not just new access added — otherwise privilege accumulates over a career ("privilege creep")
- **Privilege escalation**: legitimate elevated-access mechanisms (e.g., `sudo`) must be tightly controlled and *audited* — every use of elevated privilege should be logged and reviewable, distinguishing authorized escalation from an attacker's attempt to gain higher privileges
- **Service account management**: non-human accounts used by applications/automation are easy to overlook in access reviews, often over-privileged, and rarely have passwords rotated — a disproportionately common source of real-world breaches
- Provisioning models span **on-premises, cloud, and hybrid** environments, each with different native IAM tooling that must still be governed under one consistent policy

## [5.6](#56-authentication-systems) Implement authentication systems

- **Credential management systems**: password vaults and secrets managers securely store and control access to credentials, especially for shared/service accounts, reducing hard-coded or written-down credentials
- **Single Sign-On (SSO)**: one authentication grants access to multiple systems — improves usability and centralizes authentication security, but also centralizes risk (compromise of the SSO identity compromises everything it protects)
- **Just-In-Time (JIT) access**: grants elevated or specific access only for the duration it's needed, then automatically revokes it — reduces the standing attack surface of always-on privileged accounts, a growing best practice alongside zero trust
