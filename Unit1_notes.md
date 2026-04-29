# Unit 1 — Introduction & SDLC Models
> BCS601 Software Engineering | Tier A: Topics 1, 2 | Tier B: Topics 12, 13

---

## TOPIC 1 — Software Characteristics + Software Crisis
`Frequency: 4/4 years` `Tier A`

---

### What is Software?

Software = Programs + Documentation + Data

**Exam definition:**
> Software is a collection of executable programs, configuration files, system documentation, and user documentation that together provide a required system capability.

---

### Software Characteristics (Memorize these 8)

| # | Characteristic | One-line explanation |
|---|---------------|----------------------|
| 1 | **Developed, not manufactured** | Software is engineered — no physical production process |
| 2 | **Does not wear out** | No physical degradation; bugs are design flaws, not wear |
| 3 | **Custom built** | Mostly built for specific requirements, not assembled from parts |
| 4 | **Complex** | High logical complexity compared to other engineering products |
| 5 | **Flexible** | Can be modified easily (unlike hardware) |
| 6 | **Conformity** | Must conform to human institutions and systems |
| 7 | **Changeability** | Software is continuously under pressure to change |
| 8 | **Invisibility** | Software has no physical form — hard to visualize |

**Exam tip:** "Software does not wear out" wala statement almost har saal poochha gaya hai. Explanation: Hardware degrades due to physical stress. Software has no moving parts — it either works or it doesn't. Failure rate is high initially (bugs), then stable, then rises again as software becomes obsolete — not because it "wears out."

---

### Software Crisis

**Definition:**
> Software crisis refers to a set of problems encountered in the development of software — cost overruns, schedule delays, poor quality, and failure to meet requirements — that became apparent in the late 1960s.

**Reasons for Software Crisis:**

1. Increasing complexity of software systems
2. Lack of proper development methods and tools
3. Poor project management and estimation
4. Inadequate testing before delivery
5. Rapidly changing user requirements
6. No standard development process followed
7. Communication gap between developers and clients

**Impact:**
- Projects delivered late and over budget
- Software that didn't meet user needs
- High maintenance costs
- Unreliable and error-prone systems

**Solution → Software Engineering:**
Applying systematic, disciplined, and measurable approaches to software development.

---

### Software Components (3 types)

1. **System Software** — OS, compilers, drivers (e.g., Windows, Linux)
2. **Application Software** — end-user applications (e.g., MS Word, Chrome)
3. **Engineering/Scientific Software** — simulation, CAD tools
4. **Embedded Software** — software in devices (washing machine, car ECU)
5. **Product-line Software** — reusable software for specific market (e.g., ERP)
6. **Web Applications** — browser-based apps
7. **AI Software** — expert systems, ML models

---

## TOPIC 2 — Spiral Model
`Frequency: 3/4 years` `Tier A`

---

### Spiral Model — Overview

Proposed by **Barry Boehm (1988)**. Combines iterative development with systematic risk management.

**Key idea:** Development happens in spirals (loops). Each loop = one phase. Risk is evaluated at every loop before moving forward.

---

### Spiral Model — 4 Phases (per loop)

```
Each spiral has 4 quadrants:

1. PLANNING        → Determine objectives, alternatives, constraints
2. RISK ANALYSIS   → Evaluate alternatives, identify & resolve risks
3. ENGINEERING     → Develop and test (actual coding/prototyping)
4. EVALUATION      → Customer evaluates, feedback taken, next loop planned
```

**Diagram description (draw this in exam):**
- Draw a spiral starting from center going outward
- Each loop divided into 4 quadrants (label them)
- Label loops: Loop 1 = Concept, Loop 2 = Requirements, Loop 3 = Design, Loop 4 = Implementation

---

### Spiral Model — Advantages

1. Risk handling is built-in at every phase
2. Good for large, complex, high-risk projects
3. Customer sees working software early (prototypes)
4. Changes can be incorporated easily
5. Works well when requirements are unclear initially

### Spiral Model — Disadvantages

1. Complex to manage
2. Risk assessment requires expertise
3. Costly — not suitable for small projects
4. No fixed end — can go on indefinitely
5. Documentation can be heavy

