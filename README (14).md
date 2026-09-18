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

| 🎯 Deliverable | 📝 What It Includes | 💰 Value |
| :---: | :---: | :---: |
| ⚔️ **154 attack modules** | Across 28 categories: firmware, wireless, cloud, mobile, voice assistants, hardware interfaces | Included |
| 🧠 **Fine-tuned local AI** | The `ares` 1.7B model — runs on Ollama, offline, on your own hardware | Included |
| 🔬 **Full training pipeline** | SFT + GRPO + RFT + curriculum — retrain on your own data with an 8 GB GPU | Included |
| 🔄 **12-stage lifecycle** | Discovery → Fingerprint → Plan → Authorize → Execute → Prove → Remediate → Re-validate | Included |
| 🔒 **Multi-condition safety gate** | Authorized? In scope? Capability allowed? Nothing runs without clearance | Included |
| 📊 **Evidence-backed findings** | Every result labeled *attempted* or *proven*. No speculation, ever. | Included |
| ✅ **Automatic re-validation** | After a patch ships, Blitz re-checks automatically — fix attestation, not a guess | Included |
| 🛡️ **Air-gapped by default** | Zero telemetry. Zero cloud. Your data never leaves your network. | Included |
| ⚙️ **`blitz-setup.sh` installer** | One command to deploy the full stack | Included |
| ♾️ **Lifetime updates** | New modules, new CVE profiles, engine upgrades — included forever | Included |

---

## 🚨 The Problem

Security teams spent 20 years getting good at defending laptops and servers. Attackers noticed, and moved somewhere easier: **IoT and OT**. 💀

The cameras, sensors, controllers, and gateways quietly running your buildings, factories, and hospitals are on the same network as everything you protect — with almost none of the same rigor.

| 🕳️ The Gap | 💥 What It Looks Like in Practice | 🎯 Who It Hurts |
| :---: | :---: | :---: |
| 🕵️ **Invisible inventory** | You don't know what IoT devices you have. | Every team |
| 🔑 **Default passwords** | `admin:admin`, unchanged, for the life of the device. | Cameras, routers |
| 🚪 **Unauthenticated services** | Video streams, control panels, management UIs built to "just work." | Cameras, NVRs |
| 📡 **Plaintext traffic** | Credentials and keys visible on the wire. | MQTT, CoAP |
| 🧱 **"Segmented" is a belief** | Flat networks turn one device into a path to everything. | Enterprise |
| 🛠️ **Nothing gets patched** | No update lifecycle. Known weaknesses persist for years. | All IoT |
| 🙈 **Detection blind spots** | Your IT security tooling cannot see IoT/OT compromise. | SOC teams |
| ✅❌ **"Fixed" is assumed** | Fixes rarely get re-verified. Resolved risk often isn't. | Compliance |

> 🚨 **This is the default state of every IoT/OT network — including yours.** The devices you trust most are the ones you've tested least. 🎯

---

## 🛡️ The Solution

**Blitz** is a fully autonomous IoT/OT red teaming system. It discovers, plans, attacks, proves, and re-validates — continuously, safely, entirely on-prem.

| ✨ Capability | 🎯 What It Does | 🏆 Why It Matters |
| :---: | :---: | :---: |
| 🔍 **Profiles each device first** | Learns what it is, what it speaks, what it exposes — then plans an attack built for that device. | No wasted noise |
| 🔒 **Authorization gate** | Every action passes multi-condition checks before execution. Safe to run continuously on live infrastructure. | Legal + safe |
| 📊 **Evidence-backed results** | Labeled *attempted* or *proven*. Fixes are automatically re-validated. | No false positives |
| 🧠 **Ares plans the assessment** | No human at the keyboard required for every test. | True autonomy |
| 🖥️ **Runs 100% on-prem** | The `ares` model runs locally via Ollama. No cloud. No per-token fees. No telemetry. | Total privacy |

**Traditional IoT scanners stop at:**

> 🥱 "Port 554 is open."

**Blitz asks:**

