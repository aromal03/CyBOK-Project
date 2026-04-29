# Educator Guidance Notes

A teaching companion to the **Risk and Reliability Analysis: FTA, ETA, and Bayesian Networks** notebook collection. This document is written for instructors, lab tutors, and self-directed learners who want to use the repository as the basis of a course module, lab series, or seminar.

---

## 1. Overview

The repository contains 12 Jupyter notebooks organized into three classical risk-analysis methodologies: Fault Tree Analysis (FTA), Event Tree Analysis (ETA), and Bayesian Networks (BN). Each methodology is presented at increasing levels of complexity and applied to different industrial, cyber-physical, and safety-critical case studies.

The collection is intentionally cross-domain: the same techniques are applied to chemical plants, autonomous vehicles, smart hospitals, water-treatment plants, infusion pumps, oil pipelines, railway signalling, and smart power grids. This makes the material suitable for engineering, safety-science, computer-science, and interdisciplinary courses.

---

## 2. Prerequisites

### 2.1 Conceptual prerequisites

Before working through these notebooks, students should be comfortable with:

- **Probability fundamentals.** Sample spaces, independence, conditional probability, and Bayes' theorem at an introductory undergraduate level.
- **Boolean logic.** AND, OR, and NOT operations, truth tables, and basic Boolean simplification (helpful for FTA cut-set reduction).
- **Set theory.** Unions, intersections, and complements (used implicitly in cut-set analysis and conditional probability).
- **Graph theory basics.** Nodes and edges, directed graphs, paths, and cycles. A formal course in graph theory is not required.
- **Reliability concepts (helpful, not required).** Failure modes, safety barriers, defense-in-depth, and the difference between hazard, risk, and consequence.

For the Bayesian Network notebooks specifically, students benefit from a brief introduction to:

- Joint and marginal distributions over discrete variables
- The chain rule of probability
- Conditional independence

### 2.2 Programming prerequisites

- Working knowledge of **Python 3** (functions, classes, lists, dictionaries, basic NumPy / pandas).
- Familiarity with **Jupyter notebooks** (running cells, restarting kernels, viewing matplotlib output).
- No prior exposure to `pgmpy`, `graphviz`, `networkx`, or `pfta` is required — the notebooks introduce them inline.

### 2.3 Technical setup

- Python 3.9 or newer
- Jupyter Notebook, JupyterLab, or Google Colab
- The system Graphviz binary (required for FTA / ETA diagrams to render)
- All Python dependencies via `pip install -r requirements.txt`

If running in Google Colab, no local setup is needed — every notebook installs its own Python dependencies in the first cell.

---

## 3. Learning Objectives

By the end of the module, students should be able to:

1. Explain the conceptual difference between deductive (FTA), inductive (ETA), and probabilistic-graphical (BN) approaches.
2. Construct a fault tree from a system description, identify minimal cut sets, and compute top-event probability.
3. Construct an event tree from an initiating event, enumerate end-state paths, and compute path and outcome probabilities.
4. Construct a Bayesian Network, define conditional probability tables, and perform forward (predictive) and backward (diagnostic) inference.
5. Critically compare the three methods, recognising where each is most appropriate and where their assumptions can be violated.
6. Apply the methods to a novel cyber-physical or safety-critical case study, including communicating results to a non-specialist audience.

---

## 4. Suggested Teaching Pathways

The notebooks support several different course shapes. Pick the pathway that matches your contact hours and audience.

### Pathway A — Single-semester full module (10–12 weeks, 2–3 hours/week)

Recommended for undergraduate or postgraduate courses on system safety, reliability engineering, or risk analysis.

| Week | Focus | Notebooks |
|---|---|---|
| 1 | Course intro, probability and reliability refresher | (none — lecture only) |
| 2 | Fault Tree fundamentals | `FTA_Simple_Autonomous_Vehicle.ipynb` |
| 3 | FTA — medium complexity, gates and cut sets | `FTA_mediumlevel_case_study.ipynb` |
| 4 | FTA — complex case study, common-cause failures | `FTA_Chemical plant_casestudy.ipynb` |
| 5 | FTA libraries and reproducible analysis | `FTA_Library_Autonomous_Vehicle_.ipynb`, `FTA_library_Smart_Infusion_Pump.ipynb` |
| 6 | Event Tree fundamentals | `ETA_Railway_Signal_Failure.ipynb` |
| 7 | ETA — medium complexity, cyber-induced events | `ETA_mediumlevel.ipynb` |
| 8 | ETA — complex case study, defense-in-depth | `ETA_complexlevel.ipynb` |
| 9 | Bayesian Networks — structure and CPTs | `BN_Smart_Hospital.ipynb` |
| 10 | BN — inference and what-if reasoning | `BN_Smart_Water_Treatment.ipynb` |
| 11 | BN — complex cyber-physical case study | `BNComplexlevel.ipynb` |
| 12 | Comparative critique, group project presentations | (student work) |

