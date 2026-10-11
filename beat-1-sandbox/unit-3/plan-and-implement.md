# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

[Your GitHub username, exactly as it appears on your profile - no @, no
profile URL. Your comment upstream is identified by this name, and it is
the only thing that ties it to you. Several students may plan the same
house issue, so this is what keeps their comments off your score and
yours off theirs.]

CHUAIXU9804

**Plan comment**

[Link to the comment where you posted your plan on the issue. Use the comment's own
permalink. **Then paste the text of that comment underneath the link** — the pasted text is
what this field is graded on, so copy across what you actually posted.]

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/59#issuecomment-6114585180

I reproduced the faithfulness checker issue in #59 and documented the results in my earlier repro comment.

The reproduction showed:

> **Expected:** The checker should recognize feedback mentioning Python, JavaScript, and Docker as supported by context containing those same skills, producing a score above 0.5.
>
> **Actual:** `test_multiple_context_chunks` returned `0.0` instead (`E assert 0.0 > 0.5`), with `claims_count=1 score=0.0 supported_count=0`.

Based on the reproduction and code inspection, the likely cause is the tokenization and fixed overlap threshold in `FaithfulnessChecker._is_supported`. Using `.split()` retains punctuation on tokens such as `python,`, preventing matches with `python` in the context. After stop-word filtering, the remaining overlap falls below the required two matching words.

The proposed fix is to normalize tokenization and use a length-aware overlap threshold in `rag/evaluator/faithfulness_checker.py`. I'll also adjust `_extract_claims` to retain short claims and update the affected tests in `tests/unit/test_faithfulness_checker.py`. The change will remain limited to lexical matching and claim extraction, without introducing semantic matching or changing the checker's return contract.

I'll verify the fix by rerunning the original reproduction, checking supported and unsupported control cases, and running the faithfulness checker and broader unit tests. I expect the original failing test to score `1.0`, while unsupported claims should remain unsupported.

One remaining question is whether the partial-support test, which would require clause-level splitting, belongs within #59. I'm leaving that larger change out of scope for now. The short-claim threshold also needs validation to avoid introducing false positives.

I'd appreciate any feedback on this approach before implementation.

---

## Your branch

**Branch**

[The name of the branch you built the change on, exactly as it appears in your fork. The
naming shape is a type prefix, then the issue number, then a short description. **The issue
number in the branch name must be the number of the issue you claimed** — a name carrying
any other number does not satisfy this field.]

fix/59-faithfulness-checker

**Evidence**

[Your Unit 2 reproduction steps re-run against the built change: the before, then the
after. Paste both, including the commands you ran and their output.]

Before:

After:

Before:

Command:

```
pytest tests/unit/test_faithfulness_checker.py::TestFaithfulnessChecker::test_multiple_context_chunks --runxfail -v
```

Output from Unit 2 reproduction:

```
E assert 0.0 > 0.5
claims_count=1 score=0.0 supported_count=0
```

The test failed because the faithfulness checker returned 0.0 for feedback describing Python, JavaScript, and Docker experience, even though all three skills appeared in the context.

After:

Command:

```
.venv/bin/python -m pytest tests/unit/test_faithfulness_checker.py -v -rx
```

Relevant output:

```
test_multiple_context_chunks PASSED
test_multiple_claims_varying_support PASSED
test_is_supported_ignores_attached_punctuation PASSED
test_is_supported_short_claim_with_one_matching_word PASSED
test_is_supported_short_claim_without_matching_word PASSED
test_is_supported_long_claim_needs_two_matching_words PASSED
test_extract_claims_keeps_short_claims PASSED

25 passed, 2 xfailed in 0.36s
```

The original failing test now passes, along with the new regression tests for punctuation handling and short-claim matching.

Additional regression verification:

Command:

```
.venv/bin/python -m pytest tests/unit -q
```

Output:

```
382 passed, 51 xfailed, 3 warnings in 11.91s
```

Command:

```
.venv/bin/python -m pytest tests/unit/test_faithfulness_checker.py::TestFaithfulnessChecker::test_multiple_context_chunks --runxfail -v
```

Output:

```
========================== test session starts ==========================
platform darwin -- Python 3.11.15, pytest-9.1.1, pluggy-1.6.0 -- /Users/cxu/PycharmProjects/AI_Projects/pathreview-ai301-fa26-s1/.venv/bin/python
cachedir: .pytest_cache
benchmark: 5.3.0 (defaults: timer=time.perf_counter disable_gc=False min_rounds=5 min_time=0.000005 max_time=1.0 calibration_precision=10 warmup=False warmup_iterations=100000)
hypothesis profile 'default'
rootdir: /Users/cxu/PycharmProjects/AI_Projects/pathreview-ai301-fa26-s1
configfile: pyproject.toml
plugins: cov-7.1.0, asyncio-1.4.0, benchmark-5.3.0, hypothesis-6.168.2, pytest_httpserver-1.1.5, platformdirs-4.12.0, anyio-4.15.1
asyncio: mode=Mode.STRICT, debug=False, asyncio_default_fixture_loop_scope=None, asyncio_default_test_loop_scope=function
collected 1 item

tests/unit/test_faithfulness_checker.py::TestFaithfulnessChecker::test_multiple_context_chunks PASSED [100%]
```

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

