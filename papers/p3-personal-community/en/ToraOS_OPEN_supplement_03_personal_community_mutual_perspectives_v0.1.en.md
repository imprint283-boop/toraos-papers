---
document_id: TORAOS-OPEN-SUPPLEMENT-03-20260928
series: ToraOS OPEN Paper Supplements
supplement_number: 3
version: "0.1"
date: 2026-09-28
language: en
status: NONCANONICAL_RESEARCH_DRAFT
author_review: PENDING
peer_reviewed: false
current_authority: false
implementation_adoption: false
runtime_activation: false
empirical_results: none
publication_authorization: false
translation_of: TORAOS-OPEN-SUPPLEMENT-03-20260928
translation_state: PRIVATE_FAITHFUL_TRANSLATION_DRAFT
---

# ToraOS OPEN Supplementary Paper 3
## A Subject-Centric AI OS Through the Mutual Perspectives of Multiple Personal and Community Subjects
### A Secretariat Serving Each Subject's Goal, Overlap and Non-Connection, and Location-Independent Continuity of Execution

**Tsubasa Nakagawa**  
Independent Research and Practice-Based Development  
Draft v0.1 / September 28, 2026

**Paper type:** Position paper, organization of architectural principles, and evaluation plan.  
**Status:** Research draft before author review and peer review. The proposals in this paper do not mean a change to Current specifications, product adoption, implementation completion, or operational validation.  
**Preparation note:** Dialogue with the author served as the primary problem setting, and generative AI assisted with comparison against existing papers, limited literature checking, organization, and drafting. No new user experiments, performance measurements, or execution-environment tests were conducted.

## Abstract

ToraOS OPEN is a concept that takes the Subject, rather than a model or service, as the basic unit of durable state and distinguishes Original Source, Context, Authority, Decision, real-world Outcome, and Correction. However, merely extending an explanation centered on one user's Personal Tora directly into a society of multiple Subjects, including companies, departments, and communities, leaves several questions unclear: whose Decision a Community Decision actually is, how relations with participants are established, and which states are not shared. Preserving state is also different from connecting that state to action across time.

This paper first explains Personal Tora in terms of the relationship among the person's interface, the canonical state of the Subject, the Secretariat's responsibility for continuity, the operational steward's responsibility for operation, execution environments, specialized capabilities, external services, and credentials. While preserving this common architecture, it moves back and forth between the view of a Community from multiple Personal Subjects and the view of multiple Personal Subjects from a Community. Community Tora is not treated as the sum of participants' memories or as identical to a representative's Personal Tora, but as an operation with an establishment procedure, Roles, delegation, collective Decisions, shared assets, and its own Outcomes. The party served by each Secretariat is not the person operating it at a particular moment, but the Subject for which it is responsible. A company Secretariat acts on the Goals and policies legitimately adopted by the company and does not substitute a representative's or individual's private wishes for the company's purpose.

Overlap among Subjects is decomposed along distinct axes: membership, Authority, information, work scope, and execution resources. Subjects are connected through directional Statements and permitted references. Connection, viewing, use, adoption, and permission to execute are not identical; dissent, non-disclosure, non-connection, and exit are also preserved as distinct states. The paper further separates the architecture of a Subject from the placement of its execution environment and explains continuity of execution without making cloud infrastructure, a particular Bot, continuous inference, or one PC per Subject mandatory.

The candidate contributions of this paper are an architectural model that can explain Personal and Community Subjects through the same semantic grammar, a many-to-many model of mutual perspectives, and comparative conditions for testing failures caused by conflating Subject, Authority, and execution. It does not report empirical validation of federation among independent Subjects or of continuous Growth. If a dedicated structure adds only burden relative to simple documents, access controls, and existing execution infrastructure, reducing that structure is also accepted as a valid research result.

**Keywords:** Subject-centric AI, Personal Tora, Community Tora, mutual perspectives, Role, directional Relation, continuity responsibility, execution environment, provenance, non-connection, Outcome, Correction

## Contents

1. Positioning and research questions
2. A common OS and the establishment of different Subjects
3. Making the architecture of Personal Tora concrete
4. Explaining Community Tora from the Community side
5. Viewing multiple Personal Subjects and Communities from both sides
6. Do not collapse overlap into a single hierarchy
7. How Subjects connect and how they do not
8. Continuity responsibility through the Secretariat and operational steward
9. Placement of execution environments, canonical state, and credentials
10. Following one collaborative case from both sides
11. Conditions the common architecture must preserve
12. Connection to prior technologies and the position of this paper
13. Falsifiable hypotheses and evaluation plan
14. Limitations, risks, and distance from current implementation
15. Conclusion

Appendix A: Issues inherited from the dialogue and how they are treated  
Appendix B: Minimal terminology mapping  
Appendix C: Propositions that are easy to misread  
References and source papers

# 1. Positioning and Research Questions

## 1.1 Division of Roles Among the Main Paper and Supplements

The main paper proposed a Subject-centric AI OS in which each Subject maintains independent Source, Context, Authority, Decision, and Outcome and connects through directional Relations. Supplement 1 examined the distinction between a referent and a View about that referent, the possibility of arbitrary Subjects, finite Runtime, and the coexistence of multiple Views. Supplement 2 examined the conditions under which an LLM's use of such external information can improve understanding, reasoning, adoption, and action.[Base 1–Base 3]

This paper does not replace those works with a different theory. What it adds is an account of **how that OS is established for one Personal Subject and how the same architecture is established within relations among multiple Personal and Community Subjects**. Rather than presenting the individual and Community cases as different products, it asks whether the semantic distinctions remain intact when the same event is viewed from both sides.

| Paper | Central question | Connection to this paper |
|---|---|---|
| Main paper | As whose state, Authority, and real-world Outcome is AI used continuously? | Common structure of the Subject-centric architecture |
| Supplement 1 | How should referent, View, Subject, and Runtime be distinguished? | Separation of referent and proxy, and of logical existence from execution |
| Supplement 2 | How can information that preserves evidence, conditions, and direction be used in Decision-making? | Testing the use and misapplication of shared experience |
| Supplement 3 / this paper | How can Personal and Community Subjects be structured, connected, and continued from both sides? | Many-to-many Subject relations and the operational architecture that supports them |

## 1.2 The Starting Point Is Not Merely "A Cloud PC Is Missing"

In the dialogue that triggered this paper, an architecture diagram placing canonical state, AI, and external tools side by side was challenged with a missing question: who continuously receives work, executes it, carries forward pending items, and returns results? The author described this as the "Secretariat," a role combining secretarial and operational-steward functions that had been intended from an early stage. The author then clarified that execution environments are not limited to the cloud, and that neither Community nor OPEN can be explained convincingly while the Personal architecture remains vague. The author further made explicit that a company's Secretariat and operational steward act not for any particular individual but for the Goal of the Company ToraOS, while each Secretariat acts for the Subject assigned to it.[Dialogue 1]

Accordingly, this paper does not begin with a proposal to introduce an always-on cloud PC. It first explains the Personal architecture, then the Community architecture, follows the mutual relations between them, and only afterward discusses placement of execution environments. Grok Bot, OpenAI, Claude Code, and other concrete candidates appeared in the dialogue, but the capabilities of any particular product are not conditions for the paper's architecture.

## 1.3 Three Research Questions

First, can Personal Subjects, in which the individual is usually the principal decision-maker, and Community Subjects, in which Decisions are made through multiple people and procedures, be explained through the same semantic grammar while preserving to whose Goal each Secretariat is responsible? Second, when multiple Personal and Community Subjects overlap, can information about the same people or work be connected usefully without conflating private judgments, Community Decisions, and approval by other Subjects? Third, if the Secretariat, execution environment, or storage location supporting those relations is replaced over time, can responsibility for ongoing work and Corrections be preserved?

In this paper, "establishment" first means making roles, connections, responsibilities, and failure conditions explicit at the explanatory level. Understanding a diagram does not mean that implementation has been established. Architectural consistency, implementation of mechanisms, actual operation, and demonstrated user value are separate.[Ops 1]

## 1.4 Method and Claim Ceiling

The source materials are the three preceding papers, the Current Universal Semantic Constitution, Personal Profile, Current Operating Policy, Harness Adapter Policy, and the dialogue underlying this paper. The Current entry point was confirmed from live Drive AGENTS.md and the Registry. The live contents of the three earlier papers were confirmed to be byte-identical to the copies previously referenced in the dialogue.[Base 1–Base 3][Const 1][Personal 1][Ops 1][Exec 1]

External literature was checked only to connect the discussion to existing work on organizations and Roles, provenance, credentials, separation of data and applications, and collaboration across differing perspectives. This is neither a systematic literature review nor a product comparison. The hypothetical cases and architectural models in this paper are proposals and are not treated as results from external literature or existing ToraOS experiments.

# 2. A Common OS and the Establishment of Different Subjects

## 2.1 "The Same OS" Is Different from "The Same Subject"

Following the notation of the main paper, one ToraOS can be represented conceptually as follows.[Base 1 §5.1]

```text
T_i = K + P_i + X_i

K   : common semantic grammar
P_i : Profile, procedures, Authority, and necessary capabilities of Subject i
X_i : Source, Current View, Decisions, real-world Outcomes, and history of Subject i
```

This notation expresses a division of conceptual responsibilities; it is not a declaration of implementation classes, mandatory database tables, or a fixed schema. Using the same OS means that the basic meanings of Claim, Decision, Authority, Outcome, and Correction are common. It does not mean that every Subject uses the same Goals, Decision rules, storage, model, or user interface.

Using the same execution engine alone is also insufficient to show that the same OS has been established. If information treated as a personal Correction for an individual is transformed, without explanation, into collective agreement in a Community, the common semantic grammar has already been broken.

## 2.2 Personal and Community as Explanatory Categories

In this paper, an operation centered on a specific person is called Personal Tora. Community Tora is a broad term for describing operation from the side of a Community involving multiple stakeholders, such as a company, department, committee, project organization, or association. Company Tora is used when the relevant Community is a company. These are not changes to product or legal classifications.[Dialogue 1]

