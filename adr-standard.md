# The ADR standard

Agreed 2026-09-05 between the agent maintaining `ai-project-template` and the advisory
agent on the `wordpress-architect` plugin, relayed by the owner. Written down because
until now it existed only in a relay conversation, which is the most fragile place an
agreement can live.

**This document is the source for the decision records that will carry it. It is not
itself a decision record and it does not make anything true in either repository.**

---

## How to read the labels

Every item carries one.

| Label | Meaning |
| --- | --- |
| **IN FORCE** | Written in a file today, in one of the two repositories, and verified by reading it |
| **AGREED** | Settled in this exchange and NOT yet written anywhere. Part 8 names the carrier |
| **HYPOTHESIS** | Rests on one measured pair of records and nothing else. Not a rule |
| **OPEN** | No file on either side answers it. Neither side invented an answer |

Nothing labelled AGREED governs anything yet. That is the reason this file exists. The
carriers are records `0024` through `0028`, listed in Part 8.

---

## Part 1. The shared core

Identical on both sides, adopted verbatim, no local variants.

### 1.1 Location — IN FORCE (framework) / does not reach the plugin repository

`.docs/decisions/` of the owning scope.

The scope rule, from `blueprints/project/PROJECT.md`: project-wide documentation and
decisions belong in `.docs/`; anything affecting one component only belongs to that
component.

**AGREED addition, from record 0025:** a folder nobody declared a scope in the registry
has no decisions of its own. Wanting one is a valid trigger to declare it. Until it is
promoted, a record about such a folder lives in the nearest declared scope's decisions
folder.

**This rule does not reach a repository that has not adopted the framework.** The
`wordpress-architect` repository is not a declared component of `ai-project-template`;
that registry is empty and says so in visible text. Where its records live is its own
decision. What is shared is the record's shape.

**DECIDED by the owner on 2026-09-05:** that repository keeps its own decision records, in
`.docs/decisions/` of that repository, in the shared shape. The same folder name, reached by
its own decision rather than by this rule.

### 1.2 Filename and numbering — AGREED, from record 0026

A record about the folder's own scope: `NNNN-slug.md`. Four digits, zero-padded. Slug
lowercase, hyphenated, English.

A record about a subfolder that has no scope of its own: `<subject>-NNNN-slug.md`, where
`<subject>` is that folder's name as it sits on disk.

Numbering is **per sequence, not per folder**. The scope runs `0001` upward; each subject
runs its own `0001` upward; each without gaps. A record therefore survives promotion of
its subfolder without renumbering, which is the property this form was chosen for.

"Newest last" holds inside a sequence and not across a folder carrying more than one.

Citation: a bare number inside the folder (`0007`), the full stem for a subject record
(`booking-0002`), the path first across a folder boundary (`wp-engine/0011`).

### 1.3 Title line — AGREED

`# NNNN. The decision in one phrase`

No `ADR-` prefix. No colon. The plugin side's `# ADR-00NN: [Decision title]` is dropped.

### 1.4 Header — AGREED

```
**Date:** YYYY-MM-DD
**Status:** <token> <prose>
```

Then a horizontal rule. No YAML frontmatter. No time, only a date: no decision on either
side has ever turned on the hour it was taken.

### 1.5 Status — AGREED

First token from a closed set, lowercase:

`proposed` · `accepted` · `superseded` · `rejected` · `deprecated`

Everything after the token is free prose. Where the status depends on another record, the
prose names it and links it. Supersession lives here and not in a field of its own.

`deprecated` means no longer applied with nothing replacing it. The framework has no
instance. It is in the set because a platform release can overtake a decision without any
decision displacing it, which is a mechanism the plugin side supplied.

**A CONSTRAINT ON WHAT MAY BE PUT HERE, measured rather than assumed.** The Status line is
rewritten when standing changes, and prior content usually does not survive it. Measured
across the framework's own records, of the three whose status names a supersession, **two
lost everything the line previously held**: `0002` no longer carries the word `accepted` at
all, and `0011` retains nothing but its supersession clause and a date. The third, `0003`,
is the counter-example and is recorded as one: "the cut stands; its four jobs are superseded
by the single test in `0004`" keeps its standing beside the supersession.

