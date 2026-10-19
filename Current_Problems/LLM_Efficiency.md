# Language Intelligence — First-Principles Possibility Landscape

RSM synthesis · Current architectural understanding · Conditional research map

## I. The fundamental objective

Determine the smallest economically sufficient system that can acquire, apply, retain, and revise broadly transferable linguistic competence.

Neither terabytes of training text nor trillions of neural parameters are established necessities. Equally, their avoidability at equivalent competence and total cost is unproven.

[RSM-02.09–02.11] The target is sufficient adaptive competence, not minimum model size in isolation.

## II. The irreducible functional problems

These are obligations, not necessarily separate modules.

| Problem             | Fundamental question                                                          | Principal obstruction                                     |
| ------------------- | ----------------------------------------------------------------------------- | --------------------------------------------------------- |
| Q0 — Capability     | What behaviors, breadth, reliability, and adaptation must the system exhibit? | No meaningful minimum exists without a specified target   |
| Q1 — Acquisition    | How can limited experience yield broadly reusable competence?                 | Inductive bias, identifiability, sample complexity        |
| Q2 — Representation | What distinctions and relationships must internal states preserve?            | Compression can erase future-relevant information         |
| Q3 — Execution      | How can learned competence solve unfamiliar problems?                         | Expressivity ≠ reliable inference ≠ efficient computation |
| Q4 — Persistence    | How should experience be retained, revised, or discarded?                     | Finite memory, interference, uncertain relevance          |

[RSM-03.03–03.08] These five questions survive abstraction because each imposes a distinct constraint. Verification and uncertainty management apply throughout.

## III. The principal architectural possibility space

| Dimension      | Competing realizations                                       | Critical trade-off                                            |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------- |
| Knowledge      | Parametric ↔ external ↔ hybrid                               | Integration and retrieval versus stored capacity              |
| Computation    | Prelearned responses ↔ adaptive inference                    | Model size versus latency and execution cost                  |
| Representation | Distributed ↔ structured ↔ hybrid                            | Flexibility versus systematic generalization                  |
| State          | Full-history access ↔ compressed predictive state            | Fidelity versus memory and computation                        |
| Learning       | Passive pretraining ↔ active experience ↔ continual learning | Information efficiency versus interaction and interference    |
| Organization   | Shared dense computation ↔ conditional specialization        | Sharing and transfer versus interference and routing overhead |

[RSM-04.02–04.03, RSM-07.01] These are available design choices, not components to accumulate. An implementation earns its place only by overcoming a demonstrated obstruction.

## IV. What we can already certify

| ID | Conclusion                                                                                                                 | Status                                               |
| -- | -------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| C1 | Broad language competence has no established trillion-parameter lower bound                                                | Established absence of such a proof                  |
| C2 | Arbitrarily growing independent information cannot be exactly retained in bounded total memory                             | Mathematical                                         |
| C3 | Parameters, data, external memory, and inference computation can substitute for one another in some regimes                | Empirical, conditional                               |
| C4 | Compact representation does not imply economical acquisition                                                               | Fundamental distinction                              |
| C5 | Compositional generalization depends on learned structure and its reliable deployment, not merely theoretical expressivity | Empirically supported                                |
| C6 | No single compressed state is sufficient for every conceivable future question                                             | Mathematical, under unrestricted information demands |
| C7 | A compact, general, lifelong language learner is possible at practical cost                                                | Unresolved                                           |

[RSM-01.04, RSM-04.09] Possibility, necessity, empirical success, and optimality are not interchangeable.

## V. The three remaining architecture-changing forks

## F1

Is general competence intrinsically compact?

A relatively small common set of reusable operations versus extensive irreducible specialization.

Changes: the plausible minimum computational core.

## F2

Can that competence be acquired economically?

Efficient discovery from informative experience versus prohibitively difficult learning, even when compact solutions exist.

Changes: training architecture, inductive biases, and experience requirements.

## F3

How separable are competence and accumulated knowledge?

Relatively stable reusable operations with independently accessible evidence versus knowledge deeply constitutive of the operations themselves.

Changes: whether external memory can substantially reduce the neural core.

[RSM-02.05, RSM-05.02] These forks remain open because different answers would meaningfully alter the architecture. Most narrower questions no longer qualify.

## VI. Resource landscape

The system's economic adequacy depends jointly on:

\\[ \boxed{ \begin{aligned} &\text{Acquisition information and computation}\\\ &+\ \text{Stored parameters and persistent memory}\\\ &+\ \text{Inference and retrieval computation}\\\ &+\ \text{Verification, adaptation, and maintenance}. \end{aligned} } \\]

These are resource categories, not directly additive numerical units until an accounting basis is chosen.

Three distinct minima matter:

- Minimum executor: smallest mechanism that can perform the required operations.
- Minimum learner: smallest economically trainable mechanism that can acquire them.
- Minimum lifelong system: smallest sustainable arrangement under accumulating experience and changing tasks.

[RSM-03.02, RSM-09.I.01] Savings in one category must not conceal costs transferred elsewhere.

## VII. Investigation boundaries

[RSM-04.07, RSM-07.02] — Closed at parent-sufficient resolution:

| Subproblem                    | Retained result                                                |
| ----------------------------- | -------------------------------------------------------------- |
| Transformer versus recurrence | Implementation-dependent memory and computation trade-offs     |
| Latent versus token reasoning | Intermediate computation need not use surface language         |
| Explicit modularity           | Functional reuse matters; physical separation remains optional |
| Factual memorization          | Arbitrary information must be stored somewhere                 |
| Test-time search              | Sometimes substitutes for learned capacity, not universally    |
| Curriculum and data selection | Information value varies by experience                         |
| Continual-learning mechanisms | Stability–plasticity trade-offs must be managed                |

Reopen only when a concrete capability failure or resource constraint makes the distinction consequential.

## VIII. The resulting architectural hypothesis

[RSM-04.02, RSM-07.01]

A plausible, deliberately minimal system consists of:

A reusable adaptive computational core, with task-conditioned working state, permitted access to persistent evidence, and additional computation or interaction when necessary.

No separate symbolic engine, world-model network, expert hierarchy, or consolidation system is presently justified as universally mandatory.

This is a candidate architecture, not a certified optimum.

### Final research position

The foundational map is sufficiently developed to stop expanding it. We have identified the necessary functional problems, the independent resource trade-offs, the information-theoretic constraints, and the three unresolved forks that could alter the architectural direction.

The most consequential remaining uncertainty is whether broadly transferable competence can be both compactly represented and economically acquired.

Everything more specific—attention mechanisms, curricula, memory algorithms, latent computations, parameter allocations—should now be investigated only when it resolves one of those forks or a demonstrated failure of the eventual system.

[RSM-04.07, RSM-10.13] — Stop certificate: The landscape is ready for future navigation. Further general decomposition is unlikely to improve the architectural decision without new discriminating evidence.