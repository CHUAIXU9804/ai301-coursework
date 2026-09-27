# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->

**Where it lives:** In an eval package, look at the repro report's environment record and compare it with the issue context and repo-facts block for relevant operating system, application, runtime, dependency, or tool versions. In live mode, look at the environment information in the draft repro comment and compare it with the GitHub issue and the repository's documentation.

**What good looks like:** The environment identifies the versions and system information relevant to reproducing the issue. If the reproduction environment differs from the environment or versions targeted by the issue, the difference is clearly stated rather than treated as equivalent.

## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->

**Where it lives**: In an eval package, look at the reproduction steps, commands, inputs, and prerequisites in the repro report, using the repo-facts block and issue context to verify required setup. In live mode, look at the draft repro comment together with setup and usage instructions in the repository's documentation.

What good looks like: The instructions provide the starting state, required setup or inputs, actions or commands, and trigger needed for another person to attempt the same reproduction without additional clarification.

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->

**Where it lives**: In an eval package, look at artifacts in the repro report, such as output excerpts, logs, error messages, screenshots, or test results, and read them against the behavior described in the issue context. In live mode, look at the evidence included or referenced in the draft repro comment and compare it with the behavior described in the GitHub issue.

**What good looks like**: The evidence shows the specific behavior described by the issue, or clearly shows that the expected behavior did not occur during the reproduction attempt. Evidence of a different or merely similar error does not establish reproduction of the reported issue.

## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->

**Where it lives:** In an eval package, compare the claim comment and the repro report's stated outcome with its supporting artifacts, steps, and environment record. In live mode, compare statements in the draft comment with the evidence the student provides from the reproduction attempt.

**What good looks like:** The stated outcome does not claim more than the available evidence demonstrates. A report that could not reproduce the issue is valid when it states that result clearly and provides evidence of the attempt; a report that claims successful reproduction when its evidence shows different behavior is not.

## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

**Where it lives:** In an eval package, compare the claim comment and repro report with the issue context, repo-facts block, and any stated repository contribution, comment, template, or AI-use disclosure requirements. In live mode, compare the draft comment with the GitHub issue, repository contribution documentation, issue templates, and other stated communication or disclosure policies.

**What good looks like:** The comments identify the specific issue and communicate the investigation and results without unsupported claims or boilerplate that could apply to any issue. They follow repository-specific communication and disclosure requirements, including AI-assistance disclosure when the repository requires it. If no disclosure appears, treat the requirement as unsatisfied rather than assuming no AI was used.
