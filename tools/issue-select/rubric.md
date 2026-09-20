# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check               | Evidence                                                                              | Pass condition                                                                                                                                                                                | Weight    |
| ------------------- | ------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- |
| Community Alive     | Last 5 default-branch commits, maintainer first-response sample, and Comments section | At least one default-branch commit by a non-bot author occurred within the last 30 days, or at least one recently updated issue received an Owner/Member/Collaborator response within 30 days | Required  |
| Issue is Unclaimed  | Assignees and Linked PRs                                                              | No Assignees and no open linked PRs                                                                                                                                                           | Required  |
| Repo in Use         | Archived flag, last push to any branch, and latest release                            | Repository is not archived and has either a push or release within the last 90 days                                                                                                           | Required  |
| Scope               | Issue body, acceptance criteria, linked files/components, maintainer comments         | The issue identifies a specific change or outcome and does not explicitly require a multi-component refactor, architectural redesign, or coordinated changes across multiple repositories     | Preferred |
| Contribution Policy | Contribution policy in CONTRIBUTING.md                                                | Repository does not prohibit the AI contribution/tooling used for this course                                                                                                                 | Required  |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->

Accept if every required check passes; preferred checks never change the verdict, they rank accepted issues; unclear counts as fail
