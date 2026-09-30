# ToraOS Subject Ontology Concept Note v1.0
## Any Subject, Multiple Views, Directional Relations, Recursion, Runtime Boundaries, and Falsifiability

> Translation state: PRIVATE FAITHFUL TRANSLATION DRAFT  
> Bound original: `ToraOS Subject Ontology Concept Note v1.0`  
> Original version: v1.0  
> Original date: UNKNOWN (the original text does not state a date)  
> Original status: NONCANONICAL CONCEPT NOTE / paper-adjacent research note  
> This translation does not update, modernize, or adopt the note into ToraOS Current.

STATUS

NONCANONICAL CONCEPT NOTE / paper-adjacent research note

This document does not automatically change the Current claims of the ToraOS paper or any implemented mechanisms. It organizes post-paper considerations in a form that can be connected to future semantic contracts, research questions, and implementation verification.

## 0. Purpose of This Document

The ToraOS paper presents a concept in which the same OS Kernel is established independently for different Subjects, such as people, companies, families, communities, and projects, and each Subject maintains its own Source, Context, Authority, Relation, Decision, Outcome, and other state.

This Concept Note examines a further generalization of that concept of Subject.

The central questions are as follows.

- What can become a Subject?
- What is the difference between a real-world referent and a ToraOS View established about that referent?
- Can a Subject exist even if the Subject itself has no Goal or Self-report Capability?
- Can multiple Views with different Currents coexist for the same Subject?
- How should the semantic direction of a Relation be separated from who observed, asserted, or inferred it?
- Even if the space of possible Subjects remains open, can Runtime remain finite?
- How can these hypotheses be made falsifiable?

This document does not propose that “everything should always run as a Subject.” One of the principal boundaries clarified here is precisely that semantic possibility and physical execution must not be conflated.

## 1. A Subject Is Not Limited to an Intentional Agent

In ToraOS, a Subject need not refer only to an intentional agent such as a human, corporation, or organization.

In theory, anything that can be distinguished and referred to as one semantic object may be capable of becoming a Subject.

Examples include one human being, one animal, a company, a family, a Community, a Project, one computer, a building, the color red, love, democracy, money, an event, a law, a field of research, “research on red,” ToraOS, or “a ToraOS about ToraOS.”

Accordingly, the following are not required conditions for a Subject to exist:

- consciousness;
- self-awareness;
- having a Goal;
- being able to take Action;
- being able to operate ToraOS by itself;
- having legal personality; or
- having high management value from a human perspective.

Being a Subject is distinct from being an Agent, being a Phenomenal Subject, being a Legal Subject, or having a Goal.

## 2. Do Not Close the Space of Possible Subjects in Advance

ToraOS does not make it an ontological objective to “fix the candidate Subject set to a finite set.”

More precisely, it does not close in advance the range of things that may become Subjects.

In the semantic world of reality, there can be concepts about concepts, research about research, systems about systems, and self-referential concepts. ToraOS therefore does not prohibit recursion or meta-concepts at the ontology level solely for “system convenience.”

This does not mean running an infinite number of ToraOS processes.

Subject Possibility and Runtime Activation are different.

## 3. Five Semantic Boundaries

This examination showed a need to distinguish at least the following five states clearly.

### 3.1 Subject Possibility

A state in which something can be semantically distinguished and referred to, and can in theory be treated as a Subject.

At this stage, a ToraOS View does not need to have been created, and no Runtime resources are required.

### 3.2 Subject View Establishment

A state in which an independent ToraOS View has been established for a referent.

A View may maintain Source, Current, Authority, Relation, Goal, and other state centered on that referent.

Multiple Views may be established for the same referent.

### 3.3 Runtime Activation

A state in which actual Runtime processing, such as storage, retrieval, inference, Relation evaluation, or Action, is performed for an established View.

It consumes finite Compute, Storage, Network, and other resources.

A View does not need to remain Active at all times merely because it exists.

### 3.4 Relation Existence

A state in which a Relation Statement exists between Subjects or Views with direction, source, time, conditions, Authority, provenance, and other qualifiers.

The existence of a Relation does not mean that the Relation is correct, trustworthy, usable, confers Authority, or is needed for the current Task.

### 3.5 Task-time Evaluation / Application

A state in which Relations, Claims, Credentials, Artifacts, or other Boundary Objects are discovered and verified for a particular Task and used in that Task.

