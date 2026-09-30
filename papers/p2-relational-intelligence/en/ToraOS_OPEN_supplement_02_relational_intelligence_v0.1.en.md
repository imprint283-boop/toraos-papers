---
document_id: TORAOS-OPEN-SUPPLEMENT-02-20260919
series: ToraOS OPEN paper supplement
supplement_number: 2
version: 0.1
date: 2026-09-19
language: en
translation_of_language: ja
translation_state: PRIVATE_FAITHFUL_TRANSLATION_DRAFT
status: NONCANONICAL_RESEARCH_DRAFT
current_authority: false
implementation_adoption: false
empirical_results: none
---

# ToraOS OPEN Supplementary Paper 2
## External Intelligence Complementation Through Variations in the LLM Semantic Map and Directional Relations
### Generalization, Hallucination, and Relational Intelligence in Community Tora

**Tsubasa Nakagawa**  
Independent Research and Practical Development  
Draft v0.1 / September 19, 2026

**Paper type**: Position paper, conceptual model, and evaluation plan.  
**Position**: The second supplementary paper following the main paper and Supplement 1.  
**Status**: Pre-peer-review and pre-author-confirmation draft. It presents research hypotheses and does not modify current semantic contracts, implementation, or adoption state. No new LLM experiment or effect measurement has been conducted.  
**Preparation note**: This document originated in dialogue with the author, with generative AI assisting literature research, issue organization, and writing. Metaphors and categorical statements from the dialogue were not adopted directly as empirically established explanations; their definitions and limitations are reorganized below.

## Abstract

The capabilities of large language models (LLMs) are not uniform across all objects and questions. This paper connects the metaphor of “variations in the density of a map of words” to the external Relation representation of the subject-centric AI architecture ToraOS OPEN. However, it does not reduce training-data frequency, geometry of internal representations, task performance, context-dependent processing, and sufficiency of evidence to one density measure. It distinguishes an LLM's internal representation from external Claims, Evidence, and Decision history maintained by each Subject and addresses task-level complementation through connections between them.

The central hypothesis is that even when a model has difficulty handling a problem directly, connecting relevant principles with permitted concrete facts, real experience, and applicability conditions may improve Decision and Action in an unseen situation. Directional Relations in that setting add not only information but also boundaries distinguishing grounds, dependency, adoption, and provenance, representing what may be referenced, inferred, and adopted. By separating semantic direction, exploration direction, claimant, origin of Evidence, and permission to use, the architecture seeks to prevent one-way Relations from being made falsely mutual, reproduced material from being treated as independent Evidence, and Inference from being turned into fact.

Complementation in Community Tora does not fuse each Subject's Context or the weights of their LLMs. It means using, only to the necessary extent, paths of Evidence and experience effective for the current Task while retaining differences among Subjects. This paper provisionally calls this ability “relational intelligence,” but does not claim the existence of an independent consciousness or a new universal Truth.

Candidate contributions of this paper are an operational decomposition of “density,” a conceptual model in which direction changes which paths are adoptable, and an evaluation plan comparing cross-Subject complementation with error amplification. It does not treat directional graphs or retrieval augmentation themselves as new technologies. ToraOS-specific value should be judged empirically against strong, simpler comparison methods.

**Keywords**: LLM, semantic representation, knowledge unevenness, generalization, directional Relation, provenance, grounded generation, Subject boundary, distributed knowledge complementation, Decision history

## Contents

1. Positioning and Research Questions
2. Redefining the LLM Semantic Map and Its Variations in Density
3. The Value of Generalization and Conditions for External Complementation
4. What Relations Provide to an LLM
5. Directional Relations and the World Available for Adoption
6. Mutual Complementation Across Subjects Through Community Tora
7. Failure Conditions, Falsification Hypotheses, and Evaluation Plan
8. Implications for ToraOS OPEN and Conclusion

Appendix A: Example Relation Description for Evaluation  
Appendix B: Status of Major Propositions  
References and Source Manuscripts

# 1. Positioning and Research Questions

## 1.1 Relationship to the Main Paper and Supplement 1

The main paper, *ToraOS: A Proposal for a Subject-Centric, Evolving AI OS Architecture*, proposed keeping each Subject's Context and Authority independent, connecting Subjects with Relations carrying provenance, direction, time, and Scope, and returning real Outcomes and Corrections to future Action. The separation of one-way Claims from mutual confirmation is already a central element of the main paper.[Base 1]

Supplement 1, *ToraOS Subject Ontology Concept Note v1.0*, examined what may be treated as a Subject, how a real-world referent differs from a View established about that referent, and whether different present Views can coexist for the same object. It also treated the semantic direction of a Relation and who observed, asserted, or inferred it as separate axes, and distinguished the existence of a Relation from whether it should be used or trusted in the current Task.[Base 2]

This paper does not further expand the range of Subjects. What it adds is the connection between **how an LLM may use independent Views and directional Relations and how that use might improve understanding, inference, adoption, and Action**. Accordingly, this paper does not propose “adding arrows to Relations” as a new mechanism; it connects existing directionality to Task-dependent information selection and evaluation.

| Document | Central question | Role relative to this paper |
|---|---|---|
| Main paper | Whose Context, Authority, and real Outcomes govern continuous AI use? | Backbone of the Subject-centric architecture |
| Supplement 1 | What can be represented, and how can different Views coexist? | Examination of representation targets and Subject boundaries |
| Supplement 2, this paper | How does an LLM follow, complement, and use that representation for Decision? | Cognitive use conditions and falsifiable evaluation |

## 1.2 Problem Setting

