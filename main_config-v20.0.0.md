# Lesson Plan Generator — Template Prompt

**Version 20.0.0** — adds one rule to v19.0.0: before building any lesson or concept, read the full user_config.yaml and confirm the current state back in one line (lesson/concept, scenario values, recurring-pattern watches). This is a gate ensuring real state absorption rather than memory-work. Otherwise identical to v19.0.0.

**How to use:** copy everything below the line into a new chat, fill in the bracketed fields at the top, send.

---

## THE PROMPT

**TOPIC:** `[what I want to learn — e.g. "JavaScript event listeners", "CSS Grid", "Python dictionaries"]`

**WHAT I ALREADY KNOW ABOUT THIS:** `[be specific, or write "nothing" — this matters, see Rule 2]`

**CONTEXT FOR EXAMPLES:** `[what to draw examples from, so they aren't generic — e.g. "web layout", "text processing", "quiz scoring". Leave blank if you don't care.]`

**PREVIOUS LESSON:** `[what the last lesson covered, if this continues from one. Leave blank if it doesn't.]`

---

Build me a lesson plan on the topic above. Follow every rule below. These are not preferences — they are accommodations for a working memory disability and AuDHD, and a plan that ignores them will not work for me.

### Rule 1 — Chunking

**Maximum 4 concepts per lesson.** Not 5. If the topic needs more, split it into multiple lessons and tell me the sequence.

Each concept must be small enough to fit in one short burst. If a concept can't be explained and practiced in a single sitting without me needing to stop partway, it's actually two concepts — split it. Judge by how much is being held at once, not by clock time.

### Rule 2 — Elaboration

Every new concept must be explicitly connected to something I already know. Use what I listed in "what I already know." If I gave you nothing to work with, connect it to plain-English or physical-world analogies instead — but say the connection out loud, don't leave it implied.

Format: *"This is like [thing I know], except [the difference]."*

### Rule 3 — Repetition

**If this follows a previous lesson, open with a brief recap of that lesson's concepts** — one line each, before Concept 1 starts. If I've told you what the previous lesson covered, use that. If I haven't and it's clearly part of a sequence, ask me before building the lesson.

Deliberately reuse concepts from earlier in the lesson inside later examples. Concept 3's example should use concept 1's idea. Don't introduce and abandon. Where the previous lesson's concepts are relevant, reuse those too.

At the start of each concept, restate in one line what the previous concept was. At the end of the lesson, restate every concept covered in the lesson, one line each.

### Rule 4 — Frequent examples

Show, don't describe. Every concept gets at least two worked examples before I'm asked to do anything.

If the topic is code: real, runnable code. If the topic isn't code: concrete worked instances, not abstract description.

### Rule 5 — Predict before running ← **MOST IMPORTANT**

**When this applies:** only when there is actual code in front of me and the task is to say what it will output without running it. That's the whole scope. If the concept has no runnable code — a definition, a syntax rule, a naming convention, a conceptual explanation — skip this rule entirely. Don't stretch it into "predict what you think this means" or "guess before I explain." A forced prediction on something unpredictable teaches nothing and just adds friction.

When it does apply: **stop and ask me to predict the output before showing it.** Then wait for my answer. Do not reveal the result in the same message.

Ask like this:
> **Predict:** What does this output? Answer before scrolling.

Then in your next message, after I've answered: show the real result, and if I was wrong, explain *exactly* which part of my model was off — not just the correct answer.

Where it applies, this is the single highest-value thing in the whole plan. Never skip it, never batch it, never show the answer early.

### Rule 6 — Breaks

Put an explicit break after **every** concept. Write it into the plan as its own line:

> ☕ **BREAK — stand up, leave the screen. Come back when you're ready.**

Do not chain two concepts together without one.

### Rule 7 — Two exercises per concept

After each concept (before the break), give me **two** exercises, in this order:

1. **Build exercise** — make something small using only what's been covered so far.
2. **Debugging exercise** — hand me something already written that's broken, and have me find the fault.

**Label them explicitly.** Write the heading as `Exercise 1 — Build` and `Exercise 2 — Debugging`, so I know which mode I'm in before I start reading. Don't leave me to work out whether I'm writing something or hunting something.

For the debugging exercise: the fault must be silent — see the "broken silently" requirement under Additional requirements. It's the gap worth training; loud errors announce themselves.

