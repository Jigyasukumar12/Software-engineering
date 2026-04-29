# Unit 2 — SRS, Requirements Engineering & SQA
> BCS601 Software Engineering | Tier A: Topics 3, 4 | Tier B: Topics 14, 15

---

## TOPIC 3 — SEI-CMM Model + ISO 9000 Comparison
`Frequency: 4/4 years` `Tier A` ← **Sabse important topic of entire syllabus**

---

### SEI-CMM — What is it?

**SEI** = Software Engineering Institute (Carnegie Mellon University)
**CMM** = Capability Maturity Model

> CMM is a framework that describes the key elements of an effective software process. It provides organizations a path to improve their software development processes over time.

**Purpose:** Evaluate and improve an organization's software development process maturity.

---

### 5 Levels of CMM (Must memorize)

```
Level 5 — OPTIMIZING     ← Best
Level 4 — MANAGED
Level 3 — DEFINED
Level 2 — REPEATABLE
Level 1 — INITIAL        ← Worst
```

**Detailed explanation:**

| Level | Name | Description | Key Feature |
|-------|------|-------------|-------------|
| 1 | **Initial** | Chaotic, ad-hoc process. Success depends on individual effort | No process. "Fire-fighting" mode |
| 2 | **Repeatable** | Basic project management in place. Past successes can be repeated | Requirements managed, planning done |
| 3 | **Defined** | Organization-wide standard process documented | Standard process for all projects |
| 4 | **Managed** | Process and product quality measured and controlled | Quantitative control using metrics |
| 5 | **Optimizing** | Continuous process improvement using feedback | Defect prevention, innovation |

**"State of fire-fighting" = Level 1 (Initial)** — asked in 2022-23 exam

---

### ISO 9000 — What is it?

> ISO 9000 is an international standard for quality management systems. It defines requirements that an organization must meet to demonstrate its ability to consistently provide products that meet customer requirements.

**ISO 9001** — most relevant standard for software (part of ISO 9000 family)

---

### SEI-CMM vs ISO 9000 Comparison (Table — must write in exam)

| Parameter | SEI-CMM | ISO 9000 |
|-----------|---------|---------|
| Full form | Capability Maturity Model | International Organization for Standardization |
| Origin | Carnegie Mellon University, USA | International standard body |
| Focus | Process improvement | Quality assurance |
| Approach | Prescriptive (tells what to do AND how) | Descriptive (tells what to do, not how) |
| Levels | 5 maturity levels | Pass/Fail (certified or not) |
| Assessment | Internal + external appraisal | External audit/certification |
| Goal | Continuous improvement | Minimum quality baseline |
| Applicability | Primarily software industry | Any industry |
| Certification | No formal certificate | ISO certificate given |

---

## TOPIC 4 — Requirements Engineering Process
`Frequency: 3/4 years` `Tier A`

---

### What is Requirements Engineering?

> Requirements Engineering is the process of defining, documenting, and maintaining requirements in the engineering design process.

It ensures that the right system is built — one that meets user needs.

---

### Requirements Engineering Process — 5 Steps

```
1. ELICITATION
      ↓
2. ANALYSIS
      ↓
3. DOCUMENTATION (SRS)
      ↓
4. REVIEW & VALIDATION
      ↓
5. MANAGEMENT
```

**1. Elicitation (Requirements Gathering)**
- Techniques: Interviews, questionnaires, observation, brainstorming, prototyping, use cases
- Goal: Understand what stakeholders need

**2. Analysis**
- Resolve conflicts between requirements
- Identify incomplete, ambiguous, or inconsistent requirements
- Classify: Functional vs Non-functional requirements

**3. Documentation**
- Write the SRS (Software Requirements Specification)
- Use IEEE standard format
- Must be: Complete, Consistent, Unambiguous, Traceable

**4. Review & Validation**
- Verify: Are requirements correct? (Verification)
- Validate: Are we building the right thing? (Validation)
- Techniques: Reviews, walkthroughs, inspections

**5. Management**
- Handle changes to requirements over time
- Version control of requirements documents
- Impact analysis when requirements change

---

### Functional vs Non-Functional Requirements

| Functional | Non-Functional |
|-----------|----------------|
| What system should DO | How system should PERFORM |
| User login feature | Response time < 2 seconds |
| Generate report | System available 99.9% uptime |
| Search books | Handle 1000 concurrent users |