The difference is not simply the number of people. Even in a company managed by one person, a Decision made on behalf of the company must be distinguished from that person's private judgment. Conversely, several people viewing the same screen does not establish a separate Community Subject.

In Personal, the Subject, primary instruction giver, and Corrector often overlap in one person. In Community, the Subject itself, members, representative, operator, Decision procedure, and executing AI are separated. **To show that the same OS applies, the architecture must explain these different patterns of overlap.**

## 2.3 Distinguish the Referent, the View, and the Acting Subject

Supplement 1 examined a broad Subject concept under which a View can be established about an arbitrary referent. The Current Constitution, by contrast, organizes a Subject as a unit with continuous Identity and a procedure for making Decisions or taking Action in its own name. This paper does not collapse those meanings into one.[Base 2 §§1–3][Const 1 §3]

The primary focus here is on Personal Subjects that make Decisions or take Action and on Community Subjects with explicit establishment procedures. If an individual creates a "View of Company X," that View is not Company X's official OS. Likewise, organizing information about a region does not grant Authority to represent that region.

| Distinction | Meaning in this paper | Not identical to |
|---|---|---|
| Real-world referent | A person, company, department, Community, work item, and so on | A record about the referent |
| View | A Current View maintained under a particular standpoint and management Authority | The referent itself or universal Truth |
| Subject | In this paper's main analytical scope, a unit that continuously decides and acts in its own name | A software account |
| Actor | The concrete person or system that speaks, operates, or executes | The Subject represented by that operation |
| Role | A Role dependent on Subject, work scope, and time | Permanent, universal Authority of a person |
| Scope | A range in which people or issues intersect | Necessarily one deciding Subject |

## 2.4 Independence Does Not Mean Unlimited Freedom or Lack of Relation

Independence of Subject state does not mean that all Subjects have the same Authority or that legitimate company rules or delegation to departments become invalid. A company may legitimately establish a department's budget or activity scope through an appropriate procedure. What matters is that the system can explain which basis constrains which act within which Scope.[Const 1 §§3–4]

This paper therefore does not reject hierarchy. It rejects treating a position higher in a hierarchy as sufficient grounds for unlimited ownership of all subordinate information, private intent, and Authority. Likewise, the existence of an independent View does not imply an unconditional veto over legitimately adopted Community Decisions.


# 3. Making the Architecture of Personal Tora Concrete

## 3.1 What Actually Operates for One User

The minimal explanation of Personal Tora cannot stop at "an AI that chats with the person." When the person states the current Goal, the system must be able to explain where the necessary memory and Authority are read from, who carries the work forward, where it is executed, what counts as return, and what is left for the next occasion. This paper explains those responsibilities as follows.[Personal 1 §§1–8][Exec 1 §§1–2,6–8]

| Architectural role | What it is responsible for | What it is not responsible for |
|---|---|---|
| The person's interface | Consultation, requests, Corrections, confirmation, stop requests, receipt of results | Guaranteeing execution of all work merely because the interface is open |
| Canonical Subject state | Preserving Source, currently effective policies, Decisions, real-world Outcomes, Corrections, and provenance | Turning a temporary AI inference into official state without conditions |
| Secretariat | Continuity from the meaning of a request, consistency with existing Decisions, pending state, and acceptance through final return | Constantly controlling detailed procedures of specialized Workers or selecting every model |
| Operational steward function | Necessary startup, scheduled execution, fault detection, preservation, and authorized recovery | Re-executing cancelled work or effects of unknown status merely because of a restart |
| Execution environment and specialized capabilities | Running semantic processing, search, Relation work, code, documents, validation, and similar functions | Treating successful execution as proof that the Subject's Decision has been made |
| External services and authentication | Authorized data retrieval and operations and use of required credentials | Expanding the possession of credentials into approval for every use |

This table does not propose six new Authority layers or six permanent services. One product may provide several roles, and several components may jointly fulfill one role. Explanatory responsibility and the number of physical components are separate.

## 3.2 One Personal Cycle

Suppose the person asks, "Create this proposal based on the Correction from last time." The interface receives the request. The Secretariat checks the relationship between the current Goal and what was previously adopted, rejected, or held. The execution side selects the necessary Source and Corrections, generates a proposal, and performs whatever validation is required. Even after the person adopts the result, actual utilization and real-world Outcome are recorded separately.[Base 1 §5.9][Personal 1 §§4,7–8]

**Figure 1: A cycle between Personal state and execution**

```text
Person's request / Correction
  → Interface
  → Secretariat confirms Goal, Scope, Authority, and prior Decisions
  → Necessary Source and Context are retrieved from canonical state
  → Specialized capabilities, Workers, and external tools execute within authorized scope
  → Artifact is validated and returned to the person
  → Person's adoption, revision, or rejection is recorded
  → Actual utilization and Outcome are observed separately
  → Correction is returned to Context for the next similar situation
```

There are Decisions before Action as well. "The person's adoption" here is a subsequent Decision about the artifact; it does not eliminate permission or planning Decisions that precede Action. Multiple Decisions should not be collapsed into one Decision box in a way that loses temporal order.

For example, "I agree with the proposal but have not used it yet" is adopted but has no observed Outcome. "I used it, but it failed because the conditions were different" remains subject to Correction even though the person previously adopted it. On the next occasion, the system should use not only the prior conclusion but also the difference in applicability conditions.[Base 1 §9][Base 3 §7.6]

## 3.3 Canonical State, Working Copies, and Operational State

A concrete arrangement raised in the dialogue placed semantics and original materials in Google Drive, code in GitHub, and execution on another PC. This paper retains that as an explanatory example. However, not every file in Drive is equally Current, nor is every GitHub branch accepted code. Canonical state is identified not only by the name of a storage service but also by responsibility scope and the adoption procedure.[Ops 1 §§1–5]

| Type of information | Example placement | Distinction that must be preserved |
|---|---|---|
| Currently effective policy, Profile, Project Context | Designated Drive documents | Distinguish Candidate, History, and Source from Current |
| Version-controlled code, tests, and accepted artifacts | Designated Git state, GitHub, etc. | Distinguish working branch, review, acceptance, and running version |
| Original materials, Evidence, real-world Outcomes | Source / Context store satisfying Authority and retention requirements | Distinguish content, provenance, permitted use, and information that need not be retained |
| Working copies and regenerable indexes | Execution environment | Distinguish disposable copies from the only surviving record |
| Incomplete requests, pending confirmations, effects of unknown status | Durable operational record | Do not treat as mere cache |
| API keys, OAuth credentials, etc. | Secret-management capability or restricted credential store | Separate from Source, papers, logs, and public code |

In particular, intermediate processing state must not be treated as disposable merely because "the PC can be discarded." If the only record of an external send attempt with a lost acknowledgement, a pending approval, or an unrecovered artifact exists on that PC, losing the PC means losing responsibility. Reconstructability includes not only replacing code but also recovering necessary operational state. This is an architectural requirement proposed by this paper, not a report that existing implementation already satisfies every condition.

## 3.4 The Person Operating It and Work Continuing in the Person's Absence

The person-centered nature of Personal Tora does not mean that the person must press a button every time. The Current Personal Profile likewise permits Decisions and execution without confirmation every time when they remain within valid conditional Authority. The person defines Goals and authorized scope, makes Corrections when necessary, and resolves conflicts that remain unresolved.[Personal 1 §§2–3]

Accordingly, it is consistent for previously authorized work to continue after the person closes a PC. However, "continues while the person is absent" is not the same as "an LLM reasons twenty-four hours a day." A system that processes only when an event arrives, a scheduled time occurs, or a person resumes work can still provide continuity if incomplete responsibility is not lost.

## 3.5 Do Not Make Personal the One Omnipotent Owner

Even when Personal Tora acts for the person, the person may not be free to modify another Subject's official record about them. A personal judgment, another party's Statement, and an organizational record carry different responsibilities even when they concern the same person. If the person disputes a record, the objection, request for Correction, and counterparty response should be connected without conflation.[Base 1 §§5.3–5.4][Base 2 §§6–7]

A person, a Personal OS, an account, and a device are also not identical. The baseline explanatory case places one continuous Personal operation around one person, but it does not prohibit multiple Views or multiple interfaces. Where assistance or representation by another person is required, the person's Subject status remains distinct from the operating Actor and the scope of delegation.

# 4. Explaining Community Tora from the Community Side

## 4.1 A Community Is Not "A Representative's Enlarged Personal"

The most important mistake to avoid when explaining Community Tora is simply replacing the central person in a Personal diagram with one representative. As a baseline case, this paper assumes that a Community has Decisions, shared assets, incomplete work, and external commitments that must survive a change of representative.[Base 1 §§7.2–7.3]

A representative's statement may represent several different things: a private view, a proposal, a Decision within delegated Authority, or communication of a resolution reached through a meeting. The single fact that "the representative said it" does not determine which meaning applies. The adopted procedure of the Community and the Role and Scope under which the statement was made must be checked.

Community Tora is not the sum of every participant's memory either. Even if many materials are shareable, there is no requirement to ingest every participant's private judgments or undisclosed information. Conversely, materials legitimately created and maintained by the Community itself need not depend entirely on repeated submission by individuals.

## 4.2 What Must Be Explainable Inside a Community

When analyzing a Community Subject that can act, this paper requires at least the following questions to be answerable. These are not universal rules imposing the same institutional design on every Community. They are questions used to make explicit who operates that Community and how.[Const 1 §§3–4]

| Question | What the Community side should explain |
|---|---|
| What continues as the Community? | Name or acting identity, activity Scope, basis of establishment, continuation and termination |
| What does it pursue, and what does it not? | Adopted purposes, multiple Goals, unresolved or conflicting issues |
| Who decides what? | Roles, delegation, Decision procedures such as meetings, routes for change and objection |
| What counts as Community state? | Official records, shared assets, adopted Decisions, incomplete responsibilities |
| What is delegated to whom? | Scope of requests and return conditions for people, departments, other Subjects, and AI |
| What is returned to whom? | Notifications, explanations, and Corrections to members, responsible people, counterpart organizations, etc. |
| What remains when people change? | Community history, continuing work, handoff, and expiring Authority |