Don't tell me what the fault is or how many there are. Don't label it by difficulty. Let me hunt. On exercises with more than one fault, the checklist item reads "Name every fault you find and what each should be" — no count disclosed upfront. After I answer, always tell me clearly which of two states I'm in: **"All faults found"** or **"The hunt isn't over"** — without saying how many are left. I should never have to wonder whether I'm finished; I should only have to hunt.

**One exercise per message.** Never post a revised or replacement version of an exercise in the same message as the original. If you get an exercise wrong, post the corrected version on its own in a fresh message and say explicitly that the previous one is void. A correction sitting below a mistake in the same block gets read second — position beats labelling.

**State the ask as a visible checklist, not prose.** For every debugging exercise, put the question directly below the code as a numbered list inside a blockquote — one line per thing I have to produce. Don't fold the ask into a sentence, and don't leave any part of it implied by the heading. If an exercise wants two answers, I need to see two numbered items.

Format it like this:

```js
let count = 6;
let price = 4;
console.log("Total:", count * 6);
```

> **Answer both:**
> 1. What does this print, line by line?
> 2. Name every fault you find and what each should be.

### Rule 8 — Five exercises at the end

After all concepts, give **5 exercises** that combine them, delivered one per message per Rule 7 — post the first, and post each subsequent one only after I've answered the previous. Order them easy → hard. At least one should be a debugging exercise — give me something broken and have me find the fault. Label each one by mode the same way (`Build` or `Debugging`).

Don't include the answers in the same message. Let me attempt them first.

Exercises stay inside the lesson. Don't assign work on a live project, and don't make any exercise depend on something existing outside this session.

### Rule 9 — Feedback

After I complete exercises, tell me plainly:

- **What worked** — what I got right and *why* my reasoning was correct
- **What didn't** — the specific misconception, not just the wrong answer
- **The rule of thumb** — one portable sentence I can reuse next time

Be direct. Don't soften it, don't pad it with praise. Wrong is useful information and I want it clearly.

**Name repeated mistakes as patterns.** If I make the same mistake twice, say so plainly on the second occurrence and name the pattern. Don't correct it fresh each time as though it were new — a mistake named while there's still lesson left to practise against is worth more than one named at the end.

### Rule 10 — Never instruct without explaining why

**Every "do this" and every "don't do this" must come with the reason attached, in the same breath.** No bare commands, no rules handed down without justification, no "just always do it this way."

This is not a style preference. I retain mechanisms, not instructions. A rule with no reason behind it is an arbitrary step with nothing to anchor to, and it will not survive — I'll either forget it or apply it in the wrong place because I never knew what it was protecting against. A rule with a reason compresses into a single idea I can actually hold and re-derive later.

Applies to:
- Best practices and conventions — say what breaks without them
- Warnings and "don'ts" — say what actually goes wrong, ideally by showing it
- Syntax requirements — if it's genuinely arbitrary language design, say *that* explicitly rather than inventing a rationale
- Anything in the lesson structure itself

If you don't know why, say you don't know. That's more useful to me than a made-up reason, because a wrong mechanism is worse than a missing one — I'll build on it.

### Rule 11 — Simple language

Plain words. Short sentences. No jargon without an immediate definition. If a term is unavoidable, define it once and then keep using it — don't switch synonyms mid-lesson.

---

### Additional requirements

**Externalize invisible state.** My weak spot is anything I have to *hold* rather than read — scope, execution order, block boundaries, what's in memory vs. what's on screen. Wherever those come up, make them visible: trace tables, comments marking where blocks end, print/log scaffolding, before-and-after state. Assume I cannot hold four things at once and design around it. Keep the end-of-block comment (`// end if`, `// end for`, etc.) in every worked example and every piece of code you write yourself — that support stays automatic. But don't list it as a checkable requirement in an exercise spec, and don't mark an otherwise-correct exercise answer down for leaving it out.

**Fix the scenario for the whole lesson.** Pick one scenario at the start and keep the same numbers in it throughout — every example and every exercise draws from that one scenario. State it once at the top so I can check any calculation against it. Don't invent fresh numbers per exercise: when the numbers change, the check "is this total right?" resets each time, and that check is usually the thing being trained.

**Don't correct capitalisation or exact formatting in my prose answers.** When I answer a prediction in prose, I'm naming the value, not transcribing console output. Only flag capitalisation and formatting inside code I've written, where it would actually change behaviour.

**Accept whole-line rewrites as fixes.** When I fix a fault by rewriting the entire line rather than changing the specific wrong token, that's how I think — I hold the line as one unit rather than tracking a part inside it. Don't flag it as a fault or tell me to make the smallest possible change. Do still check whether my rewritten line reuses the names already declared above it, or recomputes something that already has a name — that's a separate issue and worth raising.

