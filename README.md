<div align="center">

<img src="https://raw.githubusercontent.com/giridharan-veda/threatforge-physical-iot/main/blitz-banner.svg" width="100%" alt="Blitz — Automated IoT Red Teaming Platform powered by Ares">

**an Automated IoT Red Teaming & Continuous Assessment Platform**

Stop guessing whether your IoT and OT devices are actually secure.  
Blitz continuously discovers, plans, tests, proves, and re-validates — with AI-driven intelligence and strict safety controls.

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

### The Risk - IoT and OT devices now sit inside the same networks that security teams already defend — cameras, sensors, gateways, industrial controllers, smart-home hubs, medical devices, and embedded systems. These devices are rarely tested properly. Most organizations face the same problems:

- Traditional red team tools were built for Windows and Linux endpoints, not for fragile IoT protocols and constrained devices
- Manual testing is slow, expensive, and does not scale
- Uncontrolled or poorly gated tools can disrupt production systems
- Generic AI tools lack IoT context and frequently produce unsafe or irrelevant actions
- There is usually no reliable way to prove that a test actually succeeded or that a fix actually worked

The result is a dangerous gap: organizations either avoid testing these assets entirely, or they run shallow scans that provide little real security value.

### The Solution — **Blitz** is a purpose-built automated red teaming and continuous assessment platform designed specifically for IoT and OT environments.

For **$299** you receive a complete operational system that:

- Continuously discovers IoT and OT assets across multiple protocols
- Builds real, per-device security context
- Uses **Ares**, an IoT-specific AI engine, to generate intelligent and ranked assessment plans
- Enforces a strict multi-condition authorization gate before any test is allowed to run
- Executes only approved actions with full evidence collection
- Clearly distinguishes between “attempted” and “proven” results
- Generates reviewable, evidence-backed findings
- Supports remediation and automatically re-validates that fixes actually held

## What is Blitz

**Blitz** is a commercial automated red teaming and continuous assessment platform built specifically for IoT and OT environments.

Most traditional red team tools were designed for Windows and Linux endpoints. They struggle with the realities of IoT — diverse protocols, constrained devices, fragile firmware, and the need for strict safety controls. Blitz was created to solve this gap.

At its core, Blitz runs a controlled **12-stage closed-loop assessment lifecycle**. It begins by discovering devices and building real security context for each one. It then uses AI to generate intelligent assessment plans, enforces strict authorization before any test is allowed to run, executes only approved actions, verifies the results, stores evidence, generates findings, and can re-validate after remediation.

Blitz is not a vulnerability scanner.  
It is not a generic AI agent that freely interacts with devices.  
It is an operational system that separates **intelligent planning** from **safe, authorized execution**.

This design allows security teams to perform repeatable, auditable, and authorized adversary simulation against IoT and OT assets — without the operational risk that usually comes with testing these environments.

### How Blitz Is Different

Most existing tools fall into one of three categories — and all of them fall short for serious IoT red teaming:

| Existing Approach | Limitation | How Blitz Is Different |
|-------------------|----------|------------------------|
| Traditional red team frameworks (Cobalt Strike, Metasploit, etc.) | Built for enterprise endpoints, not IoT protocols or safety constraints | Native multi-protocol discovery and IoT-aware execution |
| Vulnerability scanners | Find issues but do not safely execute or prove impact | Full closed-loop execution + “attempted vs proven” verification |
| Generic AI agents | Lack domain context and safety controls | Ares is purpose-built for IoT reasoning and sits behind a capability gateway |
| Manual testing | Expensive, non-repeatable, hard to audit | Fully automated 12-stage lifecycle with persistent state and live event streaming |

Blitz is the only platform that combines **IoT-specific AI planning**, **evidence-backed execution**, and **closed-loop re-validation** in a single commercial product.

### Core Components of Blitz

Blitz is composed of seven tightly integrated components:

### Technology Stack

| Component | Role |
|-----------|------|
| **Operator Console** | Human control plane for launching assessments and monitoring live results |
| **Ares Agent** | AI orchestration layer that plans and sequences assessments |
| **Ares Bridge** | Capability gateway that enforces what Ares is allowed to request |
| **Ollama** | Local model runtime for private, on-premises AI inference |
| **Blitz Core** | Assessment & execution engine (REST + WebSocket) that runs the full closed-loop lifecycle |
| **Persistent State** | Stores devices, jobs, findings, incidents, and complete audit history |
| **Live Event Stream** | Real-time WebSocket feed of progress, results, and narratives back to the operator through the gui |

