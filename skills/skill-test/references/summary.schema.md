# The schema definitions for the summary.md file

## summary.md

Defines the skill test results for each iteration, generally should include:

- A recap of the eval results for each test case, with and without the skill.
- A comparison of the with-skill and without-skill runs, showing as tables.
- A per-expectation result table for each eval so it is clear which expectations were met in each run.

```markdown
# Iteration <N> Summary

## Skill

`<skill-name>`

## Eval Results

table of eval results for each test case, with and without skill, e.g.:

| Eval ID | With Skill Result | Without Skill Result |
| ------- | ----------------- | -------------------- |
| eval-1  | pass              | fail                 |
| eval-2  | pass              | pass                 |

## Eval Detail Results

- For each eval, a detailed comparison of the with-skill and without-skill runs, including whether expectations were met, and any notable behavior or artifacts.

### Eval ID

#### Expectation Results

| Expectation                                              | With Skill | Without Skill | Notes                                       |
| -------------------------------------------------------- | ---------- | ------------- | ------------------------------------------- |
| `the skill-test is invoked successfully`                 | met        | not met       | Skill was loaded only in the with-skill run |
| `summary.md is written to the expected output directory` | met        | met           | Both runs produced the required artifact    |
```
