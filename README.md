# Reverse Engineer Anything (REA) Build Night Template 

**Choose → Investigate → Rebuild** - Pick a product feature you're curious about. Study it with your
coding agent and [REA](https://github.com/morluto/rea), then build your own version and compare it to the original.

**We encourage you to bring your own idea**. However, if nothing comes to mind, there's a ready-made
default project: [Obsidian's graph view](#default-project-obsidians-graph-view).

> This is what you make of it! Sharing is optional, but would love to see you share what you built on **LinkedIn** and
tag us @Agentic-AI-UIUC, and you can always keep building afterward!

```
.
├── investigation/
│   ├── QUESTION.md       the one question you're answering
│   ├── EVIDENCE.md       what you found, labeled FINDING / INTERPRETATION / UNKNOWN
│   └── COMPARISON.md     same scenario, original vs your build
├── vault/                sample notes for the default Obsidian project
├── AGENTS.md             rules for your coding agent
└── PROMPTS.md            starting prompts for each step
```

There's no starter code. Building is your part.

---

## Who does what

| | Role |
|---|---|
| **You** | Choose the target and the question, check claims against the real app, decide what to build |
| **Your agent** | Investigates and writes code |
| **REA** | Supplies the inspection tools (over MCP) and a skill that tells your agent how to investigate |

Every claim your agent makes gets one label:

| Label | Meaning |
|-------|---------|
| **FINDING** | Seen directly in code or behavior, with a citation |
| **INTERPRETATION** | An explanation built from findings |
| **UNKNOWN** | Not checked, or can't be checked |

## 1. Set up REA

You need Node.js 22.x ≥ 22.19, 24.x ≥ 24.11, or 26+, plus npm.

You also need a coding agent that supports MCP!

```bash
npx rea-agents@latest setup
```

1. Pick your agent.
2. Review the config changes it proposes.
3. Restart the agent.
4. Check that the REA tools show up.

Static JavaScript analysis does **not** need Hopper or Ghidra.
Full instructions are at [rea.tools](https://rea.tools).

## 2. Choose: brainstorm your own target

Think of an app, game, or tool you use, and one thing it does that makes you think *"how does it do that?"*

A good target has all three of these:

- **One observable behavior.** Not "how does Spotify work", but one specific feature.
- **Evidence you can reach.** App files and code, network requests and responses, and observed inputs and outputs.
  Code on a private server stays hidden, so pick something that happens on your machine.
- **A result you can compare.** The same input goes into the original and your build, and you can check the outputs.

Find the REA route that fits. These are alternatives; you don't need every tool:

| Target | What REA examines | Guide |
|--------|-------------------|-------|
| Web app | Browser page, client scripts, network activity | [browser](https://rea.tools/guides/browser) |
| JavaScript / Electron desktop app | Shipped code, modules, process communication | [javascript](https://rea.tools/guides/javascript) |
| Native binary (games, classic apps) | Compiled instructions, assembly, pseudocode | [native](https://rea.tools/guides/native) |

REA also covers .NET assemblies, Android APKs, WebAssembly, and firmware. See the [full catalog](https://github.com/morluto/rea).

Stuck for ideas? Ask your agent to brainstorm with you (see [PROMPTS.md](PROMPTS.md)). You make the final pick.
When you've chosen, write your question into [`investigation/QUESTION.md`](investigation/QUESTION.md).

**Still nothing?** Use the [default project](#default-project-obsidians-graph-view). It's a good one.

## 3. Investigate

Have your agent use REA on your target. Investigate one behavior, and see evidence before you build anything.
Have the agent locate the target on your machine; don't guess paths.

> **Never commit the target's app package or extracted source.** If anything needs copying,
> put it in `investigation/work/`. That folder is gitignored.

## 4. Explain

Fill in [`investigation/EVIDENCE.md`](investigation/EVIDENCE.md) with every claim labeled.
You decide the "Rules for the build" section. Don't build until it's filled in.

## 5. Build

Build your own version of the behavior, in any stack and with any interface. Want a specific look?
Ask your agent explicitly and give it a reference. Put it in a folder in this repo, such as `app/`.
Write your own implementation, and don't paste the target's code into it.

## 6. Compare

Give the same inputs to the original and to your build, and record both results in
[`investigation/COMPARISON.md`](investigation/COMPARISON.md). Pick scenarios that could break your rules.
A match only covers the scenarios you actually checked.

---

## Default project: Obsidian's graph view

For when you don't have a target of your own. Markdown notes link to each other with
`[[Note Name]]`, and Obsidian draws those links as a graph.

**Question:** *How do `[[links]]` in Markdown become graph edges, and what happens to notes with no links?*
Copy it into `investigation/QUESTION.md`.

**Look at the original**

1. Install Obsidian from [obsidian.md](https://obsidian.md).
2. Choose **Open folder as vault**, then select this repo's `vault/` folder.
3. Open the **graph view**. ([Obsidian docs: graph view](https://obsidian.md/help/plugins/graph) · [links](https://obsidian.md/help/links))
4. Try the slide example: delete `[[Build Night]]` from `Club.md` and watch the graph.
   Then invent your own edge cases and write down what you see.
5. Put the notes back afterward. They are the shared input for your comparison.

Obsidian creates a `vault/.obsidian/` config folder. It is gitignored.

**Investigation target:** Obsidian is an Electron app, so take the
[JavaScript route](https://rea.tools/guides/javascript). Have your agent find Obsidian's installed app package.
Install locations differ by OS and install method.
*App package = investigation target. Sample notes = comparison inputs.*

> Investigate how Markdown links become graph connections. Show evidence before building!

**Build:** a Markdown notes app that can create or import notes (load `vault/`), edit and save Markdown,
link notes with `[[Note Name]]`, and update a graph as links change. Web or Electron, and your interface can vary.

**Want more?** Add backlinks, search, or graph filters. Investigate how Obsidian does each one first.

