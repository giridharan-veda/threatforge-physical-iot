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

### The Real Risk

IoT and OT devices now sit inside the same networks that security teams already defend — cameras, sensors, gateways, industrial controllers, smart-home hubs, medical devices, and embedded systems. These devices are rarely tested properly.

Most organizations face the same problems:

- Traditional red team tools were built for Windows and Linux endpoints, not for fragile IoT protocols and constrained devices
- Manual testing is slow, expensive, and does not scale
- Uncontrolled or poorly gated tools can disrupt production systems
- Generic AI tools lack IoT context and frequently produce unsafe or irrelevant actions
- There is usually no reliable way to prove that a test actually succeeded or that a fix actually worked

The result is a dangerous gap: organizations either avoid testing these assets entirely, or they run shallow scans that provide little real security value.

### The Solution — Blitz

**Blitz** is a purpose-built automated red teaming and continuous assessment platform designed specifically for IoT and OT environments.

For **$299** you receive a complete operational system that:

- Continuously discovers IoT and OT assets across multiple protocols
- Builds real, per-device security context
- Uses **Ares**, an IoT-specific AI engine, to generate intelligent and ranked assessment plans
- Enforces a strict multi-condition authorization gate before any test is allowed to run
- Executes only approved actions with full evidence collection
- Clearly distinguishes between “attempted” and “proven” results
- Generates reviewable, evidence-backed findings
- Supports remediation and automatically re-validates that fixes actually held

Blitz turns IoT security testing from a high-risk, manual activity into a controlled, repeatable, and auditable process.

### How Blitz Is Different

Most existing tools fall into one of three categories — and all of them fall short for serious IoT red teaming:

| Existing Approach | Limitation | How Blitz Is Different |
|-------------------|----------|------------------------|
| Traditional red team frameworks (Cobalt Strike, Metasploit, etc.) | Built for enterprise endpoints, not IoT protocols or safety constraints | Native multi-protocol discovery and IoT-aware execution |
| Vulnerability scanners | Find issues but do not safely execute or prove impact | Full closed-loop execution + “attempted vs proven” verification |
| Generic AI agents | Lack domain context and safety controls | Ares is purpose-built for IoT reasoning and sits behind a capability gateway |
| Manual testing | Expensive, non-repeatable, hard to audit | Fully automated 12-stage lifecycle with persistent state and live event streaming |

Blitz is the only platform that combines **IoT-specific AI planning**, **strict authorization controls**, **evidence-backed execution**, and **closed-loop re-validation** in a single commercial product.

### Core Components of Blitz

Blitz is composed of seven tightly integrated components:

| Component | Role |
|-----------|------|
| **Operator Console** | Human control plane for launching assessments and monitoring live results |
| **Ares Agent** | AI orchestration layer that plans and sequences assessments |
| **Ares Bridge** | Capability gateway that enforces what Ares is allowed to request |
| **Ollama** | Local model runtime for private, on-premises AI inference |
| **Blitz Core** | Assessment & execution engine (REST + WebSocket) that runs the full closed-loop lifecycle |
| **Persistent State** | Stores devices, jobs, findings, incidents, and complete audit history |
| **Live Event Stream** | Real-time WebSocket feed of progress, results, and narratives back to the operator |

Together these components deliver continuous, authorized, evidence-backed adversary simulation against IoT and OT estates — without the cost and risk of traditional manual engagements.

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
<img src="https://raw.githubusercontent.com/giridharan-veda/threatforge-physical-iot/main/blitz-architecture.png" width="900" alt="Blitz full operational architecture — Service topology and 12-stage closed-loop assessment lifecycle">
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

Every assessment in Blitz follows a strict, auditable 12-stage process:

| Stage | Name | What Happens |
|-------|------|--------------|
| 1 | **Discover** | Multi-protocol discovery (ARP, mDNS, SSDP, ONVIF, TCP…) |
| 2 | **Resolve Identity** | Confirm IP, MAC, and protocol evidence |
| 3 | **Fingerprint Services** | Map protocol and authentication surfaces per device |
| 4 | **Correlate Context** | Build rich per-device security context |
| 5 | **Build Assessment Plan** | Ares generates a ranked, applicability-aware test plan |
| 6 | **Authorization Gate** | Checks: Authorized? In scope? Capability allowed?<br>Any “No” → request is rejected, logged, and never executed |
| 7 | **Execute Authorized Tests** | Prepare → Execute → Cleanup |
| 8 | **Verify Result** | Clearly distinguishes “attempted” vs “proven” outcomes |
| 9 | **Persist Evidence** | Stores target + module + result + state |
| 10 | **Generate Finding** | Creates an evidence-backed, reviewable finding |
| 11 | **Remediate** | Supports fixing the identified issue |
| 12 | **Re-validate** | Confirms the fix actually held, then loops back to Discover |

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

---

### Persistent State & Live Feedback

| Component | Purpose |
|-----------|---------|
| **Persistent State** | Stores devices, jobs, findings, incidents, and the complete audit history |
| **Live Event Stream** | Real-time WebSocket feed of progress, results, narratives, and state changes |

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

### Technology Stack

| Component | Role |
|-----------|------|
| **Ares** | IoT-specific AI reasoning and orchestration |
| **Ollama** | Local large-language model runtime |
| **Blitz Core** | Closed-loop assessment and execution engine |
| **Python** | Core platform implementation |
| **REST + WebSocket** | Control plane and live event streaming |
| **Docker** | Reproducible and isolated deployment |

---