## What is Ares

**Ares** is the autonomous intelligence layer of the Blitz platform. It is the component that turns a collection of IoT security tools into a system capable of independent assessment.

<img src="https://raw.githubusercontent.com/giridharan-veda/threatforge-physical-iot/main/aresai.png" width="100%" alt="Blitz — Automated IoT Red Teaming Platform powered by Ares">

Most security tools require a human to decide what to scan, which credentials to try, which protocols to probe, and what to do next. Ares removes that dependency. It observes the current state of a target, reasons about what the device appears to be, and decides the next appropriate action from a controlled set of capabilities.

Ares does not perform network attacks itself. That responsibility belongs to Blitz. Instead, Ares acts as a decision engine. It maintains a structured knowledge base of device profiles, protocol behaviours, known attack surfaces, and tool mappings. When new information is discovered — open ports, banners, services, or vendor signatures — Ares classifies the device and builds a ranked plan of what should be tested next.

The intelligence inside Ares is deliberately narrow and controlled. A fine-tuned language model is used only at decision points to choose the next tool. Surrounding that model is a deterministic loop that enforces workflow order, applies safety constraints, records every decision, and prevents repetition or unsafe behaviour. This design keeps the system autonomous without making it unpredictable.

Because Ares understands IoT-specific context — cameras, brokers, routers, controllers, and their typical weaknesses — it can drive assessments that are more relevant and more efficient than generic scanning. The result is a system that can progress through discovery, fingerprinting, testing, and validation with minimal human intervention while remaining auditable and bounded.

## What is the Ares Bridge

The **Ares Bridge** is the controlled interface that sits between the intelligence layer (Ares) and the execution layer (Blitz). It is the component that makes the system modular, extensible, and safe.

Ares never talks directly to Blitz. Every request from the AI must pass through the Bridge. This design creates a clear boundary: Ares can decide what should happen, but the Bridge decides whether that request is allowed to proceed and how it is translated into an actual action.

During development, the Bridge was connected and tested with external AI systems such as **RedAmon** paired with **StrikeGPT**. This demonstrated that the same interface can accept decisions from different AI backends without changing the underlying execution engine. As a result, the Bridge makes it straightforward to connect Blitz to other AI APIs in the future — whether local models, cloud models, or specialised agents — while keeping the rest of the platform stable.

Beyond AI integration, the Bridge also provides a clean path for connecting external systems such as SIEM platforms. Because all capability requests and results flow through a single, well-defined interface, events and findings can be forwarded to monitoring tools without tight coupling to the core assessment engine.

In short, the Bridge exists for three reasons:

- It enforces a safety and capability boundary between planning and execution.
- It allows different AI systems to drive Blitz through a consistent interface.
- It enables integration with external tools such as SIEMs without modifying the core platform.

Without the Bridge, Ares and Blitz would be tightly coupled. With it, the platform remains modular, controllable, and ready for extension.

## What type of Ollama LLM is in Blitz

**Ollama** is the local model runtime that powers the intelligence inside Ares. It runs a fine-tuned language model specialised for IoT security decisions, keeping all inference private and on-premises.

The model used by Blitz is a 1.7-billion-parameter Qwen3 variant that was fine-tuned specifically for IoT assessment planning. It does not attempt to plan entire attack chains or interact with the network. Its only role is to answer one focused question at each step: given the current state of a device, which tool should be used next.

### How the Model Was Trained for IoT

The model was fine-tuned using QLoRA on a carefully constructed dataset of 683 IoT-specific examples. The training data combined real session exports with synthetic scenarios built around common IoT device families — cameras, routers, MQTT brokers, controllers, and similar systems.

Each training example presented the model with a compact device state (open ports, services, and basic context) and required it to select the most appropriate next tool from a fixed allowlist. The training process also included rationale distillation, so the model learned not only which tool to choose but why that choice made sense for a given device type.

Because the task was narrowly scoped, the model converged quickly. Final evaluation loss reached 0.050, indicating strong consistency on held-out IoT scenarios. Once trained, the model was quantised and registered inside Ollama as `qwen3-iot:1.7b`, where it runs entirely on local GPU resources.

