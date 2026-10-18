# Claude Code Instructions - C123 XML Tools

## Project

C123 XML Tools — collection of standalone browser-based tools for working with XML files from Siwidata's Canoe123 system.

**GitHub:** OpenCanoeTiming/c123-xml-tools | **License:** MIT | **Status:** Stable

---

## Rebuild 2026/27 — read first

- **Design:** c123-server `docs/arch`; this repo is context, not a subject (TEST-ARCHITECTURE §8).
- **Legacy line:** venues run tag `legacy-2026` of the deployables; this repo has no legacy line and is not touched by the rebuild.
- **Git:** conventional commits; squash merges; `git add <file>`, never commit `.claude/` or `.superpowers/`. Czech with the maintainer, English in code, commits and docs.

---

## Architecture

```
c123-xml-tools/
├── penalties-quality-analyzer/
│   ├── penalties-quality-analyzer.html   # Standalone HTML tool
│   └── readme.md                         # Documentation
├── race-combinator/
│   ├── canoe-race-combine.html           # Standalone HTML tool
│   ├── docs.md                           # Detailed documentation
│   └── readme.md                         # Basic info
├── participant-adder-cz/
│   ├── participant-adder-cz.html         # Standalone HTML tool
│   └── readme.md                         # Documentation
├── index.html                            # Landing page (GitHub Pages)
├── LICENSE
└── README.md
```

---

## Key References

| Purpose | Path |
|---------|------|
| **Protocol docs** | `../c123-protocol-docs/` |
| **XML format** | `../c123-protocol-docs/c123-xml-format.md` |
| **Design system** | `../timing-design-system/` |

---

## Important Rules

1. **Standalone HTML** — each tool is a single `.html` file, no build step; the only external resources are the design system CSS and the Inter web font (Google Fonts)
2. **Drag & drop** — primary interaction pattern for loading XML files
3. **Design system** — load `timing.min.css` from the timing-design-system GitHub Pages build

---

## Tools

### penalties-quality-analyzer
Analyzes quality of entered penalties in C123 XML file. Detects inconsistencies and errors.

### race-combinator
Combines multiple race XML files into one. For merging results from multiple rounds/days.

### participant-adder-cz
Adds late-registered competitors to C123 XML. Searches Czech canoe registry (CSV, Windows-1250). Direct file editing via File System Access API.

---

## Development

Tools use vanilla JavaScript with no dependencies. Open HTML in browser to test.

```bash
# Local server (optional)
npx serve .
```

---

## Workflow

Issue-driven development. Every change starts with a GitHub issue.

### 1. Rozbor (Analysis)
- Comment on issue: restate problem, challenge the idea, define scope, identify risks

### 2. Plan
- Use Claude Code plan mode to design implementation
- Get user confirmation before implementation

### 3. Implement
- Branch from main: `feat/{N}-{slug}` or `fix-{N}-{slug}`
- Commit incrementally, push regularly

### 4. PR & Review
- Every issue → PR with `Closes #N`
- Summarize what changed and why
- Squash merge; PR title keeps the conventional prefix
- `git add <file>`, never `-A`; never commit `.claude/` or `.superpowers/`

---

## Language

- User communication: **Czech**
- Documentation (README, docs): **English**
- Code, comments, commit messages: **English**

---

## Commit Message Format

```
feat: add new validation rule for gate penalties
fix: correct XML merge for overlapping runs
docs: update race-combinator documentation
```
