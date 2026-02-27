# Project Proposal

# Adversarial Learning in Open-Source Dependency Graphs

## A Controlled-Lab Study of Cascade and Robustness in Software Ecosystems

---

## 1. Project Overview

This project builds a **minimal sandbox** that functions as a **controlled experimental lab**. The sandbox is **not** the main contribution. The **contribution** is a **precise, testable research question** (or small set of questions) about dependency-network resilience, answered by using the lab to **compare policies, topologies, or robustness regimes** with **clear baselines** and **statistical evaluation**.

* The environment is based on a dependency graph (e.g. npm or PyPI subgraph); attack and defense are **abstract** and simulated. No real vulnerabilities or exploit techniques are used.
* **Priorities:** Reproducibility, sensitivity analysis, interpretable dynamics, and **analysis over infrastructure**. Multi-agent complexity is avoided; the focus is on **comparative experiments**, not building a full attack–defense RL platform.

---

## 2. Motivation

Modern software ecosystems are large, interconnected, and often centralized. Supply-chain incidents show that compromising a few packages can affect many downstream systems. It is hard to experimentally study how propagation and defense interact, and how **structure** (topology) and **policy** (who gets patched first) affect outcomes. A small, controlled lab with **simple, interpretable** infection dynamics can support such studies without overengineering.

---

## 3. Research Contribution (Primary)

The **real contribution** is framed around **precise, testable research questions**, for example:

1. **Policy comparison:** For a given topology and propagation model, how do different **defensive policies** (e.g. random, degree-based, centrality-based, optional simple learned) compare on cascade size and time-to-recovery? With **statistical evaluation** (e.g. confidence intervals, significance tests) and **baselines**.
2. **Topology comparison:** How does **network structure** (e.g. real subgraph vs same degree-sequence randomized, or high vs low modularity) affect cascade size and the **relative** performance of defensive policies?
3. **Robustness regimes:** How **sensitive** are outcomes to propagation rate, defense budget, or initial infection set? Systematic **sensitivity analysis** is part of the contribution.

Additional questions (optional, if scope allows):

* Does the **ranking** of policies change across topologies or regimes?
* How many seeds / runs are needed for stable conclusions? (Reproducibility and power.)

**Standards for every claim:**

* **Baselines:** e.g. random intervention, degree-based, centrality-based.
* **Statistical evaluation:** multiple runs, reported uncertainty (e.g. mean ± CI), and where appropriate significance tests.
* **Reproducibility:** fixed seeds, versioned configs and data.
* **Sensitivity analysis:** vary key parameters (propagation probability, budget, graph) and report how results change.

---

## 4. Sandbox (Lab) Design

The sandbox is kept **simple and interpretable** so that cause-and-effect is clear and sensitivity analysis is tractable.

### 4.1 Graph

* **Source:** Real dependency subgraph (e.g. subset of npm or PyPI) or synthetic graph with comparable statistics.
* **Representation:** Directed graph; nodes = packages, edges = depends-on.
* **Node attributes (minimal):** e.g. infection state, patch state, optional audit level or simple “importance” (e.g. degree or centrality). Avoid unnecessary complexity.

### 4.2 Infection Dynamics (Simple and Interpretable)

* If a package is **infected**, it can **probabilistically** infect its dependents (or dependees, depending on chosen direction) in each step.
* Infection probability may depend on a **small** set of factors (e.g. patch state, one audit level). No multi-step exploit logic.
* Think **simple contagion** (e.g. SIR-like or discrete-time spread along edges). The goal is interpretability and easy parameterization for **sensitivity analysis** (e.g. varying a single propagation probability).

No real exploit logic is included.

### 4.3 Intervention and “Attack”

* **Defense:** Limited budget per step or total; actions such as “patch node X” or “raise audit level of X.” Policies to **compare** include: random, degree-based, centrality-based, and optionally one simple learned or heuristic policy.
* **Attack / initial condition:** Fixed scenarios (e.g. single seed, random set, or high-degree nodes) or **simple rule-based** strategies (e.g. “infect highest degree first”). The lab does **not** require a trained Red agent; the contribution is about **comparing defenses and topologies**, not full adversarial RL.

