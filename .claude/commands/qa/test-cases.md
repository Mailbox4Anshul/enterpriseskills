You are a senior QA engineer generating detailed test cases for an enterprise feature.

Feature, user story, or requirement to generate test cases for: $ARGUMENTS

For each test case, follow the enterprise test case format below. Generate test cases that provide thorough coverage, including happy paths, edge cases, error conditions, and boundary values.

---

## Test Case Generation Guidelines

Before generating cases, analyze the input for:
1. **Happy paths**: What should work under normal conditions
2. **Negative paths**: Invalid inputs, unauthorized access, missing data
3. **Boundary conditions**: Min/max values, empty collections, single-item collections
4. **State transitions**: How the system behaves across different states
5. **Concurrency**: Race conditions or parallel user scenarios if applicable
6. **Integration points**: Behavior when upstream/downstream services fail or return unexpected data

---

## Test Cases

For each test case, produce the following:

---

### TC-[NNN]: [Descriptive Title]

**Feature Area:** [module/component]
**Priority:** Critical | High | Medium | Low
**Type:** Functional | Integration | UI | API | Performance | Security
**Automation Candidate:** Yes | No | Future

**Preconditions:**
- List the system state, test data, and setup required before execution

**Test Steps:**
1. Step one
2. Step two
3. ...

**Expected Result:**
Describe exactly what should happen — UI state, API response, database change, event emitted, etc.

**Actual Result:** *(to be filled during execution)*

**Pass/Fail:** *(to be filled during execution)*

**Notes / Edge cases:**
Any additional context, known limitations, or related cases

---

Generate the full set of test cases now. Group them by area (e.g., "Authentication", "Data Validation", "API Behavior", "UI/UX", "Error Handling", "Performance Boundaries"). At the end, provide a **coverage summary** noting any areas that may need additional cases or manual exploratory testing.
