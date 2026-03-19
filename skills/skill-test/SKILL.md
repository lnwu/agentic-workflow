---
name: skill-test
description: Evaluate skills. Use when testing skills.
---

# Test Cases

The test cases should live in the <path-to-skill>/evals/evals.json, if no such file exists, stop the user — they can't run tests without test cases.

Each eval is a JSON object with the following fields:

- `id`: a unique identifier for the test case.
- `prompt`: this should be a string that represents the user's input.
- `expected_output`: the expected summary from the skill.
- `assertions`: a list of assertions to check. Each assertion is string that should be present in the skill's output. This is optional but can help catch issues that a simple string match might miss.

# Running and evaluating test cases

This section is one continuous sequence — don't stop partway through.

Put results in skills-test-results/<skill-name>-workspace/ as a sibling to the skills directory. Within the workspace, organize results by iteration (iteration-1/, iteration-2/, etc.) and within that, each test case gets a directory (eval-<testid>/, eval-<testid>/, etc.). Don't create all of this upfront — just create directories as you go.

## Step 1: Spawn all runs (with-skill AND baseline) in the same turn

For each test case, spawn two **subagents** in the same turn — one with the skill, one without. This is important: don't spawn the with-skill runs first and then come back for baselines later. Launch everything at once so it all finishes around the same time.

**With-skill run:**

```
Execute this task:
- Skill path: <path-to-skill>
- Task: <eval prompt>
- Input files: <eval files if any, or "none">
- Save outputs to: <workspace>/iteration-<N>/eval-<ID>/with_skill/outputs/
- Outputs to save: <what the user cares about — e.g., "the .docx file", "the final CSV">
```

**Baseline run** (same prompt, but the baseline depends on context):

- **Creating a new skill**: no skill at all. Same prompt, no skill path, save to `without_skill/outputs/`.
- **Improving an existing skill**: the old version. Before editing, snapshot the skill (`cp -r <skill-path> <workspace>/skill-snapshot/`), then point the baseline subagent at the snapshot. Save to `old_skill/outputs/`.

Write an `eval_metadata.json` for each test case (assertions can be empty for now). Give each eval a descriptive name based on what it's testing — not just "eval-0". Use this name for the directory too. If this iteration uses new or modified eval prompts, create these files for each new eval directory — don't assume they carry over from previous iterations.

```json
{
  "eval_id": 0,
  "eval_name": "descriptive-name-here",
  "prompt": "The user's task prompt",
  "assertions": []
}
```
