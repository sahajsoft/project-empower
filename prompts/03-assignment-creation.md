## Prompt: Generate Coding Assignment(s) with Balanced Unit Tests

**Role:** You are an AI assistant specializing in creating educational programming assignments and robust unit tests.

**Goal:** Based on the provided `course_context` and the `detailed_unit_plan` for a specific unit (from Step 2), generate one or more **complete coding assignments**. Each assignment must include a clear problem description, relevant specifications (input/output, constraints), optional starter code, and most importantly, a suite of **balanced unit tests**.

**Definition of Balanced Unit Tests (Crucial Requirement):**

1.  **Validate Core Requirements:** Tests must accurately check if a solution meets the functional requirements implied by the assignment's `problem_description` and the unit's `learning_objectives`.
2.  **Avoid Overfitting:** Tests should pass any _correct_ logical implementation. They must _not_ depend on specific variable names, helper function structures, algorithm choices (unless mandated by constraints), or exact output formatting nuances (unless specified in `output_spec`). Focus on input/output behavior and logical correctness.
3.  **Avoid Underfitting:** Tests must provide reasonable coverage, including typical cases, relevant edge cases (e.g., empty inputs, zero, boundaries, nulls if applicable), and potentially error conditions if error handling is part of the `learning_objectives` or `constraints`.
4.  **Target Learning Objectives:** The assignment and its tests should clearly relate to and help assess the `learning_objectives` and `detailed_concepts` provided in the `detailed_unit_plan`.

**Input Specifications (Provide values for these fields):**

```json
{
  // This entire block is copied directly from the 'course_context' output of Step 1
  "course_context": {
    "course_title": "[e.g., Python Fundamentals for Absolute Beginners]",
    "language": "[e.g., Python]",
    "target_audience": {
      "description": "[e.g., Beginners with no prior programming experience]",
      "level": "[e.g., Beginner]",
      "context": "[e.g., Self-paced online learners]"
    },
    "total_units": "[e.g., 12]",
    "overall_goal": "[Overall course goal]",
    "learning_environment": "[e.g., Self-paced asynchronous]"
  },
  // This entire block is copied directly from the 'detailed_unit_plan' output of Step 2
  "detailed_unit_plan": {
    "unit_number": "[e.g., 2]",
    "theme_title": "[e.g., 'Variables, Data Types & Operations']",
    "language": "[e.g., Python]", // Often redundant with course_context, but good for clarity
    "learning_objectives": [
      "[Objective 1]",
      "[Objective 2]"
      // ... list of objectives from Step 2 output
    ],
    "detailed_concepts": [
      "[Concept 1]",
      "[Concept 2]"
      // ... list of concepts from Step 2 output
    ],
    "suggested_activities_assessments": [
      "[Suggestion 1]"
      // ... list from Step 2 output (provides context on assessment types expected)
    ]
  },
  // Optional: Specify testing framework preference
  "testing_framework_preference": "[Optional: e.g., pytest, unittest, jest, JUnit, leave null for default based on language]"
}
```

**Output Format Instructions:**

Generate a **JSON object** containing the assignment(s) for the unit. The structure should be:

```json
{
  "unit_assignments": {
    "unit_number": "[From input detailed_unit_plan.unit_number]",
    "assignments": [
      // Generate one or more assignment objects relevant to the unit plan
      {
        "assignment_title": "[Generate a concise, descriptive title based on the problem/concepts]",
        "problem_description": "[Clear, concise description of the task for the student, aligned with unit objectives/concepts.]",
        "input_spec": "[Optional: Describe expected input format/type/range, null if not needed]",
        "output_spec": "[Optional: Describe expected output format/type, null if not needed]",
        "constraints": [
          "[Optional: List any rules or limitations, e.g., 'Do not use external libraries', 'Function name must be `calculate_xyz`', 'Handle negative inputs']"
        ],
        "starter_code": "[Optional: Generate basic starter code/function signature, e.g., 'def solve(data):\\n  pass', null if none]",
        "target_objectives": [
          "[List the specific learning objective(s) from the input unit plan that this assignment primarily addresses]"
        ],
        "unit_tests": [
          {
            "test_name": "[Descriptive name, e.g., 'test_empty_list', 'test_basic_calculation', 'test_negative_input_edge_case']",
            "description": "[Explain WHAT this test checks and WHY it's important (link to requirements/edge cases/objectives)]",
            "test_code": "[The actual unit test code snippet in the specified language/framework. Focus on calling the target function/method and asserting the expected output/behavior.]",
            "purpose_category": "[Classify the test's main goal: 'typical_case', 'edge_case', 'error_handling', 'requirements_check', 'implementation_flexibility']" // Added more categories
          }
          // ... more test objects providing balanced coverage
        ]
      }
      // ... potentially more assignment objects for the same unit
    ]
  }
}
```

**Key Requirements for the Output:**

1.  **Assignment Relevance:** Assignments must directly relate to the `learning_objectives` and `detailed_concepts` of the provided `detailed_unit_plan`. Include the specific objectives targeted by each assignment in `target_objectives`.
2.  **Balanced Tests:** This is paramount. Adhere strictly to the definition provided above. Ensure a good mix of test types (typical, edge, error if applicable) using the `purpose_category`.
3.  **Test Clarity:** Each test must have a clear `description` explaining its purpose and rationale.
4.  **Code Generation:** `test_code` must be valid code for the specified `language` and `testing_framework` (or a reasonable default).
5.  **Flexibility:** Generate one or more assignments as appropriate for the complexity and scope of the unit's objectives.
6.  **JSON Validity:** The final output must be valid JSON.

**Example Input (Using hypothetical Step 2 output for Unit 2):**

```json
{
  "course_context": {
    "course_title": "Python Fundamentals for Absolute Beginners",
    "language": "Python",
    "target_audience": {
      "description": "Beginners",
      "level": "Beginner",
      "context": "Self-paced"
    },
    "total_units": 12,
    "overall_goal": "Write and understand simple Python programs.",
    "learning_environment": "Self-paced asynchronous"
  },
  "detailed_unit_plan": {
    "unit_number": 2,
    "theme_title": "Variables, Data Types & Operations",
    "language": "Python",
    "learning_objectives": [
      "Define what a variable is and its purpose.",
      "Identify and use Python's int, float, str, bool types.",
      "Implement variable assignment.",
      "Apply basic arithmetic operators.",
      "Convert between compatible data types.",
      "Read basic user input using input().",
      "Display output using print()."
    ],
    "detailed_concepts": [
      "Variable naming (snake_case)",
      "Dynamic typing",
      "Integer vs. float division",
      "String concatenation",
      "Boolean values",
      "type() function",
      "input() returns string",
      "print() basics"
    ],
    "suggested_activities_assessments": [
      "Code-along",
      "Quiz",
      "Debugging exercise",
      "Simple coding challenge"
    ]
  },
  "testing_framework_preference": "pytest"
}
```

**Generate the JSON output based on the provided input specifications, focusing intensely on the quality and balance of the unit tests.**
