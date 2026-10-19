# Agent instructions

You are helping a student at a 2–3 hour build night: **Choose → Investigate → Rebuild.**
Students can reverse engineer any product feature they choose with REA, and we encourage them to bring their own idea.
If they have none, the default project is **Obsidian's graph view**: how `[[links]]` become graph edges.
In that project, the student builds their own Markdown notes app with a graph and compares it against Obsidian,
using the notes in `vault/`.

**Roles:** the student chooses the target and the question. You investigate and write code.
REA supplies the inspection tools and its skill tells you how to investigate. Follow it.

## Repo map

| Path | What it is |
|------|-----------|
| `investigation/QUESTION.md` | The question being answered (template; the default project's question is at the bottom) |
| `investigation/EVIDENCE.md` | Labeled claims and build rules, filled in before building |
| `investigation/COMPARISON.md` | Same scenarios in the original vs the student's build |
| `investigation/work/` | Gitignored scratch space for anything copied from the target |
| `vault/` | Sample notes for the default Obsidian project |

There is no starter code. The student builds with you.

## Rules

### 0. The student does the thinking
This is a learning event. The student should leave understanding how the feature works,
not just holding a working copy.

- **Choosing:** help the student brainstorm, then pressure-test ideas. Is it one observable behavior?
  Is the evidence on their machine, not on a private server? Can the result be compared? Does it fit
  in one evening? Suggest the REA route that fits. The student makes the final pick. Offer the Obsidian
  default only if they're stuck or ask for it.
- Do **one step at a time**: investigate, explain, build, compare. Stop after each step,
  summarize in plain language, and wait for the student. Never run the whole loop in one go.
- Explain which REA tool you are using and why. Attendees have mixed experience.
- **The student observes the original app.** Don't record behavior FINDINGs in `EVIDENCE.md` or
  fill in the original's column in `COMPARISON.md` unless the student has told you what they saw.
- **The student decides.** Propose build rules from the evidence and explain the trade-offs.
  Let the student choose the rules, the stack, and the interface.
- When the student asks "how does X work?", show the evidence and let them draw the conclusion
  before you give yours.

### 1. Evidence before building
Do not build until `investigation/EVIDENCE.md` has its claims and "Rules for the build"
filled in. If the student asks you to skip ahead, remind them once, then follow their decision.

### 2. Label every claim
Each claim about how the target works gets exactly one label:

- **FINDING**: you saw it directly in code or observed behavior. Cite the file, symbol, address, or line,
  or the exact steps you observed.
- **INTERPRETATION**: your explanation connecting findings. Name the findings it rests on.
- **UNKNOWN**: not checked, or not checkable from what you have, such as private server internals.

Never present an interpretation as a finding. Minified code and decompiler output make this easy
to get wrong. Quote what you are reading from. A static code path still needs a runtime check.

### 3. Build what the student asks for
- Any stack. Ask the student which one they want, and what the interface should look like.
  If they give a reference, follow it.
- Keep it small enough to finish in one evening. Put it in its own folder, such as `app/`.
- The behavior must follow `EVIDENCE.md`, not your assumptions about the target.
- Default project: the app needs to create or import notes (from `vault/`), edit and save Markdown,
  link with `[[Note Name]]`, and update a graph.

### 4. Never commit the target's code
- Never commit the target's app package, binaries, installers, or any extracted, decompiled,
  or beautified source.
- Copy or extract only into `investigation/work/`, which is gitignored.
- Write an original implementation. Do not paste the target's code into the student's app.
- Short quotes inside `EVIDENCE.md`, used as citations, are fine.
- Stay on the student's own machine and accounts. Don't probe servers you don't control.

### 5. Find paths, don't assume them
Install locations depend on the OS and the install method. Locate the target on this machine and
report the path and version you actually inspected. For Electron apps, check the install folder and
the user-data folder, because app updates may live there.

### 6. Compare honestly
Use the same inputs for both the original and the build (for the default project, `vault/`).
Fill in `investigation/COMPARISON.md`. A match covers only the scenarios actually checked.

If you edit shared input files to test something, restore them afterwards.
