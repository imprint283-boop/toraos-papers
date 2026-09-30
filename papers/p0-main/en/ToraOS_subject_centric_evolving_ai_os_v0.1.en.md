# ToraOS: A Proposal for a Subject-Centric, Evolving AI OS Architecture
## Independent Context and Authority, Directional Relations, and Continuous Growth Driven by Real-World Outcomes

**Tsubasa Nakagawa**  
Independent Research and Practical Development  
Draft v0.1 / August 29, 2026

> **Translation metadata (not part of the original body)**: `PRIVATE_FAITHFUL_TRANSLATION_DRAFT`; bound to P0 Japanese original v0.1 dated 2026-08-29. Later ToraOS implementation or A5 findings are not imported into this translation.

> **Paper type**: Position paper, architecture proposal, and partial reference-implementation report  
> **Note**: This is a pre-peer-review draft. It explicitly separates the current ToraOS implementation, future concepts, the author's research hypotheses, and social future predictions. This paper does not claim that ToraOS is “the world's first,” that it will work at world scale, or that it is socially desirable.

## Abstract

When generative AI is used over long periods, problems appear that differ from one-off conversational performance. Past decisions fail to carry into later work; the contexts of people, organizations, and projects become mixed; the grounds for what was treated as fact are lost; and an AI proposal being accepted is conflated with whether it was actually effective. This paper treats these problems not merely as a lack of “long-term memory,” but as problems arising from where the basic unit of an AI system is placed.

This paper proposes a **subject-centric, evolving AI OS** architecture. The same OS kernel is established independently for different “Subjects,” such as people, companies, families, communities, and projects, and each Subject maintains its own original Source information, semantic interpretation, Context, Decision, real-world Outcomes, and Authority. Subjects are connected through **directional Relations** carrying provenance, direction, time, valid scope, Authority, and disclosure conditions, without implicitly merging their Contexts. Relations in the opposite direction are established independently. When both can be verified as referring to the same real-world relationship, a mutual relationship may be projected, while the two original claims are preserved. This mutuality may form “relational value” such as credentials, membership, guarantees, delegation, Authority, or trust. It must not, however, be collapsed into a single social-credit score.

ToraOS is a partial reference implementation of this concept. In the private repository as of August 29, 2026, mechanisms exist for separating original Source from derived information, field-level Authority control, Source-gated shared state, Context reasoning, validation/review/admission of Relation candidates, applying Context to real work, separating Delivery from Owner Decision and actual utilization, Correction from real Outcomes, and a path toward improved selection when similar situations recur. In contrast, federation among multiple independent ToraOS Subjects, a mutual-Relation protocol, a public conformance specification, and exchange of social trust are not implemented and remain research hypotheses.

The paper's main contributions are: (1) an abstraction that treats AI memory as state owned by the Subject rather than as an accessory of a user account; (2) a Relation boundary that connects Subjects without mixing their Context and Authority; (3) a Relation model that separates one-way claims from mutual confirmation; (4) an Outcome-driven loop in which Growth is conditioned on improvement in future Action rather than memory volume; and (5) a falsifiable public-research plan linking these ideas to implementation code, Authority documents, and development history.

**Keywords**: subject-centric AI, long-term Context, Authority separation, directional Relation, mutual Relation, provenance, continual learning, distributed AI, open source

---

# 1. Introduction

As large language models have improved, AI has expanded beyond search and text generation into planning, coding, document preparation, operational support, and decision support. But when use extends over months or years, problems appear that are difficult to explain simply as “model performance.”

First, **remembering something and using it effectively in the next Decision are different things**. Even if a large volume of history is stored, noise can increase unless the system can select only the past information relevant to the present Goal. Second, **it is normal for different Subjects to hold different understandings of the same person or organization**. If private judgments, corporate official judgments, and other perspectives are merged into one giant knowledge graph, provenance, responsibility, confidentiality, time, and legitimate decision rights collapse. Third, **an AI-generated artifact being accepted is different from that artifact being effective in reality**. If Delivery, adoption, utilization, Outcome, and Correction are collapsed into one success state, the AI cannot learn what actually worked.

ToraOS is a system that has been implemented beginning from one person's long-term AI use. Its current Universal Semantic Constitution distinguishes Original Source, Evidence, Record, Claim, Inference, and Current View, and explicitly rejects a single world-wide Truth or a single Goal governing all Subjects. It also establishes a boundary under which companies and organized Communities may become independent Subjects, while loose communities, regions, or the world need not become one giant Subject.[Internal 1]

This paper abstracts the implementation and design one level further and examines the following questions.

- **Research Question 1**: Can the same OS kernel be established independently for different Subjects, without splitting people, companies, communities, and others into separate products?
- **Research Question 2**: Can social relationships be represented without implicitly mixing each Subject's Context and Authority?
- **Research Question 3**: By separating one-way Relation claims from mutual confirmation, can trust, guarantees, and Authority be represented without depending on a centralized single trust score?
- **Research Question 4**: Can “Growth” be defined not as long-term memory itself but as returning real Outcomes and Corrections into the first Action taken later?
- **Research Question 5**: Can this structure develop into an open architecture in which separate implementations and Forks can participate, rather than remaining closed to a specific product?

This paper does not present completed empirical results answering those questions. It separates what currently exists, what can be confirmed in code, the author's adopted direction, unverified research hypotheses, and social future predictions. The boundary among these claim classes is itself treated as part of the research contribution.

# 2. Origin and Method of the Research and Development

## 2.1 A Practice-driven Starting Point by a Non-specialist

As of 2026, the author is 46 years old and is a practitioner from another field who has not had software development as a field of formal education or professional employment. The author began using generative AI seriously around 2025, moved into code implementation around May 2026, and from June of that year shifted to a paid plan with larger usage allowances and began intensive development of ToraOS. In an environment without programmers or advanced AI users available for regular consultation, design exploration was conducted mainly through dialogue with ChatGPT, while implementation, testing, and correction were conducted mainly through dialogue with Codex.

A development record dated May 27, 2026 organized the early ToraOS as “a personal AI foundation that grows from the user's history of judgment,” with a minimum success condition of one loop: “artifact → user evaluation → extraction of decision criteria → application next time.”[Internal 2] At that time, many physical structures that differ from the current system were considered, including an Obsidian memory store, department-style AIs, evaluation logs, and temporary AIs. What matters is that while boxes and product names changed repeatedly, the objective of **using the user's Decisions, discomfort, Corrections, and real Outcomes in the next situation** remained.

This background does not prove that the architecture is novel or correct. It is relevant, however, to understanding its formation: the design was not derived top-down from textbook categories of distributed systems or knowledge representation. It reached the separation of original Source, semantic interpretation, Context, Authority, Relation, and real Outcomes by decomposing failures encountered in long-term use one by one.

