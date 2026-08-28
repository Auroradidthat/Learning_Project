# Aurora's Lesson System

> A self-directed lesson system for focused, one-on-one learning with an AI tutor.

**Current version:** [`main_config-v24.0.0.md`](main_config-v24_0_0.md)  
See [`changelog.txt`](changelog.txt) for the full version history.

## What this is

Aurora's Lesson System keeps the way you are taught separate from the progress you make. That means you can start a new chat and continue where you left off—without re-explaining the course or repeating material you already know.

The system uses two files:

- **`main_config-v{version}.md`** defines the teaching rules: lesson pacing, exercise design, feedback, and other learning behavior. It changes only when those rules change.
- **`user_config.yaml`** records your personal learning state: the course, current topic, scenario, completed work, and patterns noticed during your lessons. It can change after every lesson.

## Quick start

1. Open a new chat with your AI tutor.
2. Provide the current `main_config` file and your `user_config.yaml` file.
3. Continue learning from your saved position.

If you provide only the `main_config` file, the assistant checks for saved progress. If none is available, it asks whether you want to begin tracking it and guides you through setting up a course.

## How the two files work together

| | `main_config-v{version}.md` | `user_config.yaml` |
|---|---|---|
| **Contains** | Teaching rules and lesson structure | Your learning state and history |
| **Changes when** | A rule is added, removed, or revised | Your progress is saved after a lesson |
| **Shared across courses** | Yes—it is topic-agnostic | No—it is specific to you and your course |
| **Naming** | Includes a version number | Always uses the same filename |

> **The key distinction:** Change `main_config` when you want to change **how you are taught**. Change `user_config.yaml` when you want to change **what you are learning or how far you have progressed**.

## Starting a new session

### When both files are provided

The assistant reads your saved progress and resumes with the same course, topic, and scenario. You do not need to reconstruct the context from earlier lessons.

### When only `main_config` is provided

The assistant checks for saved progress. If it finds none, it asks whether you want to start saving progress and walks you through creating a course from scratch.

## Saving progress

At the end of a completed lesson, the assistant asks:

> Save your progress so far?

- **Yes:** `user_config.yaml` is updated with completed work, the scenario used, and useful observations about your learning. If a teaching rule changed during the lesson, the rules file is also saved as a new version.
- **No:** Nothing is written, and the assistant confirms that no progress was saved.

Confirmations stay in plain language unless you ask for file-level details.

## Changing the rules during a session

You can change how the system teaches at any point. Ask for a different pace, feedback style, exercise format, or another teaching adjustment, and the assistant will:

1. Apply the change immediately.
2. Save a newly versioned rules file.
3. Tell you clearly what changed.

This is separate from the end-of-lesson prompt. That prompt saves your **progress**; a mid-session teaching change saves the **rules** immediately.

## Versioning

Every rules change receives a version number and an entry in [`changelog.txt`](changelog.txt).

- **Major** (`17.0.0` → `18.0.0`): A rule is added or removed, or its meaning changes in a way that affects how lessons work.
- **Minor** (`17.0.0` → `17.1.0`): Wording, clarity, or an example changes without changing what the rule requires.

Use the changelog to review the full history instead of comparing rule files by hand.

## File guide

| Purpose | Filename | Notes |
|---|---|---|
| Teaching rules | `main_config-v{version}.md` | Versioned; for example, `main_config-v24.0.0.md` |
| Learning progress | `user_config.yaml` | Always represents the latest saved state |
| Version history | `changelog.txt` | Records every rules change |

## Known limitations

- The system has been built and tested with one course: JavaScript fundamentals.
- Although the core rules are topic-agnostic, some techniques—such as guaranteed-broken debugging exercises and predict-before-running prompts—are designed around programming and have not yet been tested with non-coding subjects.
- A future direction is to separate the system into core rules and topic-specific modules, allowing one core file to support several unrelated courses cleanly.

## Making changes

- To change **how you are taught**, ask during a session. The rules update and save automatically; see [Changing the rules during a session](#changing-the-rules-during-a-session).
- To change **what you are learning or your progress**, use the end-of-lesson save flow. `user_config.yaml` is designed to be managed through that flow rather than edited by hand.
- If a rule change does not save automatically, treat that as a failure to follow the system—not as a reason to rewrite the rule itself.