The starting question is: “If an LLM already contains broad general knowledge, what is worth preserving in external memory?” This paper focuses not only on adding knowledge, but on conditions that exist only for a particular person, organization, or project; reasons a choice was not adopted; failures discovered only after execution; and histories of change or withdrawal.

However, rarity itself is not treated as value. Information that is unrelated to the current question, cannot be verified, or is not permitted for use cannot guide a Decision merely because it is rare. Conversely, even general knowledge may be important when a precise procedure or safety condition must be established. The question is not only “which region is sparse,” but **what is missing, which added information changes which Decision**.

The paper narrows its research questions to three. First, how can the density metaphor be translated into observable task performance and states of Evidence? Second, do Relations preserving direction, provenance, and Scope improve inference and adoption compared with indiscriminately passing the same information? Third, is connection that preserves differences among Subjects more effective than a method that merges information into one representation, and under what conditions?

## 1.3 Method and Scope of Claims

This is a conceptual study comparing existing manuscripts, the ToraOS semantic grammar, and primary literature on LLMs, retrieval augmentation, and knowledge representation. Except where explicitly stated, teams, methods, application processes, and numerical examples are hypothetical explanatory examples rather than real operational data.

This paper does not audit the latest ToraOS code. It does not reinterpret the implementation report in the main paper as of August 29, 2026 as evidence of current Runtime status or implementation Evidence for the proposals in this paper. Separation of Original Source, Claim, and Inference, conditional Relations, and Authority boundaries described in current documents are referenced as consistency conditions; their documentation alone does not demonstrate effects.[Base 1][Base 3]

Statements such as “can improve” or “can reduce” distinguish cases where prior research observed an effect from cases where this paper states an unverified hypothesis. For the latter, Chapter 7 states comparison conditions and falsification directions.

# 2. Redefining the LLM Semantic Map and Its Variations in Density

## 2.1 The Map Is an Explanatory Metaphor, Not One Internal Structure

Transformer models convert input tokens into numerical representations and process them through attention and layer-wise transformations. The embedding table at input, context-dependent internal representations, learned weights, and output probability distributions are not the same thing. The picture in which “words are placed at coordinates and the model answers by looking at that map” therefore does not literally describe the mechanism of the entire model.[1]

Ethayarajh's study of the geometry of contextualized representations showed, for BERT, ELMo, and GPT-2, that representation distributions and the context-dependence of the same word vary by layer. The study illustrates the limitations of explaining each word as one fixed point, but does not establish one identical internal arrangement for all current models.[2]

In this paper, “semantic map” is used as a general metaphor for understanding the ability to handle words, concepts, and relations in context. It does not mean a directly observed map inside a specific GPT, a precise ranking of density by domain, or the location of consciousness.

## 2.2 Do Not Reduce “Density” to One Measure

The dialogue used words such as “dense” and “sparse” to cover several different properties. If they are not separated, one may incorrectly infer that a field with more text is more correct, or that a person with more Relations is more trustworthy. This paper separates at least the following five properties.

| Property distinguished | Meaning / observation in this paper | Not equated with |
|---|---|---|
| Training support | Existence and diversity of training examples related to a fact or expression; unobserved if the training material is unknown | Accuracy or recency |
| Representation geometry | Distances and distributions measured for a specified model, layer, and input set | Amount of knowledge or depth of understanding |
| Task proficiency | Correct answers, condition discrimination, and handling of counterexamples on a specified question set | The model's self-reported confidence |
| Sufficiency of external Evidence | How well the facts and conditions required by a question can be supported by verifiable material | Number of documents or citations |
| Task-time usability | Whether necessary Evidence can actually be reached and used within Authority, search budget, and time limits | Total amount stored |

Kandpal et al. examined, for the models and factual questions they studied, the relation between the number of relevant documents in pretraining data and answer accuracy, and showed that retrieval augmentation could reduce dependence on training-time support. This does not provide universal rankings such as “English density 10, Japanese density 8,” nor does it directly determine performance on every reasoning task.[3]

Likewise, high local density in an embedding space does not by itself mean rich Evidence. Polysemy, representational bias, and abstraction may all be involved. In this paper, “complementing a sparse region” means, as a rule, **supplying Evidence, conditions, distinctions, or experience missing from the current Task**, not directly increasing local vector-space density.

## 2.3 Internal Representation, the Subject's External State, and Current Context

Three levels must be separated when discussing complementation.

The first is the LLM's trained parameters and processing ability. The second is external state held by the Subject: original material, Claims, Relations, adoptions, real Outcomes, and Corrections. The third is Context selected for the current question and actually provided to the model. Retrieval augmentation is a precedent for combining knowledge held in model parameters with external memory.[5]

The main focus of this paper is complementation that passes appropriate information from the second level to the third while keeping model weights fixed. An increasing history in external state is different from retraining the model itself specifically for a person. Selections and Corrections observed during dialogue are also treated as Decision history with a situation and Scope rather than immediately generalized into universal personal traits.[Base 1][Base 2]

**Figure 1: Connection addressed by this paper**

```text
Capability of a fixed LLM + current question
                 ↑
       Context selected for the Task
                 ↑
Subject's original material, Relations, Decision history, real Outcomes
     + permitted reference information from other Subjects
```

The arrows in this diagram represent a route by which information is supplied as input. They are not proof of causation or rewriting of model weights.

## 2.4 Separate Absence from Invisibility

Even when Evidence cannot be found, nonexistent, unrecorded, not acquired, missed in retrieval, inaccessible, undisclosed, and expired must not be collapsed into the same state. Particularly across Subjects, invisibility must not be used to infer that the other Subject lacks ability or experience.

