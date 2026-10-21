# Research Decisions Log

## Project

**Working title:** A Comparative Evaluation of Layered Safety and
Rollback Mechanisms for Objective Misinterpretation in Simulated Agentic
Workflows

**Source document:** *Safety and Rollback Mechanisms for Objective
Misinterpretation in Agentic AI Systems* (uploaded DOCX, 11 pages)

**Status:** Initial planning; implementation and experiments have not
been supplied or verified.

## Evidence labels

-   **VERIFIED** --- directly supported by the supplied review or an
    inspected source.
-   **INFERRED** --- proposed interpretation, design choice, hypothesis,
    or expected outcome requiring testing.
-   **UNKNOWN** --- not established by the evidence currently available.

## Review scope

**VERIFIED:** The review discusses objective misinterpretation, reward
misspecification, unintended side effects, resource usage, unauthorized
actions, cascading errors, irreversible consequences, objective
validation, constraint-based execution, runtime monitoring, action risk
classification, checkpointing, transaction-based execution, action logs,
objective-drift detection, human-in-the-loop controls, fail-safe
stopping, and rollback limitations.

**VERIFIED:** The review proposes a five-layer model: objective
validation; permission and constraint control; runtime monitoring;
intervention; and recovery.

**VERIFIED:** The conclusion calls for further work on reliable
objective interpretation, automated goal-drift detection, formal plan
verification, scalable human oversight, and recovery in complex
environments.

**UNKNOWN:** The supplied document does not provide a runnable
implementation, experimental protocol with results, benchmark
measurements, verified baseline, or evidence that the proposed
architecture improves safety.

**UNKNOWN:** One work on constitutional approaches is cited in the main
text as reference \[7\], but is not present in the supplied numbered
reference list. Identify and verify the intended publication before
finalizing the bibliography.

## Initial research direction

**INFERRED:** Implement a sandboxed simulator for agentic workflows and
compare: 1. Unprotected execution. 2. Objective constraints and runtime
monitoring. 3. Constraints, monitoring, checkpoints, transaction-style
validation, and rollback. 4. Optional ablation configurations that
isolate individual components.

The proposed scope is deliberately bounded. Simulated results would
establish behavior only within the simulator and would not by themselves
prove general LLM intent understanding or real-world safety.

## Candidate research questions

-   **RQ1:** How does a layered safety architecture combining objective
    constraints, runtime monitoring, and checkpoint-based recovery
    affect unsafe actions, task completion, and recovery overhead in
    simulated agentic workflows?
-   **RQ2:** Which safety components contribute most to reducing unsafe
    actions?
-   **RQ3:** How accurately and quickly does runtime monitoring detect
    violations?
-   **RQ4:** How reliably can recoverable local state be restored after
    a failed or prohibited action?
-   **RQ5:** What overhead is introduced by checkpoints, validation, and
    audit logging?

## Candidate hypotheses (not results)

-   **H1 --- INFERRED:** The combined architecture will execute fewer
    prohibited actions than an unprotected baseline.
-   **H2 --- INFERRED:** Checkpointing will improve restoration
    reliability for recoverable local state.
-   **H3 --- INFERRED:** Additional safety checks will introduce
    measurable execution overhead.
-   **H4 --- INFERRED:** Local rollback alone will not reverse simulated
    external side effects unless those effects are explicitly controlled
    or compensated.

Keep these hypotheses even if results contradict them. Do not present
them as findings before experiments.

## Five candidate research gaps

### Gap 1 --- Objective constraints versus literal goal optimization

-   **Review evidence:** Sections 2 and 4.1--4.2 describe objective
    ambiguity and propose explicit goals, constraints, prohibited
    actions, and approval requirements.
-   **Reported in review:** Objective ambiguity is a safety concern;
    objective validation and constraint-based execution are proposed.
-   **Inference:** The effectiveness of a particular implemented
    validator is unmeasured in the supplied review.
-   **Experiment:** Compare identical scenarios with and without a
    constraint validator.
-   **Metrics:** Prohibited-action rate, task completion, false-block
    rate, validation latency.
-   **Evidence to collect:** Scenario definitions, ground-truth allowed
    actions, source code, test logs, results.

### Gap 2 --- Early detection of objective drift

-   **Review evidence:** Section 6 proposes comparing current behavior
    and plans with an approved objective and monitoring resources and
    system modifications.