This design keeps the AI contribution small, fast, and domain-specific. The model contributes judgment at decision points, while the surrounding deterministic systems in Ares handle sequencing, safety, persistence, and execution.


### Key Features

| Category | Capability |
|----------|------------|
| **Discovery & Context** | Continuous multi-protocol discovery (ARP, mDNS, SSDP, ONVIF, TCP and more) with per-device identity resolution and security context correlation |
| **AI-Driven Planning** | Ares generates ranked, applicability-aware assessment plans based on live device context |
| **Safety Controls** | Multi-condition authorization gate (Authorized? In scope? Capability allowed?) — any “No” blocks execution |
| **Controlled Execution** | Prepare → Execute → Cleanup lifecycle with full audit trail |
| **Evidence & Proof** | Clear distinction between attempted and proven results + persistent evidence storage |
| **Findings & Remediation** | Evidence-backed findings + remediation support + automatic re-validation of fixes |
| **Operator Experience** | Real-time WebSocket event streaming and live narrative updates |
| **Deployment** | Docker-supported, designed for controlled and auditable environments |
| **Audience** | Red teams, purple teams, IoT/OT security programmes, and detection engineering teams |

## Architecture

<p align="center">
<img src="https://github.com/giridharan-veda/threatforge-physical-iot/blob/main/blitz-architecture.svg" width="100%" alt="Blitz — Automated IoT Red Teaming Platform powered by Ares">  
</p>

Blitz is designed as a **closed-loop automated red teaming system** specifically for IoT and OT environments.  
It separates intelligent planning from safe execution, and every action is authorized, logged, and verifiable.

### How Blitz Operates (High-Level Flow)

1. The **Operator** launches an assessment or continuous monitoring job.
2. The request goes to the **Ares Reasoning & Orchestration Layer**.
3. **Ares** (using the local Ollama model) analyzes the environment and generates an intelligent assessment plan.
4. The plan is passed through the **Ares Bridge** (capability gateway), which strictly controls what the AI is allowed to request.
5. Only approved plans are sent to **Blitz Core** (`:8088`).
6. Blitz Core executes the full **12-stage closed-loop assessment lifecycle**.
7. Results, evidence, and findings are stored in **Persistent State**.
8. Live progress and results are streamed back to the Operator in real time via **WebSocket**.

This separation of concerns (AI planning → gated capabilities → controlled execution → evidence → re-validation) is the core design principle of Blitz.

---

### Service Topology

| Layer | Components | Responsibility |
|-------|------------|----------------|
| **Operator** | Human operator / console | Starts assessments, monitors live results, reviews findings |
| **Ares – Reasoning & Orchestration** | Ares Agent (`:9010`), Ares Bridge (`:8089`), Ollama (`:11435`) | AI-driven planning and strict capability control |
| **Blitz Core** | Assessment & Execution Engine (`:8088` – REST + WebSocket) | Runs the complete 12-stage closed-loop lifecycle |
| **State & Feedback** | Persistent State + Live Event Stream | Stores everything + streams real-time updates |

---

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

### Blitz Core – 12-Stage Closed-Loop Assessment Lifecycle

1.Discover → 2.Resolve Identity → 3.Fingerprint → 4.Correlate Context →
5.Build Plan → 6.Authorization Gate → 7.Execute → 8.Verify Result →
9.Persist Evidence → 10.Generate Finding → 11.Remediate → 12.Re-validate ↺

This closed-loop design is what makes Blitz fundamentally different from traditional scanners or open-ended AI agents.

---

### Ares – Reasoning & Orchestration Layer

Ares is the intelligence layer of Blitz. It is responsible for **thinking**, not for executing.

- **Ares Agent** (`:9010`)  
  Orchestrates high-level assessment planning and sequencing.

- **Ares Bridge** (`:8089`)  
  Acts as a capability gateway. It strictly controls what the AI is allowed to request. This is a critical safety boundary.

- **Ollama** (`:11435`)  
  Runs the local language model for private, on-premises AI inference. No data leaves the environment.

**Important design rule:**  
Ares never directly touches target devices. It only plans and requests. All actual execution is performed by Blitz Core after authorization.

Every decision, every test, and every result is recorded. The operator always has full visibility.

---

### System Requirements

