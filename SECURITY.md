# Security Policy

Blitz is an offensive security platform. That means two things are true at once: it needs to be trusted to run real attacks against real infrastructure, and it needs to be held to a higher security bar than ordinary software — a vulnerability in Blitz itself is a vulnerability in every network it's deployed on.

This document describes how we handle vulnerability reports, what versions receive security fixes, and the security model behind how Blitz operates.

---

## Reporting a Vulnerability

**Please do not open a public GitHub issue for security vulnerabilities.** Public issues are visible to anyone, including people who might misuse the information before a fix is available.

Instead, report privately to:

- **Email:** `security@[yourdomain].com` *(replace with your real security contact)*
- **PGP Key:** *(optional — link or fingerprint, if you offer encrypted reporting)*
- **Alternative:** GitHub's private vulnerability reporting feature, if enabled on this repository

### What to include

To help us triage quickly, please include:

1. A clear description of the vulnerability and its potential impact
2. Steps to reproduce, or a proof-of-concept if available
3. The affected component (Operator Console, Ares Agent, Ares Bridge, Blitz Core, Ollama integration, etc.)
4. The version or commit hash you tested against
5. Whether the issue has already been publicly disclosed or shared elsewhere

### What to expect

| Stage | Timeline |
|---|---|
| Acknowledgment of your report | Within **48 hours** |
| Initial assessment and severity rating | Within **5 business days** |
| Fix or mitigation for critical issues | Target **within 14 days** of confirmed severity |
| Public disclosure / advisory | Coordinated with you, typically after a fix is available |

We follow a **coordinated disclosure** model: we ask that you give us a reasonable window to fix the issue before any public disclosure, and in return we commit to keeping you informed of progress and crediting you (if desired) once the issue is resolved.

### Scope

In scope:
- The Blitz Core execution engine
- Ares Agent and Ares Bridge (planning and capability-gating logic)
- The Operator Console (web UI / API)
- Authentication, authorization, and the capability-gating mechanism itself
- Container images and deployment configurations we publish
- Dependency vulnerabilities that are meaningfully exploitable in Blitz's default configuration

Out of scope:
- Vulnerabilities in third-party LLM providers (OpenAI, Anthropic, DeepSeek) or in Ollama itself — report those upstream
- Vulnerabilities that require an attacker to already have Operator-level credentials and full authorization-gate approval (i.e., "it can do what it's authorized to do")
- Issues in devices or networks Blitz is used *against* — that's the point of the tool, not a vulnerability in it
- Missing security best practices in a Licensee's own deployment (e.g., running Blitz on an unpatched host OS)

---

## Supported Versions

| Version | Supported |
|---|---|
| Latest v1.x release | ✅ Full security support |
| Older v1.x releases | ⚠️ Critical fixes only, for the remainder of your 12-month update window (see license) |
| v0.x / pre-release | ❌ Not supported |

We recommend always running the latest v1.x release. Security fixes are not backported beyond the current minor version line except for critical, actively-exploited issues.

---

## Security Model — How Blitz Is Designed to Fail Safely

Because Blitz executes real actions against real, often fragile devices, its security model is as much about **containing what Blitz itself can do** as it is about defending Blitz from attackers. If you're evaluating Blitz for deployment, this is the part that should matter most to your security team.

- **Authorization gate is the trust boundary.** Every action Ares proposes passes through the Ares Bridge capability gateway before it reaches a real device. Ares Bridge — not Ares itself — is the enforcement point, and it's designed to be the thing you audit most carefully.
- **Least-privilege network access.** Blitz should be deployed with network access scoped only to the IoT/OT segments it's authorized to assess — not broad access to your entire environment.
- **Local inference option.** Ollama support exists specifically so device data, findings, and assessment context can stay on-premises rather than transiting third-party AI APIs, for environments where that matters.
- **Full audit trail.** Persistent State retains a complete history of every device, job, finding, and incident — including actions that were proposed but denied by the authorization gate — so any Blitz-driven action can be reconstructed after the fact.
- **Evidence over assumption.** The "attempted vs. proven" model exists partly for accuracy and partly for safety — it discourages treating unverified AI output as an executed action.

If you find a way to make Ares propose an action that bypasses Ares Bridge, or a way to make Ares Bridge approve something it shouldn't under its stated rules, **that is exactly the kind of report we most want to receive.**

---

## Secrets, Credentials & Data Handling

- API keys for third-party LLM providers (BYOK) should be stored using your platform's secret management (environment variables, a secrets manager, or Docker secrets) — never committed to version control or embedded in configuration files checked into a repository.
- Findings and evidence collected during assessments may contain sensitive information (device credentials, network topology, exposed data) — treat Blitz's Persistent State store with the same access controls you'd apply to a penetration test report.
- If you believe Blitz mishandles, over-collects, or insecurely stores credentials or evidence, report it through the process above — this is treated as a security issue, not a feature request.

---

## Responsible Use Reminder

This policy covers vulnerabilities *in* Blitz. It does not cover, authorize, or condone using Blitz against any target without the Documented Authorization required under the [License Agreement](./LICENSE.md). Reports involving evidence of unauthorized use of Blitz against third-party infrastructure will be handled separately from standard vulnerability triage.

---

## Acknowledgments

We credit security researchers who responsibly disclose valid issues (with their permission) in our release notes and, where applicable, a security acknowledgments page. If you'd prefer to remain anonymous, let us know in your report.

---

*Questions about this policy that aren't a vulnerability report? Open a regular GitHub issue or reach out via the contact channels in the main [README](./README.md).*
