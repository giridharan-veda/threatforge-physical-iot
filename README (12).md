# ⚡ BLITZ

## IoT Red Teaming, Security Assessment & Autonomous Operations

### **Find the device. Understand the exposure. Test the attack. Prove the result.**

**Blitz is a purpose-built IoT security platform for discovering, assessing, attacking and validating real network-connected devices.**

It is designed around a simple problem:

> **Finding an IoT vulnerability is not the same thing as understanding whether it matters, testing whether it is actually exploitable, proving what happened, and fixing it.**

Blitz connects those steps into one operational system.

```text
                    ┌──────────────────┐
                    │   IoT NETWORK    │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │    DISCOVER      │
                    │ Devices / IPs    │
                    │ Services / Proto │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │    UNDERSTAND    │
                    │ Identity         │
                    │ Fingerprinting   │
                    │ Context          │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │      PLAN        │
                    │ Applicable       │
                    │ Security Tests   │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │      ATTACK      │
                    │ Authorized       │
                    │ Real-Time Tests  │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │     VERIFY       │
                    │ What actually    │
                    │ happened?        │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │      PROVE       │
                    │ Evidence / Job   │
                    │ / Finding        │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │     REMEDIATE    │
                    │ Fix → Re-test    │
                    └──────────────────┘
```

That workflow is the heart of Blitz.

---

# Why Blitz?

IoT security already has excellent tools.

**HomePwn** is a modular IoT pentesting framework with discovery and technology-specific auditing capabilities across technologies such as Wi-Fi, NFC and BLE.

**IoTHackBot** combines specialized IoT and embedded-security utilities with Claude Code skills, covering areas such as ONVIF, network analysis, firmware, Android and hardware-console access.

**Metasploit** provides a mature general-purpose exploitation framework built around modules for scanning, exploitation and post-exploitation.

**Nuclei** provides a powerful template-based vulnerability detection engine designed to run large numbers of checks efficiently and return evidence from matching requests and responses.

These tools are valuable.

The problem is the operator often becomes the integration layer:

```text
Discover with one tool
       ↓
Fingerprint with another
       ↓
Research the vulnerability
       ↓
Find an appropriate test
       ↓
Run the test
       ↓
Work out whether it actually succeeded
       ↓
Collect evidence
       ↓
Write the finding
       ↓
Remediate
       ↓
Test again
```

**Blitz is built around eliminating that fragmentation for network-layer IoT security operations.**

---

# The Blitz Idea

Blitz does not ask:

> **“How many vulnerabilities can I find?”**

It asks:

> **“What can I establish about this IoT environment, what should I test next, what happened when I tested it, and what evidence proves the result?”**

That changes the unit of value.

A scanner produces **matches**.

A pentest tool produces **actions**.

Blitz is designed to produce an **assessment outcome**.

```text
OBSERVATION
     ↓
SECURITY CONTEXT
     ↓
ASSESSMENT
     ↓
EXECUTION
     ↓
VERIFICATION
     ↓
EVIDENCE
     ↓
FINDING
     ↓
REMEDIATION
```

---

# What Happens When You Put Blitz on a Network?

Imagine an environment containing:

```text
Router
IP Camera
NVR
NAS
Smart Hub
Printer
MQTT Broker
IoT Gateway
```

A traditional workflow can leave the operator with a pile of ports, banners, scan results and vulnerability matches.

Blitz is designed to build a connected model:

```text
                        NETWORK
                           │
        ┌──────────────────┼──────────────────┐
        ▼                  ▼                  ▼
      Camera             NAS              IoT Hub
        │                  │                  │
     ONVIF              HTTP/SSH            MQTT
        │                  │                  │
        ▼                  ▼                  ▼
   Auth Surface       Admin Surface      Broker Surface
        │                  │                  │
        └──────────────────┼──────────────────┘
                           ▼
                  SECURITY CONTEXT
                           │
                           ▼
                    ASSESSMENT PLAN
                           │
                           ▼
                  AUTHORIZED TESTING
                           │
                           ▼
                       EVIDENCE
```

The important part is the relationship between the pieces.

---

# BLITZ IS A CLOSED-LOOP SECURITY SYSTEM