## 2.2 Research Materials

This paper was prepared by comparing five types of primary material.

1. **Current Authority documents**: the Universal Semantic Constitution, the Personal Tora Constitution / Profile, the Current Operating Policy, the Harness policy, and the Current Authority Registry.
2. **Adopted requirements**: ToraOS Requirements Definition v1.2, decision/growth/data design, system architecture/integration/Authority design, and related material.
3. **ToraOS OPEN future candidates**: the v0.3 integrated version, additional deep-dive semantic contracts, Gap audits, publication Gate, and related material. These are read as noncanonical future candidates with no Authority over the current implementation.
4. **Implementation code**: the private GitHub repository `imprint283-boop/toraos-shadow-harness`, main commit `3c4ccac069034b75f776b0b0109b9964f5003a5a`, as of August 29, 2026, was used as the implementation baseline.[Internal 3]
5. **Development Trajectory**: design dialogue, requirements revisions, failures, audits, PRs, Canary tests, and Owner Corrections since May 2026.

This paper does not treat the existence of a requirements document as evidence that something is “implemented,” nor the existence of code as evidence that operational value has been demonstrated.

## 2.3 Claim Levels

To avoid conflation, this paper divides claims into five levels.

| Level | Meaning | Example |
|---|---|---|
| A: Current Authority | Meaning currently effective in canonical/Authority documents | No universal world Truth; Personal Goal is not imposed on another Subject |
| B: Implementation Evidence | Mechanism confirmable in main code, tests, or accepted Receipts | Authority Map, Relation admission ledger, Outcome/Correction path |
| C: Author Direction | Direction explicitly stated by the author as the current concept | Establish the same OS independently for each Subject |
| D: Research Hypothesis | Technical or social hypothesis not yet empirically demonstrated | Mutual Relations may become context-dependent trust assets |
| E: Future Prediction | Long-term prediction involving social institutions or markets | SaaS/SNS may be relativized into Adapters around Subjects |

These levels are not an explanatory escape hatch intended to make an unfinished system look complete. They are a research boundary intended to preserve falsifiability.

# 3. Related Research and Existing Technologies

Each element of ToraOS has clear prior art. This paper therefore does not claim novelty for individual elements such as “giving AI long-term memory,” “using a relation graph,” or “using decentralized identifiers.”

## 3.1 Distributed Personal Data Foundations and Solid

Solid is a decentralized Web foundation that separates user data from applications, stores it in personal online data stores called Pods, and allows applications to use data within their permissions.[1][2] A Solid WebID may refer not only to a person but also to an organization or other agent. The current Solid Protocol states that a WebID can identify agents such as persons, organizations, and software.[2]

This is close to the ToraOS direction that state should be held on the Subject side rather than enclosed by services. Solid's central problem, however, is data ownership, access, and interoperability; it does not define Subject-specific AI Decision, real Outcome, Correction, and improvement of future Action as one OS loop. Research such as SocialGenPod, which uses generative AI on Solid, demonstrates separation and portability between private data and generative AI, but does not extend to Subject-level Authority, Decision, and Outcome-driven Growth.[10]

## 3.2 Decentralized Identifiers and Verifiable Credentials

W3C Decentralized Identifiers (DIDs) can refer to “any subject,” including people, organizations, things, data models, and abstract entities, and separate identification from a centralized identity provider.[4] Verifiable Credentials allow claims such as educational qualifications, licenses, and credentials to be exchanged in cryptographically verifiable form among issuers, holders, and verifiers.[5] Standards also exist for credential revocation and suspension.[6]

These are important candidate foundations for the future ToraOS problem of “who guaranteed what about whom” and “whether that Claim is currently valid.” DID/VC by themselves, however, do not define a Subject's long-term Context, Decision-making, real Outcomes, or continual AI Growth. ToraOS should not reinvent them. A future public protocol should stand on the side of using or connecting to existing standards.

## 3.3 Decentralized Social Networks and ActivityPub

ActivityPub is a standard for decentralized social networks that lets Actors on different server implementations exchange content and notifications.[3] In that sense, it shares a long-term direction with ToraOS: a social network can exist without everyone gathering inside one central social platform.

An ActivityPub Actor, however, is primarily an actor in social message exchange. It is not intended to maintain the Subject's internal original Source, Authority, Decision, real Outcome, and Correction as an independent cognitive OS. A future ToraOS federation would more naturally use ActivityPub as one possible social delivery route when useful rather than compete with it.

## 3.4 Provenance and PROV

W3C PROV provides standards for exchanging provenance across systems using Entity, Activity, Agent, and relations of generation, derivation, and responsibility.[7] The ToraOS emphasis on “what was Original Source, who observed it, what was derived from what, and who made a Decision under what Authority” can connect to a long history of provenance research.

ToraOS should not place its distinctiveness in “having provenance.” Its relevance is instead in applying established provenance principles to a long-term Growth loop consisting of AI Context selection, Relation candidates, Decisions, artifacts, real utilization, and Correction.

## 3.5 Long-term Memory and Lifelong Learning in LLM Agents

Long-term memory for LLM agents is already a large research field, covering memory writing, storage, retrieval, reflection, hierarchy, lifelong learning, and related topics.[8][9] By 2026, research had also begun to treat long-term memory security as a lifecycle covering writing, storage, retrieval, execution, sharing/propagation, forgetting, and rollback.[14]

ToraOS overlaps with this field but does not make “the AI agent's own memory” the highest-level concept. Memory is part of a Subject's Source or Context, while the AI model and Provider are positioned as replaceable execution engines. The current requirements likewise define Tora not as the LLM itself, but as a combination of Event Ledger, Decision Scene, Goal Structure, Decision Model, Context Selection, and Outcome Feedback.[Internal 4]

## 3.6 Trust, Reputation, and Web of Trust

Research deriving trust and reputation from network relations has a long history, including reputation systems aggregating post-transaction ratings, trust graphs in P2P networks, Web of Trust, and graph-centrality-based trust estimation.[11][12]

Therefore, the notion that “Relations can become trust” is not itself new. The distinction proposed here is to **avoid collapsing trust into one global reputation value and instead preserve each Subject's independent directional Claims, mutual confirmation, third-party guarantees, provenance, Authority, time, valid Scope, and real Outcomes, evaluating them as a relational path only when needed**.

## 3.7 Position of This Paper

Viewed by technical lineage, ToraOS sits at the intersection below.

