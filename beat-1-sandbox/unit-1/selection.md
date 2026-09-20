# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/59

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
Summary

Repo-level facts (apply to all three issues): codepath/pathreview-ai301-fa26-s1 is not archived, pushed 2026-09-16 (4 days ago), 5 recent commits by a human author (Aburke225, most recent 2026-09-16 — well within 30 days). No CONTRIBUTING.md, no AI policy file found (404s on all checked paths) → silence passes. All three issues have zero comments, zero assignees, and no linked/cross-referenced PRs.

┌──────────────────────────────────┬─────────────────┬───────────┬─────────────┬─────────────────────┬──────────────┬─────────┐
│              Issue               │ Community Alive │ Unclaimed │ Repo in Use │ Contribution Policy │ Scope (pref) │ Verdict │
├──────────────────────────────────┼─────────────────┼───────────┼─────────────┼─────────────────────┼──────────────┼─────────┤
│ #61 SQLAlchemy text() fix        │      pass       │   pass    │    pass     │        pass         │     pass     │ accept  │
│ #59 Faithfulness checker wording │      pass       │   pass    │    pass     │        pass         │     pass     │ accept  │
│ #57 Tech detector vendored files │      pass       │   pass    │    pass     │        pass         │     pass     │ accept  │
└──────────────────────────────────┴─────────────────┴───────────┴─────────────┴─────────────────────┴──────────────┴─────────┘

All three clear every required check. Rabackground, wants backend experience,open to moderate challenge):

1. #61 — directly a backend/DB fix (wrapping raw SQL in SQLAlchemy 2.x's text()), a near one-line change
   that plays straight to the Python+SQLperience goal.
2. #59 — Python backend logic in the RAG pipeline; fixing "shared wording" scoring is a bit more
   open-ended (has to decide what "suppo of just patching a line), matching theappetite for a bit of a challenge while staying in one file.
3. #57 — simplest of the three (just exc paths) and comes with a ready-made repro script, but it's an agent tooling utility rather than backend/SQL work, so it fits the stated goal
   least among the three.

[
  {
    "item": "https://github.com/codepath/issues/61",
    "checks": [
      {"name": "Community Alive", "gradeefault-branch commit by human authorAburke225 on 2026-09-16, 4 days before today (2026-09-20)"},
      {"name": "Issue is Unclaimed", "gr "assignees: [], 0 comments, nocross-referenced/linked PRs in timeline"},
      {"name": "Repo in Use", "grade": "ved: false, pushed_at2026-09-16T21:48:27Z, within 90 days"},
      {"name": "Scope", "grade": "pass",one file (api/routes/health.py) and oneroot cause (raw SQL string needs sqlalchemy.text()), no multi-component ask"},
      {"name": "Contribution Policy", "g: "CONTRIBUTING.md and AI policy filesboth return 404; silence passes"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/issues/59",
    "checks": [
      {"name": "Community Alive", "gradeefault-branch commit by human authorAburke225 on 2026-09-16, 4 days before today"},
      {"name": "Issue is Unclaimed", "gr "assignees: [], 0 comments, no linkedPRs in timeline"},                                                                                          {"name": "Repo in Use", "grade": "ved: false, pushed_at2026-09-16T21:48:27Z, within 90 days"},                                                                     {"name": "Scope", "grade": "pass",es one function (_is_supported() infaithfulness_checker.py) and one failing test (test_multiple_context_chunks), no cross-repo/refactor  ask"},
      {"name": "Contribution Policy", "grade": "pass", "evidence": "CONTRIBUTING.md and AI policy fileboth return 404; silence passes"}
    ],                                                                                                    "verdict": "accept"
  },                                                                                                    {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/57",                             "checks": [
      {"name": "Community Alive", "grade": "pass", "evidence": "Default-branch commit by human author Aburke225 on 2026-09-16, 4 days before t
      {"name": "Issue is Unclaimed", "grade": "pass", "evidence": "assignees: [], 0 comments, no linked PRs in timeline"},
      {"name": "Repo in Use", "grade": "pass", "evidence": "archived: false, pushed_at
2026-09-16T21:48:27Z, within 90 days"},
      {"name": "Scope", "grade": "pass", "evidence": "Body names one file (tech_detector.py), one fix
(exclude node_modules/build paths), withand two named failing tests"},
      {"name": "Contribution Policy", "grade": "pass", "evidence": "CONTRIBUTING.md and AI policy files
both return 404; silence passes"}
    ],
    "verdict": "accept"
  }
]
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

`agreement: 13/20 scored items`
`agreement: 3/7 scored items`
`agreement: 7/7 scored items`
`categories: claimed 4/4  clear-accept 8/8  dead-repo 3/3  policy 1/1  scope 2/4`
`agreement: 18/20 scored items  (bar: 18/20: PASS)`

**Issue analysis**

[One scored issue, identified by id (`issue-01` through `issue-20`; the `calib-`
issues are not scored). State your rubric's decision, the gold label, and the
reasoning that produced your rubric's result.]

`issue-09`

My rubric's decision was `accept`, and the gold label was `accept`.

The issue had no current assignee, and its linked PR was `#11627 (closed)`. Under my Issue is Unclaimed check, a closed linked PR does not count as an active claim; the check requires “No current assignee, no open linked PR, and no comment within the last 30 days indicating another contributor is actively working on the issue.” The repository also passed the other required checks, so my verdict rule produced an `accept` decision.

**Check rationale**

[One check from the `rubric.md` uploaded to `tools/issue-select/`, quoted as it is
currently written, with the reasoning behind its current form.]

| Repo in Use | Archived flag, last push to any branch, and latest release | Repository is not archived and has either a push or release within the last 90 days | Required |

I changed this check after my original version required the latest release to be within 30 days. That requirement rejected repositories that were still actively maintained but did not publish releases that frequently. The current check uses both pushes and releases as evidence of recent repository activity, while the archived flag identifies repositories that are explicitly no longer active. I chose a 90-day window so that an active repository does not fail only because it has not published a release within the last month.

**Trade-offs**

[What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

This check gives up the stricter requirement that a repository must have a very recent release. For example, my original check caused `issue-06` to fail Repo in Use because the repository had no release, even though it had recent repository activity. After changing the check to accept a non-archived repository with either a push or release within 90 days, I re-ran the previously failing issues with `--only`, and `issue-06` changed to the correct `accept` result.

The trade-off is that a recent push does not necessarily guarantee that a project is actively releasing or broadly maintained. I accept that limitation because the check is intended to determine whether the repository is currently in use, rather than whether it follows a frequent release schedule.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
3. The anticipated difficulty in claiming it.
]

1. The issue fits to my interest because it works with the Python backend logic in the RAG pipeline. It's a bit more challenging compare to the other two issues I looked at, but I like to take on challenges

2. The verdict identified correctly that the issue is tied to one isolated function and one failed test. I weighed that as preferred because I think it large depends on the developer's skill level and preferences, so it should not be a "mandatory requirement"

3. It's still labeled as a tier-1 challenge, should still be doable

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