The platform is designed around a closed loop rather than a scan-and-export model.

```text
Discover IoT Environment
          ↓
Resolve Device Identity
          ↓
Fingerprint Services
          ↓
Correlate Security Context
          ↓
Build Assessment Plan
          ↓
Execute Authorized Tests
          ↓
Verify Result
          ↓
Persist Evidence
          ↓
Generate Finding
          ↓
Remediate
          ↓
Re-validate
```

This is what makes Blitz more than a collection of attack modules.

---

# 1. DISCOVER THE REAL ENVIRONMENT

Blitz can combine network discovery mechanisms including:

- ARP
- mDNS
- SSDP
- ONVIF
- TCP discovery

Discovery sources have explicit operational states rather than being silently treated as successful or unsuccessful.

```text
READY
DEGRADED
FAILED
TIMEOUT
UNAVAILABLE
```

That matters because:

> **“A discovery method failed” is not the same conclusion as “the device does not exist.”**

Blitz is designed to preserve that distinction.

---

# 2. BUILD DEVICE IDENTITY

IoT environments are dynamic.

Addresses change.

Services change.

Devices reappear.

Blitz therefore treats identity as more than an IP address.

```text
              ┌── IP
              │
              ├── MAC
              │
              ├── Protocol evidence
              │
              ├── Service evidence
              │
              └── Historical observations
                         │
                         ▼
                 STABLE DEVICE IDENTITY
```

That identity becomes the foundation for later assessment and historical state.

---

# 3. UNDERSTAND THE ATTACK SURFACE

Blitz does more than say:

```text
80/tcp
554/tcp
1883/tcp
22/tcp
```

It builds service-level security context.

For example:

```text
CAMERA
│
├── HTTP
│   ├── Authentication
│   ├── Web paths
│   └── Information exposure
│
├── RTSP
│   ├── Streaming endpoint
│   └── Authentication state
│
└── ONVIF
    ├── Authentication
    ├── Users
    └── Control surface
```

The result is a much better question:

> **Which security tests are relevant to this device?**

---

# 4. CONTEXT BEFORE CONCLUSION

A vulnerability match is not automatically a confirmed vulnerability.

Blitz separates:

```text
Possible Match
     ↓
Applicable Condition
     ↓
Validation
     ↓
Observed Result
```

That distinction is central to trustworthy security testing.

A product/version keyword match should not quietly become:

> **“The device is compromised.”**

The platform instead maintains the relationship between observations, applicability, execution and verification.

---

# 5. PLAN THE RIGHT TESTS

Blitz can convert the collected security context into an assessment plan.

```text
TARGET
  ↓
OBSERVED SERVICES
  ↓
DEVICE CONTEXT
  ↓
AVAILABLE CAPABILITIES
  ↓
APPLICABILITY
  ↓
RANKING
  ↓
TEST PLAN
```

The live console uses `/api/attacks/plan` for validation planning and displays the returned modules as discrete assessment steps.

The point is not:

> **“Run every attack.”**

The point is:

> **“Run the tests that make sense for what Blitz has actually observed.”**

---

# 6. 48 BUILT-IN ATTACK CAPABILITIES

The current Blitz source contains **48 attack capability directories**.

They span major IoT-facing protocols and post-exploitation operations.

## HTTP

```text
Banner / information disclosure
CGI command injection
Basic-auth default credentials
Form default credentials
Login-form brute force
Path traversal
```

## MQTT

```text
Broker enumeration
Authentication brute force
Command injection
Retained-message takeover
TLS default certificate assessment
Wildcard subscription
```

## CoAP

```text
Resource discovery
Default credential / PSK assessment
Observe cancellation
PUT / POST manipulation
```

## ONVIF

```text
User enumeration
Missing-authentication enumeration
Administrator creation
User modification
PTZ control
Reboot
```

## RTSP

```text
Default credentials
Brute force
Stream hijacking
URI traversal
Malformed-packet testing
```

## SNMP

```text
Community brute force
Default credentials
GET information
SET configuration
```

## SSH / Telnet

```text
SSH brute force
SSH default credentials / shell
SSH key injection
SSH lateral movement
Telnet command execution
Telnet default credentials / shell
```

