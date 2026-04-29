# Unit 5 — Software Maintenance & Project Management
> BCS601 Software Engineering | Tier A: Topics 9, 10, 11 | Tier B: Topic 21

---

## TOPIC 9 — Types of Software Maintenance
`Frequency: 4/4 years` `Tier A` ← **Sabse zyada repeated topic of Unit 5**

---

### Why is Software Maintenance Required?

> Software Maintenance is the process of modifying a software product after delivery to correct faults, improve performance, or adapt it to a changed environment.

**Software maintenance is inevitable because:**
1. Environment changes (new OS, hardware, regulations)
2. User requirements change over time
3. Bugs discovered after deployment
4. Performance needs improvement
5. Business rules and processes evolve

---

### 4 Categories of Software Maintenance

**1. Corrective Maintenance**
- **What:** Fixing bugs and errors found after delivery
- **Why:** Software has defects — some found only in production
- **Example:** Fixing a login crash, resolving payment calculation error
- **Triggered by:** Bug reports from users

**2. Adaptive Maintenance**
- **What:** Modifying software to work in a changed environment
- **Why:** OS updates, new hardware, changed business rules
- **Example:** Updating software to work on Windows 11, migrating to cloud
- **Triggered by:** External environment changes

**3. Perfective Maintenance**
- **What:** Improving performance or adding new features requested by users
- **Why:** User needs evolve, competition requires better features
- **Example:** Adding dark mode, improving search speed, new report format
- **Triggered by:** User enhancement requests

**4. Preventive Maintenance**
- **What:** Making changes to prevent future problems
- **Why:** Proactive quality improvement, reduce technical debt
- **Example:** Refactoring messy code, updating outdated libraries
- **Triggered by:** Developer initiative to improve code quality

---

### Maintenance Cost Distribution (Important for exam)

| Type | Approx % of Maintenance Cost |
|------|------------------------------|
| Corrective | 20% |
| Adaptive | 25% |
| **Perfective** | **50%** (highest!) |
| Preventive | 5% |

**Exam tip:** Perfective maintenance consumes the most cost — 50%. This surprises people but it's because feature enhancements are very common.

---

### Maintenance vs Development Cost

> On average, maintenance cost is 2–4 times the development cost over a software's lifetime.

---

## TOPIC 10 — Software Re-engineering + Reverse Engineering
`Frequency: 4/4 years` `Tier A`

---

### What is Software Re-engineering?

> Software re-engineering is the process of examining and altering an existing software system to reconstitute it in a new form, and the subsequent implementation of the new form.

**Why needed:**
- Legacy software that is hard to maintain
- Outdated technology
- Poor documentation
- High maintenance cost

---

### Re-engineering Process Model (General Model)

```
Inventory Analysis
       ↓
Document Restructuring
       ↓
Reverse Engineering
       ↓
Code Restructuring
       ↓
Data Restructuring
       ↓
Forward Engineering
```

**Explanation of each step:**

1. **Inventory Analysis** — Identify which software should be re-engineered (based on business value, age, problems)
2. **Document Restructuring** — Update or create documentation for existing system
3. **Reverse Engineering** — Analyze existing code to understand design and requirements
4. **Code Restructuring** — Rewrite/refactor code without changing external behavior (no new features)
5. **Data Restructuring** — Clean up and restructure databases, file formats
6. **Forward Engineering** — Use extracted information to rebuild system with modern architecture

---

### What is Reverse Engineering?

> Reverse engineering is the process of analyzing a software system to identify its components, their interrelationships, and create representations of the system at a higher level of abstraction.

**Simple definition:** Reading existing code to understand WHAT it does and HOW it was designed — without original design documents.

**Levels of abstraction in reverse engineering:**
- Implementation level → Design level → Requirements level

---

### Re-engineering vs Reverse Engineering

| Parameter | Re-engineering | Reverse Engineering |
|-----------|---------------|---------------------|
| Goal | Rebuild/improve the system | Understand existing system |
| Output | New, improved software | Documentation, design models |
| Change | System is changed | System is NOT changed |
| Scope | Complete process | Just analysis phase |
| Includes | Reverse engineering as a step | Standalone process |
| Forward engineering | Yes (rebuilds) | No |

---

## TOPIC 11 — COCOMO Model
`Frequency: 3/4 years` `Tier A`

---

### What is COCOMO?

**COCOMO** = Constructive Cost Model
Developed by **Barry Boehm** in 1981.

> COCOMO is an algorithmic software cost estimation model that uses a regression formula with parameters derived from historical project data to estimate the effort, time, and cost required to develop software.

**Primary input:** Size of software in KLOC (Kilo Lines of Code)
**Outputs:** Effort (person-months), Duration (months), Team size

---

### 3 Project Types in COCOMO