| Lineage | Existing strength | What ToraOS attempts to add |
|---|---|---|
| Solid / PDS | Data sovereignty; application/data separation | An evolving OS including Subject Decisions, real Outcomes, and Corrections |
| DID / VC | Decentralized identity; verifiable credentials and guarantees | Connection between Subject-internal Context/Outcome and relational value |
| ActivityPub | Social federation across heterogeneous implementations | Federation among Subject OSes while preserving Context and Authority |
| PROV | Provenance, derivation, responsibility | Application to AI Context selection and Outcome learning |
| LLM Memory | Long-term memory, retrieval, reflection | Make the Subject, not the AI, the owner of state |
| Trust/Reputation | Infer trust from relations | Avoid one score; preserve mutual Relations and Authority Paths |

The candidate novelty is not any single technology, but an architecture that integrates **Subject sovereignty + AI cognition + Authority separation + directional Relations + real-Outcome learning** into a repeatable Subject unit of the same OS.

# 4. Problem Setting: From Platform-centric to Subject-centric

Many current Web services are platform-centric: a user has an account for each service, and profile, history, human relationships, trust, and operational records are duplicated inside each service.

```text
Service A ─ profile/history/relations of User A
Service B ─ profile/history/relations of User A
Service C ─ profile/history/relations of User A
```

In this model, fragments of the same person exist in multiple places, and part of the relationships and history may be lost when leaving a service. The same applies to companies: CRM, chat, accounting, HR, calendars, and other SaaS products each hold fragments of the company internally.

In a Subject-centric model, the primary unit moves from the service to the Subject.

```text
                 Subject A
       ┌─────────┼─────────┐
       │         │         │
    Service 1  Service 2  Service 3
      Adapter / Storage / Execution / Delivery
```

Services do not become unnecessary. They provide Capabilities such as storage, payment, delivery, computation, UI, and legal procedures. But they no longer need to be the sole owners of the Subject's long-term Identity, Context, Authority, and Decision history.

This direction overlaps with Solid and related systems. What this paper additionally requires is an internal cognitive loop in which AI continuously interprets meaning within the Subject and reflects past Decisions and real Outcomes in future Action.

# 5. Proposed Architecture

## 5.1 “One OS, Any Subject”

In the author's latest direction for ToraOS, Personal Tora, Company Tora, and Community Tora are not defined as separate products.

> **The same OS kernel is established independently for different Subjects.**

Conceptually, each instance can be represented as:

```text
T_i = K + P_i + X_i
```

where:

- `K`: the OS kernel of semantics, safety, provenance, Relation, time, and real Outcome common to all Subjects;
- `P_i`: the profile of Subject i, including its Constitution, Authority, Capability, disclosure policy, and Roles; and
- `X_i`: the original Source, derived state, Decisions, Outcomes, and history belonging to Subject i.

A person, company, family, community, or project is a **type of Subject**, not a “type of OS.” The same Kernel is used while only the necessary Capabilities are enabled. A company may emphasize Governance, Roles, and representative Authority; an individual may emphasize private Goals and Decision history; a conceptual Subject may legitimately have no Action Capability. This is consistent with the Optional Capability direction of ToraOS OPEN v0.3 and the current Universal Semantic Constitution's principle that “a Subject may have multiple Goals, conflicting Goals, or no Goal.”[Internal 1][Internal 5]

## 5.2 Do Not Equate the Subject with the Real-world Referent

ToraOS OPEN v0.3 separates real-world Entity/Concept from Tora Subject.[Internal 5] This separation is necessary.

“The real organization Kitano Dōhōkai” and “a ToraOS that has Kitano Dōhōkai as its Subject” are not identical. Even if anyone could create a digital Subject candidate using the same name, that alone would confer neither official status nor representative Authority. Real-world Recognition, credentials, Roles, establishment procedures, representative Authority, and similar properties must be verified through separate Relations.

This is compatible with the DID separation between subject and controller. Rather than inventing a new world-wide identifier system, ToraOS should maintain a semantic boundary that can accept existing identification and credential standards.

## 5.3 Do Not Mix Context and Authority Across Subjects

Even when the same Entity appears in multiple Subjects, what each Subject knows, treats as authoritative, or may use is different.

For example, if both Personal Subject A and Company Subject B contain the Entity “Person X”:

- A may hold private experience, personal schedules, and personal evaluations;
- B may hold Role, employment records, Company Decisions, and organizational Outcomes.

Let the Context set of Subject i be `C_i`. The default condition is that it does not automatically inherit into another Subject j.

```text
For i ≠ j, C_i is not implicitly copied into C_j.
```

Only explicitly disclosed Claims, Relations, Credentials, Artifacts, or verifiable references to them may cross the boundary, and disclosure is constrained by the Authority and Policy of the relevant Subject.

This principle already appears in current Personal Tora. Even if Personal work can generate candidates for another Subject's Source, Relation, or Outcome, reflecting them into the official Subject requires that Subject's establishment procedure, Authority, and Permission.[Internal 6]

## 5.4 Separate Two Kinds of Authority

Because ToraOS uses the word “Authority” at two layers, this paper distinguishes them.

### 5.4.1 Data Authority

The implementation-level Authority Map decides, for a given field, which store, binding, and writer is the sole authoritative updater. Current code separates classifications such as `canonical`, `shared_authoritative`, `local_authoritative`, `derived`, and `cache`, requires exactly one authoritative writer for each field, and advances revisions one step at a time.[Internal 7]

This is technical authority over “which data should be read as authoritative.”

### 5.4.2 Subject Authority

By contrast, Authority in the Universal Semantic Constitution is a Claim traceable to Framework, Source, establishment procedure, Role, Holder, Scope, Validity, Evidence, revocation, and dispute.[Internal 1] A company representative's power to enter a contract, for example, is not merely a database write permission.

This paper calls the former **Data Authority** and the latter **Subject Authority**. Capability, system permission, and socially legitimate Decision authority must not be conflated.

## 5.5 A Relation Is a Directional Statement

A relationship is not an undirected line.

```text
A → B
```

and

```text
B → A
```

are independent Claims.

ToraOS OPEN v0.3 likewise explicitly states “Relation is Directional Statement,” and provides that a mutual Relation may be projected when Statements in multiple directions are consistent.[Internal 5]

Conceptually, this paper represents one Relation as the following tuple:

```text
r = (
  issuing Subject,
  target,
  relation type,
  direction,
  source,
  Authority Scope,
  time / validity period,
  conditions,
  counterevidence,
  disclosure conditions,
  state
)
```

The current ToraOS Relation implementation also contains `subject_ref`, `object_ref`, `family`, `relation_type`, `direction`, Source refs, counterevidence, conditions, valid time, provenance, confidence, and related fields.[Internal 8]

## 5.6 One-way Relations and Mutual Relations

For example, a Relation in which Person A records “I am an officer of Company B” has value as a Claim on A's side, but by itself does not mean that the company officially recognizes it.

```text
A → ROLE_CLAIM → B
```

If, through an appropriately authorized process on Company B's side, an independent Relation exists:

```text
B → APPOINTED → A
```