## UPnP

```text
Device information
Configuration abuse
Port mapping creation
Port mapping deletion
```

## Post-Exploitation / Lateral Movement

```text
Credential replay
MQTT bot registration
Cron persistence
SSH-key persistence
SOCKS pivot proxy
Session execution
SSH lateral movement
```

The differentiator is not merely “48.”

It is that these capabilities live **inside the Blitz assessment lifecycle**.

---

# 7. ATTACKS ARE CAPABILITIES, NOT RANDOM SCRIPTS

A Blitz capability follows a structured lifecycle:

```text
Applicable
    ↓
Prepare
    ↓
Execute
    ↓
Verify
    ↓
Cleanup
    ↓
Result
```

The platform owns the surrounding control plane:

```text
Authorization
Scope
Deadlines
Cancellation
Interaction Budget
Evidence
Audit
Verification
Cleanup
Result Normalization
```

This creates an important separation:

> **The attack capability performs the operation. Blitz controls the conditions under which that operation is allowed to happen.**

---

# 8. REAL-TIME AUTHORIZED TESTING

Blitz is designed for active security testing against authorized targets.

The operational path is:

```text
PLAN
 ↓
AUTHORIZE
 ↓
CHECK TARGET SCOPE
 ↓
EXECUTE
 ↓
OBSERVE
 ↓
VERIFY
 ↓
RECORD
```

This is where Blitz moves beyond passive discovery.

The current platform supports execution jobs, live execution events, deadlines, cancellation and evidence persistence.

---

# 9. DON'T CONFUSE ATTEMPTED WITH PROVEN

One of the most important design ideas in Blitz is outcome strength.

The platform recognizes progressively stronger assessment states:

```text
DETECTED
   ↓
VALIDATED
   ↓
AUTHENTICATED
   ↓
PRIVILEGE CONFIRMED
   ↓
LATERAL PATH CONFIRMED
```

For example:

```text
“SSH is open”
```

is an observation.

```text
“The supplied credentials were accepted”
```

is an authentication result.

```text
“Privileged access was established”
```

is a materially stronger security result.

Blitz is designed to preserve these distinctions.

---

# 10. EVIDENCE IS NOT AN AFTERTHOUGHT

A serious security product must answer:

> **“Show me.”**

Blitz maintains execution and evidence state instead of reducing an operation to one sentence in a report.

A completed operation can be represented as:

```text
TARGET
  +
MODULE
  +
ACTION
  +
OBSERVED RESULT
  +
VERIFICATION
  +
EXECUTION STATE
  =
EVIDENCE
```

The live console can retrieve an evidence package for the completed job.

That makes the result reviewable rather than purely narrative.

---

# 11. ARES — THE REASONING LAYER

Then there is **Ares**.

Ares is not simply a chatbot attached to Blitz.

It operates as the reasoning and orchestration layer above the Blitz security engine.

```text
                   ┌───────────────┐
                   │    OPERATOR   │
                   └───────┬───────┘
                           │
                           ▼
                   ┌───────────────┐
                   │     ARES      │
                   │   Reasoning   │
                   │ Orchestration │
                   └───────┬───────┘
                           │
                           ▼
                   ┌───────────────┐
                   │    BLITZ      │
                   │ Assessment &  │
                   │   Execution   │
                   └───────┬───────┘
                           │
                  ┌────────┼────────┐
                  ▼        ▼        ▼
              Discover   Attack   Verify
                           │
                           ▼
                        Evidence
```

The current console implements an actual workflow:

```text
SESSION
   ↓
PLAN
   ↓
AUTONOMOUS RUN
   ↓
WATCH JOB
   ↓
RESULT DIGEST
   ↓
NARRATIVE
```

Ares can request a Blitz plan, launch the resulting job, watch its timeline, obtain job information, retrieve a narrative and refresh the live Blitz state afterwards.

So the relationship is:

> **Ares reasons. Blitz operates. Evidence tells you what actually happened.**

---

# 12. AUTONOMY WITHOUT LOSING CONTROL

Blitz is not designed around:

```text
AI
 ↓
Unrestricted Exploitation
```

