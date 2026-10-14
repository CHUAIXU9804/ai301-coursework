# Procedure: how this tool grades a PR package

<!--
THIS IS THE PART YOU WRITE (second week running for the procedure).
Week 3 you wrote these steps for a plan package; this week the graded
object is a PR package, and the read that matters most is a
side-by-side: the diff against the plan, the evidence against the test
plan, the description against both. Your week-3 procedure is the
pattern; do not paste it unchanged, because its read order was built
for a different object.

Your rotation is the design brief again, and this week friction routes
three ways: a stall on WHAT to decide is a rubric gap, a stall on
WHERE to look is a procedure gap (this file), and a stall on what the
tool even reads or outputs is a frame gap (your SKILL.md). A complete
procedure lets someone who has never seen a PR package before grade
one exactly the way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
plan's scope pair before opening the diff, and list the files the plan
names" is a step; "understand the change" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides where the plan sits in the order (before the diff? before the
description?) and says why the order matters for the side-by-side
checks that come later. -->

Read order

1. Determine the mode. In live mode, read scope.md first. Verify that the PR belongs to the repository specified by Repo: and that the repository is not an unfilled placeholder. Refuse to grade if either condition fails. In eval mode, use only the supplied bundle from eval/packages/; do not read scope.md, voice-guide.md, or external sources.

2. Read the grading components. Read rubric.md to identify the checks, pass conditions, weights, and verdict rule. Read references/evidence-guide.md to locate the evidence required for each check. Refuse to grade if rubric.md or procedure.md has no substantive instructions.

3. Read the issue and plan. In live mode, read the issue and its discussion thread, followed by plan.md, including ## Deviations. For house-chain students, use the house plan and reproduction pack instead of the student's own plan and reproduction evidence. In eval mode, read the issue context and plan supplied in the bundle. Record the reported problem, expected behavior, planned changes, file scope, test requirements, and documented deviations.

4. Read the PR implementation. Read the draft PR title, description, and commit history. In live mode, run git diff main...HEAD from the working copy. In eval mode, read the diff and commits supplied in the bundle. Record every changed file, relevant code change, and claim made in the PR description or checklist.

5. Read the test evidence. Record the test scenarios required by the issue and plan, the corresponding test artifacts, executed commands, printed output, and claimed results. Distinguish actual output from statements that tests passed.

6. Read the applicable standards. In live mode, read the repository's PR template, docs/CONTRIBUTING.md, and voice-guide.md. Record applicable mandatory submission requirements and any voice-guide violations in the draft PR title or description. In eval mode, use only standards included in the supplied bundle and ignore voice-guide.md.

## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which file, diff,
or page per your evidence guide) to pull the fact from, and what to
record. The load-bearing gathers this week are pairings: diff files
against plan scope, claimed evidence against the plan's test plan and
the repo's checks, description claims against diff contents. A
complete procedure leaves no check whose evidence an executor would
have to hunt for. -->

For each rubric check, gather and record the relevant evidence:

1. Plan alignment: Compare every file in the PR diff against the plan's file scope and ## Deviations. Record files and changes covered by the plan, documented deviations, and unexplained additions or modifications.

2. Claim verification: Compare each factual claim in the PR title, description, and checklist against the diff, commits, and test evidence. Record the specific lines or outputs that support or contradict each claim, including claims that something was not added or changed.

3. Required test coverage: Compare every test scenario explicitly required by the issue or plan against the tests and reproduction artifacts included in the PR. Record which scenarios have corresponding evidence and which are missing or unexplained.

4. Test execution evidence: Compare claimed test results against the supplied commands and their printed output. Record whether each claimed test run has both a command and actual output, and whether the output demonstrates the claimed behavior. Do not count comments describing expected output as execution evidence.

5. PR reviewability: Compare the PR title and description against the issue, plan, and diff. Record whether the reviewer can identify the issue being addressed, what changed, why it changed, and how the implementation was tested.

6. Repository standards: Compare the PR package against applicable mandatory requirements from the PR template, contribution guidelines, and issue thread. Record each requirement and the evidence of compliance or violation. Do not treat optional recommendations as mandatory.

7. Preferred check: Gather the evidence specified in rubric.md for the preferred check. For Residual Risk Documentation, read the PR description, deviations, test evidence. Check if the PR identifies relevant limitations, untested scenarios, or follow up work when such risks. But treat it as a preferred check, not a required check.

Record specific supporting, conflicting, or missing evidence before assigning grades. In live mode, record voice-guide violations separately for the summary; do not change the verdict based on voice alone unless the rubric explicitly requires it.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

1. Grade every check in the order listed in rubric.md, using the evidence gathered in the previous stage.

2. Compare the recorded evidence against every criterion in the check's pass condition. Apply the condition as written without adding new requirements.

3. Assign pass when the available evidence satisfies every criterion in the pass condition.

4. Assign fail when the evidence contradicts the pass condition or demonstrates that a required artifact, test, or action is missing.

5. Assign unclear when the available evidence is insufficient to determine whether the pass condition is satisfied. Do not infer missing evidence or treat unsupported claims as proof.

6. Record each check's name, grade, and a one-line evidence statement identifying the decisive fact, quote, or missing information.

7. Revisit a specific permitted evidence source only when necessary to verify a check. In eval mode, never retrieve evidence outside the supplied bundle. If the procedure does not specify how to perform a necessary step, report the gap rather than inventing a method.

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check: the
check whose failure the verdict turned on. When more than one check
failed, your procedure picks which one gets quoted (first failing
required check in rubric order is a fine rule); nothing picks it for
you, so write the rule down. A complete procedure produces the same
verdict from the same grades, every time. -->

1. Review the grades and weights of every check in rubric.md.

2. Assign accept only when every required check receives pass.

3. Assign reject if any required check receives fail or unclear.

4. Include the results of all preferred checks as feedback without allowing them to change the final verdict.

5. For each required check that causes rejection, identify the decisive evidence or missing information and explain which pass condition was not satisfied.

6. In live mode, include any voice-guide violations in the readable summary without changing the verdict unless an explicit rubric check applies.

7. Report the final verdict and every check result using the JSON schema required by SKILL.md. Populate item with the PR URL or bundle identifier, use the exact grades pass, fail, or unclear, and use only accept or reject for the verdict. End the response with the valid fenced JSON block and nothing after it.
