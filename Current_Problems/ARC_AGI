# RSM Investigation VI — Minimal Intelligence for ARC-AGI

Changing the target from language modeling to ARC-AGI makes the problem substantially sharper. We can discard many obligations associated with linguistic fluency, encyclopedic knowledge, and open-ended communication.

But we should not immediately design an ARC solver. We must first determine which form of intelligence ARC actually demands, and whether its different benchmark versions impose different fundamental requirements.

[RSM-02.09–02.11] — Recover the parent objective: Find the smallest system capable of efficiently acquiring unfamiliar abstract rules and using them to solve new problems, rather than the smallest model that achieves a particular leaderboard score through arbitrary specialization.

## 1. ARC-AGI is now two importantly different problems

[ARC-AGI-2 A New Challenge for Frontier AI Reasoning Systems | ARC Prize](https://images.openai.com/static-rsc-4/X6o0av3sxl1QRd334gq-IoZ_LhXt1jogi3ADnVQtEcKguzTTfGDgpCZMpCJ076K_zI5C-t_bRFKzXW6ZT-pTCm5WBS4haOaHVIsFUhsdC359tX1zGdz1umnYWG9mXgf9tqcYTyLhMvN8Yor_VfGPWEkObmtoIpYVWTZLubqfOFI?purpose=inline)

ARC-AGI-2

Given a few input-output grids, infer a rule that applies to unseen grids.

Primary challenge: inference from sparse demonstrations.

[ARC-AGI-3](https://images.openai.com/static-rsc-4/o199Ypax68-GlWuyQTvnl0IoFANa9ZRHTf8vPyQvfG7cxeQhWfq8cjjmLKY4EtX2BKb2CHhhvvesaxzdDqvqcp1YLAb3rbdZ--R4-MDi64ufRFoa5RqwYLqHhJOnzDa1Rl7RZAA8tdPT35qXmvGl5A-ppvQLR3SbW7iZo2c6LA0?purpose=inline)

ARC-AGI-3

Enter an unfamiliar environment without explicit instructions, discover its mechanics and goals, and act efficiently.

Primary challenge: learning through interaction and planning.

ARC-AGI-2 explicitly emphasizes symbolic interpretation, composition, and context-dependent rules. ARC-AGI-3 adds exploration, goal discovery, action selection, and continued adaptation.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://arcprize.org\&sz=32)

ARC Prize

+1



[RSM-03.03] — Factor the two tasks: ARC-AGI-2 is largely an inverse-model problem; ARC-AGI-3 adds a sequential intervention problem. Their common foundation matters more than their superficial similarities.

## 2. The minimal shared problem

For ARC-AGI-2, we observe examples:

\\[ D=\\{(x_i,y_i)\\}\_{i=1}^k \\]

and must find a transformation \\(h\\) consistent with them and appropriate for a new input.

For ARC-AGI-3, the learner encounters observations \\(o_t\\), takes actions \\(a_t\\), and observes consequences. It must infer both aspects of the environment and what constitutes progress.

Both can be expressed as:

> Infer useful structure from limited evidence, distinguish plausible alternatives, and exploit the resulting structure to produce correct outcomes efficiently.

This is the common parent problem.

[RSM-04.02–04.04] Both require discovering possible models and evaluating their consequences. ARC-AGI-3 additionally permits actions intended to distinguish models; static ARC usually does not.

This does not prove that one solver architecture is optimal for both.

## 3. Derive the minimal functional architecture

[RSM-04.02, RSM-07.01] — Work backward from necessary capabilities; do not equate a capability with a separate module.

| Functional obligation         | ARC-AGI-2                                                           | ARC-AGI-3                                                  |
| ----------------------------- | ------------------------------------------------------------------- | ---------------------------------------------------------- |
| Perception and representation | Identify objects, regions, relations, and relevant visual structure | Identify state variables, objects, dynamics, and changes   |
| Hypothesis construction       | Propose transformations explaining examples                         | Propose environment mechanics and possible goals           |
| Hypothesis evaluation         | Check candidate rules against demonstrations                        | Compare predictions against observed consequences          |
| Selection under uncertainty   | Choose an output despite underdetermination                         | Choose informative actions and goal-directed interventions |
| Adaptation                    | Revise the inferred transformation within a task                    | Update beliefs and policies throughout an episode          |

The common computational abstraction is:

\\[ \boxed{ \text{Represent} \rightarrow \text{Hypothesize} \rightarrow \text{Test} \rightarrow \text{Revise} \rightarrow \text{Apply} } \\]

This is a functional cycle, not five engines.

For ARC-AGI-3, test can involve taking an action that changes the environment. For ARC-AGI-2, it ordinarily means testing a hypothesis against fixed demonstration pairs.

### Is a large pretrained model necessary?

There is already strong evidence against treating large-scale pretraining as a necessary property of an ARC solver.

The ARC Prize 2025 report identifies iterative program refinement as a leading approach. It also documents the Tiny Recursive Model: roughly 7 million parameters, no conventional large-scale pretraining, and approximately 45% on ARC-AGI-1 but only 8% on ARC-AGI-2.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://arxiv.org\&sz=32)

arXiv

+1



The important distinction is that small models can solve substantial subsets of ARC, but the evidence does not establish that a small general solver can cover the full distribution.

[RSM-01.04] — Certificate ARC-C01: Billion-parameter pretraining is not necessary to solve meaningful subsets of ARC. Whether it can be eliminated while retaining near-human coverage and efficiency is unresolved.

## 4. The three architecture-changing forks

[RSM-02.05, RSM-05.02] — Retain questions whose answers could change the system's fundamental organization.

## F1

What is the smallest useful hypothesis language?

Can a compact collection of transformations, relations, and compositions express nearly all task-relevant rules? Or is open-ended invention of new abstractions indispensable?

Consequences: fixed program search versus systems that can construct new representations or operators.

## F2

How does the solver discover the relevant hypothesis efficiently?

Can structural constraints, abstraction, and systematic search narrow the candidates sufficiently? Or is learned intuition essential to orient the search?

Consequences: whether substantial pretrained knowledge is helpful, unnecessary, or indispensable for efficient coverage.

## F3

When does passive inference cease to be sufficient?

For interactive ARC, how does the system identify useful experiments, infer hidden goals, and plan under uncertain dynamics?

Consequences: whether a common static hypothesis engine can be extended with action selection or whether fundamentally different mechanisms become necessary.

F1 and F2 matter for both static and interactive ARC. F3 primarily distinguishes ARC-AGI-3.

## 5. Where the problem is likely to be hardest

[RSM-03.07, RSM-04.09] — Isolate consequential obstructions rather than listing algorithms.

The difficulty is not merely finding a rule consistent with the demonstrations.

There may be many such rules.

The hard problem is selecting the one that appropriately generalizes to an unfamiliar input.

For example, both of these may fit two examples:

- Transform the largest connected object.
- Transform the object having a particular relationship to another object.

The difference only becomes visible when object size and relational role diverge.

Thus a solver needs some inductive preference or additional evidence. Exact consistency alone does not identify the intended transformation.

This leads to three persistent obstructions:

1. Representation failure: the appropriate concept is absent from the candidate descriptions.
2. Search failure: the correct concept is expressible but too expensive to find.
3. Identification failure: several candidate concepts fit available observations yet differ on the test case.

These are not interchangeable.

For ARC-AGI-3, a fourth appears: experimental and planning failure—the agent has opportunities to collect information but cannot select or exploit them efficiently.

Certificate ARC-C02: The distinction between representation, search, identification, and interactive experimentation is sufficient to organize most major ARC solver failures at the parent level. Specific algorithms should be investigated only after identifying which obstruction they address.

## 6. A minimal candidate system

[RSM-07.01–07.02] — Architectural parsimony.

The smallest credible starting hypothesis is:

> A compact, revisable representation of the environment; a means of generating candidate transformations or dynamics; a mechanism for evaluating them against evidence; and a policy for selecting the next prediction or action.

That may be implemented by program synthesis, a small recurrent network, a learned proposal model, or combinations of these.

I would not initially require a large language model, multi-agent architecture, enormous learned world model, or general-purpose symbolic theorem prover.

Equally, I would not insist that the solver be purely symbolic. Fixed symbolic languages can fail precisely when ARC demands a representation absent from the designer's primitive vocabulary.

### What has changed from our language-model investigation?

For language models, we had to account for vast accumulated knowledge, linguistic conventions, and continually changing information.

ARC eliminates much of that burden and concentrates the problem on rapid structural inference under very limited evidence.

That makes ARC a more useful experimental setting for investigating whether compact intelligent mechanisms can replace massive pretraining.

However, success on ARC would establish competence within that benchmark family, not a complete theory of general intelligence.

## 7. Where I would investigate next—and where I would stop

[RSM-02.05, RSM-04.07, RSM-08.07] — Choose consequential experiments and stop at parent-sufficient resolution.

I would begin with ARC-AGI-2 because it isolates abstraction and hypothesis discovery without confounding them with interactive exploration and goal discovery.

The most valuable investigation would be an empirical failure decomposition using actual ARC tasks:

| Outcome                                                                                      | What it tells us                                                         |
| -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| A compact hypothesis language can express nearly every solution, but search is too expensive | Prioritize efficient hypothesis discovery                                |
| Many tasks require concepts outside the available language                                   | Prioritize representation invention                                      |
| Multiple hypotheses remain indistinguishable from demonstrations                             | Investigate inductive bias and ambiguity rather than adding brute force  |
| A compact solver covers most tasks efficiently                                               | Strong evidence against large model size being necessary for this target |

A critical precaution is that a hypothesis language must be fixed before testing on held-out tasks. Otherwise its apparent coverage may just reflect retrospective adaptation to the benchmark.

I would use the official ARC-AGI-2 training set for development, reserve evaluation tasks for genuinely held-out measurement, and compare against existing published solvers before conducting new experiments.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://github.com\&sz=32)

GitHub



Stopping criterion: Once we can reasonably characterize the achievable coverage, search complexity, and representation failures of a compact hypothesis class, stop investigating its individual primitives unless their limitations materially change the architecture.

### Provisional conclusion

The minimal-intelligence question for ARC can presently be condensed to:

How little reusable structure is sufficient for a system to invent or select the right abstraction from sparse evidence, and how efficiently can it recognize when its current abstraction is inadequate?

For ARC-AGI-2, that may be the central problem. For ARC-AGI-3, we additionally need to understand how the same process operates through active experimentation, implicit goal discovery, and long-horizon action.

[RSM-04.07] — Next decision: This new landscape is sufficiently defined to begin targeted investigation, but not yet sufficient to choose the final architecture. The first consequential uncertainty is whether a compact, extensible hypothesis language can represent the breadth of ARC-AGI-2 without being manually expanded task by task.














# RSM — Reconsidering the ARC-AGI Investigation

## 1. We were asking a prematurely architectural question

[RSM-02.03, RSM-02.09–02.11] — Audit assumptions, recover the parent purpose, and navigate upward.

Our previous question was:

> What is the smallest architecture capable of solving ARC-AGI?

This assumes three things we have not justified:

1. That solving ARC is the actual intellectual objective.
2. That a minimal architecture is the right object of investigation.
3. That ARC performance tells us which mechanism of intelligence a system possesses.

The third is particularly dangerous. A specialized solver could achieve excellent ARC performance through an enormous hand-engineered library of transformations. That would demonstrate engineering success, but not necessarily the kind of adaptive intelligence we are investigating.

Conversely, a remarkably general learning mechanism might perform poorly on ARC because its visual priors are insufficient.

The distinction between acquired skill and skill-acquisition efficiency is central to ARC's original motivation. Chollet's 2019 formulation explicitly conditions intelligence on prior knowledge, experience, generalization difficulty, and task scope.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://arxiv.org\&sz=32)

arXiv

+1



Our previous formulation risks confusing the benchmark with the underlying phenomenon.

## 2. Recover the actual family of questions

[RSM-02.09, RSM-02.12] — Investigate neighboring questions that could change the objective.

I see four possible intellectual objectives.

| Candidate purpose            | Actual question                                                                  | What changes                                                      |
| ---------------------------- | -------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| A. Benchmark achievement     | What system solves ARC most efficiently?                                         | Optimizes coverage and computational cost                         |
| B. Minimal intelligence      | What is the smallest reusable mechanism capable of acquiring unfamiliar skills?  | Investigates cognitive necessities                                |
| C. Origin of abstraction     | How does a learner construct new useful representations from limited experience? | Investigates learning mechanisms                                  |
| D. Generalization beyond ARC | Which discoveries transfer to qualitatively different problem families?          | Tests whether an apparent intelligence mechanism is truly general |

These are connected, but not equivalent.

My interpretation is that B is your central purpose, C is a major obstacle to it, D is its necessary external validity check, and A is an experimental instrument.

That interpretation fits the progression from investigating minimal language intelligence to ARC, without treating benchmark accuracy as the final intellectual goal.

### The better parent question

> What is the minimal organization of prior structure, experience, and computation that allows a system to acquire unfamiliar capabilities efficiently across a broad family of problems?

Notice what this removes.

We are no longer committed to neural networks, program synthesis, preselected object representations, or even ARC itself.

We can investigate intelligence before selecting the implementation that realizes it.

[RSM-02.10] — Backward necessity: An ARC solver is one possible implementation of the objective, not the objective itself.

## 3. A deeper correction: what counts as acquiring a new skill?

[RSM-02.03, RSM-03.03] — Challenge the assumption that unfamiliar tasks necessarily demand a new learned mechanism.

Suppose a system solves an ARC puzzle by recognizing that it needs to translate an object, recolor it, and reproduce it.

Has it learned something?

Possibly not.

It might merely have selected and composed operations that were already available.

Compare three cases:

| Case        | What occurred                                                             | What it demonstrates                    |
| ----------- | ------------------------------------------------------------------------- | --------------------------------------- |
| Selection   | Finds an appropriate existing operation                                   | Task recognition                        |
| Composition | Combines existing operations in an unfamiliar way                         | Systematic generalization               |
| Expansion   | Constructs an operation or representation that was previously unavailable | Acquisition of genuinely new capability |

There is no reason to privilege expansion automatically. An intelligent system should reuse what already works rather than invent unnecessarily.

But if the purpose is to study skill acquisition, we must distinguish these cases.

A fixed library with a sophisticated search algorithm might solve many ARC tasks without changing its underlying repertoire.

That could still demonstrate impressive generalization, but it would establish something narrower than open-ended acquisition.

Critical consequence: We should investigate not only whether the system solves unfamiliar tasks, but what changed in the system's effective abilities as a result of encountering them.

This gives us a much stronger research target than benchmark accuracy alone.

## 4. Do we even need to invent new representations?

[RSM-02.05, RSM-03.04–03.06] — Examine rival possibilities before treating representation invention as indispensable.

There are three plausible explanations for how broadly capable intelligence handles novelty.

## H1

A sufficiently expressive universal substrate

A relatively small repertoire of general operations can express extremely diverse solutions. Intelligence primarily consists of efficiently discovering their appropriate compositions.

Potential obstruction: expressibility does not imply tractable discovery.

## H2

Adaptive representation construction

Novel problems become tractable by introducing objects, relations, auxiliary variables, and effective operations that were not previously explicit.

Potential obstruction: inventing representations may merely relocate a difficult search problem.

## H3

Distributed learned intuition

A learned system develops implicit structural knowledge, enabling direct inference or guiding search without explicit symbolic representations.

Potential obstruction: expensive acquisition, unreliable transfer, and difficulty identifying what was actually learned.

These are not mutually exclusive, and hybrid systems are entirely plausible.

The important distinction is between what a system can theoretically represent and what it can economically discover.

[RSM-04.09] — Certificate: General expressivity, efficient hypothesis discovery, and adaptation to unfamiliar problem families are distinct properties. None follows automatically from another.

## 5. ARC-AGI-2 versus ARC-AGI-3: which should we actually investigate?

[RSM-02.11–02.12] — Evaluate the benchmark against the parent purpose, including complementary task conditions.

ARC-AGI-2 supplies demonstrations and requests a transformation. ARC-AGI-3 instead requires exploration of unfamiliar environments, learning their dynamics, discovering goals, and acting effectively.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://arcprize.org\&sz=32)

ARC Prize

+1



If our question is simply how to infer transformations from sparse examples, ARC-AGI-2 is an excellent environment.

If our question is how an intelligent system acquires capabilities through interaction, ARC-AGI-3 exposes more of the intended phenomenon.

But ARC-AGI-3 introduces additional variables: exploration policy, action costs, planning horizons, and implicit objectives.

We should therefore avoid selecting either benchmark as the universal target.

The better research design uses them as complementary instruments:

- ARC-AGI-2: Isolate inference, abstraction, and generalization from demonstrations.
- ARC-AGI-3: Investigate how representation and skill acquisition evolve through interventions and feedback.
- Controlled synthetic environments: Separate intrinsic limits from benchmark-specific conventions and prior knowledge.

The third is scientifically important even if it is less impressive competitively.

# 6. The critical question set

After these corrections, I would preserve just three questions at the top level.

[RSM-02.05–02.06, RSM-05.02] — Retain questions only if their possible answers change the research direction.

| ID               | Critical question                                                                                    | Consequential alternatives                                                                    |
| ---------------- | ---------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Q1 — Sufficiency | What reusable prior structure is sufficient to make broad families of unfamiliar problems tractable? | Compact universal operators versus domain-specific structures versus adaptive representations |
| Q2 — Acquisition | How can a system efficiently discover the relevant structure or capability from limited evidence?    | Search, inference, learned intuition, active experimentation, or combinations                 |
| Q3 — Transfer    | What survives when the problem family, available priors, or mode of interaction changes?             | Genuine reusable intelligence versus benchmark-specific competence                            |

These questions are intentionally not tied to ARC.

They define what ARC is supposed to help us investigate.

## 7. The investigation set that follows

[RSM-04.02–04.04, RSM-07.02] — Select investigations by their ability to distinguish competing parent-level explanations.

| Investigation                             | What it should establish                                                                                      | Why it matters                                                                         |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| I1. Prior dependence                      | How performance changes when objects, relations, transformations, and familiar conventions are varied         | Distinguishes general reasoning from hidden benchmark-specific assumptions             |
| I2. Representation versus search          | Whether failures persist despite sufficient search, or disappear after changing the representation            | Determines whether the central obstruction is expressing possibilities or finding them |
| I3. Skill acquisition versus task solving | Whether learning one unfamiliar problem improves performance on a related but distinct problem                | Distinguishes reusable learning from isolated problem solving                          |
| I4. Transfer across regimes               | Whether the same mechanism works under static demonstrations, active experimentation, and novel task families | Tests how general the proposed intelligence mechanism actually is                      |

I would not immediately implement four experiments. These are investigative obligations, and some may be settled more economically through existing literature and established systems.

### The most consequential investigation

I would prioritize I2: representation versus search, while measuring transfer in I3.

Why?

Suppose we can show that a small fixed repertoire of operations expresses a broad task family, but finding appropriate compositions is prohibitively expensive.

Then the main research problem is efficient orientation within a hypothesis space.

Alternatively, suppose even powerful search routinely fails because the relevant representation is absent.

Then improving search is secondary; the critical problem is constructing better representations.

This is a genuine architectural fork.

However, I2 must use bounded tasks with known solutions, otherwise a failure cannot be confidently attributed to representational insufficiency.

[RSM-03.07, RSM-04.07] — Stop criterion: Once we can distinguish those regimes sufficiently to select an architecture, stop refining the particular search mechanism until its costs become consequential.

## 8. The revised big picture

We can now describe the research program without presupposing its solution.

Parent purpose and investigative dependencies

## 9. What I would stop asking

[RSM-04.07, RSM-10.13] — Reject lower-level questions that cannot presently change the parent map.

I would suspend questions about the optimal ARC-specific programming language, particular visual primitives, neural-network size, beam-search variants, program-ranking heuristics, and memory mechanisms.

All may eventually matter. None should presently dictate our understanding of minimal intelligence.

I would also stop asking whether all intelligence can be reduced to abstraction, program synthesis, or world modeling. That question is too broad to discriminate realistic alternatives without defining a capability family.

### Final formulation

The strongest version of our research question is now:

> Given limited prior structure and experience, what makes a system capable of efficiently acquiring and transferring useful new abilities when confronted with unfamiliar problems?

ARC-AGI is a deliberately constrained laboratory for this question, not its definition.

[RSM-02.09, RSM-04.07] — Stopping certificate: We have corrected the parent objective, preserved the three distinctions capable of changing its interpretation, and identified four investigations that can constrain them. Further decomposition is not justified until the evidence reveals a consequential obstruction.

The next useful advance should come from distinguishing what structure the system already possesses, what it discovers during a task, and what newly acquired ability survives afterward—not from inventing an ARC solver prematurely.