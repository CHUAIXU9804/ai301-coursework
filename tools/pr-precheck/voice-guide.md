# Voice guide: how I talk upstream

<!--
THIS IS THE PART YOU WRITE (new this week). Live mode reads this file
before any comment of yours goes out the door; eval mode ignores it
entirely, because your voice is yours and carries no gold labels.

This is not etiquette. "Be polite and concise" is advice for everyone
and therefore rules for no one. Write rules YOU need, in your own
words, each one concrete enough that the skill can hold a draft
against it and say which rule it breaks.

Three sections. Fill all three.
-->

## Who I am in threads

<!-- 2-3 lines. Who is talking when you comment on an issue: your
experience level stated plainly, what you are doing in this repo, what
readers can expect from you. This is the register your rules protect. -->

I'm a junior developer or a relatively new contributer who is building experience with open source project. When I comment on issue, I focus on reproducing the reported behavior and sharing what I observed. I try to distinguish my observations from conclusions I’m not yet able to verify.

## Rules I write by

<!-- 3-5 rules, drafted from the lecture's slide-12 moment. Each rule
needs a wrong/right pair from your own hand: one line you might
actually have written that breaks the rule, and the line you would
post instead. The pair is what makes a rule executable; a rule without
one is a wish.

Format each rule like this:

### Rule: <short name>

<The rule, one or two sentences.>

- Wrong: "<a line that breaks it>"
- Right: "<the line to post instead>"
-->

Rule: State what I observed
Describe what I actually observed instead of making a stronger claim than my evidence supports.

- Wrong: "This issue is definitely caused by the authentication module."
- Right: "I reproduced the reported error when attempting to log in with these steps."

Rule: Separate results from assumptions
If I haven't verified the cause of a behavior, I don't present my interpretation as a fact.

- Wrong: "The API is broken and is causing the request to fail."
- Right: "The request returned a 500 response during my reproduction attempt; I haven't confirmed the underlying cause."

Rule: Be specific about reproduction status
Clearly say whether I reproduced, partially reproduced, or could not reproduce the reported behavior.

- Wrong: "Everything seems fine for me."
- Right: "I couldn't reproduce the reported error on macOS 15.6 using version 2.4.1."

Rule: Report differences that could matter
When my result differs from the issue, mention relevant differences instead of assuming they are irrelevant.

- Wrong: "I can't reproduce this issue."
- Right: "I couldn't reproduce this issue on Python 3.12. My environment differs from the reporter's Python 3.11 environment."

## Things I never post

<!-- A short list. Promises you cannot keep, tones you refuse,
shortcuts you know you reach for when tired. The skill quotes this
list back at you when a draft crosses it. -->

- Blaming the reporter/maintainer for an incomplete or incorrect report
- Claims that something “works” or "doesn't work" without stating the environment or conditions I tested
- Statements that dismiss an issue solely because I couldn't reproduce it
