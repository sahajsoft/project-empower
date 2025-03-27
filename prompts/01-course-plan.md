# Prompt: Generate High-Level Unit-Based Curriculum Outline

**Role:** You are an AI assistant acting as an experienced Curriculum Designer.

**Goal:** Generate a **high-level, unit-based curriculum outline** (e.g., for 12 units) for an introductory programming course. This outline should define the main theme and key topics covered in each unit, providing a logical progression for beginners. **This outline serves as the foundational structure (Step 1). Its output, specifically the `course_context` block combined with one chosen `unit` block from the `units` array, will be used as input for generating detailed unit plans in Step 2.**

**Input Specifications (Provide values for these fields):**

```json
{
  "language": "Python",
  "course_title": "[e.g., Introduction to Python Programming, Python Fundamentals for Beginners]",
  "overall_goal": "[Describe the main outcome for learners, e.g., 'Gain foundational knowledge of Python programming concepts and be able to write simple scripts.', 'Prepare learners for basic data manipulation tasks using Python.']",
  "target_audience": {
    "description": "Beginners with no prior programming experience",
    "level": "Beginner",
    "context": "[Optional: e.g., University students, Adult learners in a bootcamp, Self-paced online learners]"
  },
  "total_units": 12,
  "learning_environment": "[e.g., Online synchronous, In-person bootcamp, Self-paced asynchronous]",
  "focus_areas": [
    "[Optional: List any specific areas to emphasize or include, e.g., 'Core programming constructs', 'Introduction to data structures', 'Problem-solving skills', 'Include a mini-project in the final units']"
  ]
}
```

**Output Format Instructions:**

Generate a **JSON object** representing the high-level curriculum outline. The structure should clearly separate the overall context from the list of units:

```json
{
  "curriculum_outline": {
    "course_context": {
      "course_title": "[From input]",
      "language": "[From input]",
      "target_audience": "[From input target_audience object]",
      "total_units": "[From input total_units]",
      "overall_goal": "[From input overall_goal]",
      "learning_environment": "[From input learning_environment]",
      "description": "[Generate a brief (1-2 sentence) summary of the course based on input]"
    },
    "units": [
      {
        "unit_number": 1,
        "theme_title": "[Concise title for the unit's focus, e.g., 'Getting Started: Setup & First Program']",
        "key_topics": [
          "[List 2-5 major topics/concepts for the unit, e.g., 'What is programming?', 'Python installation (IDE/Notebook)', 'Running simple scripts', 'Basic syntax rules', 'Print function']"
        ]
      },
      {
        "unit_number": 2,
        "theme_title": "[e.g., 'Variables, Data Types & Operations']",
        "key_topics": [
          "[e.g., 'Concept of variables', 'Core data types (int, float, str, bool)', 'Assignment operator', 'Basic arithmetic operations', 'Type conversion basics']"
        ]
      }
      // ... continue for all units specified in total_units
    ]
  }
}
```

**Key Requirements for the Output:**

1.  **High-Level Focus:** Each unit should list only the major themes and foundational topics. Do not include specific learning objectives, detailed activities, assignment descriptions, or code examples in this outline.
2.  **Logical Progression:** Ensure the topics build upon each other unit by unit, appropriate for beginners.
3.  **Conciseness:** Keep the `theme_title` and `key_topics` brief and to the point.
4.  **Completeness:** Generate entries for all units specified in `total_units`.
5.  **JSON Validity:** The final output must be valid JSON.
6.  **Clear Structure for Step 2:** The output must contain a distinct `course_context` block and a `units` array. To prepare input for Step 2 (Detailed Unit Plan), the user will copy the entire `course_context` block and _one specific unit block_ from the `units` array, placing them into the corresponding fields of the Step 2 prompt.

**Example Input:**

```json
{
  "language": "Python",
  "course_title": "Python Fundamentals for Absolute Beginners",
  "overall_goal": "Equip learners with no prior coding experience with the fundamental concepts of Python programming, enabling them to write and understand simple programs.",
  "target_audience": {
    "description": "Beginners with no prior programming experience",
    "level": "Beginner",
    "context": "Self-paced online learners"
  },
  "total_units": 12,
  "learning_environment": "Self-paced asynchronous",
  "focus_areas": [
    "Core programming constructs",
    "Basic data structures",
    "Problem-solving approach",
    "Reading and writing simple files"
  ]
}
```

**Generate the JSON output based on the provided input specifications.**