| Requirement | Minimum | Recommended |
|-------------|---------|-------------|
| OS | Linux / macOS / Windows (WSL2) | Ubuntu 22.04 LTS |
| CPU | 4 cores | 8 cores |
| RAM | 8 GB | 16 GB |
| Disk | 20 GB free | 40 GB free (SSD) |
| Docker Engine | 24.x | Latest stable |
| Docker Compose | v2 | v2 |
| Python | 3.11+ | 3.11+ |

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
---


## Attack & Validation Capabilities

Blitz is an IoT security assessment engine built around **device-aware testing**, rather than a collection of generic scanners. It first determines what is actually present in the target environment—devices, ports, services, protocols, authentication mechanisms, and exposed interfaces—and then selects assessment modules relevant to those specific surfaces.

The result is a structured assessment pipeline:

**Discover → Identify → Enumerate → Assess → Validate → Correlate → Report → Re-validate**

Every operation is executed through **Blitz Core** and is subject to the **Authorization Gate**. The autonomous planner cannot directly execute arbitrary actions. **Ares** analyses the discovered environment and proposes the most relevant assessment sequence, while the execution layer determines which actions are permitted before they are sent to the target.

### What Makes Blitz Different

Traditional IoT scanners often stop at statements such as:

> "Port 554 is open."

or:

> "This device appears to expose HTTP."

Blitz goes further by determining:

> **"What does that service expose, how does it behave, what security controls protect it, and can the observed weakness be safely demonstrated?"**

For example, discovering an RTSP service is only the beginning. Blitz can identify the RTSP implementation, inspect its authentication behaviour, enumerate permitted stream endpoints where authorized, examine transport configuration, and determine whether an observed exposure can be validated without disrupting the camera or its video service.

The same protocol-aware approach is applied across **HTTP/HTTPS, RTSP, ONVIF, MQTT, CoAP, UPnP/SSDP, SSH, Telnet, SNMP, TLS**, and other IoT-facing services.

> **Blitz does not simply identify what is exposed—it determines how the service behaves, where its security boundaries are, and whether a weakness can be safely validated with evidence.**




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


### Capability Matrix