and the two Relations can be verified as referring to the same Role, period, and Scope, a mutual relationship may be projected.

The important point is that the two original Relations are not erased after mutualization.

```text
mutual relationship = Projection(r_A→B, r_B→A)
```

This structure can preserve real-world inconsistencies such as:

- A claims membership while B does not recognize it;
- B claims membership while A says the person has already left;
- third-party institution C guarantees one side;
- both sides agree, but the validity period has expired.

## 5.7 Conditions Under Which a Relation Has Value

This paper does not assume that more Relations mean greater value. It avoids the single-score reduction common to reputation systems.

The value `V` of a relation is considered a context-dependent function of the use case `q`.

```text
V_q(r) = F(
  mutuality,
  Authority of the issuing Subject,
  source and provenance,
  independent support,
  validity period,
  counterevidence,
  third-party guarantees,
  past Outcomes
)
```

`F` need not be a numerical function. It may be an explainable Evidence Path.

For example, a bundle of Relations saying “followed by one million people” and a Relation saying “a specified credentialing body has issued a currently valid credential” serve different purposes. The relation paths required for housing rental, hiring, public administration, community participation, and other uses also differ.

This paper provisionally calls a bundle of verifiable Relations received by an independent Subject from other Subjects **verifiable relational capital**. This does not mean a new world-wide currency or social-credit score.

## 5.8 Do Not Automatically Guarantee Relation Transitivity

Even if A and B, and B and C, are strongly connected:

```text
A ↔ B ↔ C
```

you must not automatically derive:

```text
A trusts C
```

What can be used is the fact that “there is a verifiable path between A and C through B.” Transitivity depends on Relation type, Scope, legal meaning, time, and purpose. Just as current ToraOS does not automatically promote correlation into causation, it must not automatically promote a relation path into trust.

## 5.9 Separate Source from Outcome

One important ToraOS invariant is not to collapse the following into one state.

```text
Original Source
  ↓
Semantic interpretation (Semantic / Claim / Inference)
  ↓
Relation
  ↓
Context Selection
  ↓
Action / Delivery
  ↓
Owner Decision
  ↓
Actual utilization / real Outcome
  ↓
Correction
  ↓
Next Context / Action
```

The current Autonomous Context / Trajectory / Outcome Growth Loop contract likewise does not treat the number of Contexts or Relations as a success metric. Its value test is whether past Evidence changes the first Action, whether later Owner Evidence connects to accurate Delivery and Context Application, and whether Correction becomes input into later ordinary selection.[Internal 9]

A response of “this is fine” is a Decision, not successful utilization. By separating Delivery, Owner Decision, utilization, Outcome, and Correction, AI can distinguish why an artifact was accepted from why it actually worked in the field.

# 6. Current ToraOS Implementation

## 6.1 Implementation Baseline as of August 29, 2026

The main HEAD of the private repository examined in this paper is `3c4ccac069034b75f776b0b0109b9964f5003a5a`. This commit is the merge of PR #36, “Add nonactivated Codex Hook payload bridge,” corresponding to approximately 01:03 JST on August 29, 2026.[Internal 3]

The repository README describes the current state as `private development history` and explicitly states that public release and an open-source license have not been approved.[Internal 3] Accordingly, at the time this paper was written, it would not be accurate to state that “ToraOS is open source.” Open-sourcing is the author's current objective.

## 6.2 Four-layer Authority

Current Authority Registry revision `TOROS-CURRENT-AUTHORITY-REGISTRY-20260828-038` selects the following four layers as Current.[Internal 10]

1. Universal Semantic Constitution
2. Personal Tora Constitution / Profile
3. Current Operating Policy
4. Harness Adapter Policy

This structure separates the universal meaning of “what ToraOS is,” the Subject-specific meaning of “what this Subject is trying to achieve,” how changes and operations are currently managed, and how these are projected into an execution Harness.

This is important for future multi-Subject architecture. The boundary already exists in Current under which the Goals or Authoritative Owner of Personal Tora are not fixed in the universal layer and are not automatically inherited by another Subject.[Internal 1][Internal 6]

## 6.3 Field-level Authority Map

`authority_map.py` validates field-level classification, store, writer, binding, read source, cache, fallback, and migration state. For authoritative classifications, it rejects promotion from non-authoritative stores and requires exactly one authoritative writer for each field.[Internal 7]

This avoids assigning authority based merely on physical location, such as “it is canonical because it is in Google Drive” or “it is canonical because the value is in the database.” If multiple Subjects are connected in the future, this design also provides a basis for ensuring that a shared Relation does not gain writer Authority over the other Subject's entire internal Context.

## 6.4 Source-gated Shared State

`shared_state.py` treats Context Selection, Context Application, Delivery, Owner Outcome, and Growth Correction as separate states, and before a write it confirms consistency with the Authority Map and Source staged commit.[Internal 11]

The shared database stores opaque IDs, revisions, closed codes, hashes, timestamps, references, and similar values, while prohibiting raw conversations, person names, secret values, and related material. This structure is an implementation-level barrier against turning shared state into a giant personal-information database.

## 6.5 Separation of Context Reasoning and Relation

`context_reasoning.py` provides a Provider-neutral and graph-neutral boundary. The Relation Graph is one internal Strategy, while an external consumer receives a canonical proposal set. States such as `ZERO_DERIVED_NORMAL`, `INSUFFICIENT_EVIDENCE`, and `FAILED_SAFE` are distinguished as normal outcomes rather than forcing Context to be generated.[Internal 8]

`relation_operational.py` further makes explicit that a Relation is not converted directly into Context. Only admitted Evidence is discovered, and Context found through a Relation must still pass Gates for original Source, lifecycle, time, privacy, Authority, and other constraints.[Internal 12]

This prevents the error “a Relation exists, therefore the information may be used.” A Relation is Evidence of relevance or of a path; it is not use permission.

## 6.6 Independent Lifecycle for Relation Admission

In PostgreSQL `020_relation_admission.sql`, Relation candidates have separate Validation Events, Review Events, Admission Events, and Admitted Relation Evidence. They are bound by payload hash, Source snapshot, Authority, generation, writer, sink, and fencing token.[Internal 13]

Triggers make admitted Relation Evidence append-only by rejecting update and delete. `NO_RELATION` and `INSUFFICIENT_EVIDENCE` are also preserved as normal terminal results.

This implementation separates an LLM producing text that looks like a relationship from the system admitting it as a Relation that may be used.

## 6.7 Real-work Growth Loop

`live_ordinary_growth_loop.py` separates visible Task identity, Context arm, start of real work, Delivery, Owner Outcome, Utilization, and Growth.[Internal 14]

`outcome_growth_correction.py` separately represents adoption, partial adoption, correction, rejection, and actual utilization states such as `USED_AS_IS`, `USED_WITH_REVISION`, and `NOT_USED`, and records Corrections to Context selection or execution method append-only.[Internal 15]

