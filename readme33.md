<div align="center">

<img src="https://raw.githubusercontent.com/giridharan-veda/threatforge-physical-iot/main/blitz-banner.svg" width="100%" alt="Blitz Enterprise — Autonomous IoT/OT Security Assessment Platform">

# Blitz Enterprise

### Autonomous IoT/OT Security Assessment Platform

**Continuous, on-premises, evidence-backed offensive security testing for connected environments — with a verifiable safety boundary between AI decision and every action.**

[![Edition](https://img.shields.io/badge/Edition-Enterprise-blue)](#licensing)
[![Deployment](https://img.shields.io/badge/Deployment-On--Premise%20%7C%20Air--Gapped-informational)](#deployment-options)
[![Modules](https://img.shields.io/badge/Modules-154-blueviolet)](#module-coverage)
[![Categories](https://img.shields.io/badge/Categories-28-blueviolet)](#module-coverage)
[![LLM](https://img.shields.io/badge/LLM-Local%20%C2%B7%20Air--Gapped-purple)](#ares-ai-engine)
[![License](https://img.shields.io/badge/License-Perpetual%20Commercial-red)](#licensing)

**[ REQUEST A DEMO ](#contact)**  •  **[ REQUEST A QUOTE ](#contact)**  •  **[ SECURITY DISCLOSURE ](#contact)**

*Commercial Edition — for security teams, consultancies, regulated industries, and critical infrastructure.*

</div>

---

## Executive Summary

Blitz is an autonomous IoT/OT security assessment platform that discovers, classifies, plans, executes, and validates offensive security testing against connected devices — continuously, on-premises, and with an auditable safety boundary between the AI decision layer and every action taken against a target.

The platform is purpose-built for environments where manual penetration testing is insufficient: distributed IoT/OT fleets, regulated industries, air-gapped networks, and organizations required to demonstrate **continuous security assurance** rather than point-in-time compliance.

| Capability | Description |
| :---: | :---: |
| **Autonomous Discovery** | Continuous asset identification across 28 protocol categories |
| **State-Driven Planning** | On-premises AI selects the next module based on device state |
| **154 Attack Modules** | Every module has documented preconditions, side effects, and safety classification |
| **Multi-Condition Safety Gate** | Scope, capability, and approval enforced before any action executes |
| **Evidence-Backed Findings** | Strict separation between *attempted* and *proven* results |
| **Automatic Re-Validation** | Remediated findings are re-tested without operator intervention |
| **Complete Audit Trail** | Every decision, authorization, and execution is logged for compliance |
| **Air-Gapped Operation** | No external telemetry, no cloud dependency, no per-token costs |

**Deployment:** Self-hosted via Docker Compose or Kubernetes. No external network calls required for operation.

**Licensing:** Perpetual commercial license. Enterprise, Government, and Academic tiers available.

---

## Table of Contents

| Section | Description |
| :---: | :---: |
| [Business Case](#business-case) | Why continuous autonomous assessment matters |
| [Reference Architecture](#reference-architecture) | System components and data flow |
| [Security & Compliance](#security--compliance) | Posture, frameworks, and audit capabilities |
| [Deployment Options](#deployment-options) | On-premises, air-gapped, and VPC deployments |
| [Operational Lifecycle](#operational-lifecycle) | The 12-stage assessment pipeline |
| [Module Coverage](#module-coverage) | 154 modules across 28 categories |
| [Ares AI Engine](#ares-ai-engine) | Decision layer, training, and retraining |
| [Integrations](#integrations) | SIEM, SOAR, ticketing, CI/CD, and API |
| [Performance & Benchmarks](#performance--benchmarks) | Measured performance with methodology |
| [Licensing](#licensing) | Commercial tiers and volume licensing |
| [Support & SLA](#support--sla) | Support tiers and response commitments |
| [Professional Services](#professional-services) | Deployment, training, and custom modules |
| [Procurement Information](#procurement-information) | Security review, legal, and vendor documentation |
| [About ApexPredator Security & Labs](#about-apexpredator-security--labs) | Company background and team |
| [Contact](#contact) | Sales, support, and security disclosures |

---

## Business Case

### The Operational Reality

Enterprise security programs have matured significantly over the past two decades. Endpoint detection, network monitoring, identity management, and cloud security posture tooling now cover traditional IT infrastructure with reasonable effectiveness.

IoT and OT environments have not received the same investment, for three structural reasons:

| Reason | Impact |
| :---: | :---: |
| **Asset invisibility** | Most organizations cannot enumerate their connected devices, let alone firmware versions, exposed services, or default configurations |
| **Lifecycle mismatch** | IoT/OT devices frequently have no vendor-supported update path. Known vulnerabilities persist for 10–15 years |
| **Assessment difficulty** | Safe testing requires protocol-specific expertise and hardware interfaces that general-purpose tooling does not provide |

The result is a persistent, unmeasured risk surface that sits adjacent to — and often on the same network as — systems that do receive rigorous assessment.

### The Cost of Point-in-Time Assessment

Annual penetration tests are effective at identifying risk at a moment in time. They are poorly suited to environments that change continuously.

| Failure Mode | Consequence |
| :---: | :---: |
| New devices deployed without security review | Unknown attack surface grows silently |
| Firmware updated — or not — without validation | Known CVEs persist undetected |
| Default credentials re-introduced during provisioning | Trivial compromise path restored |
| Network segmentation drifts | Lateral movement becomes possible |
| Remediation applied but rarely re-verified | False sense of resolution |

Continuous autonomous assessment addresses these gaps by applying the same rigor as a manual engagement, on a schedule you define, against a scope you control, with an auditable boundary between decision and action.

### Where Blitz Fits

| Deployment Pattern | Use Case | Organization Profile |
| :---: | :---: | :---: |
| **Continuous assurance** | Ongoing assessment of IoT/OT fleets | Organizations with 100+ connected devices |
| **Pre-engagement scoping** | Rapid asset discovery before on-site testing | Consultancies and pentest firms |
| **Firmware validation** | Assessing own products before release | Manufacturers and OEMs |
| **Compliance evidence** | Generating audit-ready assessment artifacts | Regulated industries |
| **Lab and training** | Realistic offensive security environments | Academic and research institutions |

---

## Reference Architecture

Blitz is composed of five discrete services, each with a single responsibility. This separation is deliberate: it ensures the AI decision layer has no direct network access, the execution layer has no autonomous decision authority, and every action passes through an auditable enforcement point.

### Component Overview

| Component | Function | Network Boundary |
| :---: | :---: | :---: |
| **Operator Console** | Human control plane — launch assessments, review proposals, approve or deny actions, monitor progress | User-facing |
| **Ares Agent** | AI orchestration — profiles devices, plans assessments, selects modules | No direct network access |
| **Ares Bridge** | Capability gateway — enforces multi-condition authorization | Enforcement boundary |
| **Ollama Runtime** | Local model server — hosts the fine-tuned `ares` model | Internal only |
| **Blitz Core** | Execution engine — runs approved modules, collects evidence, exposes APIs | Target-facing |
| **Persistent State** | Durable store — devices, jobs, findings, incidents, audit history | Internal only |

### Enforcement Model

Every action taken against a target device passes through three distinct stages:

| Stage | Actor | Responsibility |
| :---: | :---: | :---: |
| **Proposal** | Ares Agent | Decides what should happen next, based on device state |
| **Authorization** | Ares Bridge | Validates the proposal against scope, capability, and safety rules |
| **Execution** | Blitz Core | Runs only what was authorized, with full evidence capture |

Ares has no ability to execute. Blitz Core has no ability to decide. The Bridge has no ability to run anything itself.

### Data Flow

```
Operator Console
    ↓
Ares Agent  ────────► Ares Bridge  ────────► Ollama Runtime
    │                     │                        │
    ▼                     ▼                        │
Blitz Core  ◄─────────────┘                        │
    │                                              │
    ├──────► Target Devices                        │
    ├──────► Persistent State (audit + findings)   │
    └──────► Live Event Stream ◄───────────────────┘
                    │
                    ▼
              Operator Console
```

### Network Ports

| Service | Port | Protocol | Exposure |
| :---: | :---: | :---: | :---: |
| Blitz Core API | 8088 | REST + WebSocket | Internal |
| Ares Bridge | 8089 | MCP over HTTP | Internal |
| Ares Agent | 9010 | MCP over HTTP | Internal |
| Ollama Runtime | 11435 | HTTP | Localhost only |

No service exposes itself to external networks. All inter-service communication occurs over an internal Docker network or equivalent.

### Architecture Diagram

<img src="https://github.com/giridharan-veda/threatforge-physical-iot/blob/main/blitz-architecture.svg" width="100%" alt="Blitz Enterprise architecture">

---

## Security & Compliance

### Security Posture

Blitz is designed for environments with strict security review requirements.

| Area | Implementation |
| :---: | :---: |
| **Data residency** | All processing occurs on customer-controlled hardware. No external network calls during operation |
| **Telemetry** | None. No metrics, usage data, or crash reports transmitted externally |
| **Model inference** | Local via Ollama. No prompts, device context, or results leave the deployment |
| **Authentication** | Integrates with existing identity providers (OIDC, SAML) |
| **Authorization** | Role-based access control for console actions and API endpoints |
| **Audit logging** | Every action, decision, authorization, and result logged with timestamps and actor attribution |
| **Encryption in transit** | TLS 1.3 for all inter-service and operator communications |
| **Encryption at rest** | Optional — compatible with LUKS, BitLocker, or cloud provider volume encryption |
| **Dependency management** | SBOM published for every release. Dependencies pinned and scanned |
| **Vulnerability disclosure** | Coordinated disclosure policy published. Security contact monitored |

### Compliance Alignment

Blitz supports evidence generation for the following frameworks. Mapping documentation is included with enterprise licenses.

| Framework | Coverage |
| :---: | :---: |
| **IEC 62443** | Industrial automation and control systems security — assessment evidence for zones and conduits |
| **EU Cyber Resilience Act** | Vulnerability management and continuous assessment obligations |
| **NIS2 Directive** | Critical infrastructure security — continuous assessment and incident detection |
| **UK PSTI Act** | Connected product security — default credential testing and exposure validation |
| **US Cyber Trust Mark** | IoT device security labeling — assessment evidence for program participation |
| **OWASP IoT Top 10** | Full mapping of all 154 modules to Top 10 categories |
| **MITRE ATT&CK for ICS** | Technique mapping for all offensive modules |
| **NIST SP 800-53** | Control mapping for RA-5 and CA-8 |

### Audit Capabilities

For compliance and forensic purposes, Blitz maintains:

| Artifact | Retention | Export Format |
| :---: | :---: | :---: |
| Decision history | Indefinite | JSON, CSV |
| AI proposals (pre-authorization) | Indefinite | JSON |
| Authorization decisions and rules applied | Indefinite | JSON, CSV |
| Execution logs (stdout/stderr) | Configurable | Text, JSON |
| Evidence artifacts (files, hashes, timestamps) | Indefinite | Binary + manifest |
| Audit log (immutable) | Indefinite | JSON, CSV, CEF |

Optional integration with Splunk, Elastic, or Microsoft Sentinel for external forwarding.

---

## Deployment Options

### Supported Topologies

| Topology | Description | Recommended For |
| :---: | :---: | :---: |
| **Single-node** | All services on one host via Docker Compose | Labs, POCs, small deployments |
| **Multi-node** | Services distributed across hosts via Kubernetes | Production, large fleets |
| **Air-gapped** | Fully isolated from external networks | Classified environments, critical infrastructure |
| **Hybrid** | Remote sensors with central coordination | Distributed sites, branch offices |
| **VPC** | Standard deployment into AWS, Azure, or GCP | Cloud-hosted enterprise environments |

### System Requirements

| Component | Minimum | Recommended | Enterprise |
| :---: | :---: | :---: | :---: |
| **CPU** | 4 cores | 8 cores | 16 cores |
| **RAM** | 8 GB | 16 GB | 32 GB |
| **Storage** | 20 GB SSD | 40 GB SSD | 100 GB NVMe |
| **Docker Engine** | 24.x | Latest stable | Latest LTS |
| **Orchestration** | Docker Compose v2 | Docker Compose v2 | Kubernetes 1.28+ |
| **Python** | 3.11+ | 3.11+ | 3.11+ |
| **GPU (optional)** | Not required | Not required | 8 GB VRAM (retraining only) |

### Installation

**Standard installation:**

```bash
unzip blitz-enterprise-*.zip
cd blitz-enterprise
chmod +x blitz-setup.sh
./blitz-setup.sh
docker compose ps
```

**Validation:**

```bash
blitz verify                # Runs against bundled QEMU test devices
blitz scan 192.168.1.0/24   # Scans authorized network
blitz report --session latest
```

**Air-gapped installation:** Image bundles, model weights, and dependency caches are provided as a signed tarball. No external network access is required at any point.

---

## Operational Lifecycle

Blitz runs a twelve-stage assessment pipeline. Every stage is observable, auditable, and interruptible.

| Stage | Name | Description |
| :---: | :---: | :---: |
| 1 | **Discover** | Identify live hosts on authorized network scope |
| 2 | **Resolve Identity** | Associate MAC, IP, and vendor information |
| 3 | **Fingerprint** | Identify device type, model, firmware version, and services |
| 4 | **Correlate Context** | Cross-reference against known device profiles and CVEs |
| 5 | **Plan** | Ares builds a ranked assessment plan based on device state |
| 6 | **Authorize** | Multi-condition gate validates each proposed action |
| 7 | **Execute** | Run authorized modules against the target |
| 8 | **Verify** | Validate results — distinguish *attempted* from *proven* |
| 9 | **Persist Evidence** | Capture artifacts, hashes, and context for every finding |
| 10 | **Generate Findings** | Produce structured findings with severity, evidence, and remediation |
| 11 | **Remediate** | Export findings to ticketing systems or generate fix guidance |
| 12 | **Re-validate** | After remediation, re-test to confirm the fix holds |

Stages 1 through 12 run automatically. Any stage can be paused, reviewed, or terminated by the operator.

---

## Module Coverage

Blitz ships with 154 attack modules across 28 protocol and domain categories. Every module includes documented preconditions, side effects, safety classification, and MITRE ATT&CK mapping.

### Coverage Summary

| Category | Modules | Notable Capabilities |
| :---: | :---: | :---: |
| **Network Protocols** | 48 | HTTP, RTSP, ONVIF, MQTT, CoAP, SNMP, SSH, Telnet, UPnP, post-exploitation |
| **Firmware Analysis** | 28 | Extraction, secret scanning, SBOM, CVE matching, emulation, exploitation |
| **Wireless and RF** | 44 | BLE, Zigbee, Wi-Fi 802.11, Z-Wave, LoRaWAN, Matter, Thread |
| **Hardware Interfaces** | 15 | UART, SPI, JTAG, SWD, I2C, CAN, voltage and clock glitching |
| **Cloud IoT Platforms** | 5 | AWS IoT Core, Azure IoT Hub — fleet-level assessment |
| **Voice Assistant Ecosystem** | 17 | Alexa, Google Home, audio injection, promptware |
| **Mobile Companion Apps** | 3 | APK/IPA static analysis, embedded firmware, backend API testing |
| **Smart Home Platforms** | 4 | SmartThings, HomeKit, Tuya, Xiaomi |
| **OTA and Provisioning** | 2 | Firmware downgrade, signature verification bypass |
| **Medical IoT** | 1 | DICOM enumeration |
| **Botnet Simulation** | 1 | Mirai-style credential testing |

### Safety Classification

Every module carries a safety classification that determines its authorization requirements.

| Classification | Description | Authorization Required |
| :---: | :---: | :---: |
| **Passive** | No packets sent to target | None |
| **Reconnaissance** | Active probing, no state change | None |
| **Validation** | Non-destructive confirmation | None |
| **Authenticated** | Requires valid credentials | None |
| **Destructive** | May alter target state | Explicit per-target approval |
| **Weaponization** | May cause device instability | Explicit approval + human confirmation |
| **Hardware-Active** | Direct hardware interface interaction | Explicit approval + physical access confirmation |

Fuzzing is disabled by default. Destructive and weaponization modules are opt-in on a per-target basis.

---

## Ares AI Engine

### Overview

Ares is the decision layer of Blitz. It observes device state, reasons about what a device is, and selects the next appropriate module from the 154-module catalog. It does not execute actions, does not interact with the network, and does not have autonomous authority — every decision it makes is subject to authorization review.

### Model Details

| Attribute | Specification |
| :---: | :---: |
| **Base model** | Qwen3 1.7B |
| **Fine-tuning method** | QLoRA (rank 16, alpha 32, 4-bit base) |
| **Training stages** | SFT → GRPO → RFT → Curriculum |
| **Training time** | Under 3 hours on a single RTX 4060 |
| **Adapter size** | ~67 MB |
| **Deployment format** | GGUF Q4_K_M (~1.1 GB) |
| **Inference runtime** | Ollama |
| **Routing accuracy** | ~92% on evaluation set |
| **JSON validity** | ~98% |
| **Safety refusal accuracy** | 100% on destructive modules without authorization |

### Retraining

The full training pipeline ships with every license. Organizations can retrain the model on their own engagement data to improve routing accuracy for their specific device inventory.

| Step | Action |
| :---: | :---: |
| 1 | Export engagement data from your Blitz instance |
| 2 | Run the included SFT, GRPO, RFT, and curriculum scripts |
| 3 | Validate against your held-out evaluation set |
| 4 | Deploy the updated adapter to Ollama |

No cloud service, external API, or third-party data is required.

### Model Swapping

The Ares Bridge supports connection to alternative model backends — including DeepSeek, Llama, Mistral, or a customer-hosted endpoint.

| Benefit | Description |
| :---: | :---: |
| **Model evaluation** | Compare different models against identical targets |
| **Regulatory compliance** | Meet specific sovereignty or residency requirements |
| **Proprietary models** | Use internally developed models with the same execution engine |

---

## Integrations

### Supported Integrations

| Integration | Direction | Purpose |
| :---: | :---: | :---: |
| **Splunk** | Outbound | Forward findings, audit logs, and events via HEC |
| **Elastic** | Outbound | Forward logs and findings via Beats or API |
| **Microsoft Sentinel** | Outbound | Log ingestion via Log Analytics workspace |
| **IBM QRadar** | Outbound | Log forwarding via Syslog or API |
| **Jira** | Bidirectional | Auto-create tickets; update on re-validation |
| **ServiceNow** | Bidirectional | Create incidents, update remediation status |
| **Slack** | Outbound | Real-time alerts for critical findings |
| **Microsoft Teams** | Outbound | Real-time alerts for critical findings |
| **GitHub Actions** | Inbound | Trigger assessments from CI/CD pipelines |
| **GitLab CI** | Inbound | Trigger assessments from CI/CD pipelines |
| **Shuffle** | Bidirectional | SOAR playbook integration |
| **TheHive** | Bidirectional | Case management integration |
| **Cortex** | Bidirectional | Analyzer integration |

### API Access

| Interface | Purpose |
| :---: | :---: |
| **REST API** | Programmatic control — launch scans, retrieve findings, manage scope |
| **WebSocket** | Real-time event stream — progress, findings, decisions |
| **MCP** | Model Context Protocol interface for AI agent integration |
| **Webhooks** | Outbound event forwarding to customer endpoints |

Full API documentation is provided with every license. Authentication uses API keys or OIDC tokens.

---

## Performance & Benchmarks

### Measured Performance

The following figures were measured in a controlled lab environment. Full methodology and reproduction scripts are available under NDA.

| Metric | Blitz | Traditional Scanner | Manual Pentest |
| :---: | :---: | :---: | :---: |
| **Time to first finding** | 47 sec | 15 min | 2 days |
| **Devices discovered per hour** | 120 | 40 | 10 |
| **False positive rate** | <5% | ~30% | ~10% |
| **Time to re-validate a patch** | Automatic | Manual | Manual |
| **Operating cost per year** | $499 once | $10,000+ | $25,000+ |

### Lab Environment

| Attribute | Detail |
| :---: | :---: |
| **Network** | Flat /24 with mixed IoT devices |
| **Devices** | Hikvision DS-2CD, Dahua NVR, Raspberry Pi 4, ESP32, Philips Hue Bridge, Shelly Plug S |
| **Host** | Ubuntu 22.04 LTS, RTX 4060, 32 GB RAM |
| **Configuration** | Blitz Enterprise, default settings |

Reproduction scripts and full lab documentation available on request.

---

## Licensing

### Commercial Tiers

| Tier | Price | Scope | Best For |
| :---: | :---: | :---: | :---: |
| **Commercial** | $499 | Perpetual, single organization, unlimited internal assets and client engagements | Consultancies, red teams, mid-market security teams |
| **Enterprise** | Contact sales | Perpetual, multi-entity, unlimited scope, SLA included | Large organizations, regulated industries |
| **Government / Defense** | Contact sales | Perpetual, air-gapped deployment, dedicated support | Public sector, defense contractors |
| **Academic / Research** | Contact sales | Perpetual, non-commercial use, discounted | Universities, research institutions |

### What Every Tier Includes

| Included | Description |
| :---: | :---: |
| **154 attack modules** | Full catalog, lifetime updates |
| **Ares AI model** | Fine-tuned model and complete training pipeline |
| **12-stage lifecycle** | Full operational pipeline |
| **Multi-condition gate** | Scope, capability, and approval enforcement |
| **Audit and evidence** | Complete trail with artifact retention |
| **API access** | REST, WebSocket, and MCP interfaces |
| **Lifetime updates** | New modules, CVE profiles, and engine upgrades |

### Volume Licensing

Volume discounts available for:

| Category | Description |
| :---: | :---: |
| **Multi-year commitments** | 2-year and 3-year terms |
| **Enterprise-wide deployments** | 10+ instances |
| **OEM and embedded** | Licensing for integration into other products |
| **Managed service providers** | Agreements for use in customer engagements |

Contact sales for a quote.

### What Is Not Included

| Item | Notes |
| :---: | :---: |
| **Hardware** | Blitz runs on customer-provided infrastructure |
| **Cloud hosting** | Self-hosted by design |
| **Professional services** | Available separately |
| **Custom module development** | Available separately |
| **Compliance certification** | Blitz supports evidence generation; certification is customer-owned |

---

## Support & SLA

### Support Tiers

| Tier | Response Time | Channels | Included With |
| :---: | :---: | :---: | :---: |
| **Community** | Best effort | GitHub Issues | Community Edition |
| **Commercial** | 24 business hours | Email, GitHub Issues | Commercial License |
| **Enterprise** | 4 hours (P1) / 8 hours (P2) | Email, Slack Connect, dedicated portal | Enterprise License |
| **Government** | 2 hours (P1) / 4 hours (P2) | Dedicated hotline, secure email | Government License |

### SLA Commitments (Enterprise)

| Severity | Definition | Response Time | Workaround Commitment |
| :---: | :---: | :---: | :---: |
| **P1** | Platform unavailable or critical function inoperable | 4 business hours | 24 hours |
| **P2** | Major function impaired with no workaround | 8 business hours | 5 business days |
| **P3** | Minor issue with workaround available | 2 business days | Next release |
| **P4** | Cosmetic issue or feature request | 5 business days | Backlog review |

### Included Support

| Item | Description |
| :---: | :---: |
| **Module updates** | New protocol modules and CVE profiles (lifetime) |
| **Engine updates** | Enhancements and bug fixes |
| **Security patches** | Applied as released |
| **Documentation** | Updated with each release |
| **Roadmap access** | Release notes and upcoming features |

### Optional Support Add-ons

| Add-on | Description |
| :---: | :---: |
| **Technical account manager** | Dedicated point of contact |
| **Quarterly business reviews** | Strategic alignment sessions |
| **On-site troubleshooting** | Physical presence for critical issues |
| **Custom module development** | New modules for proprietary protocols |
| **Training and certification** | Operator enablement programs |

---

## Professional Services

For organizations requiring accelerated deployment or customization, ApexPredator Security & Labs offers professional services.

| Service | Description | Typical Duration |
| :---: | :---: | :---: |
| **Deployment assistance** | Remote or on-site installation, configuration, and validation | 2–5 days |
| **Integration services** | SIEM, SOAR, ticketing, and CI/CD integration | 3–10 days |
| **Model retraining** | Custom training on organization-specific engagement data | 5–10 days |
| **Custom module development** | New attack modules for proprietary protocols or devices | 1–4 weeks per module |
| **Operator training** | Enablement for security teams on autonomous assessment workflows | 2 days |
| **Assessment-as-a-Service** | Managed assessment engagements using Blitz | Custom scope |

Contact sales for scoping and pricing.

---

## Procurement Information

### Documentation Available on Request

| Document | Purpose |
| :---: | :---: |
| **Security whitepaper** | Detailed security architecture and controls |
| **Architecture documentation** | Design reference and deployment guidance |
| **SBOM** | Full software bill of materials for current release |
| **Penetration test report** | Third-party assessment of the platform itself |
| **Data handling documentation** | Processing, storage, and residency details |
| **Business continuity plan** | Operational resilience documentation |
| **Insurance certificates** | Cyber liability and E&O coverage |
| **Financial stability** | Corporate and financial documentation |

### Legal

| Area | Detail |
| :---: | :---: |
| **License agreement** | Commercial End User License Agreement provided with purchase |
| **Data processing** | No customer data is processed by ApexPredator Security & Labs. All processing occurs on customer infrastructure |
| **Export control** | Blitz contains cryptographic functionality and is subject to applicable export regulations. Customer is responsible for compliance |
| **Warranty** | Standard commercial warranty provided. Extended warranty available under Enterprise tier |
| **Indemnification** | Available under Enterprise tier |

### Vendor Information

| Attribute | Detail |
| :---: | :---: |
| **Legal entity** | ApexPredator Security & Labs |
| **Year established** | *[Insert year]* |
| **Headquarters** | *[Insert location]* |
| **Registration** | *[Insert registration number]* |
| **Tax ID** | *[Insert tax ID]* |
| **Primary contact** | *[Insert contact]* |
| **Payment terms** | Net 30 (standard), Net 60 (Enterprise) |
| **Accepted currencies** | USD, EUR, GBP |
| **Procurement vehicles** | Direct, reseller, GSA (US government) |

---

## About ApexPredator Security & Labs

ApexPredator Security & Labs is a research group focused on autonomous security assessment for connected environments. The organization develops the Ares AI reasoning engine and the Blitz platform, and conducts original research in IoT/OT offensive security.

*[Placeholder: add founder bios, years active, prior research, CVE credits, conference talks, and any public writeups. Enterprise buyers require named points of contact and demonstrated credentials.]*

---

## Contact

| Purpose | Contact |
| :---: | :---: |
| **Sales** | *[Insert sales email]* |
| **Support** | *[Insert support email]* |
| **Security disclosures** | *[Insert security email + PGP key]* |
| **General inquiries** | *[Insert general email]* |
| **Headquarters** | *[Insert mailing address]* |

---

## Authorized Use

Blitz is a security testing platform. It executes real attacks against real devices, including credential attempts, protocol abuse, stream access, and exploit chaining.

**Blitz must be used only against infrastructure you own, or infrastructure for which you have explicit, written authorization to test.**

The Ares Bridge authorization gate enforces scope at the tool level. It does not replace — and is not a substitute for — having written authorization in place before you scan a target. ApexPredator Security & Labs provides Blitz as a testing platform; responsibility for lawful, authorized use rests with the licensee.

---

<div align="center">

<img src="https://github.com/giridharan-veda/threatforge-physical-iot/blob/main/apexpredator-logo-bottom.png" alt="ApexPredator Security & Labs" width="600">

**Blitz Enterprise**

*Continuous autonomous security assessment for IoT and OT environments.*

**[ REQUEST A DEMO ](#contact)**  •  **[ REQUEST A QUOTE ](#contact)**  •  **[ SECURITY DISCLOSURE ](#contact)**

*Commercial Edition · Perpetual License · Air-Gapped by Design*

</div>