So content *can* survive a rewrite and nothing requires it to, and in two cases of three it
did not. **Status prose is therefore unreliable for any durable fact and no such fact may be
stored there.** The weaker premise carries the same conclusion, which is why the
counter-example is named rather than left out.

### 1.6 The record's parts — AGREED

**The count is dropped, because it went stale the first time membership moved.** An earlier
draft of this document called these "the seven fields" and meant a different seven: the
revisit trigger was an item and `Date` was not. Restructuring 1.6 to state the section order
once moved the revisit trigger to where it belongs, as the last line of Consequences, and
brought `Date` into the enumeration. The total is unchanged and the membership is not, which
is exactly the trap a count sets. **Anyone citing "the seven fields" from an earlier reading
means the older membership.** The parts are named below and nowhere counted.

**Two header fields and five sections. The sections appear in the order below, and Part 7 is
the single statement of that order.** Earlier drafts of this document stated the order twice
and differently, which mattered because 2.3 makes order checkable.

Header: `**Date:**`, then `**Status:**`.

1. **Context**, the situation and the constraints that forced the decision.
2. **Decision**, in one sentence, then the scope it covers and the boundary it creates or
   changes.
3. **Options considered.** What was examined, and for each what it buys and how it fails.
   Where examination found no viable alternative, say so and say what was examined to
   establish it.
   **No count is specified, deliberately.** A count catches the wrong quantity: a record
   with two options, one of them a strawman, passes a count and is exactly the advocacy the
   field exists to prevent. The test is whether the record says what was examined.
4. **Consequences**, including what it costs and what it gives up, and the risks accepted
   with no mitigation. The recovery path sits here rather than in a section of its own.
   **It ends with a revisit trigger**: a date, or the condition that would reopen the
   decision. The trigger is a line, not a section of its own.
5. **Origin**, naming the channel a decision arrived through and not its author.

**Not adopted, and the reason for each.** `Owner`: constant in a single-owner repository,
and a constant field is noise. `Evidence and links` as a link list: the local sense of
evidence is what was measured against what control, which is prose belonging to Context and
Consequences. `Delivery and recovery` as its own section: folded into field 4.

### 1.7 Stated absence is a valid filling — AGREED

Every field is present in every record. A stated absence fills it.

"No viable alternative existed: X is the only mechanism the platform offers here" is one
line, it is informative, and it is a properly filled options field. "No revisit trigger:
this holds unless the platform changes X" likewise.

**Where the rule stops.** It applies wherever an absence would otherwise read as correct. A
missing top-level field leaves a record that looks complete, so its absence has to be
stated or it is invisible. A missing sub-heading inside a field that is present and filled
with prose is not invisible. **The rule does not recurse by default.**

### 1.8 Condition on shipping the options field — AGREED

Any form carrying the options field also carries the instruction to ground every statement
in the source and to say where the source does not show something.

The reason is in Part 5.4. The condition is checkable by inspecting the form, which is what
makes it usable rather than an intention.

### 1.9 No Follow-up section — IN FORCE

Obligations a decision creates go to the backlog.

`## Follow-up` appears in exactly one record of 26, which is `0001`. It is the longest
section of that record, which is why it read as part of the form to a reader sampling one
document. `0001` was committed 2026-08-09; `backlog.md` was created 2026-08-25. The
function moved to the backlog when the backlog existed. It was never cut from a form,
because it was never in one.

### 1.10 Accepted records are not edited in place — IN FORCE, as practice

Corrections and changes arrive as new records that link back. The superseded record's Status
gains a sentence and a link.

Stated as practice and not as a prohibition, because that is what the framework holds. No
written rule forbids editing an accepted record.