### Pathway B — Short course or workshop (4–5 sessions)

Recommended for industry training, intensive workshops, or a self-contained module within a broader safety-engineering course.

| Session | Theme | Notebooks |
|---|---|---|
| 1 | FTA — concepts and one example | `FTA_Simple_Autonomous_Vehicle.ipynb` |
| 2 | ETA — concepts and one example | `ETA_Railway_Signal_Failure.ipynb` |
| 3 | Bayesian Networks — concepts and one example | `BN_Smart_Hospital.ipynb` |
| 4 | Complex case-study comparison: chemical plant via FTA, ETA, and BN | `FTA_Chemical plant_casestudy.ipynb`, `ETA_complexlevel.ipynb`, `BNComplexlevel.ipynb` |
| 5 (optional) | Hands-on lab: students apply one method to a new system | (student work) |

### Pathway C — Domain-focused stream (cyber-physical safety)

Recommended for courses on industrial control system security, cyber-physical safety, or critical infrastructure protection.

1. `BN_Smart_Hospital.ipynb` — sensor and network failure leading to patient risk
2. `BN_Smart_Water_Treatment.ipynb` — cyber-safety in critical infrastructure
3. `ETA_complexlevel.ipynb` — cyber-induced failure in a smart substation
4. `FTA_Library_Chemical_Plant_.ipynb` — chemical plant cybersecurity-safety failure
5. `BNComplexlevel.ipynb` — cyber-physical risk in chemical processing

This stream emphasises how cyber threats interact with classical safety analysis.

### Pathway D — Self-study / flipped classroom

For learners working alone, follow each methodology in its complexity ladder before moving to the next:

1. **FTA** — Simple → Medium → Complex → Library versions
2. **ETA** — Railway (simple) → Oil Pipeline (medium) → Power Grid (complex)
3. **BN** — Smart Hospital → Water Treatment → Chemical Plant

End each block with a one-page reflection: *what would change if I applied a different method to the same system?*

---

## 5. Notebook-by-Notebook Teaching Notes

Each notebook is designed to be self-contained, but the points below highlight specific items to emphasise in class.

### Fault Tree Analysis

**`FTA_Simple_Autonomous_Vehicle.ipynb`** — Use this as the first FTA exposure. Emphasise: top event identification, decomposition into gates, and the meaning of basic versus intermediate events. Pause at the gate-evaluation step to manually verify a calculation.

**`FTA_mediumlevel_case_study.ipynb`** — Introduces a richer tree using `networkx` for layout. Good moment to discuss minimal cut sets and importance measures (Birnbaum and Fussell-Vesely if covered in lecture).

**`FTA_Chemical plant_casestudy.ipynb`** — Most detailed FTA in the collection. Useful for highlighting common-cause failures and the limits of independence assumptions.

**FTA library notebooks (`FTA_Library_*.ipynb`)** — Compare the from-scratch implementation with the `pfta` library. Discussion prompt: *what are the benefits and risks of relying on a library for safety-critical analysis?*

### Event Tree Analysis

**`ETA_Railway_Signal_Failure.ipynb`** — Excellent first ETA. Emphasise the difference between the initiating event and the consequences, and how each barrier branches the tree. Have students count paths before running the code.

**`ETA_mediumlevel.ipynb`** — Cyber-induced valve-control failure on an oil pipeline. Good for discussing how an initiating event can be either an accidental or adversarial trigger.

**`ETA_complexlevel.ipynb`** — Six-layer defense-in-depth in a smart power-grid substation. Use this notebook to discuss layered protection, residual risk, and the value of human-in-the-loop barriers.

### Bayesian Networks

**`BN_Smart_Hospital.ipynb`** — Smallest BN in the set; ideal for first exposure. Emphasise: prior probabilities for root nodes, CPTs for child nodes, and how evidence updates downstream beliefs.

**`BN_Smart_Water_Treatment.ipynb`** — Larger BN with more variables. Useful for showing how the joint distribution factors over the DAG, and for introducing diagnostic queries (P(cause | observed effect)).

**`BNComplexlevel.ipynb`** — Eight nodes, ten edges, multiple inference queries. Emphasise the *explaining away* effect when conditioning on a collider, and the practical challenge of populating CPTs from limited data or expert judgement.

---

## 6. Integration Suggestions

### 6.1 Integrating into existing courses

- **Reliability engineering / system safety.** Drop in the FTA stream alongside lectures on RBDs and Markov models. The notebooks complement traditional textbook treatments by showing how analysis scales with system complexity.
- **Probabilistic risk assessment.** Use FTA + ETA + BN together to mirror the structure of an integrated PRA. The chemical-plant case studies appear across all three methodologies, enabling a direct comparison.
- **Industrial control systems / cyber-physical security.** The cyber-induced case studies (smart substation, valve control, water treatment, smart hospital) make excellent labs for ICS security courses.
- **Data science and probabilistic modelling.** The Bayesian Network notebooks introduce `pgmpy` and inference algorithms (variable elimination) in a concrete setting, which works well in applied probability or graphical models courses.
- **Software engineering for safety-critical systems.** Use the *library vs. from-scratch* FTA notebooks to discuss verification, reproducibility, and trust in third-party safety tooling.

