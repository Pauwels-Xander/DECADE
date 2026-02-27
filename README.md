# Dependency Ecosystem Cascade and Adversarial Dynamics Engine (DECADE)
DECADE is a research sandbox for studying adversarial dynamics in open source dependency networks using graph machine learning and multi agent reinforcement learning.

The system simulates a dependency graph derived from real package ecosystems such as npm or PyPI. It provides a controlled environment for analyzing systemic fragility, cascade behavior, and defensive strategy under uncertainty.

All dynamics are abstracted and sandboxed. No real exploit logic or vulnerabilities are included.

---

## Overview

Modern software ecosystems are deeply interconnected through dependency graphs. A single compromised package can propagate across thousands of downstream systems. DECADE models this phenomenon in a fully abstracted simulation environment.

Within the environment:
* A **Red agent** attempts to maximize systemic compromise through abstract infection dynamics.
* A **Blue agent** attempts to minimize cascade impact under budget and observability constraints.

The environment captures:
* Probabilistic propagation across dependency edges
* Resource constrained defensive intervention
* Partial and noisy detection signals
* Structural network effects

---

## Core Components

### Graph-Based Environment

* Constructed from real world dependency data
* Directed dependency graph representation
* Configurable propagation dynamics

### Multi Agent Reinforcement Learning

* Red and Blue policies trained via PPO or similar algorithms
* Competitive and co-evolutionary learning setup
* Budget and action space constraints

### Graph Feature Encoding

* Node and structural features
* Optional graph neural network embeddings
* Centrality and structural importance measures

### Cascade Metrics

* Infection spread magnitude
* Time to systemic compromise
* Structural resilience indicators
* Defensive efficiency metrics

### Meta Agent Orchestration (Optional)

* OpenClaw integration
* Higher level coordination experiments

---

## Research Focus

DECADE investigates:

* Cascade dynamics under adaptive attack
* Defensive prioritization under uncertainty
* Structural changes in network topology
* Emergent resilience through adversarial co evolution
* Generalization to unseen attack distributions

The framework is designed for controlled, reproducible experimentation on systemic risk in interconnected ecosystems.

---

## Safety and Scope

DECADE is strictly a research sandbox.

* No real vulnerabilities are modeled.
* No exploit primitives are implemented.
* No actionable attack logic is included.

All attack and defense dynamics are abstract probabilistic processes intended for resilience research only.

---

## Intended Use Cases

* Academic research on network robustness
* Study of adversarial multi agent learning
* Analysis of cascade behavior in complex systems
* Experimentation with graph based reinforcement learning

---

## Design Philosophy

* Reproducibility first
* Clear separation between abstract dynamics and real world systems
* Modular components for experimentation
* Safe by construction

---

## License
MIT License

**Conclusion:** DECADE provides a controlled and extensible framework for studying adversarial cascade dynamics and resilience in dependency ecosystems without modeling real world exploits.