```
# eval run written by run_eval.py at 2026-10-11T21:13:42Z
# model: sonnet (pinned)
# graded: /Users/cxu/.claude/skills/plan-check
# packages: 20 scored
#   rubric.md  sha256:183078525a1bc97a
#   evidence-guide.md  sha256:e5b0cca8ae5dfbbb
#   procedure.md  sha256:8202a55105322659
#   SKILL.md  sha256:4688d0d0f4cf6cb3
#
grading 20 package(s) with rubric.md + evidence-guide.md + procedure.md, model sonnet, 5 worker(s)...
  pkg-03: accept
  pkg-02: accept
  pkg-04: reject
  pkg-01: reject
  pkg-05: accept
  pkg-10: reject
  pkg-09: accept
  pkg-07: reject
  pkg-06: reject
  pkg-08: accept
  pkg-12: reject
  pkg-13: accept
  pkg-11: reject
  pkg-15: reject
  pkg-14: reject
  pkg-16: reject
  pkg-17: reject
  pkg-18: reject
  pkg-19: reject
  pkg-20: reject

item    category           gold    verdict  agree  note
pkg-01  wrong-cause        reject  reject   yes    
pkg-02  clear-accept       accept  accept   yes    
pkg-03  clear-accept       accept  accept   yes    
pkg-04  thread-convention  reject  reject   yes    
pkg-05  clear-accept       accept  accept   yes    
pkg-06  scope-creep        reject  reject   yes    
pkg-07  wrong-cause        reject  reject   yes    
pkg-08  clear-accept       accept  accept   yes    
pkg-09  clear-accept       accept  accept   yes    
pkg-10  unbuildable        reject  reject   yes    
pkg-11  wrong-cause        reject  reject   yes    
pkg-12  scope-creep        reject  reject   yes    
pkg-13  clear-accept       accept  accept   yes    
pkg-14  clear-accept       accept  reject   NO     failed: uncertainty-handling, regression-awareness
pkg-15  scope-creep        reject  reject   yes    
pkg-16  wrong-cause        reject  reject   yes    
pkg-17  unbuildable        reject  reject   yes    
pkg-18  unbuildable        reject  reject   yes    
pkg-19  scope-creep        reject  reject   yes    
pkg-20  thread-convention  reject  reject   yes    

categories: clear-accept 6/7  scope-creep 4/4  thread-convention 2/2  unbuildable 3/3  wrong-cause 4/4
agreement: 19/20 scored items  (bar: 18/20: PASS)
```

**Package analysis**

[Pick one scored package (`pkg-01` through `pkg-20` — the four `calib-` packages are never
scored). Name it by id, say what your rubric decided and what the gold label said, and
explain why your rubric read it that way.]

For pkg-14. The package evaluation returned reject, while the gold label was accept, failing uncertainty-handling and regression-awareness. The plan left exact function locations unresolved but proposed using debug logs to identify them. It also acknowledged the risk of consuming legitimate keystrokes and proposed limiting input handling to OSC responses. The rejection may have been overly strict because the plan included reasonable investigation and validation steps.

**Check rationale**

[Quote one check from the `rubric.md` you uploaded to `tools/plan-check/`, exactly as it reads now.
Then say why it reads that way — what you revised to get there, or what you rejected in
favour of it.]

```
| uncertainty-handling | The plan's causal claims, assumptions, unresolved questions, and proposed validation steps compared against the Repro evidence and repo-facts block                                | Pass if assumptions essential to the solution are supported by available evidence or explicitly identified as unverified with a way to validate them before they affect implementation. Fail if an unsupported assumption is presented as confirmed, or an unresolved question could materially change the proposed fix without a validation step                                                                                     | Required  |
```

I designed this check to distinguish evidence-supported conclusions from assumptions that still need verification. A plan should not automatically fail simply because it contains uncertainty, since some implementation details may remain unresolved during planning. However, uncertainty that could materially change the proposed fix needs an explicit validation step. This makes the check focus on whether the plan handles uncertainty responsibly rather than whether every detail is already known.

**Trade-offs**

[Every check gives something up. Any one of these is a complete answer: a package whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

The uncertainty-handling check allows plans with unresolved assumptions to pass when those assumptions are explicitly identified and accompanied by appropriate validation steps. This avoids rejecting potentially workable plans simply because some details cannot be confirmed before implementation.

The trade-off is that a plan may pass even though its proposed solution has not yet been fully validated. The check evaluates whether uncertainty is acknowledged and addressed, not whether every assumption ultimately proves correct. I accepted this limitation because requiring complete certainty during planning would be unnecessarily restrictive.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