Separating Relation Existence from Task-time Evaluation avoids the error of “using it because it is in the Graph.”

The important non-equivalences are:

```text
Can be a Subject ≠ a View exists
A View exists ≠ Active in Runtime
A Relation exists ≠ evaluate it now
Evaluate a Relation ≠ trust it
Trust it ≠ confer Authority
Authority exists ≠ it is Truth
```

## 4. A Large Graph Is a Possible Result, Not the Objective

ToraOS does not aim to design a world-scale giant Graph first and then fill that Graph.

Reality contains many objects, concepts, events, observations, and views. Subject Views may be established for them as needed, and necessary Relations may be formed. A large-scale Relational Field may emerge as a result.

Therefore, the existence of one million Subjects does not imply the need to verify one million times one million Relations.

An all-pairs Relation check among all Subjects is not an architectural requirement.

The implementation scaling question is not whether to eliminate candidate Subjects, but whether Relation discovery, candidate generation, path selection, and Task-time evaluation can be kept bounded.

## 5. Do Not Equate a Real-world Referent with a ToraOS View

“Red” and “a ToraOS View established about red” are not the same thing.

View A, View B, and View C may all refer to the same red.

A and B do not need to have the same Current, Authority, Source, or Goal.

A may have the Goal “treat red from physical, cultural, and psychological perspectives,” B may have no Goal, and C may cover only art history.

Those are not Goals of red itself. They are Goals adopted by the respective Views.

## 6. Current Is Not Truth

Current is the present view adopted or maintained by that View at a given time.

Current does not mean the universal Truth of the referent itself.

A and B may have different Currents about the same Subject.

One may later be falsified. Both may be partially wrong. They may be updated. They do not need to be merged.

ToraOS does not generate “multiple truths.” It “keeps multiple Subject-local Currents distinct.”

## 7. Authority over Representation ≠ Authority over Referent

Even if an administrator manages a View of red, that person does not thereby gain absolute Authority over red itself.

Authority is not the power to determine Truth about the world.

Authority expresses who has legitimate power, based on a particular Framework, Role, Procedure, Scope, Validity, and other conditions, to assert, decide, update, disclose, delegate, or revoke something.

Accordingly, the following distinctions are maintained:

```text
Authority over representation ≠ Authority over referent
Canonical adoption ≠ Truth
Capability ≠ Authority
System permission ≠ Social / legal authority
```

## 8. A Fork Is View Divergence, Not Merely a Version Copy

In ToraOS, a Fork is not limited to a file copy or a Git-style version branch.

For the same referent, independent Views may be established with different Authority, Source, Current, and Trajectory.

Views after a Fork are not required to merge.

They may agree, partly agree, disagree, be unrelated, or remain disconnected.

More precisely, a Fork does not “create multiple Truths”; it allows independent Subject Views of the same referent to diverge.

## 9. Recursion Is Not Prohibited in Theory

ToraOS itself may become a Subject.

Therefore, “a ToraOS about ToraOS,” and in theory a ToraOS about that ToraOS, are not excluded.

This does not require infinite Runtime.

A semantically recursive space and finite Runtime are kept separate.

## 10. Connections Between Subjects Do Not Require Implicit Context Merging

A ToraOS Subject boundary does not mean isolation in which no information is ever exchanged with other Subjects.

Things that may cross a boundary can include not only Relations, but also explicitly disclosed Claims, Credentials, Artifacts, and verifiable references.

What matters is that Subject A’s Context itself is not implicitly copied into Subject B.

Connections occur through Boundary Objects constrained by Authority, provenance, time, Scope, Disclosure Policy, and other conditions.

It is not mandatory that they reside in physically separate databases. The important point is that semantic and Authority boundaries do not collapse.

## 11. A Relation Has at Least Multiple Axes

The example of Pino made clear that treating a directional Relation as merely A→B may be insufficient.

At least the following should be distinguished.

### 11.1 Semantic Direction

The semantic direction of the Relation itself.

Examples:

```text
Pino → PREFERS → Food A
Person A → MEMBER_OF → Company B
```

### 11.2 Statement Issuer

Who issued or asserted the Relation or Claim.

### 11.3 Observer

Who or what observed the underlying event, behavior, or state.

### 11.4 Inference Origin

The AI, logic, human process, or other mechanism that generated an Inference from an Observation or Source.

### 11.5 Provenance

The processing and derivation path from Source to Claim, Inference, Relation, and Current.