Accordingly, an implementation of “density” should prefer states such as “no record of a required condition,” “Evidence not reached,” “outside disclosure Scope,” or “conditions in conflict” over a single color called “sparse.” Different unknown states imply different next Actions: search, inquiry, verification, or hold.

# 3. The Value of Generalization and Conditions for External Complementation

## 3.1 Generalization Does Not Occur Only in Sparse Domains

Generalization means using acquired structure in unseen situations rather than merely repeating exactly the same training or example cases. But unseen problems differ: close transformations of known examples, new combinations, transfer of a rule, or major environmental changes. These difficulties should not be collapsed into one category.

SCAN by Lake and Baroni is a precedent that asks whether a model can systematically handle combinations under particular train/test splits. Those results concern the recurrent models studied at the time and do not directly establish the limitations of current LLMs. What this paper borrows is the evaluation principle of separating repeated examples from transfer to unseen combinations.[4]

The paper therefore rejects a binary division in which “dense domains are memorization and sparse domains are intelligence.” Well-known fields contain difficult unseen problems, while some rare-fact problems require only acquisition of one fact. Information rarity and inference difficulty are different axes.

## 3.2 Value Arises When a Deficiency Matches a Useful Connection

The hypothesis is not that sparsity itself creates value, but that **additional information is especially valuable when the ability to handle relevant principles, access to necessary facts, and the ability to distinguish conditions complement one another**.

Consider a hypothetical attempt to improve an organization's application-processing procedure. An LLM may handle general workflow decomposition and exception processing but may not know the organization's authorized approver, a work location with no communications, or why an existing procedure failed. External information fills those specific gaps. On the other hand, providing only the approver's name does not automatically make a new procedure design correct.

The minimum unit is therefore not “density” across an entire domain, but Claims and conditions required by the question. If evaluation of a candidate depends on a communications condition, confirming that condition may be highly valuable. Adding ten similar articles that do not change the evaluation does not fill the missing requirement.

## 3.3 Separate Fact Acquisition, Inference, and Exploration

External complementation has different roles. First, acquire a previously unknown specific fact. Second, derive a new proposal or conditional conclusion from known principles and the acquired fact. Third, design observation or experimentation for a problem that still has no answer.

Separating these avoids two extremes. One is inventing a fact by inference. The other is refusing to form any new hypothesis or solution merely because there is no direct record. Even for a new problem, a conclusion may be provable from stated rules, or a verifiable experiment may be designed.

This paper does not adopt “stop whenever something is unknown” as a general principle. Unconfirmed facts remain unconfirmed; Inference states its Evidence and assumptions; execution checks permission and reversibility. What must stop is treating an unknown as known or crossing an unresolved Authority boundary.[Base 3]

## 3.4 Evaluating Complementation Value

Conceptually, complementation value is judged by how much the Task result improves relative to a condition with no added information. Evaluation should record not only wrong answers, but also traceability of Evidence, unnecessary holds, confirmation burden, time, and computation cost separately.

If the burden of organizing, maintaining, and querying information exceeds the improvement, practical value is not established even when useful information was obtained. Conversely, even if the raw error rate changes little, effects such as no longer using withdrawn Evidence or correctly distinguishing whose adoption a Decision represents should be evaluated independently. These should not be offset against each other in a single total score.

# 4. What Relations Provide to an LLM

## 4.1 Adding Information and Adding Boundaries of Interpretation

A simple association might record only “Document A is related to Method X.” A semantically meaningful Relation distinguishes relationships such as “Document A cites Method X” or “Team B adopted Method X under Condition C.” It can further allow tracing who made the Claim, which material supports it, when it was valid, and within what Scope.

RDF is prior art representing Relations as subject-predicate-object triples, and PROV provides vocabulary for generation, derivation, and responsibility. Directional Relations and provenance themselves are not novel claims of this paper.[9][10]

The additional ToraOS question is how such representations connect to Subject-specific Decisions, use conditions, Corrections, and future Action. A Graph is a projection for finding and explaining information; it is not the sole canonical owner replacing Original Source or the grounds of a Relation.[Base 3]

## 4.2 Descriptive Constraints and Execution Constraints

Instructing a model in text “do not speculate” is different from designing a system that does not allow an unconfirmed value to pass into an official output or operation. Passing Relations into a prompt alone still leaves room for the model to misunderstand their meaning or add explanations unsupported by Evidence.

For example, in a limited report that should show only confirmed approvers, the selectable values can be constrained to a verified set, with unconfirmed cases left blank or marked for confirmation. This can mechanically prevent fabrication in that field. It does not, however, prove that the original roster is correct or that surrounding free text is accurate.

Fact acquisition, structuring, Context selection, generation, output validation, and operation authorization should therefore be considered separately. Not every step must be made heavy; necessary checks should be placed at boundaries where errors matter.

## 4.3 Relations May Reduce Hallucination, but Do Not Make It Zero

Early RAG research reported that generative models using external memory produced more factual outputs than comparison systems. Shuster et al. also reported, by human evaluation, reduced hallucination from retrieval on the knowledge-grounded dialogue Tasks they studied. These results support the possibility of retrieval-based complementation, but do not prove that arbitrary Relation structures eliminate error.[5][6]

This paper measures at least three things separately: disagreement with reality or an evaluation answer, lack of support in presented Evidence, and misattribution of another person's statement, speculation, or adoption. An answer can be faithful to an incorrect document yet wrong about reality.

The presence of a citation is also insufficient. ALCE by Gao et al. demonstrates the need to evaluate content correctness and citation quality separately. This paper likewise separates “a link to Evidence exists” from “that Evidence supports this Claim.”[13]