**DECLARED DIVERGENCE.** The plugin side holds this as a RULE rather than as practice,
deliberately, on the ground that an appended correction makes one record say two things.
Same behaviour, different force. This item is therefore not shared in the way the rest of
Part 1 is, and it is recorded here rather than left to read as shared.

Live examples: `0002` superseded by `0003`; `0011` superseded in part by `0015`; `0023`
supersedes part of `0011`.

### 1.11 No index file — AGREED as argued, previously unresolved

There is no index of decisions, and the absence is argued rather than merely unresolved.

A bare filename index writes what a folder listing already shows, which the framework's
oldest rule forbids: a document carries what cannot be seen. An index carrying status and
one-line summaries becomes a second place where status lives, and a fact in two places is a
fact that will disagree with itself.

**What stays open is not indexing but DISCOVERY**: how a reader finds the record that
governs a question. Today that is answered by reading, and no better answer has been
proposed.

---

## Part 2. Where the two sides differ, and the reason

Not compromises. Each has a reason that holds on one side and not the other, so a single
rule would be wrong somewhere.

### 2.1 When a record is owed

**Shared criterion — AGREED:** a record is owed when the trade-off outlives the task that
produced it. Not when the change felt large. A choice made in ten minutes can bind
migration, backup and export for years, and how long it took is not evidence about how long
it lasts.

The plugin side additionally enumerates what typically qualifies in WordPress work: a new
module boundary, a public API, a storage surface, an external provider, a queue, an auth
model, a shared UI pattern, deployment behaviour, and its high-risk classes.

**That list is an elaboration of the criterion and never a competing trigger. If the list
ever yields a different answer from the criterion, the list is wrong and the criterion
stands.** An elaboration that can overrule what it elaborates is a second trigger wearing a
different name.

### 2.2 The six consequence dimensions

The plugin template breaks Consequences into data and migration, APIs and consumers,
security and privacy, performance and reliability, operations and support, testing and
release.

Under rule 1.7 these cannot be enforced as absences, since the rule does not recurse. **They
survive as a coverage prompt inside the plugin's command, not as structure in the record.**

This is a real loss and it is named as one. It earns its place for a second reason: if the
redirection hypothesis in Part 5.2 holds, a coverage prompt on Consequences is the
counterweight to the field set's own side effect, on the side that has a command to carry
one. The framework has no command and so cannot.

### 2.3 Mechanical verification

The framework has nothing executable: no CI, no workflow files, no scripts. Verified by
looking. The plugin side has a documentation checker and a CI workflow, neither of which
touches records today.

So the plugin side is the only one that could ever check the shared format mechanically.
The asymmetry is deliberate rather than accidental.

**The boundary any such checker must state in its own output:** a check inside a record can
reach the header lines, the Status first token against the closed set, the presence and
order of the sections, and a revisit line at the end of Consequences. It cannot reach
whether an option is real, whether a cost is honest, or whether a search happened.

> Structural conformance only. A passing record is a record shaped correctly, and that says
> nothing about whether its options are real or its costs honest.

---

## Part 3. The addition rule

### 3.1 The rule — AGREED

> The header fields and sections named in 1.6 are shared and carry the same meaning on both
> sides. A side may carry an additional HEADER field where a written rule of its own domain
> requires a fact no shared field holds. An added field may not restate, replace or redefine a
> shared field or section, and it is declared to the other side when added.
>
> **Identical shape is not the goal. Identical meaning of the shared fields is.**

The rule exists because defending byte-identical shape produced two wrong placements in a
row: an approver first pushed into Consequences prose, where a reader will not look for it,
then into Status prose, which is rewritten wholesale and would have deleted it.

### 3.2 First instance: `**Approval:**` on the plugin side — AGREED

Declared by the plugin side and checked against the rule item by item. It restates no shared
field, holds a fact none of them holds, is required by a written domain rule, and was
declared.

**Present on every record, not only on high-risk ones.** A field appearing only on high-risk
records makes a missing line on a high-risk record read as correct, which is the case rule
1.7 exists for and the case where a silent failure costs most.