> 🔥 **"What does that service expose, how does it behave, what protects it, and can the weakness be safely demonstrated?"**

---

<a name="-proof"></a>
## 📊 Proof

### 🏆 Benchmarks *(Placeholder — fill with real results)*

| 📊 Metric | ⚡ **Blitz** | 🥱 Traditional Scanner | 🐢 Manual Pentest | 🎯 Winner |
| :---: | :---: | :---: | :---: | :---: |
| ⏱️ Time to first finding | **47 sec** | 15 min | 2 days | ⚡ Blitz |
| 📡 Devices discovered / hour | **120** | 40 | 10 | ⚡ Blitz |
| 🎯 False positive rate | **<5%** | ~30% | ~10% | ⚡ Blitz |
| 🔄 Re-validation after patch | **Automatic** | Manual | Manual | ⚡ Blitz |
| 🤖 Runs unattended | **Yes** | No | No | ⚡ Blitz |
| 💰 Cost per year | **$299 once** | $10k+ | $25k+ | ⚡ Blitz |

> 📖 Methodology and lab setup documented in `/docs/benchmarks`. *(Replace with your actual numbers before publishing.)*

### 🔬 Lab-Validated Devices *(Placeholder — fill with real list)*

| 🏷️ Category | 📦 Devices Tested | 📡 Protocols Covered |
| :---: | :---: | :---: |
| 📹 **IP Cameras** | Hikvision DS-2CD series, Dahua NVR, Reolink, Amcrest | ONVIF, RTSP, HTTP |
| 💡 **Smart Home** | Philips Hue Bridge, Shelly Plug S, Shelly 1, Tuya devices | MQTT, HTTP, CoAP |
| 🤖 **Single-Board Computers** | Raspberry Pi 4, Pi Zero 2W, ESP32, ESP8266 | SSH, HTTP, BLE |
| 🔊 **Voice Assistants** | Amazon Echo (Gen 3/4), Google Nest Hub | Alexa, Google Home |
| 🌐 **Network Gear** | TP-Link, Netgear, MikroTik routers | UPnP, SNMP, HTTP |
| 🏭 **Industrial** | Modbus RTU/TCP devices, BACnet controllers | Modbus, BACnet |

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

| 👤 Role | 💬 Quote | 🏢 Source |
| :---: | :---: | :---: |
| 🏢 **CISO** | *"Blitz found issues our $25k pentest missed."* | [Company] |
| 🛠️ **Red Team Lead** | *"The safety gate is the reason we can run it continuously."* | [Company] |
| 🔬 **Security Researcher** | *"Retraining on our own engagement data took 3 hours."* | [Institution] |

*(Replace with real quotes. Offer early adopters a discount or free license in exchange.)*

---

<a name="-who-blitz-is-for"></a>
## 👥 Who Blitz Is For

