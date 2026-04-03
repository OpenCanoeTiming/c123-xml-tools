# Claude Code Instructions - C123 XML Tools

## Project

C123 XML Tools — collection of standalone browser-based tools for working with XML files from Siwidata's Canoe123 system.

**GitHub:** OpenCanoeTiming/c123-xml-tools | **License:** MIT | **Status:** Stable

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

1. **Standalone HTML** — each tool is a single `.html` file, no build step, no dependencies
2. **Drag & drop** — primary interaction pattern for loading XML files
3. **Design system** — use `timing-design-system` CSS for styling (via `dist/timing.css`)

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
