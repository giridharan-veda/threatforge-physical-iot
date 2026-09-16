# GitHub Discussions & Community Guidelines

Welcome to the Blitz GitHub Discussions space! This is the primary community forum for licensed operators, reverse engineers, IoT/OT security engineers, and contributors to discuss capability coverage, refine heuristics, and share deployment feedback[cite: 2].

---

## 📌 Rules & Guidelines

All interactions in GitHub Discussions are governed by our [Code of Conduct](./CODE_OF_CONDUCT.md), [CONTRIBUTING.md](./CONTRIBUTING.md), and [License Agreement](./LICENSE.md)[cite: 1, 2, 3].

* **Valid License Required:** Participating in technical design discussions or proposing code contributions requires an active Blitz license in good standing[cite: 2].
* **Strictly Authorized Scope Only:** Never post target IPs, unredacted PCAPs, live credentials, or logs from systems you do not have written authorization to test[cite: 1, 3, 5].
* **No Blitz Vulnerabilities Here:** If you discover a bug that bypasses the **Ares Bridge** capability gateway or impacts Blitz itself, **do not post it publicly**[cite: 2, 5]. Follow the private reporting process in [SECURITY.md](./SECURITY.md)[cite: 2, 5].
* **Respectful Technical Debate:** Pointed criticism regarding heuristics, safety boundaries, or capability gating is welcome; contempt or personal attacks are not[cite: 1, 2].

---

## 💡 Discussion Categories

Please post your topic in the appropriate category:

### 📢 Announcements
* **Maintained by:** ApexPredator Security Team[cite: 4]
* **Purpose:** Release updates, new protocol modules, CVE profiles, and maintenance notices[cite: 4].

### 🧠 Ares AI & Heuristics (`ares/`)
* **Purpose:** Planning prompts, tool-selection heuristics, local Ollama performance, and fine-tuning datasets[cite: 2, 4].

### 🛡️ Ares Bridge & Safety (`ares/bridge/`)
* **Purpose:** Capability gateway rules, scope enforcement, and blast-radius safety[cite: 2, 4].
* **Requirement:** Open a design discussion here *before* opening a PR that touches `ares/bridge/` or authorization logic[cite: 2].

### 🔌 Protocols & Target Modules (`blitz-core/`, `configs/`)
* **Purpose:** Requests and design specs for protocol decoders, active probes, and device fingerprint rules in `capabilities.yaml` (e.g., BACnet, Modbus, ONVIF, RTSP)[cite: 2, 4].

### 💡 Ideas & Feature Requests
* **Purpose:** Proposals for execution enhancements, Operator Console UI updates, or deployment workflows[cite: 4].

### ❓ Q&A / Support
* **Purpose:** Help with `docker-compose` deployments, `blitz-setup.sh`, or general configuration issues[cite: 4].

---

## 🚀 Creating a Discussion

1. **Search First:** Check existing issues and discussions to avoid duplicate topics[cite: 2].
2. **Be Precise:** State what you tested, what environment you used (e.g., QEMU ARM64, Docker emulation, lab hardware), and what you observed[cite: 1, 2]. Redact all sensitive target data[cite: 1, 2].
3. **Discuss Architecture Early:** If you intend to submit code, outline your design here first so maintainers can review safety implications before you write code[cite: 2].

---

*Need to report a security issue? See [SECURITY.md](./SECURITY.md).*[cite: 2, 5]  
*Preparing a pull request? Read [CONTRIBUTING.md](./CONTRIBUTING.md).*[cite: 2]