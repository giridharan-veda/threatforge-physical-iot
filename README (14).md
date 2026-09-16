<div align="center">

<img src="https://raw.githubusercontent.com/giridharan-veda/threatforge-physical-iot/main/blitz-banner.svg" width="100%" alt="Blitz — Automated IoT Red Teaming Platform powered by Ares">

### an Automated IoT Red Teaming & Assessment Platform

**Stop guessing whether your  Internet of Things / Operational Technology devices are actually secure. Blitz autonomously hunts down every IoT/OT device on your network and upon authorization launches live real attacks against IoT, delivering proof of what's actually vulnerable.**

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Docker](https://img.shields.io/badge/Docker-Supported-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)
[![Ares AI](https://img.shields.io/badge/Ares-IoT%20AI%20Engine-purple)](#what-is-ares)
[![License](https://img.shields.io/badge/License-Commercial-red.svg)](LICENSE)
[![Price](https://img.shields.io/badge/Starting%20at-%24299-brightgreen)]()

[Overview](#overview) •
[Architecture](#architecture) •
[What is Blitz](#what-is-blitz) •
[What is Ares](#what-is-ares) •
[Capabilities](#capabilities) •
[Installation](#installation--system-requirements) •
[Best Practices](#best-practices--faqs)

</div>

---

## Overview

### ⚠️ The Risk - Security teams have spent two decades getting good at defending laptops and servers. Attackers noticed this and moved somewhere easier. 🎯

That somewhere is **IoT and OT**: the cameras, sensors, controllers, and gateways quietly running your buildings, your factories, your hospitals. They're on the same network as everything you actually protect — but almost none of the same rigor applies to them. Here's what that gap actually looks like in practice:

- 🕵️ **You can't defend what you can't see.** Most orgs don't even have a full inventory of their IoT/OT assets.
- 🔑 **The manufacturer's password is still the password.** `admin:admin`  default and unchanged, for the life of the device.
- 🚪 - **A service requires no authentication at all.** Video streams, control interfaces, mgt panels built to "just work," without security layers.
- 📡 **The traffic is unprotected.** No encryption means anything on the wire like credentials, pass keys is visible to anyone having the creds.
- 🧱 **"Segmented" is usually a belief, not a fact.** Flat networks and misconfigured VLANs put a compromised device a critical vulnerability.
- 🛠️ **Nothing here gets patched.** No update lifecycle exists for most embedded firmware, known weaknesses just persist.
- 🙈 **Detection tooling doesn't cover this layer.** Built for IT traffic, blind to IoT/OT — compromise here often goes unnoticed.
- 🎯 **The riskiest devices are tested the least**, because testing them safely takes expertise most teams don't any security for IoT.
- ✅❌ **"Fixed" is usually an assumption, not a fact.** Fixes rarely get re-verified, so "resolved" risk often isn't.

> 🚨 **This isn't the exception. It's the default state of every IoT/OT network — including yours.**
> The devices you trust the most are the ones you've tested the least. That's not bad luck. That's an open invitation.
---

## 🛡️ Enter --- **Blitz** - an **autonomous system** built to test IoT/OT security the way it actually needs to be tested!

<img src="https://github.com/giridharan-veda/threatforge-physical-iot/blob/main/blitz.png" width="100%" alt="Blitz — Automated IoT Red Teaming Platform powered by Ares">

- 🔍 Profiles each device first: what it is, what it speaks, what it's exposed to. Then it plans an attack built for that device.
- 🔒 Attack action passes an **authorization gate** before execution, safer to run continuously on live production infrastructure.
- 📊 Results are evidence-backed & labeled **attempted** or **proven**. Once a fix ships, Blitz goes back and revalidates automatically.
- ⚖️ Where Blitz stands out is the operating model, not the toolset: every tool above is **driven by a human**, cmd by cmd.
- 🕵️ Makes discovery, decision-making, execution, and proof **continuous and autonomous** running every day across the network.
- 🧠 Intelligence that decides when, where, and how to use them running without needing someone at the keyboard for every test.
  
### 🔍 Blitz vs. Established Open-Source IoT Security Tools

| Capability | 🛠️ RouterSploit | 🏠 HomePwn | 💥 EXPLIoT | 🤖 IoTHackBot | ⚡ Blitz |
|---|---|---|---|---|---|
| **Category** | Embedded/router exploitation framework | Local-proximity IoT pentest toolkit | IoT security testing & exploitation framework | AI-assisted IoT recon & hardware toolkit | Autonomous IoT/OT red-teaming platform |
| **Runs without a human at the keyboard** | ❌ Manual, one session at a time | ❌ Manual, one session at a time | ❌ Manual, one session at a time | ❌ Human/AI, command-by-command | ✅ **Fully autonomous, continuous operation** |
| **Finds new devices on its own** | ❌ You point it at a known target | ❌ You run discovery modules yourself | ❌ You select a target manually | ❌ You run `wsdiscovery` per session | ✅ **Continuous, automatic discovery** |
| **Decides what's worth testing** | ❌ You choose the exploit module | ❌ You choose the module | ❌ You choose the plugin | ⚠️ AI-assisted, but you drive it | ✅ **Ares plans the assessment itself** |
| **Stops unsafe actions before they run** | ❌ No gating — a misfire can crash the device | ❌ No gating | ❌ No gating | ⚠️ Disclaimer only, not enforced | ✅ **Multi-condition authorization gate, every action** |
| **Proves impact instead of guessing** | ❌ Pass/fail, no evidence trail | ❌ Manual write-up | ❌ Manual write-up | ❌ Manual output review | ✅ **"Attempted vs. Proven," evidence-backed** |
| **Confirms a fix actually worked** | ❌ Requires a fresh manual run | ❌ Requires a fresh manual run | ❌ Requires a fresh manual run | ❌ Requires a fresh manual run | ✅ **Automatic re-validation** |
| Protocol coverage | HTTP, Telnet, SNMP | BLE, WiFi, SSDP, mDNS, NFC | Broad, plugin-extensible | ONVIF, network traffic, firmware | 13 protocols, 48 modules |
| Hardware access (JTAG/UART/SWD) | ❌ | ❌ | ✅ | ✅ | ✅  Targeted vuln check for firmware cve's |

It first determines what is actually present in the target environment—devices, ports, services, protocols, authentication mechanisms, and exposed interfaces—and then selects assessment modules relevant to those specific surfaces.

### What Makes Blitz Different - Traditional IoT scanners often stop at statements such as:

> "Port 554 is open."

or:

> "This device appears to expose HTTP." Blitz goes further by determining,

> **"What does that service expose, how does it behave, what security controls protect it, and can the observed weakness be safely demonstrated?"**

For example, discovering an RTSP service is only the beginning. Blitz can identify the RTSP implementation, inspect its authentication behaviour, enumerate permitted stream endpoints where authorized, examine transport configuration, and determine whether an observed exposure can be validated without disrupting the camera or its video service. The same protocol-aware approach is applied across **HTTP/HTTPS, RTSP, ONVIF, MQTT, CoAP, UPnP/SSDP, SSH, Telnet, SNMP, TLS**, and other IoT-facing services.

### Technology Stack

<div align="center">

| Component | Role | Description |
|---|---|---|
| 🎛️ **Operator Console** | Human control plane for launching assessments and monitoring live results | The interface where a human stays in the loop — launching new assessments, reviewing what Ares is proposing, and approving or denying actions before they run. This is where authorization decisions actually happen. |
| 🧠 **Ares Agent** | AI orchestration layer that plans and sequences assessments | Profiles each discovered device, reasons about what's actually worth testing on it, and plans an intelligent, prioritized sequence of actions — rather than running a fixed checklist against everything it finds. |
| 🔒 **Ares Bridge** | Capability gateway that enforces what Ares is allowed to request | Sits between Ares and the execution engine as a hard boundary — every action Ares wants to take is checked against strict, multi-condition rules before it's ever allowed to reach a real device. This is what keeps autonomy safe. |
| 🖥️ **Ollama** | Local model runtime for private, on-premises AI inference | Runs the AI models that power Ares entirely on-premises — no data or device context ever has to leave your environment to generate an assessment plan. |
| ⚙️ **Blitz Core** | Assessment & execution engine (REST + WebSocket) that runs the full closed-loop lifecycle | The engine that actually executes approved actions, collects evidence, and drives the full lifecycle from discovery through proof — exposed via REST and WebSocket so every stage can be tracked and integrated. |
| 🗄️ **Persistent State** | Stores devices, jobs, findings, incidents, and complete audit history | The system of record — every device ever seen, every job ever run, every finding and incident, kept as a durable, auditable history rather than a one-time report that gets filed away. |
| 📡 **Live Event Stream** | Real-time WebSocket feed of progress, results, and narratives back to the operator through the GUI | Streams what's happening as it happens — progress updates, results, and plain-language narratives — so the operator watches the assessment unfold live instead of waiting for a final report. |

</div>

## Ares AI

**Ares** is the autonomous intelligence layer of the Blitz platform. It is the component that turns a collection of IoT security tools into a system capable of independent assessment.

<img src="https://raw.githubusercontent.com/giridharan-veda/threatforge-physical-iot/main/aresai.png" width="100%" alt="Blitz — Automated IoT Red Teaming Platform powered by Ares">

Most security tools require a human to decide what to scan, which credentials to try, which protocols to probe, and what to do next. Ares removes that dependency. It observes the current state of a target, reasons about what the device appears to be, and decides the next appropriate action from a list of attacks or capabilities.

Ares does not perform network attacks itself. That responsibility belongs to Blitz. Instead, Ares acts as a decision engine. It maintains a structured knowledge base of device profiles, protocol behaviours, known attack surfaces, and tool mappings. When new information is discovered — open ports, banners, services, or vendor signatures — Ares classifies the device and builds a ranked plan of what should be tested next.

The intelligence inside Ares is fine-tuned automatically when the decision points to choose the next tool, Surrounding that model is a loop that enforces workflow order, records every decision. This design keeps the system autonomous without making it unpredictable.

Ares understands IoT-specific contexts — cameras, brokers, routers, controllers, and their typical weaknesses — it can drive assessments that are more efficient than generic scanning. The result is a system that can progress through with minimal human intervention.

## What is the Ares Bridge

The **Ares Bridge** is the interface that sits between the intelligence layer (Ares) and the execution layer (Blitz). It is the component that makes the system extensible. Ares can decide what should happen, but the Bridge decides whether that request is allowed to proceed and how it is translated into an actual action.

During development, the Bridge was connected and tested with external AI systems such as **RedAmon** paired with **StrikeGPT**, experimenting blitz and ares conneted to strikegpt q4-k-m and redamon is highly recommendable. This same interface can accept decisions from different AI backends without changing the underlying execution engine. As a result, the Bridge connects Blitz to other AI APIs and LLM's.

Beyond AI integration, the Bridge also provides a clean path for connecting external systems such as SIEM platforms. Because all capability requests and results flow through a single, well-defined interface, events and findings can be forwarded to monitoring tools without touching the core engine.

## Ollama LLM in Blitz

**Ollama** is the local model runtime that powers the intelligence inside Ares. It runs a fine-tuned language model specialised for IoT security decisions.

The model used by Blitz is a 1.7-billion-parameter Qwen3 variant that was fine-tuned specifically for IoT assessment planning. It does not attempt to plan entire attack chains or interact with the network. Its only role is to answer one focused question at each step: given the current state of a device, which tool should be used next.

### How the Model Was Trained for IoT

The model was fine-tuned using QLoRA on a dataset of 683 IoT-specific examples. The training data combined real session exports with synthetic scenarios built around common IoT device families — cameras, routers, MQTT brokers, controllers, and similar systems.

Each training example presented the model with a compact device state (open ports, services, and basic context) and required it to select the most appropriate next tool from a fixed allowlist. The training process also included rationale distillation, so the model learned not only which tool to choose but why that choice made sense for a given device type.

This design of the LLM model contributes judgment at decision points, while the surrounding systems in Ares handle sequencing, thinking, persistence, and execution.

## Architecture

Blitz is designed as a **closed-loop automated red teaming system** specifically for IoT and OT environments.

<p align="center">
<img src="https://github.com/giridharan-veda/threatforge-physical-iot/blob/main/blitz-architecture.svg" width="100%" alt="Blitz — Automated IoT Red Teaming Platform powered by Ares">  
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
It first determines what is actually present in the target environment—devices, ports, services, protocols, authentication mechanisms, and exposed interfaces—and then selects assessment modules relevant to those specific surfaces.

### Protocol-Specific Attack Coverage

| Protocol | What It Tests | Common IoT Devices | Real-Time Validation |
|---|---|---|---|
| **HTTP / HTTPS** | Web login, admin pages, access control, input and configuration flaws | Cameras, routers, NVRs, NAS, smart hubs | Finds web services and paths, sends controlled requests, tests authentication and verifies access restrictions. |
| **RTSP** | Video-stream exposure and authentication | IP cameras, CCTV, DVRs, NVRs | Connects to RTSP, discovers streams, checks authentication and verifies whether restricted streams are accessible. |
| **ONVIF** | Camera management and authorization | IP/PTZ cameras, NVRs, VMS | Discovers ONVIF services, identifies camera capabilities and verifies authentication and management permissions. |
| **MQTT** | Broker security, topic access and publish/subscribe permissions | Sensors, gateways, smart-home and industrial IoT | Connects to the broker, checks authentication, discovers permitted topics and validates read/write ACLs. |
| **CoAP** | Resource exposure and access control | Sensors, smart lighting, thermostats, embedded IoT | Discovers CoAP resources and sends controlled requests to verify whether protected resources are accessible. |
| **UPnP / SSDP** | Device discovery and exposed control services | Routers, TVs, NAS, cameras, smart appliances | Discovers UPnP devices, maps their services and checks whether control interfaces are unnecessarily exposed. |
| **SSH** | Remote administration and authentication | IoT gateways, routers, NAS, embedded Linux devices | Identifies SSH, checks configuration and authentication, and validates authorized remote access. |
| **Telnet** | Insecure remote administration | Legacy routers, cameras, DVRs, embedded devices | Detects Telnet, evaluates authentication and confirms whether administrative access is exposed over plaintext remote management. |
| **SNMP** | Management access and information exposure | Routers, switches, printers, UPS, cameras | Identifies SNMP, tests authorized credentials/community strings and checks what management information is accessible. |
| **TLS** | Encryption, certificates and cryptographic configuration | HTTPS cameras, routers, gateways, MQTT services, APIs | Establishes a TLS connection, examines supported versions/ciphers and validates certificate and transport security. |

## ATT&CK Matrix

<img src="https://github.com/giridharan-veda/threatforge-physical-iot/blob/main/ares-attack-matrix.svg" width="100%" alt="Blitz — Automated IoT Red Teaming Platform powered by Ares">

### The Ultimate Autonomous IoT Red Teaming Arsenal

Blitz transforms fragmented IoT assessment tasks into a high-speed, automated offensive workbench. Whether auditing physical facilities, competing in CTF arenas, or stress-testing hardware in a staging lab, Blitz and the Ares AI engine deliver seven integrated operational capabilities:

### Operational Modes Matrix

| Mode / Feature | Primary Target Surface | Autonomy Level | Primary Output |
|---|---|---|---|
| **Autonomous AutoPwn** | Multi-protocol IoT subnets | Fully Autonomous | Chained compromise proofs |
| **Protocol Fuzzing** | MQTT, CoAP, RTSP, ONVIF | Configurable concurrency | Crash logs & input boundary flaws |
| **Firmware Carving** | Raw embedded binary images | Automated batch | Extracted secrets & CGI vulnerabilities |
| **Ghost Recon** | Layer 2 broadcast domains | Passive to high-throughput | Device topology & identity maps |
| **BYO-Brain Engine** | Planning & reasoning layer | AI-Directed | Execution plans & tool selection |
| **CTF Arena Mode** | Staging labs & QEMU images | Real-Time Interactive | Live streaming WebSocket feed |
| **Re-Validation Loop** | Post-remediation targets | Targeted automated replay | Fix attestation & regression reports |


---

### 1. Autonomous AutoPwn & Exploit Chaining Loop
Eliminate disjointed scripts and manual credential handoffs. The Ares AI reasoning engine analyzes device state, correlates exposure vectors, and chains multi-stage validation paths automatically:
* **Dynamic Pivoting:** Ares identifies an anonymous MQTT broker, subscribes to wildcard topics (`#`), extracts credentials from broadcast device telemetry, and validates access against exposed administrative or RTSP services on adjacent subnets.
* **Impact Verification:** Extracts cryptographic and operational proof (video frame captures, broker ACL write confirmations, or directory listings) into persistent state storage without human intervention.

### 2. Multi-Protocol Chaos Fuzzing Engine
Generic web application scanners fail when probing constrained hardware protocols. Blitz deploys native protocol engines across all 48 specialized testing modules simultaneously:
* **Protocol Diversity:** Native query and assessment engines for MQTT, CoAP, RTSP, ONVIF, UPnP/SSDP, embedded CGI, raw TCP sockets, and legacy Telnet/SSH services.
* **Boundary Validation:** Detects malformed packet handling, memory exhaustion conditions, and logic flaws across embedded network stacks (such as lwIP, FreeRTOS, and Zephyr).

### 3. Automated Firmware Decapitation & Taint Mining
Ingest raw `.bin`, `.img`, or firmware packages directly into the analysis pipeline for automated inspection:
* **Automated Extraction:** Decompresses and extracts standard embedded file systems, including SquashFS, CramFS, UBIFS, and JFFS2.
* **Secret & Vulnerability Extraction:** Scans the extracted root filesystem for hardcoded private cryptographic keys, embedded credentials, default tokens, and debug CGI binaries.

### 4. Ghost Recon (Zero-Noise Stealth to High-Velocity Sweeps)
Configure discovery intensity anywhere from silent network sniffing to high-throughput active scanning:
* **Passive Listener Mode:** Passively maps local environments by monitoring ambient mDNS, UPnP, SSDP, and ARP broadcasts without transmitting packets on the wire.
* **High-Speed Network Sweep:** Executes parallel multi-protocol host discovery with Layer 2 adjacency, identifying device vendor, model, firmware revision, and exposed surfaces.

### 5. BYO-Brain: Hot-Swappable AI Model Engine
Ares utilizes an open, modular capability bridge rather than a locked AI provider:
* **Air-Gapped Local Inference:** Ships configured with the fine-tuned `qwen3-iot:1.7b` model running offline via local Ollama (`:11435`) to ensure zero external telemetry and zero per-token API costs.
* **Model Hot-Swapping:** Route requests through the Ares Bridge (`:8089`) to alternate local or remote model endpoints (such as DeepSeek-Coder, Llama, or Mistral) to evaluate different reasoning models against identical targets.

### 6. Hardware Lab & CTF Arena Mode
Engineered for repeatable experimentation in staging and competitive environments:
* **Live WebSocket Telemetry:** Streams raw operational decision graphs and execution telemetry directly to terminal consoles or custom dashboards over WebSocket port `:8088`.
* **Target Emulation Compatibility:** Deploy against virtualized or physical targets (via Docker, QEMU, or hardware test benches) to run repeatable attack simulations against simulated camera arrays, smart meters, and industrial IoT controllers.

### 7. Instant Proof-of-Impact & Remediation Diffs
Converts automated test data into verifiable technical artifacts:
* **Attempted vs. Proven Telemetry:** Eliminates speculative findings by strictly separating an initial service probe from a cryptographically or functionally confirmed vulnerability.
* **Closed-Loop Re-Validation:** Following remediation, execute Stage 12 (**Re-validate**) to automatically replay the verified exploit chain and confirm whether the vulnerability was mitigated without running an entire re-scan.

---

### 💸 The Real Cost of "Waiting for Your Next Pentest"

| | 🧑‍💻 Standard IT Pentest | 🔌 IoT/OT-Specific Pentest | 🎯 Red-Team-Level IoT Engagement | ⚡ Blitz |
|---|:---:|:---:|:---:|:---:|
| **Cost** | $5,000 – $100,000+ (avg **$18,300**) | **$10,000 – $40,000** per engagement | **$30,000 – $150,000+** | **$499 — once** |
| **Billing model** | Per engagement | Per engagement, higher due to firmware/hardware work | $120–$350+/hr, senior tester day rates | Flat, one-time |
| **What you actually get** | One report, one point in time | One report — firmware analysis, protocol testing, one snapshot | Deep manual exploitation, still just one snapshot | **Continuous testing**, every device, as it appears |
| **Valid for how long?** | Stale the moment scope changes | Stale the moment a new device joins the network | Stale the day it's delivered | **Never goes stale — always running** |
| **Re-testing after a fix** | Rarely included, extra cost | Rarely included, extra cost | Rarely included, extra cost | ✅ **Automatic, included, always** |
| **Frequency you can realistically afford** | Once a year, if budget allows | Once a year, if at all | Once, maybe never repeated | **Every day** |
| **Cost vs. Blitz** | ~97% more expensive | **~95–99% more expensive** | **~98–99.7% more expensive** | **The baseline** |

---

> 🧮 **The honest math:** even against the *cheapest* IoT pentest quote on the market ($10,000), Blitz costs **~95% less**. Against a realistic mid-range engagement ($25,000), that's **~98% less** — roughly **one-fiftieth the price** — and unlike every row to its left, it doesn't stop working the day after you pay.

> 🎯 **You're not choosing between "cheap" and "thorough."**
> **You're choosing between paying once for a moment — or paying once for a process that never stops checking.**

## ⚡ Why Blitz Is Worth Every Dollar, Run the numbers honestly:

> 🔥 **A manual pentest gives you a moment. A scanner gives you noise. Blitz gives you an autonomous red team that never clocks out.** ⏱️
- 💸 A manual IoT/OT pentest costs **$15,000–$50,000+** — for one report, valid for exactly one day, stale the moment a new device joins your network.
- 💣 One unpatched IoT device is often all it takes — the single entry point behind breaches that costs **millions**, downtime, response, and regulatory fallout.
- ⚖️ Against that math, **$499 isn't an expense. It's the cheapest insurance policy on your entire risk register.**

### What $499 Actually Buys You

- ✅ **Continuous discovery** — not a once-a-year snapshot
- 🧠 **AI-driven, protocol-aware planning** — Ares profiles before it acts
- 🔒 **Gated, safe execution** — nothing runs without clearance
- 📊 **Proof, not guesswork** — attempted vs. proven, always
- 🔁 **Automatic re-validation** — every fix, checked, every time

That's not a tool. That's a **red team that works while you sleep.** 🌙

> 🎯 **Your devices are already connected. Already exposed. Already being watched — by someone.**
> 🔓 **$499 decides who finds the weakness first — you, or them.**
> ⚡ **Blitz. The autonomous red team the IoT era needed yesterday.**

## The Ultimate Autonomous IoT Red Teaming Arsenal

### 💰 Blitz vs. Whatever You've Tried Before

| | 🧑‍💻 Manual Pentest | 🖥️ Generic Scanner / AI Tool | ⚡ Blitz |
|---|---|---|---|
| **Cost** | $15K–$50K+ per engagement | "Free" — until it misses everything that matters | **$499** |
| **Frequency** | Once or twice a year, if budget allows | Runs often, tells you nothing useful | **Continuous — every day, every new device** |
| **Understands IoT/OT protocols** | Depends entirely on who you hired | ❌ Built for IT, blind to RTSP/ONVIF/MQTT/CoAP | ✅ **Purpose-built for IoT/OT from the ground up** |
| **Safe on fragile production devices** | Depends on the tester's experience | ❌ Aggressive, generic actions — can crash a device | ✅ **Gated execution, every single action** |
| **Context-aware before acting** | Yes, but slow and manual | ❌ No device context — fires blind | ✅ **Ares profiles each device before testing it** |
| **Findings you can trust** | Expert-validated, but only that one day | ❌ Alerts and false positives, no proof | ✅ **Attempted vs. Proven — always evidence-backed** |
| **Re-checks that fixes actually worked** | Rarely — costs extra, needs re-engagement | ❌ Never | ✅ **Automatic re-validation, built in** |
| **Scales across your entire estate** | ❌ Limited by human hours | ⚠️ Scales, but shallow | ✅ **Scales without losing depth** |
| **Audit / compliance ready** | One static report, stale in weeks | ❌ Raw output, not evidence | ✅ **Living, dated, defensible record** |
| **What you're really left with** | A snapshot from one day, months ago | A dashboard full of noise | 🎯 **Continuous, proven, actionable truth** |

---

## Commercial Licensing & Access

Blitz is distributed as an enterprise-grade, perpetual commercial package under **ApexPredator Security**. A single license grants perpetual operational rights to deploy the full autonomous stack on internal corporate infrastructure and authorized client engagements.

### License Tiers & Real-Time Availability

| Tier | Price | Availability | License Scope |
|---|---|---|---|
| **Early Adopter Cohort** | **$299** ~~$499~~ | **Active Now** (Code: `EARLYBIRD`) | **First 25 Licenses Only** • Perpetual commercial rights |
| **Standard Commercial** | **$499** | Standard List Price | Perpetual commercial rights • Unlimited targets & audits |

[![Purchase Blitz Commercial License](https://img.shields.io/badge/Purchase%20Blitz-%24299%20Early%20Adopter-brightgreen?style=for-the-badge&logo=github)](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)

---

### What Is Included in the License

* **Complete Autonomous Stack:** Blitz Core execution engine (`:8088`), Ares Agent reasoning layer (`:9010`), and Ares Bridge capability gateway (`:8089`).
* **Local, Air-Gapped AI Model:** Dedicated `qwen3-iot:1.7b` weights fine-tuned on 683 IoT attack scenarios. Runs offline on local hardware via Ollama (`:11435`) with zero telemetry leaving your network and zero recurring API token costs.
* **All 48 Protocol & Validation Modules:** Full coverage across RTSP, ONVIF, MQTT, CoAP, UPnP/SSDP, embedded HTTP/CGI, SSH, Telnet, SNMP, and automated proof verification.
* **12-Stage Closed-Loop Lifecycle:** Complete execution pipeline with multi-condition authorization gating (Authorized? In scope? Capability allowed?), distinction between "attempted" vs. "proven" results, and persistent SQLite evidence storage[cite: 1].
* **Automated Deployment:** Ready-to-run `blitz-setup.sh` installer script and production `docker-compose.yml` configurations[cite: 1].
* **Perpetual Commercial Rights:** Unlimited internal asset coverage and external client penetration tests with zero per-target, per-scan, or per-seat metering fees.
* **Continuous Updates:** Lifetime access to new protocol modules, CVE detection profiles, and engine enhancements.

---

### Step-by-Step Payment & Automated Delivery Walkthrough

Payment processing, tax compliance, and repository access are automated through our Merchant of Record partner, **Polar.sh** (powered by Stripe). Fulfillment is programmatic—there is no manual verification queue or waiting period.

[ 1. Link GitHub Account ] ──► [ 2. One-Click Checkout  ] ──► [ 3. Instant Repo Access & Zip Download ]



# Blitz — Installation Guide

## 🖥️ System Requirements

| Requirement | Minimum | Recommended | Why It Matters |
|---|---|---|---|
| **OS** | Linux / macOS / Windows (WSL2) | Ubuntu 22.04 LTS | Blitz's core services and Docker networking are tested and most stable on Linux; WSL2 gives Windows users the same kernel-level container support. Ubuntu 22.04 LTS is the reference environment for long-term compatibility and support. |
| **CPU** | 4 cores | 8 cores | Ares' reasoning layer, Blitz Core's execution engine, and concurrent protocol scans (RTSP, ONVIF, MQTT, etc.) run as parallel workloads — more cores mean faster assessment cycles and the ability to test multiple devices simultaneously without queuing. |
| **RAM** | 8 GB | 16 GB | Local AI inference (via Ollama), persistent state storage, and live WebSocket event streaming all hold data in memory. 16 GB gives headroom for larger device inventories and longer-running continuous assessments without swapping. |
| **Disk** | 20 GB free | 40 GB free (SSD) | Persistent state (devices, jobs, findings, audit history) and locally-run AI models take real disk space — SSD is recommended because model loading and database I/O are latency-sensitive, especially under continuous operation. |
| **Docker Engine** | 24.x | Latest stable | Blitz's components (Operator Console, Ares Agent, Ares Bridge, Blitz Core) run as containerized services — Docker Engine is the runtime that isolates and orchestrates them. |
| **Docker Compose** | v2 | v2 | Used to define and launch the full multi-container stack (Console, Agent, Bridge, Core, Ollama) as a single coordinated deployment. |
| **Python** | 3.11+ | 3.11+ | Required for Blitz Core and supporting tooling — 3.11+ ensures compatibility with current dependency versions and performance improvements over earlier releases. |

## Two ways to install blitz:

1. Recommended - Download the purchased Blitz package and transfer it to the directory where Blitz will be deployed. Blitz includes blitz-setup.sh for automated deployment.

```bash
unzip blitz-*.zip
cd blitz
ls -la
chmod +x blitz-setup.sh
./blitz-setup.sh
docker compose ps
docker compose logs -f

```
2. Custom values configuration using Docker Compose Installation

```bash

docker compose build --no-cache
docker compose up -d
docker compose ps
docker compose logs -f

```

Configure the values required by the supplied Blitz deployment, including service endpoints, Ares integration, authentication settings, and runtime options. Blitz is running when the required containers report a healthy or running state according to the supplied Compose configuration. perform a full stop and start if encountered errors during installation:

```bash

docker compose down -v
docker compose build --no-cache
docker compose up -d

```

## Contributing to Blitz

### Priority Contribution Tracks

* **New Protocol Modules (`blitz-core/`):** Add native decoders and active probes for unmapped embedded interfaces (e.g., BACnet, Modbus, Zigbee over IP, or proprietary camera APIs).
* **Ares AI Reasoning & Heuristics (`ares/`):** Refine planning prompts, fine-tuning datasets, and tool-selection heuristics to improve decision velocity on complex target states.
* **Gateway & Blast-Radius Safety (`ares/bridge/`):** Strengthen the Ares Bridge to catch erratic AI behavior, prevent cyclic planning loops, and enforce strict execution boundaries.
* **Target Hardware Signatures (`configs/`):** Expand device identification matrices and service fingerprint rules in `capabilities.yaml`.
---

## Citation

If you reference Blitz or the Ares AI architecture in academic research, technical whitepapers, security assessments, or publications, please cite this repository using the included. BibTeX and standard citation formats are generated automatically by GitHub.

---

## Disclaimer

- Blitz is engineered strictly for authorized security assessment, defensive evaluation, vulnerability research, and continuous risk validation on networks, devices, and firmware where explicit written authorization has been.
- It is designed to be deployed in controlled staging labs, isolated target ranges, and approved client assessment scopes.
- ApexPredator Security and the project authors assume no liability and are not responsible for any misuse, operational disruption, device malfunction, or unauthorized deployment of this software.
- Operators are solely responsible for maintaining compliance with all applicable local, national, and international cybersecurity legislation, organizational policies, and statutory frameworks prior to executing any discovery, assessment, or validation workflow.

---

## License

- Blitz is proprietary commercial software distributed under the terms of the ApexPredator Security Commercial License. 
- A valid commercial license purchase is required to install, deploy, and operate the platform for internal estate assessments or commercial client engagements.
- Redistribution, sublicensing, unauthorized mirroring, or public sharing of the core binaries, source repositories, or fine-tuned model artifacts is strictly prohibited.
  
---

## Acknowledgements

Blitz and the Ares AI orchestration framework build upon outstanding open-source software, protocols, and developer communities[cite: 1]:

* **Ollama** — Enabling private, efficient, on-premises language model execution[cite: 1].
* **Qwen Team** — The foundational model architecture supporting the fine-tuned `qwen3-iot:1.7b` reasoning engine[cite: 1].
* **Docker** — Delivering reliable, isolated, and containerized deployment across host environments[cite: 1].
* **Python Community** — Providing the network engineering, asynchronous I/O, and testing libraries powering Blitz Core[cite: 1].

<div align="center">

**Blitz — Autonomous IoT Red Teaming & Continuous Assessment.**
</div>