The intended model is:

```text
LIVE ENVIRONMENT
      ↓
ARES REASONS
      ↓
BLITZ BUILDS / EXECUTES PLAN
      ↓
SECURITY CONTROLS
      ↓
VERIFIED RESULT
      ↓
ARES INTERPRETS
      ↓
OPERATOR REVIEW
```

The operator remains inside the security boundary.

---

# 13. STOP THE OPERATION

Automation without control is not a professional security workflow.

The console provides an emergency-stop path for active Blitz jobs.

```text
                RUNNING
                   │
          ┌────────┴────────┐
          ▼                 ▼
       CONTINUE          EMERGENCY
                          STOP
```

That is especially important for active IoT testing where device stability and service availability matter.

---

# 14. ATTACK PATHS

IoT compromise rarely exists in isolation.

A vulnerable camera may sit on the same network as an NVR.

An NVR may communicate with a storage system.

An IoT gateway may have relationships with other assets.

Blitz can represent those relationships as a candidate attack path:

```text
Origin
  ↓
Observed Device
  ↓
Network / Service Relationship
  ↓
Potentially Exposed Device
  ↓
Candidate Security Path
```

A candidate path remains a candidate until further validation establishes it.

That keeps attack-path analysis useful without presenting hypotheses as confirmed compromises.

---

# 15. FROM FINDING TO FIX

A security platform should not end at “Critical.”

Blitz connects assessment with remediation and re-validation.

```text
Assessment
    ↓
Finding
    ↓
Remediation
    ↓
Re-validation
    ↓
Confirmed New State
```

The current console provides remediation operations, re-validation handoff, telemetry controls and audit visibility.

This changes the customer outcome from:

> **“We found 17 vulnerabilities.”**

to:

> **“We found them, tested them, fixed them, and tested the resulting state again.”**

---

# 16. PERSISTENT SECURITY MEMORY

Blitz maintains persistent operational state for things such as:

```text
Devices
Assessments
Objectives
Jobs
Observations
Events
Findings
Incidents
Execution Records
```

That creates:

```text
CURRENT STATE
     +
HISTORICAL STATE
     +
EXECUTION HISTORY
     =
OPERATIONAL SECURITY CONTEXT
```

A scan gives you a snapshot.

Blitz is designed to maintain a security picture.

---

# 17. LIVE OPERATIONS, NOT A STATIC DASHBOARD

The Blitz console is built around live operational state.

It brings together:

```text
Environment
Devices
Risk
Findings
Events
Incidents
SIEM
Audit
Assessment
Attack Operations
Remediation
Ares
```

The frontend consumes the real Blitz REST and WebSocket interfaces rather than maintaining a fictional data layer.

The Ares interface itself exposes session, plan, autonomous execution, job monitoring and narrative workflows.

---

# 18. WHAT MAKES BLITZ DIFFERENT

Not “more features.”

A different **operating model**.

| Capability | Traditional IoT Toolkit | Vulnerability Scanner | Exploit Framework | **Blitz** |
|---|---|---|---|---|
| Discover devices | ✓ | ✓ | Partial | **✓** |
| IoT protocol awareness | ✓ | Partial | Partial | **✓** |
| Maintain device context | Partial | Partial | Session-based | **✓** |
| Context-aware planning | Limited | Template/workflow based | Module based | **✓** |
| Active testing | ✓ | Limited | ✓ | **✓** |
| Verification lifecycle | Tool-dependent | Check-dependent | Module-dependent | **Built into workflow** |
| Persistent assessment state | Limited | Results-oriented | ✓ | **✓** |
| Evidence tied to execution | Partial | ✓ | ✓ | **✓** |
| Attack-path context | Limited | Limited | Available through workflows | **✓** |
| Remediation loop | Usually external | Usually external | Usually external | **Integrated** |
| Re-validation | Manual | Manual/workflow | Manual/workflow | **Integrated** |
| AI reasoning layer | Varies | Increasingly available | Separate | **Ares** |
| IoT-focused end-to-end workflow | Partial | No | No | **Core purpose** |

The fair comparison is important.

HomePwn remains a strong specialist toolkit with a different technology focus and operating model.