Two forms, both carrying something a reader can contradict:

```
**Approval:** <name>, as a high-risk change under domain rule 14 (payment flow)
**Approval:** not required; a documentation change, none of the high-risk classes in domain rule 14
```

The not-required form makes a positive claim about what the change is, in the same
vocabulary. A bare "not required" asserts an absence, can be neither confirmed nor
contradicted, and becomes a line nobody reads.

The not-required form above was proposed by the framework side and adopted verbatim by the
plugin side, replacing a bare "not required; not one of the high-risk classes".

`Owner` is not adopted on either side. Its only written backing on the plugin side sits
inside the command being rewritten, and **a rule whose only backing sits inside the artefact
being rewritten cannot constrain that rewrite.** It is a question inside the work, not an
input to it.

### 3.3 Second instance: `**Review:**` on the plugin side — AGREED, conditionally

Declared by the plugin side. Present on every record, on the same argument as `Approval`.

```
**Review:** Claude/Code (Opus 5), independent review of the decision, through the owner as relay
**Review:** ChatGPT/Codex (Terra), read for cost and failure modes
**Review:** Alex, read for scope and cost
**Review:** none; drafted and accepted in one session
```

**THE CONDITION.** Rule 3.1 requires a written rule of the side's own domain. The backing
cited is `PRINCIPLES.md`, "Change through review", which governs domain guidance and not
records. The plugin side named this itself and will extend `domain/14` by one line **before
the field exists**. Until that line lands the field is declared and not yet justified. The
sequencing is the plugin side's own and it is the right one.

**THE BOUNDARY AGAINST `Origin`, which has to be stated or the two fields will drift into
each other.** `Origin` names the channel a decision ARRIVED through, and in the framework
that channel is frequently a review relayed by the owner. `Review` names who scrutinised the
RECORD after it was drafted. A record can arrive through no review and then be reviewed, or
arrive through a relayed review and never be reviewed as a record. They are separable, and
only because that sentence exists.

**ON NAMING A MODEL.** The field records the reviewing model as configured or selected for
that review, and claims nothing about which weights served the request. That distinction is
the plugin side's and it is not theoretical: at least one runtime states plainly that the
serving model can differ from the configured one and can change mid-session, which the
framework side can confirm from its own environment. Fixing the meaning once in the field's
definition is what lets an individual record carry the value with no hedge.

---

## Part 4. Open gaps, on both sides — OPEN

Written down so that silence on both sides is not mistaken for agreement. Neither side
invented an answer.

- **Permitted status transitions.** Not written on either side.
- **Who may change a status.** Not written on either side. The framework's practice is that
  the owner decides and a session drafts. Nothing records it.
- **Reviewer and approver ROLES.** Undefined on both sides. The plugin side now carries a
  field for each fact, `Approval` and `Review`, which records what happened on a given
  record and still says nothing about who may occupy either role, who may decline, or what
  a review must cover to count as one. **A field is not a role.** This gap is narrower than
  it was and it is not closed.
- **Discovery.** See 1.11.
- **Nothing reads inside a record**, on either side. The framework's three prompt-driven
  checks verify that a decisions folder is reachable and declared; none opens a record. The
  plugin side has no check at all.

**A shared format is therefore a shared habit and not a contract either side can verify
mechanically.** That is the frame's own caveat and both sides carry it.

The first three are process rather than format. They are the owner's to settle and not two
agents' to agree.

---

## Part 5. Hypotheses — one measured pair, and nothing else

On 2026-09-05 one architecture decision was recorded twice, in parallel, in isolated
sessions, from instructions differing by exactly two insertions. Everything in this part
rests on that pair and on nothing else. **One pair is one observation and settles nothing on
its own, in either direction.**

Registered before the run and held: the treatment named an alternative the control did not;
the treatment named a revisit condition the control did not; both arms reached the same
decision.

