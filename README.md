# がっちむち♂ | gatchimuchio

### I build the architecture beneath AI — not just applications on top of it.

**Cognitive Engineering · Non-Neural Execution Engines · AI Agent Infrastructure · AI-Native Compilation**

> **日本語:** AIの出力だけでなく、**計算・判断・実行・権限・記憶・監査を成立させる構造そのもの**を研究・設計しています。主力は **D4 Pocket、BLUE-TANUKI、MINIDORA（ミニドラ）**。さらに **MINIDORA-BETA、AI-compiler、こんにゃく翻訳、MARS再現研究**へ展開しています。対象・責任・証拠・保証範囲を分け、仕様と実装を照合する工学を重視します。

A language model is not automatically an agent. A fluent answer is not proof of correct judgment. And granting tools to an LLM does not, by itself, create a trustworthy authority system.

**My work tackles all three gaps: the model, the decision-making and action-control layer, and the runtime infrastructure around it.**

I lead the architecture, specifications, development direction and acceptance criteria, using AI coding agents as implementation collaborators. The central engineering question is always the same: **What structure actually produces the result, and how can we rebuild and verify it without inheriting unnecessary assumptions?**

---

## Three Flagship Projects / 主力3プロジェクト

| Project | The proposition | Current evidence and boundary |
|---|---|---|
| **[🐚 D4 Pocket](https://github.com/gatchimuchio/D4-POCKET)** | **The operating foundation for AI agents.** A general-purpose control plane for runtimes, agents and tools, with explicit permission, approval, audit and recovery boundaries. | Scoped Windows normal Release / Codex CLI acceptance (W01); end-to-end Agent → MCP → result-dependent task still open (W02). Linux and other target OS paths are incomplete. **16 of 18 release blockers unresolved; not released.** |
| **[🦝 BLUE-TANUKI](https://github.com/gatchimuchio/BLUE-TANUKI)** | **Give AI capabilities, not unchecked authority.** A resident agent system with upstream governance, bounded execution, memory and auditable outcomes. | Public `1.0.0-rc.1` technical RC exists. Later `QE_BUILD` work adds bounded execution, recovery and browser/memory paths, but full system acceptance, five-OS release and owner GO remain open. |
| **[⚙️ MINIDORA / ミニドラ](https://github.com/gatchimuchio/NOTNN-LLM-MINIDORA)** | **Reconstruct language-model functions without neural networks or a Transformer core.** Keep the language model, judgment, external knowledge and capabilities distinct. | Historical same-run LIVE GPQA **29/198 → 80/198 (+51, zero regressions)** with added modules; a separate core run **40/198**. The isolated [MINIDORA-BETA](https://github.com/gatchimuchio/MINIDORA-BETA) is a different engine baseline, **not** a fresh benchmark of these scores. |

These are **three different engineering responsibilities**, not three names for the same chatbot.

### 🐚 D4 Pocket — AI agents need an operating foundation

**[Repository →](https://github.com/gatchimuchio/D4-POCKET)**

D4 Pocket (formerly GUI Shell) is built around a simple proposition: **as AI agents gain capabilities, runtime governance should become infrastructure—not an ad hoc collection of UI buttons, prompts and wrappers.**

- **Contract-driven integration:** Runtime, Adapter, Agent Task and permission boundaries are defined through machine-readable schemas and conformance paths.
- **Authority-sensitive Rust Broker:** authenticated execution, approval eligibility, audit and recovery are kept separate from the Flutter presentation layer.
- **Multi-agent operational surfaces:** comparison, handoff, task handling, runtime catalogs and a product-facing Agent Center.

The [October 11, 2026 B4-L2 development record](https://github.com/gatchimuchio/D4-POCKET/blob/main/docs/REV5_PRODUCT_PROGRESS.md) reports **569 Rust tests passed, 167 schemas and 245 conformance checks**, alongside bounded live Codex CLI integration tests. Those figures belong to that source revision and test environment, not to the current HEAD.

The [November 10 integrated progress record](https://github.com/gatchimuchio/D4-POCKET/blob/main/docs/QE_2026-11-09/進捗.md) now distinguishes **W01 scoped Windows acceptance** from **W02 open end-to-end Codex → MCP Tool → dependent task execution**. Ubuntu package install/update/rollback/uninstall has bounded acceptance evidence, but Linux product acceptance and broader release gates remain open. The record reports **16 unresolved release blockers of 18** and `release_ready=false`.

**The ambition:** an extensible “four-dimensional pocket” of agent capabilities, with the authority and responsibility to operate them coherently.

### 🦝 BLUE-TANUKI — AI should act within a system of judgment

**[Repository →](https://github.com/gatchimuchio/BLUE-TANUKI)**

BLUE-TANUKI is not designed as another chat frontend that happens to call tools. Its core idea is **to separate capability from authority**.

- **HDS-BRAIN** provides a standalone upstream decision and control boundary; its authority decisions do not call an LLM.
- **LLMs, tools and communication channels** remain downstream capabilities, not independent sources of permission.
- **Approval, audit, memory and recovery** are explicit parts of the execution model. Historical content and external metadata do not automatically escalate authority.

A public [technical RC](https://github.com/gatchimuchio/BLUE-TANUKI/releases) provides a bounded implementation and portable installers. The [November `QE_BUILD` ledger](https://github.com/gatchimuchio/BLUE-TANUKI/blob/main/docs/開発進捗.md) records local wiring for browser observation, task-scoped recovery, source-bound memory and subsequent decisions. Many entries report build or fixture evidence while explicitly marking full tests, live provider paths, five-OS acceptance and product release **NOT_RUN or OPEN**. The five-OS vision is a target, not a claim of five completed releases.

**The ambition:** move from “AI that can call things” to **AI whose decisions and actions can be governed and inspected**.

### ⚙️ MINIDORA — Rebuild an LLM without inheriting the Transformer architecture

**[Repository →](https://github.com/gatchimuchio/NOTNN-LLM-MINIDORA) · [Live demo video →](https://youtu.be/q7hF26QBabI) · [Measured capability experiment →](https://github.com/gatchimuchio/NOTNN-LLM-MINIDORA/blob/main/評価/GPQA_Diamond_MINIDORA80_Module_E2E_正本_2026-09-09.md)**

**What if the next route to capable AI is not a larger neural model, but a different engineering structure?** MINIDORA tackles that question by building a **non-neural language-model core**, separating decision governance through HDS, and attaching computation, knowledge retrieval and replaceable capabilities without turning them into one monolithic model.

Its strongest bounded demonstration is not just that the model can run. **On the September 9, 2026 GPQA Diamond experiment, enabling scientific-capability modules raised the same-run LIVE result from 29/198 to 80/198—51 additional correct answers, zero regressions—without retraining or enlarging the retained model core for that addition.**

| Evidence series | Recorded result | Interpretation |
|---|---:|---|
| Historical MINIDORA80 same-run comparison | **29/198 OFF → 80/198 ON (+51)** | End-to-end capability added by modules in that bounded experiment |
| Separate September 27, 2026 core measurement | **40/198 GPQA Diamond** | LIVE core-only evaluation, not interchangeable with MINIDORA80 |
| October 2026 Google ADK / Cloud Run | **Real HTTP responses, source retrieval and trace checks** | Working bounded chatbot paths—not an all-purpose conversational-quality certificate |

The historical MINIDORA80 40.40% result also sits in the same **roughly 40% numerical range** as the **39% GPT-4 baseline published in the original GPQA paper**. The tested subsets and evaluation conditions differ; it is **not a same-condition win or a claim of overall GPT-4 equivalence**.

The October 1 integrated implementation and subsequent chat additions have **not yet been measured across all 198 GPQA questions**, so the older benchmark results stay attached to their original versions.

**The ambition:** to reopen how LLM capabilities are engineered—**not only how many parameters they contain**.

---

## Current Expansion / 2026年11月の新展開

These are **distinct projects with their own contracts and acceptance gates**. Their presence in the portfolio does not mean they are integrated or released.

| Project | Engineering target | Verified public state / boundary |
|---|---|---|
| **[MINIDORA-BETA](https://github.com/gatchimuchio/MINIDORA-BETA)** | A general-purpose HDS-driven **input → core → output** execution engine, not a chatbot-only model. | Isolated `0.6.0b1` beta; **313 selected regression tests passed** on Linux/Python 3.12 (Nov 3). The R2 whole-system redesign is **design-only**; no new overall capability or GPQA claim. |
| **[AI-compiler](https://github.com/gatchimuchio/AI-compiler)** | An AI-oriented textual operation format compiled into machine-level artifacts under explicit ISA/ABI/format contracts, without requiring an existing high-level language as an intermediate. | Initial AIC/0.2 path targets **Linux x86-64, System V ABI, ELF64 objects**. Rust compiler and C++ harness are wired; local QC is recorded, but broad standards conformance and beta release are **not complete**. |
| **[Konjac Translation / こんにゃく翻訳](https://github.com/gatchimuchio/konjac-Translation)** | A multi-surface translation experience across text, speech, video, subtitles, documents and camera input, with MINIDORA-BETA as the intended engine boundary. | **Design and contracts only.** No runnable Konjac application or proven end-to-end translation pipeline yet. |
| **[MARS reconstruction](https://github.com/gatchimuchio/MARS)** | Recover Japanese railway reservation-system engineering knowledge by preserving historical sources and testing the design decisions they support. | Source-grounded MARS-1/MARS-101 **bounded logical experiments**, not a reproduction of the original machines or an official JR/Hitachi project. |

## Shared Engineering Method — Distinct Responsibilities

```text
Cognitive Engineering → shared inquiry and audit discipline

MINIDORA (research) → MINIDORA-BETA (isolated execution engine)
                        └── Konjac Translation (planned product consumer)
BLUE-TANUKI          → governed agent execution
D4 Pocket            → generic runtimes, tools and operator control

AI-compiler          → independent AI-to-machine translation research
MARS                 → independent historical engineering reconstruction
```

**These lines distinguish roles and proposed relationships; they do not certify cross-project integration or production readiness.**

The architecture is informed by the same method across domains:

```text
Observe the actual system
→ separate the target from its present implementation
→ identify relations, state changes and causal boundaries
→ specify who or what owns each decision
→ implement a testable alternative
→ measure results, failures and remaining gaps
→ revise the architecture where the evidence requires it
```

The point is not to invent terminology for its own sake. It is to stop mistaking the vocabulary of an existing implementation for the structure of the problem.

## Research Foundations / 研究基盤

**[Cognitive Engineering Foundations](https://github.com/gatchimuchio/cognitive-engineering-foundations)** archives the Japanese canonical work behind my cognitive-engineering program, including language-base theory, the Trinity Principle, Closure Phase Ψ and **神の領域原理（仮）** (the provisional God's Domain Principle). Its current 14 canonical documents have separately classified English full translations and summary projections. The Japanese original remains authoritative; the project investigates how objects, relations and judgments are formed before they are promoted into engineering models.

**[LLM-Constitutive-Specification](https://github.com/gatchimuchio/LLM-Constitutive-Specification)** separates the constitutive conditions of a language model from a particular model family, and distinguishes reproducing a local operation from reproducing a decision-making system. It is a specification with explicit applicability boundaries—not a statement that every model must use HDS.

**[HDS-BlackBox-Translator](https://github.com/gatchimuchio/HDS-BlackBox-Translator)** records an earlier bounded public explanation experiment. It is a **legacy public projection**, not a current HDS specification or a disclosure of private internals.

The current theoretical publication boundary exposes **HDS by name only**. Historical public demos and product-level references must not be read as a current disclosure of HDS internals. Each repository sets its own public evidence and publication boundary.

## 🌸 Project ORCHID — Work Beyond AI

**[Project ORCHID](https://github.com/DigitalServerHost/ORCHID)** is low-level execution and memory-architecture work that grew from my initial locality and multi-memory-role proof-of-concept research.

- **Concept originator:** credited under my personal name in the [ORCHID repository](https://github.com/DigitalServerHost/ORCHID) (GitHub: [@gatchimuchio](https://github.com/gatchimuchio))
- **Core architecture and maintainer:** Kevin West ([@westkevin12](https://github.com/westkevin12))

The ORCHID repository preserves the division of responsibility and the [original baseline](https://github.com/DigitalServerHost/ORCHID/tree/gatchimuchio-original). The engineering connection with my AI work is the deliberate separation of **what a system must do** from **how its current hardware or software implementation happens to do it**.

## How I Build / 開発手法

**I treat AI coding agents as an engineering workforce—not as the source of project goals, permission or final judgment.**

My role is to determine the problem, design the system, formalize constraints and instructions, inspect the actual implementation, and decide whether the observed evidence warrants acceptance. A change in code is not automatically a change in capability; a passing unit test is not automatically a working product.

The working rules are straightforward:

- **Goals and responsibility boundaries before tool choice**
- **End-to-end integration before mistaking isolated components for a finished system**
- **Evidence tied to exact source revisions, environments and conditions**
- **Explicit authorization, auditability and recovery for consequential actions**
- **Failure analysis that can reopen an upstream assumption, not just patch a downstream symptom**

I am interested in systems whose operating principles can be explained, tested, challenged and improved—even when the implementation breaks with convention.

---

## Links

**Flagship projects:** [D4 Pocket](https://github.com/gatchimuchio/D4-POCKET) · [BLUE-TANUKI](https://github.com/gatchimuchio/BLUE-TANUKI) · [MINIDORA](https://github.com/gatchimuchio/NOTNN-LLM-MINIDORA)

**New work:** [MINIDORA-BETA](https://github.com/gatchimuchio/MINIDORA-BETA) · [AI-compiler](https://github.com/gatchimuchio/AI-compiler) · [Konjac Translation](https://github.com/gatchimuchio/konjac-Translation) · [MARS](https://github.com/gatchimuchio/MARS)

**Research and collaboration:** [Cognitive Engineering](https://github.com/gatchimuchio/cognitive-engineering-foundations) · [LLM Constitutive Specification](https://github.com/gatchimuchio/LLM-Constitutive-Specification) · [Legacy HDS demo](https://github.com/gatchimuchio/HDS-BlackBox-Translator) · [Project ORCHID](https://github.com/DigitalServerHost/ORCHID)

**GitHub:** [@gatchimuchio](https://github.com/gatchimuchio)

*Portfolio status reviewed against public repository records on November 10, 2026 (JST). Each milestone describes its recorded revision and scope, not blanket certification or commercial release readiness.*