| Type | Description | Example |
|------|-------------|---------|
| **Organic** | Small team, well-understood problem, flexible requirements | Payroll system, small utility |
| **Semi-detached** | Medium team, mixed experience, some rigid requirements | Database management system |
| **Embedded** | Strict hardware/software constraints, complex requirements | Air traffic control, medical devices |

---

### Basic COCOMO Formulas

```
Effort (E) = a × (KLOC)^b   [person-months]
Duration (D) = c × (E)^d    [months]
Team size = E / D            [persons]
```

**Constants (must memorize):**

| Mode | a | b | c | d |
|------|---|---|---|---|
| Organic | 2.4 | 1.05 | 2.5 | 0.38 |
| Semi-detached | 3.0 | 1.12 | 2.5 | 0.35 |
| Embedded | 3.6 | 1.20 | 2.5 | 0.32 |

---

### Person-Month (PM) — Definition

> A Person-Month (PM) is a unit of measurement representing the work done by one person in one month. It is used to estimate effort in software projects.

Example: If a project needs 12 PM effort, it could mean:
- 1 person × 12 months, OR
- 2 people × 6 months, OR
- 12 people × 1 month

---

### COCOMO Levels

**1. Basic COCOMO:**
- Simple formula using only KLOC
- Rough estimate, quick calculation

**2. Intermediate COCOMO:**
- Uses KLOC + 15 cost driver attributes
- Cost drivers: Product, Hardware, Personnel, Project attributes
- More accurate than basic

**3. Detailed COCOMO:**
- Applies cost drivers at each phase (design, coding, testing)
- Most accurate, most complex

---

### Solved Example

**Given:** Software = 50 KLOC, Organic mode
```
E = 2.4 × (50)^1.05
  = 2.4 × 58.84
  = 141.2 person-months

D = 2.5 × (141.2)^0.38
  = 2.5 × 14.06
  = 35.1 months

Team size = 141.2 / 35.1 ≈ 4 persons
```

---

## TOPIC 21 — Risk Management
`Frequency: 2/4 years` `Tier B`

---

### What is Software Risk?

> A software risk is any condition or event that may cause problems in the project — affecting schedule, cost, or quality.

**Risk = Probability × Impact**

---

### Types of Risks

**1. Project Risks:**
- Threaten the project plan (schedule, budget, resources)
- Example: Key developer quits, budget cuts, requirement changes

**2. Technical Risks:**
- Threaten quality or timeliness of software
- Example: Unproven technology, complex algorithms, integration issues

**3. Business Risks:**
- Threaten viability of software or organization
- Example: Market changes, losing to competition, management changes

---

### Project Risk vs Technical Risk

| Parameter | Project Risk | Technical Risk |
|-----------|-------------|----------------|
| Affects | Schedule, budget, resources | Quality, functionality |
| Source | Management, process issues | Technology, design issues |
| Example | Developer leaves project | Algorithm too complex |
| Who identifies | Project manager | Technical lead |
| Resolution | Re-planning, hiring | Prototyping, research |

---

### Risk Management Process

```
1. Risk Identification
       ↓
2. Risk Analysis (Probability × Impact)
       ↓
3. Risk Planning (mitigation strategies)
       ↓
4. Risk Monitoring (track risks throughout project)
```

**Risk Mitigation Strategies:**
- **Avoid** — change plan to eliminate risk
- **Transfer** — shift risk to third party (insurance, outsource)
- **Accept** — acknowledge risk, have contingency plan
- **Reduce** — take actions to lower probability or impact

---

## Quick Revision — Unit 5

| Topic | Key Point |
|-------|----------|
| Corrective maintenance | Fix bugs after delivery (20% cost) |
| Adaptive maintenance | Adapt to new environment (25% cost) |
| Perfective maintenance | Add features/improve performance (50% cost) |
| Preventive maintenance | Prevent future problems (5% cost) |
| Re-engineering | Rebuild software using reverse + forward engineering |
| Reverse engineering | Analyze existing code to extract design/requirements |
| COCOMO | E = a × KLOC^b, D = c × E^d |
| Organic mode | a=2.4, b=1.05 (small, flexible projects) |
| Person-Month | Effort unit = 1 person working 1 month |
| Risk | Probability × Impact |

---

## Exam Answer Tips — Unit 5

- **Maintenance types question** → Write all 4 types with definition + example + trigger. Add the cost distribution table at end.
- **Re-engineering model** → Draw the 6-step diagram (Inventory → Document → Reverse → Code → Data → Forward). Ye diagram marks deta hai.
- **Re-engineering vs Reverse engineering** → Table format mein likho. Clear distinction needed.
- **COCOMO** → Formula likhna mandatory. Constants table (a, b, c, d for all 3 modes) likhna. Ek solved numerical bhi karo.
- **Risk management** → 4-step process + types of risks + project vs technical risk table.
- **"Software maintenance is inevitable"** (asked 2024-25) → 5 reasons: changing environment, new user needs, bugs found post-delivery, performance needs, business rule changes.