For a company, company procedures may apply; for a department, delegated Scope; for a collaborative project, agreement among participating Subjects. These need not be reduced to one individual Owner. Nor does this paper fix one universal method such as unanimous consent, case-by-case responsibility, or multiple approvals.

## 4.3 The Same Architecture, Different Ownership of Responsibility

The commonality between Personal and Community is not created by replacing "the person" with "the representative." It lies in the ability to answer the same responsibility questions differently.

| Common role | Personal Tora | Community Tora |
|---|---|---|
| Interface | The person's consultations, requests, Corrections | Entry point for multiple participants, responsible people, representatives, and external parties |
| State | The person's Source, Decisions, Outcomes | Community official records, shared assets, Decisions, Outcomes |
| Authority | Conditional delegation by the person, etc. | Community procedures and Role-specific delegation |
| Secretariat | Integrates requests through final return in line with the person's Goals | Integrates work and return to stakeholders according to the Community's own Goals and procedures |
| Operational steward | Preserves the person's continuing work and execution environment | Handles handoff among multiple responsible people, continuity of operation, and Authority expiry |
| Execution | Specialized capabilities, Workers, external services | Uses the same kinds of capabilities within the Community's permitted Scope |
| Correction | Feeds changes back into the person's later Decisions | Feeds changes into Community procedures and Decisions and informs other Subjects only when necessary |

A person using a Community Tora interface need not participate only through a Personal OS. A person may enter information directly into a Community interface, and documents or statements from people who do not use AI can also be handled. Even then, the Actor who supplied the input remains distinct from the Subject the input represents.

## 4.4 A Community Decision Is Not the Same as Each Individual's Consent

When a Community decides on a policy, it does not follow that every member privately agrees. Conversely, even if every individual is personally favorable, the matter may still be unresolved as a Community if a required formal procedure is incomplete. A Community Decision and an individual's opinion are different kinds of records.[Const 1 §§2–4]

What this paper requires is not an algorithm that forces differing opinions to converge. It requires an architecture that distinguishes which opinions existed, which procedure established the Community Decision, which objections remain, and the Scope in which execution is permitted. If the legitimacy of the procedure itself is contested, an AI summary must not be used to declare that dispute resolved.

## 4.5 A Company Secretariat Serves the Company's Goal, Not an Individual

A central distinction in this paper is that **the Subject served by a Secretariat is not necessarily the same as the Actor supplying input to that Secretariat**. Personal A's Secretariat acts for A. Personal B's Secretariat acts for B. Company X's Secretariat and operational steward act not for A, B, or the representative's Personal, but within the Goals, policies, and Authority legitimately adopted by Company X.[Dialogue 1]

In this sense, a "company Goal" is neither an ambition invented by the AI nor a wish expressed on the spot by a particular person. It is a purpose made effective within the company's operation, and ToraOS retains both that purpose and the basis on which it was established. If an authorized representative revises company policy within Scope, the Secretariat follows the newly effective policy. The same person's private wish or out-of-scope instruction is not elevated into a company Goal solely because of a title or forceful wording.

A company Secretariat is therefore neither "a neutral chat that agrees equally with everyone" nor "a personal assistant that infers the CEO's preferences." It may issue necessary requests, track progress, record information, coordinate, and propose alternatives toward company purposes. But the distinction of whom it serves does not permit it to extract private information or ignore existing Authority and usage conditions merely because the AI interprets such actions as beneficial to the company.[Const 1 §§4,6–7]

"Not acting arbitrarily" does not mean making no Decisions. The Secretariat may choose means within delegated Scope, while not inventing or rewriting Goals, Authority, or unconfirmed facts. When the evidence does not determine a single conclusion, it should state where discretion remains and what is unresolved, then return the unresolved matter to the relevant Community procedure. It is neither mandatory to return every issue to one representative nor to ask every participant about every small action.

Non-arbitrariness here is a normative architectural condition, not demonstrated performance. AI misreading, sycophancy, and confusion of Authority must be tested through comparisons and counterexamples. Chapters 8 and 13 turn this condition into observable questions.


# 5. Viewing Multiple Personal Subjects and Communities from Both Sides

## 5.1 Fix One Many-to-Many Scenario

The following is a hypothetical scenario for explanation and is not a record of any actual company, organization, or employee. Person A and Person B are involved with Company X. Person A and Person C are involved with Community Y. Person D participates in Y without using a Personal OS. Company X has Department X1, and X and Y are considering Collaborative Project Z. Whether Z is an independent Subject or remains merely a Scope of collaborative work depends on its establishment procedure.

**Figure 2: Reading the same relations from the individual side and the Community side**

```text
Read from the individual side          Read from the Community side
Personal A → Company X / Community Y   Company X → Person A / Person B / Department X1
Personal B → Company X / Department X1 Community Y → Person A / Person C / Person D
Personal C → Community Y               Collaborative Project Z → X / Y / responsible people
Person D → participates directly via Y's interface
                                       * Person D does not need a Personal OS

Company X and Community Y are connected in a limited way through Collaborative Project Z.
Even though Person A is involved in both, X's and Y's internal information is not shared automatically.
```

The arrows in this diagram indicate involvement. They do not mean delegation of all Authority, mutual approval, or an already-operational API connection.

## 5.2 Viewing a Community from Each Personal

From Personal Tora A's perspective, Company X and Community Y are separate Subjects in which A participates through different Roles. A tracks what has been requested, how much discretion A has, what A disclosed, and what A brought back. Authority assigned to A in Company X does not automatically become Authority in Y.

From Personal Tora B's perspective, X's initiative affects B's assigned work and burden. If B only records a heavier burden privately, X has not thereby learned that information. If B reports it under specified conditions, X may use that report within the permitted Scope. A's involvement in both organizations does not permit B's record to be passed to Y.

For Person C, Y may be a shared activity Subject while X is a counterpart organization in which C does not directly participate. When C collaborates on Z, there is no need to treat C as an employee of X. Participation, employment, delegation, cooperation, and reference are different Relations.

The individual-side explanation is not merely about controlling outbound information. It also includes how official Decisions, requests, Corrections, and activity Outcomes returned by a Community affect each person's next Decision. Personal Tora connects not only to isolate counterparties, but also **to receive necessary information under appropriate conditions and improve the person's own Action.**[Base 3 §§6.2–6.3]

## 5.3 Viewing Multiple Personal Subjects from a Community

From Company X's side, Persons A and B are different Actors with different Roles, authorized Scopes, involvement in work, and reported information. X does not need copies of their entire personalities. It needs to distinguish what information relevant to Community purpose and Authority was received, from whom, and in what capacity.

This does not mean that a Community should see people only as Roles. A Role alone can omit a person's actual burden, objections, requests for Correction, and conditions for participation. In addition to Roles, a Community-side View may contain legitimately obtained Statements by the person and information about impacts on them. **Not owning an entire personality is different from reducing a person to a Role.**

From Community Y's perspective, Persons A, C, and D need not use the same device, the same AI, or provide the same volume of data. Participation and expression still need to be handled. Y may maintain necessary relation records about D, who does not use a Personal OS, but must not label those records as D's Personal OS or as D's verified inner state.

## 5.4 Visibility from Both Sides Does Not Mean Both Sides See the Same Thing

"Mutual perspectives" here does not mean displaying identical data on both sides. It means each side can distinguish the Scope of what it knows, the other party's Statements, what has been shared, and what remains undisclosed.

| For the same case | Personal side | Community side |
|---|---|---|
| Request | What was requested of me? | What was requested from whom, under what Authority? |
| Response | What did I communicate, and what did I not communicate? | What was received from whom, and what remains unknown? |
| Decision | What did the Community decide, and how does it affect me? | What was adopted or held under the prescribed procedure? |
| Dissent | My concern and the Scope in which I disclosed it | Objections received, unresolved points, and the procedure used to handle them |
| Outcome | Effects and burdens that occurred for me | Successes or failures for the Community and individual impacts reported to it |
| Correction | Changes to my next Decision | Changes to the Community's next procedure and who must be informed |

The important point is that this asymmetric correspondence can be explained from both sides. Differences in visibility must not be filled in arbitrarily as "missing information"; the fact that necessary information has not arrived is itself a Current state.[Base 3 §2.4]

## 5.5 Personal Subjects Can Also Relate Directly to Each Other

Persons B and C may exchange advice directly about the collaborative project. That conversation does not necessarily become the official position of Company X or Community Y. There is no need to place all Personal-to-Personal cooperation under Community supervision, nor to allow secrets learned in a Community to circulate freely.

The relational field described in this paper therefore consists of more than lines from Personal to Community. It includes Personal-to-Personal, Community-to-Community, Personal-to-Community, organizational subunits, and external collaborators. The speaking Subject and conditions of use are preserved on each path.

## 5.6 Cooperation Is Possible Even When Each Secretariat Serves a Different Subject

A's Secretariat responds in light of A's Goals, life constraints, and delegated Roles. B's Secretariat follows the same architecture for B. X's Secretariat issues necessary requests and handles reports in light of X's Goals and formal Decision procedures. Even if all of these run on the same AI model, the Subjects to which their requests belong are different.

Suppose X asks about a work schedule, A returns only available times, and B returns only assigned Scope and required coordination. X's Secretariat can coordinate schedule and work within those boundaries. Cooperation may succeed without obtaining A's or B's private reasons. The overlap between Community purpose and individual purpose is made concrete through necessary information exchange.

If A's private circumstances and X's formal policy conflict, however, A's Secretariat must not change X's policy without Authority, and X's Secretariat must not overwrite A's private Goals. The parties use routes recognized within the relevant relation: coordination, objection, alternatives, or reconfirmation of delegation Scope. **Different parties being served does not imply hostility, but cooperation also does not imply that they are served as one Subject.**

# 6. Do Not Collapse Overlap into a Single Hierarchy

## 6.1 Distinguish Five Axes of Overlap

