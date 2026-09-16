<div align="center">

<img src="https://raw.githubusercontent.com/giridharan-veda/threatforge-physical-iot/main/blitz-banner.svg" width="100%" alt="Blitz — Autonomous IoT Red Teaming Platform powered by Ares">

### ⚡ The Autonomous IoT/OT Red Teaming & Continuous Assessment Platform

**Stop guessing whether your Internet of Things / Operational Technology devices are actually secure. Blitz autonomously hunts down every IoT/OT device on your network and, upon authorization, launches live attacks against them — delivering proof of what's actually vulnerable, every single day.**

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Docker](https://img.shields.io/badge/Docker-Supported-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)
[![Ares AI](https://img.shields.io/badge/Ares-IoT%20AI%20Engine-purple)](#ares-ai)
[![License](https://img.shields.io/badge/License-Commercial-red.svg)](LICENSE)
[![Price](https://img.shields.io/badge/Early%20Adopter-%24299-brightgreen)](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)

**🔥 Early Adopter Cohort — $299, first 25 licenses only, code `EARLYBIRD`**

[![Purchase Blitz Commercial License](https://img.shields.io/badge/Purchase%20Blitz-%24299%20Early%20Adopter-brightgreen?style=for-the-badge&logo=github)](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)

[Overview](#overview) •
[Architecture](#architecture) •
[Ares AI](#ares-ai) •
[Protocol Coverage](#protocol-specific-attack-coverage) •
[Capabilities](#capabilities) •
[Blitz vs. Alternatives](#comparison) •
[Pricing](#pricing) •
[Licensing & Pricing](#commercial-licensing--access) •
[FAQ](#faq) •
[Authorized Use](#authorized-use) •
[About](#about) •
[Installation](#installation--system-requirements)

**🛡️ For authorized security testing only.** Blitz must only be run against devices and networks you own or have explicit written authorization to test. See [Authorized Use](#authorized-use).

</div>

---

## Overview

### ⚠️ The Risk

Security teams have spent two decades getting good at defending laptops and servers. Attackers noticed, and moved somewhere easier. 🎯

That somewhere is **IoT and OT**: the cameras, sensors, controllers, and gateways quietly running your buildings, your factories, your hospitals. They're on the same network as everything you actually protect — but almost none of the same rigor applies to them. Here's what that gap looks like in practice:

- 🕵️ **You can't defend what you can't see.** Most orgs don't have a full inventory of their IoT/OT assets.
- 🔑 **The manufacturer's password is still the password.** `admin:admin`, default and unchanged, for the life of the device.
- 🚪 **A service requires no authentication at all.** Video streams, control interfaces, and management panels built to "just work," without a security layer.
- 📡 **The traffic is unprotected.** No encryption means anything on the wire — credentials, keys — is visible to anyone with access to it.
- 🧱 **"Segmented" is usually a belief, not a fact.** Flat networks and misconfigured VLANs turn one compromised device into a path to everything else.
- 🛠️ **Nothing here gets patched.** No update lifecycle exists for most embedded firmware; known weaknesses just persist.
- 🙈 **Detection tooling doesn't cover this layer.** Built for IT traffic, blind to IoT/OT — compromise here often goes unnoticed.
- 🎯 **The riskiest devices are tested the least**, because testing them safely takes expertise most teams don't staff for.
- ✅❌ **"Fixed" is usually an assumption, not a fact.** Fixes rarely get re-verified, so "resolved" risk often isn't.

> 🚨 **This is the default state of every IoT/OT network — including yours.** The devices you trust most are the ones you've tested least.

---

## 🛡️ Enter — Blitz

**Blitz** is an **autonomous system** built to test IoT/OT security the way it actually needs to be tested.

<img src="https://github.com/giridharan-veda/threatforge-physical-iot/blob/main/blitz.png" width="100%" alt="Blitz — Autonomous IoT Red Teaming Platform powered by Ares">

- 🔍 **Profiles each device first** — what it is, what it speaks, what it's exposed to — then plans an attack built for that device.
- 🔒 **Every action passes an authorization gate** before execution, so it's safe to run continuously against live production infrastructure.
- 📊 **Results are evidence-backed**, labeled *attempted* or *proven*. Once a fix ships, Blitz revalidates it automatically.
- ⚖️ **The real difference is the operating model, not the toolset.** Every comparable tool on the market is driven by a human, command by command.
- 🕵️ **Discovery, decision-making, execution, and proof run continuously and autonomously** — every day, across the whole network.
- 🧠 **An intelligence layer decides when, where, and how to act**, without needing someone at the keyboard for every test.

It first determines what's actually present in the target environment — devices, ports, services, protocols, authentication mechanisms, exposed interfaces — and then selects assessment modules relevant to those specific surfaces.

### What Makes Blitz Different

Traditional IoT scanners stop at statements like:

> "Port 554 is open."

or:

> "This device appears to expose HTTP."

Blitz goes further and asks:

> **"What does that service expose, how does it behave, what security controls protect it, and can the observed weakness be safely demonstrated?"**

Discovering an RTSP service, for example, is only the beginning. Blitz identifies the RTSP implementation, inspects its authentication behavior, enumerates permitted stream endpoints where authorized, examines transport configuration, and determines whether the observed exposure can be validated against the live camera or video service. The same protocol-aware approach applies across:

**HTTP/HTTPS, RTSP, ONVIF, MQTT, CoAP, UPnP/SSDP, SSH, Telnet, SNMP, TLS**, and other IoT-facing services.

### Technology Stack

<div align="center">

| Component | Role | Description |
|---|---|---|
| 🎛️ **Operator Console** | Human control plane for launching assessments and monitoring live results | The interface where a human stays in the loop — launching new assessments, reviewing what Ares is proposing, and approving or denying actions before they run. This is where authorization decisions happen. |
| 🧠 **Ares Agent** | AI orchestration layer that plans and sequences assessments | Profiles each discovered device, reasons about what's actually worth testing on it, and plans an intelligent, prioritized sequence of actions — rather than running a fixed checklist against everything it finds. |
| 🔒 **Ares Bridge** | Capability gateway that enforces what Ares is allowed to request | Sits between Ares and the execution engine as a hard boundary — every action Ares wants to take is checked against strict, multi-condition rules before it ever reaches a real device. This is what keeps autonomy safe. |
| 🖥️ **Ollama** | Local model runtime for private, on-premises AI inference | Runs the AI models that power Ares entirely on-premises — no data or device context ever has to leave your environment to generate an assessment plan. |
| ⚙️ **Blitz Core** | Assessment & execution engine (REST + WebSocket) that runs the full closed-loop lifecycle | The engine that executes approved actions, collects evidence, and drives the full lifecycle from discovery through proof — exposed via REST and WebSocket so every stage can be tracked and integrated. |
| 🗄️ **Persistent State** | Stores devices, jobs, findings, incidents, and complete audit history | The system of record — every device ever seen, every job ever run, every finding and incident — kept as a durable, auditable history rather than a one-time report that gets filed away. |
| 📡 **Live Event Stream** | Real-time WebSocket feed of progress, results, and narratives to the operator GUI | Streams what's happening as it happens — progress updates, results, plain-language narratives — so the operator watches the assessment unfold live instead of waiting for a final report. |

</div>

---

## 🧠 Ares AI

**Ares** is the autonomous intelligence layer of the Blitz platform — the component that turns a collection of IoT security tools into a system capable of independent assessment.

<img src="https://raw.githubusercontent.com/giridharan-veda/threatforge-physical-iot/main/aresai.png" width="100%" alt="Blitz — Autonomous IoT Red Teaming Platform powered by Ares">

Most security tools require a human to decide what to scan, which credentials to try, which protocols to probe, and what to do next. Ares removes that dependency: it observes the current state of a target, reasons about what the device appears to be, and decides the next appropriate action from a defined list of attacks and capabilities.

Ares does not perform network attacks itself — that responsibility belongs to Blitz Core. Ares acts purely as a decision engine. It maintains a structured knowledge base of device profiles, protocol behaviors, known attack surfaces, and tool mappings. When new information is discovered — open ports, banners, services, vendor signatures — Ares classifies the device and builds a ranked plan of what should be tested next.

The model powering Ares is fine-tuned specifically to make that call — which tool is the right next step at each decision point. Because Ares understands IoT-specific context (cameras, brokers, routers, controllers, and their typical weaknesses), it drives assessments that are meaningfully more efficient than generic scanning. The result is a system that can move through an assessment with minimal human intervention.

### 🔌 Ares Bridge

The **Ares Bridge** sits between the intelligence layer (Ares) and the execution layer (Blitz). It's the component that makes the system extensible: Ares decides what should happen, but the Bridge decides whether that request is allowed to proceed and how it's translated into an actual action.

During development, the Bridge was tested against external AI backends — including RedAmon paired with StrikeGPT (`q4-k-m` quantization) — to confirm the interface can accept decisions from third-party planning systems without any change to the underlying execution engine. As a result, the Bridge connects Blitz to other AI APIs and LLMs beyond the default stack.

Beyond AI integration, the Bridge also provides a clean path for connecting external systems such as SIEM platforms. Because every capability request and result flows through a single, well-defined interface, events and findings can be forwarded to monitoring tools without touching the core engine.

### 🖥️ Ollama LLM in Blitz

**Ollama** is the local model runtime that powers the intelligence inside Ares. The model Blitz ships with is a 1.7-billion-parameter Qwen3 variant fine-tuned specifically for IoT pentesting. It doesn't plan entire attack chains or interact with the network — its only job is to answer one question at a time: given the current state of a device, which tool should run next.

### How the model was trained

The model was fine-tuned using QLoRA on a dataset of 683 IoT-specific examples, combining real session exports with synthetic scenarios built around common IoT device families — cameras, routers, MQTT brokers, controllers, and similar systems.

Each training example presented the model with a compact device state (open ports, services, basic context) and required it to select the most appropriate next tool from a fixed allowlist. Training also included rationale distillation, so the model learned not just which tool to choose, but why that choice made sense for a given device type.

In this design, the model contributes judgment at each decision point, while the surrounding systems in Ares handle sequencing, state, persistence, and execution.

---

## Architecture

Blitz is designed as a **closed-loop automated red teaming system** built specifically for IoT and OT environments.

<p align="center">
<img src="https://github.com/giridharan-veda/threatforge-physical-iot/blob/main/blitz-architecture.svg" width="100%" alt="Blitz — Autonomous IoT Red Teaming Platform powered by Ares">
</p>

### Data Flow & Ports

| Hop | Protocol / Port | Description |
|-----|------------------|-------------|
| Operator → Ares Agent | Internal | Assessment request and high-level job launch |
| Ares Agent → Ares Bridge | Internal (`:8089`) | Capability requests are gated and authorized |
| Ares Bridge → Ollama | Internal (`:11435`) | Local model inference for reasoning and planning |
| Ares → Blitz Core | REST (`:8088`) | Only approved assessment plans are submitted |
| Blitz Core → Target Devices | Multi-protocol (ARP, mDNS, SSDP, ONVIF, TCP, etc.) | Discovery, fingerprinting, and authorized test execution |
| Blitz Core → Persistent State | Internal | Devices, jobs, findings, incidents, and full audit trail |
| Blitz Core → Operator | WebSocket | Live events, progress, narratives, and results |

---

### Repository Structure

```text
Blitz/
├── ares/                         # Ares – AI Reasoning & Orchestration Layer
│                                 # Contains Ares Agent, Ares Bridge (capability gateway),
│                                 # and prompt templates used for intelligent planning
│
├── blitz-core/                   # Blitz Core – Assessment & Execution Engine
│   ├── discovery/                # Stages 1–4: Discover, Resolve Identity, Fingerprint, Correlate Context
│   ├── planning/                 # Stage 5: Build ranked assessment plan (Ares-assisted)
│   ├── authorization/            # Stage 6: Authorization Gate (Authorized? In scope? Capability allowed?)
│   ├── execution/                # Stages 7–8: Execute authorized tests + Verify results
│   ├── evidence/                 # Stages 9–10: Persist evidence + Generate findings
│   ├── remediation/              # Stages 11–12: Remediate + Re-validate
│   └── api/                      # REST + WebSocket API (:8088)
│
├── state/                        # Persistent State & Audit
│                                 # Stores devices, jobs, findings, incidents, and full audit trail
│
├── configs/                      # Configuration
│                                 # capabilities.yaml, scopes.yaml, settings.yaml
│
├── docker/                       # Deployment
│                                 # docker-compose.yml, Dockerfiles, and environment templates
│
├── docs/                         # Documentation
│                                 # Architecture, installation, API reference, and usage guides
│
├── assets/                       # Static Assets
│                                 # Banner, architecture diagrams, and visual resources
│
├── scripts/                      # Utility Scripts
│                                 # Startup, health checks, and maintenance helpers
│
├── tests/                        # Test Suite
│                                 # Unit and integration tests
│
├── LICENSE                       # Commercial License
├── README.md                     # Project overview and documentation
└── requirements.txt              # Python dependencies
```

### Protocol-Specific Attack Coverage

| Protocol | What It Tests | Common IoT Devices | Real-Time Validation |
|---|---|---|---|
| **HTTP / HTTPS** | Web login, admin pages, access control, input and configuration flaws | Cameras, routers, NVRs, NAS, smart hubs | Finds web services and paths, sends controlled requests, tests authentication and verifies access restrictions. |
| **RTSP** | Video-stream exposure and authentication | IP cameras, CCTV, DVRs, NVRs | Connects to RTSP, discovers streams, checks authentication, and verifies whether restricted streams are accessible. |
| **ONVIF** | Camera management and authorization | IP/PTZ cameras, NVRs, VMS | Discovers ONVIF services, identifies camera capabilities, and verifies authentication and management permissions. |
| **MQTT** | Broker security, topic access, and publish/subscribe permissions | Sensors, gateways, smart-home and industrial IoT | Connects to the broker, checks authentication, discovers permitted topics, and validates read/write ACLs. |
| **CoAP** | Resource exposure and access control | Sensors, smart lighting, thermostats, embedded IoT | Discovers CoAP resources and sends controlled requests to verify whether protected resources are accessible. |
| **UPnP / SSDP** | Device discovery and exposed control services | Routers, TVs, NAS, cameras, smart appliances | Discovers UPnP devices, maps their services, and checks whether control interfaces are unnecessarily exposed. |
| **SSH** | Remote administration and authentication | IoT gateways, routers, NAS, embedded Linux devices | Identifies SSH, checks configuration and authentication, and validates authorized remote access. |
| **Telnet** | Insecure remote administration | Legacy routers, cameras, DVRs, embedded devices | Detects Telnet, evaluates authentication, and confirms whether administrative access is exposed over plaintext remote management. |
| **SNMP** | Management access and information exposure | Routers, switches, printers, UPS, cameras | Identifies SNMP, tests authorized credentials/community strings, and checks what management information is accessible. |
| **TLS** | Encryption, certificates, and cryptographic configuration | HTTPS cameras, routers, gateways, MQTT services, APIs | Establishes a TLS connection, examines supported versions/ciphers, and validates certificate and transport security. |

---

## ATT&CK Coverage Map

<img src="https://github.com/giridharan-veda/threatforge-physical-iot/blob/main/ares-attack-matrix.svg" width="100%" alt="Blitz — Autonomous IoT Red Teaming Platform powered by Ares">

*The techniques above map Blitz's autonomous testing activity — discovery, credential access, protocol abuse, impact validation — against the stages a real IoT/OT intrusion would follow, so results can be read in attacker terms, not just scan output.*

## 🎯 Capabilities

### The Ultimate Autonomous IoT Red Teaming Arsenal

Blitz transforms fragmented IoT assessment work into a single high-speed, automated offensive workbench. Whether you're auditing physical facilities, competing in CTF arenas, or stress-testing hardware in a staging lab, Blitz and the Ares AI engine deliver seven integrated operational capabilities.

### Operational Modes Matrix

| Mode / Feature | Primary Target Surface | Autonomy Level | Primary Output |
|---|---|---|---|
| **Autonomous AutoPwn** | Multi-protocol IoT subnets | Fully autonomous | Chained compromise proofs |
| **Protocol Fuzzing** | MQTT, CoAP, RTSP, ONVIF | Configurable concurrency | Crash logs & input boundary flaws |
| **Firmware Carving** | Raw embedded binary images | Automated batch | Extracted secrets & CGI vulnerabilities |
| **Ghost Recon** | Layer 2 broadcast domains | Passive to high-throughput | Device topology & identity maps |
| **BYO-Brain Engine** | Planning & reasoning layer | AI-directed | Execution plans & tool selection |
| **CTF Arena Mode** | Staging labs & QEMU images | Real-time interactive | Live streaming WebSocket feed |
| **Re-Validation Loop** | Post-remediation targets | Targeted automated replay | Fix attestation & regression reports |

---

### 1. Autonomous AutoPwn & Exploit Chaining Loop
Eliminates disjointed scripts and manual credential handoffs. The Ares reasoning engine analyzes device state, correlates exposure vectors, and chains multi-stage validation paths automatically:
- **Dynamic Pivoting:** Ares identifies an anonymous MQTT broker, subscribes to wildcard topics (`#`), extracts credentials from broadcast device telemetry, and validates access against exposed administrative or RTSP services on adjacent subnets.
- **Impact Verification:** Extracts cryptographic and operational proof (video frame captures, broker ACL write confirmations, directory listings) into persistent state storage without human intervention.

### 2. Multi-Protocol Chaos Fuzzing Engine
Generic web scanners fail against constrained hardware protocols. Blitz runs native protocol engines across its full library of specialized testing modules simultaneously:
- **Protocol Diversity:** Native query and assessment engines for MQTT, CoAP, RTSP, ONVIF, UPnP/SSDP, embedded CGI, raw TCP sockets, and legacy Telnet/SSH services.
- **Boundary Validation:** Detects malformed packet handling, memory exhaustion conditions, and logic flaws across embedded network stacks (lwIP, FreeRTOS, Zephyr, and others).

### 3. Automated Firmware Decapitation & Taint Mining
Ingests raw `.bin`, `.img`, or firmware packages directly into the analysis pipeline for automated inspection:
- **Automated Extraction:** Decompresses and extracts standard embedded filesystems, including SquashFS, CramFS, UBIFS, and JFFS2.
- **Secret & Vulnerability Extraction:** Scans the extracted root filesystem for hardcoded private cryptographic keys, embedded credentials, default tokens, and debug CGI binaries.

### 4. Ghost Recon (Zero-Noise Stealth to High-Velocity Sweeps)
Discovery intensity is configurable from silent listening to high-throughput active scanning:
- **Passive Listener Mode:** Passively maps the local environment by monitoring ambient mDNS, UPnP, SSDP, and ARP broadcasts without transmitting packets.
- **High-Speed Network Sweep:** Executes parallel multi-protocol host discovery with Layer 2 adjacency, identifying device vendor, model, firmware revision, and exposed surfaces.

### 5. BYO-Brain: Hot-Swappable AI Model Engine
Ares runs on an open, modular capability bridge rather than a locked-in AI provider:
- **Air-Gapped Local Inference:** Ships configured with the fine-tuned `qwen3-iot:1.7b` model, running offline via local Ollama (`:11435`) for zero external telemetry and zero per-token API costs.
- **Model Hot-Swapping:** Route requests through the Ares Bridge (`:8089`) to alternate local or remote model endpoints (such as DeepSeek-Coder, Llama, or Mistral) to evaluate different reasoning models against identical targets.

### 6. Hardware Lab & CTF Arena Mode
Built for repeatable experimentation in staging and competitive environments:
- **Live WebSocket Telemetry:** Streams raw operational decision graphs and execution telemetry directly to terminal consoles or custom dashboards over WebSocket port `:8088`.
- **Target Emulation Compatibility:** Deploy against virtualized or physical targets (Docker, QEMU, or hardware test benches) to run repeatable attack simulations against simulated camera arrays, smart meters, and industrial IoT controllers.

### 7. Instant Proof-of-Impact & Remediation Diffs
Converts automated test data into verifiable technical artifacts:
- **Attempted vs. Proven Telemetry:** Strictly separates an initial service probe from a cryptographically or functionally confirmed vulnerability — no speculative findings.
- **Closed-Loop Re-Validation:** After remediation, Stage 12 (**Re-validate**) automatically replays the verified exploit chain to confirm whether the vulnerability was actually mitigated — without re-running a full scan.

---

<a name="comparison"></a>
## ⚔️ Blitz vs. Established Open-Source IoT Security Tools

| Capability | 🛠️ RouterSploit | 🏠 HomePwn | 💥 EXPLIoT | 🤖 IoTHackBot | ⚡ Blitz |
|---|---|---|---|---|---|
| **Category** | Embedded/router exploitation framework | Local-proximity IoT pentest toolkit | IoT security testing & exploitation framework | AI-assisted IoT recon & hardware toolkit | Autonomous IoT/OT red-teaming platform |
| **Runs without a human at the keyboard** | ❌ Manual, one session at a time | ❌ Manual, one session at a time | ❌ Manual, one session at a time | ❌ Human/AI, command-by-command | ✅ **Fully autonomous, continuous operation** |
| **Finds new devices on its own** | ❌ You point it at a known target | ❌ You run discovery modules yourself | ❌ You select a target manually | ❌ You run `wsdiscovery` per session | ✅ **Continuous, automatic discovery** |
| **Decides what's worth testing** | ❌ You choose the exploit module | ❌ You choose the module | ❌ You choose the plugin | ⚠️ AI-assisted, but you drive it | ✅ **Ares plans the assessment itself** |
| **Stops unsafe actions before they run** | ❌ No gating — a misfire can crash the device | ❌ No gating | ❌ No gating | ⚠️ Disclaimer only, not enforced | ✅ **Multi-condition authorization gate, every action** |
| **Proves impact instead of guessing** | ❌ Pass/fail, no evidence trail | ❌ Manual write-up | ❌ Manual write-up | ❌ Manual output review | ✅ **"Attempted vs. Proven," evidence-backed** |
| **Confirms a fix actually worked** | ❌ Requires a fresh manual run | ❌ Requires a fresh manual run | ❌ Requires a fresh manual run | ❌ Requires a fresh manual run | ✅ **Automatic re-validation** |
| **Protocol coverage** | HTTP, Telnet, SNMP | BLE, WiFi, SSDP, mDNS, NFC | Broad, plugin-extensible | ONVIF, network traffic, firmware | **10 protocols, 48 validation modules** |
| **Hardware access (JTAG/UART/SWD)** | ❌ | ❌ | ✅ | ✅ | ✅ Targeted vulnerability checks against known firmware CVEs |

*Comparison based on each project's public documentation and repositories as of the date of this README; open-source tools evolve, so verify current capabilities against their latest releases.*

---

<a name="pricing"></a>
## 💰 The Real Cost of Waiting for Your Next Pentest

| | 🧑‍💻 Standard IT Pentest | 🔌 IoT/OT-Specific Pentest | 🎯 Red-Team-Level IoT Engagement | ⚡ Blitz |
|---|:---:|:---:|:---:|:---:|
| **Cost** | $5,000 – $100,000+ (commonly cited industry estimate) | **$10,000 – $40,000** per engagement | **$30,000 – $150,000+** | **$299 — once, early adopter** |
| **Billing model** | Per engagement | Per engagement, higher due to firmware/hardware work | $120–$350+/hr, senior tester day rates | Flat, one-time |
| **What you actually get** | One report, one point in time | One report — firmware analysis, protocol testing, one snapshot | Deep manual exploitation, still just one snapshot | **Continuous testing**, every device, as it appears |
| **Valid for how long?** | Stale the moment scope changes | Stale the moment a new device joins the network | Stale the day it's delivered | **Never goes stale — always running** |
| **Re-testing after a fix** | Rarely included, extra cost | Rarely included, extra cost | Rarely included, extra cost | ✅ **Automatic, included, always** |
| **Frequency you can realistically afford** | Once a year, if budget allows | Once a year, if at all | Once, maybe never repeated | **Every day** |
| **Cost vs. Blitz** | ~98% more expensive | **~97–99% more expensive** | **~99–99.8% more expensive** | **The baseline** |

> 🧮 **The honest math:** even against the *cheapest* IoT pentest quote on the market ($10,000), Blitz's early-adopter price costs **~97% less**. Against a realistic mid-range engagement ($25,000), that's **~99% less** — and unlike every row to its left, it doesn't stop working the day after you pay.

> 🎯 **You're not choosing between "cheap" and "thorough."**
> **You're choosing between paying once for a moment — or paying once for a process that never stops checking.**

**What your license actually buys you:**
- ✅ Continuous discovery — not a once-a-year snapshot
- 🧠 AI-driven, protocol-aware planning — Ares profiles before it acts
- 🔒 Gated, safe execution — nothing runs without clearance
- 📊 Proof, not guesswork — attempted vs. proven, always
- 🔁 Automatic re-validation — every fix, checked, every time

> ⚡ **Your devices are already connected. Already exposed. Already being watched — by someone.**
> **$299 decides who finds the weakness first — you, or them.**

---

## Commercial Licensing & Access

Blitz is distributed as an enterprise-grade, perpetual commercial package under **ApexPredator Security**. A single license grants perpetual operational rights to deploy the full autonomous stack on internal corporate infrastructure and authorized client engagements.

### License Tiers & Real-Time Availability

| Tier | Price | Availability | License Scope |
|---|---|---|---|
| **Early Adopter Cohort** | **$299** ~~$499~~ | **Active now** (code `EARLYBIRD`) | First 25 licenses only • Perpetual commercial rights |
| **Standard Commercial** | **$499** | Standard list price | Perpetual commercial rights • Unlimited targets & audits |

[![Purchase Blitz Commercial License](https://img.shields.io/badge/Purchase%20Blitz-%24299%20Early%20Adopter-brightgreen?style=for-the-badge&logo=github)](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)

---

### What Is Included in the License

- **Complete Autonomous Stack:** Blitz Core execution engine (`:8088`), Ares Agent reasoning layer (`:9010`), and Ares Bridge capability gateway (`:8089`).
- **Local, Air-Gapped AI Model:** Dedicated `qwen3-iot:1.7b` weights fine-tuned on 683 IoT attack scenarios. Runs offline on local hardware via Ollama (`:11435`) with zero telemetry leaving your network and zero recurring API token costs.
- **All 48 Protocol & Validation Modules:** Full coverage across RTSP, ONVIF, MQTT, CoAP, UPnP/SSDP, embedded HTTP/CGI, SSH, Telnet, SNMP, and automated proof verification.
- **12-Stage Closed-Loop Lifecycle:** Complete execution pipeline with multi-condition authorization gating (Authorized? In scope? Capability allowed?), a strict distinction between "attempted" and "proven" results, and persistent SQLite evidence storage.
- **Automated Deployment:** Ready-to-run `blitz-setup.sh` installer script and production `docker-compose.yml` configurations.
- **Perpetual Commercial Rights:** Unlimited internal asset coverage and external client penetration tests, with zero per-target, per-scan, or per-seat metering fees.
- **Continuous Updates:** Lifetime access to new protocol modules, CVE detection profiles, and engine enhancements.

---

<a name="faq"></a>
## ❓ FAQ

**Is Blitz safe to run against production devices?**
Yes — every action Ares proposes passes through the Ares Bridge's multi-condition authorization gate (authorized? in scope? capability allowed?) before it ever reaches a real device. That gate is what makes continuous, unattended testing viable on live infrastructure.

**Am I authorized to test devices I don't own?**
Only with explicit authorization from the asset owner — the same rule that governs any red-team or penetration-testing engagement. Blitz's scoping and authorization gate exist specifically to enforce that boundary; it is your responsibility to have written authorization in place for every target before you scan it.

**Does any data leave my network?**
No. The `qwen3-iot:1.7b` model that powers Ares runs locally via Ollama, so device context and reasoning stay on your infrastructure — zero telemetry, zero per-token API costs.

**Will the $299 price come back?**
No — the Early Adopter Cohort is capped at 25 licenses. Once those are claimed, price returns to the $499 standard list price shown above.

**Can I use one license across multiple client engagements?**
Yes. The license grants perpetual commercial rights with unlimited internal asset coverage and external client penetration tests — no per-target, per-scan, or per-seat fees.

**What happens after I buy?**
Checkout, repository access, and delivery are automated through Polar.sh (see the [payment walkthrough](#step-by-step-payment--automated-delivery-walkthrough) below) — no manual approval queue.

---

<a name="authorized-use"></a>
## 🛡️ Authorized Use Only

Blitz executes real attacks against real devices — credential attempts, protocol abuse, stream access, exploit chaining. It must be run **only** against infrastructure you own, or infrastructure you have explicit, written authorization to test, under the same rules that govern any penetration test or red-team engagement.

The authorization gate in Ares Bridge enforces scope at the tool level — it does not replace, and is not a substitute for, having that written authorization in place before you scan a target. ApexPredator Security & Labs provides Blitz as a testing platform; responsibility for lawful, authorized use of that platform rests with the licensee.

---

<a name="about"></a>
## 🏴 About ApexPredator Security & Labs

Blitz is built and maintained by **ApexPredator Security & Labs**, the research group behind the Ares AI reasoning engine and the closed-loop assessment methodology this platform runs on. Every module, protocol integration, and the fine-tuned `qwen3-iot:1.7b` model shipped with Blitz was built in-house specifically for IoT/OT offensive testing — this isn't a wrapper around existing open-source scanners.

*[ApexPredator — add a sentence or two here on team background, years active, prior research, or any public writeups/CVEs credited to the team. A named point of contact or a link to the org's research blog goes a long way toward buyer trust for a product in this category.]*

---

## 💬 Support & Updates

- **Included with every license:** lifetime access to new protocol modules, CVE detection profiles, and engine enhancements (see [What Is Included in the License](#what-is-included-in-the-license)).
- **Questions before you buy, or issues after:** *[ApexPredator — add a support email, docs site, or Discord/community link here.]*

---

## ⚙️ Installation & System Requirements

### 🖥️ System Requirements

| Requirement | Minimum | Recommended | Why It Matters |
|---|---|---|---|
| **OS** | Linux / macOS / Windows (WSL2) | Ubuntu 22.04 LTS | Blitz's core services and Docker networking are tested and most stable on Linux; WSL2 gives Windows users the same kernel-level container support. Ubuntu 22.04 LTS is the reference environment for long-term compatibility and support. |
| **CPU** | 4 cores | 8 cores | Ares' reasoning layer, Blitz Core's execution engine, and concurrent protocol scans (RTSP, ONVIF, MQTT, etc.) run as parallel workloads — more cores mean faster assessment cycles and the ability to test multiple devices simultaneously without queuing. |
| **RAM** | 8 GB | 16 GB | Local AI inference (via Ollama), persistent state storage, and live WebSocket event streaming all hold data in memory. 16 GB gives headroom for larger device inventories and longer-running continuous assessments without swapping. |
| **Disk** | 20 GB free | 40 GB free (SSD) | Persistent state (devices, jobs, findings, audit history) and locally-run AI models take real disk space — SSD is recommended because model loading and database I/O are latency-sensitive, especially under continuous operation. |
| **Docker Engine** | 24.x | Latest stable | Blitz's components (Operator Console, Ares Agent, Ares Bridge, Blitz Core) run as containerized services — Docker Engine is the runtime that isolates and orchestrates them. |
| **Docker Compose** | v2 | v2 | Used to define and launch the full multi-container stack (Console, Agent, Bridge, Core, Ollama) as a single coordinated deployment. |
| **Python** | 3.11+ | 3.11+ | Required for Blitz Core and supporting tooling — 3.11+ ensures compatibility with current dependency versions and performance improvements over earlier releases. |

### Two Ways to Install Blitz

**1. Recommended — packaged install.** Download the purchased Blitz package and transfer it to the directory where Blitz will be deployed. Blitz includes `blitz-setup.sh` for automated deployment.

```bash
unzip blitz-*.zip
cd blitz
ls -la
chmod +x blitz-setup.sh
./blitz-setup.sh
docker compose ps
docker compose logs -f
```

**2. Custom configuration — Docker Compose install.**

```bash
docker compose build --no-cache
docker compose up -d
docker compose ps
docker compose logs -f
```

Configure the values required by your deployment, including service endpoints, Ares integration, authentication settings, and runtime options. Blitz is running when the required containers report a healthy or running state according to your Compose configuration. If you hit errors during installation, do a full stop and restart:

```bash
docker compose down -v
docker compose build --no-cache
docker compose up -d
```

---

### Step-by-Step Payment & Automated Delivery Walkthrough

Payment processing, tax compliance, and repository access are automated through our Merchant of Record partner, **Polar.sh** (powered by Stripe). Fulfillment is programmatic — there is no manual verification queue or waiting period.

```
[ 1. Link GitHub Account ] ──► [ 2. One-Click Checkout ] ──► [ 3. Instant Repo Access & Zip Download ]
```

---

## 🙏 Acknowledgements

<div align="center">

**Blitz — Autonomous IoT Red Teaming & Continuous Assessment.**

*[ApexPredator — add current product/README version and last-updated date here, e.g. "v1.0 — September 2026", so buyers can confirm they're reading the current terms.]*

</div>
