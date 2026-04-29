# Unit 4 — Software Testing
> BCS601 Software Engineering | Tier A: Topics 7, 8 | Tier B: Topics 19, 20

---

## TOPIC 7 — BVA + Equivalence Partitioning
`Frequency: 4/4 years` `Tier A` ← **Har saal ek program deke test cases banana padta hai**

---

### Equivalence Partitioning (EP)

> Equivalence Partitioning is a black box testing technique that divides input data into partitions (classes) such that test cases can be designed for each class. The assumption is that all values in one class behave the same way.

**Key idea:** Agar ek partition mein ek value se test pass ho, toh baaki values se bhi pass hoga. Toh ek partition se sirf EK test case banana enough hai.

**Types of partitions:**
1. **Valid equivalence class** — inputs that should be accepted
2. **Invalid equivalence class** — inputs that should be rejected

---

### Boundary Value Analysis (BVA)

> BVA is a testing technique that focuses on the boundaries of equivalence classes, because errors tend to cluster at the boundaries of input domains.

**Key idea:** Boundaries pe bugs zyada hote hain. Toh boundaries pe test karo.

**For a range [min, max], BVA test values:**
```
min - 1   (just below lower boundary) → invalid
min       (lower boundary) → valid
min + 1   (just above lower boundary) → valid
nominal   (middle value) → valid
max - 1   (just below upper boundary) → valid
max       (upper boundary) → valid
max + 1   (just above upper boundary) → invalid
```

---

### Solved Example — Quadratic Equation (from 2024-25 PYQ)

**Problem:** Input = (a, b, c) where each ∈ [0, 10]. Output = Not quadratic / Real / Imaginary / Equal roots.

**Step 1: Equivalence Classes**

| Class | Condition | Valid/Invalid |
|-------|-----------|--------------|
| EC1 | 0 ≤ a ≤ 10 | Valid |
| EC2 | a < 0 | Invalid |
| EC3 | a > 10 | Invalid |
| EC4 | 0 ≤ b ≤ 10 | Valid |
| EC5 | b < 0 | Invalid |
| EC6 | b > 10 | Invalid |
| EC7 | 0 ≤ c ≤ 10 | Valid |
| EC8 | c < 0 | Invalid |
| EC9 | c > 10 | Invalid |

**EP Test Cases:**

| Test Case | a | b | c | Expected Output |
|-----------|---|---|---|----------------|
| TC1 | 1 | 2 | 3 | Real roots (b²-4ac=4-12 <0 → Imaginary) |
| TC2 | -1 | 2 | 3 | Invalid input |
| TC3 | 11 | 2 | 3 | Invalid input |
| TC4 | 1 | -1 | 3 | Invalid input |
| TC5 | 1 | 2 | -1 | Invalid input |
| TC6 | 0 | 2 | 3 | Not a quadratic equation (a=0) |
| TC7 | 1 | 2 | 1 | Equal roots (b²-4ac=0) |

**Step 2: BVA Test Cases (for variable a, range [0,10])**

| Test Case | a | b | c | Expected |
|-----------|---|---|---|---------|
| TC-B1 | -1 | 5 | 5 | Invalid |
| TC-B2 | 0 | 5 | 5 | Not quadratic |
| TC-B3 | 1 | 5 | 5 | Valid input |
| TC-B4 | 5 | 5 | 5 | Valid input (nominal) |
| TC-B5 | 9 | 5 | 5 | Valid input |
| TC-B6 | 10 | 5 | 5 | Valid input |
| TC-B7 | 11 | 5 | 5 | Invalid |

*(Same pattern repeat for b and c)*

---

### Solved Example — Prime Number (from 2023-24 PYQ)

**Problem:** Input = integer in range [1, 100]. Determine if prime or not.

**Equivalence Classes:**
- Valid: 1 ≤ n ≤ 100
- Invalid: n < 1, n > 100, non-integer

**BVA Test Cases:**

| TC | Input | Expected |
|----|-------|---------|
| 1 | 0 | Invalid |
| 2 | 1 | Not prime |
| 3 | 2 | Prime |
| 4 | 50 | Not prime (nominal) |
| 5 | 99 | Not prime |
| 6 | 100 | Not prime |
| 7 | 101 | Invalid |

---

## TOPIC 8 — Black Box vs White Box Testing
`Frequency: 3/4 years` `Tier A`

---

### Black Box Testing (Functional Testing)

> Black box testing is a testing method where the tester has NO knowledge of the internal structure or code of the software. Tests are based on requirements and specifications only.

**Tester's view:** Input → [??? System ???] → Output

**Techniques:**
- Equivalence Partitioning
- Boundary Value Analysis
- Decision Table Testing
- State Transition Testing
- Use Case Testing

**When used:** System testing, Acceptance testing

---

### White Box Testing (Structural Testing)

> White box testing is a testing method where the tester has FULL knowledge of the internal structure, code, and logic of the software. Tests are designed to cover code paths.

**Tester's view:** Complete source code visible

**Techniques:**
- Statement coverage
- Branch/Decision coverage
- Path coverage
- Cyclomatic Complexity-based testing
- Control Flow Graph (CFG) analysis

