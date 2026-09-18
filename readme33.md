<div align="center">

<img src="https://raw.githubusercontent.com/giridharan-veda/threatforge-physical-iot/main/blitz-banner.svg" width="100%" alt="Blitz Enterprise — Autonomous IoT/OT Security Assessment Platform">

# Blitz Enterprise

### Autonomous IoT/OT Security Assessment Platform

**Continuous, on-premises, evidence-backed offensive security testing for connected environments — with a verifiable safety boundary between AI decision and every action.**

[![Edition](https://img.shields.io/badge/Edition-Enterprise-blue)](#licensing)
[![Deployment](https://img.shields.io/badge/Deployment-On--Premise%20%7C%20Air--Gapped-informational)](#deployment)
[![Modules](https://img.shields.io/badge/Modules-154-blueviolet)](#module-coverage)
[![Categories](https://img.shields.io/badge/Categories-28-blueviolet)](#module-coverage)
[![LLM](https://img.shields.io/badge/LLM-Local%20%C2%B7%20Air--Gapped-purple)](#ares-ai-engine)
[![License](https://img.shields.io/badge/License-Perpetual%20Commercial-red)](#licensing)

**[ REQUEST A DEMO ](#contact)**  •  **[ REQUEST A QUOTE ](#contact)**  •  **[ SECURITY DISCLOSURE ](#contact)**

*Commercial Edition — for security teams, consultancies, regulated industries, and critical infrastructure.*

</div>

---

## Executive Summary

Your organization has spent years hardening its endpoints, its cloud, and its identity infrastructure. It has annual penetration tests, a SOC, and an incident response plan. And yet, sitting on the same networks as those systems, are hundreds of cameras, controllers, sensors, and gateways that have never been assessed — that cannot be patched, that speak protocols no scanner understands, and that are frequently running with default credentials.

**Blitz exists for that gap.**

Blitz is an autonomous IoT/OT security assessment platform. It discovers every connected device on an authorized scope, identifies what each one is, decides what to test, runs only what has been authorized, and produces evidence you can act on. It runs continuously, entirely on your infrastructure, with no cloud dependency and no external telemetry.

It is not a scanner. It is not a checklist runner. It is an autonomous operator — one that thinks about your network the way a red teamer would, and stops where your rules of engagement tell it to stop.

### Why Organizations Deploy Blitz

Most security teams already know their IoT/OT surface is under-tested. The reason it stays that way is structural, not a lack of awareness. Blitz was built specifically to remove those structural barriers.

| Barrier | How Blitz Removes It |
| :--- | :--- |
| **Manual IoT testing requires rare expertise** | 154 in-house modules cover the protocols and hardware interfaces that generalist tools miss |
| **Continuous testing is expensive** | Perpetual license, no per-device or per-scan fees, runs unattended |
| **Safety concerns block autonomous testing** | Multi-condition authorization gate, safety classification on every module, fuzzing off by default |
| **Regulatory evidence is hard to produce** | Every decision, action, and result is logged, timestamped, and exportable |
| **Cloud AI is a non-starter** | Runs entirely on-prem, including the AI model, with zero external network calls |
| **Manual re-validation never happens** | Stage 12 re-tests automatically after remediation |

### What You Get

| Capability | Delivered |
| :--- | :--- |
| **154 attack modules** | Across 28 protocol and domain categories |
| **Fine-tuned local AI** | On-premises `ares` model, fully offline |
| **Full training pipeline** | Retrain on your own engagement data with one 8 GB GPU |
| **12-stage lifecycle** | Discovery through re-validation, fully automated |
| **Multi-condition safety gate** | Scope, capability, and approval enforced before every action |
| **Complete audit trail** | Every decision and result retained and exportable |
| **Air-gapped operation** | Zero external network calls, zero telemetry, zero cloud dependency |

---

## The Problem

Enterprise security programs have matured significantly over the past two decades. Endpoint detection, network monitoring, identity management, and cloud security posture tooling now cover traditional IT infrastructure with reasonable effectiveness.

IoT and OT environments have not received the same investment, for three structural reasons.

**First, most organizations cannot enumerate their connected devices.** A typical enterprise network contains cameras, badge readers, HVAC controllers, environmental sensors, industrial gateways, and building management systems that no one has ever catalogued. You cannot protect what you have not inventoried.

**Second, IoT/OT devices do not follow an enterprise patch lifecycle.** A camera deployed in 2018 is running its 2018 firmware today, because the vendor discontinued support or the device cannot be updated without physical access. Known vulnerabilities persist for the operational life of the device, which in industrial settings can be fifteen years or longer.

**Third, testing these environments safely requires expertise most teams do not staff.** Protocol-specific knowledge, hardware interfaces, physical safety considerations, and the ability to distinguish between a device that is vulnerable and a device that will brick if tested — this is a specialist discipline.

The result is a persistent, unmeasured risk surface that sits adjacent to systems that do receive rigorous assessment, on networks that are frequently flat and unsegmented.

### The Cost of Point-in-Time Assessment

Annual penetration tests are effective at identifying risk at a moment in time. They are poorly suited to environments that change continuously.

A new camera is deployed without security review. A controller is replaced during maintenance. A firmware update silently removes an earlier hardening configuration. A network segment is flattened during a migration. Remediation is applied but rarely re-verified.

Each of these events invalidates the point-in-time assessment. None of them triggers a new one. The gap between what was tested and what exists today grows quietly.

Continuous autonomous assessment addresses this not by replacing human expertise, but by extending it across every device, on a schedule you define, with an auditable boundary between decision and action.

---

## What Blitz Does

Blitz is not a scanner that reports ports. It is not a fuzzer that crashes devices. It is not a checklist that runs the same tests against every target.

Blitz is a state-driven assessment platform. It profiles each device first — what it is, what it speaks, what it exposes — and then decides what to test based on that profile. An ONVIF camera and a Modbus controller receive different assessments, because they are different devices with different risk profiles.

The platform operates in a closed loop across twelve stages, from discovery through re-validation, all of which run automatically and all of which are interruptible by an operator at any point.

### Enforcement Model

The most important architectural decision in Blitz is that the AI never touches the network.

Every action taken against a target passes through three distinct stages:

1. **Proposal** — the Ares agent reads device state and proposes what should happen next
2. **Authorization** — the Ares Bridge validates the proposal against scope, capability, and safety rules
3. **Execution** — Blitz Core runs only what was authorized, with full evidence capture

Ares has no ability to execute. Blitz Core has no ability to decide. The Bridge has no ability to run anything itself. The operator can stop the system at any point.

This is what makes continuous, unattended testing viable in production environments.

---

## Reference Architecture

Blitz is composed of five discrete services, each with a single responsibility. The separation is deliberate — it ensures the AI has no direct network access, the executor has no autonomous authority, and every action passes through an auditable enforcement point.

<img src="https://github.com/giridharan-veda/threatforge-physical-iot/blob/main/blitz-architecture.svg" width="100%" alt="Blitz Enterprise architecture">

### Components

| Component | Function | Network Boundary |
| :--- | :--- | :--- |
| **Operator Console** | Human control plane for launching assessments, reviewing proposals, and approving or denying actions | User-facing |
| **Ares Agent** | AI orchestration layer. Profiles devices, plans assessments, selects modules from the catalog | No direct network access |
| **Ares Bridge** | Capability gateway. Enforces multi-condition authorization before any action reaches the executor | Enforcement boundary |
| **Ollama Runtime** | Local model server hosting the fine-tuned `ares` model. Operates entirely offline | Internal only |
| **Blitz Core** | Execution engine. Runs approved modules, collects evidence, exposes REST and WebSocket APIs | Target-facing |
| **Persistent State** | Durable store for devices, jobs, findings, incidents, and complete audit history | Internal only |

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
| :--- | :--- | :--- | :--- |
| Blitz Core API | 8088 | REST + WebSocket | Internal |
| Ares Bridge | 8089 | MCP over HTTP | Internal |
| Ares Agent | 9010 | MCP over HTTP | Internal |
| Ollama Runtime | 11435 | HTTP | Localhost only |

No service exposes itself to external networks. All inter-service communication occurs over an internal Docker network or equivalent.

---

## Security & Compliance

Blitz is designed for environments with strict security review requirements. All processing occurs on customer-controlled hardware. No external network calls are made during operation.

### Security Controls

| Control Area | Implementation |
| :--- | :--- |
| **Data residency** | All processing on customer infrastructure. Zero external network calls |
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

Blitz supports evidence generation for the following frameworks. Detailed mapping documentation is included with enterprise licenses.

| Framework | Coverage |
| :--- | :--- |
| **IEC 62443** | Industrial automation and control systems security — assessment evidence for zones and conduits |
| **EU Cyber Resilience Act** | Vulnerability management and continuous assessment obligations for products with digital elements |
| **NIS2 Directive** | Critical infrastructure security — continuous assessment and incident detection |
| **UK PSTI Act** | Connected product security — default credential testing and exposure validation |
| **US Cyber Trust Mark** | IoT device security labeling — assessment evidence for program participation |
| **OWASP IoT Top 10** | Full mapping of all 154 modules to Top 10 categories |
| **MITRE ATT&CK for ICS** | Technique mapping for all offensive modules |
| **NIST SP 800-53** | Control mapping for RA-5 and CA-8 |

### Audit and Retention

For compliance and forensic purposes, Blitz retains a complete record of every assessment — not just the findings, but the reasoning that produced them. This includes the AI's raw proposal before authorization, the specific rule or condition that determined the authorization outcome, and the full execution log for every module that ran.

| Artifact | Retention | Export Format |
| :--- | :--- | :--- |
| Decision history | Indefinite | JSON, CSV |
| AI proposals (pre-authorization) | Indefinite | JSON |
| Authorization decisions and rules applied | Indefinite | JSON, CSV |
| Execution logs (stdout/stderr) | Configurable | Text, JSON |
| Evidence artifacts (files, hashes, timestamps) | Indefinite | Binary + manifest |
| Audit log (immutable) | Indefinite | JSON, CSV, CEF |

Optional integration with Splunk, Elastic, or Microsoft Sentinel for external forwarding.

---

## Deployment

Blitz is self-hosted by design. It runs on your infrastructure, on your network, under your control. There is no SaaS version and no cloud dependency.

### Deployment Topologies

| Topology | Description | Recommended For |
| :--- | :--- | :--- |
| **Single-node** | All services on one host via Docker Compose | Labs, proof-of-concept, small deployments |
| **Multi-node** | Services distributed across hosts via Kubernetes | Production deployments, large fleets |
| **Air-gapped** | Fully isolated from external networks. Image bundles provided as a signed tarball | Classified environments, critical infrastructure |
| **Hybrid** | Remote sensors collect data, central instance coordinates and reports | Distributed sites, branch offices |
| **VPC** | Standard deployment into AWS VPC, Azure VNet, or GCP VPC | Cloud-hosted enterprise environments |

### System Requirements

| Component | Minimum | Recommended | Enterprise |
| :--- | :--- | :--- | :--- |
| **CPU** | 4 cores | 8 cores | 16 cores |
| **RAM** | 8 GB | 16 GB | 32 GB |
| **Storage** | 20 GB SSD | 40 GB SSD | 100 GB NVMe |
| **Docker Engine** | 24.x | Latest stable | Latest LTS |
| **Orchestration** | Docker Compose v2 | Docker Compose v2 | Kubernetes 1.28+ |
| **Python** | 3.11+ | 3.11+ | 3.11+ |
| **GPU (optional)** | Not required | Not required | 8 GB VRAM (retraining only) |

### Installation

Standard installation on a prepared host:

```bash
unzip blitz-enterprise-*.zip
cd blitz-enterprise
chmod +x blitz-setup.sh
./blitz-setup.sh
docker compose ps
```

Validation:

```bash
blitz verify                # Runs against bundled QEMU test devices
blitz scan 192.168.1.0/24   # Scans authorized network scope
blitz report --session latest
```

For air-gapped deployments, image bundles, model weights, and dependency caches are provided as a signed tarball. No external network access is required at any point during installation or operation.

---

## Operational Lifecycle

Blitz runs a twelve-stage assessment pipeline. Every stage is observable, auditable, and interruptible by an operator. Stages run automatically, but any stage can be paused for review or terminated outright.

| Stage | Name | Description |
| :--- | :--- | :--- |
| 1 | **Discover** | Identify live hosts on authorized network scope |
| 2 | **Resolve Identity** | Associate MAC, IP, and vendor information |
| 3 | **Fingerprint** | Identify device type, model, firmware version, and exposed services |
| 4 | **Correlate Context** | Cross-reference against known device profiles and CVE databases |
| 5 | **Plan** | Ares builds a ranked assessment plan based on device state |
| 6 | **Authorize** | Multi-condition gate validates each proposed action |
| 7 | **Execute** | Run authorized modules against the target |
| 8 | **Verify** | Validate results, distinguishing *attempted* from *proven* |
| 9 | **Persist Evidence** | Capture artifacts, hashes, and context for every finding |
| 10 | **Generate Findings** | Produce structured findings with severity, evidence, and remediation |
| 11 | **Remediate** | Export findings to ticketing systems or generate fix guidance |
| 12 | **Re-validate** | After remediation, re-test to confirm the fix holds |

Stage 12 is what distinguishes Blitz from every other assessment tool. A finding is not closed when it is reported. It is closed when the fix has been verified against the live device, automatically, without a separate engagement.

---

## Module Coverage

Blitz ships with 154 attack modules across 28 protocol and domain categories. Every module includes documented preconditions, side effects, safety classification, and MITRE ATT&CK mapping.

These are not plugin-marketplace modules. They were built in-house, by the same team that built the platform, specifically for IoT and OT environments.

### Coverage Summary

| Category | Modules | Notable Capabilities |
| :--- | :---: | :--- |
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

Every module carries a safety classification that determines its authorization requirements. This is not documentation — it is the mechanism the Bridge uses to decide whether a proposed action can execute.

| Classification | Description | Authorization Required |
| :--- | :--- | :--- |
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

Ares is the decision layer of Blitz. It observes device state, reasons about what a device is, and selects the next appropriate module from the 154-module catalog.

It does not execute actions. It does not interact with the network. It does not have autonomous authority. Every decision it makes is subject to authorization review, and every decision is logged with the reasoning that produced it.

### Model Details

| Attribute | Specification |
| :--- | :--- |
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

The choice to use a small, fine-tuned model rather than a large general-purpose one was deliberate. Ares is not asked to reason about the world. It is asked one narrow question at a time — *given this device state, which module should run next?* — and a specialist trained on exactly that question outperforms a generalist on that question, at a fraction of the compute cost, running on hardware you already own.

### Retraining on Your Own Data

The full training pipeline ships with every license. Organizations can retrain the model on their own engagement data to improve routing accuracy for their specific device inventory.

The workflow is straightforward:

1. Export engagement data from your Blitz instance
2. Run the included SFT, GRPO, RFT, and curriculum scripts
3. Validate against your held-out evaluation set
4. Deploy the updated adapter to Ollama

No cloud service, external API, or third-party data is required at any step.

### Model Swapping

The Ares Bridge supports connection to alternative model backends — including DeepSeek, Llama, Mistral, or a customer-hosted endpoint. This allows organizations to evaluate different models against identical targets, meet specific regulatory or sovereignty requirements, or use proprietary models developed internally, without changing anything about the execution engine.

---

## Integrations

Blitz fits into existing security operations workflows. Findings, audit logs, and events can be forwarded to the systems your team already uses, and assessments can be triggered programmatically from CI/CD pipelines.

### Supported Integrations

| Integration | Direction | Purpose |
| :--- | :--- | :--- |
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
| :--- | :--- |
| **REST API** | Programmatic control — launch scans, retrieve findings, manage scope |
| **WebSocket** | Real-time event stream — progress, findings, decisions |
| **MCP** | Model Context Protocol interface for AI agent integration |
| **Webhooks** | Outbound event forwarding to customer endpoints |

Full API documentation is provided with every license. Authentication uses API keys or OIDC tokens.

---

## Performance

The following figures were measured in a controlled lab environment. Full methodology and reproduction scripts are available under NDA.

| Metric | Blitz | Traditional Scanner | Manual Pentest |
| :--- | :---: | :---: | :---: |
| **Time to first finding** | 47 sec | 15 min | 2 days |
| **Devices discovered per hour** | 120 | 40 | 10 |
| **False positive rate** | <5% | ~30% | ~10% |
| **Time to re-validate a patch** | Automatic | Manual | Manual |
| **Operating cost per year** | $499 once | $10,000+ | $25,000+ |

### Lab Environment

The benchmarks were measured on a flat /24 network containing a Hikvision DS-2CD camera, a Dahua NVR, a Raspberry Pi 4, an ESP32 development board, a Philips Hue Bridge, and a Shelly Plug S. The host was Ubuntu 22.04 LTS running on an RTX 4060 with 32 GB of RAM, using Blitz Enterprise in default configuration.

Reproduction scripts and full lab documentation available on request.

---

## Licensing

Blitz is sold as a perpetual commercial license. There are no subscriptions, no per-device fees, and no per-scan metering.

### Commercial Tiers

| Tier | Price | Scope | Best For |
| :--- | :--- | :--- | :--- |
| **Commercial** | $499 | Perpetual, single organization, unlimited internal assets and client engagements | Consultancies, red teams, mid-market security teams |
| **Enterprise** | Contact sales | Perpetual, multi-entity, unlimited scope, SLA included | Large organizations, regulated industries |
| **Government / Defense** | Contact sales | Perpetual, air-gapped deployment, dedicated support | Public sector, defense contractors |
| **Academic / Research** | Contact sales | Perpetual, non-commercial use, discounted | Universities, research institutions |

### What Every Tier Includes

Every license — regardless of tier — includes the complete platform:

- 154 attack modules
- Ares AI model and full training pipeline
- 12-stage operational lifecycle
- Multi-condition authorization gate
- Complete audit trail and evidence storage
- REST API, WebSocket, and MCP interfaces
- Lifetime updates and new modules

There is no "module pack" upsell, no premium tier that unlocks capabilities, and no feature gating.

### Volume Licensing

Volume discounts are available for multi-year commitments, enterprise-wide deployments of ten or more instances, OEM and embedded licensing, and managed service provider agreements. Contact sales for a quote.

### What Is Not Included

Blitz is a software platform. It does not include hardware, cloud hosting, professional services, custom module development, or compliance certification. Each of these is available separately.

---

## Support & SLA

### Support Tiers

| Tier | Response Time | Channels | Included With |
| :--- | :--- | :--- | :--- |
| **Community** | Best effort | GitHub Issues | Community Edition |
| **Commercial** | 24 business hours | Email, GitHub Issues | Commercial License |
| **Enterprise** | 4 hours (P1) / 8 hours (P2) | Email, Slack Connect, dedicated portal | Enterprise License |
| **Government** | 2 hours (P1) / 4 hours (P2) | Dedicated hotline, secure email | Government License |

### SLA Commitments (Enterprise)

| Severity | Definition | Response Time | Workaround Commitment |
| :--- | :--- | :--- | :--- |
| **P1** | Platform unavailable or critical function inoperable | 4 business hours | 24 hours |
| **P2** | Major function impaired with no workaround | 8 business hours | 5 business days |
| **P3** | Minor issue with workaround available | 2 business days | Next release |
| **P4** | Cosmetic issue or feature request | 5 business days | Backlog review |

### Included With Every License

- New protocol modules and CVE profiles (lifetime)
- Engine enhancements and bug fixes
- Security patches
- Documentation updates
- Access to release notes and roadmap

### Optional Support Add-ons

Dedicated technical account management, quarterly business reviews, on-site troubleshooting, custom module development, and operator training and certification are available for organizations that need them.

---

## Professional Services

For organizations requiring accelerated deployment or customization, ApexPredator Security & Labs offers professional services. These are optional — Blitz is designed to be deployed and operated by your own team without vendor involvement.

| Service | Description | Typical Duration |
| :--- | :--- | :--- |
| **Deployment assistance** | Remote or on-site installation, configuration, and validation | 2–5 days |
| **Integration services** | SIEM, SOAR, ticketing, and CI/CD integration | 3–10 days |
| **Model retraining** | Custom training on organization-specific engagement data | 5–10 days |
| **Custom module development** | New attack modules for proprietary protocols or devices | 1–4 weeks per module |
| **Operator training** | Enablement for security teams on autonomous assessment workflows | 2 days |
| **Assessment-as-a-Service** | Managed assessment engagements using Blitz | Custom scope |

Contact sales for scoping and pricing.

---

## Procurement Information

The following documentation is available on request for security review, legal, and procurement teams.

| Document | Purpose |
| :--- | :--- |
| **Security whitepaper** | Detailed security architecture and controls |
| **Architecture documentation** | Design reference and deployment guidance |
| **SBOM** | Full software bill of materials for the current release |
| **Penetration test report** | Third-party assessment of the platform itself |
| **Data handling documentation** | Processing, storage, and residency details |
| **Business continuity plan** | Operational resilience documentation |
| **Insurance certificates** | Cyber liability and E&O coverage |
| **Financial stability** | Corporate and financial documentation |

### Legal and Vendor Information

| Area | Detail |
| :--- | :--- |
| **License agreement** | Commercial End User License Agreement provided with purchase |
| **Data processing** | No customer data is processed by ApexPredator Security & Labs. All processing occurs on customer infrastructure |
| **Export control** | Blitz contains cryptographic functionality and is subject to applicable export regulations. Customer is responsible for compliance |
| **Warranty** | Standard commercial warranty provided. Extended warranty available under Enterprise tier |
| **Indemnification** | Available under Enterprise tier |
| **Legal entity** | ApexPredator Security & Labs |
| **Year established** | *[Insert year]* |
| **Headquarters** | *[Insert location]* |
| **Registration** | *[Insert registration number]* |
| **Tax ID** | *[Insert tax ID]* |
| **Payment terms** | Net 30 (standard), Net 60 (Enterprise) |
| **Accepted currencies** | USD, EUR, GBP |
| **Procurement vehicles** | Direct, reseller, GSA (US government) |

---

## About ApexPredator Security & Labs

ApexPredator Security & Labs is a research group focused on autonomous security assessment for connected environments. The organization develops the Ares AI reasoning engine and the Blitz platform, and conducts original research in IoT/OT offensive security.

Every module, protocol integration, and the fine-tuned `ares` model shipped with Blitz was built in-house. This is not a wrapper around existing open-source scanners. It is not an orchestration layer on top of someone else's tooling. It is a purpose-built platform developed specifically for the problem it solves.

*[Placeholder: add founder bios, years active, prior research, CVE credits, conference talks, and any public writeups. Enterprise buyers require named points of contact and demonstrated credentials.]*

---

## Contact

| Purpose | Contact |
| :--- | :--- |
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