IoTHackBot is interesting precisely because it assembles many specialized utilities and AI-assisted workflows.

Metasploit is far broader than IoT and has a much larger general-purpose exploitation ecosystem.

Nuclei is exceptionally strong as an extensible detection engine and template ecosystem.

**Blitz is not trying to win by being “another Metasploit.”**

It is trying to win by being:

# **The system an IoT security operator lives inside.**

---

# Why That Matters

A collection of specialist tools gives you capabilities.

An integrated platform gives you **continuity**.

```text
TOOLCHAIN
─────────────
Discovery
   ↓
Export
   ↓
Different tool
   ↓
Manual context
   ↓
Another tool
   ↓
Manual evidence
   ↓
Manual reporting
   ↓
Manual remediation
```

versus:

```text
BLITZ
─────────────────────────────
Discover
   ↓
Understand
   ↓
Plan
   ↓
Attack
   ↓
Verify
   ↓
Prove
   ↓
Remediate
   ↓
Re-test
```

**The operator stops being the glue.**

That is the value proposition.

---

# Why $299?

Because the product is not priced as a port scanner.

It is priced as an integrated professional workflow.

```text
             BLITZ
               │
     ┌─────────┼─────────┐
     ▼         ▼         ▼
 Discovery  Intelligence Attack
     │         │         │
     └─────────┼─────────┘
               ▼
            Verify
               ▼
            Evidence
               ▼
           Findings
               ▼
          Remediation
               ▼
          Re-validation
               │
               ▼
             ARES
```

The customer is paying for the reduction in operational fragmentation.

Instead of maintaining separate workflows for:

```text
Asset discovery
+
IoT fingerprinting
+
Security correlation
+
Attack planning
+
Execution
+
Verification
+
Evidence
+
Reporting
+
Remediation
+
Re-testing
+
AI orchestration
```

Blitz gives the operator one connected environment.

---

# $299 Means Something Very Specific

It does **not** mean:

> “Pay $299 because Blitz has AI.”

It means:

> **“Pay $299 for a purpose-built IoT security operation that connects the work you would otherwise perform across multiple tools and manual steps.”**

That is a much stronger product argument.

---

# Built for People Who Actually Test IoT

## Penetration Testers

Run repeatable IoT assessments without rebuilding the workflow for every engagement.

## Red Teams

Move from discovery to controlled active testing and evidence.

## Security Consultants

Produce assessments that can be explained, reviewed and re-tested.

## IoT Security Researchers

Work directly with protocol-specific assessment capabilities.

## Enterprise Security Teams

Maintain visibility over IoT assets, findings, attack paths and remediation.

## Advanced Security Practitioners

Use a dedicated IoT security operations environment instead of adapting generic tools for every engagement.

---

# What Blitz Is Really Selling

Not:

```text
48 attacks
```

Not:

```text
AI
```

Not:

```text
A dashboard
```

Not:

```text
Another vulnerability scanner
```

Blitz is selling this:

```text
                    CONFIDENCE

                       ▲
                       │
                 VERIFICATION
                       │
                    EVIDENCE
                       │
                   EXECUTION
                       │
                    PLANNING
                       │
                    CONTEXT
                       │
                    IDENTITY
                       │
                   DISCOVERY
```

The higher you move through this stack, the stronger your security conclusion becomes.

---

# The Blitz Philosophy

## Discover before you assume.

## Context before you classify.

## Plan before you execute.

## Verify before you claim.

## Preserve evidence before you report.

## Remediate before you close.

## Re-test before you declare victory.

That is the standard Blitz is built around.

---

# Architecture

```text
                    ┌─────────────────────┐
                    │  BLITZ OPERATIONS   │
                    │       CONSOLE       │
                    └──────────┬──────────┘
                               │
             ┌─────────────────┼─────────────────┐
             │                 │                 │
             ▼                 ▼                 ▼
       ┌───────────┐     ┌────────────┐    ┌───────────┐
       │ ARES AGENT│     │ ARES BRIDGE│    │ BLITZ CORE│
       │  :9010    │────▶│   :8089    │───▶│   :8088   │
       └─────┬─────┘     └────────────┘    └─────┬─────┘
             │                                     │
             ▼                                     ▼
       ┌───────────┐                       ┌──────────────┐
       │  OLLAMA   │                       │  PERSISTENT  │
       │   :11435  │                       │    STATE     │
       └───────────┘                       └──────────────┘
                                                    │
                                                    ▼
                                           ┌────────────────┐
                                           │ LIVE EVENTS /  │
                                           │    RESULTS     │
                                           └────────────────┘
```