| 🎭 Persona | 🎯 Why They Choose Blitz | 💰 What It Replaces | 🚀 Start Here |
| :---: | :---: | :---: | :---: |
| 🔬 **Security Researchers** | Study how LLMs perform on real IoT attack planning. Full pipeline ships with Blitz. | Manual tool chains | [🧠 Ares AI](#-ares-ai--the-intelligence-layer) |
| 🏢 **Enterprise Security Teams** | Replace $25,000 engagements with continuous automated assessment. Evidence-backed. Re-validated. On-prem. | Annual pentests | [💰 Why Blitz](#-pricing--read-this-before-you-buy-anything-else) |
| 🛠️ **Red Teams & Consultants** | 154 modules across firmware, wireless, cloud, mobile, voice assistants. No new hardware for network testing. | Fragmented scripts | [⚔️ Attack Surface](#-attack-surface--154-modules-across-28-categories) |
| 🎯 **Lab & CTF Enthusiasts** | Deploy against QEMU device farms or your own home lab. Every module documents its preconditions. | Manual recon + exploits | [⚙️ Install](#️-installation) |

---

## 🧠 How Blitz Works

Blitz is a closed-loop autonomous system with five core components.

| 🧩 Component | 🎯 Role | 🔌 Port |
| :---: | :---: | :---: |
| 🎛️ **Operator Console** | Human control plane. Launch assessments, approve/deny actions, watch live progress. | UI |
| 🧠 **Ares Agent** | AI orchestration layer. Profiles devices, plans assessments, picks the next module. | `:9010` |
| 🔒 **Ares Bridge** | Capability gateway. Every action is checked against multi-condition rules before execution. | `:8089` |
| 🖥️ **Ollama** | Local model runtime. Runs the `ares` model entirely on-prem. | `:11435` |
| ⚙️ **Blitz Core** | Execution engine. Runs approved modules, collects evidence, drives the 12-stage lifecycle. | `:8088` |
| 🗄️ **Persistent State** | Durable audit trail. Devices, jobs, findings, incidents — everything, forever. | DB |
| 📡 **Live Event Stream** | Real-time WebSocket feed to the operator GUI. Watch it happen live. | `:8088` |

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

| 🎯 Stage | 🛠️ Method | 📊 Dataset | 🏆 Result |
| :---: | :---: | :---: | :---: |
| **1️⃣ SFT** | QLoRA on curated examples | 638 examples | ~85% correct routing |
| **2️⃣ GRPO** | Rule-based reward alignment | Generated candidates | ~98% JSON validity, ~92% routing, 100% safety refusal |
| **3️⃣ RFT** | Self-improvement loop | 638 → ~1,000 examples | Higher data quality, no new human labels |
| **4️⃣ Curriculum** | Easy → hard sorting | Reordered dataset | Smoother training, +1–3% final accuracy |

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

| 🔧 Feature | 🎯 What It Enables | 🏆 Benefit |
| :---: | :---: | :---: |
| 🔄 **Hot-swappable brain** | Point Ares at DeepSeek-Coder, Llama, Mistral, or your own endpoint through the Ares Bridge — no code changes. | Model freedom |
| 🔬 **Retrain on your own data** | Every engagement becomes training data. The pipeline is included. | Gets smarter over time |
| 🛡️ **Air-gapped by default** | Zero telemetry. Zero cloud. Your data never leaves your network. | Enterprise-ready |

---

<a name="-attack-surface--154-modules-across-28-categories"></a>
## 🔬 Attack Surface — 154 Modules Across 28 Categories

Blitz covers **every layer** where IoT devices have been shown to be exploitable in the wild.

<details>
<summary><b>🌐 Network Protocols (48 modules) — click to expand</b></summary>

| 🔌 Protocol | 📦 Modules | 🎯 What It Tests | 🏆 Real-Time Validation |
| :---: | :---: | :---: | :---: |
| **HTTP / HTTPS** | 6 | Web login, admin pages, access control, input flaws | Live auth + path fuzzing |
| **RTSP** | 5 | Video-stream exposure and authentication | Stream enumeration |
| **ONVIF** | 6 | Camera management and authorization | Device + profile enum |
| **MQTT** | 6 | Broker security, topic access, pub/sub permissions | Wildcard subscribe |
| **CoAP** | 4 | Resource exposure and access control | Resource probing |
| **SNMP** | 4 | Management access and information exposure | Community string test |
| **SSH** | 6 | Remote administration and authentication | Algorithm audit |
| **Telnet** | 2 | Insecure remote administration | Credential test |
| **UPnP / SSDP** | 4 | Device discovery and control services | SOAP injection |
| **Post-Exploit** | 7 | Credential replay, persistence, lateral movement | Chain validation |

</details>

<details>
<summary><b>🔬 Firmware Analysis (28 modules) — click to expand</b></summary>

| 🎯 Phase | 🛠️ Capabilities | 📦 Modules |
| :---: | :---: | :---: |
| **Extraction** | binwalk, unblob (30+ formats), SquashFS, CramFS, UBIFS, JFFS2, mount, carving | 8 |
| **Analysis** | entropy, secret scanning, credential extraction, SBOM, CVE matching, unsafe functions | 7 |
| **Emulation** | FirmAE, Firmadyne, config extraction, emulated scanning, web fuzzing, service fuzzing | 6 |
| **Runtime** | GDB attach, Frida hooking, strace tracing | 3 |
| **Exploitation** | ROP gadget discovery, shellcode generation, PoC generation | 4 |

</details>

<details>
<summary><b>📡 Wireless & RF (44 modules) — click to expand</b></summary>

| 📶 Subcategory | 📦 Modules | 🎯 Coverage | 🏆 Highlight |
| :---: | :---: | :---: | :---: |
| **BLE** | 12 | Scan, GATT enum, characteristic R/W, pairing downgrade, sniffing, replay, cracking, jamming, spoofing | GATT abuse |
| **Zigbee** | 8 | Network scan, sniffing, key extraction, frame replay, Touchlink abuse, ZCL injection, factory reset | Key extraction |
| **Wi-Fi 802.11** | 8 | Deauth, handshake capture, PMKID, WPS brute, KTO deauth, WPA3 downgrade, transition-mode twin | WPA3 attacks |
| **Additional RF** | 4 | Z-Wave S0 downgrade, LoRaWAN join replay, Matter DoS, Thread border router attack | Matter + Thread |

</details>

<details>
<summary><b>🔌 Hardware Interfaces (15 modules) — click to expand</b></summary>

| 🔧 Interface | 🎯 Coverage | 📦 Modules |
| :---: | :---: | :---: |
| **UART** | Baud detection, boot log capture, interactive console | 3 |
| **SPI** | Flash dump, integrity verification | 2 |
| **JTAG** | Chain scan, memory dump | 2 |
| **SWD** | ARM Cortex memory dump | 1 |
| **I2C** | Bus scan, EEPROM dump | 2 |
| **CAN** | Bus sniffing, frame injection | 2 |
| **Glitching** | ChipWhisperer voltage/clock glitching, parameter sweep | 2 |
| **Probe** | Automated hardware detection | 1 |

</details>

<details>
<summary><b>☁️ Cloud, Mobile, Voice & Smart Home (19 modules) — click to expand</b></summary>

| 🎯 Category | 📦 Modules | 💥 Coverage | 🏆 Highlight |
| :---: | :---: | :---: | :---: |
| **AWS / Azure IoT** | 5 | Fleet enumeration, shadow injection for RCE, wildcard MQTT subscription | Fleet-wide RCE |
| **Amazon Alexa** | 7 | OAuth CSRF, rogue account linking, break-tag chain, skill squatting, SkillVet bypass, DMC-Xplorer, Alexa vs. Alexa | SkillVet bypass |
| **Google Home** | 5 | Rogue account link, DNS rebinding, prompt injection, promptware v2, voice traffic fingerprinting | Promptware |
| **Audio Injection** | 2 | Ultrasonic (NUIT 1/2), laser (LightCommands, LCMA) | Laser injection |
| **Mobile Companion Apps** | 3 | APK/IPA static analysis, embedded firmware extraction, backend API IDOR | Firmware in apps |
| **Smart Home** | 4 | SmartThings (CVE-2025-2233), HomeKit Pair-Setup, Tuya CloudCutter, Xiaomi tokens | Tuya CloudCutter |
| **OTA / Provisioning** | 2 | Firmware downgrade, signature stripping (CVE-2026-1122) | Sig stripping |
| **Medical IoT** | 1 | DICOM C-FIND patient enumeration | Patient data |
| **Botnet** | 1 | Mirai-style default credential bruteforce | Botnet sim |

</details>

> 💀 **Total: 154 modules. Every major IoT attack surface documented in security research.**

---

<a name="-blitz-vs-everything-else"></a>
## ⚔️ Blitz vs. Everything Else

| 🎯 Capability | 🛠️ RouterSploit | 🏠 HomePwn | 💥 EXPLIoT | 🤖 IoTHackBot | ⚡ **Blitz** |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 🤖 Runs without a human at the keyboard | ❌ | ❌ | ❌ | ❌ | ✅ |
| 🔍 Finds new devices on its own | ❌ | ❌ | ❌ | ❌ | ✅ |
| 🧠 Decides what's worth testing | ❌ | ❌ | ❌ | ⚠️ | ✅ |
| 🔒 Stops unsafe actions before they run | ❌ | ❌ | ❌ | ⚠️ | ✅ |
| 💀 Proves impact (not just pass/fail) | ❌ | ❌ | ❌ | ❌ | ✅ |
| 🔄 Confirms a fix actually worked | ❌ | ❌ | ❌ | ❌ | ✅ |
| 📡 Protocol coverage | Narrow | Narrow | Broad | Narrow | **154 modules** |
| 🔬 Firmware analysis | ❌ | ❌ | ⚠️ | ✅ | ✅ |
| 📶 Wireless (BLE/Zigbee/Wi-Fi) | ❌ | ⚠️ | ⚠️ | ❌ | ✅ |
| ☁️ Cloud IoT (AWS/Azure) | ❌ | ❌ | ❌ | ❌ | ✅ |
| 🎤 Voice assistant attacks | ❌ | ❌ | ❌ | ❌ | ✅ |
| 🔌 Hardware (UART/SPI/JTAG/CAN) | ❌ | ❌ | ✅ | ✅ | ✅ |
| 🧠 Local LLM (no cloud) | ❌ | ❌ | ❌ | ❌ | ✅ |

---

<a name="-pricing--read-this-before-you-buy-anything-else"></a>
## 💰 Pricing — Read This Before You Buy Anything Else

| 💼 Engagement Type | 💵 Cost | 📅 Billing | 📄 What You Get | ⏳ Valid For |
| :---: | :---: | :---: | :---: | :---: |
| 🧑‍💻 **Standard IT Pentest** | $5k–$100k+ | Per engagement | One report | Until scope changes |
| 🔌 **IoT/OT Pentest** | $10k–$40k | Per engagement | One snapshot | Until a device joins |
| 🎯 **Red-Team IoT Engagement** | $30k–$150k+ | $120–$350/hr | Deep manual testing | Until delivered |
| ⚡ **Blitz** | **$299 once** | Flat, one-time | Continuous, every device | Always running 🚀 |

> 🧮 **The honest math:** Even against the cheapest IoT pentest quote on the market ($10,000), Blitz costs **~97% less** — and unlike every other row, it doesn't stop working the day after you pay.

### 🧮 ROI Calculator

| 📊 Your Situation | 💸 Cost Without Blitz | ⚡ Cost With Blitz | 💰 Savings | 📉 Reduction |
| :---: | :---: | :---: | :---: | :---: |
| 100 IoT devices, 1 pentest/year | $25,000 | $299 | **$24,701** | 98.8% |
| 500 IoT devices, 1 pentest/year | $40,000 | $299 | **$39,701** | 99.3% |
| 3-year pentest cycle (3 tests) | $75,000 | $299 | **$74,701** | 99.6% |
| **Cost per device (100 devices)** | $250 | **$2.99** | — | — |

### 🎯 Pricing Tiers

| 🏷️ Tier | 💵 Price | 📅 Availability | 🎁 Scope | 🎯 Best For |
| :---: | :---: | :---: | :---: | :---: |
| 🔥 **Early Adopter** | **$299** ~~$499~~ | First 25 licenses — code `EARLYBIRD` | Perpetual commercial rights | Solo researchers, small teams |
| 💼 **Standard Commercial** | **$499** | Standard list price | Perpetual commercial rights | Consultancies, red teams |
| 🏢 **Enterprise** | *Contact us* | Custom | + SLA, custom modules, dedicated support | Large orgs, regulated industries |

**[ 🚀 BUY EARLY ADOPTER LICENSE — $299 ](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)**

> ⚡ **Your devices are already connected. Already exposed. Already being watched — by someone.**
> **💀 $299 decides who finds the weakness first — you, or them.**

---

## 🛡️ Risk Reversal

We don't want you to guess. Here's what protects you. 🔒

| 🛡️ Protection | 🎯 What It Means | 🏆 Buyer Benefit |
| :---: | :---: | :---: |
| ✅ **30-day money-back guarantee** | If Blitz doesn't find at least one issue on a device you own, we refund you in full. | Zero-risk purchase |
| 🔒 **Safety gate built in** | Every action passes multi-condition authorization. Fuzzing is off by default. Destructive modules are opt-in per target. | No bricked devices |
| 🛡️ **Air-gapped AI** | No telemetry, no cloud, no per-token fees. Your data never leaves your network. | Full privacy |
| ⚖️ **Perpetual commercial rights** | Unlimited internal assets and client engagements. No per-target, per-scan, or per-seat fees. | No surprise costs |
| ♾️ **Lifetime updates** | New modules, new CVE profiles, engine upgrades — included forever. | Never outdated |

---

## 🏢 For Investors

Blitz is built by **ApexPredator Security & Labs**. We're taking Blitz from a research project into a commercial platform. 🚀

| 🎯 Dimension | 📊 Details | 🎁 Value |
| :---: | :---: | :---: |
| 🌍 **Market** | IoT/OT security is one of the fastest-growing segments in cybersecurity. Regulatory tailwinds (EU CRA, NIS2, UK PSTI, US Cyber Trust Mark) are forcing every organization to assess their IoT/OT fleet. | Massive TAM |
| 📈 **Traction** | *[Insert: licenses sold, revenue, GitHub stars, engagement count]* | Proof of demand |
| 🏰 **Moat** | Proprietary `ares` model, 154 in-house modules, reproducible training pipeline, multi-condition safety gate, closed-loop re-validation lifecycle. | Hard to clone |
| 💰 **Business model** | $299 early / $499 standard / enterprise custom. | Clean unit economics |
| 🗺️ **Roadmap** | Matter 1.4, Thread 1.4, Wi-Fi 7, 5G RedCap, Ambient IoT, AI agent security, compliance mapping (CRA/NIS2/IEC 62443). | Clear expansion |
| 👥 **Team** | *[Insert founder bios, CVE credits, talks, publications]* | Credible founders |
| 🎯 **Ask** | *[Insert: raising $X, or open to acquisition]* | Clear ask |

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

| 🔧 Requirement | 🟡 Minimum | 🟢 Recommended | 🎯 Why It Matters |
| :---: | :---: | :---: | :---: |
| **OS** | Linux / macOS / Windows (WSL2) | Ubuntu 22.04 LTS | Stable Docker networking |
| **CPU** | 4 cores | 8 cores | Parallel module execution |
| **RAM** | 8 GB | 16 GB | Local AI inference + state |
| **Disk** | 20 GB free | 40 GB free (SSD) | Model + audit history |
| **Docker Engine** | 24.x | Latest stable | Container runtime |
| **Docker Compose** | v2 | v2 | Multi-service orchestration |
| **Python** | 3.11+ | 3.11+ | Blitz Core compatibility |
| **GPU (optional)** | 6 GB VRAM | 8 GB VRAM | Only for retraining |

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

| 🎯 Resource | 📝 Description | 🔗 Link |
| :---: | :---: | :---: |
| ♾️ **Lifetime updates** | New protocol modules, CVE detection profiles, and engine enhancements included with every license. | Included |
| 💬 **Support** | Direct line to the team for purchase questions and post-purchase issues. | *[Insert email / Discord]* |
| 🗺️ **Public roadmap** | See what's shipping next: Matter, Thread, Wi-Fi 7, compliance mapping. | *[Insert link]* |
| 💡 **Feature requests** | Request new modules, integrations, or capabilities. | *[Insert link]* |

---

<div align="center">

**⚡ Blitz — Autonomous IoT/OT Red Teaming & Continuous Assessment. ⚡**

*Your devices are already connected. Already exposed. Already being watched — by someone.* 💀

*💵 $299 decides who finds the weakness first.*

**[ 🚀 BUY EARLY ADOPTER LICENSE — $299 ](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)**

*🔥 First 25 licenses only • Code `EARLYBIRD` • Perpetual commercial rights • Lifetime updates*

</div>
