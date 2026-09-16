# Contributing to Blitz

Blitz is commercial software, but it's built in the open with input from the people who actually use it — red teamers, IoT/OT security engineers, reverse engineers, and distributed systems developers. This document is how you become part of that group: the **ApexPredator community**.

Before contributing, please read the [License Agreement](./LICENSE.md), [SECURITY.md](./SECURITY.md), and [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md). This document assumes familiarity with all three.

---

## Who This Is For

- Licensed operators who've found a gap, a bug, or a better way to handle a device family in the field.
- Protocol and firmware people who want to add coverage Blitz doesn't have yet.
- Anyone who's spent time in the Ares Bridge and has opinions about how the authorization gate should behave.

You don't need to be a core maintainer to contribute — you need a working license, a focused change, and a willingness to go through review.

---

## Before You Start

1. **Check for an existing issue or discussion.** Search open issues and pull requests first. If nothing matches, open an issue describing the problem or idea before writing code — this avoids duplicated work and lets maintainers flag design concerns (especially around the authorization gate) before you've invested time.
2. **For anything touching Ares Bridge, capability gating, or execution boundaries**, open a design discussion first. This is the trust boundary of the whole platform (see SECURITY.md) — changes here get more scrutiny, earlier.
3. **Confirm your license covers this.** Contributing requires a valid Blitz license in good standing. See [Licensing & Contributor Terms](#licensing--contributor-terms) below.

---

## Priority Contribution Tracks

These are the areas where contributions have the most impact right now:

| Track | Location | What's Needed |
|---|---|---|
| **New Protocol Modules** | `blitz-core/` | Native decoders and active probes for unmapped embedded interfaces — BACnet, Modbus, Zigbee over IP, proprietary camera APIs, etc. |
| **Ares AI Reasoning & Heuristics** | `ares/` | Refined planning prompts, fine-tuning data, and tool-selection heuristics that improve decision quality on complex device states |
| **Gateway & Blast-Radius Safety** | `ares/bridge/` | Hardening the Ares Bridge against erratic AI behavior, cyclic planning loops, or requests that shouldn't be approved |
| **Target Hardware Signatures** | `configs/` | Expanded device identification matrices and fingerprint rules in `capabilities.yaml` |
| **Documentation** | `docs/` | Architecture write-ups, module usage guides, troubleshooting notes from real deployments |

If your idea doesn't fit cleanly into one of these, that's fine — open an issue and describe it. Not everything useful fits a table.

---

## Development Workflow

1. **Fork & branch.** Create a focused feature branch off `main`:
   ```bash
   git checkout -b feat/add-bacnet-enumeration
   ```
   Use a prefix that describes the change: `feat/`, `fix/`, `docs/`, `safety/` (for anything touching the authorization gate).

2. **Keep changes scoped.** One protocol module, one heuristic change, one fix per PR. Large mixed PRs are hard to review carefully, and careful review matters more here than in most projects — see the note on safety below.

3. **Follow existing patterns.** New protocol modules should mirror the structure of existing ones in `blitz-core/` (discovery → fingerprint → assessment → verification), not introduce a parallel style. Look at an existing module in the same directory before writing a new one.

4. **Test locally against a real or emulated target.** Unit tests aren't sufficient for protocol or execution changes — validate against QEMU/Docker-emulated devices or a lab target you're authorized to test against. Include what you tested against in your PR description.

5. **Run the test suite:**
   ```bash
   cd tests/
   # follow the test runner instructions in tests/README.md
   ```

6. **Update documentation.** If your change adds a module, a config option, or changes behavior an operator would notice, update the relevant file in `docs/`. PRs that add capability without docs will be asked to add them before merge.

7. **Open the PR.** Reference the issue it addresses. Describe what you changed, why, and what you tested it against — especially for anything that executes actions against a device.

---

## What Gets Extra Scrutiny

Because Blitz executes real actions against real, often fragile hardware, some categories of change are held to a higher bar than typical open-source review:

- **Anything in `ares/bridge/`** — the capability gateway is the safety boundary between planning and execution. Changes here need a clear explanation of what new capability is being gated, how it's constrained, and what happens if Ares requests it incorrectly.
- **New execution primitives** — any new "attempted" action needs a corresponding "proven" verification path. We don't merge modules that claim impact without evidence.
- **Changes that widen default scope** — anything that makes Blitz touch more of a network or a device by default, rather than narrower and explicit, needs justification.
- **Anything that could turn a probe into a disruptive action** — fuzzing intensity, retry behavior, timeout handling on constrained devices. Bricking risk is real; see the Hardware Disclaimer in the License.

If you're not sure whether your change falls into one of these categories, ask in the issue before opening the PR. It's a five-minute question that saves a slow review cycle.

---

## Code Style

- Python 3.11+, type-hinted where the surrounding code already is.
- Match the logging and error-handling conventions of the module you're editing — Blitz Core, Ares, and the Bridge each have slightly different idioms; don't introduce a fourth.
- New protocol modules should fail closed: an unhandled response, timeout, or malformed packet should result in "no finding" or "attempted, not proven," never a false "proven."
- No hardcoded credentials, tokens, or target IPs in code or tests — see SECURITY.md's guidance on secrets handling, which applies to contributions too.

---

## Reporting Bugs vs. Reporting Vulnerabilities

- **Bugs** (a module misidentifies a device, a false positive, a crash on a specific input): open a regular GitHub issue.
- **Security vulnerabilities in Blitz itself** (something that lets Ares bypass the Bridge, or lets the Bridge approve something it shouldn't): **do not open a public issue.** Follow the private reporting process in [SECURITY.md](./SECURITY.md).

If you're not sure which one you've found, treat it as the latter and report it privately — it's easy to downgrade a private report, much harder to undo a public one.

---

## Licensing & Contributor Terms

Blitz is commercial software under the [ApexPredator Security Commercial License](./LICENSE.md), not an open-source license. A few things follow from that:

- **You need an active, valid license** to contribute. Contributions from unlicensed accounts will be closed without review.
- **By submitting a contribution**, you grant ApexPredator Security a perpetual, worldwide, royalty-free license to use, modify, and incorporate your contribution into Blitz, including in future commercial releases. You retain attribution credit but not exclusive rights to the merged code.
- **Don't contribute anything you don't have the rights to.** Code lifted from another commercial tool's decompiled output, someone else's proprietary heuristics, or another project's incompatible-licensed code will be rejected and, if merged in error, removed on discovery.
- **Contributions don't grant additional license seats.** Contributing to the project doesn't change your seat tier under Section 1 of the License Agreement.

If your organization needs a separate contributor agreement (e.g., for a significant module contributed on behalf of a company), open an issue and we'll sort out the paperwork before you invest real time.

---

## Community Standards

All contribution spaces — issues, PRs, discussions, review comments — are covered by the [Code of Conduct](./CODE_OF_CONDUCT.md). The short version: be precise, respect scope, don't paste live target data into a public PR, and disagree about code without being unpleasant about it.

---

## Recognition

Contributors whose changes get merged are credited in release notes and, for significant or sustained contributions, in a contributors' acknowledgments page. If you'd rather stay anonymous, say so in your PR.

This is early — the ApexPredator community is small on purpose right now. Good contributions here carry real weight, and the people who show up early shape what this becomes.