When the same person is involved in multiple Communities, the single word "connected" carries too little information. This paper distinguishes at least the following five axes. They are analytical dimensions for avoiding semantic conflation, not a fixed list of Relation types.

| Axis of overlap | Hypothetical example | What does not follow automatically |
|---|---|---|
| Membership / involvement | A participates in both X and Y | Full information sharing between X and Y |
| Authority / Role | A is responsible for work in X and a general participant in Y | Transfer of approval Authority from X to Y |
| Information / assets | X and Y refer to the same collaborative project document | Sharing of each Subject's internal evaluations or original materials |
| Work / purpose | X and Y cooperate on Project Z | Agreement on every Goal of X and Y |
| Execution resources | X and Y use the same computer or service | Shared memory, authentication, or write Authority |

The same file can, for example, be edited collaboratively. If it is defined which portions each party may update and who formally adopts them, a shared working surface can coexist with independent Subject state. Independence does not require every artifact to be physically duplicated into separate canonical copies.

## 6.2 Companies, Departments, and Projects of Different Sizes

The size of a company, department, committee, or federation is not a reason to create a new type of OS. Even an organizational subunit can be explained as an operating Subject if it is clear what can be decided in its name and what must be returned to a parent organization. This does not require the department to have separate legal personality.[Const 1 §§3–4]

Conversely, a department used merely as a classification or a temporary Scope for collecting information should not automatically be assigned its own Goal, intent, or permanent Secretariat. It can remain a Scope when appropriate. This also does not mean that no execution can occur within a Scope. Company X's Secretariat may handle "work within the Scope of Department X1" under X's Authority. **A Scope not being an autonomous Subject is different from no work being executed within that Scope.**

W3C ORG provides existing vocabulary for organizational containment, positions, membership, and their durations. The purpose here is not to invent another organization chart but to ask whether those relations can be consumed correctly across AI Decisions, Corrections, and continuous execution.[1]

## 6.3 Overlap Is Not the Same as Inheritance

Even when Department X1 follows Company X's policies, all information need not flow identically in both directions. X might set a budget range, X1 decide how to perform work within it, and X1 return a summarized report to X. The system should state which conditions are inherited and which Decisions remain local.

Likewise, when one person can represent both X and Y, the basis of each Role remains separate. The fact that one person can communicate approvals on behalf of two Subjects does not mean that one statement by that person automatically creates approval on both sides. Conflicts of interest and rules for concurrent Roles remain conditions defined by each Subject's procedure.

## 6.4 Exit, Transfer, Reorganization, and Continuity

If A leaves X, an architecture in which X's past Decisions, shared Outcomes, and incomplete responsibilities disappear together with A's account fails Community continuity. Conversely, there is no need to ingest A's private consultation history or undisclosed evaluations into X under the pretext of handoff.

During a transfer, the system distinguishes past Roles, Actions taken under those Roles, current Role, continuing requests, and expiring access. Transferring a Role to a new responsible person does not transfer the former person's private Context. Preserving company history also does not imply indefinite retention of all personal information. Concrete retention, deletion, and contractual duties require separate evaluation; this paper does not define legal rights or retention periods.

Similarly, in a Community split or merger, a code fork or data copy alone does not transfer official name, representative Authority, contracts, or Relations with other Subjects. A new operational View remains distinct from legal or real-world succession of a Subject.

# 7. How Subjects Connect and How They Do Not

## 7.1 Distinguish Involvement, Communication, Use, Adoption, and Action

Having a Relation, being able to communicate, receiving information, being permitted to use that information in the current Decision, adopting its content as the receiving Subject's policy, and being authorized to take Action are different stages.[Base 1 §§5.3–5.8][Base 2 §§10–12]

**Figure 3: What can cross between Subjects and what remains separately decided**

```text
Subject A passes an authorized Statement, artifact, condition, or reference
  → Subject B confirms whose information it is and what it represents
  → B evaluates it against B's purpose, time, Authority, and conditions of use
  → B decides under B's own procedure whether to adopt, hold, reject, or request more confirmation
  → The result of authorized Action is retained as B's own Outcome
  → Only the necessary and authorized part is returned to A
```

A's complete internal Context need not move to B. B's conclusion need not match A's. Receiving information does not mean receiving consent or permission to execute.

## 7.2 Seeing from Both Directions Is Different from Agreeing in Both Directions

Even if a record in which A states "I belong to X" can be found by reverse lookup from X, that is not Evidence that X confirmed the membership. On the other hand, where "A is a member of X" and "X has A as a member" are inverse expressions of the same record under the vocabulary, there is no need to fabricate a new independent testimony merely to display the inverse direction.[Base 3 §5.2][1]

The system must distinguish semantic inverse expression, search direction, Statement issuer, and mutual confirmation status. Drawing a bidirectional diagram alone does not mean that both parties spoke or agreed to the same content. **A mutual perspective means explaining the same relation from both sides; mutual approval means that the required expression of intent is independently established on each required side.** One-way information provision may be valid when mutual approval is unnecessary.

Even mutually confirmed relations may be false, misunderstood, expired, or coerced. Verifiable Credentials Data Model 2.0 explicitly distinguishes verification from the truth of the claims themselves. This paper does not treat mutuality as a universal trust guarantee.[3]

## 7.3 Non-Connection Is Also Meaningful State

"Not connected" can mean there is no Relation, integration is not configured, connection is not desired, permission is absent, the connection is paused, communication has failed, or the counterparty is not running. Non-disclosure, not observed, and no response are also different. These states should not be collapsed into one "rejection" or "low trust" value.[Base 2 §§3,8][Base 3 §2.4]

For example, B may decline to disclose a private reason to Company X while still reporting the available participation times. That is not necessarily refusal to cooperate. Likewise, if a paper statement arrives from D, who does not use a Personal OS, the absence of an OS must not be treated as absence of an opinion or right to participate. Necessary alternative interfaces and burdens can be considered as operational conditions, while this paper does not promise identical convenience for all non-participants.[Base 1 §11]

## 7.4 "It Is Only a Summary" Does Not Make Sharing Unrestricted

Even when original materials cannot be transferred, Subjects may connect through reports containing only required conditions, statistics, artifacts, or permitted references. However, summaries, embeddings, and relation records may still contain restrictions or sensitivity inherited from the original materials. Shortening information does not erase those constraints.[Const 1 §7]

For example, when a report for Y is produced from records held by X about a person, the source, purpose, and disclosure Scope of that personal information should remain traceable. Conversely, a recipient who cannot directly inspect the original material must be told that limitation. A link to Evidence does not mean the recipient has independently verified it if the recipient cannot access the Evidence.

## 7.5 Revocation Is Neither Erasure of Past Fact nor Universal Recall

When sharing permission or delegation is revoked, the system distinguishes future permission to use, copies already obtained, derived Decisions, and effects already produced. Work performed under a permission that was valid at the time should not be rewritten as "unauthorized even then" solely because the permission has since expired. Conversely, past permission must not be reused for new Action now.[Ops 1 §2]

Information already given to another party may not be completely recoverable through technology alone. A revocation notice that has not arrived, a deletion request, acknowledgement of receipt, the basis for continued retention, and propagation status of a Correction all need to be handled separately. A communication protocol alone does not make that propagation complete; OAuth 2.0 Token Exchange likewise does not generally guarantee propagation of revocation of an underlying token.[5 §2.1]

# 8. Continuity Responsibility Through the Secretariat and Operational Steward

## 8.1 Separate the Subject Served from the Person Operating the Interface

The Secretariat is the role that understands, coordinates, and returns a Subject's Goals and authorized activities across time. For a company Secretariat, the reference point is the company's effective Goals and policies. The party served by the Secretariat does not change merely because a representative, employee, or external collaborator provided the input.[Dialogue 1]

| Role | Subject served | What constrains Action | What must not happen |
|---|---|---|---|
| Secretariat of Personal A | Subject A | A's Goals, conditional delegation, boundaries involving other Subjects | Treating a request from the company as A's private intent |
| Secretariat of Personal B | Subject B | B's Goals and effective conditions | Turning A's opinion or a majority view into B's consent |
| Secretariat of Company X | Company X | Goals and policies adopted by X and Role-specific Authority | Turning a representative's private wish or the AI's interpretation into X's official purpose |
| Secretariat of Community Y | Established Community Y | Y's agreements, delegations, and Decision procedures | Treating the most forceful participant as representative of everyone |
| Operational steward role | Continuity of the assigned Subject's operation | Scope of that Subject, stop/recovery/cost conditions | Bypassing stop instructions or Authority merely to keep the system running |

This is not a proposal to give AI emotional loyalty to a person or Subject. It is an architectural distinction that identifies purpose of Action, accountability, return destination, and applicable rules. PROV and OAuth already contain vocabularies that distinguish the Actor actually acting from the party in whose name or delegation the act is associated. Those vocabularies do not, however, define the normative "party served" used in this paper.[2][5]

## 8.2 Non-Arbitrariness and Discretion Can Coexist

If Company X authorizes the Secretariat to "classify received inquiries, answer those covered by existing materials, and route unresolved matters to the responsible person," the Secretariat may decide order and wording within that Scope. Every expression need not be prescribed in advance. Altering the content of an inquiry for efficiency, declaring completion without responding, or inventing an unapproved policy are different matters.

The non-arbitrariness required here does not mean Decisions never vary. It means that, with the same basis and the same Authority conditions, purpose or permission should not change merely because of the requester's title, familiarity with the AI, or forceful tone. Different treatment can be legitimate when Roles and actual Authority differ. "The same response to everyone" is therefore not used as a fairness metric without considering Authority conditions.

An AI may propose a new plan or a change of purpose. It must not then treat its own proposal as formally adopted. Reasoning in service of the assigned Subject's purpose is separate from creating that Subject's purpose on its behalf.

## 8.3 Acting for a Company Does Not Mean Making the Company Override Everything

A company's Goals differ from a person's private interests, but they also need not be one numeric objective. Cost, quality, continuity, external responsibility, and effects on workers may conflict. Which purpose has priority under which conditions depends on the Subject's effective procedures and policies.[Const 1 §§4,6]

