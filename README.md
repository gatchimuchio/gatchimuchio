# がっちむち♂ | gatchimuchio

### I build the architecture beneath AI — not just applications on top of it.

**AI Agent Infrastructure · Cognitive Engineering · Non-Neural LLMs · Systems Architecture**

> **日本語:** AIの出力を使うだけではなく、**知能の構成、判断、権限、実行、記憶、監査を成立させる仕組みそのもの**を研究・設計しています。主力プロジェクトは **D4 Pocket、BLUE-TANUKI、MINIDORA（ミニドラ）**。目標は、AIの能力と実世界での運用責任を、実装・検証できる工学構造に変えることです。

A language model is not automatically an agent. A fluent answer is not proof of correct judgment. And granting tools to an LLM does not, by itself, create a trustworthy authority system.

**My work tackles all three gaps: the model, the decision-making and action-control layer, and the runtime infrastructure around it.**

I lead the architecture, specifications, development direction and acceptance criteria, using AI coding agents as implementation collaborators. The central engineering question is always the same: **What structure actually produces the result, and how can we rebuild and verify it without inheriting unnecessary assumptions?**

---

## Three Flagship Projects / 主力3製品

| Project | The proposition | Current evidence and boundary |
|---|---|---|
| **[🐚 D4 Pocket](https://github.com/gatchimuchio/D4-POCKET)** | **The operating foundation for AI agents.** A general-purpose control plane for runtimes, agents and tools, with explicit permission, approval, audit and recovery boundaries. | Windows feature-complete development milestone; bounded mobile/non-Windows acceptance; B4 integration remains open. **Not yet a production release.** |
| **[🦝 BLUE-TANUKI](https://github.com/gatchimuchio/BLUE-TANUKI)** | **Give AI capabilities, not unchecked authority.** A resident agent system with standalone HDS-BRAIN governing decisions, execution boundaries and traceable results. | Public `1.0.0-rc.1` technical release candidate; newer end-to-end agent work in `QE_BUILD`. **GA and owner release approval remain pending.** |
| **[⚙️ MINIDORA / ミニドラ](https://github.com/gatchimuchio/NOTNN-LLM-MINIDORA)** | **Rebuild LLMs from first principles, without a Transformer core.** A non-neural system that separates the language model, judgment, knowledge and extensible capabilities. | Historical same-run LIVE GPQA: **29/198 → 80/198 (+51, zero regressions)** without core retraining for this capability addition; independent core run **40/198**; bounded ADK/Cloud Run demo. Newer integrated code is not yet re-benchmarked. |

These are **three different engineering responsibilities**, not three names for the same chatbot.

### 🐚 D4 Pocket — AI agents need an operating foundation

**[Repository →](https://github.com/gatchimuchio/D4-POCKET)**

D4 Pocket (formerly GUI Shell) is built around a simple proposition: **as AI agents gain capabilities, runtime governance should become infrastructure—not an ad hoc collection of UI buttons, prompts and wrappers.**

- **Contract-driven integration:** Runtime, Adapter, Agent Task and permission boundaries are defined through machine-readable schemas and conformance paths.
- **Authority-sensitive Rust Broker:** authenticated execution, approval eligibility, audit and recovery are kept separate from the Flutter presentation layer.
- **Multi-agent operational surfaces:** comparison, handoff, task handling, runtime catalogs and a product-facing Agent Center.

The [October 11, 2026 B4-L2 development record](https://github.com/gatchimuchio/D4-POCKET/blob/main/docs/REV5_PRODUCT_PROGRESS.md) reports **569 Rust tests passed, 167 schemas and 245 conformance checks**, alongside bounded live Codex CLI integration tests. Those figures describe a particular source revision and test environment—not a universal product guarantee. The complete Windows Desktop → Broker → real Codex → Agent Center product path was still open, with `release_ready=false`.

**The ambition:** an extensible “four-dimensional pocket” of agent capabilities, with the authority and responsibility to operate them coherently.

### 🦝 BLUE-TANUKI — AI should act within a system of judgment

**[Repository →](https://github.com/gatchimuchio/BLUE-TANUKI)**

BLUE-TANUKI is not designed as another chat frontend that happens to call tools. Its core idea is **to separate capability from authority**.

- **HDS-BRAIN** provides a standalone upstream decision and control boundary; its authority decisions do not call an LLM.
- **LLMs, tools and communication channels** remain downstream capabilities, not independent sources of permission.
- **Approval, audit, memory and recovery** are explicit parts of the execution model. Historical content and external metadata do not automatically escalate authority.

A public [technical RC](https://github.com/gatchimuchio/BLUE-TANUKI/releases) provides a bounded implementation and portable installers. Subsequent development expands the plan → execution → result → memory → resumed-work chain. The current five-OS product vision is **a development target**, not a claim of five completed releases.

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

## One Engineering Program — Different Layers

```text
Cognitive Engineering / HDS
     │   principles, distinctions, judgment boundaries
     │
     ├── MINIDORA      → language-model functions and computation
     ├── BLUE-TANUKI   → judgment, authority, execution governance
     └── D4 Pocket     → generic runtimes, tools and operator control
```

**This is a map of design responsibilities and intended integration—not a claim that every cross-project production connection has already shipped.**

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

**[Cognitive Engineering Foundations](https://github.com/gatchimuchio/cognitive-engineering-foundations)** is the public archive of my Japanese-first cognitive-engineering work, including language-base theory, the Trinity Principle, Closure Phase Ψ and the Domain of God Principle (神域原理). The project examines how objects, distinctions, relations and judgments are formed before they become engineering models.

**[LLM-Constitutive-Specification](https://github.com/gatchimuchio/LLM-Constitutive-Specification)** separates the constitutive conditions of a language model from a particular model family, and distinguishes reproducing a local operation from reproducing a decision-making system. It is a specification with explicit applicability boundaries—not a statement that every model must use HDS.

**[ARC-2-AGI-SOLVER](https://github.com/gatchimuchio/ARC-2-AGI-SOLVER)** explores general-purpose solving using a learning-machine structure, reusable memory and task-grounded evaluation. Its public repository documents the environment and ongoing work; this profile does not assert a competition score.

The public repositories intentionally do **not** disclose complete private HDS internals or full mappings from private theoretical definitions to implementation. The publication boundary of each repository controls what is shared.

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

**Research:** [Cognitive Engineering](https://github.com/gatchimuchio/cognitive-engineering-foundations) · [LLM Constitutive Specification](https://github.com/gatchimuchio/LLM-Constitutive-Specification) · [Project ORCHID](https://github.com/DigitalServerHost/ORCHID)

**GitHub:** [@gatchimuchio](https://github.com/gatchimuchio)

*Technical milestones above are dated observations, not blanket certification or commercial release claims.*
