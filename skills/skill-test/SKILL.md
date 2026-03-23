---
name: skill-test
description: Evaluate skills. Use when testing skills.
---

# Test Cases

The test cases should live in the <path-to-skill>/evals/evals.json, if no such file exists, stop the user — they can't run tests without test cases.

See [evals.json schema](references/evals.schema.md) for details.

# Running and evaluating test cases

This section is one continuous sequence — don't stop partway through.

Put results in skills-test-results/<skill-name>-workspace/ as a sibling to the skills directory. Within the workspace, organize results by iteration (iteration-1/, iteration-2/, etc.) and within that, each test case gets a directory (eval-<testid>/, eval-<testid>/, etc.). Don't create all of this upfront — just create directories as you go.

## Step 1: Spawn all runs (with-skill AND without-skill) in the same turn

For each test case, spawn two **subagents** in the same turn — one with the skill, one without. This is important: don't spawn the with-skill runs first and then come back for without-skill later. Launch everything at once so it all finishes around the same time.

**With-skill run:**

```
Execute this task:
- Skill path: <path-to-skill>
- Task: <eval prompt>
- Input files: <eval files if any, or "none">
- Save outputs to: <workspace>/iteration-<N>/eval-<ID>/with_skill/outputs/
- Outputs to save: <what the user cares about — e.g., "the .docx file", "the final CSV">
```

**Without-skill** (same prompt, but no skill):

No skill at all. Same prompt, no skill path, save to `without_skill/outputs/`.

## Step 2: Write summaries

After the runs finish, write a `summary.md` for each run (with and without skill) and show **Eval Results** and **Eval Detail Results** section to the user.

See [summary.md schema](references/summary.schema.md) for details.