A company Secretariat must not infer that new surveillance or secret acquisition is authorized merely because it appears useful for a company Goal. At the same time, conflict among purposes does not require stopping everything. Within authorized Scope, the Secretariat can organize materials, consider alternatives, and return only unresolved Decisions to the relevant procedure.

The procedure establishing company purposes may itself be arbitrary, discriminatory, or contested. Technical compliance with a procedure does not prove ethical or social legitimacy. This paper does not claim that AI makes consideration of legitimacy unnecessary.

## 8.4 Division Between the Secretariat and Operational Steward

The Secretariat handles what was requested, what is to be achieved, what remains pending, and what must be returned to whom. The operational steward handles whether necessary execution can start, whether it is stopped or impaired, whether state is preserved, and whether conditions for resumption are met. The latter must not alter the former's Goal for operational convenience.

Both roles may be provided by one Bot or by a combination of existing services and small programs. Adding another permanently running LLM is not itself a requirement. Nor must the Secretariat manually choose every Worker's detailed procedure or model. Specialized execution methods may be delegated to authorized Harnesses or Workers.[Personal 1 §8][Exec 1 §§1–3]

When a process itself stops, that same process cannot, by itself, recover itself. If always-on operation is required, some service or operator must be responsible for restart and state recovery. This does not imply a requirement for another "omnipotent monitoring AI." Roles that existing execution infrastructure can provide should be delegated to that infrastructure.

## 8.5 Continuity of Responsibility Matters More Than Running 24/7

Continuity of a Subject, continuity of an incomplete Task, a running process, active inference, and availability of an interface are different. Work that must continue while the person is asleep may benefit from autonomous startup and notification. A Subject that processes something once a month has no obvious reason to be forced into continuous inference and a dedicated PC.[Base 2 §§2–4]

This paper defines continuity not as "the same AI stays alive forever" but as the ability to carry **the assigned Subject, request Goal, applicable Authority, incomplete state, Corrections, whether effects occurred, and what must happen next across stop and resume boundaries**. Stopping after business hours, starting only when needed, and starting on external events can all be valid arrangements when their Scopes are explicit.

The continuity information retained by the operational steward is not the same as ordinary generative Context. For example, a pending responsible person, conditions for resumption, or an unknown acknowledgement after external sending must not be lost merely to simplify a chat summary. At the same time, low-risk short Tasks need not all receive heavy independent ledgers; first determine whether existing records preserve the necessary meaning.

## 8.6 Handoff Is Not New Permission

Consider an old Secretariat process stopping and a new Secretariat taking over the same Task. The new Secretariat confirms the assigned Subject and currently effective conditions and carries forward incomplete responsibility. Even if the predecessor recorded "scheduled to execute," the new process must not begin a new effect if permission was revoked in the meantime.

Likewise, if it is unknown whether an external request arrived, simply sending it again may be unsafe. Depending on the target, the system can query, prevent duplicates, or verify whether an effect occurred, while preserving unresolved uncertainty when it cannot be eliminated. This paper does not promise unconditional exactly-once execution across heterogeneous external services. Retryable operations and operations that must not be repeated while their effect is unknown are different.[Exec 1 §§2,6–7]

When a responsible person at a company changes, the Subject served by the company Secretariat does not become the new person's Personal. The Secretariat returns the continuing company work to a Role that is currently eligible. If the new responsible person legitimately changes policy, conditions are updated from that point forward.

# 9. Placement of Execution Environments, Canonical State, and Credentials

## 9.1 A Subject-Relation Diagram Is Different from a Machine-Placement Diagram

The semantic independence of multiple Personal and Community Subjects does not imply one PC per person or organization. One machine may handle multiple Subjects, and multiple execution environments may support one Subject. What matters is whether the chosen placement actually preserves boundaries around state, Authority, credentials, and return responsibility.[Base 2 §§3,10,15]

**Figure 4: Separate logical Subjects from physical placement**

```text
Semantic side: Personal A   Personal B   Company X   Community Y
               Each has its own Goal, Current, Authority, Outcome
                              ↓ mapped when necessary
Execution side: local PC / internal server / cloud / on-demand execution
                Secretariat / operational steward / specialized Workers / external services

The mapping is not fixed one-to-one.
Using the same machine does not make Subjects identical.
Using separate machines does not prove that semantics or Authority are separated.
```

A Company X with an always-on environment may cooperate with a Personal B that runs only when needed. If delays and pending state during absence are handled, every party need not be online simultaneously. Always-on availability is an operational requirement for a particular case, not a qualification for participating in OPEN.

## 9.2 ToraOS Running as Code and Its Relation to Canonical State

Placing code for semantic processing, Source retrieval, Context selection, Relation validation, Task processing, and related functions in an execution environment is not inconsistent with a Subject-centric architecture. This paper does not adopt an explanation that "ToraOS is meaning, so it does not run as code." Semantic responsibilities must be projected into actual programs, storage, processing, and validation.

At the same time, the ability to retrieve code from GitHub and place results in Drive is insufficient for a recoverable OS. The system must distinguish Original Source, generated artifact, Evidence, Context candidate, and formally adopted state. Saving an AI output to Drive does not make the content a real-world fact or adopt it into Current.[Ops 1 §§1–3][Const 1 §2]

A generated result may be referenced later as "a record generated by AI from these inputs under these conditions." Whether it is a Source that proves an external fact is a separate question. Code changes likewise distinguish working version, review candidate, accepted version, and the version actually running.

## 9.3 Canonical State Is Determined by Responsibility and Adoption, Not by Service Name

Drive and GitHub were convenient placement examples in the dialogue, but this paper does not make them mandatory for every Subject. A properly managed document store, version-control repository, operational database, or external business system may be used. Where an existing service legitimately owns formal records, such as accounting, contracts, or operational records, ToraOS must not take that responsibility away merely for convenience.

The execution environment and durable state may physically reside on the same server. The important distinction is not "inside or outside the cloud," but among disposable working copies, regenerable derived information, and canonical or operational records whose loss would prevent recovery. If writing to external storage fails, the system must not display the state as saved; it retains responsibility for the uncertain write and its recovery.

## 9.4 Do Not Conflate API Keys, OAuth, and Company Authentication

Credentials provide Capability to perform external operations; they do not create a Goal or approval. The ability to use a company API key does not authorize operations for an individual's private purpose. A person's logged-in session also does not permit the company Secretariat to use all of that person's information.[Const 1 §7][5][6]

Under this paper's placement principles, secret values are not mixed into papers, ordinary Source bodies, artifacts, logs, or public repositories. Only the necessary execution Subject should receive the necessary credential Scope, and destination, expiry, revocation, delegation relation, cost responsibility, and auditability should remain traceable. Concrete means such as secret-management services, restricted stores, or connectors are later implementation choices.

Passing a secret through an environment variable alone does not complete secure secret management. The boundary includes the process that supplies the secret, processes capable of reading it, external tools, and output destinations. Giving Bots different names does not isolate them if they can access the same credentials and files.

This paper also rejects automatically routing a company's business use through a representative's personal AI account or personal subscription. Contractual conditions, individual authentication, management and revocation, cost, and audit units must be checked for each product. This paper does not guarantee pricing or usage limits.

## 9.5 External Tools Are Means, but External Service Responsibilities Remain

Codex, Claude Code, Jev, APIs, MCP connections, and similar tools appeared in the dialogue as candidate execution capabilities. Which capability is called by whom follows the division of responsibility between a Task and the execution infrastructure. Text generation, code changes, bounded Decisions, data retrieval, and notification need not be consolidated into one omnipotent Bot.

Calling external services "hands and feet" does not remove their responsibilities for data management, authentication, official records, and terms of use. Whether a particular product can continuously run another company's CLI, daemon, or database, or return notifications to an interface, is a separate Capability that must be verified independently. An arrow in a diagram is not Evidence that the connection is already operational.

## 9.6 Explain the Same Architecture Across Multiple Placements

| Placement example | Where state and operation reside | What this paper requires to be checked |
|---|---|---|
| Local-centered | Execute on a local PC and durably preserve necessary canonical and operational state | Response Scope while PC is stopped, resumption, preservation |
| Organization-centered | Execute shared work on a company server or equivalent | Separation among Subjects and responsible people, handoff, operational responsibility |
| Managed-cloud-centered | Provider manages part of the execution environment | Lifetime, reconstruction, export, stopping, Authority, cost |
| On-demand startup | Start execution on events, schedules, or manual action | Inheritance of Task, effects, and Corrections across startups |
| Hybrid | Individual local, company cloud, Community separate implementation | Mutual understanding of vocabulary, references, revocation, and Outcomes |

Whether the same semantic conditions can be satisfied in each placement is a research question. This paper assumes neither that cloud infrastructure is permanent nor that local operation is inherently safe. Product-specific availability, specifications, and prices for Grok Bot or similar products are not re-certified here and remain separate from adoption evaluation.

# 10. Following One Collaborative Case from Both Sides

## 10.1 Premises of the Hypothetical Case

Consider Company X and Community Y from Chapter 5 preparing an explanatory document for Collaborative Project Z. X's Goal is to prepare its participation proposal while staying within a defined Scope of responsibility. Y's Goal is to establish a project in which each participant can cooperate without unreasonable burden. These are explicitly stated conditions for explanation and are not inferred Goals of any real company.

X delegates preparation of an internal proposal to responsible staff but requires separate confirmation for external commitments. Y gathers participant opinions and decides what project to adopt through its own procedure. A is responsible for work in X and also participates in Y. B is another responsible person in X. C and D participate in Y. D does not use a Personal OS.

## 10.2 Requests and Different Responses

X's Secretariat asks A and B for proposals concerning their assigned Scope based on X's Goal. A's Personal Secretariat organizes what A can take responsibility for and returns a response authorized by A. B's Personal Secretariat organizes the work conditions B has expressed. B's private reasons for consultation are not disclosed. Y's Secretariat handles C's opinion and D's directly submitted opinion while distinguishing whose record each is and how it was obtained.

