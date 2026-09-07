# [Domain-3](#domain-3-security-architecture-and-engineering) **Security Architecture and Engineering**

> 🤖 [AI Tutor](https://edureify.com/certification/exam/cissp) · 🎓 [Training](https://edureify.com/certification/cybersecurity/cissp/training) · 📝 [Practice Test](https://edureify.com/certification/cybersecurity/cissp/practice-test) · 🎯 [Mock Exam](https://edureify.com/certification/cybersecurity/cissp/mock-exam) · 📊 [Readiness Test](https://edureify.com/certification/cybersecurity/cissp/readiness-test) · 📄 [Cheat Sheet](https://edureify.com/certification/cybersecurity/cissp/cheat-sheet) · 📖 [Study Guide](https://edureify.com/certification/cybersecurity/cissp/study-guide)

- Domain 3 carries a **13% weighting** and is one of the most technically dense domains — covering secure design, system types, cryptography, and physical/facility security
- The domain rewards *engineering* security in from the start (secure-by-design) rather than bolting it on after a system is built

## [3.1](#31-secure-design-principles) Research, implement and manage engineering processes using secure design principles

- Core secure design principles (know each by name and what it prevents):
  - **Threat modeling**: identify threats during design (see Domain 1.10)
  - **Least privilege**: grant only the access needed to perform a function, nothing more
  - **Defense in depth**: layer multiple controls so no single failure is catastrophic
  - **Secure defaults**: systems should ship in their most secure reasonable configuration, requiring deliberate action to loosen
  - **Fail securely**: when a control fails, it should fail closed (deny) rather than fail open (allow), unless safety requires otherwise
  - **Segregation of Duties (SoD)**: split sensitive tasks across multiple people so no one person can complete a critical/fraud-prone process alone
  - **Keep it simple and small**: reduced complexity and attack surface are easier to secure and audit
  - **Zero trust ("never trust, always verify")**: no implicit trust based on network location; every request is authenticated, authorized, and continuously validated — a major architectural shift from perimeter-based trust models
  - **Privacy by design**: build privacy protections into a system's architecture from the start, not as an add-on
  - **Shared responsibility**: in cloud models, security is divided between provider and customer depending on service model (IaaS/PaaS/SaaS) — misunderstanding this boundary is a common real-world breach cause
  - **Secure Access Service Edge (SASE)**: converges networking and security (SD-WAN, zero trust network access, CASB, secure web gateway) into a single cloud-delivered service — a modern architecture pattern for distributed/remote workforces

## [3.2](#32-security-models) Understand the fundamental concepts of security models (e.g., Biba, Star Model, Bell-LaPadula)

- **Bell-LaPadula**: confidentiality-focused model ("no read up, no write down") — prevents a lower-clearance subject from reading higher-classified data, and a higher-clearance subject from writing down to a lower classification (preventing leakage)
- **Biba**: integrity-focused model, the conceptual mirror of Bell-LaPadula ("no write up, no read down") — prevents contamination of high-integrity data by lower-integrity sources
- **Star (\*) Property**: refers to the "write" rules within these models (e.g., the \*-property in Bell-LaPadula is the "no write down" rule) — a frequently confused exam point since "Star Model" isn't a separate model but a property within Bell-LaPadula
- These formal models underpin *why* certain access control and classification rules exist, even though most real systems implement simplified, practical versions rather than the full formal model

## [3.3](#33-select-controls) Select controls based upon systems security requirements

- Control selection should trace back to a documented requirement (regulatory, contractual, or risk-based) — the exam consistently rewards answers that map a control to an actual stated requirement over answers that are just "more secure" in the abstract
- Requirements differ meaningfully by system type (see 3.4/3.5) — a control appropriate for a traditional server may be impractical or irrelevant for an embedded or IoT device

## [3.4](#34-security-capabilities-of-is) Understand security capabilities of Information Systems (IS) (e.g., memory protection, Trusted Platform Module (TPM), encryption/decryption)

- **Memory protection**: hardware/OS mechanisms (e.g., address space layout randomization, execution prevention) that stop one process from reading/corrupting another's memory, and mitigate classes of exploits like buffer overflows
- **Trusted Platform Module (TPM)**: a dedicated hardware chip that securely generates/stores cryptographic keys and can attest to a system's boot integrity — underpins features like full-disk encryption key protection and secure boot
- **Encryption/decryption capability**: built-in hardware acceleration and secure key storage (e.g., hardware security modules) reduce the performance and security trade-offs of encrypting data broadly

## [3.5](#35-assess-and-mitigate-vulnerabilities) Assess and mitigate the vulnerabilities of security architectures, designs, and solution elements

- Know the security implications and typical controls for each system/architecture type:
  - **Client-based / server-based systems**: traditional endpoint and server hardening
  - **Database systems**: access control at the row/column level, encryption, injection-attack defenses
  - **Cryptographic systems**: key management is usually the weakest link, not the algorithm itself
  - **Industrial Control Systems (ICS)/SCADA**: often prioritize availability and safety over confidentiality; legacy protocols may lack authentication — typically isolated via network segmentation rather than patched like IT systems
  - **Cloud-based systems (IaaS/PaaS/SaaS)**: shared responsibility boundary shifts with each model — customer owns more of the stack in IaaS, less in SaaS
  - **Distributed systems**: consistency, availability, and partition tolerance trade-offs (CAP theorem) affect how failures propagate
  - **Internet of Things (IoT)**: often resource-constrained, hard to patch, and deployed at scale — segmentation and lifecycle management are key mitigations
  - **Microservices/APIs**: expanded attack surface from many small, independently deployed services communicating over APIs — API authentication/authorization and rate limiting are critical
  - **Containerization**: shares the host OS kernel, so container escape and image provenance (trusted, scanned base images) are primary concerns
  - **Serverless**: the provider manages the runtime entirely; security shifts almost fully to code-level (function) security and IAM permission scoping
  - **Embedded systems**: often long-lived, hard to update, and resource constrained — security is largely designed in upfront since it's difficult to retrofit
  - **High-Performance Computing / Edge computing**: distribute processing closer to data sources or scale massively — expand the physical and network attack surface across many more locations
  - **Virtualized systems**: hypervisor security and VM escape are primary concerns; strong isolation between tenants matters especially in multi-tenant environments

## [3.6](#36-cryptographic-solutions) Select and determine cryptographic solutions

- **Cryptographic life cycle**: keys and algorithms are not "set and forget" — plan for eventual algorithm deprecation and key rotation from the start
- **Cryptographic methods**:
  - **Symmetric**: same key encrypts and decrypts (e.g., AES) — fast, but key distribution is the challenge
  - **Asymmetric**: public/private key pairs (e.g., RSA, ECC) — solves key distribution, but much slower; commonly used to exchange a symmetric session key
  - **Elliptic curve cryptography (ECC)**: achieves equivalent security to RSA with much smaller key sizes — widely used in constrained/mobile environments
  - **Quantum/post-quantum cryptography**: a sufficiently powerful quantum computer could break current RSA/ECC via Shor's algorithm; NIST has standardized post-quantum algorithms (**FIPS 203/204/205**) designed to resist quantum attack, and organizations are beginning "crypto-agility" and migration planning now even though large-scale cryptographically-relevant quantum computers don't yet exist
- **Public Key Infrastructure (PKI)**: the certificate authorities, registration authorities, and trust chain that bind public keys to identities; **Quantum Key Distribution (QKD)** is an emerging, physics-based (not computationally-based) method of securely exchanging keys, distinct from post-quantum algorithms which are still computational
- **Key management practices**: generation, distribution, storage, rotation, and destruction — most real-world cryptographic failures stem from poor key management, not broken algorithms
- **Digital signatures and certificates**: provide nonrepudiation and integrity by combining hashing with asymmetric encryption (signing a hash of the message with the sender's private key, verifiable with their public key)

## [3.7](#37-cryptanalytic-attacks) Understand methods of cryptanalytic attacks

- **Brute force**: try every possible key — mitigated by sufficient key length
- **Ciphertext-only**: attacker has only encrypted data to work with — hardest attack scenario for the attacker
- **Known-plaintext**: attacker has matching plaintext/ciphertext pairs
- **Chosen-ciphertext**: attacker can get chosen ciphertexts decrypted (e.g., via a system that leaks information through error responses)
- **Frequency analysis**: exploits statistical patterns in language — effective against classical/simple substitution ciphers, not modern algorithms
- **Implementation attacks** (attack the implementation, not the math):
  - **Side-channel**: infers key material from indirect signals (power consumption, electromagnetic emissions)
  - **Fault injection**: deliberately induces errors (e.g., voltage glitching) to reveal key material through the resulting incorrect output
  - **Timing attacks**: infers information from how long an operation takes to complete
- **Protocol/credential attacks**: **Man-in-the-Middle (MITM)** (intercepting/altering communication between two parties who believe they're communicating directly), **pass-the-hash** (reusing a captured password hash to authenticate without knowing the plaintext password), **Kerberos exploitation** (e.g., "Golden Ticket"/"Silver Ticket" attacks against Kerberos authentication), and **ransomware** (which weaponizes legitimate encryption against the victim's own data)

## [3.8](#38-site-and-facility-design) Apply security principles to site and facility design

- Physical security follows the same layered/defense-in-depth logic as logical security: site selection, perimeter, building, and interior layers each add protection
- Considerations include crime rate and natural disaster risk of the location, proximity to emergency services, and visibility/deterrence of the site itself

## [3.9](#39-facility-security-controls) Design site and facility security controls

- **Utilities and HVAC**: environmental controls that protect equipment from heat/humidity damage and support uptime
- **Environmental issues**: natural disasters (flood, earthquake, fire) and man-made hazards (nearby industrial risk, civil unrest) factor into site risk assessment
- **Fire prevention, detection, and suppression**: appropriate suppression method matters — water damages electronics, so data centers typically use clean-agent gas suppression or pre-action sprinkler systems
- **Power**: redundant feeds, UPS, and generator backup protect availability
- **Specialized areas**: wiring closets/IDFs, server rooms/data centers, media storage facilities, evidence storage (requires strict chain-of-custody controls), and restricted/work-area security — each needs access controls proportional to what it protects

## [3.10](#310-information-system-lifecycle) Manage the information system lifecycle

- Standard systems engineering lifecycle stages: **Stakeholder needs and requirements → Requirements analysis → Architectural design → Development/implementation → Integration → Verification and validation → Transition/deployment → Operations and maintenance/sustainment → Retirement/disposal**
- Security should be integrated at every stage, not appended at "verification and validation" — a recurring exam theme (shift security left)
- Retirement/disposal connects back to Domain 2's asset retention and data destruction requirements — a system's lifecycle isn't complete until its data and hardware are properly sanitized/disposed of