## 4.4 Failure Can Occur Before and After a Relation

A process using Relations may fail because of an incorrect original document, misidentification of a person or object, loss of conditions during extraction, selection of an outdated Relation, retrieval failure, or overgeneralization in output. This is why one aggregate “hallucination rate” makes it difficult to identify where improvement is needed.

Self-RAG examined generation that evaluates when retrieval is needed and assesses retrieved/generated material. *Lost in the Middle* showed for the models studied at the time that utilization performance varied with the position of required information. Merely putting information into Context is not evidence that it was used correctly.[8][12]

An effective design does more than increase the number of Relations. It preserves states such as missing, conflicting, expired, and retrieval failed in the output. When Evidence is insufficient, it separates what can be answered, what can be proposed conditionally, and what cannot be decided.

# 5. Directional Relations and the World Available for Adoption

## 5.1 Distinguish Four Kinds of Direction or Role

Direction can enrich meaning, but mixing different kinds of arrows in one diagram can increase misunderstanding. This paper adopts the following distinctions as basic.[Base 2][9][10]

| Distinction | Example | What must not be derived from it |
|---|---|---|
| Semantic direction of a Relation | A refers to B | B also refers to A |
| Origin of Claim / Observation / derivation | C reports “A refers to B” | A itself testified to that |
| Exploration direction | From B, reverse-search for “documents referring to B” | A new fact reversing the original semantic direction |
| Permission for use / disclosure | B may be used for internal comparison | B may be redistributed to a third party |

Semantic direction means “what Relation is asserted between which things”; the claimant is separate. A text about A is not necessarily a Claim by A. Likewise, a provenance arrow indicates derivation of data, not necessarily real-world causal action.

## 5.2 Reverse Lookup, Inverse Relations, and Mutual Relations

Suppose there is a record “Feature A depends on Component B.” Reverse-looking from B to A is an operation for finding what may be affected by changing B. It is not a Claim that “B depends on A.”

In some vocabularies, “A is parent of B” and “B is child of A” express the same content using inverse Relations. But “A trusts B” and “B trusts A” are independent. Whether both parties have confirmed the same relationship is yet another matter, distinct from whether the predicate itself is symmetric.

The mutuality in the main paper is a Projection created when independent Statements from both sides can be verified as referring to the same real-world relationship. This paper likewise preserves the original Statements, Scope, and time so that mutual-confirmation state can be re-evaluated after a change or revocation on one side.[Base 1][Base 2]

**Figure 2: The chosen path differs by the question even for the same objects**

```text
Feature A ── depends on ──→ Component B

To learn A's operating conditions: follow A to B
To learn the impact of changing B: reverse-search from B to A

Neither exploration adds the Claim “B depends on A”
```

## 5.3 An Arrow Alone Does Not Establish Causation

The sequence “Decision → execution → result” is important as event history. But a later result is not necessarily caused only by that Decision. Other changes, environment, operators, or selection bias may matter.

Causal inference distinguishes observed association from changes under intervention and makes assumptions explicit. Pearl's treatment emphasizes that causal conclusions depend on assumptions as well as data.[11]

Accordingly, even if a ToraOS Relation is labeled “cause,” the label itself is not proof. Observation, the author's explanation, comparative support, intervention support, and an unverified hypothesis should be distinguished. Searching backward from a result for candidate causes is possible, but a reached candidate must not immediately be promoted into an established cause.

Likewise, if A trusts B and B trusts C, A does not necessarily trust C. Using a chain of Relations for inference requires rules that depend on each Relation's meaning and conditions. Arbitrary arrow composition is not given transitivity.

## 5.4 Adoption Is Not Decided Merely by “Nearness” or “Count”

Suppose Method X has ten introductory articles and one failure report. If all ten articles cite the same report, they are not ten independent demonstrations. Provenance can reveal this duplication. Even reports from different Subjects may depend on common material or measurement methods, so issuer count alone does not establish independence.

Conversely, if a failure report concerns an environment different from the current Task, it should not be generalized to every condition. Evaluation of adoption candidates depends less on superficial similarity to a method than on the conditions under which success or failure occurred, counterexamples, actual use, and the Goal of the deciding Subject.

For Subject i, Task q, time t, and exploration budget b, the conceptual model expresses usable candidate paths as:

```text
P_i(q,t,b) = the set of paths that can be discovered and confirmed within budget
             and satisfy identity matching, permission to use, time, and Scope
```

This notation does not guarantee completeness of search or truth. It limits what is being evaluated. After a path is found, the support provided by the Evidence, condition fit, contradictions, and alternative explanations still need examination. Depending on vocabulary and Claim importance, an unconfirmed path can be separated and retained as an unconfirmed candidate rather than merely discarded.

Adoption as a reference candidate, adoption as grounds for an answer, adoption into a Subject's policy, and permission to execute are also separate. The fact that another Subject adopted X may be one reason for this Subject to consider X, but is not automatic approval.

In this sense, direction does not change reality itself. It changes **the Relations a Subject can distinguish for a question and the range of candidates it can justify adopting**.

# 6. Mutual Complementation Across Subjects Through Community Tora

## 6.1 A Common Model and Different External Experience

Even when multiple Subjects use the same LLM, the external materials, activities, Decisions, and real Outcomes they retain can differ. The complementation discussed here primarily comes from those differences. Merely running the same model multiple times is not treated as creating independent expertise or observations.

Summarizing the same material repeatedly with the same model does not create independent real-world experience. The value hypothesis of Community Tora therefore depends not on the number of people or agents, but on whether the current Task can reach different observations, conditions, and reasons for Decisions.