### 5.1 The effect is on evaluation, not on naming — HYPOTHESIS

The difference between the arms is mostly not which alternatives are named. It is whether
they are evaluated. The control named genuine candidates and evaluated none of them.

**This was not the registered prediction**, which was written about naming. Reading the
result as support for the field set requires a prediction nobody registered. **The next pair
registers evaluation rather than naming.**

Measured: treatment four alternatives in its options section, three carrying explicit buys
and fails, the fourth declared not live by the record itself. Control two alternatives named
in prose, none evaluated.

### 5.2 The field set may redirect evaluation rather than add it — HYPOTHESIS

The control's Consequences ran 612 words, the largest single section in either document,
against 421 in the treatment. The control spent its evaluative effort on the consequences of
what was chosen; the treatment moved a large part of that effort onto what was not.

**Word counts cannot separate redirection from compression.** A shorter section is equally
consistent with content moved elsewhere and with the same content written more tightly. The
next pair puts a content question to the judge about both sections.

If it holds it changes what the field is for. A field that adds analysis and a field that
moves it are different products.

### 5.3 The shared sections contract — HYPOTHESIS

Measured per section, headings excluded: Context 365 against 461, Decision 99 against 108,
Consequences without the revisit block 421 against 612, Origin 68 against 143. Shared total
953 against 1324, a difference of minus 371, against 451 words of new sections. Whole
documents 1468 against 1367.

Shorter in all four shared sections is **one observation and not four**: a drafter working to
a length budget shortens everything at once.

Prediction for a next pair, falsifiable with no new instrument: under the field set the
shared sections contract while whole-document length holds roughly constant.

### 5.4 The grounding instruction is load-bearing and untested — KNOWN UNTESTED DEPENDENCY

The treatment did not fabricate a decision history where its source recorded none. It
labelled its reconstruction. The control disclosed the same gap unprompted, **with no options
field at all**.

So the disclosure is **not attributable to the options field**. That is the negative and it is
established. The positive half, attributing it to the grounding instruction both arms
carried, is not separated from the drafter's own disposition, because no arm lacked the
clause.

It will not be separated, because isolating it needs an arm no form would ship. Recorded as a
known untested dependency rather than as an open question, so that nobody reopens it every
time the clause turns up in a result.

**The tell that would reopen it:** a record asserting a decision history its source does not
support, appearing under a form that carries the clause. That would show the clause is not
doing what it is credited with, and it arrives without anyone running anything.

### 5.5 Watch item: the arbitrary date — HYPOTHESIS, with both closing conditions

The treatment's three revisit conditions were reasoned from the material. Its scheduled date,
one year from the drafting day, was derived from nothing. The field's wording, "a date, or
the condition", may invite a date that reads as scheduling and carries no information.

- **Closes as unfounded** if two or three further records under the current wording produce
  dates deriving from something real: a contract term, an end of life, a season.
- **Closes as confirmed**, and the field changes to prefer a condition and admit a date only
  where derived, if two or three further records produce dates deriving from nothing.

Either close ends the item. A watch item without a stated closing condition is a permanent
doubt rather than a pending question.

### 5.6 What the pair does not license

It does not close the framework's condition for shipping a template into `blueprints/`, which
requires at least one further pair from outside WordPress.

Confounds carried with every figure above: one pair, one subject, one domain, a different
repository and different authors from the framework's own 26 records. The subject was named
after the predictions were read, by a side holding a position. The judge was a model and
could not be blind to which record carried an options section, since the arms differ visibly
by construction.

---

## Part 6. Method findings from the exchange

Not about ADRs. About how the two sides worked, and worth keeping because both were paid for.

**A claim made without opening the thing it is about will be wrong often enough to matter.**
This is the class both sides produced most, and neither side produced fewer. It covers
generalising a form from the one record of 26 that had a Follow-up section; taking a count of
alternatives from a judge's discussion instead of from the record's own section; inferring
that a document was shorter from line counts across different wrap widths; carrying another
side's figure into a task without checking it; and preparing a question about a protocol file
that could simply have been opened. **Every instance on both sides was caught the same way,
by the other side asking to see the source rather than the summary.** No count is given here
for the same reason 1.6 gives none.

