# The schema definitions for the evals.json file

## evals.json

Defines the evals for a skill. Located at `evals/evals.json` within the skill directory.

```json
{
  "skill_name": "example-skill",
  "evals": [
    {
      "id": 1,
      "prompt": "User's example prompt",
      "files": ["evals/files/sample1.pdf"],
      "expectations": [
        { "step": "skill-invoke", "description": "This skill was invoked" },
        { "step": "output", "description": "The output includes X" },
        { "step": "script", "description": "The skill used script Y" }
      ]
    }
  ]
}
```

**Fields:**

- `skill_name`: Name matching the skill's frontmatter
- `evals[].id`: Unique integer identifier
- `evals[].prompt`: The task to execute
- `evals[].files`: Optional list of input file paths (relative to skill root)
- `evals[].expectations`: List of verifiable statements, each with:
  - `step`: The point in the process this expectation applies to (e.g., "skill-invoke", "output", "script")
  - `description`: A clear statement of what should be true at this step for the expectation to be met
