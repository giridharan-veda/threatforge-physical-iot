<div align="center">

<img src="https://raw.githubusercontent.com/giridharan-veda/threatforge-physical-iot/main/blitz-banner.svg" width="100%" alt="Blitz — Autonomous IoT Red Teaming Platform powered by Ares">

### ⚡ The Autonomous IoT/OT Red Teaming & Continuous Assessment Platform

**Stop guessing whether your Internet of Things / Operational Technology devices are actually secure. Blitz autonomously hunts down every IoT/OT device on your network upon authorization, launches live attacks against them — delivering proof of what's actually vulnerable.**

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Docker](https://img.shields.io/badge/Docker-Supported-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)
[![Ares AI](https://img.shields.io/badge/Ares-IoT%20AI%20Engine-purple)](#ares-ai)
[![Modules](https://img.shields.io/badge/Modules-154-informational)](#protocol-specific-attack-coverage)
[![Categories](https://img.shields.io/badge/Categories-28-blueviolet)](#protocol-specific-attack-coverage)
[![License](https://img.shields.io/badge/License-Commercial-red.svg)](LICENSE)
[![LLM](https://img.shields.io/badge/LLM-ares--1.7b-blue)](#ares-ai)
[![Community](https://img.shields.io/badge/ApexPredator-Community-orange)](#who-this-is-for)
[![Price](https://img.shields.io/badge/Early%20Adopter-%24299-brightgreen)](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)

**🔥 Early Adopter Cohort — $299, first 25 licenses only, code `EARLYBIRD` • $499 standard list price • Perpetual commercial rights • Lifetime updates**

[![Purchase Blitz Commercial License](https://img.shields.io/badge/Purchase%20Blitz-%24299%20Early%20Adopter-brightgreen?style=for-the-badge&logo=github)](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)

[Overview](#overview) •
[Who This Is For](#who-this-is-for) •
[Ares AI](#ares-ai) •
[Attack Surface](#protocol-specific-attack-coverage) •
[Architecture](#architecture) •
[Capabilities](#capabilities) •
[Blitz vs. Alternatives](#comparison) •
[Pricing](#pricing) •
[Licensing & Pricing](#commercial-licensing--access) •
[FAQ](#faq) •
[Authorized Use](#authorized-use) •
[About](#about) •
[Installation](#installation--system-requirements)

</div>

---

## What Blitz Actually Does

```console
$ blitz scan 192.168.1.0/24

[SCAN]      Discovered 4 IoT devices
[CLASSIFY]  192.168.1.50 → Hikvision IP camera  (confidence 0.94)
[CLASSIFY]  192.168.1.51 → Dahua NVR            (confidence 0.87)
[CLASSIFY]  192.168.1.60 → Raspberry Pi          (confidence 0.91)
[CLASSIFY]  192.168.1.70 → Unknown device        (investigating...)

[PLAN]      Ares planning assessment for 192.168.1.50
            → firmware-identify → http-banner-info-disclosure
            → rtsp-default-credentials → firmware-cve-match

[AUTHORIZE] ✓ authorized | ✓ in scope | ✓ non-destructive → PROCEED

[EXECUTE]   firmware-identify ............ Hikvision DS-2CD, firmware 5.6.3
[EXECUTE]   http-banner-info-disclosure .. Server: webs, PHP/5.4.16
[EXECUTE]   rtsp-default-credentials ..... ✓ admin:admin accepted
[EXECUTE]   firmware-cve-match ........... CVE-2021-36260 applicable

[PROVE]     CRITICAL — Unauthenticated RCE available
            Evidence:  evidence/192.168.1.50/CVE-2021-36260-probe.txt
            State:     PROVEN (not attempted)

Assessment complete in 47 seconds. 4 devices, 3 findings (1 critical).
```

Every competitor's README says "autonomous testing." **Blitz shows you what that looks like.**

---

<a name="who-this-is-for"></a>
## 👥 Who Blitz Is For

<table>
<tr>
<td width="50%" valign="top">

### 🔬 Security Researchers

Study how LLMs perform on real IoT attack planning. The full training pipeline — SFT, GRPO, RFT, curriculum — is documented and reproducible. Retrain on your own data with a single 8 GB GPU.

**Start here →** [Ares AI training pipeline](#ares-ai)

</td>
<td width="50%" valign="top">

### 🏢 Enterprise Security Teams

Replace $25,000 annual engagements with continuous automated assessment. Every finding is evidence-backed. Every fix is automatically re-validated. No data leaves your network.

**Start here →** [Why Blitz vs. pentests](#pricing)

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🛠️ Red Teams & Consultants

154 modules across firmware, wireless, cloud, mobile, and voice assistants — no other tool covers this much of the IoT attack surface. No new hardware required for network testing.

**Start here →** [Attack surface coverage](#protocol-specific-attack-coverage)

</td>
<td width="50%" valign="top">

### 🎯 Lab & CTF Enthusiasts

Deploy against QEMU device farms or your own home lab. Every module documents its preconditions. Safe to run against devices you own.

**Start here →** [Installation](#installation--system-requirements)

</td>
</tr>
</table>

---

## Overview

### ⚠️ The Risk — Security teams have spent two decades getting good at defending laptops and servers. Attackers noticed, and moved somewhere easier. 🎯

That somewhere is **IoT and OT**: the cameras, sensors, controllers, and gateways quietly running your buildings, your factories, your hospitals. They're on the same network as everything you actually protect — but almost none of the same rigor applies to them. Here's what that gap looks like in practice:

| The Gap                            | What It Looks Like in Practice                                                  |
| :--------------------------------- | :------------------------------------------------------------------------------ |
| 🕵️ **Invisible inventory**         | Most orgs don't have a full inventory of their IoT/OT assets.                   |
| 🔑 **Default passwords**           | `admin:admin`, default and unchanged, for the life of the device.               |
| 🚪 **Unauthenticated services**    | Video streams, control interfaces, and management panels built to "just work."  |
| 📡 **Plaintext traffic**           | No encryption means anything on the wire — credentials, keys — is visible.      |
| 🧱 **"Segmented" is a belief**     | Flat networks and misconfigured VLANs turn one device into a path to everything. |
| 🛠️ **Nothing gets patched**        | No update lifecycle exists for most embedded firmware; known weaknesses persist. |
| 🙈 **Detection blind spots**       | IT security tooling is blind to IoT/OT — compromise often goes unnoticed.       |
| 🎯 **Riskiest, tested least**      | Testing these safely takes expertise most teams don't staff for.                |
| ✅❌ **"Fixed" is assumed**        | Fixes rarely get re-verified, so "resolved" risk often isn't.                    |

> 🚨 **This is the default state of every IoT/OT network — including yours.** The devices you trust most are the ones you've tested least.

---

## 🛡️ Enter — Blitz

**Blitz** is an **autonomous system** built to test IoT/OT security the way it actually needs to be tested.

<img src="https://github.com/giridharan-veda/threatforge-physical-iot/blob/main/blitz.png" width="100%" alt="Blitz — Autonomous IoT Red Teaming Platform powered by Ares">

- 🔍 **Profiles each device first** — what it is, what it speaks, what it's exposed to — then plans an attack built for that device.
- 🔒 **Every action passes an authorization gate** before execution, so it's safe to run continuously against live production infrastructure.
- 📊 **Results are evidence-backed**, labeled *attempted* or *proven*. Once a fix ships, Blitz revalidates it automatically.
- ⚖️ **The real difference is the operating model, not the toolset.** Every comparable tool on the market is driven by a human.
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

Discovering an RTSP service, for example, is only the beginning. Blitz identifies the RTSP implementation, inspects its authentication behavior, enumerates permitted stream endpoints where authorized, examines transport configuration, and determines whether the observed exposure can be validated against the live camera or video service. The same protocol-aware approach applies across **154 modules spanning 28 attack categories** — from network protocols to firmware, wireless, cloud, mobile apps, and voice-assistant ecosystems.

### Technology Stack

<div align="center">

| Component                  | Role                                                              | Description                                                                                                                                                                                                                     |
| :------------------------- | :---------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 🎛️ **Operator Console**   | Human control plane for launching assessments and monitoring live results | The interface where a human stays in the loop — launching new assessments, reviewing what Ares is proposing, and approving or denying actions before they run. This is where authorization decisions happen.                      |
| 🧠 **Ares Agent**          | AI orchestration layer that plans and sequences assessments       | Profiles each discovered device, reasons about what's actually worth testing on it, and plans an intelligent, prioritized sequence of actions — rather than running a fixed checklist against everything it finds.               |
| 🔒 **Ares Bridge**         | Capability gateway that enforces what Ares is allowed to request  | Sits between Ares and the execution engine as a hard boundary — every action Ares wants to take is checked against strict, multi-condition rules before it ever reaches a real device. This is what keeps autonomy safe.          |
| 🖥️ **Ollama**             | Local model runtime for private, on-premises AI inference        | Runs the AI models that power Ares entirely on-premises — no data or device context ever has to leave your environment to generate an assessment plan.                                                                           |
| ⚙️ **Blitz Core**          | Assessment & execution engine (REST + WebSocket)                  | The engine that executes approved actions, collects evidence, and drives the full lifecycle from discovery through proof — exposed via REST and WebSocket so every stage can be tracked and integrated.                          |
| 🗄️ **Persistent State**   | Stores devices, jobs, findings, incidents, and complete audit history | The system of record — every device ever seen, every job ever run, every finding and incident — kept as a durable, auditable history rather than a one-time report that gets filed away.                                          |
| 📡 **Live Event Stream**   | Real-time WebSocket feed to the operator GUI                      | Streams what's happening as it happens — progress updates, results, plain-language narratives — so the operator watches the assessment unfold live instead of waiting for a final report.                                        |

</div>

---

<a name="ares-ai"></a>
## 🧠 Ares AI

**Ares** is the autonomous intelligence layer of the Blitz platform — the component that turns a collection of IoT security tools into a system capable of independent assessment.

<img src="https://raw.githubusercontent.com/giridharan-veda/threatforge-physical-iot/main/aresai.png" width="100%" alt="Ares — the AI reasoning engine inside Blitz">

Most security tools require a human to decide what to scan, which credentials to try, which protocols to probe, and what to do next. Ares removes that dependency: it observes the current state of a target, reasons about what the device appears to be, and decides the next appropriate action from **154 defined modules across 28 attack categories**.

Ares does not perform network attacks itself — that responsibility belongs to Blitz Core. Ares acts purely as a decision engine. It maintains a structured knowledge base of device profiles, protocol behaviors, known attack surfaces, and tool mappings. When new information is discovered — open ports, banners, services, vendor signatures — Ares classifies the device and builds a plan of what should be done next.

The model powering Ares is fine-tuned specifically to make that call — which module is the right next step at each decision point. Because Ares understands IoT-specific context (cameras, brokers, routers, controllers, cloud platforms, and their typical weaknesses), it drives assessments that are meaningful rather than generic scanning. The result is a system that can move through an assessment with minimal human intervention.

### 🔌 Ares Bridge

The **Ares Bridge** sits between the intelligence layer (Ares) and the execution layer (Blitz). It's the component that makes the system extensible: Ares decides what should happen, but the Bridge decides whether that request is allowed to proceed and turns it into an actual action.

During development, the Bridge was tested against external AI backends — including RedAmon paired with StrikeGPT (`q4-k-m` quantization) — to confirm the interface can accept decisions from third-party planning systems without any change to the underlying execution engine. As a result, the Bridge connects Blitz to other AI APIs and LLMs beyond the default stack.

Beyond AI integration, the Bridge also provides a clean path for connecting external systems such as SIEM platforms. Because every request and result flows through a single interface, events and findings can be forwarded to monitoring tools without touching the core engine.

### 🖥️ Ollama LLM in Blitz

**Ollama** is the local model runtime that powers the intelligence inside Ares. The model Blitz ships with — **`ares`** — is a 1.7-billion-parameter Qwen3 variant fine-tuned specifically for IoT pentesting. It doesn't plan entire attack chains or interact with the network — its only job is to answer one question at a time: given the current state of a device, which module should run next.

Because the model runs locally via Ollama, **device context and reasoning never leave your network**. There are no per-token API costs, no external telemetry, and no dependency on a cloud vendor's uptime.

### How Ares Was Trained

The model was trained in **four stages**, each documented and reproducible on a single 8 GB GPU in under 3 hours. The full pipeline ships with Blitz in `/training/`.

#### Stage 1 — Supervised Fine-Tuning (SFT)

- Base model: `unsloth/Qwen3-1.7B`
- Dataset: 638 curated examples spanning all 154 modules
- Method: QLoRA (rank 16, alpha 32, 4-bit base)
- Training time: ~25 min on an RTX 4060
- Result: ~85% correct module routing

#### Stage 2 — GRPO (Group Relative Policy Optimization)

- Rule-based reward function enforcing:
  - Valid JSON output (`+1.0`)
  - Module ID in known catalog (`+2.0`)
  - No hallucinated module IDs (`+1.0`)
  - Correct refusal on destructive actions (`+3.0`)
  - No `<think>` block emissions (`-0.5` penalty)
- Generates multiple candidates per prompt; reinforces high-scoring trajectories
- Result: ~98% valid JSON, ~92% correct routing, 100% safety-refusal accuracy

#### Stage 3 — Rejection Sampling Fine-Tuning (RFT)

- Self-improvement loop: generates 3 candidates per prompt, keeps the best
- Expands the training set from 638 → ~1,000 examples with no new human labels
- No teacher model required — the model improves itself

#### Stage 4 — Curriculum Learning

- Training data sorted by difficulty (short routing → multi-turn chains → refusal cases)
- Smoother gradient flow, lower training variance
- Result: +1–3% final accuracy and more consistent outputs

### The Reward Function (Actual Code)

```python
def reward(completion):
    r = 1.0 if valid_json(completion) else -1.0
    mid = extract_module_id(completion)
    if mid in CATALOG:
        r += 2.0
    if all_ids_in_catalog(completion):
        r += 1.0
    if refused_destructive(mid):
        r += 3.0
    elif ran_destructive_without_auth(mid):
        r -= 2.0
    if emitted_think_block(completion):
        r -= 0.5
    return r
```

The entire training pipeline is included. Retrain on your own engagement data using the same scripts.

In this design, the model contributes judgment at each decision point, while the surrounding systems in Ares handle sequencing, state, persistence, and execution.

---

## Architecture

Blitz is designed as a **closed-loop automated red teaming system** built specifically for IoT and OT environments.

<p align="center">
<img src="https://github.com/giridharan-veda/threatforge-physical-iot/blob/main/blitz-architecture.svg" width="100%" alt="Blitz — Autonomous IoT Red Teaming Platform powered by Ares">
</p>

### Data Flow & Ports

| Hop                          | Protocol / Port                                     | Description                                                          |
| :--------------------------- | :-------------------------------------------------- | :------------------------------------------------------------------- |
| Operator → Ares Agent        | Internal                                            | Assessment request and high-level job launch                         |
| Ares Agent → Ares Bridge     | Internal (`:8089`)                                  | Capability requests are gated and authorized                         |
| Ares Bridge → Ollama         | Internal (`:11435`)                                 | Local model inference for reasoning and planning                     |
| Ares → Blitz Core            | REST (`:8088`)                                      | Only approved assessment plans are submitted                         |
| Blitz Core → Target Devices  | Multi-protocol (ARP, mDNS, SSDP, ONVIF, TCP, etc.)  | Discovery, fingerprinting, and authorized test execution             |
| Blitz Core → Persistent State | Internal                                           | Devices, jobs, findings, incidents, and full audit trail             |
| Blitz Core → Operator        | WebSocket                                           | Live events, progress, narratives, and results                       |

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
├── capabilities/                 # 154 attack modules across 28 categories
│   ├── firmware/                 # 28 modules: extraction, analysis, emulation, exploitation
│   ├── ble/                      # 12 modules: BLE 4.x/5.x scanning and manipulation
│   ├── zigbee/                   # 8 modules: 802.15.4 and Zigbee attacks
│   ├── wifi/                     # 8 modules: 802.11 deauth, handshake, PMKID, WPA3
│   ├── hardware/                 # 15 modules: UART, SPI, JTAG, SWD, I2C, CAN, glitching
│   ├── cloud/                    # 5 modules: AWS IoT Core, Azure IoT Hub
│   ├── alexa/                    # 7 modules: Alexa cloud and skill exploitation
│   ├── google_home/              # 5 modules: Google Home and Gemini attacks
│   ├── audio/                    # 2 modules: ultrasonic and laser injection
│   ├── mobile/                   # 3 modules: companion app analysis
│   ├── smart_home/               # 4 modules: SmartThings, HomeKit, Tuya, Xiaomi
│   ├── ota/                      # 2 modules: firmware downgrade, signature strip
│   ├── medical/                  # 1 module: DICOM C-FIND enumeration
│   ├── botnet/                   # 1 module: Telnet/Mirai credential bruteforce
│   ├── zwave/                    # 1 module: Z-Wave S0 downgrade
│   ├── lorawan/                  # 1 module: LoRaWAN join replay
│   ├── matter/                   # 1 module: Matter DoS
│   ├── thread/                   # 1 module: Thread border router attack
│   └── [network protocols]/      # 48 modules: HTTP, RTSP, ONVIF, MQTT, CoAP, SNMP, SSH, Telnet, UPnP, post-exploit
│
├── training/                     # Full training pipeline (SFT + GRPO + RFT + Curriculum)
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

---

<a name="protocol-specific-attack-coverage"></a>
## Attack Surface — 154 Modules Across 28 Categories

Blitz covers **every layer** where IoT devices have been shown to be exploitable in the wild.

### 🌐 Network Protocols (48 modules)

| Protocol            | Modules | What It Tests                                              | Real-Time Validation                                                                                          |
| :------------------ | :-----: | :--------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------ |
| **HTTP / HTTPS**    |    6    | Web login, admin pages, access control, input flaws        | Finds web services and paths, sends controlled requests, tests authentication, verifies access restrictions.  |
| **RTSP**            |    5    | Video-stream exposure and authentication                   | Connects to RTSP, discovers streams, checks authentication, verifies restricted stream accessibility.         |
| **ONVIF**           |    6    | Camera management and authorization                        | Discovers ONVIF services, identifies capabilities, verifies auth and management permissions.                  |
| **MQTT**            |    6    | Broker security, topic access, pub/sub permissions         | Connects to broker, checks authentication, discovers permitted topics, validates read/write ACLs.             |
| **CoAP**            |    4    | Resource exposure and access control                       | Discovers CoAP resources, sends controlled requests, verifies protected resource accessibility.               |
| **SNMP**            |    4    | Management access and information exposure                 | Identifies SNMP, tests community strings, checks accessible management info.                                  |
| **SSH**             |    6    | Remote administration and authentication                   | Identifies SSH, checks configuration and auth, validates authorized remote access.                            |
| **Telnet**          |    2    | Insecure remote administration                             | Detects Telnet, evaluates auth, confirms plaintext admin exposure.                                            |
| **UPnP / SSDP**     |    4    | Device discovery and exposed control services              | Discovers devices, maps services, checks for unnecessarily exposed control interfaces.                        |
| **Post-Exploit**    |    7    | Credential replay, persistence, lateral movement           | Chains compromised access into broader environment control.                                                   |

### 🔬 Firmware Analysis (28 modules)

Full lifecycle: extract → analyze → emulate → exploit.

- **Extraction:** binwalk, unblob (30+ formats), SquashFS / CramFS / UBIFS / JFFS2, mount, filesystem carving
- **Analysis:** entropy analysis, secret scanning, credential extraction, SBOM generation, CVE matching, unsafe function detection
- **Emulation:** FirmAE, Firmadyne, config extraction, emulated network scanning, web fuzzing, service fuzzing
- **Runtime:** GDB attach, Frida hooking, strace tracing
- **Exploitation:** ROP gadget discovery, shellcode generation, PoC generation

### 📡 Wireless & RF (44 modules)

| Subcategory         | Modules | Coverage                                                                                                                        |
| :------------------ | :-----: | :------------------------------------------------------------------------------------------------------------------------------ |
| **BLE**             |   12    | Scan, GATT enumeration, characteristic read/write, pairing downgrade, sniffing, replay, cracking, jamming, spoofing, notifications |
| **Zigbee**          |    8    | Network scan, sniffing, key extraction, frame replay, Touchlink abuse, ZCL injection, factory reset                             |
| **Wi-Fi 802.11**    |    8    | Deauth, handshake capture, PMKID, WPS brute, PMKID+bruteforce, KTO deauth, WPA3 downgrade, transition-mode twin                  |
| **Additional RF**   |    4    | Z-Wave S0 downgrade, LoRaWAN join replay, Matter DoS, Thread border router attack                                                |

### 🔌 Hardware Interfaces (15 modules)

| Interface       | Coverage                                                           |
| :-------------- | :----------------------------------------------------------------- |
| **UART**        | Baud detection, boot log capture, interactive console              |
| **SPI**         | Flash dump, integrity verification                                 |
| **JTAG**        | Chain scan, memory dump                                            |
| **SWD**         | ARM Cortex memory dump                                             |
| **I2C**         | Bus scan, EEPROM dump                                              |
| **CAN**         | Bus sniffing, frame injection                                      |
| **Glitching**   | ChipWhisperer voltage/clock glitching, parameter sweep             |
| **Probe**       | Automated hardware detection                                       |

### ☁️ Cloud IoT Platforms (5 modules)

- **AWS IoT Core** — fleet enumeration, shadow injection for remote code execution, MQTT wildcard subscription for fleet-wide data harvest
- **Azure IoT Hub** — device registry enumeration, twin read/write, CVE-2026-13768 RCE chain

### 🎤 Voice Assistant Ecosystem (17 modules)

- **Amazon Alexa** — OAuth CSRF, rogue account linking, break-tag chain, skill squatting, SkillVet bypass, DMC-Xplorer device management abuse, Alexa vs. Alexa self-command
- **Google Home** — rogue account link, DNS rebinding, prompt injection, promptware v2
- **Audio injection** — ultrasonic (NUIT 1/2), laser (LightCommands, LCMA)
- **Network analysis** — voice traffic fingerprinting

### 📱 Mobile Companion Apps (3 modules)

- APK/IPA static analysis for hardcoded cloud credentials
- Embedded firmware extraction from apps
- Backend API IDOR and auth bypass fuzzing

### 🏠 Additional Categories (24 modules)

| Category                    | Modules | Coverage                                                                       |
| :-------------------------- | :-----: | :----------------------------------------------------------------------------- |
| **Smart Home Platforms**    |    4    | SmartThings (CVE-2025-2233), HomeKit Pair-Setup, Tuya CloudCutter, Xiaomi tokens |
| **OTA / Provisioning**      |    2    | Firmware downgrade, signature stripping (CVE-2026-1122)                        |
| **Medical IoT**             |    1    | DICOM C-FIND patient enumeration                                               |
| **Botnet / Telnet**         |    1    | Mirai-style default credential bruteforce                                      |

**Total: 154 modules. Every major IoT attack surface documented in security research is covered.**

---

## ATT&CK Coverage Map

<img src="https://github.com/giridharan-veda/threatforge-physical-iot/blob/main/ares-attack-matrix.svg" width="100%" alt="Blitz — Autonomous IoT Red Teaming Platform powered by Ares">

*The techniques above map Blitz's autonomous testing activity — discovery, credential access, protocol abuse, impact validation — against the stages a real IoT/OT intrusion would follow, so results can be read in attacker terms, not just scan output.*

---

## 🎯 Capabilities

### The Ultimate Autonomous IoT Red Teaming Arsenal

Blitz transforms fragmented IoT assessment work into a single high-speed, automated offensive workbench. Whether you're auditing physical facilities, competing in CTF arenas, or stress-testing hardware in a staging lab, Blitz and the Ares AI engine deliver **ten integrated operational capabilities**.

### Operational Modes Matrix

| Mode / Feature              | Primary Target Surface                          | Autonomy Level              | Primary Output                      |
| :-------------------------- | :---------------------------------------------- | :-------------------------- | :---------------------------------- |
| **Autonomous AutoPwn**      | Multi-protocol IoT subnets                      | Fully autonomous            | Chained compromise proofs           |
| **Protocol Fuzzing**        | MQTT, CoAP, RTSP, ONVIF                         | Configurable concurrency    | Crash logs & input boundary flaws   |
| **Firmware Carving**        | Raw embedded binary images                      | Automated batch             | Extracted secrets & CGI vulns       |
| **Ghost Recon**             | Layer 2 broadcast domains                       | Passive to high-throughput  | Device topology & identity maps     |
| **BYO-Brain Engine**        | Planning & reasoning layer                      | AI-directed                 | Execution plans & tool selection    |
| **CTF Arena Mode**          | Staging labs & QEMU images                      | Real-time interactive       | Live streaming WebSocket feed       |
| **Re-Validation Loop**      | Post-remediation targets                        | Targeted automated replay   | Fix attestation & regression reports |
| **Physical & Wireless**     | BLE, Zigbee, Wi-Fi, UART, SPI, JTAG, I2C, CAN   | Hardware-dependent          | Full physical attack surface        |
| **Cloud & Companion App**   | AWS IoT, Azure IoT, mobile apps                 | Credential-driven           | Fleet-wide compromise chains        |
| **Voice Assistant & AI**    | Alexa, Google Home, LLM pipelines               | Signal and prompt injection | Cross-ecosystem lateral movement    |

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
- **Cloud Chain Discovery:** When cloud credentials are found in firmware, they automatically feed the AWS IoT Core and Azure IoT Hub modules — turning a firmware finding into a fleet-wide compromise.

### 4. Ghost Recon (Zero-Noise Stealth to High-Velocity Sweeps)

Discovery intensity is configurable from silent listening to high-throughput active scanning:

- **Passive Listener Mode:** Passively maps the local environment by monitoring ambient mDNS, UPnP, SSDP, and ARP broadcasts without transmitting packets.
- **High-Speed Network Sweep:** Executes parallel multi-protocol host discovery with Layer 2 adjacency, identifying device vendor, model, firmware revision, and exposed surfaces.

### 5. BYO-Brain: Hot-Swappable AI Model Engine

Ares runs on an open, modular capability bridge rather than a locked-in AI provider:

- **Air-Gapped Local Inference:** Ships configured with the fine-tuned **`ares`** model, running offline via local Ollama (`:11435`) for zero external telemetry and zero per-token API costs.
- **Model Hot-Swapping:** Route requests through the Ares Bridge (`:8089`) to alternate local or remote model endpoints (such as DeepSeek-Coder, Llama, or Mistral) to evaluate different reasoning models against identical targets.
- **Retrain on Your Data:** The full SFT + GRPO + RFT + curriculum pipeline is included. Retrain on your own engagements with an 8 GB GPU.

### 6. Hardware Lab & CTF Arena Mode

Built for repeatable experimentation in staging and competitive environments:

- **Live WebSocket Telemetry:** Streams raw operational decision graphs and execution telemetry directly to terminal consoles or custom dashboards over WebSocket port `:8088`.
- **Target Emulation Compatibility:** Deploy against virtualized or physical targets (Docker, QEMU, or hardware test benches) to run repeatable attack simulations against simulated camera arrays, smart meters, and industrial IoT controllers.

### 7. Instant Proof-of-Impact & Remediation Diffs

Converts automated test data into verifiable technical artifacts:

- **Attempted vs. Proven Telemetry:** Strictly separates an initial service probe from a cryptographically or functionally confirmed vulnerability — no speculative findings.
- **Closed-Loop Re-Validation:** After remediation, Stage 12 (**Re-validate**) automatically replays the verified exploit chain to confirm whether the vulnerability was actually mitigated — without re-running a full scan.

### 8. Physical & Wireless Attack Surface

Covers the layers that network-only tools can't reach:

- **Wireless:** BLE GATT enumeration and characteristic exploitation, Zigbee network key extraction, Wi-Fi handshake capture and PMKID attacks, Z-Wave S0 downgrade.
- **Hardware:** Full UART / SPI / JTAG / SWD / I2C / CAN bus analysis and injection; voltage and clock glitching via ChipWhisperer.

### 9. Cloud IoT & Companion App Testing

Attacks the cloud backend that manages the fleet — the layer where one compromised credential means thousands of compromised devices:

- **AWS IoT Core / Azure IoT Hub:** Fleet enumeration, device shadow injection for RCE, wildcard MQTT subscription for fleet-wide telemetry harvest.
- **Companion Mobile Apps:** APK/IPA static analysis for hardcoded cloud credentials, embedded firmware extraction, backend API IDOR and auth bypass.

### 10. Voice Assistant & AI Attack Surface

The newest and fastest-moving attack class — how attackers reach IoT devices through the AI layer that controls them:

- **Alexa / Google Home Cloud:** OAuth CSRF, rogue account linking, DNS rebinding, prompt injection.
- **Signal Injection:** Ultrasonic (NUIT 1/2) and laser (LightCommands, LCMA) command injection.
- **Promptware:** Indirect prompt injection against LLM-integrated IoT devices.

---

<a name="comparison"></a>
## ⚔️ Blitz vs. Established Open-Source IoT Security Tools

| Capability                                    | 🛠️ RouterSploit                  | 🏠 HomePwn                        | 💥 EXPLIoT                        | 🤖 IoTHackBot                     | ⚡ Blitz                                  |
| :-------------------------------------------- | :-------------------------------- | :-------------------------------- | :-------------------------------- | :-------------------------------- | :---------------------------------------- |
| **Category**                                  | Embedded/router exploitation      | Local-proximity IoT pentest       | IoT security testing & exploitation | AI-assisted IoT recon & hardware | Autonomous IoT/OT red-teaming platform    |
| **Runs without a human at the keyboard**      | ❌ Manual, one session at a time  | ❌ Manual, one session at a time  | ❌ Manual, one session at a time  | ❌ Human/AI, command-by-command   | ✅ **Fully autonomous, continuous**       |
| **Finds new devices on its own**              | ❌ You point it at a known target | ❌ You run discovery yourself     | ❌ You select a target manually   | ❌ You run `wsdiscovery` per session | ✅ **Continuous, automatic discovery**  |
| **Decides what's worth testing**              | ❌ You choose the exploit module  | ❌ You choose the module          | ❌ You choose the plugin          | ⚠️ AI-assisted, but you drive it  | ✅ **Ares plans the assessment itself**   |
| **Stops unsafe actions before they run**      | ❌ No gating                      | ❌ No gating                      | ❌ No gating                      | ⚠️ Disclaimer only, not enforced  | ✅ **Multi-condition auth gate**          |
| **Proves impact instead of guessing**         | ❌ Pass/fail, no evidence         | ❌ Manual write-up                | ❌ Manual write-up                | ❌ Manual output review           | ✅ **"Attempted vs. Proven"**             |
| **Confirms a fix actually worked**            | ❌ Fresh manual run               | ❌ Fresh manual run               | ❌ Fresh manual run               | ❌ Fresh manual run               | ✅ **Automatic re-validation**            |
| **Protocol coverage**                         | HTTP, Telnet, SNMP                | BLE, WiFi, SSDP, mDNS, NFC        | Broad, plugin-extensible          | ONVIF, network traffic, firmware  | **154 modules across 28 categories**      |
| **Firmware analysis**                         | ❌                                | ❌                                | ⚠️                                | ✅                                | ✅ **Full extraction-to-exploitation**    |
| **Wireless (BLE / Zigbee / Wi-Fi)**           | ❌                                | ⚠️                                | ⚠️                                | ❌                                | ✅ **44 wireless modules**                |
| **Cloud IoT (AWS / Azure)**                   | ❌                                | ❌                                | ❌                                | ❌                                | ✅ **Fleet-level exploitation**           |
| **Voice assistant attacks**                   | ❌                                | ❌                                | ❌                                | ❌                                | ✅ **Alexa / Google Home / promptware**   |
| **Hardware (UART / SPI / JTAG / I2C / CAN)**  | ❌                                | ❌                                | ✅                                | ✅                                | ✅ **15 hardware modules + glitching**    |
| **Local LLM (no cloud, no per-token costs)**  | ❌                                | ❌                                | ❌                                | ❌                                | ✅ **Air-gapped `ares` via Ollama**       |

*Comparison based on each project's public documentation and repositories as of the date of this README; open-source tools evolve, so verify current capabilities against their latest releases.*

---

<a name="pricing"></a>
## 💰 The Real Cost of Waiting for Your Next Pentest

|                                                   | 🧑‍💻 Standard IT Pentest                      | 🔌 IoT/OT-Specific Pentest                                | 🎯 Red-Team-Level IoT Engagement                  | ⚡ Blitz                                    |
| :------------------------------------------------ | :--------------------------------------------- | :-------------------------------------------------------- | :------------------------------------------------ | :------------------------------------------ |
| **Cost**                                          | $5,000 – $100,000+ (industry estimate)          | **$10,000 – $40,000** per engagement                      | **$30,000 – $150,000+**                           | **$299 — once, early adopter**              |
| **Billing model**                                 | Per engagement                                  | Per engagement, higher due to firmware/hardware work      | $120–$350+/hr, senior tester day rates            | Flat, one-time                              |
| **What you actually get**                         | One report, one point in time                   | One report — firmware, protocol testing, one snapshot     | Deep manual exploitation, still one snapshot      | **Continuous testing, every device**        |
| **Valid for how long?**                           | Stale the moment scope changes                  | Stale the moment a new device joins                       | Stale the day it's delivered                      | **Never goes stale — always running**       |
| **Re-testing after a fix**                        | Rarely included, extra cost                     | Rarely included, extra cost                               | Rarely included, extra cost                       | ✅ **Automatic, included, always**          |
| **Frequency you can realistically afford**        | Once a year, if budget allows                   | Once a year, if at all                                    | Once, maybe never repeated                        | **Every day**                               |
| **Cost vs. Blitz**                                | ~98% more expensive                             | **~97–99% more expensive**                                | **~99–99.8% more expensive**                      | **The baseline**                            |

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

| Tier                       | Price              | Availability                    | License Scope                                                  |
| :------------------------- | :----------------- | :------------------------------ | :------------------------------------------------------------- |
| **Early Adopter Cohort**   | **$299** ~~$499~~  | **Active now** (code `EARLYBIRD`) | First 25 licenses only • Perpetual commercial rights            |
| **Standard Commercial**    | **$499**           | Standard list price             | Perpetual commercial rights • Unlimited targets & audits        |
| **Enterprise**             | *Contact us*       | Custom                          | + SLA, + custom modules, + dedicated support                    |

[![Purchase Blitz Commercial License](https://img.shields.io/badge/Purchase%20Blitz-%24299%20Early%20Adopter-brightgreen?style=for-the-badge&logo=github)](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)

---

### What Is Included in the License

- **Complete Autonomous Stack:** Blitz Core execution engine (`:8088`), Ares Agent reasoning layer (`:9010`), and Ares Bridge capability gateway (`:8089`).
- **Local, Air-Gapped AI Model:** Dedicated **`ares`** weights (1.7B Qwen3 variant) fine-tuned on the full SFT + GRPO + RFT + curriculum pipeline. Runs offline on local hardware via Ollama (`:11435`) with zero telemetry leaving your network and zero recurring API token costs.
- **All 154 Attack Modules Across 28 Categories:** Full coverage of network protocols (HTTP, RTSP, ONVIF, MQTT, CoAP, SNMP, SSH, Telnet, UPnP), firmware analysis, wireless (BLE, Zigbee, Wi-Fi, Z-Wave, LoRaWAN, Matter, Thread), hardware interfaces (UART, SPI, JTAG, SWD, I2C, CAN, glitching), cloud IoT (AWS, Azure), voice assistant ecosystems (Alexa, Google Home), mobile companion apps, smart-home platforms, and more.
- **12-Stage Closed-Loop Lifecycle:** Complete execution pipeline with multi-condition authorization gating (Authorized? In scope? Capability allowed?), a strict distinction between "attempted" and "proven" results, and persistent SQLite evidence storage.
- **Reproducible Training Pipeline:** Full source code for SFT, GRPO, RFT, and curriculum training. Retrain on your own engagement data with a single 8 GB GPU.
- **Automated Deployment:** Ready-to-run `blitz-setup.sh` installer script and production `docker-compose.yml` configurations.
- **Perpetual Commercial Rights:** Unlimited internal asset coverage and external client penetration tests, with zero per-target, per-scan, or per-seat metering fees.
- **Continuous Updates:** Lifetime access to new protocol modules, CVE detection profiles, and engine enhancements.

---

<a name="faq"></a>
## ❓ FAQ

**Is Blitz safe to run against production devices?**
Yes — every action Ares proposes passes through the Ares Bridge's multi-condition authorization gate (authorized? in scope? capability allowed?) before it ever reaches a real device. Destructive modules (fuzzing, firmware modification, credential writes) are opt-in per target. Fuzzing is off by default. That gate is what makes continuous, unattended testing viable on live infrastructure.

**Am I authorized to test devices I don't own?**
Only with explicit authorization from the asset owner — the same rule that governs any red-team or penetration-testing engagement. Blitz's scoping and authorization gate exist specifically to enforce that boundary; it is your responsibility to have written authorization in place for every target before you scan it.

**Does any data leave my network?**
No. The `ares` model that powers Ares runs locally via Ollama, so device context and reasoning stay on your infrastructure — zero telemetry, zero per-token API costs. When you retrain the model, your training data also stays on your hardware.

**Do I need special hardware to use it?**
For network, firmware, cloud, and mobile modules — no. For wireless modules (Wi-Fi, BLE, Zigbee) — any $10 USB adapter. For hardware modules (UART, SPI, JTAG) — any $20 CH341A/UART programmer. Total to cover every attack surface: roughly $50.

**Can I retrain the model on my own engagements?**
Yes. The full pipeline — SFT, GRPO, RFT, and curriculum learning — is included with the license. Retrain on your own session data using the same scripts, on an 8 GB GPU in under 3 hours.

**What if a new IoT device class appears?**
Add a device profile to `knowledge/device_profiles.yaml`. The framework picks it up on the next run. No model retraining required for basic coverage — retrain only if you want the model to reason about new routing decisions natively.

**How does the model handle new modules I write?**
Add the module's `manifest.toml` and `knowledge.toml`. Retrain with the provided scripts to include the new routing decision in the model. Or run with the base model and rely on the framework's fallback logic — the classifier will still select the correct category, and the framework will route to the nearest matching module.

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

Blitz is built and maintained by **ApexPredator Security & Labs**, the research group behind the Ares AI reasoning engine and the closed-loop assessment methodology this platform runs on. Every module, protocol integration, and the fine-tuned `ares` model shipped with Blitz was built in-house specifically for IoT/OT offensive testing — this isn't a wrapper around existing open-source scanners.

*[ApexPredator — add a sentence or two here on team background, years active, prior research, or any public writeups/CVEs credited to the team. A named point of contact or a link to the org's research blog goes a long way toward buyer trust for a product in this category.]*

---

## 💬 Support & Updates

- **Included with every license:** lifetime access to new protocol modules, CVE detection profiles, and engine enhancements (see [What Is Included in the License](#what-is-included-in-the-license)).
- **Questions before you buy, or issues after:** *[ApexPredator — add a support email, docs site, or Discord/community link here.]*

---

## ⚙️ Installation & System Requirements

### 🖥️ System Requirements

| Requirement         | Minimum                                   | Recommended              | Why It Matters                                                                                                                                                                                              |
| :------------------ | :---------------------------------------- | :----------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **OS**              | Linux / macOS / Windows (WSL2)            | Ubuntu 22.04 LTS         | Blitz's core services and Docker networking are tested and most stable on Linux; WSL2 gives Windows users the same kernel-level container support. Ubuntu 22.04 LTS is the reference environment.           |
| **CPU**             | 4 cores                                   | 8 cores                  | Ares' reasoning layer, Blitz Core's execution engine, and concurrent protocol scans run as parallel workloads — more cores mean faster cycles and the ability to test multiple devices simultaneously.       |
| **RAM**             | 8 GB                                      | 16 GB                    | Local AI inference (via Ollama), persistent state storage, and live WebSocket event streaming all hold data in memory. 16 GB gives headroom for larger inventories and longer-running assessments.            |
| **Disk**            | 20 GB free                                | 40 GB free (SSD)         | Persistent state (devices, jobs, findings, audit history) and locally-run AI models take real disk space — SSD is recommended because model loading and database I/O are latency-sensitive.                  |
| **Docker Engine**   | 24.x                                      | Latest stable            | Blitz's components run as containerized services — Docker Engine is the runtime that isolates and orchestrates them.                                                                                        |
| **Docker Compose**  | v2                                        | v2                       | Used to define and launch the full multi-container stack (Console, Agent, Bridge, Core, Ollama) as a single coordinated deployment.                                                                          |
| **Python**          | 3.11+                                     | 3.11+                    | Required for Blitz Core and supporting tooling — 3.11+ ensures compatibility with current dependency versions and performance improvements over earlier releases.                                            |
| **GPU (optional)**  | 6 GB VRAM                                 | 8 GB VRAM                | Not required for running Blitz. Required only if you want to retrain the `ares` model on your own engagement data.                                                                                          |

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
  <img src="https://github.com/giridharan-veda/threatforge-physical-iot/blob/main/apexpredator-logo-bottom.png" alt="Description" width="600">
</div>

<div align="center">

**Blitz — Autonomous IoT Red Teaming & Continuous Assessment.**

*Your devices are already connected. Already exposed. Already being watched — by someone.*

*$299 decides who finds the weakness first.*

[![Purchase Blitz Commercial License](https://img.shields.io/badge/Purchase%20Blitz-%24299%20Early%20Adopter-brightgreen?style=for-the-badge&logo=github)](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)

</div>
