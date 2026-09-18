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

> 📹 **[Watch the 60-second demo →](#)** — full run from scan to proof. *(Replace with your Loom or YouTube link.)*

Every other IoT tool's README says "autonomous." **Blitz shows you what that looks like.** 🔥

---

<a name="-what-you-get-for-299"></a>
## 🎁 What You Get For $299

**One-time purchase. Perpetual commercial rights. Zero per-token fees. Zero per-device fees. Zero subscriptions.** 💯

| 🎯 Deliverable | 📝 What It Includes | 🏆 Why It Matters | 💰 Value |
| :---: | :---: | :---: | :---: |
| ⚔️ **154 attack modules** | Across 28 categories: firmware, wireless, cloud, mobile, voice, hardware | Widest IoT coverage in any tool | Included |
| 🧠 **Fine-tuned local AI** | The `ares` 1.7B model runs on Ollama, offline, on your hardware | No cloud, no leaks | Included |
| 🔬 **Full training pipeline** | SFT + GRPO + RFT + curriculum — retrain on your own data | Gets smarter over time | Included |
| 🔄 **12-stage lifecycle** | Discovery → Fingerprint → Plan → Authorize → Execute → Prove → Remediate → Re-validate | Full autonomy loop | Included |
| 🔒 **Multi-condition safety gate** | Authorized? In scope? Capability allowed? | Legal + safe | Included |
| 📊 **Evidence-backed findings** | Every result labeled *attempted* or *proven* | Zero false positives | Included |
| ✅ **Automatic re-validation** | Re-checks after patch, gives fix attestation | Proves remediation | Included |
| 🛡️ **Air-gapped by default** | Zero telemetry, zero cloud, zero per-token fees | Enterprise-ready | Included |
| ⚙️ **`blitz-setup.sh` installer** | One command deploys the full stack | Fast onboarding | Included |
| ♾️ **Lifetime updates** | New modules, CVE profiles, engine upgrades | Never outdated | Included |

---

## 🚨 The Problem

Security teams spent 20 years getting good at defending laptops and servers. Attackers noticed, and moved somewhere easier: **IoT and OT**. 💀

The cameras, sensors, controllers, and gateways quietly running your buildings, factories, and hospitals are on the same network as everything you protect — with almost none of the same rigor.

| 🕳️ The Gap | 💥 What It Looks Like in Practice | 🎯 Who It Hurts | 📉 Cost of Ignoring |
| :---: | :---: | :---: | :---: |
| 🕵️ **Invisible inventory** | You don't know what IoT devices you have | Every team | Unknown attack surface |
| 🔑 **Default passwords** | `admin:admin`, unchanged, for the life of the device | Cameras, routers | Trivial compromise |
| 🚪 **Unauthenticated services** | Video streams, control panels, management UIs built to "just work" | Cameras, NVRs | Data exposure |
| 📡 **Plaintext traffic** | Credentials and keys visible on the wire | MQTT, CoAP | Credential theft |
| 🧱 **"Segmented" is a belief** | Flat networks turn one device into a path to everything | Enterprise | Lateral movement |
| 🛠️ **Nothing gets patched** | No update lifecycle. Known weaknesses persist for years | All IoT | Persistent risk |
| 🙈 **Detection blind spots** | IT security tooling cannot see IoT/OT compromise | SOC teams | Silent breach |
| ✅❌ **"Fixed" is assumed** | Fixes rarely get re-verified. Resolved risk often isn't | Compliance | False confidence |

> 🚨 **This is the default state of every IoT/OT network — including yours.** The devices you trust most are the ones you've tested least. 🎯

---

## 🛡️ The Solution

**Blitz** is a fully autonomous IoT/OT red teaming system. It discovers, plans, attacks, proves, and re-validates — continuously, safely, entirely on-prem.

| ✨ Capability | 🎯 What It Does | 🏆 Why It Matters | 🎁 Buyer Benefit |
| :---: | :---: | :---: | :---: |
| 🔍 **Profiles each device first** | Learns what it is, what it speaks, what it exposes | No wasted noise | Faster results |
| 🔒 **Authorization gate** | Multi-condition checks before every action | Legal + safe | Run continuously |
| 📊 **Evidence-backed results** | Labeled *attempted* or *proven*, re-validated | No speculation | Trust the findings |
| 🧠 **Ares plans the assessment** | No human at the keyboard required | True autonomy | Scale testing |
| 🖥️ **Runs 100% on-prem** | Local `ares` model, Ollama, zero cloud | Total privacy | Enterprise-ready |

**Traditional IoT scanners stop at:**

> 🥱 "Port 554 is open."

**Blitz asks:**

> 🔥 **"What does that service expose, how does it behave, what protects it, and can the weakness be safely demonstrated?"**

---

<a name="-proof"></a>
## 📊 Proof

### 🏆 Benchmarks *(Replace placeholder with your real numbers)*

| 📊 Metric | ⚡ **Blitz** | 🥱 Traditional Scanner | 🐢 Manual Pentest | 🎯 Winner | 📉 Gap |
| :---: | :---: | :---: | :---: | :---: | :---: |
| ⏱️ Time to first finding | **47 sec** | 15 min | 2 days | ⚡ Blitz | ~19× faster |
| 📡 Devices discovered / hour | **120** | 40 | 10 | ⚡ Blitz | 3× faster |
| 🎯 False positive rate | **<5%** | ~30% | ~10% | ⚡ Blitz | 6× cleaner |
| 🔄 Re-validation after patch | **Automatic** | Manual | Manual | ⚡ Blitz | Zero touch |
| 🤖 Runs unattended | **Yes** | No | No | ⚡ Blitz | True autonomy |
| 💰 Cost per year | **$299 once** | $10k+ | $25k+ | ⚡ Blitz | ~97% cheaper |

### 🔬 Lab-Validated Devices *(Replace with your real list)*

| 🏷️ Category | 📦 Devices Tested | 📡 Protocols Covered | 🎯 Attack Modules Used |
| :---: | :---: | :---: | :---: |
| 📹 **IP Cameras** | Hikvision DS-2CD, Dahua NVR, Reolink, Amcrest | ONVIF, RTSP, HTTP | 17 |
| 💡 **Smart Home** | Philips Hue Bridge, Shelly Plug S, Shelly 1, Tuya | MQTT, HTTP, CoAP | 12 |
| 🤖 **Single-Board Computers** | Raspberry Pi 4, Pi Zero 2W, ESP32, ESP8266 | SSH, HTTP, BLE | 14 |
| 🔊 **Voice Assistants** | Amazon Echo (Gen 3/4), Google Nest Hub | Alexa, Google Home | 12 |
| 🌐 **Network Gear** | TP-Link, Netgear, MikroTik routers | UPnP, SNMP, HTTP | 15 |
| 🏭 **Industrial** | Modbus RTU/TCP devices, BACnet controllers | Modbus, BACnet | 9 |

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

### 💬 What Early Adopters Are Saying *(Replace with real quotes)*

| 👤 Role | 💬 Quote | 🏢 Source | ⭐ Rating |
| :---: | :---: | :---: | :---: |
| 🏢 **CISO** | *"Blitz found issues our $25k pentest missed."* | [Company] | ⭐⭐⭐⭐⭐ |
| 🛠️ **Red Team Lead** | *"The safety gate is why we can run it continuously."* | [Company] | ⭐⭐⭐⭐⭐ |
| 🔬 **Security Researcher** | *"Retraining on our own data took 3 hours."* | [Institution] | ⭐⭐⭐⭐⭐ |

---

<a name="-who-blitz-is-for"></a>
## 👥 Who Blitz Is For

| 🎭 Persona | 🎯 Why They Choose Blitz | 💰 What It Replaces | 📈 Key Benefit | 🚀 Start Here |
| :---: | :---: | :---: | :---: | :---: |
| 🔬 **Security Researchers** | Study how LLMs perform on real IoT attack planning | Manual tool chains | Reproducible pipeline | [🧠 Ares AI](#-ares-ai--the-intelligence-layer) |
| 🏢 **Enterprise Security Teams** | Replace $25k engagements with continuous assessment | Annual pentests | Always-current posture | [💰 Pricing](#-pricing--read-this-before-you-buy-anything-else) |
| 🛠️ **Red Teams & Consultants** | 154 modules, no new hardware for network testing | Fragmented scripts | Unified arsenal | [⚔️ Attack Surface](#-attack-surface--154-modules-across-28-categories) |
| 🎯 **Lab & CTF Enthusiasts** | Deploy against QEMU farms or home labs | Manual recon + exploits | Safe, documented modules | [⚙️ Install](#️-installation) |

---

## 🧠 How Blitz Works

Blitz is a closed-loop autonomous system with five core components.

| 🧩 Component | 🎯 Role | 🔌 Port | 🛡️ Safety Boundary |
| :---: | :---: | :---: | :---: |
| 🎛️ **Operator Console** | Human control plane. Launch, approve, monitor | UI | Human-in-the-loop |
| 🧠 **Ares Agent** | AI orchestration. Profiles devices, plans assessments | `:9010` | No network I/O |
| 🔒 **Ares Bridge** | Capability gateway. Multi-condition rule checks | `:8089` | Enforcement point |
| 🖥️ **Ollama** | Local model runtime. Runs `ares` entirely on-prem | `:11435` | No external calls |
| ⚙️ **Blitz Core** | Execution engine. Runs approved modules, collects evidence | `:8088` | Executes only approved |
| 🗄️ **Persistent State** | Durable audit trail of devices, jobs, findings, incidents | DB | Immutable log |
| 📡 **Live Event Stream** | Real-time WebSocket feed to operator GUI | `:8088` | Full observability |

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

| 🎯 Stage | 🛠️ Method | 📊 Dataset Size | 🏆 Result Achieved |
| :---: | :---: | :---: | :---: |
| **1️⃣ SFT** | QLoRA on curated examples | 638 examples | ~85% correct routing |
| **2️⃣ GRPO** | Rule-based reward alignment | Generated candidates | ~98% JSON validity, ~92% routing, 100% safety refusal |
| **3️⃣ RFT** | Self-improvement loop | 638 → ~1,000 examples | Higher data quality, no new labels |
| **4️⃣ Curriculum** | Easy → hard sorting | Reordered dataset | Smoother training, +1–3% accuracy |

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

| 🔧 Feature | 🎯 What It Enables | 🏆 Buyer Benefit | 📈 Impact |
| :---: | :---: | :---: | :---: |
| 🔄 **Hot-swappable brain** | Point Ares at DeepSeek, Llama, Mistral, or your own endpoint | Model freedom | No lock-in |
| 🔬 **Retrain on your data** | Every engagement becomes training data | Compounds value | Gets better |
| 🛡️ **Air-gapped by default** | Zero telemetry, zero cloud, zero per-token | Full privacy | Enterprise OK |

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

| 🎯 Phase | 🛠️ Capabilities | 📦 Modules | 🏆 Highlight |
| :---: | :---: | :---: | :---: |
| **Extraction** | binwalk, unblob (30+ formats), SquashFS, CramFS, UBIFS, JFFS2 | 8 | 30+ formats |
| **Analysis** | entropy, secret scanning, credential extraction, SBOM, CVE matching | 7 | CVE matching |
| **Emulation** | FirmAE, Firmadyne, config extraction, emulated scanning, fuzzing | 6 | Full emulation |
| **Runtime** | GDB attach, Frida hooking, strace tracing | 3 | Live debugging |
| **Exploitation** | ROP gadget discovery, shellcode generation, PoC generation | 4 | Auto PoC |

</details>

<details>
<summary><b>📡 Wireless & RF (44 modules) — click to expand</b></summary>

| 📶 Subcategory | 📦 Modules | 🎯 Coverage | 🏆 Highlight |
| :---: | :---: | :---: | :---: |
| **BLE** | 12 | Scan, GATT enum, characteristic R/W, pairing downgrade, sniffing, replay, cracking, jamming, spoofing | GATT abuse |
| **Zigbee** | 8 | Network scan, sniffing, key extraction, frame replay, Touchlink, ZCL injection | Key extraction |
| **Wi-Fi 802.11** | 8 | Deauth, handshake capture, PMKID, WPS brute, KTO deauth, WPA3 downgrade | WPA3 attacks |
| **Additional RF** | 4 | Z-Wave S0 downgrade, LoRaWAN join replay, Matter DoS, Thread attack | Matter + Thread |

</details>

<details>
<summary><b>🔌 Hardware Interfaces (15 modules) — click to expand</b></summary>

| 🔧 Interface | 🎯 Coverage | 📦 Modules | 🏆 Highlight |
| :---: | :---: | :---: | :---: |
| **UART** | Baud detection, boot log capture, interactive console | 3 | Console access |
| **SPI** | Flash dump, integrity verification | 2 | Flash dump |
| **JTAG** | Chain scan, memory dump | 2 | Memory dump |
| **SWD** | ARM Cortex memory dump | 1 | Cortex support |
| **I2C** | Bus scan, EEPROM dump | 2 | EEPROM read |
| **CAN** | Bus sniffing, frame injection | 2 | Frame injection |
| **Glitching** | ChipWhisperer voltage/clock glitching | 2 | Voltage glitch |
| **Probe** | Automated hardware detection | 1 | Auto detect |

</details>

<details>
<summary><b>☁️ Cloud, Mobile, Voice & Smart Home (19 modules) — click to expand</b></summary>

| 🎯 Category | 📦 Modules | 💥 Coverage | 🏆 Highlight |
| :---: | :---: | :---: | :---: |
| **AWS / Azure IoT** | 5 | Fleet enumeration, shadow injection for RCE, wildcard MQTT | Fleet-wide RCE |
| **Amazon Alexa** | 7 | OAuth CSRF, rogue account linking, break-tag chain, SkillVet bypass | SkillVet bypass |
| **Google Home** | 5 | Rogue account link, DNS rebinding, prompt injection, promptware v2 | Promptware |
| **Audio Injection** | 2 | Ultrasonic (NUIT 1/2), laser (LightCommands, LCMA) | Laser injection |
| **Mobile Apps** | 3 | APK/IPA static analysis, embedded firmware, backend API IDOR | Firmware in apps |
| **Smart Home** | 4 | SmartThings, HomeKit, Tuya CloudCutter, Xiaomi tokens | Tuya CloudCutter |
| **OTA / Provisioning** | 2 | Firmware downgrade, signature stripping | Sig stripping |
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

| 💼 Engagement Type | 💵 Cost | 📅 Billing | 📄 What You Get | ⏳ Valid For | 💡 Reality |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 🧑‍💻 **Standard IT Pentest** | $5k–$100k+ | Per engagement | One report | Until scope changes | Snapshot only |
| 🔌 **IoT/OT Pentest** | $10k–$40k | Per engagement | One snapshot | Until a device joins | Higher for firmware |
| 🎯 **Red-Team IoT Engagement** | $30k–$150k+ | $120–$350/hr | Deep manual testing | Until delivered | Day-rate expensive |
| ⚡ **Blitz** | **$299 once** | Flat, one-time | Continuous, every device | Always running 🚀 | The baseline |

> 🧮 **The honest math:** Even against the cheapest IoT pentest quote on the market ($10,000), Blitz costs **~97% less** — and unlike every other row, it doesn't stop working the day after you pay.

### 🧮 ROI Calculator

| 📊 Your Situation | 💸 Cost Without Blitz | ⚡ Cost With Blitz | 💰 Net Savings | 📉 Reduction |
| :---: | :---: | :---: | :---: | :---: |
| 100 IoT devices, 1 pentest/year | $25,000 | $299 | **$24,701** | 98.8% |
| 500 IoT devices, 1 pentest/year | $40,000 | $299 | **$39,701** | 99.3% |
| 3-year pentest cycle (3 tests) | $75,000 | $299 | **$74,701** | 99.6% |
| **Cost per device (100 devices)** | $250 | **$2.99** | — | — |

### 🎯 Pricing Tiers

| 🏷️ Tier | 💵 Price | 📅 Availability | 🎁 Scope | 🎯 Best For | ⚡ Savings |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 🔥 **Early Adopter** | **$299** ~~$499~~ | First 25 licenses — code `EARLYBIRD` | Perpetual commercial rights | Solo researchers, small teams | 40% off |
| 💼 **Standard Commercial** | **$499** | Standard list price | Perpetual commercial rights | Consultancies, red teams | Baseline |
| 🏢 **Enterprise** | *Contact us* | Custom | + SLA, custom modules, dedicated support | Large orgs, regulated industries | Custom |

**[ 🚀 BUY EARLY ADOPTER LICENSE — $299 ](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)**

> ⚡ **Your devices are already connected. Already exposed. Already being watched — by someone.**
> **💀 $299 decides who finds the weakness first — you, or them.**

---

## 🛡️ Risk Reversal

We don't want you to guess. Here's what protects you. 🔒

| 🛡️ Protection | 🎯 What It Means | 🏆 Buyer Benefit | ✅ Confidence |
| :---: | :---: | :---: | :---: |
| ✅ **30-day money-back guarantee** | If Blitz doesn't find at least one issue on a device you own, we refund in full | Zero-risk purchase | 100% |
| 🔒 **Safety gate built in** | Multi-condition authorization, fuzzing off by default, destructive modules opt-in | No bricked devices | 100% |
| 🛡️ **Air-gapped AI** | No telemetry, no cloud, no per-token fees | Full privacy | 100% |
| ⚖️ **Perpetual commercial rights** | Unlimited internal assets and client engagements | No surprise costs | 100% |
| ♾️ **Lifetime updates** | New modules, new CVE profiles, engine upgrades included | Never outdated | 100% |

---

## 🏢 For Investors

Blitz is built by **ApexPredator Security & Labs**. We're taking Blitz from a research project into a commercial platform. 🚀

| 🎯 Dimension | 📊 Details | 🎁 Value | 📈 Trajectory |
| :---: | :---: | :---: | :---: |
| 🌍 **Market** | IoT/OT security is one of the fastest-growing segments in cybersecurity | Massive TAM | Regulatory tailwinds |
| 📈 **Traction** | *[Insert: licenses sold, revenue, GitHub stars]* | Proof of demand | Growing cohort |
| 🏰 **Moat** | Proprietary `ares` model, 154 in-house modules, safety gate, re-validation loop | Hard to clone | Deepening |
| 💰 **Business model** | $299 early / $499 standard / enterprise custom | Clean unit economics | Scalable |
| 🗺️ **Roadmap** | Matter 1.4, Thread 1.4, Wi-Fi 7, 5G RedCap, CRA/NIS2 mapping | Clear expansion | Multi-year |
| 👥 **Team** | *[Insert founder bios, CVE credits, talks]* | Credible founders | Proven |
| 🎯 **Ask** | *[Insert: raising $X, or open to acquisition]* | Clear ask | Open |

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

Add the module's `manifest.toml` and `knowledge.toml`. Retrain with the provided scripts to include the new routing decision in the model. Or run with the base model and rely on the framework's fallback logic.

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

| 🔧 Requirement | 🟡 Minimum | 🟢 Recommended | 🎯 Why It Matters | 💰 Cost |
| :---: | :---: | :---: | :---: | :---: |
| **OS** | Linux / macOS / Windows (WSL2) | Ubuntu 22.04 LTS | Stable Docker networking | Free |
| **CPU** | 4 cores | 8 cores | Parallel module execution | — |
| **RAM** | 8 GB | 16 GB | Local AI inference + state | — |
| **Disk** | 20 GB free | 40 GB free (SSD) | Model + audit history | — |
| **Docker Engine** | 24.x | Latest stable | Container runtime | Free |
| **Docker Compose** | v2 | v2 | Multi-service orchestration | Free |
| **Python** | 3.11+ | 3.11+ | Blitz Core compatibility | Free |
| **GPU (optional)** | 6 GB VRAM | 8 GB VRAM | Only for retraining | — |

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

| 🎯 Resource | 📝 Description | 🔗 Link | 🎁 Included |
| :---: | :---: | :---: | :---: |
| ♾️ **Lifetime updates** | New protocol modules, CVE detection profiles, engine enhancements | Automatic | ✅ With license |
| 💬 **Support** | Direct line to the team for pre-sale and post-sale questions | *[Insert email / Discord]* | ✅ With license |
| 🗺️ **Public roadmap** | See what's shipping next: Matter, Thread, Wi-Fi 7, compliance | *[Insert link]* | ✅ Public |
| 💡 **Feature requests** | Request new modules, integrations, or capabilities | *[Insert link]* | ✅ Community |

---

<div align="center">

**⚡ Blitz — Autonomous IoT/OT Red Teaming & Continuous Assessment. ⚡**

*Your devices are already connected. Already exposed. Already being watched — by someone.* 💀

*💵 $299 decides who finds the weakness first.*

**[ 🚀 BUY EARLY ADOPTER LICENSE — $299 ](https://polar.sh/apexpredator-security/products/blitz?discount_code=EARLYBIRD)**

*🔥 First 25 licenses only • Code `EARLYBIRD` • Perpetual commercial rights • Lifetime updates*

</div>