### 11.6 Authority

What legitimate power the Statement Issuer, Observer, Inference Origin, and others have within the relevant Scope.

Do not conflate Semantic Direction with Provenance Direction.

If an AI infers that “Pino is likely to prefer Food A,” that does not mean Pino himself asserted “I like Food A.”

## 12. One-way Relations and Mutual Relations

A→B and B→A are independent Statements.

Even if Evidence for one direction is strong, a Claim in the opposite direction does not necessarily exist.

When the Subject itself cannot Self-report, a large amount of human or AI Observation and Inference must not automatically be promoted to a Statement confirmed by the Subject.

A mutual Relation is treated as a Projection when Statements in multiple corresponding directions independently exist and can be verified as referring to the same real-world relationship.

The original Statements are retained.

## 13. The Pino Example: Action Can Improve Even When Truth Is Unknown

Establish a ToraOS View about Pino.

Even if Pino himself cannot enter into ToraOS “I like this food,” “I like this place,” or “I dislike outside,” people around him can provide Observations.

Example:

```text
Observation: In nine of the past ten trials, Pino chose Food A first.
Human Claim: The owner believes that “Pino likes Food A.”
Inference: Given the current Evidence, Pino is likely to prefer Food A.
Prediction: Under the same conditions, Pino is likely to choose Food A again.
Outcome: In fact, Pino chose Food B.
Correction: Re-evaluate differences in conditions or the previous Inference.
```

The important point is not to collapse Observation, Human Claim, Inference, Prediction, and Outcome into one thing.

ToraOS does not need to reach absolute Truth about Pino’s inner experience.

From past Evidence and Outcomes, it can predict which Action is more likely to be selected next and revise toward an Action more likely to be desirable for the Subject.

Complete acquisition of Truth is not made a necessary condition for better Action.

## 14. Boundary with Qualia

ToraOS does not solve the problem of qualia itself.

It may not be possible for humans or AI to directly access how Pino experiences a particular smell, that is, the subjective experience itself.

However, ToraOS can keep external Observation, third-party Claim, Inference, and First-person Evidence, when a first-person Claim is available, from being collapsed into the same thing.

In other words, the inability to directly access subjective experience is not treated as a system failure. ToraOS can learn about a Subject while preserving that boundary.

Being a Subject is not equated with being a Phenomenal Subject.

## 15. Subject-neutral Kernel and Optional Capability

Even if Person, Company, Community, Animal, Concept, and others can exist under the same Subject grammar, they do not need to have the same Capabilities.

A Person may have Self-report, Goal, and Action.  
A Company may require Roles, Governance, and Representative Authority.  
An Animal may have limited Self-report Capability.  
A Concept need not have Action Capability or a Goal.

The hypothesis “One OS. Any Subject.” does not mean treating all Subjects in the same way.

It asks whether the common meaning of the Kernel can be maintained while differences are represented as Capability, Profile, Governance, and other variations.

## 16. Central Principles at Present

1. Do not close in advance the range of things that may become Subjects.
2. Do not require consciousness, Goal, Action, or Self-report for something to be a Subject.
3. Do not equate a Subject with the ToraOS View established about that Subject.
4. Separate Subject Possibility, View Establishment, Runtime Activation, Relation Existence, and Task-time Evaluation.
5. Multiple independent Views may exist for the same referent.
6. Current is not Truth.
7. Administrative Authority is not Truth Authority over the referent itself.
8. Goal is Optional State, not a condition for Subject existence.
9. Allow Forks, contradictions, disagreement, disconnection, and Abstention as normal states.
10. Do not prohibit recursive Subjects in theory.
11. Graph scale is not an ontological reason for prohibition. Treat scaling as a bounded Runtime problem.
12. Do not conflate Relation Semantic Direction with Statement Issuer, Observer, Inference Origin, provenance, or Authority.
13. The existence of a Relation does not imply use, trust, or Authority.
14. Do not disguise an Inference that cannot be confirmed by the Subject as a First-person Claim.
15. Even without attaining complete Truth, improve Action using Evidence, Prediction, Outcome, and Correction.
16. ToraOS does not aim to converge the world onto one Truth.

## 17. Central Falsifiable Hypotheses

This Concept Note emphasizes turning the theory into hypotheses that can be broken rather than making the theory look elegant.

### H1. Outcome-driven Growth

Hypothesis:

