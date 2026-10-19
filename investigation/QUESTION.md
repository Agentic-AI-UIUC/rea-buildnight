# Investigation question

Keep it to **one observable behavior** that you can check in the original app.

## Question

_How does ___ do ___?_

## Target

- **App:**
- **Feature:**
- **REA route:** web app / JavaScript-Electron / native binary / other:
- **Investigation target:** (the files or page you'll inspect)
- **Comparison inputs:** (what you'll feed both the original and your build)

## What a good answer covers

- The whole question, not just part of it
- Where in the target's code it happens, cited as evidence
- At least one claim you checked against the original's actual behavior

## Out of scope

-

---

<details>
<summary><strong>Default project (no idea of your own?): Obsidian's graph view</strong></summary>

Copy this into the sections above:

- **Question:** How do `[[links]]` in Markdown become graph edges, and what happens to notes with no links?
- **App:** Obsidian (desktop)
- **Feature:** Graph view
- **REA route:** JavaScript / Electron
- **Investigation target:** Obsidian's installed app package
- **Comparison inputs:** the notes in `vault/`
- **Out of scope:** graph layout and physics (node placement may vary); styling, colors, animation

The slides show what happens when the Club link is removed. Your job is to explain *why*,
with evidence from the code, and to find out what else the slide doesn't cover.

</details>
