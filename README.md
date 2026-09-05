# Teppei Oohira / 大平鉄兵

### Cognitive Engineering, Systems Architecture, and Non-Neural LLMs

I work on engineering systems by separating **what must be true for a system to exist or function** from **the implementation currently used to realize it**.

My typical process is:

```text
observe the existing system
→ separate what is currently fused together
→ identify the relations and state changes that actually produce the result
→ define the constitutive boundary
→ rebuild the required structure in another form
→ verify it through implementation and measurement
```

This approach currently connects my work in cognitive engineering, language-model architecture, runtime control, and low-level execution systems.

---

## Current Focus — MINIDORA

[**NOTNN-LLM-MINIDORA**](https://github.com/gatchimuchio/NOTNN-LLM-MINIDORA) is a non-neural, non-Transformer LLM research and implementation project.

MINIDORA did **not** begin from the question:

```text
Can I replace Transformer with another architecture?
```

The actual sequence was:

```text
1. Separate “what makes an LLM an LLM” from a specific implementation.
2. Define constitutive conditions, boundaries, and capability actions.
3. Structuralize existing LLMs by observing what they retain, change,
   reuse, revisit, recombine, and route.
4. Reimplement those constitutive and functional relations without
   using a neural network or Transformer as the core mechanism.
5. The resulting implementation is MINIDORA.
```

The central distinction is:

> **The currently dominant implementation of an LLM is not automatically identical to the constitutive conditions of an LLM.**

MINIDORA therefore treats neural networks and Transformers as powerful realization methods, not as definitions that must be embedded into the meaning of “LLM” itself.

### What is already implemented and measured

- non-neural strict language-model core
- explicit persistent model state and language-state boundaries
- capability/state-delta execution paths
- deterministic and inspectable execution boundaries
- externalized Data / Knowledge / Compute / Capability separation
- capability modules that can be attached without retraining the Core
- execution traces that preserve why a state or candidate changed

The repository intentionally separates these claims:

```text
strict language-model formation
!= reasoning mechanism formation
!= Core capability performance
!= Module-augmented system performance
!= product readiness
!= frontier-model equivalence
```

### Why GPQA Diamond appears in the repository

GPQA Diamond is used as a **measurement surface**, not as the definition of an LLM and not as proof by benchmark score alone.

It provides a fixed 198-question set on which the same Core can be measured while changing one mechanism or connection condition at a time.

For example, a controlled replay with existing scientific capability modules observed:

```text
Module OFF = 8 / 198
Module ON  = 63 / 198
Module fired = 55
improved     = 55
regressed    = 0
```

The important result is not the absolute score. The important result is that the same Core could acquire additional effective capability through externally attached modules **without retraining, fine-tuning, weight updates, Core replacement, or Core enlargement for that capability addition**.

Repository: [gatchimuchio/NOTNN-LLM-MINIDORA](https://github.com/gatchimuchio/NOTNN-LLM-MINIDORA)

---

## Constitutive Specification of LLMs

[**LLM-Constitutive-Specification**](https://github.com/gatchimuchio/LLM-Constitutive-Specification) is the specification layer that precedes MINIDORA.

Its purpose is to separate language-model formation from implementation-specific names and technologies.

A current core formulation is:

```text
complete language-state space
+ persistent model state
→ one coherent language probability law
```

The specification also separates observable capability-action units such as:

```text
state carrier
operation
state delta
subsequent use
reference change
route change
computation change
re-reference
recombination
cycle scale
```

This is not a claim that reproducing local actions reproduces an entire neural model, decision system, or capability subject. Those boundaries are kept explicit.

Repository: [gatchimuchio/LLM-Constitutive-Specification](https://github.com/gatchimuchio/LLM-Constitutive-Specification)

---

## Cognitive Engineering Foundations

[**cognitive-engineering-foundations**](https://github.com/gatchimuchio/cognitive-engineering-foundations) is the public source archive for my current cognitive-engineering framework.

The repository treats cognition not merely as an object to be described, but as a prior engineering layer involved in how objects, distinctions, relations, information, judgments, and models are formed.

Current public work includes:

- what cognitive engineering is
- language-base theory for information engineering
- Umami Gap
- Trinity Principle
- Closure Phase Ψ
- Domain of God Principle / 神域原理（仮）
- applied argument-audit and game-theory work

The canonical language is **Japanese**. Other-language versions are downstream translations when needed for external communication.

Repository: [gatchimuchio/cognitive-engineering-foundations](https://github.com/gatchimuchio/cognitive-engineering-foundations)

---

## Project ORCHID

[**Project ORCHID**](https://github.com/DigitalServerHost/ORCHID) is a low-level execution and memory-architecture project that grew from my initial proof-of-concept work.

My original focus was not merely “loop optimization.” It was the broader question of whether data placement, movement, reuse, preparation, and memory-role separation should be treated as explicit execution structure.

The initial work included:

- cache-locality experiments
- execution-order effects on identical computation
- role-separated multi-memory-bank concepts
- early execution-architecture PoCs

The project was then expanded into a larger public system by Kevin West.

- **Concept Originator:** Teppei Oohira / 大平鉄兵 (@gatchimuchio)
- **Core Architecture & Maintainer:** Kevin West (@westkevin12)

Current ORCHID work includes execution-daemon, scheduling, JIT, x86-64 / AVX paths, ARM64, memory-role scheduling, SDK, and containerized execution work.

Repository: [DigitalServerHost/ORCHID](https://github.com/DigitalServerHost/ORCHID)

---

## The common pattern between ORCHID and MINIDORA

The target layers are completely different, but the engineering operation is similar.

```text
ORCHID
existing CPU / memory execution
→ separate access, locality, movement, and resource roles
→ rebuild execution structure

MINIDORA
existing LLM implementation
→ separate constitutive conditions, state changes, reuse, routing,
  recombination, capability, data, and control
→ rebuild language-model structure
```

I am generally more interested in **what actually makes a result exist** than in preserving the implementation categories that currently surround it.

---

## Other Systems Work

| Project | Role | Scope |
|---|---|---|
| [MINIDORA](https://github.com/gatchimuchio/NOTNN-LLM-MINIDORA) | Architect / Maintainer | Non-neural, non-Transformer LLM implementation, structuralized capability paths, modular capability growth |
| [LLM-Constitutive-Specification](https://github.com/gatchimuchio/LLM-Constitutive-Specification) | Author / Maintainer | Constitutive definition of language models independent of a specific implementation family |
| [cognitive-engineering-foundations](https://github.com/gatchimuchio/cognitive-engineering-foundations) | Author / Maintainer | Cognitive engineering foundations, language-base theory, Trinity, Ψ, 神域原理（仮） |
| [Project ORCHID](https://github.com/DigitalServerHost/ORCHID) | Concept Originator | Low-level execution, memory locality, role-separated memory scheduling foundations |
| [GUI Shell](https://github.com/gatchimuchio/GUI-Shell) | Architect / Maintainer | Desktop-first AI Runtime / Agent Operation Shell with permission, approval, audit, and recovery boundaries |
| [BLUE-TANUKI](https://github.com/gatchimuchio/blue-tanuki) | Architect / Maintainer | Local resident AI control plane with explicit authority ownership and inspectable downstream execution |

---

## Engineering Position

I do not treat an existing implementation, benchmark, abstraction, authority, or explanation as identical to the system or world it describes.

My working principles are:

- **constitutive structure before implementation habit**
- **causal and state relations before labels**
- **explicit boundaries before hidden assumptions**
- **reproducible evidence before completion claims**
- **failed experiments are preserved when they delimit what is not yet established**
- **a current model may be used strongly without being promoted into an irreversible final truth**

For that reason, my public repositories intentionally preserve not only successes, but also failed measurements, unresolved boundaries, version history, and the distinction between what was implemented, what was observed, and what is still only a possibility.

---

## Links

- GitHub: [@gatchimuchio](https://github.com/gatchimuchio)
- MINIDORA: [gatchimuchio/NOTNN-LLM-MINIDORA](https://github.com/gatchimuchio/NOTNN-LLM-MINIDORA)
- LLM Constitutive Specification: [gatchimuchio/LLM-Constitutive-Specification](https://github.com/gatchimuchio/LLM-Constitutive-Specification)
- Cognitive Engineering Foundations: [gatchimuchio/cognitive-engineering-foundations](https://github.com/gatchimuchio/cognitive-engineering-foundations)
- Project ORCHID: [DigitalServerHost/ORCHID](https://github.com/DigitalServerHost/ORCHID)
- GUI Shell: [gatchimuchio/GUI-Shell](https://github.com/gatchimuchio/GUI-Shell)
- BLUE-TANUKI: [gatchimuchio/blue-tanuki](https://github.com/gatchimuchio/blue-tanuki)
