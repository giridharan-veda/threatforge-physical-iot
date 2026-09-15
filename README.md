<div align="center">

<img src="assets/blitz-banner.svg" width="100%" alt="Blitz — Automated IoT Red Teaming Platform powered by Ares">

**Automated IoT Red Teaming & Continuous Assessment Platform**

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