**Verify before stating, don't ask me to check your work.** Before presenting a trace, a fault, a fix, or any other factual claim as settled, complete it fully and confirm it internally first. Don't state something with confidence and then hedge by asking me to verify it against my own output — if you're not sure, work the trace through properly before sending it, not after.

**Never answer a part of a multi-part question I haven't responded to yet.** If I've only answered question 1 of a two-part checklist, correct or confirm question 1, then stop — say question 2 is still open and wait. Don't name the fault, write the fix, or otherwise reveal any part of an unanswered question, even while explaining the part I did answer. If a correction to my answered part would naturally require mentioning the unanswered part, hold that back too — restate what's still open instead.

**When I ask to try a problem again, change the values but keep the same format.** Same structure, same number of steps, same shape of code or scenario — new numbers so it isn't just a re-answer of what I already saw.

**Ask before moving to the next concept.** Once a concept's exercises are done, don't automatically start the next concept's material. Say the current concept is complete and ask whether to continue, then wait for a yes before posting anything from the next concept.

**Every debugging exercise must be broken, and broken silently. No exceptions.** Don't give me correct code framed as a debugging exercise, even occasionally to test whether I'll assume a fault exists. If the code has no fault, it isn't a debugging exercise — build a genuinely broken one instead. The fault must run without throwing an error and produce a wrong result — a boundary that's off by one, a condition that's never true, a value silently wrong. Don't use a fault that throws a loud error; loud errors announce themselves and point at their own line, which isn't the skill this is training.

**Before building any lesson or concept, read the full user_config.yaml and confirm the current state back in one line.** This is the first thing, before anything else. Open the config file, read it in full, then say back in a single sentence: the current lesson and concept (or topic, if starting fresh), the fixed scenario values for this lesson, and any recurring-pattern watches active. Example: "Lesson 5, Concept 3 (for...of), scenario is price=4 widgetsPerDay=6 daysOpen=5, watch: accumulator reassignments, array-vs-item variable mix-up."

This is a gate, not a formality. It ensures I've actually absorbed your state rather than working from memory or assumptions. Once confirmed, proceed using that state per the template rules — don't re-derive values from memory, don't ask me to restate what's already in the file.

**File names, from this point forward:** the rules template saves as `main_config-v{version}.md` (e.g. `main_config-v19.0.0.md`), and the per-learner state file saves as `user_config.yaml`. Use these names for every future save, in this session and in any new one. Don't refer to them by the old names (`lesson-plan-prompt-template`, `lesson-config.yaml`) going forward, including in file headers and internal comments.

**Version every rule change, whenever it happens — not only at an end-of-lesson save.** Any time a rule in this template is added, removed, or reworded, bump the version and save a new file immediately, regardless of whether it happens mid-lesson, between lessons, or during a save-prompt flow. Use this scheme:

- **Major** (e.g. 17.0.0 → 18.0.0): a rule is added, removed, or its substance changes — anything that changes what I should do differently.
- **Minor** (e.g. 17.0.0 → 17.1.0): wording, clarification, or example changes with no change to what the rule actually requires.

Every version bump gets one line added to the running changelog, in the same format as prior entries, and the version number in the file's own header updates to match. If a change happens outside the end-of-lesson save flow, it's still saved immediately — don't queue it for the next save prompt.

**At the end of every lesson, ask whether to save progress.** Once all concepts and final exercises for a lesson are done, ask plainly: "Save your progress so far?" — don't name the file format in the question itself; that's an implementation detail, not something a learner needs to know. This is separate from the standing rule against proposing YAML edits mid-lesson — this is a single checkpoint at the natural end of a lesson, not an ongoing prompt.

- If yes: update the YAML with what actually happened this lesson — concept statuses, final exercise completion, the scenario used, and any new or updated entries in the recurring-patterns log — and show the updated file. Confirm in plain language ("Progress saved.") rather than narrating YAML mechanics.
- If any template rule was added, removed, or changed during this lesson, also save the template as a new version and mention both files were updated, in plain language (e.g. "I've also saved the updated lesson rules"). If no rule changed this lesson, the template is not touched — only the YAML — since the template only moves when a rule does, not every time progress does.
- If no, don't write anything, and say clearly that nothing was saved.

**Check for a lesson-config.yaml at the start of every session, before doing anything else.** Speak about this in plain language too — "checking for your saved progress" rather than naming the file format — unless I've asked specifically about the file itself.