The first completion line defined by the current Personal Tora Profile is:

```text
Source
→ Context Application
→ causal approximation
→ Action / Delivery
→ Outcome
→ Correction
→ later similar Task
→ reduction of preventable correction, or appropriate differentiation for changed conditions
```

[Internal 6] A distinguishing feature is that the requirement is for an actual difference in later work, rather than for test count or storage volume.

## 6.8 Natural-language Owner Ingress

`ordinary_owner_ingress.py` is a thin boundary that projects the Owner's natural language into existing Dispatch, Context, Outcome, and Relation paths. It does not persist the raw Owner text, retaining only a hash and limited derived fields.[Internal 16]

This implementation treats natural-language AI not as an omnipotent Planner that owns everything, but as an Adapter passing meaning to existing state owners.

## 6.9 Source Intake

`live_source_semantic_intake.py` incrementally retrieves Codex rollouts from a read-only Provider, retains screened raw Source in local Runtime, and passes high-signal ranges to a replaceable semantic worker.[Internal 17] Source capture alone does not assert Semantic completion or Outcome completion.

The separation “Source acquisition ≠ semantic understanding ≠ Relation existence ≠ Context use ≠ Outcome” will remain necessary when extending the architecture to federation among Subjects.

## 6.10 Replaceability Boundary for the Execution Provider

`codex_sdk_controller.py` uses Codex as the current Owner-facing transport but does not give it ownership of Planning, Scheduling, Context, Relation, Admission, or Health. It defines a Provider-neutral `OwnerTaskTransport`, with Codex as one Adapter.[Internal 18]

This design is important to avoid binding ToraOS to the application stack of one AI company.

## 6.11 Current Incomplete Boundaries

The latest PR #36 added a Codex Hook payload bridge but did not activate the Hook, Scheduled Task, or production operation. A TOCTOU issue around projection directory replacement remains at P2, and unattended execution, production, and Hook activation are STOP conditions.[Internal 19]

This state matters for the paper. ToraOS implements many mechanisms, but **not every automation path is in production operation**.

## 6.12 Implemented and Unimplemented Areas

| Area | State as of 2026-08-29 |
|---|---|
| Source / Derived separation | Implementation exists |
| field-level Authority | Implementation exists |
| Context Selection / Application | Implementation exists |
| Relation derivation / validation / review / admission | Implementation exists |
| Relation-assisted Context | Implementation exists |
| Separation of Delivery / Owner Decision / Utilization / Outcome | Implementation exists |
| Outcome → Correction | Implementation exists |
| feedback path to later similar Tasks | Implemented / at acceptance stage; natural recurrence Evidence managed separately |
| natural-language Owner ingress | Implementation exists |
| Codex SDK transport | Implementation exists |
| full Hook automation | Not activated; STOP conditions exist |
| multiple independent ToraOS instances for Person / Company / Community | Not implemented |
| Relation federation among Subjects | Not implemented |
| cross-instance mutual-Relation handshake | Not implemented |
| public interoperability with DID/VC and similar standards | Not implemented |
| public conformance suite | Not implemented |
| OSS license / public repository | Undecided / not public |
| social credit using Relations | Research hypothesis |

# 7. Subject-Centric Model Newly Integrated by This Paper

## 7.1 Relationship to Earlier OPEN Proposals

In the design Trajectory of ToraOS OPEN, some material dated August 10, 2026 contained a hypothesis called “Personal Node Only.”[Internal 20] It was a safety-oriented hypothesis intended to avoid anthropomorphizing an organization into one giant person.

A later v0.3 revision allowed Company, Community, Concept, and others to be Tora Subjects while changing Constitution, Goal, Action, and Growth into Optional Capabilities rather than requirements imposed on every Subject.[Internal 5]

The current Universal Semantic Constitution further recognizes as Current Semantic Grammar that a Company or organized Community may become a Subject.[Internal 1]

Based on this Trajectory, the paper organizes the author's latest direction as follows.

> Personal, Company, and Community are not different products.  
> **The same ToraOS Kernel is established independently for each different Subject.**

This does not erase the earlier Personal Node Only hypothesis from history. It preserves it as a Trajectory of falsification and revision, while introducing a newer higher-level hypothesis.

## 7.2 Company Tora as a Second Instance

The purpose of Company Tora is not to create a “company mode” of Personal Tora.

It is a **second-instance test** of whether the same Kernel can handle another Subject after removing assumptions that held implicitly in Personal Tora: one Owner, one decider of Goals, and one Context boundary.

For a Company Subject, it is necessary to:

- separate the representative from the Subject;
- separate Role from Actor;
- separate Company Decisions from individual opinions;
- separate Company Outcomes from individual Outcomes;
- prevent Personal Context from flowing implicitly into the company; and
- prevent Personal Tora from exercising Company Authority on the company's behalf.

If this test succeeds, it would provide initial Evidence that ToraOS can be abstracted from “AI dedicated to one user” into a “Subject-neutral OS.”

## 7.3 Community as a Third Instance

A Community may additionally lack a single representative, employment agreement, or legal personality. Multiple Goals, dissent, provisional agreement, departure, rejoining, and unresolved states may be normal.

If the same Kernel can operate here, it becomes more plausible that Subject need not be limited to Person or Company and can represent diverse collectives through combinations of establishment procedure and Capability.

# 8. Relational Value Produced by Mutual Relations

## 8.1 Self-report and Relations Returned by Others

A profile that a Subject maintains about itself is information. By contrast, a Relation issued about the Subject by another Subject and returned with Authority and Evidence may, depending on the case, express trust, credentials, guarantees, Authority, membership, or delegation.

```text
A writes about itself:
A → MEMBER_OF → B

B returns:
B → HAS_MEMBER → A
```

The latter adds independent Evidence beyond A's self-report.

If a third party C further guarantees the official status of organization B or the A-B relationship, trust can be explained as an Evidence Path rather than a single score.

```text
C → RECOGNIZES → B
B → APPOINTED → A
A → ACCEPTS_ROLE → B
```

## 8.2 Hypothesis for Applications to Credit, Guarantees, and Authority

If, in the future, financial institutions, public agencies, credentialing bodies, companies, regional organizations, and others operate ToraOS or compatible implementations, Relations could express:

- affiliation / Role;
- credentials / certification;
- representative Authority / delegation;
- contractual relationships;
- guarantees;
- payment / performance history;
- recommendations;
- continuing business relationships; and
- administrative residence / registration relationships.

These must not automatically become a value such as “trust score 80.” Relations needed for a housing contract differ from those needed for medical access.