By maintaining past Source, Outcome, and Correction as Subject State and applying them to related later Tasks, first Action can improve without requiring weight updates to the Foundation Model.

Falsification direction:

Compare groups with and without Correction on unseen Tasks that are related to past Tasks but have different conditions. If improvements in first Action, reduced Owner correction, or better Outcomes exceeding a predefined minimum meaningful effect do not reproduce, the hypothesis is weakened.

### H2. Subject Boundary

Hypothesis:

Necessary cross-Subject collaboration can be achieved through explicit Boundary Objects such as Claims, Relations, Credentials, and Artifacts without implicitly merging Context and Authority across Subjects.

Falsification direction:

If representative cross-Subject Tasks consistently require Raw Context sharing across boundaries and explicit limited disclosure does not function in practice, this boundary hypothesis is weakened.

### H3. Directional Relation

Hypothesis:

A structure that preserves A→B and B→A as independent Statements and creates a mutual Projection only when needed can represent disagreement, revocation, temporal difference, Authority difference, and dispute with less information loss than a single shared Relation Record.

Falsification direction:

If, across multiple domains such as employment, membership, delegation, credentials, and guarantees, there is no material difference from a single Relation Record in information value, correctability, or ability to represent disputes, the value of this added complexity is rejected.

### H4. Subject-neutral Kernel

Hypothesis:

Person, Company, Community, Animal, Concept, and other Subjects can be represented while preserving a common Semantic Kernel and expressing differences through Capability, Profile, Governance, and related dimensions.

Falsification direction:

If every added Subject type requires the core meanings of Source, Authority, Relation, Current, Outcome, and others to branch into separate implementations, leaving the common Kernel effectively empty, the “One OS. Any Subject.” hypothesis fails.

### H5. Claim / Provenance Integrity

Hypothesis:

By separating Observation, Statement Issuer, Semantic Relation, Inference Origin, provenance, and Authority, the system can operate without disguising AI Inference or third-party Observation as a Claim or Authority belonging to the Subject itself.

Falsification direction:

If normal operation or Red Team testing cannot semantically detect and reject improper promotion from Inference / Observation to a Verified First-person Claim or Authority-bearing Claim, this Integrity hypothesis does not hold.

## 18. Questions Still OPEN

The following questions remain unresolved not to narrow the range of possible Subjects, but to project the concept into implementation without breaking its meaning.

- What is a formal definition of “semantically distinguishable and referable”?
- How should the vocabulary Entity / Concept / Subject / Referent / View be formalized?
- How should multiple Views referring to the same referent be resolved? Is a world-wide common ID necessary or unnecessary?
- What are the minimum conditions for View Establishment?
- How should an Inactive View be stored and restored?
- How can Relation discovery and Task-time evaluation be bounded?
- What is the formal schema for Relation Semantic Direction, Statement Issuer, and related dimensions?
- How should Mutuality be defined when the Subject itself cannot Self-report?
- What semantic operations correspond to Fork, Divergence, Merge, and Rebase?
- How should Recursive Subjects be handled without cycles or infinite evaluation?
- How can the relationship between Authority over representation and Authority over referent be proved or denied?
- How should laundering from AI Inference to Claim be Red Teamed?
- Does the common portion of a Subject-neutral Kernel really contain enough meaning?
- When Outcomes conflict across multiple Subjects, how should Correction be separated?
- How can a minimum Semantic Grammar interoperate among different implementations and Forks?

## 19. Central Proposition at Present

ToraOS is not an OS only for humans, companies, or AI.

For any Subject that can be semantically distinguished, including reality, physical objects, living things, events, concepts, ideas, relations, systems, and concepts about those things, ToraOS may in theory establish an independent View.

That View is not the universal Truth of the referent itself. It is a Subject-local Current formed by one ToraOS View from Source, Authority, Claim, Relation, Inference, Outcome, and other state.

Different Views with different Currents may exist for the same referent, and Forks, falsification, contradiction, recursion, disconnection, and Abstention are normal.

Even when the Subject itself cannot operate ToraOS or Self-report, understanding and Action can be revised from Observation, Claim, Inference, Prediction, and Outcome. However, these must not be disguised as the Subject’s own first-person Truth or Authority.

ToraOS does not aim to converge the world onto one correct Graph.

It aims to test whether a semantic environment can exist in which different Subject Views remain different yet can relate without losing Source, Authority, provenance, Direction, time, or Disclosure, and whether future Action can improve from those Relations and real Outcomes.