A Community may exist as one Subject with an explicit decision procedure, or merely as a Scope in which independent Subjects connect. A single representative or one shared Goal for all participants is not assumed by default.[Base 1][Base 3]

## 6.2 Borrow Without Blending

Information used across Subjects is not dissolved into one summary without origin. It preserves whose Observation, Claim, adoption, or Outcome it was. The receiving Subject forms a new hypothesis about applying it to its own conditions and, where necessary, returns to its own Decision procedure.

**Figure 3: Basic form of cross-Subject complementation**

```text
Subject A: original material, conditions, Decision, real Outcome
         ↓ permitted reference information
Subject B: compare with current Task → application hypothesis → Decision under B's procedure
         ↓ permitted execution and observation
       B's own real Outcome and Correction
```

What is shared need not be all Raw Context. It may be limited to what is necessary: a case with explicit conditions, a particular Claim, an artifact, or a verifiable reference to Evidence. When the Original Source cannot be disclosed, the fact that the recipient cannot directly verify it is preserved rather than labeling unseen Evidence “verified.”[Base 2][Base 3]

When connecting different vocabularies, do not immediately assume “the same word means the same object” or “similar descriptions indicate the same Relation.” Mapping between referents and vocabulary transformations have their own provenance and uncertainty. If that mapping is wrong, every later path may attach to the wrong referent.

## 6.3 Example in Which Complementation Leads to a New Proposal

Consider three hypothetical teams. A reports success using application-processing Method X in a small-scale operation that retained double-checking. B reports that it also used X but exception handling became a bottleneck at high volume. C reports using a different Method Y in a low-connectivity environment and encountering difficulties with later reconciliation.

If these records are collapsed into “one positive vote for X, one negative vote for X, and Y also has problems,” transferable knowledge is lost. If conditions and paths are preserved, Subject D can separately reference A's double-checking, the exception condition found by B, and the later-reconciliation issue reported by C.

D's LLM may construct a new operational combination from those pieces. That new combination, however, is not thereby empirically demonstrated by A, B, or C. It is presented as a new Inference: “this combination may work under D's conditions,” and is evaluated through a permitted small trial and its Outcome.

The value of this example lies not only in copying other people's conclusions. It lies in **discovering choices or checks that the receiving Subject did not have, through differences in conditions embedded in other Subjects' experience**. Negative transfer caused by dropping assumptions must also be measured.

## 6.4 Mutuality Does Not Guarantee Quality

Confirmation by two parties contains different information from a Claim by only one party. Yet both parties may misunderstand the matter, rely on the same false information, or collude in a false statement. Mutual confirmation indicates the confirmation state of a relationship; it does not guarantee universal correctness of its content.

Complementation can also be one-way. If an owner of information discloses it to another Subject and the receiver uses it effectively, symmetric provision is not required. Conversely, participation by both parties must not be interpreted as permission to share secret information.

Mutuality, strength of Evidence, expertise, Authority, and permission to use must not be collapsed into one trust score. They answer different questions.

## 6.5 Definition and Boundary of Relational Intelligence

This paper defines “relational intelligence” as **a system-level ability to select paths from external information while preserving differences among Subjects, infer while distinguishing Evidence from assumptions, and then verify and correct the result for the current Task**.

This is not a Claim that a new capability automatically emerges inside the LLM. It is a working concept for measuring what improvement appears at the level of the whole system when retrieval, knowledge representation, Authority management, model reasoning, user Decision, and observation of real Outcomes work together.

GraphRAG is prior work using graph structure and aggregated information to answer questions about an entire document corpus. Its “community,” however, means a group of related nodes inside a graph and is not synonymous with Community Tora composed of people or organizations. Improvements reported for summarization in that work are not extended here into Evidence of preserved Authority across Subjects or elimination of hallucination.[7]

# 7. Failure Conditions, Falsification Hypotheses, and Evaluation Plan

## 7.1 Complementation Can Also Amplify Error

External information can complement capability, but it can also provide a path to the wrong conclusion. PoisonedRAG showed, in the RAG configurations studied, that malicious insertion into a knowledge base can manipulate answers. This demonstrates again that the form “there is external Evidence” does not itself guarantee safety.[14]

For ToraOS, the following failures should be observed separately. This table is not a measurement of their incidence; it is a list of evaluation items for testing the proposed method.

| Failure | What happens | Counterexample to test |
|---|---|---|
| Misidentification / wrong mapping | Different person, version, or term is connected as the same referent | Same names, renamed objects, similar predicates |
| Direction reversal | Citation becomes cited-by; dependency becomes reverse dependency | Counterexample where only one direction is valid |
| Provenance laundering | Reposts or AI summaries are counted as independent Evidence | A group of documents copied from one common original |
| Loss of conditions / time | Past success or expired permission is used as current | Task with one changed condition; one-sided revocation |
| Grounded wrong answer | Fidelity to a wrong document is treated as correctness | Plausible false material; contradictions among materials |
| Excessive stopping | Useful hypotheses are rejected merely because Evidence is incomplete | Unseen Task solvable from explicit rules |
| Boundary violation | Secret attributes are inferred or redistributed from readable information | Cases where permissions differ by Action |
| Negative transfer | Another Subject's success conditions are wrongly applied to this Subject | Different Goals, resources, or environments |

In cross-Subject connections, contradictions are not automatically resolved by “majority conclusion.” The system should determine whether both can be true under different times or conditions, whether they genuinely conflict, or whether needed Evidence is missing. Preserving differences in understanding is also different from treating clearly false facts as equally supported.

## 7.2 Four Hypotheses to Test

