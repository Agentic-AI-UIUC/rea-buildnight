# Prompts

Starting points, not a script. Pasting every prompt in order won't teach you much.
Read what comes back, check it against the real app, and write your own follow-ups.
Your agent follows `AGENTS.md`, so it stops after each step and waits for you.

## Get oriented

```
Read AGENTS.md, README.md, and investigation/QUESTION.md. In a few lines, tell me how
tonight works and what you'll need from me. Don't change anything.
```

```
List the REA tools you have, and tell me which kinds of targets each one is for.
```

## Choose

```
Help me brainstorm something to reverse engineer tonight. Here are apps, games, and tools I use:
___. For each one, suggest one specific behavior I could investigate. Then rate each idea:
can I reach the evidence on my machine, can I compare the result, and does it fit in one evening?
```

```
I want to reverse engineer how ___ does ___. Is that one observable behavior? Which REA route
fits, and what evidence can I actually reach? What would make it too big for tonight?
```

When you've picked, write `investigation/QUESTION.md` yourself.

## Investigate

```
Find where ___ is installed on this machine (or which page/files we need), and tell me
what you'll inspect and why. Don't guess paths.
```

```
Using REA, investigate the question in investigation/QUESTION.md. Show evidence before
building. Label every claim FINDING, INTERPRETATION, or UNKNOWN.
```

Good follow-ups come from what surprised you in the original, or from a claim you don't believe yet:

- "Show me the code behind claim ___."
- "Is ___ a FINDING or an INTERPRETATION? What would make it a FINDING?"
- "I saw ___ happen in the app. Does that match the code?"

## Explain

```
Help me fill in investigation/EVIDENCE.md from what we found. Propose rules for the build,
each traced to a claim, and explain the trade-offs. I'll choose the rules.
```

## Build

```
Build my own version of ___ in app/ using ___. Follow the "Rules for the build" in
investigation/EVIDENCE.md. Interface: ___ (describe it, or attach a screenshot or sketch).
Explain the code to me as you go.
```

## Compare

Choose the scenarios yourself. Pick ones that could break your rules.

```
I'm going to run "___" in both the original and our build. Before I look, predict what
our build will show, and why.
```

```
Scenario ___ doesn't match. Is this a bug in our build or a gap in our evidence?
```

---

## Default project: Obsidian's graph view

Only if you don't have your own idea. Copy the question from the bottom of
`investigation/QUESTION.md`, then:

```
Find where Obsidian is installed on this machine and locate the package that holds its
application JavaScript. Tell me the path, the version, and how you found it.
```

This is the prompt from the slides:

```
Investigate how Markdown links become graph connections in Obsidian, using REA.
Show evidence before building. Label every claim FINDING, INTERPRETATION, or UNKNOWN.
```

```
Build a small Markdown notes app in app/ using ___ (web or Electron). It should load
the notes in vault/, let me create, edit, and save notes, support [[Note Name]] links,
and show a graph that updates when links change. Follow the "Rules for the build" in
investigation/EVIDENCE.md. Interface: ___.
```

Want more? Ideas, not prompts: backlinks, search, graph filters. Investigate each one first.