---

### Feasibility Study (asked in 2023-24)

Before starting development, check:

1. **Technical feasibility** — can we build it with current technology?
2. **Economic feasibility** — is the cost justified by benefits?
3. **Operational feasibility** — will users actually use it?
4. **Legal feasibility** — are there legal issues?
5. **Schedule feasibility** — can we deliver on time?

---

## TOPIC 14 — DFD (Data Flow Diagram)
`Frequency: 2/4 years` `Tier B`

---

### DFD — What is it?

> A Data Flow Diagram (DFD) is a graphical representation of the "flow of data" through an information system. It shows how data moves from input to output.

---

### DFD Symbols

| Symbol | Shape | Meaning |
|--------|-------|---------|
| External Entity | Rectangle | Source or destination of data (outside system) |
| Process | Circle / Rounded rectangle | Transforms input to output |
| Data Store | Open rectangle / parallel lines | Where data is stored |
| Data Flow | Arrow | Movement of data |

---

### DFD Levels

**Level 0 (Context Diagram):**
- System as a single process (black box)
- Shows only external entities and data flows
- No internal details

**Level 1 DFD:**
- Main system broken into major sub-processes
- Shows major data stores
- Typically 3-7 processes

**Level 2 DFD:**
- Each Level 1 process further decomposed
- More detail about internal workings

---

### Example — Library Management System DFD

**Level 0 (Context):**
```
[User] → (Login request) → [Library System] → (Books list) → [User]
[Librarian] → (Reports request) → [Library System] → (Reports) → [Librarian]
```

**Level 1 processes:**
1. Authenticate User
2. Issue/Return Books
3. Generate Reports
4. Maintain Database

**Exam tip:** Jab bhi DFD banana ho — pehle Level 0 banao (simple), fir Level 1. External entities ko rectangle mein, processes ko circle mein, data stores ko lines ke beech mein.

---

## TOPIC 15 — SRS Document + IEEE Format
`Frequency: 2/4 years` `Tier B`

---

### SRS — What is it?

> SRS (Software Requirements Specification) is a complete description of the behavior of the software to be developed. It includes functional and non-functional requirements.

**Purpose of SRS:**
1. Agreement between client and developer
2. Reduces development effort
3. Baseline for validation and verification
4. Basis for cost estimation

---

### Characteristics of a Good SRS

- **Correct** — reflects actual user needs
- **Unambiguous** — only one interpretation possible
- **Complete** — all requirements covered
- **Consistent** — no contradictions
- **Ranked** — requirements prioritized
- **Verifiable** — can be tested
- **Modifiable** — can be changed easily
- **Traceable** — each requirement has an origin

---

### IEEE Standard SRS Format

```
1. Introduction
   1.1 Purpose
   1.2 Scope
   1.3 Definitions, Acronyms, Abbreviations
   1.4 References
   1.5 Overview

2. Overall Description
   2.1 Product Perspective
   2.2 Product Functions
   2.3 User Characteristics
   2.4 Constraints
   2.5 Assumptions and Dependencies

3. Specific Requirements
   3.1 External Interface Requirements
       3.1.1 User Interfaces
       3.1.2 Hardware Interfaces
       3.1.3 Software Interfaces
   3.2 Functional Requirements
   3.3 Non-functional Requirements
   3.4 Performance Requirements

4. Appendices
```

---

## Quick Revision — Unit 2

| Topic | Key Points |
|-------|-----------|
| CMM Level 1 | Initial — chaotic, fire-fighting |
| CMM Level 3 | Defined — standard process exists |
| CMM Level 5 | Optimizing — continuous improvement |
| ISO 9000 vs CMM | ISO = certification, CMM = maturity levels |
| Requirements Engineering | 5 steps: Elicit → Analyze → Document → Validate → Manage |
| DFD Level 0 | Context diagram — system as black box |
| SRS good properties | Correct, unambiguous, complete, consistent |

---

## Exam Answer Tips — Unit 2

- **CMM levels question** → draw a pyramid with 5 levels, describe each. Without pyramid diagram marks cut hote hain.
- **ISO vs CMM comparison** → table format mein likho. Examiner tables ko prefer karta hai comparison questions mein.
- **DFD question** → Level 0 pehle banao, fir Level 1. Symbols correct hone chahiye.
- **Requirements Engineering** → flowchart/diagram banao 5 steps ka — marks milte hain.
