# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check             | Evidence                                                                                                                                                                | Pass condition                                                                                                                                                                                                                                                                                                         | Weight    |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- |
| Environment_Check | The repro report’s environment record, read against the repo-facts block for relevant tool/runtime requirements                                                         | if the report names the tool version or the OS information                                                                                                                                                                                                                                                             | Required  |
| Reproducibility   | The repro report's reproduction steps and commands, read against the repo-facts block and the issue’s described setup/preconditions                                     | if the report contains specific steps and information for others to reproduce the issue without additional clarification                                                                                                                                                                                               | Required  |
| Behavior_Match    | The repro report's observed output and supporting artifacts, read against the behavior described in the issue                                                           | The observed behavior matches the specific behavior described by the issue rather than a different or adjacent problem                                                                                                                                                                                                 | required  |
| Outcome_Accuracy  | The repro report's stated outcome, read against its observed results and supporting artifacts                                                                           | The stated outcome is supported by the evidence. An evidenced cannot-reproduce passes; claiming reproduction when the evidence shows different behavior fails                                                                                                                                                          | required  |
| Repo_Conventions  | The claim comment and repro report, read against the repo-facts block for repository-specific contribution, communication, template, and AI-use disclosure requirements | The comments satisfy applicable repository-specific requirements. If the repository requires disclosure of AI assistance, the comments disclose the tool used and extent of assistance as required; missing a required disclosure fails this check. Do not infer from the absence of a disclosure that AI was not used | required  |
| Support_Evidence  | Screenshots, logs, or images in the report                                                                                                                              | if the report contains any useful screenshots, Logs, or Terminal outputs                                                                                                                                                                                                                                               | Preferred |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Accept if every required check passes; preferred checks never change the verdict; unclear counts as fail