| # | Module | Protocol / Surface | What It Does |
|---:|---|---|---|
| 01 | **ARP Discovery** | Network | Finds live devices and maps IP addresses to MAC addresses. |
| 02 | **TCP Discovery** | TCP | Finds reachable TCP ports and exposed services. |
| 03 | **Device Fingerprinting** | Network | Identifies device vendor, model and device type from observed behaviour. |
| 04 | **Service Fingerprinting** | TCP / UDP | Determines which protocol or service is running on a discovered port. |
| 05 | **HTTP Discovery** | HTTP / HTTPS | Detects exposed web interfaces on IoT devices. |
| 06 | **HTTP Path Discovery** | HTTP | Finds login, admin, status and configuration endpoints. |
| 07 | **HTTP Authentication Test** | HTTP | Checks whether web interfaces require authentication and tests authorized credentials. |
| 08 | **HTTP Access-Control Test** | HTTP | Verifies that protected web resources cannot be accessed without proper authorization. |
| 09 | **HTTP Input Validation** | HTTP | Checks exposed parameters for unsafe input handling. |
| 10 | **HTTP Configuration Check** | HTTP | Detects insecure web-server and management-interface configuration. |
| 11 | **HTTP Information Disclosure** | HTTP | Identifies sensitive information revealed through responses, headers or errors. |
| 12 | **RTSP Discovery** | RTSP | Detects RTSP services commonly used by cameras and NVRs. |
| 13 | **RTSP Authentication Test** | RTSP | Checks whether video streams are properly protected by authentication. |
| 14 | **RTSP Stream Enumeration** | RTSP | Identifies available video-stream endpoints. |
| 15 | **RTSP Access-Control Test** | RTSP | Verifies whether restricted streams can be accessed without the required authorization. |
| 16 | **RTSP Capability Enumeration** | RTSP | Identifies supported RTSP methods and service capabilities. |
| 17 | **ONVIF Discovery** | ONVIF | Finds ONVIF-enabled cameras and their management interfaces. |
| 18 | **ONVIF Service Enumeration** | ONVIF | Maps camera management services exposed through ONVIF. |
| 19 | **ONVIF Device Enumeration** | ONVIF | Retrieves available camera identity and capability information. |
| 20 | **ONVIF Authentication Test** | ONVIF | Checks whether ONVIF management functions are properly authenticated. |
| 21 | **ONVIF Authorization Test** | ONVIF | Verifies that authenticated users only receive permitted camera operations. |
| 22 | **ONVIF Profile Enumeration** | ONVIF | Identifies supported camera profiles and related functionality. |
| 23 | **MQTT Broker Discovery** | MQTT | Detects reachable MQTT brokers used by IoT systems. |
| 24 | **MQTT Authentication Test** | MQTT | Checks broker authentication requirements using authorized credentials. |
| 25 | **MQTT Topic Enumeration** | MQTT | Identifies topics visible through the permitted MQTT interface. |
| 26 | **MQTT Subscribe Test** | MQTT | Verifies whether restricted topics can be read by an unauthorized context. |
| 27 | **MQTT Publish Test** | MQTT | Verifies whether clients can write to topics outside their intended permissions. |
| 28 | **MQTT Transport Check** | MQTT / TLS | Checks whether MQTT communication is appropriately protected in transit. |
| 29 | **UPnP / SSDP Discovery** | UPnP / SSDP | Discovers devices and services advertised through UPnP. |
| 30 | **UPnP Service Enumeration** | UPnP | Maps exposed UPnP services and device functions. |
| 31 | **UPnP Exposure Test** | UPnP | Checks for unnecessarily exposed control or management interfaces. |
| 32 | **SNMP Assessment** | SNMP | Evaluates SNMP exposure, access controls and information available through management interfaces. |
| 33 | **SSH Assessment** | SSH | Checks SSH exposure, authentication and remote-management configuration. |
| 34 | **Telnet Assessment** | Telnet | Detects insecure Telnet administration and evaluates its authentication exposure. |
| 35 | **CoAP Enumeration** | CoAP | Discovers CoAP endpoints and resources exposed by constrained IoT devices. |
| 36 | **CoAP Access-Control Test** | CoAP | Verifies whether protected CoAP resources require the expected authorization. |
| 37 | **TLS Configuration Test** | TLS | Checks TLS versions, cryptographic configuration and transport-security weaknesses. |
| 38 | **Certificate Inspection** | TLS | Validates certificates, expiration, identity and other certificate issues. |
| 39 | **Credential Validation** | Multiple | Tests supplied or authorized credentials against the correct device service. |
| 40 | **DNS Enumeration** | DNS | Resolves device hostnames and related DNS information within scope. |
| 41 | **Vulnerability Correlation** | Multiple | Correlates device, firmware and service information with known vulnerabilities. |
| 42 | **Command-Injection Validation** | HTTP / Embedded Web | Safely checks whether an input is improperly interpreted as an OS command. |
| 43 | **Path-Traversal Validation** | HTTP / Embedded Web | Checks whether file or path inputs can escape their intended resource boundary. |
| 44 | **CGI / Web-Interface Validation** | HTTP | Validates security weaknesses in embedded CGI and management interfaces. |
| 45 | **Passive Reconnaissance** | Network / DNS / TLS | Collects observable information without actively stressing the target. |
| 46 | **Active Reconnaissance** | Multiple | Performs controlled protocol queries to expand the discovered attack surface. |
| 47 | **Autonomous AutoPwn Validation** | Multiple | Ares chains authorized, non-destructive validation modules to confirm real security impact. |
| 48 | **Re-Validation** | Multiple | Repeats confirmed checks after remediation to verify that the weakness is fixed. |

## How Ares Guides the Attack

**Ares is Blitz's AI reasoning layer.** It analyses the target's devices, services, protocols and previous results, then guides Blitz toward the most relevant next action.

Ares continuously:

- **Understands the target** — identifies device type, exposed services and attack surface.
- **Selects modules** — chooses the appropriate HTTP, RTSP, ONVIF, MQTT, SSH, SNMP and other tests.
- **Builds the attack path** — determines the logical sequence of checks instead of blindly running all modules.
- **Adapts in real time** — uses each module's result to decide what should be tested next.
- **Correlates evidence** — connects findings across multiple services on the same device.
- **Guides validation** — selects the safest relevant validation when a weakness appears exploitable.

