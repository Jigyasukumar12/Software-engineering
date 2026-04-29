# Unit 3 — Software Design & Metrics
> BCS601 Software Engineering | Tier A: Topics 5, 6 | Tier B: Topics 16, 17, 18

---

## TOPIC 5 — Coupling & Cohesion
`Frequency: 4/4 years` `Tier A` ← **Har saal aaya — kisi bhi form mein**

---

### Basic Concept

> **Goal of good software design:** LOW COUPLING + HIGH COHESION

**Cohesion** = How closely related are the elements WITHIN a single module.
**Coupling** = How dependent are DIFFERENT modules on each other.

Simple analogy:
- Cohesion = ek team ke andar kitna coordination hai (high = good)
- Coupling = alag alag teams kitni depend karti hain ek doosre pe (low = good)

---

### Why "Low Coupling, High Cohesion" is Better?

| Property | Benefit |
|---------|---------|
| High Cohesion | Module does ONE thing well → easy to understand, test, maintain |
| Low Coupling | Modules are independent → change in one doesn't break others |
| Together | Software is modular, reusable, maintainable, and testable |

---

### Types of Cohesion (Worst to Best — 7 types)

```
WORST → Coincidental
        Logical
        Temporal
        Procedural
        Communicational
        Sequential
BEST  → Functional
```

| Type | Description | Example |
|------|-------------|---------|
| **Coincidental** (worst) | Elements grouped randomly, no relation | Random utility functions dumped together |
| **Logical** | Elements perform similar logical category of functions | All input routines in one module |
| **Temporal** | Elements execute at the same time | Startup initialization functions |
| **Procedural** | Elements follow a specific sequence of execution | Steps of a procedure |
| **Communicational** | Elements operate on the same data | Functions that read and write same file |
| **Sequential** | Output of one element is input of next | Pipeline processing |
| **Functional** (best) | All elements contribute to ONE specific task | `calculateInterest()` — only calculates interest |

**Exam tip:** Functional cohesion = best. Coincidental = worst. Examiner often asks to rank them.

---

### Types of Coupling (Worst to Best — 7 types)

```
WORST → Content Coupling
        Common Coupling
        External Coupling
        Control Coupling
        Stamp Coupling
        Data Coupling
BEST  → No Coupling (ideal, rarely achievable)
```

| Type | Description | Example |
|------|-------------|---------|
| **Content** (worst) | One module directly modifies another's internal data | Module A changes Module B's local variable |
| **Common** | Modules share global data | Two modules read/write same global variable |
| **External** | Modules share externally imposed format or protocol | Both modules depend on external file format |
| **Control** | One module controls flow of another by passing flag | Passing a boolean flag to decide what function does |
| **Stamp** | Modules share composite data structure (only part used) | Passing whole record when only name needed |
| **Data** | Modules share only necessary data through parameters | Passing only required values |
| **No coupling** (best) | Modules are completely independent | — |

---

### Functional Independence

> A module is functionally independent if it performs a single function with little interaction with other modules.

Measured by:
- **Cohesion** (should be high)
- **Coupling** (should be low)

High functional independence = better modularization = easier maintenance.

---

## TOPIC 6 — Cyclomatic Complexity + CFG
`Frequency: 3/4 years` `Tier A`

---

### What is Cyclomatic Complexity?

> Cyclomatic Complexity (V(G)) is a software metric that measures the number of linearly independent paths through a program's source code.

Introduced by **Thomas McCabe**.

**Higher complexity = harder to test and maintain.**

**Recommended:** V(G) ≤ 10 for a module.

---

### Control Flow Graph (CFG)

A CFG is a directed graph where:
- **Nodes** = statements or groups of statements
- **Edges** = flow of control between statements
- **Predicate nodes** = nodes with more than one outgoing edge (if, while, for)

---

### 3 Methods to Calculate Cyclomatic Complexity

**Method 1 (Graph formula):**
```
V(G) = E - N + 2P
Where:
  E = number of edges
  N = number of nodes
  P = number of connected components (usually 1)
```

**Method 2 (Predicate nodes):**
```
V(G) = P + 1
Where:
  P = number of predicate nodes (decision points)
```

**Method 3 (Regions):**
```
V(G) = number of enclosed regions + 1
(Count closed regions in the CFG diagram)
```

---

### Solved Example — from 2022-23 PYQ

**Code:**
```
IF A = 100 THEN
  IF B > C THEN
    A = B
  ELSE
    A = C
  ENDIF
ENDIF
PRINT A
```

**CFG Nodes:**
```
Node 1: IF A = 100
Node 2: IF B > C
Node 3: A = B
Node 4: A = C
Node 5: PRINT A
```

**Edges:** 1→2, 1→5, 2→3, 2→4, 3→5, 4→5 → **E = 6**
**Nodes:** N = 5
**Predicate nodes:** Node 1, Node 2 → **P = 2**

**V(G) = E - N + 2 = 6 - 5 + 2 = 3**
**V(G) = P + 1 = 2 + 1 = 3** ✓

**Independent paths:**
- Path 1: 1 → 5 (A ≠ 100)
- Path 2: 1 → 2 → 3 → 5 (A=100, B>C)
- Path 3: 1 → 2 → 4 → 5 (A=100, B≤C)

---

### GCD Example — from 2024-25 PYQ

**Code:**
```c
int compute_gcd(x, y) {
  while (x != y) {
    if (x > y)
      x = x - y;
    else
      y = y - x;
  }
  return x;
}
```