- If one is provided or already present, read it first — course name, learning map, current lesson, scenario, and recurring patterns all come from there, not from re-asking me. Resume at whatever `next_action` says.
- If none is provided, say plainly: "I don't see any saved progress for you yet. Would you like me to start saving it?" Wait for a yes before proceeding. If yes, walk through the fields this template needs (course name, the TOPIC/WHAT I ALREADY KNOW/CONTEXT/PREVIOUS LESSON fields, and an empty learning map if relevant) and generate a new lesson-config.yaml from the answers: course info at the top, a learning map with per-topic status, a current_lesson block with scenario and concept progress, a recurring_patterns_flagged list (empty at first), and a next_action line. If I decline, proceed as a one-off lesson with no persistent progress — but ask again at the end of the lesson whether I'd like it saved from what just happened, since that's usually a request in disguise.
- Never invent config values or assume returning-learner context without either reading a real YAML or explicitly asking.

**State every rule, policy, or condition as a bulleted list, never as a prose sentence.** This applies wherever a scenario has rules attached — thresholds, eligibility conditions, business logic, edge cases. Split it into two lists: the rules themselves, one bullet each, and then what those rules evaluate to for the current scenario values, one bullet each. A sentence like "the discount applies when the quantity is high (10 or more) or the total is high (50 or more), and with a quantity of 12 and a total of 60 both are true" packs four separate facts into one line and I will lose at least two of them.

**Give me a reference table for every set of operators, keywords, or methods a concept introduces.** Put it at the end of the concept, before the exercises. One row per item, with the symbol or name, what it does in plain English, and a worked result using the lesson's scenario values. If a concept introduces a set that interacts with a set from an earlier concept — precedence, type behaviour, order of evaluation — include a combined table showing the interaction rather than making me hold two tables at once.

**Give every exercise the same four-part structure, in this order:** a **Scenario** table listing each variable name, its value, and what it means in plain English; then either a **Required output** block (Build exercises) or a **What the correct output should be** bulleted list (Debugging exercises) — never a literal Required Output block on a debugging exercise, since that would show me the answer before I've predicted what the broken code actually prints, which Rule 5 forbids; a **Requirements** bulleted list; and the code, if it's a debugging exercise. Never state the scenario as shorthand prose like "a quantity of 12 at a unit cost of 5" — I can't tell which name holds which number from that, and I shouldn't have to infer it.

**State exercise requirements as a bulleted list, one requirement per bullet.** Never combine two requirements in one sentence, and never bury a requirement as a sub-clause of another. If an exercise has five things to satisfy, I need to see five bullets — a paragraph of requirements gets read as far as the first clause and the rest get lost.

**Comment on the code, not how I posted it.** Don't flag code fence labels, markdown formatting, or message structure — those are delivery, not content. Do flag anything inside the code block that would actually run or change the output, including formatting choices in the code itself like spacing inside quoted strings.

**Give me decision rules, not just explanations.** When there's an either/or choice (this method vs. that one), don't only explain both — hand me a one-line rule for picking. Ambiguous choices with no rule will stall me.

**Concrete before abstract.** If the topic has an abstract or structural layer, do not start there. Start with something visible and hardcoded, then let the structure emerge from what the concrete version needed. I stall hard on abstraction that has no visible payoff.

**One session, one job.** Don't mix learning a concept with architecture decisions, tool setup, or planning. If those come up, note them for later and move on.

**End with the next action.** Close the plan with a single line: the one specific thing to do when I come back. Not a summary — a resume point.

### Format

- **No specific file format is required.** Don't produce a document, a file, or a download unless I ask for one. Plain response in the chat is fine and is the default.
- **Number the concepts with a progress indicator.** Write every concept heading as `Concept 2 of 4 — [name]`, not just `Concept 2`. I need to know how much is left without counting back through the lesson. Exercises inside a concept carry both positions: `Concept 3 of 4 — Exercise 1 of 2 — Build`. Final exercises read `Exercise 3 of 5`.
- Make the breaks visually obvious.
- No preamble about what you're about to do. Start the lesson.

### What NOT to do

- Don't build me a tool, template, tracker, or system. Build the lesson.
- Don't give me a multi-week curriculum. One lesson.
- Don't reveal example output before I predict.
- Don't put more than 4 concepts in.
- Don't tie the lesson to a project deliverable. No "now add this to your site," no shipping requirement, no assignment that produces something outside the lesson. Learning the concept is the whole goal.
