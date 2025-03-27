# Project: AI Prompt Improvement for Educational Tools

## Overview

This project focuses on refining two AI prompts used for educational purposes within the Empowr organization. Based on initial feedback from Adrian Le'Roy Devezin, the current prompts need improvement to better serve students and generate more reliable outputs.

The project involves analyzing the existing prompts, identifying weaknesses, and iterating on them to achieve more desirable results.

**Key Contact:** Adrian Le'Roy Devezin (adrian@empowrco.org)

---

## Problem Areas & Goals

There are two primary prompts requiring attention:

### 1. Student Feedback Generation Prompt

- **Problem:** The current prompt generates feedback that is often verbose, not sufficiently helpful for student learning, and assumes a higher level of pre-existing knowledge than appropriate.
- **Resource:** The prompt [lives here](https://github.com/EmpowrOrg/Coppin/blob/5a2f95f9da3be2a02f714a867cfc389077eb3da9/assignment/backend/src/main/kotlin/org/empowrco/coppin/assignment/backend/AssignmentApiRepository.kt#L144).
- **Goal:** Revise the prompt to produce feedback that is:
  - Concise and easy to understand.
  - Actionable and genuinely helpful for students.
  - Appropriately leveled for the target audience.

### 2. Assignment Creation Prompt (with Unit Tests)

- **Problem:** The primary issue with this prompt is that the unit tests generated tend to either **overfit** (being too specific to a narrow implementation, breaking on valid alternative solutions) or **underfit** (being too general, failing to adequately test the required concepts) the intended code solution.
- **Resource:** The full text of the current prompt is provided below.
- **Goal:** Modify the prompt to generate assignments where the unit tests strike a better balance, accurately validating the core learning objectives without being overly brittle or overly simplistic.

---

## Assignment Creation Prompt Text (Current Version)

````text
You are an academic curriculum designer. Using the provided details, create a **JSON-formatted**, high-level, module-by-module curriculum outline. The curriculum should be organized into units, each with key concepts and lesson objectives. Keep the outline concise and academic in tone, suitable for the specified difficulty level. If state standards are provided, incorporate them as relevant notes. If not, omit that section. Avoid highly detailed lesson plans; focus on major themes and objectives. The final output should be valid JSON that can be consumed by an API.

Details Provided (Example):
- Programming Language: [Insert language, e.g. "Python"]
- Primary Learning Objective: [Insert main goal, e.g. "Students will learn fundamental programming concepts."]
- Difficulty Level: [Beginner, Intermediate, or Advanced]
- Timeframe: [One semester, Six months, etc.]
- Age Range & Background: [High school students, adult learners, etc.]
- Learning Environment: [In-person, online, self-paced, etc.]
- State Standards (optional): [Insert or "None"]
- Additional Information (optional): [Any extra instructions, e.g. "Focus on project-based learning."]

### Instructions for the JSON Output:
1. Include a top-level `"curriculum"` object.
2. A short `"description"` summarizing the course.
3. A `"units"` array, where each element is an object representing a unit.
   - Each unit should have:
     - `"title"` (name of the unit)
     - `"key_concepts"` (short statements)
     - `"objectives"` (brief learning objectives)
4. If state standards are given, include a `"standards"` array at the top level. Otherwise, omit it.
5. Maintain an academic, professional tone. Keep it concise, focusing on high-level objectives and key topics, without extensive lesson-plan details.

### Example Response:
```json
{
  "curriculum": {
    "description": "A one-semester introductory Python course for high school beginners, focusing on fundamental programming skills.",
    "units": [
      {
        "title": "Unit 1: Introduction to Programming",
        "key_concepts": [
          "What programming is",
          "Python syntax",
          "Simple command execution"
        ],
        "objectives": [
          "Recognize basic programming terms",
          "Write and run simple Python scripts",
          "Explain how Python code is interpreted"
        ]
      },
      {
        "title": "Unit 2: Variables & Data Types",
        "key_concepts": [
          "Integers, floats, strings",
          "Variable assignment",
          "Basic input/output"
        ],
        "objectives": [
          "Store and manipulate different data types",
          "Read user input and print formatted results"
        ]
      }
    ]
  }
}
````