### 6.2 Assessment ideas

- **Notebook walk-through (formative).** Ask students to annotate one notebook with a one-paragraph explanation of each block.
- **Replication exercise (formative).** Provide a system description and ask students to reproduce one of the existing notebooks from scratch, or modify barrier probabilities and re-run the analysis.
- **Method-transfer assignment (summative).** Pick one case study (e.g., the chemical plant) and ask students to apply the OTHER two methods to it. Compare assumptions, results, and ease of communication.
- **Open-ended project (summative).** Students choose their own cyber-physical or safety-critical system and produce a notebook applying at least one of the three methods. Mark on technical correctness, justification of probability values, and clarity of the visual output.
- **Critical-comparison essay.** A 1,500-word essay comparing FTA, ETA, and BN on a system of the student's choice, drawing on the worked examples in the repository.

### 6.3 Discussion prompts

Use these to provoke seminar discussion or as short-answer exam questions:

1. *Where do the probabilities used in these notebooks come from in the real world, and how should an engineer defend them?*
2. *Common-cause failure can break the independence assumption that FTA, ETA, and BN all rely on in different ways. How does each method handle (or fail to handle) it?*
3. *In the smart-substation ETA, the catastrophic-failure probability drops below 0.01 only when several barriers are present. Is this an argument for or against defense-in-depth in your view, and why?*
4. *Bayesian Networks can be used both predictively (forward) and diagnostically (backward). Give a real-world example where each direction would be more valuable.*
5. *If you had to choose ONE method to present to a non-technical executive board, which would you choose and why?*

### 6.4 Common student misconceptions and pitfalls

- **Confusing OR-gate addition with the exact union formula.** P(A) + P(B) is a rare-event approximation, not the exact value. Reinforce this on the small-numbers FTA examples.
- **Treating the initiating event probability and the path probabilities as the same thing.** ETA paths are conditional on the initiating event having occurred.
- **Assuming barrier independence when barriers share components or operators.** Walk through the chemical-plant and substation examples explicitly.
- **Forgetting that BN edges encode conditional independence, not causation in a strict sense.** The graph reflects modelling choices.
- **Reading off probabilities from a BN without checking that the model has been validated** (`model.check_model()` in pgmpy).

### 6.5 Suggested extensions and projects

- **Sensitivity analysis.** Vary each barrier or basic-event probability over a range and plot the effect on the top-level outcome.
- **Cut-set ranking.** Add code to rank minimal cut sets by probability and discuss which contribute most to risk.
- **Bow-tie analysis.** Combine an FTA notebook (causes) with an ETA notebook (consequences) for the same top event, producing an integrated bow-tie diagram.
- **Parameter learning.** Extend a BN notebook to learn CPTs from synthetic data using `pgmpy`'s estimators rather than fixed expert values.
- **Comparative dashboard.** Build a small Streamlit or Voila dashboard that lets users adjust input probabilities and see the effect on all three methods simultaneously.
- **Cyber-attack modelling.** Add an attack-tree layer above an FTA, or extend a BN with an explicit `AttackerCapability` node, and discuss the risk-management implications.

---

## 7. Practical Tips for Running the Notebooks in Class

- **Pre-flight check.** Before a teaching session, run all notebooks end-to-end on the lab environment. Graphviz installation issues are the most common cause of failed lab demos.
- **Colab fallback.** Keep a Colab link ready; this avoids local-environment debugging if a student's machine misbehaves.
- **Slow the rendering.** When demonstrating visualisations live, walk through one or two paths or branches manually before the diagram renders, so students predict the output before seeing it.
- **Print intermediate tables.** Encourage students to display the barrier table, cut-set table, or CPT inline. Reading these tables is a learnable skill.
- **Pair-work for case studies.** The medium and complex notebooks are long enough that pair-programming or small-group work usually produces deeper engagement than solo runs.

---

## 8. Further Reading

For instructors who would like to recommend background or follow-up reading:

- *Reliability Engineering and Risk Analysis* — Modarres, Kaminskiy, Krivtsov
- *Probabilistic Risk Assessment and Management for Engineers and Scientists* — Kumamoto, Henley
- *Probabilistic Graphical Models: Principles and Techniques* — Koller and Friedman
- *Bayesian Networks and Decision Graphs* — Jensen and Nielsen
- IAEA and US NRC technical reports on PRA (freely available online) for industrial-scale worked examples

---

## 9. Feedback and Contributions

If you adapt this material for teaching, contributions back to the repository — additional case studies, clarifying comments, alternative parameter values, classroom exercises, or translated notebook commentary — are very welcome via pull request.

For corrections or questions, open a GitHub issue on the repository.