**H1: Deficiency-fit hypothesis.** Selecting information that supplies facts, conditions, or counterexamples missing from a Task will improve unseen-Task performance or reduce confirmation burden compared with adding the same amount of similar material. If an independent evaluation shows no difference, or negative transfer increases, the hypothesis is unsupported under those conditions.

**H2: Direction-preservation hypothesis.** A representation preserving semantic direction and provenance will reduce errors that confuse dependency, grounds, citation, or adopting Subject relative to a representation that removes direction. However, if a comparison condition that expresses the same meaning in natural language performs equivalently, the need for a dedicated Graph representation is not supported.

**H3: Subject-boundary hypothesis.** Sharing that preserves the Subject and applicability conditions will reduce erroneous transfer of another Subject's adoption, Authority, or Outcome relative to merged summaries that erase origin. Conditions in which the preserved boundary omits useful information and worsens practical performance or burden must also be identified.

**H4: Selective-commitment hypothesis.** A method that distinguishes confirmed answers, conditional proposals, and holds according to Evidence, conditions, and permission will reduce unsupported assertions while retaining usefulness on answerable questions. Merely refusing to answer everything and thereby reducing errors does not support the hypothesis.

H1 through H4 are proposals of this paper. They are not validated or adopted merely because this paper was written.

## 7.3 Strong Baselines and Factor-wise Comparison

Evaluation should use, as a rule, the same model, same Tasks, and same Original Source material. However, conditions in which all material is directly passed to the model and conditions in which retrieval is used differ in actual input, so both the upper bound on information access and the real input budget should be recorded.

At minimum, compare model-only, ordinary retrieval augmentation, natural-language or tabular representation with explicit provenance and conditions, and a directional-Relation method. Where appropriate, also include existing graph-based methods. Beating only a weak undirected graph does not establish the value of the specialized method.[5][7]

In factor-wise comparison, do not drop multiple kinds of information at once. Remove only direction, only provenance, or only time in separate conditions and investigate the source of the performance difference. If direction is removed while detailed explanatory text is also removed, one cannot tell whether improvement came from arrows or simply from more information.

Include a baseline where ordinary RAG receives equivalent provenance, conditions, and permissions. Even if no advantage of a specialized Graph appears, a design principle preserving Subject boundaries and provenance may still have value. Evaluate semantic requirements separately from the implementation form used to store them.

## 7.4 Task Sets and Construction of Ground Truth

The basic Task set should include six types: fact checking, reverse lookup, selecting an option under conditions, cross-Subject application, update/revocation, and insufficient Evidence. Each Task should have a human-verifiable mapping to the Original Source material, correct referent, acceptable conclusions, and required holds or confirmations.

A mere paraphrase of the same sentence should not count as an unseen Task. Different Subjects, periods, and unseen combinations of conditions should be split into evaluation. Reposts and summaries of the same case should be treated as the same provenance group and must not be split across calibration and evaluation. To reduce the possibility that the evaluation model already knows the material internally, explicitly created hypothetical cases and permitted real cases should be evaluated separately.

For Tasks without one uniquely correct conclusion, evaluate required conditions, correspondence of Evidence, treatment of contradictions, and permission Scope rather than whether the evaluator agrees with the conclusion. Real operational adoption Decisions should not be left to an LLM evaluator alone. If automated judgment is used as an aid, disagreements between the evaluator and humans should be retained.[13]

## 7.5 Metrics and Decision Criteria

Report accuracy, Evidence-support rate, direction error, Subject-attribution error, use of expired information, unnecessary hold rate, confirmation burden, time, and computational cost separately. Evidence-support rate should measure, for factual Claims selected for evaluation, the proportion actually supported by the corresponding material. Keep it separate from factual correctness so that uncited but correct general knowledge is not conflated with cited falsehood.

For methods that allow holding, report both coverage of answered questions and error rate among answered questions. Compare at equal answer rates or show the relationship between answer rate and error rate. Because shortening an answer alone may improve some metrics, also verify completion of required answer elements.

Use paired comparisons on the same Tasks and repeat evaluations when model outputs vary. Define primary metrics and acceptable burden limits before evaluation and report uncertainty in differences. The required number of Tasks should be designed from early-evaluation variance and the effect size one wants to detect; this paper does not invent an unsupported sample size.

## 7.6 Growth and the Case Where the Hypothesis Does Not Hold

A one-time improvement does not prove continual Growth. Compare whether past real Outcomes and Corrections improve first responses on new similar Tasks, with and without the Correction information. Re-running exactly the same Task is not itself Evidence of Growth.[Base 1]

If no effect is found, do not add complexity merely to protect the hypothesis. Separate possible causes: perhaps the necessary information never existed, retrieval failed, the model could not use the distinction, or storage and verification costs were too high. Where natural language and ordinary retrieval already satisfy the necessary conditions, use that smaller configuration.

# 8. Implications for ToraOS OPEN and Conclusion

## 8.1 Do Not Make a New Giant Memory Store Mandatory

This paper does not justify immediately requiring a new Graph database, many always-on agents, or prior structuring of every document. If references to Original Source and the needed Relations and conditions can be handled by existing mechanisms, evaluation can begin there. Whether another storage or indexing form is needed should be decided by measuring search burden and correctability.

Likewise, do not force the same fixed fields or common scores onto every Relation. What matters is that meaning needed for the current Decision is preserved and that the system can return to Original Source, Scope, origin, and change. Avoiding up-front Graph conversion of all information and treating a Graph as a regenerable projection are also consistent with the referenced ToraOS semantic grammar.[Base 3]

## 8.2 Will Better LLMs Make External Information Unnecessary?