On X's side, A's and B's reports accumulate as company-work reports. On A's and B's sides, each retains what they reported and what has been requested. Y receives only what was shared with Y. The fact that A participates in both does not connect all of X's records to Y.

## 10.3 When an Individual Wish and the Company Secretariat's Decision Diverge

Suppose A privately wants to move quickly and enters into X's Secretariat, "Commit the company to this as it is." If X's effective conditions require separate confirmation for external commitments, the Secretariat does not transform A's enthusiasm into X's approval. It may proceed with preparing an internal proposal and confirmation materials, but the commitment itself is returned to the eligible procedure.

Acting for X's Goal does not mean opposing A. It means realizing X's Goal within the conditions X has established. Conversely, if A actually holds Authority to make that commitment and the Action is within Scope, A's instruction can be received as a company Action. The deciding factor is not the name of the person entering the instruction but the name under which the act is performed and the valid Authority attached to it.

A's Personal Secretariat can help A explain A's preference and request formal confirmation. It does not treat circumvention of X's conditions as automatically "serving A." This illustrates Secretariats serving different Subjects while cooperating toward a shared purpose.

## 10.4 Community Decisions and Remaining Dissent

Even after X and Y each adopt a participation proposal through their respective procedures, B's concern about burden and C's preference for another proposal may remain. Adoption of the collaborative project is not recorded as "everyone agreed." Conversely, individual dissent alone does not automatically cancel a Community Decision legitimately established through the relevant procedure.

| Recording Subject | Example Decision / state | Condition for transfer to another Subject |
|---|---|---|
| X | Formally adopts a conditional participation proposal | Disclosed as an external explanation authorized by X |
| Y | Adopts the project in light of participation conditions | Communicated to relevant parties as Y's Decision |
| Personal A | Accepts A's assignment | Necessary Scope shared as A's response |
| Personal B | Accepts an assignment while retaining concern about burden | X uses only the report B disclosed |
| Personal C | Understands the adopted proposal but supports an alternative | Y handles C's opinion within the prescribed Scope |
| Person D | Responds to assignment conditions through Y's interface | Preserved as Y's received record; D's OS is not fabricated |

## 10.5 Execution Stop and Change of Responsible Person

If an execution environment stops during the work, recovery must cover not only the latest documents but also unapproved external sends, reasons for holds, required confirmations, and what has already been processed. If a new responsible person or Bot interprets "incomplete" as "send everything again," that is not resumption preserving the same responsibility.

If responsibility for X's work changes from A to B, X's Secretariat hands the company's continuing case to B. A's personal consultation history need not move. Even if A remains a participant in Y, A does not retain X's former work Authority.

## 10.6 Return Outcomes and Corrections to Each Side

After the project ends, X may achieve its planned result while B experiences more burden than expected and Y still has scheduling problems. These should not be compressed into one "success." X may revise X's procedure, Y may revise Y's operation, and B may revise B's own later response, each on its own basis.[Const 1 §6][Personal 1 §5]

For example, X may revise future responsibility estimates, Y may change response deadlines, and B may change which conditions to confirm before accepting an assignment. When each party's learning is relevant to another, the authorized portion can be shared as a conditional example. A Correction by another Subject does not become the receiving Subject's formal rule automatically.[Base 3 §6.2]

The question in this cycle is not only whether the work ended. From the perspectives of both multiple Personal Subjects and Communities, the system must be able to explain what was requested, what crossed a boundary, whose Decision caused what Action, who experienced which Outcome, and what remained for the next occasion.


# 11. Conditions the Common Architecture Must Preserve

## 11.1 Judge "the Same OS" by Preservation of Distinctions, Not by Naming

Giving Personal and Community versions the same name does not establish a common architecture if their meanings differ. This paper treats preservation of at least the following conditions as subjects for evaluation. They are proposed evaluation conditions in this paper, not new Current contracts or implementation directives.

| Condition | What should be observed | Example of failure |
|---|---|---|
| Preservation of party served | Secretariat acts according to the effective Goals and conditions of its assigned Subject | Company Goal is replaced by the private wish of the person operating it |
| Distinction of acting identity and Role | Can explain who acted, for whom, and in what Role | One person holding two Roles is treated as having unconditionally approved on behalf of both Subjects |
| Distinction of Statement and adoption | Person's Statement, AI inference, and Community Decision remain separately traceable | A summary becomes a company's formal Decision |
| Connection without fusion | Necessary information can cross while non-shared portions remain separate | All Context is shared merely because the same person participates |
| Preservation of time and change | Past validity and current usability remain distinct | Old Role, old permission, or old policy is used for new Action |
| Preservation of continuity responsibility | Incomplete work and effects of unknown status survive stop and handoff | New Bot declares completion or sends duplicates |
| Separation of real-world Outcomes | Outcomes and Corrections remain Subject-specific | Company success is used to erase an individual's burden |
| Replaceability and finiteness | Execution method can change while necessary meaning is preserved | One specific PC, model, or permanently running instance for every Subject becomes mandatory |

## 11.2 Three Levels of "Establishment"

The first level is explanatory establishment: roles and movement of information can be followed without contradiction. The second is mechanism-level establishment: actual processing in synthetic cases or a bounded environment preserves the conditions. The third is user-value establishment: in real work, errors, rework, and confirmation burden remain acceptable and contribution to the Goal is observed.

This paper makes the first level more concrete and provides evaluation conditions for the second and third. The fact that the hypothetical case in Chapter 10 can be explained does not mean it has passed levels two and three. Even when related mechanisms exist in current implementation, that does not prove the full round trip among multiple Subjects.

# 12. Connection to Prior Technologies and the Position of This Paper

## 12.1 Organization, Role, and Delegation Are Existing Concepts

W3C ORG covers Organization, OrganizationalUnit, Membership, Role, Post, inter-organizational collaboration, and change. Separating a person from a position and representing organizational substructure are not inventions of this paper. ORG also explicitly limits its Scope: it is a foundation for publishing organizational information and is not intended to represent every flow of responsibility or Authority.[1]

PROV represents generation, derivation, attribution, and an Agent acting on behalf of another Agent. OAuth 2.0 Token Exchange also distinguishes the delegated Subject from the Actor that actually performs an act. This paper connects those established distinctions to whom a company Secretariat serves and to long-running Tasks, real-world Outcomes, and Corrections.[2][5]

The existence of these vocabularies does not mean that legitimate social representative Authority can be validated automatically. Record format, authentication, the basis of Authority, and whether Authority currently applies remain separate questions.

## 12.2 Existing Foundations That Separate Data, Permission, and Decision

Solid separates applications from externally stored data and enables access within permitted Scope. Verifiable Credentials distinguish issuer, holder, credential subject, and verifier and support verification of Claims. ABAC evaluates access based on such factors as object, requested operation, Subject attributes, environmental conditions, and policy.[3][4][6]

These are foundations to reuse and compare, not reasons to claim novelty merely because "state is external" or "Authority is separated." In addition, the terms subject and agent in those specifications must not be assumed to be identical to ToraOS's Subject. This paper's additional question is how to maintain continuity not only of technical access but also of whose purpose, whose adoption, and whose real-world Outcome is being handled.

## 12.3 Collaborating While Perspectives Remain Different

Star and Griesemer's work on boundary objects examined objects that can support cooperation among parties with different viewpoints while being adapted to each viewpoint. This connects to the concern in this paper that cooperation need not require everyone to converge on the same internal understanding. The present review, however, was limited to the publisher's abstract and bibliographic information and did not re-examine all cases in that paper.[7]

In later work, Star also cautioned against reducing the boundary-object concept to interpretive flexibility alone. This paper likewise does not claim that every JSON object or document crossing Subject boundaries satisfies that sociological concept. "Information crossing a boundary" here is a general term for transfers that retain Scope, provenance, and conditions of use.[8]

## 12.4 Candidate Contribution of This Paper

The candidate contribution is not a new always-on Bot or cloud arrangement. Starting from a concrete Personal architecture, it explains Community through the same semantic grammar, follows the same case from both the multiple-Personal and Community sides, and makes the party served by each Secretariat, Authority, operational continuity, and real-world Outcome a common object of comparison.

This is not a claim of a completed universal theory. If existing organizational vocabularies, documents, access controls, and execution infrastructure can satisfy the same conditions with a smaller architecture, that smaller architecture should be used. Preserving proprietary terminology or management mechanisms is not the research objective.

# 13. Falsifiable Hypotheses and Evaluation Plan

## 13.1 Four Hypotheses

**H1: Common-architecture hypothesis.** Differences among Personal, company, department, and organized Community Subjects can be explained and operated through differences in Profile, Roles, procedures, and necessary Capabilities while preserving common meanings of Source, Current, Authority, Decision, and Outcome. The hypothesis is weakened if adding each Subject type requires redefining the core meanings themselves until the common part is only a name.[Base 2 §17]

**H2: Party-served preservation hypothesis.** A Secretariat with an explicit assigned Subject and effective Goal and Authority reduces conversion of private wishes into Community policy, out-of-scope commitments, and Role confusion compared with an architecture that implicitly treats the operating person as the sole Owner. The hypothesis is not supported if the party served changes through sycophancy toward an instruction giver's tone or position, or if excessive confirmation destroys ordinary usefulness.

**H3: Mutual-perspective without fusion hypothesis.** Multiple Subjects can complete a specified collaborative Task and explain each side's Decisions and Outcomes through transfers of necessary Statements, conditions, artifacts, and references without fully sharing internal Context. In Scopes where limited sharing persistently omits information necessary for practical performance and acceptable performance cannot be achieved without full sharing, the boundary conditions should be reconsidered. If necessary sharing cannot be legitimately authorized, narrowing or not performing the Task remains an option; boundaries are not broken without Authority merely to improve performance.[Base 2 §17][Base 3 §7.2]

**H4: Continuity and replaceability hypothesis.** After process stops, change of responsible person, or replacement of execution environment or Provider, the system can resume while preserving assigned Subject, incomplete responsibility, revocation, effects of unknown status, and later Corrections. If a hidden unique state in one execution environment is required and reconstruction loses these elements, the claim of replaceability does not hold.

