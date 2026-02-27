# Dependency Ecosystem Cascade and Adversarial Dynamics Engine (DECADE)

DECADE is a **controlled experimental lab** for studying cascade and robustness in open-source dependency networks. The sandbox is not the primary contribution—it enables it. The **real contribution** is answering precise, testable research questions by comparing policies, topologies, and robustness regimes in a reproducible way.

All dynamics are abstract and sandboxed. No real exploit logic or vulnerabilities are included.

---

## Contribution

* **Primary:** A small set of **precise, testable research questions** about dependency-network resilience (e.g. effect of topology on cascade size, relative performance of defensive policies, sensitivity to propagation parameters).
* **Method:** Use the sandbox to **compare** defensive policies, graph topologies, or robustness regimes under controlled conditions.
* **Standards:** **Clear baselines** (e.g. random, degree-based, centrality-based), **statistical evaluation** (confidence intervals, significance tests), **reproducibility** (seeds, configs, data versions), and **sensitivity analysis** (varying key parameters).

Infrastructure supports the experiments; **analysis and findings** are prioritized over building a large platform.

---

## Sandbox (Lab)

The environment is a **minimal, interpretable** simulation:

* **Graph:** Dependency graph (real or synthetic); nodes = packages, edges = depends-on.
* **Infection dynamics:** Simple, interpretable propagation (e.g. probabilistic spread along edges; no complex multi-step exploits).
* **Intervention:** Defensive actions (e.g. patch, audit) with a fixed budget; attack can be fixed scenarios or simple rule-based policies to keep the focus on comparing **defense** and **structure**.

The lab is kept **simple** to avoid overengineering and to make cause-and-effect clear. Multi-agent RL or co-evolution are **not** required for the core contribution; the emphasis is on **comparative experiments** (e.g. Policy A vs Policy B, Topology X vs Y, high vs low propagation rate).

---

## Research Focus

* Compare **defensive policies** (e.g. degree-based vs centrality-based vs learned) on cascade size and recovery.
* Compare **topologies** (e.g. real npm/PyPI subgraphs vs randomized or modular variants) for robustness.
* Compare **robustness regimes** (e.g. propagation rate, budget, seed set) and report sensitivity.
* **Baselines:** Always include simple, interpretable baselines (random, degree, centrality).
* **Evaluation:** Statistical reporting (e.g. mean ± CI, significance), multiple seeds, and sensitivity over key parameters.
* **Reproducibility:** Fixed seeds, versioned configs and data, and documented sensitivity analyses.

---

## Design Philosophy

* **Analysis over infrastructure** — Build only what is needed to run the comparisons.
* **Reproducibility first** — Seeds, configs, and sensitivity plans from the start.
* **Simple, interpretable dynamics** — Easy to explain and to vary for sensitivity.
* **Baselines and statistics** — Every claim supported by baselines and proper evaluation.
* **Safe by construction** — Abstract dynamics only; no real vulnerabilities or exploit logic.

---

## Safety and Scope

DECADE is a research lab only.

* No real vulnerabilities are modeled.
* No exploit primitives are implemented.
* No actionable attack logic is included.

All dynamics are abstract and intended for resilience and robustness research.

---

## License

MIT License
