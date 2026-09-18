<div align="center">

<img src="https://raw.githubusercontent.com/giridharan-veda/threatforge-physical-iot/main/blitz-banner.svg" width="100%" alt="Blitz — Autonomous IoT Red Teaming Platform powered by Ares">

# ⚡ Blitz

### Find every IoT/OT device. Attack it. Prove it. Re-validate it. Autonomously.

**The only autonomous IoT/OT red teaming platform that runs 100% on-prem, ships with a fine-tuned local AI, and covers 154 attack modules across 28 categories — for $299, once.**

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Docker](https://img.shields.io/badge/Docker-Supported-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)
[![Ares AI](https://img.shields.io/badge/Ares-IoT%20AI%20Engine-purple)](#-ares-ai--the-intelligence-layer)
[![Modules](https://img.shields.io/badge/Modules-154-informational)](#-attack-surface--154-modules-across-28-categories)
[![Categories](https://img.shields.io/badge/Categories-28-blueviolet)](#-attack-surface--154-modules-across-28-categories)
[![LLM](https://img.shields.io/badge/LLM-ares--1.7b%20local-blue)](#-ares-ai--the-intelligence-layer)
[![Price](https://img.shields.io/badge/Early%20Adopter-%24299-brightgreen)](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)

**[ 🚀 BUY EARLY ADOPTER LICENSE — $299 ](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)**  •  **[ 📺 WATCH 60-SEC DEMO ](#-see-it-run)**

**🔥 First 25 licenses only — code `EARLYBIRD` • $499 standard • Perpetual commercial rights • Lifetime updates**

[📺 Demo](#-see-it-run) • [🎁 What You Get](#-what-you-get-for-299) • [📊 Proof](#-proof) • [👥 Who It's For](#-who-blitz-is-for) • [⚔️ vs Alternatives](#️-blitz-vs-everything-else) • [💰 Pricing](#-pricing--read-this-before-you-buy-anything-else) • [❓ FAQ](#-faq) • [⚙️ Install](#️-installation)

</div>

---

<a name="-see-it-run"></a>
## 📺 See It Run

```console
$ blitz scan 192.168.1.0/24

[🔍 SCAN]      Discovered 4 IoT devices
[🧠 CLASSIFY]  192.168.1.50 → Hikvision IP camera   (confidence 0.94)
[🧠 CLASSIFY]  192.168.1.51 → Dahua NVR             (confidence 0.87)
[🧠 CLASSIFY]  192.168.1.60 → Raspberry Pi          (confidence 0.91)
[🧠 CLASSIFY]  192.168.1.70 → Unknown device        (investigating...)

[🎯 PLAN]      Ares planning assessment for 192.168.1.50
               → firmware-identify → http-banner-info-disclosure
               → rtsp-default-credentials → firmware-cve-match

[🔒 AUTHORIZE] ✓ authorized | ✓ in scope | ✓ non-destructive → PROCEED

[⚔️ EXECUTE]   firmware-identify ............ Hikvision DS-2CD, firmware 5.6.3
[⚔️ EXECUTE]   http-banner-info-disclosure .. Server: webs, PHP/5.4.16
[⚔️ EXECUTE]   rtsp-default-credentials ..... ✓ admin:admin accepted
[⚔️ EXECUTE]   firmware-cve-match ........... CVE-2021-36260 applicable

[💀 PROVE]     CRITICAL — Unauthenticated RCE available
               Evidence:  evidence/192.168.1.50/CVE-2021-36260-probe.txt
               State:     PROVEN (not attempted)

✅ Assessment complete in 47 seconds. 4 devices, 3 findings (1 critical).
```

> 📹 **[Watch the 60-second demo →](#)** — full run from scan to proof. *(Placeholder: link to your Loom/YouTube demo.)*

Every other IoT tool's README says "autonomous." **Blitz shows you what that looks like.** 🔥

---

<a name="-what-you-get-for-299"></a>
## 🎁 What You Get For $299

**One-time purchase. Perpetual commercial rights. Zero per-token fees. Zero per-device fees. Zero subscriptions.** 💯

<table align="center">
<thead>
<tr>
<th align="center">🎯 Deliverable</th>
<th align="center">📝 What It Includes</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">⚔️ <b>154 attack modules</b></td>
<td align="center">Across 28 categories: firmware, wireless, cloud, mobile, voice assistants, hardware interfaces</td>
</tr>
<tr>
<td align="center">🧠 <b>Fine-tuned local AI</b></td>
<td align="center">The <code>ares</code> 1.7B model — runs on Ollama, offline, on your own hardware</td>
</tr>
<tr>
<td align="center">🔬 <b>Full training pipeline</b></td>
<td align="center">SFT + GRPO + RFT + curriculum — retrain on your own data with an 8 GB GPU</td>
</tr>
<tr>
<td align="center">🔄 <b>12-stage lifecycle</b></td>
<td align="center">Discovery → Fingerprint → Plan → Authorize → Execute → Prove → Remediate → Re-validate</td>
</tr>
<tr>
<td align="center">🔒 <b>Multi-condition safety gate</b></td>
<td align="center">Authorized? In scope? Capability allowed? Nothing runs without clearance</td>
</tr>
<tr>
<td align="center">📊 <b>Evidence-backed findings</b></td>
<td align="center">Every result labeled <i>attempted</i> or <i>proven</i>. No speculation, ever.</td>
</tr>
<tr>
<td align="center">✅ <b>Automatic re-validation</b></td>
<td align="center">After a patch ships, Blitz re-checks automatically — fix attestation, not a guess</td>
</tr>
<tr>
<td align="center">🛡️ <b>Air-gapped by default</b></td>
<td align="center">Zero telemetry. Zero cloud. Your data never leaves your network.</td>
</tr>
<tr>
<td align="center">⚙️ <b><code>blitz-setup.sh</code> installer</b></td>
<td align="center">One command to deploy the full stack</td>
</tr>
<tr>
<td align="center">♾️ <b>Lifetime updates</b></td>
<td align="center">New modules, new CVE profiles, engine upgrades — included forever</td>
</tr>
</tbody>
</table>

---

## 🚨 The Problem

Security teams spent 20 years getting good at defending laptops and servers. Attackers noticed, and moved somewhere easier: **IoT and OT**. 💀

The cameras, sensors, controllers, and gateways quietly running your buildings, factories, and hospitals are on the same network as everything you protect — with almost none of the same rigor.

<table align="center">
<thead>
<tr>
<th align="center">🕳️ The Gap</th>
<th align="center">💥 What It Looks Like in Practice</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">🕵️ <b>Invisible inventory</b></td>
<td align="center">You don't know what IoT devices you have.</td>
</tr>
<tr>
<td align="center">🔑 <b>Default passwords</b></td>
<td align="center"><code>admin:admin</code>, unchanged, for the life of the device.</td>
</tr>
<tr>
<td align="center">🚪 <b>Unauthenticated services</b></td>
<td align="center">Video streams, control panels, management UIs built to "just work."</td>
</tr>
<tr>
<td align="center">📡 <b>Plaintext traffic</b></td>
<td align="center">Credentials and keys visible on the wire.</td>
</tr>
<tr>
<td align="center">🧱 <b>"Segmented" is a belief</b></td>
<td align="center">Flat networks turn one device into a path to everything.</td>
</tr>
<tr>
<td align="center">🛠️ <b>Nothing gets patched</b></td>
<td align="center">No update lifecycle. Known weaknesses persist for years.</td>
</tr>
<tr>
<td align="center">🙈 <b>Detection blind spots</b></td>
<td align="center">Your IT security tooling cannot see IoT/OT compromise.</td>
</tr>
<tr>
<td align="center">✅❌ <b>"Fixed" is assumed</b></td>
<td align="center">Fixes rarely get re-verified. Resolved risk often isn't.</td>
</tr>
</tbody>
</table>

> 🚨 **This is the default state of every IoT/OT network — including yours.** The devices you trust most are the ones you've tested least. 🎯

---

## 🛡️ The Solution

**Blitz** is a fully autonomous IoT/OT red teaming system. It discovers, plans, attacks, proves, and re-validates — continuously, safely, entirely on-prem.

<table align="center">
<thead>
<tr>
<th align="center">✨ Capability</th>
<th align="center">🎯 What It Does</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">🔍 <b>Profiles each device first</b></td>
<td align="center">Learns what it is, what it speaks, what it exposes — then plans an attack built for that device.</td>
</tr>
<tr>
<td align="center">🔒 <b>Authorization gate</b></td>
<td align="center">Every action passes multi-condition checks before execution. Safe to run continuously on live infrastructure.</td>
</tr>
<tr>
<td align="center">📊 <b>Evidence-backed results</b></td>
<td align="center">Labeled <i>attempted</i> or <i>proven</i>. Fixes are automatically re-validated.</td>
</tr>
<tr>
<td align="center">🧠 <b>Ares plans the assessment</b></td>
<td align="center">No human at the keyboard required for every test.</td>
</tr>
<tr>
<td align="center">🖥️ <b>Runs 100% on-prem</b></td>
<td align="center">The <code>ares</code> model runs locally via Ollama. No cloud. No per-token fees. No telemetry.</td>
</tr>
</tbody>
</table>

**Traditional IoT scanners stop at:**

> 🥱 "Port 554 is open."

**Blitz asks:**

> 🔥 **"What does that service expose, how does it behave, what protects it, and can the weakness be safely demonstrated?"**

---

<a name="-proof"></a>
## 📊 Proof

### 🏆 Benchmarks *(Placeholder — fill with real results)*

<table align="center">
<thead>
<tr>
<th align="center">📊 Metric</th>
<th align="center">⚡ Blitz</th>
<th align="center">🥱 Traditional Scanner</th>
<th align="center">🐢 Manual Pentest</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">⏱️ Time to first finding</td>
<td align="center"><b>47 sec</b></td>
<td align="center">15 min</td>
<td align="center">2 days</td>
</tr>
<tr>
<td align="center">📡 Devices discovered / hour</td>
<td align="center"><b>120</b></td>
<td align="center">40</td>
<td align="center">10</td>
</tr>
<tr>
<td align="center">🎯 False positive rate</td>
<td align="center"><b>&lt;5%</b></td>
<td align="center">~30%</td>
<td align="center">~10%</td>
</tr>
<tr>
<td align="center">🔄 Re-validation after patch</td>
<td align="center"><b>Automatic</b></td>
<td align="center">Manual</td>
<td align="center">Manual</td>
</tr>
<tr>
<td align="center">🤖 Runs unattended</td>
<td align="center"><b>Yes</b></td>
<td align="center">No</td>
<td align="center">No</td>
</tr>
<tr>
<td align="center">💰 Cost per year</td>
<td align="center"><b>$299 once</b></td>
<td align="center">$10k+</td>
<td align="center">$25k+</td>
</tr>
</tbody>
</table>

> 📖 Methodology and lab setup documented in `/docs/benchmarks`. *(Replace with your actual numbers before publishing.)*

### 🔬 Lab-Validated Devices *(Placeholder — fill with real list)*

<table align="center">
<thead>
<tr>
<th align="center">🏷️ Category</th>
<th align="center">📦 Devices Tested</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">📹 <b>IP Cameras</b></td>
<td align="center">Hikvision DS-2CD series, Dahua NVR, Reolink, Amcrest</td>
</tr>
<tr>
<td align="center">💡 <b>Smart Home</b></td>
<td align="center">Philips Hue Bridge, Shelly Plug S, Shelly 1, Tuya devices</td>
</tr>
<tr>
<td align="center">🤖 <b>Single-Board Computers</b></td>
<td align="center">Raspberry Pi 4, Pi Zero 2W, ESP32, ESP8266</td>
</tr>
<tr>
<td align="center">🔊 <b>Voice Assistants</b></td>
<td align="center">Amazon Echo (Gen 3/4), Google Nest Hub</td>
</tr>
<tr>
<td align="center">🌐 <b>Network Gear</b></td>
<td align="center">TP-Link, Netgear, MikroTik routers</td>
</tr>
<tr>
<td align="center">🏭 <b>Industrial</b></td>
<td align="center">Modbus RTU/TCP devices, BACnet controllers</td>
</tr>
</tbody>
</table>

### 💀 Sample Finding (Redacted)

```yaml
🎯 Finding:       Unauthenticated Remote Code Execution
📦 Device:        Hikvision DS-2CD2143G0-I
🔧 Firmware:      V5.6.3
💀 CVE:           CVE-2021-36260
📊 CVSS:          9.8 (Critical)
✅ State:         PROVEN (not attempted)
📁 Evidence:      evidence/192.168.1.50/CVE-2021-36260-probe.txt
🛠️ Remediation:   Upgrade firmware to V5.7.3 or later
🔄 Re-validation: Pending — will re-check automatically after patch
```

### 💬 What Early Adopters Are Saying *(Placeholder)*

<table align="center">
<thead>
<tr>
<th align="center">👤 Role</th>
<th align="center">💬 Quote</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">🏢 <b>CISO, [Company]</b></td>
<td align="center"><i>"Blitz found issues our $25k pentest missed."</i></td>
</tr>
<tr>
<td align="center">🛠️ <b>Red Team Lead, [Company]</b></td>
<td align="center"><i>"The safety gate is the reason we can run it continuously."</i></td>
</tr>
<tr>
<td align="center">🔬 <b>Security Researcher, [Institution]</b></td>
<td align="center"><i>"Retraining on our own engagement data took 3 hours."</i></td>
</tr>
</tbody>
</table>

*(Replace with real quotes. Offer early adopters a discount or free license in exchange.)*

---

<a name="-who-blitz-is-for"></a>
## 👥 Who Blitz Is For

<table align="center">
<thead>
<tr>
<th align="center">🎭 Persona</th>
<th align="center">🎯 Why They Choose Blitz</th>
<th align="center">🚀 Start Here</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">🔬 <b>Security Researchers</b></td>
<td align="center">Study how LLMs perform on real IoT attack planning. Full pipeline ships with Blitz. Retrain on your own data with one 8 GB GPU.</td>
<td align="center"><a href="#-ares-ai--the-intelligence-layer">🧠 Ares AI</a></td>
</tr>
<tr>
<td align="center">🏢 <b>Enterprise Security Teams</b></td>
<td align="center">Replace $25,000 engagements with continuous automated assessment. Evidence-backed. Re-validated. On-prem.</td>
<td align="center"><a href="#-pricing--read-this-before-you-buy-anything-else">💰 Why Blitz</a></td>
</tr>
<tr>
<td align="center">🛠️ <b>Red Teams &amp; Consultants</b></td>
<td align="center">154 modules across firmware, wireless, cloud, mobile, voice assistants. No new hardware for network testing.</td>
<td align="center"><a href="#-attack-surface--154-modules-across-28-categories">⚔️ Attack Surface</a></td>
</tr>
<tr>
<td align="center">🎯 <b>Lab &amp; CTF Enthusiasts</b></td>
<td align="center">Deploy against QEMU device farms or your own home lab. Every module documents its preconditions. Safe on your own devices.</td>
<td align="center"><a href="#️-installation">⚙️ Install</a></td>
</tr>
</tbody>
</table>

---

## 🧠 How Blitz Works

Blitz is a closed-loop autonomous system with five core components.

<table align="center">
<thead>
<tr>
<th align="center">🧩 Component</th>
<th align="center">🎯 Role</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">🎛️ <b>Operator Console</b></td>
<td align="center">Human control plane. Launch assessments, approve/deny actions, watch live progress.</td>
</tr>
<tr>
<td align="center">🧠 <b>Ares Agent</b></td>
<td align="center">AI orchestration layer. Profiles devices, plans assessments, picks the next module.</td>
</tr>
<tr>
<td align="center">🔒 <b>Ares Bridge</b></td>
<td align="center">Capability gateway. Every action is checked against multi-condition rules before execution.</td>
</tr>
<tr>
<td align="center">🖥️ <b>Ollama</b></td>
<td align="center">Local model runtime. Runs the <code>ares</code> model entirely on-prem.</td>
</tr>
<tr>
<td align="center">⚙️ <b>Blitz Core</b></td>
<td align="center">Execution engine. Runs approved modules, collects evidence, drives the 12-stage lifecycle.</td>
</tr>
<tr>
<td align="center">🗄️ <b>Persistent State</b></td>
<td align="center">Durable audit trail. Devices, jobs, findings, incidents — everything, forever.</td>
</tr>
<tr>
<td align="center">📡 <b>Live Event Stream</b></td>
<td align="center">Real-time WebSocket feed to the operator GUI. Watch it happen live.</td>
</tr>
</tbody>
</table>

**🔄 Data Flow:**

```text
Operator → Ares Agent → Ares Bridge (:8089) → Ollama (:11435)
                          ↓
                     Blitz Core (:8088) → Target Devices 🎯
                          ↓
                     Persistent State + WebSocket Events 📡
```

---

<a name="-ares-ai--the-intelligence-layer"></a>
## 🧠 Ares AI — The Intelligence Layer

**Ares** is the autonomous reasoning engine inside Blitz. It observes device state, reasons about what a device is, and picks the next appropriate module from **154 modules across 28 categories**. 🎯

Ares does **not** perform network attacks. It acts purely as a decision engine. **Ares proposes, Blitz disposes.** ⚖️

The model powering Ares — **`ares`** — is a 1.7B Qwen3 variant fine-tuned specifically for IoT pentesting. It runs locally via Ollama. **Device context and reasoning never leave your network.** 🛡️

### 🎓 How Ares Was Trained

Reproducible on a single 8 GB GPU in under 3 hours. Full pipeline ships in `/training/`.

<table align="center">
<thead>
<tr>
<th align="center">🎯 Stage</th>
<th align="center">🛠️ Method</th>
<th align="center">📊 Result</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center"><b>1️⃣ SFT</b></td>
<td align="center">QLoRA on 638 curated examples</td>
<td align="center">~85% correct routing</td>
</tr>
<tr>
<td align="center"><b>2️⃣ GRPO</b></td>
<td align="center">Rule-based reward alignment</td>
<td align="center">~98% JSON validity, ~92% routing, 100% safety refusal</td>
</tr>
<tr>
<td align="center"><b>3️⃣ RFT</b></td>
<td align="center">Self-improvement loop (638 → ~1,000 examples)</td>
<td align="center">Higher data quality, no new human labels</td>
</tr>
<tr>
<td align="center"><b>4️⃣ Curriculum</b></td>
<td align="center">Easy → hard sorting</td>
<td align="center">Smoother training, +1–3% final accuracy</td>
</tr>
</tbody>
</table>

**💀 The Reward Function (Actual Code):**

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

<table align="center">
<thead>
<tr>
<th align="center">🔧 Feature</th>
<th align="center">🎯 What It Enables</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">🔄 <b>Hot-swappable brain</b></td>
<td align="center">Point Ares at DeepSeek-Coder, Llama, Mistral, or your own endpoint through the Ares Bridge — no code changes.</td>
</tr>
<tr>
<td align="center">🔬 <b>Retrain on your own data</b></td>
<td align="center">Every engagement becomes training data. The pipeline is included.</td>
</tr>
<tr>
<td align="center">🛡️ <b>Air-gapped by default</b></td>
<td align="center">Zero telemetry. Zero cloud. Your data never leaves your network.</td>
</tr>
</tbody>
</table>

---

<a name="-attack-surface--154-modules-across-28-categories"></a>
## 🔬 Attack Surface — 154 Modules Across 28 Categories

Blitz covers **every layer** where IoT devices have been shown to be exploitable in the wild.

<details>
<summary><b>🌐 Network Protocols (48 modules) — click to expand</b></summary>

<table align="center">
<thead>
<tr>
<th align="center">🔌 Protocol</th>
<th align="center">📦 Modules</th>
<th align="center">🎯 What It Tests</th>
</tr>
</thead>
<tbody>
<tr><td align="center"><b>HTTP / HTTPS</b></td><td align="center">6</td><td align="center">Web login, admin pages, access control, input flaws</td></tr>
<tr><td align="center"><b>RTSP</b></td><td align="center">5</td><td align="center">Video-stream exposure and authentication</td></tr>
<tr><td align="center"><b>ONVIF</b></td><td align="center">6</td><td align="center">Camera management and authorization</td></tr>
<tr><td align="center"><b>MQTT</b></td><td align="center">6</td><td align="center">Broker security, topic access, pub/sub permissions</td></tr>
<tr><td align="center"><b>CoAP</b></td><td align="center">4</td><td align="center">Resource exposure and access control</td></tr>
<tr><td align="center"><b>SNMP</b></td><td align="center">4</td><td align="center">Management access and information exposure</td></tr>
<tr><td align="center"><b>SSH</b></td><td align="center">6</td><td align="center">Remote administration and authentication</td></tr>
<tr><td align="center"><b>Telnet</b></td><td align="center">2</td><td align="center">Insecure remote administration</td></tr>
<tr><td align="center"><b>UPnP / SSDP</b></td><td align="center">4</td><td align="center">Device discovery and control services</td></tr>
<tr><td align="center"><b>Post-Exploit</b></td><td align="center">7</td><td align="center">Credential replay, persistence, lateral movement</td></tr>
</tbody>
</table>

</details>

<details>
<summary><b>🔬 Firmware Analysis (28 modules) — click to expand</b></summary>

<table align="center">
<thead>
<tr>
<th align="center">🎯 Phase</th>
<th align="center">🛠️ Capabilities</th>
</tr>
</thead>
<tbody>
<tr><td align="center"><b>Extraction</b></td><td align="center">binwalk, unblob (30+ formats), SquashFS, CramFS, UBIFS, JFFS2, mount, carving</td></tr>
<tr><td align="center"><b>Analysis</b></td><td align="center">entropy, secret scanning, credential extraction, SBOM, CVE matching, unsafe functions</td></tr>
<tr><td align="center"><b>Emulation</b></td><td align="center">FirmAE, Firmadyne, config extraction, emulated scanning, web fuzzing, service fuzzing</td></tr>
<tr><td align="center"><b>Runtime</b></td><td align="center">GDB attach, Frida hooking, strace tracing</td></tr>
<tr><td align="center"><b>Exploitation</b></td><td align="center">ROP gadget discovery, shellcode generation, PoC generation</td></tr>
</tbody>
</table>

</details>

<details>
<summary><b>📡 Wireless & RF (44 modules) — click to expand</b></summary>

<table align="center">
<thead>
<tr>
<th align="center">📶 Subcategory</th>
<th align="center">📦 Modules</th>
<th align="center">🎯 Coverage</th>
</tr>
</thead>
<tbody>
<tr><td align="center"><b>BLE</b></td><td align="center">12</td><td align="center">Scan, GATT enumeration, characteristic R/W, pairing downgrade, sniffing, replay, cracking, jamming, spoofing</td></tr>
<tr><td align="center"><b>Zigbee</b></td><td align="center">8</td><td align="center">Network scan, sniffing, key extraction, frame replay, Touchlink abuse, ZCL injection, factory reset</td></tr>
<tr><td align="center"><b>Wi-Fi 802.11</b></td><td align="center">8</td><td align="center">Deauth, handshake capture, PMKID, WPS brute, PMKID+brute, KTO deauth, WPA3 downgrade, transition-mode twin</td></tr>
<tr><td align="center"><b>Additional RF</b></td><td align="center">4</td><td align="center">Z-Wave S0 downgrade, LoRaWAN join replay, Matter DoS, Thread border router attack</td></tr>
</tbody>
</table>

</details>

<details>
<summary><b>🔌 Hardware Interfaces (15 modules) — click to expand</b></summary>

<table align="center">
<thead>
<tr>
<th align="center">🔧 Interface</th>
<th align="center">🎯 Coverage</th>
</tr>
</thead>
<tbody>
<tr><td align="center"><b>UART</b></td><td align="center">Baud detection, boot log capture, interactive console</td></tr>
<tr><td align="center"><b>SPI</b></td><td align="center">Flash dump, integrity verification</td></tr>
<tr><td align="center"><b>JTAG</b></td><td align="center">Chain scan, memory dump</td></tr>
<tr><td align="center"><b>SWD</b></td><td align="center">ARM Cortex memory dump</td></tr>
<tr><td align="center"><b>I2C</b></td><td align="center">Bus scan, EEPROM dump</td></tr>
<tr><td align="center"><b>CAN</b></td><td align="center">Bus sniffing, frame injection</td></tr>
<tr><td align="center"><b>Glitching</b></td><td align="center">ChipWhisperer voltage/clock glitching, parameter sweep</td></tr>
<tr><td align="center"><b>Probe</b></td><td align="center">Automated hardware detection</td></tr>
</tbody>
</table>

</details>

<details>
<summary><b>☁️ Cloud, Mobile, Voice & Smart Home (19 modules) — click to expand</b></summary>

<table align="center">
<thead>
<tr>
<th align="center">🎯 Category</th>
<th align="center">📦 Modules</th>
<th align="center">💥 Coverage</th>
</tr>
</thead>
<tbody>
<tr><td align="center"><b>AWS / Azure IoT</b></td><td align="center">5</td><td align="center">Fleet enumeration, shadow injection for RCE, wildcard MQTT subscription</td></tr>
<tr><td align="center"><b>Amazon Alexa</b></td><td align="center">7</td><td align="center">OAuth CSRF, rogue account linking, break-tag chain, skill squatting, SkillVet bypass, DMC-Xplorer, Alexa vs. Alexa</td></tr>
<tr><td align="center"><b>Google Home</b></td><td align="center">5</td><td align="center">Rogue account link, DNS rebinding, prompt injection, promptware v2, voice traffic fingerprinting</td></tr>
<tr><td align="center"><b>Audio Injection</b></td><td align="center">2</td><td align="center">Ultrasonic (NUIT 1/2), laser (LightCommands, LCMA)</td></tr>
<tr><td align="center"><b>Mobile Companion Apps</b></td><td align="center">3</td><td align="center">APK/IPA static analysis, embedded firmware extraction, backend API IDOR</td></tr>
<tr><td align="center"><b>Smart Home</b></td><td align="center">4</td><td align="center">SmartThings (CVE-2025-2233), HomeKit Pair-Setup, Tuya CloudCutter, Xiaomi tokens</td></tr>
<tr><td align="center"><b>OTA / Provisioning</b></td><td align="center">2</td><td align="center">Firmware downgrade, signature stripping (CVE-2026-1122)</td></tr>
<tr><td align="center"><b>Medical IoT</b></td><td align="center">1</td><td align="center">DICOM C-FIND patient enumeration</td></tr>
<tr><td align="center"><b>Botnet</b></td><td align="center">1</td><td align="center">Mirai-style default credential bruteforce</td></tr>
</tbody>
</table>

</details>

> 💀 **Total: 154 modules. Every major IoT attack surface documented in security research.**

---

<a name="-blitz-vs-everything-else"></a>
## ⚔️ Blitz vs. Everything Else

<table align="center">
<thead>
<tr>
<th align="center">🎯 Capability</th>
<th align="center">🛠️ RouterSploit</th>
<th align="center">🏠 HomePwn</th>
<th align="center">💥 EXPLIoT</th>
<th align="center">🤖 IoTHackBot</th>
<th align="center">⚡ Blitz</th>
</tr>
</thead>
<tbody>
<tr><td align="center">🤖 Runs without a human at the keyboard</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">✅</td></tr>
<tr><td align="center">🔍 Finds new devices on its own</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">✅</td></tr>
<tr><td align="center">🧠 Decides what's worth testing</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">⚠️</td><td align="center">✅</td></tr>
<tr><td align="center">🔒 Stops unsafe actions before they run</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">⚠️</td><td align="center">✅</td></tr>
<tr><td align="center">💀 Proves impact (not just pass/fail)</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">✅</td></tr>
<tr><td align="center">🔄 Confirms a fix actually worked</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">✅</td></tr>
<tr><td align="center">📡 Protocol coverage</td><td align="center">Narrow</td><td align="center">Narrow</td><td align="center">Broad</td><td align="center">Narrow</td><td align="center"><b>154 modules</b></td></tr>
<tr><td align="center">🔬 Firmware analysis</td><td align="center">❌</td><td align="center">❌</td><td align="center">⚠️</td><td align="center">✅</td><td align="center">✅</td></tr>
<tr><td align="center">📶 Wireless (BLE/Zigbee/Wi-Fi)</td><td align="center">❌</td><td align="center">⚠️</td><td align="center">⚠️</td><td align="center">❌</td><td align="center">✅</td></tr>
<tr><td align="center">☁️ Cloud IoT (AWS/Azure)</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">✅</td></tr>
<tr><td align="center">🎤 Voice assistant attacks</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">✅</td></tr>
<tr><td align="center">🔌 Hardware (UART/SPI/JTAG/CAN)</td><td align="center">❌</td><td align="center">❌</td><td align="center">✅</td><td align="center">✅</td><td align="center">✅</td></tr>
<tr><td align="center">🧠 Local LLM (no cloud)</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">❌</td><td align="center">✅</td></tr>
</tbody>
</table>

---

<a name="-pricing--read-this-before-you-buy-anything-else"></a>
## 💰 Pricing — Read This Before You Buy Anything Else

<table align="center">
<thead>
<tr>
<th align="center">💼 Engagement Type</th>
<th align="center">💵 Cost</th>
<th align="center">📅 Billing</th>
<th align="center">📄 What You Get</th>
<th align="center">⏳ Valid For</th>
</tr>
</thead>
<tbody>
<tr><td align="center">🧑‍💻 <b>Standard IT Pentest</b></td><td align="center">$5k–$100k+</td><td align="center">Per engagement</td><td align="center">One report</td><td align="center">Until scope changes</td></tr>
<tr><td align="center">🔌 <b>IoT/OT Pentest</b></td><td align="center">$10k–$40k</td><td align="center">Per engagement</td><td align="center">One snapshot</td><td align="center">Until a device joins</td></tr>
<tr><td align="center">🎯 <b>Red-Team IoT Engagement</b></td><td align="center">$30k–$150k+</td><td align="center">$120–$350/hr</td><td align="center">Deep manual testing</td><td align="center">Until delivered</td></tr>
<tr><td align="center">⚡ <b>Blitz</b></td><td align="center"><b>$299 once</b></td><td align="center">Flat, one-time</td><td align="center">Continuous, every device</td><td align="center">Always running 🚀</td></tr>
</tbody>
</table>

> 🧮 **The honest math:** Even against the cheapest IoT pentest quote on the market ($10,000), Blitz costs **~97% less** — and unlike every other row, it doesn't stop working the day after you pay.

### 🧮 ROI Calculator

<table align="center">
<thead>
<tr>
<th align="center">📊 Your Situation</th>
<th align="center">💸 Cost Without Blitz</th>
<th align="center">⚡ Cost With Blitz</th>
<th align="center">💰 Savings</th>
</tr>
</thead>
<tbody>
<tr><td align="center">100 IoT devices, 1 pentest/year</td><td align="center">$25,000</td><td align="center">$299</td><td align="center"><b>$24,701</b></td></tr>
<tr><td align="center">500 IoT devices, 1 pentest/year</td><td align="center">$40,000</td><td align="center">$299</td><td align="center"><b>$39,701</b></td></tr>
<tr><td align="center">3-year pentest cycle (3 tests)</td><td align="center">$75,000</td><td align="center">$299</td><td align="center"><b>$74,701</b></td></tr>
<tr><td align="center"><b>Cost per device (100 devices)</b></td><td align="center">$250</td><td align="center"><b>$2.99</b></td><td align="center">—</td></tr>
</tbody>
</table>

### 🎯 Pricing Tiers

<table align="center">
<thead>
<tr>
<th align="center">🏷️ Tier</th>
<th align="center">💵 Price</th>
<th align="center">📅 Availability</th>
<th align="center">🎁 Scope</th>
</tr>
</thead>
<tbody>
<tr><td align="center">🔥 <b>Early Adopter</b></td><td align="center"><b>$299</b> <s>$499</s></td><td align="center">First 25 licenses — code <code>EARLYBIRD</code></td><td align="center">Perpetual commercial rights</td></tr>
<tr><td align="center">💼 <b>Standard Commercial</b></td><td align="center"><b>$499</b></td><td align="center">Standard list price</td><td align="center">Perpetual commercial rights</td></tr>
<tr><td align="center">🏢 <b>Enterprise</b></td><td align="center"><i>Contact us</i></td><td align="center">Custom</td><td align="center">+ SLA, custom modules, dedicated support</td></tr>
</tbody>
</table>

**[ 🚀 BUY EARLY ADOPTER LICENSE — $299 ](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)**

> ⚡ **Your devices are already connected. Already exposed. Already being watched — by someone.**
> **💀 $299 decides who finds the weakness first — you, or them.**

---

## 🛡️ Risk Reversal

We don't want you to guess. Here's what protects you. 🔒

<table align="center">
<thead>
<tr>
<th align="center">🛡️ Protection</th>
<th align="center">🎯 What It Means</th>
</tr>
</thead>
<tbody>
<tr><td align="center">✅ <b>30-day money-back guarantee</b></td><td align="center">If Blitz doesn't find at least one issue on a device you own, we refund you in full. <i>(Placeholder — only publish if you'll honor it.)</i></td></tr>
<tr><td align="center">🔒 <b>Safety gate built in</b></td><td align="center">Every action passes multi-condition authorization. Fuzzing is off by default. Destructive modules are opt-in per target.</td></tr>
<tr><td align="center">🛡️ <b>Air-gapped AI</b></td><td align="center">No telemetry, no cloud, no per-token fees. Your data never leaves your network.</td></tr>
<tr><td align="center">⚖️ <b>Perpetual commercial rights</b></td><td align="center">Unlimited internal assets and client engagements. No per-target, per-scan, or per-seat fees.</td></tr>
<tr><td align="center">♾️ <b>Lifetime updates</b></td><td align="center">New modules, new CVE profiles, engine upgrades — included forever.</td></tr>
</tbody>
</table>

---

## 🏢 For Investors

Blitz is built by **ApexPredator Security & Labs**. We're taking Blitz from a research project into a commercial platform. 🚀

<table align="center">
<thead>
<tr>
<th align="center">🎯 Dimension</th>
<th align="center">📊 Details</th>
</tr>
</thead>
<tbody>
<tr><td align="center">🌍 <b>Market</b></td><td align="center">IoT/OT security is one of the fastest-growing segments in cybersecurity. Regulatory tailwinds (EU CRA, NIS2, UK PSTI, US Cyber Trust Mark) are forcing every organization to assess their IoT/OT fleet.</td></tr>
<tr><td align="center">📈 <b>Traction</b></td><td align="center"><i>[Insert: licenses sold, revenue, GitHub stars, engagement count]</i></td></tr>
<tr><td align="center">🏰 <b>Moat</b></td><td align="center">Proprietary <code>ares</code> model, 154 in-house modules, reproducible training pipeline, multi-condition safety gate, closed-loop re-validation lifecycle.</td></tr>
<tr><td align="center">💰 <b>Business model</b></td><td align="center">$299 early / $499 standard / enterprise custom.</td></tr>
<tr><td align="center">🗺️ <b>Roadmap</b></td><td align="center">Matter 1.4, Thread 1.4, Wi-Fi 7, 5G RedCap, Ambient IoT, AI agent security, compliance mapping (CRA/NIS2/IEC 62443).</td></tr>
<tr><td align="center">👥 <b>Team</b></td><td align="center"><i>[Insert founder bios, CVE credits, talks, publications]</i></td></tr>
<tr><td align="center">🎯 <b>Ask</b></td><td align="center"><i>[Insert: raising $X, or open to acquisition]</i></td></tr>
</tbody>
</table>

**📩 Request our deck:** *[Insert investor contact email]*

---

<a name="-faq"></a>
## ❓ FAQ

<details>
<summary><b>🔒 Is Blitz safe to run against production devices?</b></summary>

Yes — every action Ares proposes passes through the Ares Bridge multi-condition authorization gate (authorized? in scope? capability allowed?) before it ever reaches a real device. Destructive modules (fuzzing, firmware modification, credential writes) are opt-in per target. Fuzzing is off by default. That gate is what makes continuous, unattended testing viable on live infrastructure.

</details>

<details>
<summary><b>⚖️ Am I authorized to test devices I don't own?</b></summary>

Only with explicit, written authorization from the asset owner — the same rule that governs any red-team or penetration-testing engagement. Blitz's scoping and authorization gate exist specifically to enforce that boundary. It is your responsibility to have authorization in place for every target before you scan it.

</details>

<details>
<summary><b>🛡️ Does any data leave my network?</b></summary>

No. The `ares` model runs locally via Ollama. Device context and reasoning stay on your infrastructure. Zero telemetry, zero per-token API costs, zero dependency on a cloud vendor's uptime. When you retrain the model, your training data also stays on your hardware.

</details>

<details>
<summary><b>🔌 Do I need special hardware?</b></summary>

For network, firmware, cloud, and mobile modules — no. For wireless modules (Wi-Fi, BLE, Zigbee) — any $10 USB adapter. For hardware modules (UART, SPI, JTAG) — any $20 CH341A/UART programmer. Total to cover every attack surface: roughly $50.

</details>

<details>
<summary><b>🧠 Can I retrain the model on my own engagements?</b></summary>

Yes. The full pipeline — SFT, GRPO, RFT, and curriculum — ships with Blitz. Retrain on your own session data using the same scripts, on an 8 GB GPU, in under 3 hours.

</details>

<details>
<summary><b>📦 What if a new IoT device class appears?</b></summary>

Add a device profile to `knowledge/device_profiles.yaml`. The framework picks it up on the next run. No model retraining required for basic coverage — retrain only if you want the model to reason about new routing decisions natively.

</details>

<details>
<summary><b>🔧 How does the model handle new modules I write?</b></summary>

Add the module's `manifest.toml` and `knowledge.toml`. Retrain with the provided scripts to include the new routing decision in the model. Or run with the base model and rely on the framework's fallback logic — the classifier still selects the correct category, and the framework routes to the nearest matching module.

</details>

<details>
<summary><b>💵 Will the $299 price come back?</b></summary>

No — the Early Adopter Cohort is capped at 25 licenses. Once those are claimed, the price returns to the $499 standard list price shown above.

</details>

<details>
<summary><b>🏢 Can I use one license across multiple client engagements?</b></summary>

Yes. The license grants perpetual commercial rights with unlimited internal asset coverage and external client penetration tests — no per-target, per-scan, or per-seat fees.

</details>

<details>
<summary><b>🚀 What happens after I buy?</b></summary>

Checkout, repository access, and delivery are automated through Polar.sh. No manual approval queue. Link your GitHub account, complete checkout, get instant repo access and a zip download.

</details>

<details>
<summary><b>💬 What support is included?</b></summary>

Lifetime access to new modules, CVE profiles, and engine updates. Questions before you buy or issues after: *[Insert support email, Discord, or docs site]*.

</details>

---

## 🛡️ Authorized Use Only

Blitz executes real attacks against real devices — credential attempts, protocol abuse, stream access, exploit chaining. Run it **only** against infrastructure you own, or infrastructure you have explicit, written authorization to test, under the same rules that govern any penetration test or red-team engagement.

The authorization gate in Ares Bridge enforces scope at the tool level. It does not replace, and is not a substitute for, having written authorization in place before you scan a target. **ApexPredator Security & Labs** provides Blitz as a testing platform; responsibility for lawful, authorized use rests with the licensee.

---

<a name="️-installation"></a>
## ⚙️ Installation

### 🖥️ System Requirements

<table align="center">
<thead>
<tr>
<th align="center">🔧 Requirement</th>
<th align="center">🟡 Minimum</th>
<th align="center">🟢 Recommended</th>
</tr>
</thead>
<tbody>
<tr><td align="center"><b>OS</b></td><td align="center">Linux / macOS / Windows (WSL2)</td><td align="center">Ubuntu 22.04 LTS</td></tr>
<tr><td align="center"><b>CPU</b></td><td align="center">4 cores</td><td align="center">8 cores</td></tr>
<tr><td align="center"><b>RAM</b></td><td align="center">8 GB</td><td align="center">16 GB</td></tr>
<tr><td align="center"><b>Disk</b></td><td align="center">20 GB free</td><td align="center">40 GB free (SSD)</td></tr>
<tr><td align="center"><b>Docker Engine</b></td><td align="center">24.x</td><td align="center">Latest stable</td></tr>
<tr><td align="center"><b>Docker Compose</b></td><td align="center">v2</td><td align="center">v2</td></tr>
<tr><td align="center"><b>Python</b></td><td align="center">3.11+</td><td align="center">3.11+</td></tr>
<tr><td align="center"><b>GPU (optional)</b></td><td align="center">6 GB VRAM</td><td align="center">8 GB VRAM — only for retraining</td></tr>
</tbody>
</table>

### ⚡ Quick Start (3 commands)

```bash
# 1️⃣ Install
unzip blitz-*.zip && cd blitz && chmod +x blitz-setup.sh && ./blitz-setup.sh

# 2️⃣ Scan
blitz scan 192.168.1.0/24

# 3️⃣ Report
blitz report --session latest
```

### 🐳 Custom Install (Docker Compose)

```bash
docker compose build --no-cache
docker compose up -d
docker compose ps
docker compose logs -f
```

If you hit errors: `docker compose down -v && docker compose build --no-cache && docker compose up -d`.

---

## 🏴 About ApexPredator Security & Labs

Blitz is built and maintained by **ApexPredator Security & Labs** — the research group behind the Ares AI reasoning engine and the closed-loop assessment methodology Blitz runs on. Every module, protocol integration, and the fine-tuned `ares` model was built in-house specifically for IoT/OT offensive testing. 🎯

*[Placeholder: add founder bios, years active, prior research, CVE credits, conference talks. Buyers in this category trust people, not just products. A named point of contact goes a long way.]*

---

## 💬 Support & Updates

<table align="center">
<thead>
<tr>
<th align="center">🎯 Resource</th>
<th align="center">🔗 Link</th>
</tr>
</thead>
<tbody>
<tr><td align="center">♾️ <b>Lifetime updates</b></td><td align="center">New protocol modules, CVE detection profiles, and engine enhancements included with every license.</td></tr>
<tr><td align="center">💬 <b>Support</b></td><td align="center"><i>[Insert support email / Discord / docs URL]</i></td></tr>
<tr><td align="center">🗺️ <b>Public roadmap</b></td><td align="center"><i>[Insert link]</i></td></tr>
<tr><td align="center">💡 <b>Feature requests</b></td><td align="center"><i>[Insert link or GitHub Discussions]</i></td></tr>
</tbody>
</table>

---

<div align="center">

**⚡ Blitz — Autonomous IoT/OT Red Teaming & Continuous Assessment. ⚡**

*Your devices are already connected. Already exposed. Already being watched — by someone.* 💀

*💵 $299 decides who finds the weakness first.*

**[ 🚀 BUY EARLY ADOPTER LICENSE — $299 ](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)**

*🔥 First 25 licenses only • Code `EARLYBIRD` • Perpetual commercial rights • Lifetime updates*

</div>