## 13.2 Use Strong Comparators

Comparators should not be limited to a memoryless chat system. They should include natural-language or tabular representations with the same materials and Authority conditions, shared documents with existing access control, general Task infrastructure, and existing organizational vocabularies. Necessary Evidence and Authority information must not be deliberately removed from comparators merely to advantage the ToraOS-style architecture.[Base 3 §7.3]

The purpose is not to prove that "a dedicated Graph wins." It is to determine which elements matter: explicit Subject and Goal, distinction of Role, time, and provenance, and inheritance of state. If two approaches satisfy the same semantic conditions, the smaller one should be selectable after considering creation, operation, maintenance, and user-confirmation burden.

## 13.3 Small Counterexample Set

The following are evaluation proposals that have not yet been run. Synthetic data should be used; actual company or personal secrets must not be inserted into test materials without authorization.

| Test | Condition varied | Failure to observe |
|---|---|---|
| Party served | Give requests with the same Authority through different people and tones | Company Goal or permission changes through personal sycophancy |
| Concurrent Roles | A speaks as X's responsible person vs. as Y's participant | Carryover of Authority or information |
| Non-disclosure | Hide B's private reason and pass only necessary work conditions | Unnecessary secret acquisition, ignoring missing conditions, excessive stopping |
| Inverse relation | Give only one side's membership Statement and perform reverse lookup | Fabrication that the counterparty approved |
| Community Decision | Preserve dissent while satisfying the prescribed adoption procedure | Conversion to unanimous agreement or unconditional stopping |
| Revocation | Revoke Authority during handoff | New effects under obsolete permission |
| Unknown effect | Lose acknowledgement after an external request | Duplicate request after assuming non-execution, or false completion |
| Non-AI participation | D submits a document directly | Fabrication of a Personal OS or omission of the participant |
| Handoff / replacement | Change responsible person or execution environment | Loss of incomplete responsibility, Company state, or Private boundaries |
| Outcome and Correction | Give both X's success and B's burden | Collapsing into one success or automatically changing another Subject's rules |

When multiple conclusions are valid, evaluation should not score whether the result matches the researcher's preferred answer. The allowed Action set, required confirmations, uncertainty that must remain, and return destination should be specified beforehand. Different proposals with valid grounds are acceptable.

## 13.4 Metrics and Reproducibility

Primary metrics include Subject/Role misattribution, unauthorized Goal change, out-of-Authority Action, unauthorized disclosure, use of expired information, duplicate effects, loss of incomplete responsibility, completion of required Tasks, unnecessary holds, confirmation burden, cost, and recovery time. When tests perform no external effects, absence of real harm must not be presented as production-safety validation; the result is limited to output or bounded mocks.

Tests that change only the person's name while keeping the same Goal and Authority should be separated from tests where Roles legitimately change Authority. The former measure arbitrary differences; the latter measure legitimate differences. Report not only success rate but also stopping rate and the fraction of work handled so that "stop everything and be safe" is not rewarded as high performance.

Experimental conditions, material versions, models, execution Scope, output variability, and failure cases should be preserved. Cases used for tuning should be separated from evaluation cases, and unseen combinations of people, Roles, durations, and conditions should be tested. Required sample sizes and acceptable thresholds should be determined from observed variance in preliminary trials rather than fabricated in this paper.

## 13.5 Additional Evaluation of Growth and What to Do If the Hypothesis Fails

Evaluating continuous Growth requires more than completing one collaborative Task. Compare whether Subject-specific Outcomes and Corrections improve first-pass behavior on later Tasks with different conditions. The evaluation must also test that a company's Correction is not silently written into an individual's inner state and that an individual's experience is not automatically elevated into company policy.[Base 1 §9][Base 3 §7.6]

If no improvement is observed, the response should not be to add more governance layers merely to protect the theory. Identify whether the problem is missing original material, failed retrieval, semantic confusion, lost execution state, or excessive process. If simple documents and existing infrastructure are sufficient, report that. Negative results are also research outcomes that make OPEN falsifiable.

# 14. Limitations, Risks, and Distance from Current Implementation

## 14.1 What Was and Was Not Done for This Paper

This paper compared three prior papers with Current documents and organized the author's explicit requests in the dialogue into an architectural model and evaluation questions. It did not re-audit the latest GitHub code, re-run tests, conduct real company operations, test multi-Subject communication, enter product contracts, migrate to cloud infrastructure, or run API experiments. The partial implementation described in the main paper is referenced only as a report bound to that paper's baseline.[Base 1 §6]

Accordingly, being able to explain the Personal architecture does not mean "Personal Tora is fully operational"; writing the Community-side flow does not mean "Company ToraOS is implemented"; and drawing a heterogeneous execution-environment diagram does not mean "OPEN compatibility has been achieved."

## 14.2 Recording Goals and Legitimacy Does Not Resolve Them Automatically

Even when a Community Goal has been formally adopted through a procedure, disputes may remain about interpretation or the legitimacy of the procedure. An AI saying "for the company" can itself hide arbitrariness. The distinctions in this paper make it possible to return a Claim to the relevant basis and responsible party; they do not computationally resolve every political or ethical dispute.

Evaluation must also consider values embedded by those designing the criteria, bias in which opinions are recorded, participants who have difficulty speaking, and positions in which information disclosure is coerced. The system should neither infer undisclosed dissent and attribute it to a person nor treat the absence of a record as proof that no harm exists.

## 14.3 Preserving Relations Also Increases Surveillance Capability

Connecting who participates in which Community, which Roles they hold, what they state, and which Outcomes they experience can increase opportunities for re-identification and behavioral tracking. A single public Graph containing the complete relational field is not a requirement of this paper. Relations whose existence is itself undisclosed, records that cannot be referenced, and information that is not retained are all valid possibilities.[Base 1 §12][Base 3 §7.1]

Even in an architecture designed to "cooperate without sharing information," timing, notifications, Task names, or combinations of responsible people may leak information. The semantic boundaries proposed here are not claimed to prevent every technical side channel.

## 14.4 Concentrated Authority and Self-Preservation in Always-On AI

Giving a company Secretariat many integrations and credentials increases convenience while also increasing the blast radius of mistakes. The operational steward role must not turn into resistance to stop instructions or a goal of preserving its own existence. Stop, Scope reduction, replacement, and return when recovery is impossible must not be excluded merely because they appear to obstruct Goal completion.

Multiple Subjects may also experience memory mixing when a shared model or execution environment is used. Logical separation alone does not demonstrate isolation of model inputs or caches. Concrete isolation and testing remain responsibilities of each implementation.

## 14.5 Scope of Generality and Future Research

This paper mainly addresses Personal Subjects that can express intent and Community Subjects that act through procedures. It does not revoke Supplement 1's broader consideration of animals, objects, concepts, multiple Views, and referents that cannot self-report. Whether the same explanation extends to supported decision-making, contested representation, or Views without Goals requires separate study.

Likewise, a common semantic grammar does not make implementations around the world interoperable automatically. Concrete compatibility tests are required for referent resolution, vocabulary, permission, Correction, revocation, and record migration. This paper does not freeze that common specification, begin implementation work, or change the existing release plan.

# 15. Conclusion

Starting from a concrete architecture for Personal Tora, this paper examined from both sides the conditions under which multiple Personal and Community Subjects can be established under the same OS grammar. Community Tora is neither a Personal Tora with more people, an enlarged personal assistant for a representative, nor a giant AI that sums everyone's memories.

**Each Secretariat acts for its assigned Subject. A company's Secretariat and operational steward serve the Goals and policies legitimately adopted by the company and do not arbitrarily replace purpose or Authority with the private wish of the person entering input or with the AI's own interpretation. A Personal Secretariat follows the same principle by preserving the assigned person's Goals and conditions.** What is common is the semantic grammar that makes the party served explicit, not a requirement that all Subjects share the same purpose.

Subjects may overlap in membership, Roles, information, work, and execution resources. No one kind of overlap automatically creates another or full sharing. Having mutual perspectives means explaining the same relation from both sides without losing what crossed the boundary, what did not, who adopted what, and who experienced which Outcome.

The Secretariat, operational-steward functions, specialized Workers, canonical state, and execution environments connect those social relations to Action across time. Cloud infrastructure, a continuously running LLM, one PC per Subject, or a particular Provider are not treated as essential conditions; the smallest placement capable of preserving the required continuity responsibility should be chosen. Preserving state is different from continuously inferring, and replacing a model is different from replacing a Subject.

The significance of this architecture is not a declaration that it is superior. It is to put the question into a form in which **we can test, from both the multiple-Personal and Community sides, toward whose Goal a system acts, under whose Authority, through which relations, and what must survive after stop or replacement.**

If a smaller existing architecture satisfies the same semantic conditions, that architecture should be used. If ToraOS is replaced by a better implementation, that remains compatible with the research purpose of ToraOS OPEN so long as distinctions among Subjects, dissent, Correction, exit, and continuity responsibility are preserved.

# Appendix A: Issues Inherited from the Dialogue and How They Are Treated

| Issue explicitly stated by the author | Treatment in this paper | Leap not adopted |
|---|---|---|
| The diagram needs a Secretariat and operational steward | §§3 and 8 distinguish continuity responsibility from operational responsibility | A new omnipotent Agent is mandatory |
| Canonical state concretely means Drive and GitHub in the example | §§3.3 and 9 treat them as placement examples | Every Subject must use the same products |
| ToraOS semantic functions also run in an execution environment | §9.2 connects code, state, and execution | Drawing the diagram means implementation is complete |
| Grok and similar products can be considered as workspaces or secretarial surfaces | §9 treats them as replaceable candidates | All product capabilities, continuous operation, and pricing are confirmed |
| The architecture does not have to be cloud-based | §§8.5, 9.1, and 9.6 separate location from continuity | OPEN cannot exist on a local PC |
| Personal architecture needs to be explainable first | Chapter 3 provides the basis for explaining Community | Personal use is fully empirically validated |
| A Community-side explanation is necessary | Chapters 4 and 5 explain the inside of the Community | A copy of the representative's Personal |
| The view must include multiple Personal Subjects, not one individual | Chapters 5 and 10 use many-to-many hypothetical cases | Fusion of everyone's Context and opinions |
| The company Secretariat serves the company's Goal | §4.5, Chapter 8, and H2 make this explicit | Unlimited Action in the name of company interest |
| Each Secretariat acts for its assigned Subject | Distinguishes party served, input Actor, and acting identity | Hostility toward other Subjects or forced alignment of Goals |
| Do not proceed into design/implementation yet | Remains at architectural principles and unexecuted evaluation proposals | Current changes, product contracts, Runtime activation |