The Universal Semantic Constitution of ToraOS likewise treats remuneration, HR, compensation, commercial use, rights restrictions, and similar matters as optional Decision layers that may be connected only if the relevant Subject has adopted their purpose, Scope, Authority, explanation procedure, and Correction procedure.[Internal 1]

## 8.3 Relational Capital Is Not Necessarily Non-transferable, but Neither Is It Automatically Transitive

Bidirectional connections with valuable Subjects may become Evidence explaining a Subject's social position. But “this person belongs to a trusted company” does not imply “all of this person's Actions can be trusted.”

Relational value must be bounded by Relation type, Scope, time, Authority, and Outcome. Ignoring those boundaries creates borrowed Authority, relation laundering, and reputation laundering.

# 9. Real-Outcome-driven “Growth”

## 9.1 Do Not Treat Memory Volume as Growth

The current ToraOS requirements do not use stored volume, file count, Relation count, Graph density, or test count as Growth metrics.[Internal 4][Internal 6]

This paper defines Growth of an AI OS as follows:

> **Past Source, Decisions, discomfort, failures, and Outcomes cause a better first Action or appropriate differentiation in a related later situation, and the resulting Outcome can again be verified.**

A reduction in repeated Correction is one form of Evidence, but becoming rigidly anchored to the past and losing flexibility is not Growth.

## 9.2 Outcomes Differ by Subject

The same Action may have different Outcomes when viewed from a Person, Company, or Community.

For example, if operational efficiency improves for a company while placing excessive burden on an individual, the two should not be offset into one aggregate score. The current Personal Profile also specifies that Outcome Views for different Subjects are kept separately.[Internal 6]

This becomes important in Subject federation. When multiple Subjects participate in the same real-world Action, Outcome is not reduced to one “correct answer for the world.”

# 10. A Distributed Federation of Subjects as a “Pseudo-world”

## 10.1 Not One Giant ToraOS

The long-term hypothesis of this paper is not to place the whole world inside one centralized ToraOS.

```text
ToraOS Subject A  ←→  ToraOS Subject B
       ↑                    ↓
       └────→  OtherOS C  ←─┘
```

Different Subjects, implementations, and operators maintain independent state while exchanging permitted Relations, Claims, Credentials, and Artifacts.

Therefore, final success is not “everyone uses ToraOS.” Even if ToraOS disappears and a better Fork or entirely different implementation spreads, the concept may still count as successful if an interoperable Subject-centric grammar remains.

## 10.2 Hypothesis of a Change in the Role of SaaS/SNS

Today, a common design is:

```text
people are inside the SNS
companies are inside the SaaS
```

In a Subject-centric world, the relationship may reverse:

```text
SNS, SaaS, AI, payment, storage, and public services
connect around Subjects such as people and companies
```

This is not a prediction that SaaS/SNS will disappear. Rather, they may be **relativized from places that own Subject Identity and long-term Context into Adapters providing Capabilities**. This can also be viewed as a hypothesis extending the application/data separation already proposed by Solid into AI Decision and Outcome layers.

## 10.3 The World Is Not One Truth Graph

This “pseudo-world” is not one world knowledge graph.

Each Subject has an independent Truth View and Authority, and the Views overlap through Relations as a Relational Field. Contradictory Relations may both be preserved when the dispute itself exists in reality.

This design is closer to the plurality of real society than a structure in which one central AI decides “the world is like this.”

# 11. Freedom Not to Participate and Social Friction

## 11.1 Non-participation Does Not Guarantee the Same Convenience

If a Subject-centric social foundation becomes widespread, some people may choose not to use it. However, there is no need to guarantee that choosing not to participate creates no friction or additional cost whatsoever.

Today, people are free to visit a counter instead of using an online procedure, avoid cashless payment, or avoid electronic contracts, but differences can arise in time, cost, or available services.

If machine-verifiable Relations become common in public administration, insurance, employment, and similar areas, non-participants may need paper certificates, in-person confirmation, additional review, or other alternatives.

## 11.2 But Do Not Equate Non-participation with Exclusion

On the other hand, if socially essential public services become effectively unusable, the issue is no longer merely a technical choice but one of law, policy, and rights.

ToraOS Core should not determine world-wide rules such as “which alternative route must be guaranteed at what cost.” What the Core should preserve are semantic boundaries such as:

- connection and non-connection can be explicitly represented as Relations;
- a coerced Relation is not disguised as voluntary consent;
- Authority and Effect are traceable; and
- the absence of Relations for a non-participant is not automatically interpreted as low trust.

# 12. Risks and Falsification Conditions

## 12.1 Becoming a Surveillance Foundation

The more a Subject's Source, Relations, and Outcomes are connected, the more surveillance capability may rise along with convenience. In particular, if permission to `read` and permission to `infer` are not separated, attributes that were never explicitly disclosed may be inferred through Relation paths.

The current Universal Semantic Constitution treats `ingest / retain / read / use / infer / relate / disclose / prove` as separate Actions. This is an important foundation for addressing this problem.[Internal 1]

## 12.2 Coercion of Mutual Relations

A powerful Subject such as an employer or public agency may say, “we will not provide service unless you return a mutual Relation.” Even when the relationship is formally bidirectional, that does not necessarily mean the consent was voluntary.

A Relation therefore needs to be able to express its establishment Procedure, Authority, coerciveness, objection and revocation paths, and related state.

## 12.3 Sybil Attacks and False Official Subjects

If Subjects can be created permissionlessly, fake companies, fake credentialing bodies, and fake personal Subjects can be created at scale. A name or the mere creation of a Subject must not confer official status.

Combinations of existing standards such as DID/VC, real-world Registries, third-party Recognition, and Authority Paths will be necessary.

## 12.4 Relation Laundering

An attacker may attempt to borrow relational value by forming a superficial connection to a valuable Subject. A trust calculation based only on Relation count, popularity, or short path length would be vulnerable to this attack.

## 12.5 Degeneration into a Single Social Score

If an implementer aggregates Relations into one score for convenience, the plurality proposed by this paper can easily be lost. This is a major falsification or deviation condition for the ToraOS direction.

## 12.6 Turning AI Inference into Authority

If the ability of AI to generate Relation candidates is not separated from Canonical adoption of a Relation, hallucinations can be promoted into social relationships. This is why the current Relation-admission design separates Validation, Review, and Admission.[Internal 13]

## 12.7 OSS Capture and Fragmentation

After publication, concentration around a particular company's trademark or hosting, Forks that break compatibility, maintainer burnout, vulnerability management problems, and other issues may arise. Becoming open source does not automatically guarantee decentralization.

# 13. Evaluation Plan

The concept proposed in this paper is intended to become falsifiable through the following stages.

## 13.1 E1: Recurrence Evidence in Personal Tora

Within the current Personal Tora, a past Correction should change the first Action on a naturally occurring later similar Task, with improvement confirmed through real Outcomes.