**A claim can outrun its instrument while pointing the right way.** "Three of three superseded
records lost everything" was measured as two of three with one counter-example. The conclusion
held on the weaker premise, and the weaker premise was always the load-bearing half. State the
premise the measurement supports, not the one the conclusion would enjoy.

**A rule whose only written backing sits inside the artefact being rewritten cannot constrain
that rewrite.** It is a question inside the work, not an input to it.

**Everything that got settled was settled by opening a file.** The options count, the control's
count, the durability of the Status line, the per-section word counts, the Follow-up census,
the material's freedom from leaks, the prompt diff, the registry's contents, the absence of any
CI. **And every question still open is one no file answers**: status transitions, who may change
a status, reviewer roles. The division is exact. Argument moved positions in this exchange. It
never closed anything.

---

## Part 7. The skeleton

```markdown
# NNNN. The decision in one phrase

**Date:** YYYY-MM-DD
**Status:** accepted

---

## Context

The situation and the constraints that forced the decision. What was true before, what could
not be changed, what was at stake.

## Decision

The decision in one sentence. Then the scope it covers and the boundary it creates or changes.

## Options considered

What was examined, and for each what it buys and how it fails. Where examination found no
viable alternative, say so and say what was examined to establish it.

## Consequences

What follows, including what it costs and what it gives up. The risks accepted with no
mitigation. The recovery path, where there is one.

**Revisit** when <condition>, or by <date>.

## Origin

The channel the decision arrived through, not its author.
```

### The plugin side's form, with both added header fields

Added fields sit after `Status`, which keeps the shared header block contiguous at the top.
Nothing else differs.

```markdown
# NNNN. The decision in one phrase

**Date:** YYYY-MM-DD
**Status:** accepted
**Approval:** not required; a documentation change, none of the high-risk classes in domain rule 14
**Review:** none; drafted and accepted in one session

---

## Context
```

### The instruction

The instruction that produces such a record carries, in addition: *ground every statement in
the source, and where you rely on something the source does not show, say so and say what
would confirm or refute it.* That sentence is a condition on the options field, per 1.8.

---

## Part 8. What is not yet written, and where it goes

Nothing in Parts 1 to 6 marked AGREED or HYPOTHESIS exists in any repository file as of
2026-09-05. Planned:

| Carrier | Content |
| --- | --- |
| Record `0024` | Its own enumeration of six, the razor split, the shipping question. **Drafted, written to disk, not committed.** Its enumeration is the older membership and `0027` supersedes that part of it |
| Record `0025` | The location rule and the lazy path. **Drafted, written to disk, not committed** |
| Record `0026` | Filename, numbering, citation. **Drafted, written to disk, not committed** |
| Record `0027` | Status as a header field; stated absence and its boundary; the restatement of the options field; the addition rule; the constraint on Status prose; the argued index absence |
| Record `0028` | The measurement condition rewritten: arms differing by one variable, the variable being the field set, the prediction about evaluation rather than naming |
| `.docs/predictions/` | 5.1, 5.2, 5.3 as pre-registrations for the next pair |
| `.docs/backlog.md` | The cold-start component question, the `handover.md:90` amendment, the template measurement, the plugin-side task, the watch item in 5.5 |
| Plugin side | Its own records, in `.docs/decisions/` of that repository, in the shape above. Location decided by the owner 2026-09-05. Plus the one line in `domain/14` that `Review` waits on |

Two verified anchors on the plugin side, cited in this exchange:
`commands/wp-adr.md:38`, the options mandate this standard deliberately does not carry,
confirmed independently by the framework side; and `agents/wordpress-architect/AGENT.md:54`,
the unconditional source-label requirement, cited by the plugin side and not independently
confirmed.
