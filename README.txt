AURORA'S LESSON SYSTEM - README
=================================

CURRENT VERSION: main_config-v36.0.0.md
(check changelog.md for what changed and when)

WHAT THIS IS
------------
A self-directed lesson system, built for one-on-one learning with an
AI tutor. It splits into two files so the teaching rules and your
personal progress never get tangled together:

  - main_config       - the rules. How lessons are paced, how
                         exercises are built, how feedback is given.
                         Rarely changes.
  - user_config.yaml  - your progress. What course, what topic, what
                         scenario, what you've completed, what
                         patterns have shown up in your work. Changes
                         every lesson.

Paste both into a new chat and the assistant picks up exactly where
you left off - no re-explaining the course, no repeating what you
already know.


THE TWO-FILE SPLIT
-------------------
                    main_config              user_config.yaml
Holds               rules and structure      your state and history
Changes              only when a rule is      every lesson
                     added, removed, or
                     reworded
Shared across        yes - topic-agnostic     no - specific to you
courses?                                      and this course
Named                main_config-v{version}.md   user_config.yaml

This is the single most important thing to understand before editing
either file by hand. If you want to change how lessons are taught -
pacing, exercise format, feedback style - that's a main_config
change. If you want to change what's being taught or how far along
you are, that's user_config.yaml.


STARTING A NEW SESSION
-----------------------
  Both files pasted in:
    The assistant reads your saved progress and resumes from there -
    same course, same topic, same scenario, no need to re-explain
    anything.

  Only main_config pasted in:
    The assistant checks for saved progress, doesn't find any, and
    asks plainly whether you'd like it to start saving some. Say yes
    and it walks you through setting up a course from scratch.


HOW SAVING WORKS
------------------
At the end of every lesson - once all concepts and exercises are
done - you'll be asked: "Save your progress so far?"

  Yes: your progress file updates with what happened that lesson -
       what's complete, what scenario was used, anything worth
       remembering about how you're doing. If any rule changed
       during the lesson, the rules file is saved too, as a new
       version. You'll get a plain confirmation either way - no file
       jargon, unless you ask about the files directly.

  No:  nothing is written, and you'll be told plainly that nothing
       was saved.


SUGGESTING CHANGES MID-SESSION
--------------------------------
You don't have to wait for the end of a lesson to change how things
work. At any point in a session, you can ask for a change to the
rules - pacing, formatting, what gets flagged, anything about how
you're being taught. When you do:

  - The change is made to the rules immediately, not queued for
    later.
  - The rules file is versioned and saved right away, automatically
    - you don't need to separately ask for a save.
  - You'll be told plainly what changed and that the file was
    updated, without needing to ask.

This is different from the end-of-lesson prompt, which is about
saving your PROGRESS. Suggesting a rule change saves the RULES, on
the spot, every time.


VERSIONING
----------
Every rules change gets a version number and a line in the
changelog.

  Major (17.0.0 -> 18.0.0):
    a rule was added, removed, or its substance changed. Something
    about how lessons work is different.

  Minor (17.0.0 -> 17.1.0):
    wording, clarity, or an example changed, but the rule itself
    requires nothing different than before.

Full history of every change lives in changelog.md - check there
rather than trying to diff the rules file by hand.


FILE NAMING
------------
  Rules:     main_config-v{version}.md   (e.g. main_config-v36.0.0.md)
  Progress:  user_config.yaml            (no version number - always
                                          the latest, overwritten
                                          each save)
  History:   changelog.md


KNOWN LIMITATIONS
-------------------
  - Built and tested for one course (JavaScript fundamentals). The
    rules themselves don't name any subject, but some of them -
    guaranteed-broken debugging exercises, predict-before-running -
    are shaped around code specifically, and haven't been tried
    against a non-coding subject.
  - A "core rules + per-topic module" split, so one core file could
    serve multiple unrelated courses cleanly, is a planned future
    direction, not something built yet.


MAKING CHANGES
----------------
  - Want to change how you're taught? Say so, any time, in a
    session. It updates and saves automatically - see "Suggesting
    changes mid-session" above.
  - Want to change what you're learning or your progress? That's
    user_config.yaml, and it's meant to be edited through the
    end-of-lesson save prompt, not by hand.
  - If a rule change does NOT auto-save, that's a bug in following
    the rules - not a sign the rule itself needs rewriting.