**Failure condition**: Context merely increases without reducing Corrections, or over-application of past Context increases.

## 13.2 E2: Second Subject Instance

Establish a second ToraOS with a Company or similar Subject using the same Kernel.

**Success condition**: independent Source, Authority, Decision, and Outcome can be maintained without adding a large number of Personal-specific branches to the Kernel.

**Failure condition**: a separate OS is required for Company use, or Personal Context implicitly flows into it.

## 13.3 E3: Mutual Relation

Create one-way Relations independently between a Personal Subject and Company Subject, and create a mutual Projection only when the Relations from both sides correspond.

**Success condition**: one-sided revocation, temporal differences, Role changes, third-party guarantees, and contradictions can be preserved.

**Failure condition**: mutualization requires integration into one shared Truth Record.

## 13.4 E4: Third Subject and Multi-Subject Outcome

Add a third Subject such as a Community and preserve different Outcome Views for the same Action.

## 13.5 E5: Compatibility with Another Implementation

A ToraOS Fork or independent implementation interoperates using a minimum grammar for Subject identity, Relation Statement, provenance, revocation, disclosure, and related concepts.

**Only when E5 is achieved can ToraOS be said to have progressed from a “product” toward an open architecture.**

# 14. Meaning of OSS Publication

## 14.1 Publication Need Not Wait for Completion

If the purpose of open-sourcing ToraOS is not to sell a completed product but to place the idea and implementability of a Subject-centric AI OS in the world, completion of v1.0 is not a prerequisite for publication.

Instead, at publication time the project can explicitly distinguish:

- implemented;
- experimental;
- designed but not implemented;
- research hypothesis; and
- social future prediction.

In that case, incompleteness itself becomes part of the research state.

## 14.2 ToraOS as a Reference Implementation

The success condition of ToraOS OPEN should not be “number of ToraOS users.”

> ToraOS may be the first Reference Implementation of a Subject-centric architecture.

It may be Forked. It may be rewritten in another language. It may be replaced by a more usable implementation. Even if the name ToraOS disappears, it would remain consistent with the author's objective if the grammar in which Subjects have independent Context and Authority, connect through Relations, and grow from Outcomes survives.

## 14.3 Minimum Requirements Before Publication

From the position of this paper, at least the following are necessary before publication.

1. Remove Personal / Raw / Secret material from code intended for public release.
2. Decide the LICENSE.
3. Separate Current implementation from Future Vision in the README.
4. Publish a public version of the Manifesto or Semantic Constitution.
5. Define minimum terminology for Subject, Relation, Authority, and Outcome.
6. Clearly disclose known major unimplemented areas and STOP conditions.
7. Create Issue / Discussion routes through which outsiders can falsify, Fork, and compare the work.

Because the current private README explicitly states that a license has not been approved, the project should not be called OSS until this Gate is crossed.[Internal 3]

# 15. Limitations of This Research

First, ToraOS is currently centered on Personal Tora used in practice by a single author, and federation of multiple independent Subjects has not been empirically demonstrated.

Second, much of the code was developed with AI assistance. Tests and fresh Reviews exist, but no independent academic research team has conducted a code audit or formal verification.

Third, the Current code's Authority Map addresses technical Authority over field writers, whereas the social Authority discussed in this paper is broader. The common vocabulary and boundary between the two require further formalization.

Fourth, the idea that Relations can produce trust, guarantees, or Authority is already widely present in existing research. Comparative experiments are needed to determine whether the mutual-Relation model proposed here is actually superior to existing SSI, Web of Trust, VC, or reputation models.

Fifth, the discussion that SaaS/SNS may be reorganized around Subjects is a future prediction, not a conclusion that follows from the implementation Evidence in this paper.

Sixth, applications to public administration, healthcare, employment, and similar domains cannot be determined by technology alone. Law, ethics, discrimination, administrative burden, rights guarantees, and institutional design require collaboration with specialists in those fields.

# 16. Discussion

ToraOS development began with the simple desire to make AI “remember more.” Over long-term use, however, the real need was not storage capacity.

Who said it? What was the Original Source? Was it merely the AI's interpretation? Who had the Authority to decide? When was that Decision valid? Was it actually used? What happened? What should be changed next time?

As these questions are separated one by one, AI becomes less like a “chat system with a giant memory” and more like an OS handling the continuous state of a Subject.

When Subject is generalized from Person to Company and Community, what was a Personal AI problem becomes a social-structure problem. The Contexts of different Subjects must be connected socially through Relations without being merged into one center.

At that point, Relation is no longer merely a Knowledge Graph edge. A bundle of relationships containing self-report, confirmation from the counterpart, third-party guarantees, Authority, time, and Outcome may become a path explaining real-world trust or Authority.

At the same time, this structure can be repurposed for surveillance, exclusion, Social Scores, or concentration of Authority. The value of ToraOS therefore does not lie in “connecting everything,” but in **not losing the meaning, grounds, Authority, disclosure, revocation, and falsifiability of a connection**.

# 17. Conclusion

This paper redefined ToraOS not merely as a Personal AI OS, but as a **subject-centric, evolving AI OS**.

Its central principles are as follows.

1. **One OS, any Subject**: Person, Company, Community, and others are types of Subject, not separate OS products.
2. **Independent Context and Authority per Subject**: even when Subjects know the same Entity, their knowledge, canonical state, Decisions, and secrets are separate.
3. **A Relation is a directional Claim**: preserve A→B and B→A separately; do not infer mutuality, but project it from Evidence.
4. **Mutual Relations may generate relational value**: trust, guarantees, Authority, credentials, membership, and similar concepts are represented as verifiable Relation Paths rather than a central score.
5. **Growth is judged through Outcome**: Growth is not memory or Graph volume but a loop in which past Evidence improves the next Action and its result returns to Correction.
6. **The world is not owned by one OS**: the long-term goal is a distributed Relational Field in which independent Subjects and different implementations connect through Relations.
7. **The spread of ToraOS itself is not the final objective**: it is enough if the idea survives through a public specification, Reference Implementation, Forks, and independent implementations.

Current code already contains implementations supporting Source separation, field Authority, Context, Relation admission, Outcome, Correction, and related mechanisms. In contrast, multi-Subject federation and social use of mutual Relations are unimplemented.

The conclusion is therefore not “ToraOS is the future world OS.”

> **An architecture in which Subjects themselves hold AI Context and Authority, independent Subjects connect through verifiable Relations, and the system is continuously updated from real Outcomes is a promising research direction distinct from today's platform-centric AI. ToraOS is one Reference Implementation for testing that hypothesis through real code and real use.**

If the hypothesis is wrong, the published code and design should allow it to be falsified. If a better implementation appears, it should replace ToraOS. The purpose of ToraOS OPEN is not to enclose a finished product, but to place this question in the world in a falsifiable form.

