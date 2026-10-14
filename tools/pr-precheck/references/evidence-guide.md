# Evidence guide: where evidence lives in a PR package

## Plan fidelity (harness category: silent-drift)

<!-- Where the plan states its scope, boundary, and deviation notes,
and where the diff shows what actually changed. What it means for a
diff to match the plan, for an honest deviation to re-tie a mismatch,
and what silent drift looks like in each direction (more than the
plan, or less with no note). The description's fidelity claims read
against the diff live here too: a description claiming more or less
than the diff delivers is silent drift, not a comms problem. -->

**Where evidence lives:**

- **Eval mode:** Read the package's Plan context block, especially the planned file scope, change boundaries, and test plan. Compare these against the Candidate PR's unified diff, commit list, and description. Check for any documented deviations.
- **Live mode:** Read `plan.md`, including its `## Deviations` section, and compare the planned files and changes against `git diff main...HEAD`. Read the PR title and description in `pr_draft.md` and compare their implementation claims against the actual diff.

**What good looks like:**

Every changed file and implemented behavior falls within the plan's stated scope or is explicitly accounted for in a deviation note explaining what changed and why. Planned work that was omitted is also disclosed. Claims in the PR description accurately reflect what the diff implements, adds, removes, or leaves unchanged. Unexplained additions, omissions, or contradictory claims indicate silent drift.

## Test evidence (harness category: not-tested)

<!-- Where the PR shows its proof: the test-evidence section's
before/after against the plan's test plan and the reproduction's own
steps, and the outcome of the repo's own checks or suite. What
decisive looks like (an observable behavior named, the expected-after
stated, the checks' outcome visible) next to "tests pass". -->

**Where evidence lives:**

- **Eval mode:** Read the Plan context block's test plan and reproduction requirements. Compare these against the Candidate PR's test-evidence section and the tests or fixtures shown in the diff. Check any repository test requirements stated in Repo facts.
- **Live mode:** Read the test plan in `plan.md`, the original issue's reproduction steps, `test_evidence.md`, and the test-related changes in `git diff main...HEAD`. Compare the captured test results against the repository's required checks in `docs/CONTRIBUTING.md` and its PR template.

**What good looks like:**

The evidence identifies the original failing behavior, expected behavior after the fix, and results from running the relevant reproduction and regression tests. Claimed test executions include the actual commands and printed output, allowing a reviewer to verify the outcomes. Required test scenarios are covered, and failures or unrun checks are disclosed rather than represented as passing.

## Diff quality (harness category: unreviewable)

<!-- Where the change itself lives: the unified diff and the commit
list. What a reviewable change looks like (the fix visible, nothing
unrelated riding along) and the debris tells: debug leftovers, dead
code, commented-out blocks, formatting churn, drive-by edits. -->

**Where evidence lives:**

- **Eval mode:** Inspect the Candidate PR's unified diff and commit list. Compare the changed files and code against the intended implementation described in Plan context.
- **Live mode:** Inspect `git diff main...HEAD` and the branch's commits relative to `main`. Compare the implementation against `plan.md` and its documented deviations.

**What good looks like:**

The diff contains the intended implementation and supporting changes, with enough context for a reviewer to identify the fix. It does not contain unrelated modifications, temporary debugging statements, unused code, commented-out implementation blocks, or unnecessary formatting changes that obscure the fix. Commit history and diff provide a traceable view of what changed.

## Standards and comms (harness category: standards-wall)

<!-- Where the repo states its asks (the repo-facts block's PR
template sections, contributing instructions, and stated policy,
including AI-use disclosure) and where the PR honors them: the
stated sections filled with real content, the disclosure present,
explicit maintainer direction in the thread engaged. What compliant
looks like next to boilerplate or a visibly ignored ask. (Whether
the description's claims match the diff is plan fidelity, above.) -->

**Where evidence lives:**

- **Eval mode:** Read the Repo facts block for the PR template's required sections, contribution instructions, stated policies, and AI-use disclosure requirements. Compare these against the Candidate PR's title, description, checklist, and any applicable maintainer directions included in the package.
- **Live mode:** Read `.github/PULL_REQUEST_TEMPLATE.md`, `docs/CONTRIBUTING.md`, and the issue's discussion thread. Compare applicable requirements against `pr_draft.md` and the supporting test evidence. Read `voice-guide.md` separately for personal writing rules.

**What good looks like:**

The PR title and description provide the information required by the repository's template, including a meaningful summary, issue reference, changes, testing information, and reviewer notes where applicable. Mandatory contribution requirements and explicit maintainer instructions are addressed, and the required AI-use disclosure is present. Checklist entries accurately indicate completed actions, while unavailable or incomplete results are disclosed. Voice-guide violations are reported separately and do not affect the verdict unless the rubric explicitly makes them a check.