---

## 5. What We Do *Not* Emphasize

To keep the contribution focused and avoid overengineering:

* **Multi-agent RL / co-evolution** — Not the core. Comparison of fixed or rule-based attack scenarios with different defensive policies is sufficient for the main research questions.
* **Complex agent design** — No requirement for Red and Blue both being learned, phased training, or self-play. Optional later extension only if the core questions are answered first.
* **Heavy infrastructure** — Meta-controllers, orchestration, and large ML stacks are secondary. **Analysis, baselines, and sensitivity** come first.
* **Complicated dynamics** — Infection model stays simple and interpretable; parameters are few and explicit for sensitivity analysis.

---

## 6. Evaluation and Reproducibility

### 6.1 Metrics

* **Cascade:** e.g. total infected reach, largest infected component, time to full spread or to recovery.
* **Policy comparison:** Same scenario and topology; compare policies on cascade size and recovery time (with uncertainty).
* **Topology comparison:** Same policy and scenario; compare topologies (e.g. real vs randomized, or by modularity).
* **Sensitivity:** Vary propagation probability, budget, seed set size, or graph; report how metrics and **rankings** of policies change.

### 6.2 Baselines

* **Random** — Random choice of nodes to patch / audit.
* **Degree-based** — Prioritize by degree (in- or out-, as appropriate).
* **Centrality-based** — e.g. PageRank or betweenness; prioritize high-centrality nodes.

Any proposed policy should be compared against these.

### 6.3 Statistical Evaluation

* Multiple runs per (config, policy, topology) with **fixed seeds** and reported **mean and confidence intervals** (e.g. 95%).
* Where comparisons are made (e.g. Policy A vs B), use appropriate tests (e.g. permutation or bootstrap) and report effect size.
* Document **sensitivity**: which parameters matter most, and over what range results are stable.

### 6.4 Reproducibility

* **Seeds:** All RNG seeds fixed and recorded.
* **Configs:** Full experiment config (graph source/version, parameters, budgets) versioned and stored.
* **Data:** Graph and scenario definitions (or generators) versioned so experiments can be re-run.
* **Sensitivity plan:** Pre-specify which parameters will be varied and how, so the analysis is transparent and reproducible.

---

## 7. Expected Outcomes

The main outcomes are **answers** to the research questions, not “we built a sandbox.” Concretely:

* **Policy comparison:** Quantified comparison of defensive policies (vs baselines) on cascade size and recovery, with uncertainty and sensitivity.
* **Topology comparison:** Quantified effect of structure (e.g. modularity, randomizations) on cascade and on relative policy performance.
* **Sensitivity:** Clear reporting of how outcomes depend on propagation rate, budget, and other key parameters.
* **Reproducibility:** Artifacts (code, configs, seeds) and a sensitivity plan that allow others to reproduce and extend the experiments.

A strong result would be: “Under conditions X, policy P outperforms baselines by Y; this ranking is robust over topologies Z1, Z2 and over propagation rates in [a, b], but reverses when …” — i.e. **interpretable, testable, and reproducible** findings.

---

## 8. Ethical Considerations

* All infection dynamics are **abstract**.
* No real vulnerabilities or exploit techniques are modeled or implemented.
* The focus is **resilience and robustness research** in a simulation. This is not a security tool or attack platform.

---

## 9. Conclusion

The project provides a **minimal, interpretable sandbox** as a controlled lab. The **contribution** is a **precise, testable research question** (or small set) about dependency-network resilience, answered by **comparing policies, topologies, and robustness regimes** with **clear baselines**, **statistical evaluation**, **reproducibility**, and **sensitivity analysis**. Infection dynamics stay simple; multi-agent complexity is avoided; **analysis is prioritized over infrastructure**.