---

# Internal Primary Sources

**[Internal 1]** ToraOS, “Universal Semantic Constitution / Tora Core Constitution,” revision `TOROS-UNIVERSAL-SEMANTIC-CONSTITUTION-20260812-006`, Current Authority Layer 1, 2026.

**[Internal 2]** ToraOS, “ToraOS concept / implementation-preparation chat,” historical chat-analysis log, source date 2026-05-27.

**[Internal 3]** ToraOS private repository, `imprint283-boop/toraos-shadow-harness`, main commit `3c4ccac069034b75f776b0b0109b9964f5003a5a`, README and repository tree, accessed 2026-08-29.

**[Internal 4]** ToraOS, “ToraOS Requirements Definition v1.2,” document `TOROS-RD-20260719-001`, adopted 2026-07-19.

**[Internal 5]** ToraOS, “ToraOS OPEN Requirements / Semantic Definition v0.3 Integrated Version,” revision `TOROS-OPEN-V03-20260810-001`, noncanonical future candidate, 2026-08-10.

**[Internal 6]** ToraOS, “Personal Tora Constitution / Profile,” revision `TOROS-PERSONAL-TORA-CONSTITUTION-PROFILE-20260825-008`, Current Authority Layer 2, 2026.

**[Internal 7]** ToraOS source code, `toraos_shadow/authority_map.py`, commit `3c4ccac...`, 2026-08-29.

**[Internal 8]** ToraOS source code, `toraos_shadow/context_reasoning.py`, commit `3c4ccac...`, 2026-08-29.

**[Internal 9]** ToraOS, `AUTONOMOUS_CONTEXT_TRAJECTORY_GROWTH_LOOP_CONTRACT.md`, revision `TOROS-AUTONOMOUS-CONTEXT-GROWTH-LOOP-20260826-001`, 2026.

**[Internal 10]** ToraOS, `CURRENT_AUTHORITY_REGISTRY.md`, revision `TOROS-CURRENT-AUTHORITY-REGISTRY-20260828-038`, 2026-08-28.

**[Internal 11]** ToraOS source code, `toraos_shadow/shared_state.py`, commit `3c4ccac...`, 2026-08-29.

**[Internal 12]** ToraOS source code, `toraos_shadow/relation_operational.py`, commit `3c4ccac...`, 2026-08-29.

**[Internal 13]** ToraOS source code, `sql/postgresql/020_relation_admission.sql`, commit `3c4ccac...`, 2026-08-29.

**[Internal 14]** ToraOS source code, `toraos_shadow/live_ordinary_growth_loop.py`, commit `3c4ccac...`, 2026-08-29.

**[Internal 15]** ToraOS source code, `toraos_shadow/outcome_growth_correction.py`, commit `3c4ccac...`, 2026-08-29.

**[Internal 16]** ToraOS source code, `toraos_shadow/ordinary_owner_ingress.py`, commit `3c4ccac...`, 2026-08-29.

**[Internal 17]** ToraOS source code, `toraos_shadow/live_source_semantic_intake.py`, commit `3c4ccac...`, 2026-08-29.

**[Internal 18]** ToraOS source code, `toraos_shadow/codex_sdk_controller.py`, commit `3c4ccac...`, 2026-08-29.

**[Internal 19]** ToraOS GitHub Pull Request #36, “Add nonactivated Codex Hook payload bridge,” merged into commit `3c4ccac...`, 2026-08-29 JST.

**[Internal 20]** ToraOS, “ToraOS OPEN Empirical Test / Falsification / Publication Gate v0.1,” revision `TOROS-OPEN-GATE-20260810-001`, future research plan, 2026-08-10.

# External References

**[1]** E. Mansour, A. V. Sambra, S. Hawke, M. Zereba, S. Capadisli, A. Ghanem, A. Aboulnaga, T. Berners-Lee, “A Demonstration of the Solid Platform for Social Web Applications,” *Proceedings of the 25th International Conference Companion on World Wide Web*, pp. 223–226, 2016. DOI: 10.1145/2872518.2890529.

**[2]** Solid Community Group, “Solid Protocol,” Version 0.11.0, Solid Project, accessed 2026-08-29.

**[3]** W3C, “ActivityPub,” W3C Recommendation, 23 January 2018.

**[4]** W3C, “Decentralized Identifiers (DIDs) v1.1: Core architecture, data model, and representations,” Candidate Recommendation Snapshot, 5 March 2026.

**[5]** W3C, “Verifiable Credentials Data Model v2.0,” W3C Recommendation, 15 May 2025.

**[6]** W3C, “Bitstring Status List v1.0,” W3C Recommendation, 15 May 2025.

**[7]** W3C, “PROV-O: The PROV Ontology,” W3C Recommendation, 30 April 2013.

**[8]** Z. Zhang, X. Bo, C. Ma, R. Li, X. Chen, Q. Dai, J. Zhu, Z. Dong, J.-R. Wen, “A Survey on the Memory Mechanism of Large Language Model based Agents,” arXiv:2404.13501, 2024.

**[9]** J. Zheng, C. Shi, X. Cai, Q. Li, D. Zhang, C. Li, D. Yu, Q. Ma, “Lifelong Learning of Large Language Model based Agents: A Roadmap,” arXiv:2501.07278, 2025.

**[10]** V. Vizgirda, R. Zhao, N. Goel, “SocialGenPod: Privacy-Friendly Generative AI Social Web Applications with Decentralised Personal Data Stores,” arXiv:2403.10408, 2024.

**[11]** A. Jøsang, R. Ismail, C. Boyd, “A survey of trust and reputation systems for online service provision,” *Decision Support Systems*, Vol. 43, No. 2, pp. 618–644, 2007. DOI: 10.1016/j.dss.2005.05.019.

**[12]** K. Avrachenkov, D. Nemirovsky, K. S. Pham, “A survey on distributed approaches to graph based reputation measures,” *SMCTOOLS*, 2010. DOI: 10.4108/smctools.2007.2027.

**[13]** A. Narayanan, V. Toubiana, S. Barocas, H. Nissenbaum, D. Boneh, “A Critical Look at Decentralized Personal Data Architectures,” arXiv:1202.4503, 2012.

**[14]** Z. Lin, X. Hao, R. Fu, S. Cui, K. Chen, C. Li, Z. Li, F. Xiong, “A Survey on Long-Term Memory Security in LLM Agents: Attacks, Defenses, and Governance Across the Memory Lifecycle,” arXiv:2604.16548, 2026.

---

## Author's Note

This paper describes the author's individual research and development activity and does not represent the official views of any company, corporation, organization, public institution, or other entity with which the author is associated. Even when a real organization is used as an example, that does not mean the organization has adopted, approved, or operates ToraOS.
