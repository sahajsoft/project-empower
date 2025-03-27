## Prompt: Generate Detailed Unit Plan

**Role:** You are an AI assistant acting as an Instructional Designer, specializing in breaking down curriculum topics into actionable unit plans.

**Goal:** Take the high-level theme and key topics for a **single unit** from a course outline (generated in Step 1) and expand it into a **detailed unit plan**. This plan should include specific learning objectives, a more granular breakdown of concepts, and suggestions for learning activities and assessment types. **This detailed plan (Step 2) serves as the direct input for generating specific assignments and tests in Step 3.**

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
  // This block is copied directly from ONE specific unit object in the 'units' array of Step 1 output
  "unit_to_detail": {
    "unit_number": "[The specific unit number, e.g., 2]",
    "theme_title": "[The theme title for this unit, e.g., 'Variables, Data Types & Operations']",
    "key_topics": [
      "[The list of key topics for this unit, e.g., 'Concept of variables', 'Core data types (int, float, str, bool)', 'Assignment operator', 'Basic arithmetic operations', 'Type conversion basics']"
    ]
  }
}
```

**Output Format Instructions:**

Generate a **JSON object** representing the detailed plan for the specified unit. The structure should be:

```json
{
  "detailed_unit_plan": {
    "unit_number": "[From input unit_to_detail.unit_number]",
    "theme_title": "[From input unit_to_detail.theme_title]",
    "language": "[From input course_context.language]",
    "learning_objectives": [
      "[List 3-5 specific, measurable learning objectives for this unit. Start with action verbs (e.g., Define, Explain, Identify, Use, Implement, Differentiate, Convert). Objectives should align directly with the key topics.]"
      // e.g., "Define what a variable is and its purpose in programming."
      // e.g., "Identify and correctly use Python's fundamental data types: int, float, str, bool."
      // e.g., "Implement variable assignment using the '=' operator."
      // e.g., "Apply basic arithmetic operators (+, -, *, /, %) to numeric types."
      // e.g., "Convert variables between compatible data types using functions like int(), str(), float()."
    ],
    "detailed_concepts": [
      "[Break down the key_topics into more specific sub-topics or concepts that would be covered in lessons/materials for this unit.]"
      // e.g., "Variable naming conventions (snake_case)"
      // e.g., "Dynamic typing in Python"
      // e.g., "Integer vs. float division"
      // e.g., "String concatenation and basic string methods (lower(), upper())"
      // e.g., "Boolean logic basics (True/False)"
      // e.g., "Using the type() function"
      // e.g., "Reading user input with input() (and its string nature)"
      // e.g., "Basic output formatting with print()"
    ],
    "suggested_activities_assessments": [
      "[List potential *types* of learning activities or formative assessments suitable for the concepts and objectives. Do *not* write the full activity/assessment details.]"
      // e.g., "Interactive code-along: Declaring variables and performing operations."
      // e.g., "Short quiz: Matching data types to examples."
      // e.g., "Debugging exercise: Finding errors in variable usage or type mismatches."
      // e.g., "Simple coding challenge: Write a script that takes user input, performs a calculation, and prints the result."
      // e.g., "Concept map: Visually relating variables, data types, and operators."
      // e.g., "Peer discussion: Explaining the difference between int and float division."
    ]
  }
}
```

**Key Requirements for the Output:**

1.  **Focus on One Unit:** The output must pertain _only_ to the unit specified in the `unit_to_detail` input.
2.  **Actionable Objectives:** Learning objectives must be clear, specific, and use action verbs indicating observable learner behavior.
3.  **Granularity:** `detailed_concepts` should offer more specific points than the input `key_topics`.
4.  **Activity/Assessment _Types_:** `suggested_activities_assessments` should list _kinds_ of tasks (quiz, challenge, code-along, discussion) rather than fully detailed assignment prompts.
5.  **Alignment:** Ensure objectives, detailed concepts, and suggested activities are all logically aligned with the unit's `theme_title` and `key_topics`.
6.  **Bridge to Step 3:** The output should provide sufficient detail (especially objectives and concept breakdown) to effectively guide the generation of specific assignments and tests in the next step.
7.  **JSON Validity:** The final output must be valid JSON.

**Example Input (Expanding Unit 2 from previous example):**

```json
{
  "course_context": {
    "course_title": "Python Fundamentals for Absolute Beginners",
    "language": "Python",
    "target_audience": {
      "description": "Beginners with no prior programming experience",
      "level": "Beginner",
      "context": "Self-paced online learners"
    },
    "total_units": 12,
    "overall_goal": "Equip learners with no prior coding experience with the fundamental concepts of Python programming, enabling them to write and understand simple programs.",
    "learning_environment": "Self-paced asynchronous"
  },
  "unit_to_detail": {
    "unit_number": 2,
    "theme_title": "Variables, Data Types & Operations",
    "key_topics": [
      "Concept of variables",
      "Core data types (int, float, str, bool)",
      "Assignment operator",
      "Basic arithmetic operations",
      "Type conversion basics"
    ]
  }
}
```

**Generate the JSON output based on the provided input specifications.**
