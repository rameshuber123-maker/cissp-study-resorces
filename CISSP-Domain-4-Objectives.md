# [Domain-4](#domain-4-communication-and-network-security) **Communication and Network Security**

> 🤖 [AI Tutor](https://edureify.com/certification/exam/cissp) · 🎓 [Training](https://edureify.com/certification/cybersecurity/cissp/training) · 📝 [Practice Test](https://edureify.com/certification/cybersecurity/cissp/practice-test) · 🎯 [Mock Exam](https://edureify.com/certification/cybersecurity/cissp/mock-exam) · 📊 [Readiness Test](https://edureify.com/certification/cybersecurity/cissp/readiness-test) · 📄 [Cheat Sheet](https://edureify.com/certification/cybersecurity/cissp/cheat-sheet) · 📖 [Study Guide](https://edureify.com/certification/cybersecurity/cissp/study-guide)

- Domain 4 carries a **13% weighting**, covering everything from fundamental network models to modern software-defined and cloud networking
- The 2024 outline pushed this domain further into current infrastructure patterns — SD-WAN/SDN, zero trust micro-segmentation, and cloud VPCs sit alongside the classic OSI/TCP-IP fundamentals

## [4.1](#41-secure-network-architecture) Assess and implement secure design principles in network architectures

- **OSI vs. TCP/IP models**: know both — OSI's 7 layers are the conceptual/teaching reference, TCP/IP's 4 layers reflect what's actually implemented; be able to map common protocols and attacks to their layer
- **IPv4 vs. IPv6**: IPv6 expands the address space and has built-in support for IPSec, but introduces its own security considerations (e.g., new address types — unicast, broadcast/multicast, anycast — and transition-period dual-stack risks)
- **Secure protocols**: IPSec (network-layer VPN encryption), SSH (secure remote administration), TLS (the modern successor to SSL — always specify TLS, as SSL is deprecated/insecure) — know what layer each secures and what it replaces
- **Multilayer protocol implications**: protocols that operate across multiple OSI layers can complicate security inspection and filtering, since a firewall inspecting only one layer may miss threats operating at another
- **Converged protocols**: iSCSI (storage over IP), VoIP (voice over IP), InfiniBand over Ethernet, and Compute Express Link (CXL) — converging traffic types onto shared IP infrastructure increases efficiency but also increases the blast radius of a network compromise
- **Transport architecture**: topology, and the separation of data/control/management planes — a recurring zero-trust and SDN concept, since compromising the control plane can compromise the whole network's forwarding behavior
- **Performance metrics**: bandwidth, latency, jitter, throughput, signal-to-noise ratio — availability and quality-of-service considerations that intersect with security (e.g., a DoS attack primarily degrades these metrics)
- **Traffic flows**: north-south (client-to-server, in/out of a data center) vs. east-west (server-to-server, within a data center) — modern architectures increasingly need east-west inspection/segmentation since traditional perimeter defenses only watch north-south traffic

## [4.2](#42-secure-network-components) Secure network components

- **Segmentation approaches**:
  - **Physical**: in-band, out-of-band, and air-gapped networks — air-gapping is the strongest isolation but sacrifices connectivity/convenience
  - **Logical**: VLANs, VPNs, virtual routing and forwarding (VRF), virtual domains — separate traffic without separate physical infrastructure
  - **Micro-segmentation**: fine-grained segmentation (often via network overlays/encapsulation and distributed firewalls/IDS/IPS) that enforces zero-trust principles down to the individual workload level, rather than just at network perimeters
- **Edge networks**: ingress/egress points and peering relationships — the boundary where an org's network meets external providers/internet exchanges
- **Wireless networks**: Bluetooth, Wi-Fi, Zigbee, and satellite — each has distinct range, power, and security-protocol considerations (e.g., WPA3 for Wi-Fi)
- **Cellular/mobile networks**: 4G and 5G — 5G's network slicing and edge-compute integration introduce new architectural considerations beyond simple mobile data connectivity
- **Content Distribution Networks (CDN)**: cache/serve content from geographically distributed edge nodes — improves performance and absorbs some DoS traffic, but adds a third-party trust dependency
- **Software-Defined Networks (SDN)**: separates the control plane from the data plane, managed via APIs — includes SD-WAN and network functions virtualization (NFV), enabling centralized, programmable network security policy
- **Virtual Private Cloud (VPC)**: a logically isolated network within a public cloud provider — the cloud-native equivalent of a traditional segmented network, configured via provider-specific security groups/network ACLs
- **Monitoring and management**: network observability, traffic flow/shaping, capacity management, and fault detection/handling — visibility is a prerequisite for detecting anomalies
- **Operation of infrastructure**: redundant power, warranty, and support agreements — availability depends on operational, not just architectural, decisions
- **Transmission media**: physical security of cabling and signal propagation quality — e.g., fiber is harder to tap covertly than copper, but physical access to any medium is still a risk
- **Network Access Control (NAC)**: enforces device compliance (patch level, endpoint security posture) before granting network access — physical and virtual implementations
- **Endpoint security (host-based)**: complements network controls since not all threats can be caught in transit — EDR/host firewalls/host IDS
- **Voice, video, and collaboration**: conferencing platforms are a network security concern in their own right — eavesdropping, unauthorized meeting access ("zoom-bombing" style incidents), and recording/data-retention implications
- **Remote access**: securing network administrative functions performed remotely is especially sensitive — high-privilege access deserves stronger controls (MFA, jump hosts, session recording) than standard remote user access
- **Data communications**: backhaul networks and satellite links used to connect distributed sites, sometimes over higher-latency or less-secure paths that need additional protection
- **Third-party connectivity**: telecom providers and hardware support vendors often have network access as part of their service — that access needs the same governance as any third party (see Domain 1.11/3.5)

## [4.3](#43-secure-communication-channels) Implement secure communication channels according to design

- Selecting and correctly implementing the secure protocols and segmentation strategies above for a specific communication need — e.g., choosing site-to-site IPSec vs. a cloud provider's native VPC peering vs. an SD-WAN overlay depends on the actual trust boundaries and performance requirements involved, not a one-size-fits-all default
- A recurring exam theme: the "most secure" protocol on paper (e.g., full network isolation) is often the wrong answer if it breaks a legitimate, required business communication path — the design must balance security with the communication's actual purpose