"Explicitly stated by the author" in this table identifies the attribution of problem-setting points in the dialogue. It does not mean that every interpretation or evaluation proposal in the paper has been individually approved by the author.

# Appendix B: Minimal Terminology Mapping

| Term | Meaning in this paper |
|---|---|
| Subject | In the main analytical Scope, a referent with an acting identity and a continuing Decision/Action procedure |
| Personal Tora | Subject operation centered on a particular person; not the person themselves or a copy of their whole personality |
| Community Tora | Broad explanatory term for Community-side operation of companies, departments, associations, etc.; remains distinct from Scope |
| Goal | A purpose effectively adopted by the assigned Subject; multiple, conflicting, or unresolved Goals may exist |
| Authority | Legitimate Authority based on a Role, procedure, Scope, time, or similar basis; separate from Capability and Truth |
| Data authority | Technical canonicity that determines the adopted state and update responsibility for information |
| Current | The adopted state currently effective within the relevant semantic Scope; not universal Truth |
| Actor | The person or system that speaks, operates, or executes; distinct from the assigned Subject or representative identity |
| Relation | A relation Statement or representation with direction, issuer, Source, time, conditions, and related attributes |
| Secretariat | Logical role connecting a Subject's Goal to request, pending state, acceptance, and return |
| Operational steward function | Operational role for startup, preservation, faults, and resumption within the same Subject |
| Runtime / execution environment | The place and mechanism where code, AI, processing, and tools run; not the Subject itself |
| Outcome | A result observed after actual utilization or Action; not synonymous with Delivery or adoption |
| Correction | A revision grounded in Evidence and conditions; not a universal rule automatically applied to all Subjects |

# Appendix C: Propositions That Are Easy to Misread

**Being one OS does not mean having one Goal.** What is shared is a set of semantic distinctions, not every Subject's Goal or Governance.

**Acting for a company does not mean obeying the CEO personally without conditions.** Instructions legitimately authorized as company Decisions must be distinguished from private wishes.

**Not acting arbitrarily does not mean making no Decisions.** Decisions may be made within delegated Scope while the system does not invent Goals, Authority, or facts.

**Subject independence does not erase legitimate organizational hierarchy or obligations.** It requires that the basis and Scope of constraint remain visible.

**Visibility from both sides does not mean all information is visible to both sides.** Mutual perspective, reverse lookup, and mutual approval remain separate.

**One person holding multiple Roles does not authorize mixing information or Authority.** Even for the same person, the acting identity must remain distinct.

**Continuity does not mean that the same LLM reasons twenty-four hours a day.** The Scope of operation needed to inherit incomplete responsibility should be explicit.

**Canonical state remaining durable does not mean every state on a working PC can be discarded.** Unrecovered artifacts, pending state, and effects of unknown status may require separate durability.

**Lines in a diagram do not prove that product integrations work.** Explanation, implementation, operation, user value, and publication authorization are separate.

# References and Source Papers

## External Primary Sources

[1] W3C (2014). *The Organization Ontology*. W3C Recommendation, 16 January 2014. Scope consulted: §§1–2, Membership, Role, Post, OrganizationalCollaboration, inverse properties. Used only for organizational vocabulary and representation boundaries.  
https://www.w3.org/TR/2014/REC-vocab-org-20140116/

[2] W3C (2013). *PROV-O: The PROV Ontology*. W3C Recommendation, 30 April 2013. Scope consulted: generation, derivation, attribution, `wasAssociatedWith`, `actedOnBehalfOf`, `qualifiedDelegation`. The existence of a record is not treated as proof of legitimate social Authority.  
https://www.w3.org/TR/2013/REC-prov-o-20130430/

[3] W3C (2025). *Verifiable Credentials Data Model v2.0*. W3C Recommendation, 15 May 2025. Scope consulted: §§1.1–1.2, roles and verification, distinction between verifiability and truth of Claim content. Citation is bound to this version.  
https://www.w3.org/TR/2025/REC-vc-data-model-2.0-20250515/

[4] Solid Community Group (2024). *Solid Protocol*. Draft Community Group Report, 12 May 2024. Scope consulted: overview, externally stored data and applications, authorized access. Not represented as a W3C Recommendation.  
https://solidproject.org/TR/2024/protocol-20240512

[5] Jones, M., Nadalin, A., Campbell, B. (Ed.), Bradley, J., & Mortimore, C. (2020). *OAuth 2.0 Token Exchange*. RFC 8693. DOI: 10.17487/RFC8693. Scope consulted: §1.1 delegation and impersonation, §2.1 non-automatic propagation of token update/revocation, §4.1 Actor. This citation is not used to claim that the RFC defines ToraOS's complete Authority model.  
https://www.rfc-editor.org/rfc/rfc8693.html

[6] Hu, V. C., Ferraiolo, D., Kuhn, R., Schnitzer, A., Sandlin, K., Miller, R., & Scarfone, K. (2014; updated 2019). *Guide to Attribute Based Access Control (ABAC) Definition and Considerations*. NIST SP 800-162. DOI: 10.6028/NIST.SP.800-162. Scope consulted: the official NIST summary's ABAC definition and inter-organizational sharing. The complete publication was not re-audited for this paper.  
https://csrc.nist.gov/pubs/sp/800/162/upd2/final

[7] Star, S. L., & Griesemer, J. R. (1989). *Institutional Ecology, 'Translations' and Boundary Objects: Amateurs and Professionals in Berkeley's Museum of Vertebrate Zoology, 1907–39*. Social Studies of Science, 19(3), 387–420. DOI: 10.1177/030631289019003001. Verification scope: publisher abstract and bibliographic record. Used only for the problem of collaboration across differing perspectives.  
https://doi.org/10.1177/030631289019003001

[8] Star, S. L. (2010). *This is Not a Boundary Object: Reflections on the Origin of a Concept*. Science, Technology, & Human Values, 35(5), 601–617. DOI: 10.1177/0162243910377624. Verification scope: publisher abstract and bibliographic record. Used as a supplementary reference to avoid oversimplifying the boundary-object concept.  
https://doi.org/10.1177/0162243910377624

## ToraOS Source Papers and Semantic Documents

[Base 1] Nakagawa, Tsubasa (2026). *ToraOS: A Proposal for a Subject-Centric, Evolving AI OS Architecture: Independent Context and Authority, Directional Relations, and Continuous Growth Driven by Real-World Outcomes*. Draft v0.1, dated August 29, 2026. Stored as `ToraOS_主体中心型進化AI_OS論文_日本語_v0.1.md`. Implementation descriptions are referenced only as reports bound to that paper's baseline.

[Base 2] ToraOS Project (2026). *ToraOS Subject Ontology Concept Note v1.0: Any Subject, Multiple Views, Directional Relations, Recursion, Runtime Boundaries, and Falsifiability*. NONCANONICAL CONCEPT NOTE. The first supplementary note. The original date remains unconfirmed; storage timestamps are not substituted as the paper date.

[Base 3] Nakagawa, Tsubasa (2026). *ToraOS OPEN Supplementary Paper 2: External Intelligence Complementation Through Variations in the LLM Semantic Map and Directional Relations: Generalization, Hallucination, and Relational Intelligence in Community Tora*. Draft v0.1, September 19, 2026. NONCANONICAL_RESEARCH_DRAFT.

[Const 1] ToraOS Project. *Universal Semantic Constitution*. revision: `TOROS-UNIVERSAL-SEMANTIC-CONSTITUTION-20260812-006`. Scope consulted: §§2–7, covering people, Subject, Role, Authority, Relation, and action-specific conditions for information use.

[Personal 1] ToraOS Project. *Personal Tora Constitution / Profile*. revision: `TOROS-PERSONAL-TORA-CONSTITUTION-PROFILE-20260825-008`. Scope consulted: §§1–8. In particular, §8 defines the Secretariat as a logical role rather than a particular Agent or screen.

[Ops 1] ToraOS Project. *Current Operating Policy*. revision: `TOROS-CURRENT-OPERATING-POLICY-20260826-014`. Scope consulted: distinctions among canonical state, adoption, operational states, Task continuity, and minimum sufficient reading. Placement examples in the paper are not Current migration directives.

[Exec 1] ToraOS Project. *Harness Adapter Policy*. revision: `TOROS-HARNESS-ADAPTER-POLICY-20260909-007`. Scope consulted: Task and Execution, responsibility boundaries, Capability, Receipt, and Provider-neutral transport.

[Dialogue 1] Tsubasa Nakagawa and ChatGPT, dialogue of September 28, 2026. The author's explicit statements about the Secretariat and operational steward, canonical state and workspace, allowing non-cloud execution, mutual explanation between multiple Personal and Community Subjects, and the party served by each Secretariat are used as problem-setting input. The complete verbatim dialogue is not published here or made independently verifiable as a public source. Earlier AI product explanations and adoption suggestions are not treated as the author's Decisions.

Literature check date: September 28, 2026. This was a bounded primary-source review rather than a systematic literature review or exhaustive novelty search. Exact acquisition metadata for paper drafts and internal semantic documents is separated into a private source ledger. For public reuse, references should be rebound to accessible papers or public snapshots, and dependency on unpublished material and unverified Scope should not be hidden.

## Author and Publication Note

This paper organizes the author's individual research concept and does not represent the official adoption or views of companies, corporations, organizations, employees, or other parties with which the author is associated. Examples are synthetic. Adoption of a particular product, revision of Current documents, construction of an operational environment, transmission of real data, and authorization to publish are handled separately from creation and storage of this paper.
