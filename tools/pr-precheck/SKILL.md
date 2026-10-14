---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

<!--
THIS IS THE PART YOU WRITE, and it is the last one: the frame itself.
Weeks 1 through 3 handed you a working SKILL.md and you filled the
files behind it; this week the frame ships as headings, and you write
what it says. The frontmatter above and the section headings below are
fixed (CONTRACT.md's layout rule); the instructions under each heading
are yours. Write instructions to the tool, in the imperative, the way
weeks 1-3's frames spoke to you: what to read, in what order, what to
refuse, what to emit. Your executor in the rotation is the test: a
frame gap they hit (cannot tell what the tool reads, or how a verdict
gets assembled) is a missing sentence here.

One section is not yours: the JSON schema in "Verdict and output" is
reproduced from CONTRACT.md verbatim and may not be altered. Your
words decide everything around it.
-->

## The question

<!-- State, in your words, the one question this tool answers and what
a PR package is: what artifacts it contains and what they are read
against. CONTRACT.md fixes the question; your frame has to say it so
the tool cannot wander into grading something else. -->

The PR-Precheck tool answers exactly one question about exactly one PR package: Is this ready to submit? A PR package is a pull request submitted by the candidate which includes a title, a description, commits, diff, and test evidence. Read against the plan the package claims to implement and the issue the plan belongs to. The tool never answers a different question, never answers from gut feeling.

## Inputs and modes

<!-- Define both modes. Live mode: name every input (your plan.md with
its deviation notes, your branch's diff, your draft PR title and
description, your test evidence, your issue), where each comes from,
and what a house-chain student reads instead. The branch's diff is
everything the branch changes relative to the repo's default branch:
`git diff main...HEAD` (three dots), run from the working copy, is
the command that produces it; name the source that concretely. Eval
mode: state that the bundle is the whole world, nothing is fetched,
and every check runs with the full verdict rule. -->

The tool runs in exactly two modes:

**Live mode**:

Check the student's own PR before submission. Read plan.md, including its ## Deviations section, the branch diff produced by git diff main...HEAD from the working copy, the draft PR title and description, and the test evidence. Compare these against the issue and its discussion thread, the repository's PR template, and docs/CONTRIBUTING.md. For house-chain students, read the house plan and house repro pack instead of the student's own plan and reproduction evidence. Apply the same checks. Review the branch's commits alongside the diff to identify changes that may not align with the plan.

**Eval mode**:

Read only the supplied package bundle from eval/packages/. Treat the bundle as the complete evidence source. Do not fetch external information or read local repository files outside the bundle. Evaluate every rubric check and apply the full verdict rule.

## The scope seam (live mode only)

<!-- Tell the tool when to read scope.md, what to do with the rules it
finds there, what to refuse, and what to do when the scope's repo line
is an unfilled placeholder. State that eval mode ignores scope.md
entirely. CONTRACT.md names the required behavior; your frame has to
instruct it. -->

In live mode, the tool reads `scope.md` before anything else. The scope names where the student's PR must live and the house rules of that environment; the tool refuses to grade work outside the scoped repo, and if the scope's repo line still carries an unfilled placeholder it stops without grading and tells the student to fill the `Repo:` line in `scope.md` with their section's Path Review repo. It never guesses a scope. In eval mode, `scope.md` is ignored entirely.

## The voice seam (live mode only)

<!-- Tell the tool when to read voice-guide.md, which outgoing text it
gates (the PR title and description), how to report a broken rule, and
why it never changes the verdict on its own. State that eval mode
ignores it entirely. -->

In live mode, the tool also reads `voice-guide.md` (the student's own rules for how they write upstream, carried forward from week 2) and holds the outgoing PR text, the title and the description, against those rules, reporting any rule the draft breaks in the summary. The voice guide never changes the verdict on its own unless the rubric has a check that reads it. In eval mode, `voice-guide.md` is ignored entirely: voice is personal and carries no gold labels; universal communication-quality checks live in the rubric.

## Component reads

<!-- Tell the tool how the pieces connect: rubric.md defines the
checks and the verdict rule, references/evidence-guide.md maps where
each evidence family lives, procedure.md is executed as written. Say
what the tool does when the procedure is silent on a step (report the
gap, never improvise around it) and what it does when rubric.md or
procedure.md has no content (the refusal rule, stated as an
instruction). -->

Read rubric.md to identify all checks, their pass conditions, and the verdict rule. Read references/evidence-guide.md to determine where to find the evidence required for each check. Follow procedure.md exactly to gather evidence, grade checks, and determine the final verdict.

Refuse to grade if rubric.md or procedure.md contains no substantive instructions. Explain which component is missing instead of inventing checks or procedures.

If procedure.md does not specify how to perform a necessary step, report the gap rather than improvising a new procedure. Use only the evidence and grading criteria defined by the components.

If the evidence is incomplete, grade the relevant check as unclear rather than refusing to grade, unless a specific refusal condition applies. Apply the rubric's verdict rule to determine the final verdict.

## Verdict and output

<!-- State the binary verdict space (accept means submit, reject means
hold) and instruct the tool to end its reply with the fenced JSON
block below, valid and last, with nothing after it. The schema is
CONTRACT.md's, verbatim; do not edit it. -->

Use only two final verdicts: accept means the PR is ready to submit, and reject means it must be held for revision. Grade each check as pass, fail, or unclear, with a one-line evidence statement explaining the decision.

Provide a readable summary of the checks when useful. End every completed grading response with the exact fenced JSON block below. Populate its fields with the package identifier, check results, evidence, and final verdict. Ensure the JSON is valid, preserve the schema and field order, and do not output anything after the closing code fence.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {
      "name": "<check name>",
      "grade": "pass|fail|unclear",
      "evidence": "<one line: the fact or quote that decided it>"
    }
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

<!-- Write the standing rules the tool grades under: evidence first,
grade the thing not the polish, the rubric decides, the procedure
decides how, and how unclear grades are treated when the rubric's
verdict rule is silent. CONTRACT.md states each as a guarantee; your
frame has to make them instructions. -->

These are not style advice; they are interface guarantees the master
tool honors and the bar assumes:

- **Evidence first.** For every check, cite the specific fact or quote supporting its grade. Never assign a grade without evidence.
- **Grade the thing, not the polish.** A terse complete PR can be
  ready and a beautiful confident one can be hiding drift. Every check
  reads the artifact itself against the plan, the issue, and the
  stated standards, never the formatting.
- **The rubric decides, not the run.** If a check passes by its stated
  condition but feels wrong, it still passes; the fix belongs in the
  rubric, not in the run.
- **The procedure decides how, not the run.** The tool follows
  `procedure.md` as written and reports its gaps instead of silently
  inventing steps.
- **Unclear defaults to fail.** Treat `unclear` as the rubric's
  verdict rule directs; where the rule is silent, an unverifiable
  claim is a failing one. A PR you cannot verify from the package is a
  PR that is not ready to submit.