---

### When to use Spiral Model?

- Large, mission-critical projects (NASA, defense)
- Projects where requirements change frequently
- High-risk projects where failure is not acceptable

---

### Criteria for Selection of SDLC Model (asked in 2024-25)

| Model | Use when |
|-------|---------|
| Waterfall | Requirements are clear and fixed |
| Prototype | Requirements unclear, user feedback needed early |
| Spiral | High risk, large project, requirements may change |
| Iterative | Large project, deliver parts incrementally |

---

## TOPIC 12 — Prototype Model
`Frequency: 2/4 years` `Tier B`

---

### Prototype Model — Overview

**Key idea:** Build a working model (prototype) of the system first → show to client → get feedback → refine → repeat until client approves → then build actual system.

---

### Prototype Model — Phases

```
1. Requirements gathering (initial, incomplete)
2. Quick design (focus on visible parts — UI, I/O)
3. Build prototype
4. Customer evaluates prototype
5. Refine prototype (based on feedback)
6. Repeat steps 4-5 until approved
7. Engineer actual product
```

---

### Advantages over Conventional (Waterfall) Model

| Waterfall | Prototype |
|-----------|-----------|
| Requirements must be complete upfront | Works with incomplete requirements |
| Client sees product only at end | Client sees working model early |
| Changes are expensive | Changes are easy and expected |
| High risk of final product mismatch | Risk of mismatch is low |

### Disadvantages

1. Client may think prototype = final product
2. Developer may make poor implementation choices in prototype
3. Prototype may be kept as-is (poorly engineered)
4. Scope creep — client keeps adding features

---

## TOPIC 13 — Software Quality Attributes
`Frequency: 2/4 years` `Tier B`

---

### Software Quality — Definition

> Software quality is the degree to which software possesses a desired combination of attributes that fulfill stated or implied needs.

---

### McCall's Quality Factors (Quality Triangle)

McCall organized quality factors into 3 categories (the triangle):

```
         PRODUCT REVISION
        (Can I change it?)
              /\
             /  \
            /    \
           /------\
PRODUCT   /        \ PRODUCT
OPERATION \        / TRANSITION
(Does it  \      / (Can I move it
  work?)   \    /   elsewhere?)
            \  /
             \/
```

**Product Operation factors:**
- Correctness — does it do what's required?
- Reliability — does it perform consistently?
- Efficiency — does it use resources well?
- Integrity — is it secure?
- Usability — is it easy to use?

**Product Revision factors:**
- Maintainability — can it be fixed easily?
- Flexibility — can it be changed?
- Testability — can it be tested easily?

**Product Transition factors:**
- Portability — can it run on different environments?
- Reusability — can parts be reused?
- Interoperability — can it work with other systems?

---

### Software Quality Attributes (General list — for Section A)

1. **Correctness** — behaves as specified
2. **Reliability** — performs consistently under defined conditions
3. **Efficiency** — optimal use of CPU, memory, time
4. **Usability** — easy to learn and use
5. **Maintainability** — easy to fix and update
6. **Portability** — works across platforms
7. **Testability** — easy to test

---

## Quick Revision — Unit 1

| Topic | Key Point to Remember |
|-------|----------------------|
| Software characteristics | Does not wear out, developed not manufactured |
| Software crisis | Late 1960s, cost overruns, bad quality |
| Spiral model | Boehm 1988, 4 quadrants, risk at every loop |
| Prototype model | Build → Show → Feedback → Refine |
| McCall's factors | 3 categories: Operation, Revision, Transition |

---

## Exam Answer Tips — Unit 1

- **2-mark questions:** Definition + 2-3 bullet points. No diagrams needed.
- **7-mark questions:** Definition → Diagram (if applicable) → Explain phases/points → Advantages → Disadvantages. Aim for 1.5–2 pages.
- Spiral model question mein **diagram banana mandatory hai** — without diagram full marks nahi milenge.
- Software characteristics mein "does not wear out" ko **elaborate** karo — examiner is par marks deta hai.