**Predicate nodes:** while (x!=y), if (x>y) → **P = 2**
**V(G) = P + 1 = 3**

**Independent paths:**
- Path 1: x == y initially → skip while → return x
- Path 2: x > y → x = x - y → loop back
- Path 3: x < y → y = y - x → loop back

---

## TOPIC 16 — Function Point (Albretch Method)
`Frequency: 2/4 years` `Tier B`

---

### What is Function Point?

> Function Point (FP) is a unit of measurement to express the amount of business functionality an information system provides. It measures software size from user's perspective.

Developed by **Allan Albretch** at IBM.

---

### Function Point Calculation Steps

**Step 1: Count UFP (Unadjusted Function Points)**

Count these 5 components:

| Component | Simple | Average | Complex |
|-----------|--------|---------|---------|
| External Inputs (EI) | 3 | 4 | 6 |
| External Outputs (EO) | 4 | 5 | 7 |
| External Inquiries (EQ) | 3 | 4 | 6 |
| Internal Logical Files (ILF) | 7 | 10 | 15 |
| External Interface Files (EIF) | 5 | 7 | 10 |

**UFP = Sum of (count × weight) for all components**

**Step 2: Calculate CAF (Complexity Adjustment Factor)**

14 general system characteristics (GSC), each rated 0–5:
- Data communications, Distributed functions, Performance, etc.

```
TDI = Total Degree of Influence = sum of all 14 GSC ratings
CAF = 0.65 + (0.01 × TDI)
```

TDI range: 0 to 70
CAF range: 0.65 to 1.35 (i.e., ±35% adjustment — this is what exam asks to prove)

**Step 3: Calculate FP**
```
FP = UFP × CAF
```

**Why ±35%?**
- Min CAF = 0.65 + (0.01 × 0) = **0.65** → reduces UFP by 35%
- Max CAF = 0.65 + (0.01 × 70) = **1.35** → increases UFP by 35%
- Hence CAF adjusts UFP by ±35% ✓

---

## TOPIC 17 — Top-Down vs Bottom-Up Design
`Frequency: 2/4 years` `Tier B`

---

### Top-Down Design

- Start from the **highest-level module** (main function)
- Break it down into sub-modules
- Continue decomposing until lowest-level modules reached
- **Stubs** used for testing (dummy lower modules)

**Advantages:**
1. Easy to understand overall system structure
2. Early testing of high-level logic
3. Good for large, complex systems
4. Integration is easier

**Disadvantages:**
1. Low-level details ignored initially
2. Stubs needed → extra work
3. Difficult to identify reusable components early

---

### Bottom-Up Design

- Start from **lowest-level modules** (utility functions)
- Combine them to build higher-level modules
- Continue until complete system built
- **Drivers** used for testing (dummy calling modules)

**Advantages:**
1. Reusable components identified early
2. Low-level modules fully tested before integration
3. Parallel development possible

**Disadvantages:**
1. High-level design may suffer
2. Integration problems appear late
3. System overview not clear initially

---

### Comparison Table

| Parameter | Top-Down | Bottom-Up |
|-----------|---------|-----------|
| Start from | Highest level module | Lowest level module |
| Testing aid | Stubs (dummy lower modules) | Drivers (dummy upper modules) |
| System view | Clear from beginning | Unclear initially |
| Reusability | Hard to identify early | Easy to identify |
| Best for | New systems, unclear low-level details | Systems with reusable components |

---

## TOPIC 18 — LOC (Line of Code)
`Frequency: 2/4 years` `Tier B`

---

### What is LOC?

> LOC is the simplest size-oriented measure of software — it counts the number of lines of source code in a program.

Used for: Cost estimation, productivity measurement, quality metrics.

---

### Advantages of LOC

1. Simple to understand and measure
2. Universally applicable to any language
3. Basis for many cost estimation models (like COCOMO)

### Disadvantages / Drawbacks of LOC

1. **Language dependent** — 100 lines in Assembly ≠ 100 lines in Python
2. **Penalizes good programmers** — efficient code has fewer lines
3. **Doesn't measure functionality** — a complex algorithm in 10 lines vs simple code in 100 lines
4. **Difficult to estimate early** — can't measure before coding
5. **Blank lines and comments** — whether to count or not is ambiguous
6. **Not suitable for comparison** — across different projects or teams

---

## Quick Revision — Unit 3

| Topic | Must Remember |
|-------|--------------|
| Cohesion types | Coincidental (worst) → Functional (best) |
| Coupling types | Content (worst) → Data (best) |
| Low coupling, High cohesion | Better maintainability and testability |
| Cyclomatic Complexity | V(G) = E-N+2P = P+1 = regions+1 |
| V(G) ≤ 10 | Good module complexity |
| Function Point | UFP × CAF, CAF range = 0.65 to 1.35 |
| Top-Down testing | Uses stubs |
| Bottom-Up testing | Uses drivers |
| LOC drawback | Language dependent, penalizes good coders |

---

## Exam Answer Tips — Unit 3

- **Coupling & Cohesion question** → List all 7 types of each, then explain with example, then write why low coupling high cohesion is better. 7-mark mein sab aana chahiye.
- **Cyclomatic Complexity** → Draw CFG first, then calculate using all 3 methods, then list independent paths. Agar ek method galat ho bhi, baaki se marks milenge.
- **Function Point** → CAF = 0.65 + 0.01×TDI formula yaad rakho. ±35% proof likhna mat bhoolo.
- **Top-Down vs Bottom-Up** → Table format + stubs/drivers ka mention must hai.
