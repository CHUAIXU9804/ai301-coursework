# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

Record of the pull request you opened against the Path Review repo, and of the evaluation
runs that produced `eval-run.txt`. This file is graded at the path above; a copy kept
anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your pull request

### Pull request

https://github.com/codepath/pathreview-ai301-fa26-s1/pull/188

### Branch

> [The name of the branch the pull request comes from, exactly as it appears in your fork.
> The naming shape is a type prefix, then the issue number, then a short description. **The
> issue number in the branch name must be the number of the issue the pull request fixes** —
> a name carrying any other number does not satisfy this field.]

```text
fix/59-faithfulness-checker
```

---

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

### Run history

> [The agreement score of each run you did, in order. A single run is a complete answer if
> only one run occurred. **The last score in your list must match the agreement line in the
> `eval-run.txt` you committed** — that file is the record of your final run.]

```text
# eval run written by run_eval.py at 2026-10-14T02:14:44Z
# model: sonnet (pinned)
# graded: /Users/cxu/.claude/skills/pr-precheck
# packages: 20 scored
# SKILL.md sha256:e24c30cfa9849f29
# rubric.md sha256:355f71b2b718abb9
# procedure.md sha256:5758b66167341b41
# evidence-guide.md sha256:7ff0da734696d8e5
#
grading 20 package(s) with the tool at /Users/cxu/.claude/skills/pr-precheck, model sonnet, 5 worker(s)...
pkg-03: reject
pkg-01: reject
pkg-05: accept
pkg-04: reject
pkg-02: accept
pkg-06: reject
pkg-07: reject
pkg-09: reject
pkg-10: reject
pkg-08: accept
pkg-11: reject
pkg-14: reject
pkg-12: reject
pkg-13: accept
pkg-15: reject
pkg-18: reject
pkg-17: reject
pkg-16: accept
pkg-20: reject
pkg-19: accept

item category gold verdict agree note
pkg-01 standards-wall reject reject yes  
pkg-02 clear-accept accept accept yes  
pkg-03 silent-drift reject reject yes  
pkg-04 not-tested reject reject yes  
pkg-05 clear-accept accept accept yes  
pkg-06 silent-drift reject reject yes  
pkg-07 not-tested reject reject yes  
pkg-08 clear-accept accept accept yes  
pkg-09 silent-drift reject reject yes  
pkg-10 not-tested reject reject yes  
pkg-11 clear-accept accept reject NO failed: Claim verification, Required test coverage, Test execution evidence
pkg-12 unreviewable reject reject yes  
pkg-13 clear-accept accept accept yes  
pkg-14 not-tested reject reject yes  
pkg-15 unreviewable reject reject yes  
pkg-16 clear-accept accept accept yes  
pkg-17 silent-drift reject reject yes  
pkg-18 unreviewable reject reject yes  
pkg-19 clear-accept accept accept yes  
pkg-20 standards-wall reject reject yes

categories: clear-accept 6/7 not-tested 4/4 silent-drift 4/4 standards-wall 2/2 unreviewable 3/3
agreement: 19/20 scored items (bar: 18/20: PASS)
```

### Package analysis

> [Pick one scored package (`pkg-01` through `pkg-20` — the four `calib-` packages are never
> scored). Name it by id, say what your rubric decided and what the gold label said, and
> explain why your rubric read it that way.]

I tested pkg-20 (Ghostty). The gold label rejected it, and my rubric also rejected it, because the repository required AI usage disclosure, and the package lacked that information. My rubric requires mandatory repository instructions to be satisfied, so a missing required disclosure caused the repository standards to fail.

### Check rationale

> [Quote one check from the `rubric.md` you uploaded to `tools/pr-precheck/`, exactly as it reads now.
> Then say why it reads that way — what you revised to get there, or what you rejected in
> favour of it.]

```text
| Diff quality | Unified diff, changed-file list, commits, plan, and deviations | The intended fix is identifiable and reviewable. The diff does not contain unrelated modifications, temporary debugging code, dead code, commented-out implementation blocks, or unnecessary formatting churn that obscures the change. | required |
```

I added this check because passing tests alone does not guarantee that a PR contains only relevant, high-quality changes. Reviewers should be able to identify the intended fix without unrelated modifications or unnecessary changes obscuring it. I wanted the rubric to evaluate not just whether the implementation works, but also whether the diff is focused, maintainable, and easy to review.

### Trade-offs

> [Every check gives something up. Any one of these is a complete answer: a package whose
> result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
> stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
> the point in full when the reason follows.]

The trade-off is that a stricter Diff quality check may reject a technically correct fix because the PR includes unrelated changes. I encountered this with my PR for issue #59: the implementation passed its tests and CI, but the precheck rejected the PR because an unrelated commit introduced additional documents and lockfile changes. I corrected the branch history to keep only the intended implementation and test changes. I consider this trade-off worthwhile because a focused diff makes the PR easier to review and reduces the risk of merging unintended changes.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/pr-precheck/`.
