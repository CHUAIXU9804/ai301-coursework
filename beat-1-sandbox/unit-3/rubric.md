# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check                | Evidence                                                                                                                                                                           | Pass condition                                                                                                                                                                                                                                                                                                                                                                                                                        | Weight    |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- |
| diagnosis-supported  | The plan's stated diagnosis or cause compared against the repro evidence's failures steps, observed results, control cases, and relevant repo facts                                | Pass if the identified cause explains the observed failure, is consistent with the control cases, and is not contradicted by any reproduced observation or relevant repo fact. Fail if it merely restates the symptom, relies on a contradicted assumption, or cannot explain the difference between failing and control cases where that difference is relevant                                                                      | Required  |
| fix-targets-cause    | The plan's proposed changes and implementation approach compared with its stated cause and the Repro evidence's observed failure                                                   | Pass if the proposed changes modify the mechanism responsible for the failure and explain how the change would prevent the reproduced failure under the same conditions. Fail if the solution only hides the incorrect output, suppresses the error, or leaves the identified cause unaddressed                                                                                                                                       | Required  |
| scope-bounded        | The plan's scope statement, proposed changes, and exclusions, compared with the reproduced problem and the relevant repo facts                                                     | Pass if every proposed change is necessary to fix the reproduced problem or preserve directly affected behavior, and the scope does not exclude work essential to the fix. Fail if it includes unrelated features, unnecessary refactoring, or changes beyond the bug's required boundaries                                                                                                                                           | Required  |
| execution-ready      | The plan's implementation steps and proposed changes compared against the repo facts block's relevant files, components, and existing mechanisms                                   | Pass if the target implementation location, intended behavior change, and technical approach are sufficiently specified for another developer to identify where to start and what logic to implement without independently designing the solution. Fail if any essential implementation decision, target component, or prerequisite is missing                                                                                        | Required  |
| uncertainty-handling | The plan's causal claims, assumptions, unresolved questions, and proposed validation steps compared against the Repro evidence and repo-facts block                                | Pass if assumptions essential to the solution are supported by available evidence or explicitly identified as unverified with a way to validate them before they affect implementation. Fail if an unsupported assumption is presented as confirmed, or an unresolved question could materially change the proposed fix without a validation step                                                                                     | Required  |
| test-validity        | The plan's proposed test cases, inputs, and expected results compared against the Repro evidence's failing steps, control cases, and the behavior targeted by the proposed changes | Pass if the proposed tests would reproduce the original failure, specify observable expected behavior after the fix, and fail if the original defect remained. Where a plausible incorrect fix would break a relevant control case, the tests must also distinguish that incorrect behavior from the intended result. Fail if the tests lack observable assertions, cannot detect the original bug, or miss an essential control case | Required  |
| thread-alignment     | The plan's proposed changes and accompanying plan comment compared against the thread highlights, including stated requirements, restrictions, and prior decisions                 | Pass if the proposed approach and comment are consistent with applicable thread requirements, respect explicit restrictions, and do not contradict established decisions without an explained reason. Fail if they overlook a material requirement, violate a restriction, or misrepresent an established decision                                                                                                                    | Required  |
| repo-conventions     | The plan's implementation approach compared against the repo-facts block's existing mechanisms, technical constraints, and documented conventions                                  | Pass if the proposed implementation follows applicable existing repository mechanisms and constraints, or provides a technically justified reason for departing from them. Fail if it contradicts an explicit constraint or unnecessarily replaces or duplicates an established mechanism                                                                                                                                             | Required  |
| regression-awareness | The plan's scope, proposed changes, and tests compared against adjacent behaviors described in the Repro evidence or repo-facts block                                              | Pass if the plan identifies relevant neighboring behaviors that could be affected by the fix and proposes tests with observable expected outcomes for those behaviors. Fail if a clearly identifiable neighboring regression risk is omitted or the proposed test would not detect it                                                                                                                                                 | Preferred |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Ready only if every required check passes. Any required check graded F means hold. Any required check graded ? means hold, because we cannot verify the fix targets the real bug. Preferred checks are reported but never change the verdict.