The view of this paper is that even as model generalization improves, concrete facts that have never been made public or learned, and facts about who permitted or adopted what, still need to be supplied separately. This is an information constraint: ability alone cannot establish an unknown fact. It does not imply the necessity of any specific external-memory product or Graph format.

On the other hand, more capable models may reduce the need to pre-extract fine-grained Relations, because Original Source plus appropriate retrieval may become sufficient. The value of external representation should therefore not be fixed as “adding a complicated aid because the model is weak.” The question is what Evidence, Subject boundaries, and Correction paths need to remain even when the model changes, and what implementation is minimally sufficient at that time.

## 8.3 The Goal Is Not to Fill Every Blank

Sparse areas for an LLM are candidates where external complementation may have value. But not every blank must be filled. Undisclosed, unobserved, undecided, and conflicting are each legitimate states. Identifying what kind of blank exists and complementing only what is necessary may reduce unnecessary speculation and confirmation.

Community Tora likewise does not define success as converging every Subject's understanding into one. The question is whether, while different conditions and Decisions remain different, the information usable for the current Task increases, incorrect transfer decreases, and resulting Outcomes can be corrected.

## 8.4 Conclusion

This paper treated the “variations in density of an LLM's map of words” not as a measured map of internal geometry, but as an entry point for considering unevenness in Task capability and Evidence. It then discussed the possibility that directional Relations can preserve citations, grounds, dependencies, adoption, claimant, and applicability conditions that semantic nearness alone cannot distinguish, improving information selection and use.

The central proposition is:

**External intelligence complementation in ToraOS OPEN does not mean replacing the LLM's internal map with one giant Graph. It means connecting differences in facts, experience, and Decisions held by different Subjects to the current question without losing direction, origin, conditions, or permission, thereby expanding opportunities for generalization while suppressing unsupported commitment and illegitimate Authority transfer.**

Its value should be tested by first responses on unseen Tasks, real Outcomes, correctability, and confirmation burden rather than Relation count or diagram complexity. Direction alone does not create Truth, mutual confirmation alone does not guarantee reliability, and more participants alone do not create intelligence.

Even so, under suitable conditions, a Subject may reach experience and counterexamples unavailable from itself alone and connect them to new hypotheses and Actions. **In addition to what is known, handling whose Evidence can be reached under which conditions and what may legitimately be brought back is the core of the relational intelligence proposed here.**

# Appendix A: Example Relation Description for Evaluation

The following is an explanatory example for designing comparative experiments in this paper. It is not the formal schema of current ToraOS and does not propose making the same fields mandatory for every Relation. Information may be referenced from Original Source or existing records rather than duplicated into independent fields.

| Field | Hypothetical example | Meaning preserved |
|---|---|---|
| Subject and predicate | Team A → adopted → Method X | What Relation is being stated |
| Claimant | Person responsible for Team A's report | Whose report; a role separate from the Relation target |
| Evidence | Relevant paragraph and version of the report | What should be checked |
| Conditions | Small-scale processing; double-checking enabled | Do not transfer unconditionally to other environments |
| Time | Period of the trial | Whether it still applies today requires separate confirmation |
| Real Outcome | Reported success; independent verification not performed | Separate report content from verification state |
| Correction / withdrawal | Reference to applicable later record | Separate historical record from current usability |
| Use Scope | Internal review only; redistribution excluded | Readability is not permission for every use |

If another Subject cites this report, the new record has provenance that “the Subject cited the report.” It does not make Team A's trial occur twice, nor does it mean the citing Subject empirically demonstrated X.

A minimal use procedure for Decision is to identify the question; confirm referent and conditions; acquire required paths within a budget; distinguish Claim, Evidence, adoption, and Authority; and then return what can be answered and what remains unconfirmed. This should not be conflated with adding an independent new service or dedicated agent.

# Appendix B: Status of Major Propositions

| Proposition | Treatment in this paper |
|---|---|
| Context-dependent representations and Task performance are uneven | Finding shown by prior work under particular models and conditions; not a density map for all models |
| Dense areas are memorization and sparse areas are generalization | Simplification not adopted |
| This paper is the first to propose directional Relations | Not adopted; prior technology and the main paper already contain them |
| Relations eliminate hallucination | Not adopted; errors in acquisition, interpretation, generation, and Original Source remain |
| Subject-boundary-preserving connections improve practical performance | Research hypothesis of this paper; comparative experiments required |
| Mutual confirmation or many citations guarantee Truth | Not adopted; provenance, conditions, and independence must be checked |
| Original Source and ordinary retrieval are sufficient in some domains | Allowed as falsification and simplification |
| Writing this paper changes the Current specification | It does not; preservation, design adoption, and implementation are separate |

# References and Source Manuscripts

## External Primary Literature

[1] Vaswani, A., et al. (2017). *Attention Is All You Need*. Advances in Neural Information Processing Systems 30. Referenced for: model architecture, attention, embeddings, and layer-wise transformations.  
https://arxiv.org/abs/1706.03762

[2] Ethayarajh, K. (2019). *How Contextual are Contextualized Word Representations? Comparing the Geometry of BERT, ELMo, and GPT-2 Embeddings*. EMNLP-IJCNLP, 55–65. DOI: 10.18653/v1/D19-1006. Referenced for: geometry of contextualized representations and layer-wise variation.  
https://aclanthology.org/D19-1006/

[3] Kandpal, N., Deng, H., Roberts, A., Wallace, E., & Raffel, C. (2023). *Large Language Models Struggle to Learn Long-Tail Knowledge*. ICML, PMLR 202, 15696–15707. Referenced for: training-data support, factual-question accuracy, and retrieval complementation.  
https://proceedings.mlr.press/v202/kandpal23a.html

