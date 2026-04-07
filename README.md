# taste

A Claude Code skill for engineering taste and quality judgment. Evaluates code, architecture, product, design, and communication through a calibrated 5-dimension lens.

Use this skill when the question is "is this *good*?" rather than "does this *work*?"

## What It Does

- **Quick Judgment** — verdict + highest-leverage fix for single files or snippets
- **Deep Review** — dimension-by-dimension analysis for large codebases, architecture docs, or PRDs
- **Guide** — taste-informed code generation and refactoring with explicit design rationale
- **Compare** — judgment-oriented comparison between approaches, labeling taste vs objective tradeoffs

## Five Dimensions

| Dimension | Core Tension | Ultimate Test |
|-----------|-------------|---------------|
| Code | Consistency > cleverness | Can a tired engineer at 2am understand this? |
| Architecture | Resilience > elegance | Will this survive the next 3 requirement changes? |
| Product | Composability > completeness | Does removing this make the product better? |
| Design | Intentionality > decoration | Does every pixel earn its place? |
| Communication | Teaching > describing | Can a newcomer understand the intent without asking? |

## Triggers

The skill activates on:

- "taste", "品味", "/taste"
- Subjective quality signals: "feels off", "amateur", "overengineered", "is this good"
- Explicit quality goals: "build X with good taste", "review the design quality"

Does **not** activate for: bug fixes, performance optimization, security audits, or functional requests with no quality signal.

## Structure

```
taste/
├── SKILL.md                          # Main skill instructions
├── references/
│   ├── code-taste.md                 # Naming, functions, errors, cognitive load, consistency, deps, testing
│   ├── architecture-taste.md         # Boundaries, coupling, evolution, state, failure modes, scaling, data
│   ├── product-taste.md              # Feature composition, simplicity, mental models, defaults, scope, edge cases
│   ├── design-taste.md               # Hierarchy, typography, spacing, color, motion, components, responsiveness
│   ├── communication-taste.md        # Naming, API design, documentation, commits, PRs, error messages
│   └── scoring-rubric.md             # 1-5 scale descriptors, calibration examples, surface scoring rules
└── agents/
    ├── reviewer.md                   # Deep review executor for large targets
    └── advisor.md                    # Pre-generation taste guidance for greenfield code
```

## Install

Copy the `taste/` directory to your Claude Code skills path:

```bash
cp -r taste/ ~/.claude/skills/taste/
```

The skill will appear in Claude Code's available skills automatically.

## Usage

Just ask naturally:

```
这段代码品味如何？
```

```
Deep review these 5 files for taste
```

```
帮我重构这个组件，要有品味
```

```
Which of these two implementations has better taste?
```

## Design Philosophy

This skill was built with its own principles in mind:

- **Judgment first, structure second.** Quick prose judgment is the default. Scoring, templates, and dimension breakdowns are available but never forced.
- **Evidence-driven.** Only score dimensions with direct evidence. Skip the rest with a note, not a guess.
- **No fake precision.** No weighted overall scores. Dimension scores are optional shorthand, not the point.
- **Boundary clarity.** Each dimension owns specific territory. Naming mechanics go to Code; domain language goes to Communication. The same issue is never penalized twice.
- **Respect the codebase.** In generation mode, existing project patterns take priority over reference principles unless they're actively harmful.

## Intellectual Sources

Unix Philosophy, Dieter Rams, Paul Graham, Cognitive Load Theory, Christopher Alexander, Steve Krug, Rich Hickey, Sandi Metz, Kent Beck, Linus Torvalds.

## License

[MIT](LICENSE)