The current service model is:

| Service | Port | Interface | Role |
|---|---:|---|---|
| `blitz` | `8088` | REST + WebSocket | IoT inventory, discovery, assessment, jobs, remediation |
| `ares-bridge` | `8089` | MCP | Capability execution gateway |
| `ares-agent` | `9010` | MCP | Orchestration |
| `ollama` | `11435` | REST | Local model runtime |

---

# IoT Security Coverage

Blitz is focused on network-layer IoT environments, including assets such as:

```text
IP Cameras
NVRs
Routers
Gateways
NAS
Smart Hubs
Printers
Smart Speakers
Smart TVs
Thermostats
IoT Gateways
```

Protocol capability includes:

```text
HTTP
RTSP
MQTT
CoAP
ONVIF
SNMP
SSH
Telnet
UPnP
```

The attack fabric is designed around supported capabilities rather than unrestricted arbitrary exploit execution.

---

# Security by Design

Active operations are bounded by controls around:

```text
Operator Authorization
Target Scope
Capability Policy
Deadlines
Cancellation
Interaction Budgets
Evidence Handling
Secret Redaction
Auditability
Verification
```

The intended decision path is:

```text
Operator Request
      ↓
Authorized?
   ┌──┴──┐
   │     │
  NO    YES
   │     │
 Reject  Target in Scope?
            ┌──┴──┐
            │     │
           NO    YES
            │     │
          Reject  Capability Allowed?
                        ┌──┴──┐
                        │     │
                       NO    YES
                        │     │
                      Reject  Execute
                               ↓
                             Verify
                               ↓
                        Record Evidence
```

---

# BLITZ IN ONE PICTURE

```text
                         ┌─────────────────┐
                         │    OPERATOR     │
                         └────────┬────────┘
                                  │
                                  ▼
                         ┌─────────────────┐
                         │      ARES       │
                         │  REASON / PLAN  │
                         └────────┬────────┘
                                  │
                                  ▼
                    ┌──────────────────────────┐
                    │          BLITZ           │
                    │                          │
                    │  DISCOVER                │
                    │      ↓                   │
                    │  IDENTIFY                │
                    │      ↓                   │
                    │  FINGERPRINT             │
                    │      ↓                   │
                    │  CORRELATE               │
                    │      ↓                   │
                    │  PLAN                    │
                    │      ↓                   │
                    │  ATTACK                  │
                    │      ↓                   │
                    │  VERIFY                  │
                    │      ↓                   │
                    │  EVIDENCE                │
                    │      ↓                   │
                    │  FINDING                 │
                    │      ↓                   │
                    │  REMEDIATE               │
                    │      ↓                   │
                    │  RE-VALIDATE             │
                    └────────────┬─────────────┘
                                 │
                                 ▼
                         ┌─────────────────┐
                         │  PROVABLE       │
                         │ SECURITY RESULT │
                         └─────────────────┘
```

---

# THE BLITZ PROMISE

**Don't just find the IoT device.**

**Understand it.**

**Don't just identify a vulnerability.**

**Test it.**

**Don't just run an attack.**

**Verify it.**

**Don't just produce a report.**

**Preserve the evidence.**

**Don't just report the problem.**

**Fix it.**

**Don't just fix it.**

**Test it again.**

---

# BLITZ

## **IoT Security, From Discovery to Proof.**

### **Discover → Understand → Attack → Verify → Prove → Remediate**

**$299**

Built by **Apex Predator Security Technologies**

---

## Responsible Use

Blitz is an offensive-security platform intended for authorized security testing.

Use it only against systems you own, systems for which you have explicit authorization, or environments covered by an approved assessment scope.

## License

See the repository license and commercial terms accompanying the product distribution.