-   **Reported in review:** Drift detection is important.
-   **Inference:** Detection accuracy, false alarms, and intervention
    timing have not been measured in the supplied review.
-   **Experiment:** Compare action-level monitoring with end-of-task
    checking.
-   **Metrics:** Detection rate, false-positive rate, unsafe actions
    executed before intervention, detection latency.
-   **Evidence to collect:** Timestamped traces, labelled violation
    points, monitor decisions, matched scenarios.

### Gap 3 --- Rollback correctness and recovery overhead

-   **Review evidence:** Section 5 discusses checkpoints,
    transaction-style execution, action logs, and restoring a prior
    state; it notes the importance of reconstructable state.
-   **Reported in review:** Rollback is a recovery layer and depends on
    recoverability.
-   **Inference:** Recovery correctness, latency, and checkpoint
    overhead are not quantified in the supplied review.
-   **Experiment:** Inject controlled failures and compare
    no-checkpoint, periodic-checkpoint, and transaction-based
    configurations.
-   **Metrics:** Restoration success, residual changes, rollback
    latency, checkpoint storage, total task time.
-   **Evidence to collect:** State snapshots, failure-injection logs,
    checkpoint configuration, repeated measurements.

### Gap 4 --- Individual safeguards versus a combined architecture

-   **Review evidence:** Sections 4 and 10--11 propose complementary
    safety layers.
-   **Reported in review:** A layered model is proposed.
-   **Inference:** The relative contribution of each layer and the
    combined benefit have not been demonstrated in the supplied review.
-   **Experiment:** Compare unprotected execution, constraints only,
    monitoring only, rollback only, and combined safeguards.
-   **Metrics:** Unsafe-action rate, task success, recovery success,
    false blocking, runtime, storage overhead.
-   **Evidence to collect:** Ablation configurations, consistent inputs,
    implementation version, complete results.

### Gap 5 --- Reversible versus irreversible actions

-   **Review evidence:** Sections 7--9 discuss external communications,
    financial transfers, physical damage, and hidden side effects that
    local rollback may not reverse.
-   **Reported in review:** Rollback has limits for irreversible or
    externally propagated consequences.
-   **Inference:** The effectiveness of a particular risk classification
    and approval policy is unmeasured.
-   **Experiment:** Compare rollback-only against risk-based approval
    plus rollback using simulated external effects.
-   **Metrics:** Unrecoverable side-effect rate, unauthorized-action
    rate, task completion, approval frequency, intervention latency.
-   **Evidence to collect:** Reversibility labels, external-state
    ledger, test traces, policy-comparison results.

## Preliminary prioritization

Assuming a Python simulator and local test execution are feasible: 1.
**Combined safety layers and ablation testing** --- high potential
significance and high implementation feasibility. 2. **Rollback
correctness and recovery overhead** --- high potential significance and
high feasibility. 3. **Objective constraints and runtime detection** ---
high potential significance and high feasibility.

This is a planning assessment, not an empirical ranking. Revisit after
confirming hardware, time, programming skills, and access to models.

## Preliminary external literature check

A preliminary web search surfaced relevant recent work: - *Crab: A
Semantics-Aware Checkpoint/Restore Runtime for Agent Sandboxes*
(arXiv:2604.28138). - *ACRFence: Preventing Semantic Rollback Attacks in
Agent Checkpoint-Restore* (arXiv:2603.20625). - *AgentRewind:
Recoverable Execution for Long-Horizon LLM Agents* (arXiv:2608.14380). -
*State-Aware Runtime for Long-Horizon LLM Agents: A Conceptual Framework
and Research Agenda* (working-paper versions surfaced in 2026).

These search results indicate overlap with checkpointing, rollback, and
long-horizon agent recovery. This is not an exhaustive review, and
metadata/claims should be verified from the original publications before
citing them in a paper.

**Novelty status: UNKNOWN.** Do not claim that rollback for agents is
unstudied. Investigate whether the proposed combination, benchmark,
evaluation protocol, or specific findings provide a defensible
contribution.

## Experimental protocol decisions

1.  Define a simulator with explicit initial state, intended objective,
    permitted actions, prohibited actions, recoverable state, and
    simulated external effects.