**When used:** Unit testing, Integration testing

---

### Black Box vs White Box — Comparison Table

| Parameter | Black Box | White Box |
|-----------|-----------|-----------|
| Knowledge of code | No | Yes |
| Also called | Functional testing | Structural testing |
| Focus | What system does | How system works |
| Test basis | Requirements/Specs | Source code/Design |
| Who does it | Tester (not developer) | Developer |
| Coverage | Functionality | Code paths |
| Techniques | BVA, EP, Decision tables | CFG, Statement coverage |
| Level | System, Acceptance | Unit, Integration |
| Finds | Functional defects | Logic errors, missing paths |

---

### Using Both Simultaneously

**Answer for "how to use both together":**

1. Use **black box** to identify all functional test cases from requirements
2. Use **white box** to analyze code paths and ensure adequate coverage
3. Black box finds WHAT is wrong; white box helps find WHERE it's wrong
4. Combined approach = better test coverage
5. Example: BVA identifies boundary test cases (black box); CFG ensures all branches are covered (white box)

---

## TOPIC 19 — Integration Testing
`Frequency: 2/4 years` `Tier B`

---

### What is Integration Testing?

> Integration testing is a phase of software testing in which individual software modules are combined and tested as a group to verify that they work correctly together.

**Purpose:** Detect interface defects between modules.

---

### Types of Integration Testing

**1. Big Bang Integration:**
- All modules integrated at once and tested together
- Simple but hard to isolate failures
- Not recommended for large systems

**2. Top-Down Integration:**
- Start from top-level (main) module
- Lower modules replaced by **stubs** (dummy modules)
- Stubs replaced one by one as real modules are ready
- Advantage: Main logic tested early
- Disadvantage: Stubs need to be written

**3. Bottom-Up Integration:**
- Start from lowest-level modules
- Upper modules replaced by **drivers** (dummy calling modules)
- Advantage: No stubs needed, real modules tested first
- Disadvantage: Main logic tested late

**4. Sandwich (Hybrid) Integration:**
- Combination of top-down and bottom-up
- Middle layer tested in both directions

---

### Stubs vs Drivers

| | Stub | Driver |
|--|------|--------|
| Used in | Top-down integration | Bottom-up integration |
| What it is | Dummy lower module | Dummy upper module |
| Purpose | Simulates called module | Simulates calling module |
| Direction | Downward | Upward |

---

## TOPIC 20 — Alpha, Beta & Regression Testing
`Frequency: 2/4 years` `Tier B`

---

### Alpha Testing

> Alpha testing is conducted by the development team or internal testers at the developer's site, before the product is released to external users.

- Done in a **controlled environment** (developer's lab)
- Simulated or real operational testing
- Developer observes and records bugs
- Happens before Beta testing

---

### Beta Testing

> Beta testing is conducted by actual end-users at their own sites, before the final product is released to the market.

- Done in **real environment** (user's computer/site)
- Developer NOT present — users report bugs
- Feedback used to fix final bugs
- Real-world usage conditions

---

### Alpha vs Beta — Comparison

| Parameter | Alpha Testing | Beta Testing |
|-----------|--------------|--------------|
| Who | Internal team/testers | External end-users |
| Where | Developer's site | User's site/real environment |
| Developer present | Yes | No |
| Environment | Controlled | Real |
| Stage | Before beta | Before release |
| Purpose | Find bugs early | Get real-world feedback |

---

### Regression Testing

> Regression testing is re-testing of software after modifications to ensure that changes haven't introduced new bugs or broken existing functionality.

**When done:**
- After bug fixes
- After adding new features
- After performance improvements
- After code refactoring

**Process:**
1. Identify modified modules
2. Select test cases from existing test suite
3. Re-run those test cases
4. Compare results with previous baseline
5. Report new failures (regressions)

**Test case selection strategies:**
- Retest all — exhaustive but time-consuming
- Select modified module tests — efficient
- Prioritization — run high-risk tests first

---

## Quick Revision — Unit 4

| Topic | Key Point |
|-------|----------|
| Equivalence Partitioning | Divide inputs into valid/invalid classes |
| BVA | Test at min-1, min, min+1, max-1, max, max+1 |
| Black Box | No code knowledge, functional testing |
| White Box | Full code knowledge, structural testing |
| Stubs | Dummy lower modules (top-down testing) |
| Drivers | Dummy upper modules (bottom-up testing) |
| Alpha testing | Internal, developer's site, controlled |
| Beta testing | External users, real environment |
| Regression | Re-test after changes to catch new bugs |

---

## Exam Answer Tips — Unit 4

- **BVA/EP question** → Always write test cases in a TABLE format — TC number, input values, expected output. Examiner gives marks for organized table.
- **Black box vs White box** → Table comparison + explain each with one technique example.
- **Integration testing** → Draw diagram showing top-down (stubs) and bottom-up (drivers). Label clearly.
- **BVA** → For every problem, handle: below min (invalid), min, min+1, nominal, max-1, max, above max (invalid) — ye saat values standard hain.
- **Exhaustive testing not possible** (asked in 2024-25) → Because: number of possible input combinations is infinite, can't test all paths in reasonable time, not cost-effective.