Discover → Ares Analyzes → Selects Module → Blitz Executes
                         ↑                  ↓
                         └── Result / Evidence
AutoPwn does not mean uncontrolled exploitation. In Blitz, AutoPwn is an autonomous validation workflow.

Ares analyses the discovered attack surface and selects relevant modules. Blitz then executes only the actions permitted by the Authorization Gate.

AutoPwn is intended to safely demonstrate security impact—for example, confirming that an unauthenticated RTSP stream is accessible, that an HTTP administrative resource bypasses its expected authorization, or that an MQTT account can access a restricted topic.

It is not intended to destroy devices, deploy persistence, intentionally crash services, perform uncontrolled denial-of-service, or propagate automatically beyond the authorized scope.

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

```text
[ 1. One-Click Checkout ] ──► [ 2. Link GitHub Account ] ──► [ 3. Instant Repo Access & Zip Download ]



# Blitz — Installation Guide

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

## The Ultimate Autonomous IoT Red Teaming Arsenal

Blitz transforms fragmented IoT assessment tasks into a high-speed, automated offensive workbench. Whether auditing physical facilities, competing in CTF arenas, or stress-testing hardware in a staging lab, Blitz and the Ares AI engine deliver seven integrated operational capabilities:

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

## The Ultimate Autonomous IoT Red Teaming Arsenal

Blitz transforms fragmented IoT assessment tasks into a high-speed, automated offensive workbench. Whether auditing physical facilities, competing in CTF arenas, or stress-testing hardware in a staging lab, Blitz and the Ares AI engine deliver seven integrated operational capabilities:

---

## Contributing to Blitz

Contributions from security researchers, reverse engineers, and distributed systems developers are welcome. Whether you are adding protocol modules, refining Ares AI reasoning templates, or enhancing the Authorization Gate, follow the operational guidelines below.

---

### Priority Contribution Tracks

* **New Protocol Modules (`blitz-core/`):** Add native decoders and active probes for unmapped embedded interfaces (e.g., BACnet, Modbus, Zigbee over IP, or proprietary camera APIs).
* **Ares AI Reasoning & Heuristics (`ares/`):** Refine planning prompts, fine-tuning datasets, and tool-selection heuristics to improve decision velocity on complex target states.
* **Gateway & Blast-Radius Safety (`ares/bridge/`):** Strengthen the Ares Bridge to catch erratic AI behavior, prevent cyclic planning loops, and enforce strict execution boundaries.
* **Target Hardware Signatures (`configs/`):** Expand device identification matrices and service fingerprint rules in `capabilities.yaml`.

---

### Development Workflow

1. **Fork & Branch:** Create a focused feature branch off `main`:
   ```bash
   git checkout -b feat/add-bacnet-enumeration

   ## Citation

If you reference Blitz or the Ares AI architecture in academic research, technical whitepapers, security assessments, or publications, please cite this repository using the included [`CITATION.cff`](CITATION.cff). BibTeX and standard citation formats are generated automatically by GitHub.

For details regarding the autonomous planning engine, 12-stage closed-loop assessment lifecycle, and domain-specific model fine-tuning, refer to the [Blitz Architecture Documentation](docs/)[cite: 1].

---

## Disclaimer

Blitz is engineered strictly for authorized security assessment, defensive evaluation, vulnerability research, and continuous risk validation on networks, devices, and firmware where explicit written authorization has been granted[cite: 1]. It is designed to be deployed in controlled staging labs, isolated target ranges, and approved client assessment scopes[cite: 1].

ApexPredator Security and the project authors assume no liability and are not responsible for any misuse, operational disruption, device malfunction, or unauthorized deployment of this software. Operators are solely responsible for maintaining compliance with all applicable local, national, and international cybersecurity legislation, organizational policies, and statutory frameworks prior to executing any discovery, assessment, or validation workflow.

---

## License

Blitz is proprietary commercial software distributed under the terms of the ApexPredator Security Commercial License[cite: 1]. A valid commercial license purchase is required to install, deploy, and operate the platform for internal estate assessments or commercial client engagements.

* Redistribution, sublicensing, unauthorized mirroring, or public sharing of the core binaries, source repositories, or fine-tuned model artifacts is strictly prohibited.
* For the full commercial agreement, operational rights, and usage boundaries, see the [`LICENSE`](LICENSE) file[cite: 1].

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
