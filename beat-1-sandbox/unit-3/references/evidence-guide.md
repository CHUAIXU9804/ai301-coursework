# Evidence guide: where evidence lives in a plan package

<!--
THIS IS THE PART YOU WRITE (second week running: the judgment files
stay in your hands). The skill uses this guide as its map: for every
kind of evidence a rubric check names, this file says WHERE to find it
in a plan package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repro-evidence block,
  the candidate plan's scope statement or test plan, the plan comment,
  the repo-facts block). In live mode (where on GitHub or in the
  draft: the issue thread, the student's posted repro comment, the
  repo's docs, the draft plan and comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the stated cause cites behavior the
  repro evidence actually shows") over adjectives ("diagnosis is
  solid").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts twice: your
procedure.md tells the skill WHEN to gather each family, and this
guide tells it WHERE. Write the map you wish your executor had.
-->

## Diagnosis and grounding

<!-- Where the plan states its cause, and where the repro evidence
pins down the behavior that cause must explain. What it means for a
diagnosis to follow from the evidence rather than contradict or
ignore it. -->

**Where it lives:**

In an eval bundle, look at the candidate plan's Diagnosis, Cause, or Summary and compare it with the issue context, repro-evidence block (including failure and control cases), and relevant repo facts. In live mode, check the draft plan, GitHub issue, student's posted repro comment, and relevant repository code or documentation.

**What good looks like:**

The stated cause explains the observed failure and is consistent with the reproduction steps and control cases. The proposed fix addresses the identified failure mechanism rather than only hiding its symptoms.

## Scope

<!-- Where the plan bounds itself: the in-scope statement, the
not-in-scope line, the files or areas named. What one bounded change
looks like next to a drive-by rewrite. -->

**Where it lives:**

In an eval bundle, look at the candidate plan's Scope, Changes, and Not-in-scope statements, compared with the issue context and repro evidence. In live mode, inspect the draft plan's proposed changes and exclusions against the GitHub issue and reproduced behavior.

**What good looks like:**

Every proposed change directly contributes to fixing the reproduced problem or preserving affected behavior. The plan excludes unrelated features and refactoring without excluding work necessary for the fix.

## Executability

<!-- Where the plan says what will actually be done: files or areas,
approach, order of work. What it means for a stranger to be able to
start executing without asking the author anything. -->

**Where it lives:**

In an eval bundle, look at the candidate plan's proposed changes, implementation steps, and repo-facts block. In live mode, examine the draft implementation approach against the relevant repository files, existing mechanisms, and documentation.

**What good looks like:**

The plan identifies where the change should occur, what behavior or logic must change, and how the proposed approach works. Another developer could begin implementation without guessing essential technical decisions.

## Test plan

<!-- Where the plan says how success will be observed, and how that
maps onto the repro evidence's steps and artifacts. What a decisive
test plan names that a vague one does not. -->

**Where it lives:**

In an eval bundle, compare the candidate plan's Test section against the repro-evidence block's failing steps, observed results, expected behavior, and control cases. In live mode, compare the draft test plan with the student's posted repro evidence and relevant existing repository tests.

**What good looks like:**

The proposed tests specify inputs and observable expected outcomes that would fail with the original bug and pass after a correct fix. Relevant control cases verify that the fix does not introduce incorrect behavior in previously unaffected scenarios.

## Honesty

<!-- Where claims meet uncertainty: risks, unknowns, and deviations.
How to tell stated unknowns from false confidence, and where an
honest mid-build deviation gets recorded. -->

**Where it lives:**

In an eval bundle, examine the candidate plan's diagnosis, assumptions, risks, unknowns, and proposed changes against the repro evidence and repo facts. In live mode, inspect the draft plan, issue discussion, and any documented implementation updates or deviations.

**What good looks like:**

Claims essential to the proposed fix are supported by available evidence, while unresolved assumptions are identified with steps to verify them. Any known deviation from the original approach is documented with its reason and impact rather than presented as if the original plan was followed unchanged.

## Comms

<!-- Where the words meet the thread and the repo: the plan comment
read against the issue's maintainer signals (thread highlights, or
the live thread) and against the repo-facts block's stated templates,
contributing asks, and contribution policy (including AI-use
disclosure requirements). What thread-aware looks like next to
boilerplate. -->

**Where it lives:**

In an eval bundle, compare the plan comment and proposed changes with the thread highlights and repo-facts block, including contribution templates, maintainer instructions, and AI-use disclosure requirements. In live mode, inspect the GitHub issue thread, draft plan comment, CONTRIBUTING.md, issue or PR templates, and applicable repository policies.

**What good looks like:**

The plan comment addresses relevant maintainer requests, accurately represents the proposed approach, and follows applicable repository communication and disclosure requirements. It does not ignore explicit restrictions, misrepresent prior decisions, or substitute generic boilerplate for issue-specific information.