2.  Create labelled safe and unsafe scenarios before running tests.
3.  Verify baseline behavior and save the baseline logs.
4.  Implement each safety component as a separate module.
5.  Test components independently before combining them.
6.  Run identical scenarios across configurations.
7.  Record every run, configuration, seed (if applicable), software
    version, and failure.
8.  Report aggregate and per-scenario metrics, including negative or
    inconclusive results.
9.  Never claim execution or metrics unless supported by actual output.

## Metric definitions to finalize before experiments

-   **Unsafe-action rate:** prohibited actions executed / prohibited
    actions attempted.
-   **Task completion rate:** tasks completed successfully / tasks
    attempted.
-   **Detection rate:** actual violations detected / actual violations
    presented.
-   **False-positive rate:** safe actions incorrectly blocked / safe
    actions presented.
-   **Recovery success rate:** recovery attempts that restore the
    defined recoverable state / recovery attempts.
-   **Residual side effects:** unintended changes remaining after
    recovery.
-   **Execution overhead:** additional runtime or operations caused by
    safety mechanisms.
-   **Checkpoint overhead:** time and storage needed to create and
    maintain checkpoints.

Freeze denominator definitions and treatment of blocked actions before
collecting final results.

## Decisions and reasons

  --------------------------------------------------------------------------------------------------------
  ID          Decision           Reason                Evidence/source       Status      Next action
  ----------- ------------------ --------------------- --------------------- ----------- -----------------
  D-01        Start from the     Preserves the         Supplied review,      VERIFIED    Map every
              uploaded review's  existing research     Sections 4 and 10--12             implemented
              layered            direction                                               component to a
              architecture                                                               review passage

  D-02        Begin with a       Enables repeatable,   Feasibility inference INFERRED    Confirm coding
              sandboxed          safe tests without                                      environment and
              simulator          real-world side                                         project
                                 effects                                                 constraints

  D-03        Compare baseline,  Enables quantitative  Review proposes       INFERRED    Define scenario
              monitoring, and    comparison and        multiple layers;                  set and baseline
              combined recovery  ablation              evaluation design is              behavior
              system                                   inferred                          

  D-04        Measure both       A system that blocks  Experimental-design   INFERRED    Finalize metrics
              safety and         everything is not a   decision                          and denominators
              utility/overhead   useful success                                          

  D-05        Do not claim       Preliminary search    Preliminary external  VERIFIED    Perform
              novelty yet        found directly        search                that        systematic search
                                 related                                     related     and
                                 checkpoint/recovery                         results     paper-by-paper
                                 work                                        surfaced;   comparison
                                                                             novelty     
                                                                             UNKNOWN     

  D-06        Treat irreversible Local restoration may Supplied review,      VERIFIED    Implement an
              effects separately not undo external     Section 9                         external-effect
              from local state   effects                                                 ledger in
                                                                                         simulator

  D-07        Keep original      Prevents selective    Reproducibility       INFERRED    Pre-register or
              hypotheses even if reporting             decision                          timestamp
              unsupported by                                                             hypotheses before
              results                                                                    evaluation
  --------------------------------------------------------------------------------------------------------

## Evidence inventory and missing inputs

-   **Available:** Uploaded conceptual research review and its listed
    references.
-   **Missing:** Original full texts for all cited publications,
    confirmed hardware/runtime constraints, implementation source code,
    scenario dataset, baseline output, experiment logs, metric tables,
    and reproducibility instructions.
-   **Required before manuscript claims:** Original-source verification,
    literature-search record, working code, baseline validation, full
    experimental output, and a transparent account of limitations.

## Immediate next actions

1.  Confirm that Python is acceptable and specify any deadline or
    hardware restrictions.
2.  Obtain or verify the original papers cited by the review, especially
    the missing reference \[7\].
3.  Conduct a documented literature search for objective
    misinterpretation, agent runtime monitoring, checkpoint/restore,
    rollback correctness, and safety benchmarks.
4.  Finalize the research question and scenario taxonomy.
5.  Implement and test the simulator and unprotected baseline.
6.  Save baseline outputs before adding safety components.
7.  Implement constraint validation, monitoring, checkpointing, and
    rollback.
8.  Run ablations and record all outputs.
9.  Analyze results, revise the contribution claim, and draft the paper
    with only supported claims.

## Change log

-   **2026-10-21:** Initial scope extraction, candidate-gap analysis,
    proposed research questions, preliminary external search, and first
    decision log created from the supplied review. No experiments have
    been run as part of this document.
