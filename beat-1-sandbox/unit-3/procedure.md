# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides the order (issue first? repro evidence first?) and says why
the order matters for the checks that come later. -->

1. Read the repo facts and record relevant components, existing mechanisms, and repository constraints.

2. Read the issue and record the reported bug and expected behavior.

3. Read the repro evidence and record the failing steps, observed results, expected results, and control cases.

4. Read the candidate plan's diagnosis, scope, proposed changes, and test plan. Record the stated cause, intended fix, change boundaries, and proposed tests.

5. Read the thread highlights and plan comment to identify relevant requirements, restrictions, and prior decisions before grading.

## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which page or
thread location per your evidence guide) to pull the fact from, and
what to record. A complete procedure leaves no check whose evidence an
executor would have to hunt for. -->

For each check, record the relevant claim and the evidence it must match:

1. **Diagnosis:** Compare the plan's stated cause against each repro step, observed result, control case, and relevant repo fact.
2. **Fix and scope:** Compare the proposed changes against the diagnosed cause, repro evidence, scope boundaries, and exclusions.
3. **Execution readiness:** Compare the proposed implementation steps against the repo facts; record target components, intended logic, and missing technical details.
4. **Test validity:** Compare the proposed test inputs, assertions, and expected outcomes against the repro's actual and expected behavior.
5. **Uncertainty:** Identify unsupported assumptions or unresolved questions in the plan and record whether evidence or validation steps address them.
6. **Thread alignment:** Compare the plan's changes and comment against the thread highlights; record applicable requirements, restrictions, and conflicts.
7. **Repo conventions:** Compare the proposed approach against existing mechanisms and constraints in the repo facts.
8. **Regression awareness:** Compare proposed tests against adjacent behaviors and repro control cases; record any identifiable regression risks without coverage.

Record the specific supporting, conflicting, or missing evidence for each check before grading.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

1. Grade each rubric check in the order listed in rubric.md, using the evidence gathered in the previous stage.

2. Compare the recorded evidence against every criterion in the check's pass condition.

3. Assign P (Pass) if all criteria are satisfied by the available evidence.

4. Assign F (Fail) if the evidence contradicts the pass condition or demonstrates that a required criterion is not satisfied.

5. Assign ? (Unclear) if essential evidence is missing or insufficient to determine whether the condition is satisfied. Do not assume missing information is true or false.

6. Record the grade, supporting evidence, and a brief explanation for each check. Revisit the package only if the gathered evidence is insufficient and a specific source needs to be verified.

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check. A
complete procedure produces the same verdict from the same grades,
every time. -->

1. Review the grades for all checks marked required in rubric.md.

2. Assign accept (ready) only if every required check receives P.

3. Assign reject (hold) if any required check receives F or ?.

4. Record the preferred check results as feedback without allowing them to change the verdict.

5. For each required check that caused rejection, quote the specific evidence or identify the missing information and explain which pass condition was not satisfied.

6. Report the final verdict and per-check grades using the output format required by the skill.