[4] Lake, B. M., & Baroni, M. (2018). *Generalization without Systematicity: On the Compositional Skills of Sequence-to-Sequence Recurrent Networks*. ICML, PMLR 80, 2873–2882. Referenced for: task splits evaluating unseen combinations; not cited as evidence of current LLM performance.  
https://proceedings.mlr.press/v80/lake18a.html

[5] Lewis, P., et al. (2020). *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks*. Advances in Neural Information Processing Systems 33. Referenced for: generation combining parametric knowledge and external memory.  
https://proceedings.neurips.cc/paper/2020/hash/6b493230205f780e1bc26945df7481e5-Abstract.html

[6] Shuster, K., Poff, S., Chen, M., Kiela, D., & Weston, J. (2021). *Retrieval Augmentation Reduces Hallucination in Conversation*. Findings of EMNLP, 3784–3803. DOI: 10.18653/v1/2021.findings-emnlp.320. Referenced for: reduced hallucination on the dialogue Tasks studied.  
https://aclanthology.org/2021.findings-emnlp.320/

[7] Edge, D., et al. (2024; v2, 2025). *From Local to Global: A Graph RAG Approach to Query-Focused Summarization*. arXiv:2404.16130v2. Referenced for: graph-based corpus-level summarization; not used as empirical Evidence for federation among Subjects.  
https://arxiv.org/html/2404.16130v2

[8] Asai, A., Wu, Z., Wang, Y., Sil, A., & Hajishirzi, H. (2023). *Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection*. arXiv:2310.11511. Referenced for: retrieval when needed and evaluation of retrieved/generated material.  
https://arxiv.org/abs/2310.11511

[9] W3C (2014). *RDF 1.1 Concepts and Abstract Syntax*. W3C Recommendation, 25 February 2014. Referenced for: subject-predicate-object representation, directed graphs, and multiple graphs; citation fixed to the adopted version.  
https://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/

[10] W3C (2013). *PROV-O: The PROV Ontology*. W3C Recommendation, 30 April 2013. Referenced for: derivation, generation, attribution, and inverse-relation vocabulary.  
https://www.w3.org/TR/prov-o/

[11] Pearl, J. (2009). *Causal Inference in Statistics: An Overview*. Statistics Surveys, 3, 96–146. DOI: 10.1214/09-SS057. Referenced for: distinction among association, intervention, and causal assumptions.  
https://ftp.cs.ucla.edu/pub/stat_ser/r350.pdf

[12] Liu, N. F., et al. (2024). *Lost in the Middle: How Language Models Use Long Contexts*. Transactions of the Association for Computational Linguistics, 12, 157–173. DOI: 10.1162/tacl_a_00638. Referenced for: information position in Context and utilization performance for the models studied.  
https://aclanthology.org/2024.tacl-1.9/

[13] Gao, T., Yen, H., Yu, J., & Chen, D. (2023). *Enabling Large Language Models to Generate Text with Citations*. EMNLP, 6465–6488. DOI: 10.18653/v1/2023.emnlp-main.398. Referenced for: evaluation of content correctness and citation quality.  
https://aclanthology.org/2023.emnlp-main.398/

[14] Zou, W., Geng, R., Wang, B., & Jia, J. (2025). *PoisonedRAG: Knowledge Corruption Attacks to Retrieval-Augmented Generation of Large Language Models*. 34th USENIX Security Symposium, 3827–3844. Referenced for: answer manipulation through external knowledge.  
https://www.usenix.org/conference/usenixsecurity25/presentation/zou-poisonedrag

## ToraOS Source Manuscripts

[Base 1] Nakagawa, Tsubasa (2026). *ToraOS: A Proposal for a Subject-Centric, Evolving AI OS Architecture: Independent Context and Authority, Directional Relations, and Continuous Growth Driven by Real-World Outcomes*. Draft v0.1, original text dated August 29, 2026. Stored as `ToraOS_主体中心型進化AI_OS論文_日本語_v0.1.md`. Main paper for this supplement. Content consulted on September 19, 2026. Its implementation descriptions report the baseline of that paper and are not a re-verification of the current state by this paper.

[Base 2] ToraOS Project (2026). *ToraOS Subject Ontology Concept Note v1.0: Any Subject, Multiple Views, Directional Relations, Recursion, Runtime Boundaries, and Falsifiability*. NONCANONICAL CONCEPT NOTE. Treated here as the preceding Supplement 1. Content consulted on September 19, 2026. The existing file name, number, and status are not changed.

[Base 3] ToraOS Project (2026). *Universal Semantic Constitution*. constitution_id: TOROS-UNIVERSAL-SEMANTIC-CONSTITUTION-20260812-006. Referenced for: §2 separation of Original Source, Claim, and Inference; §5 Relations and conditional causality; §6 real Outcomes and Growth; §7 Action-specific boundaries for information use. This is an internal ToraOS semantic consistency condition confirmed on September 19, 2026 through the AGENTS.md and Current Authority Registry read path, not external peer-reviewed research.

The source manuscripts are ToraOS internal materials and are not necessarily external verification material available to every reader. If the comparative experiments in this paper are made public, definitions, hypothetical Tasks, and evaluation procedures usable by third parties will need to be provided separately. Preservation of this paper does not automatically authorize publication of Original Source or private code.

External literature checked September 19, 2026. The literature review is scoped to the conceptual organization needed for this paper and is not a systematic review. The existence of the references does not establish the validity or novelty of the proposal as a whole.
