# Presentation Creator - Setup Summary

## What Was Created

You now have a complete presentation creation system with **3 specialized agents** and **4 comprehensive skills** for building professional reveal.js presentations.

## Agents Created

### 1. **presentation-builder.agent.md** (User-Invocable)

**Main orchestrator for creating presentations from scratch.**

- Handles the complete workflow: planning → design → content → scaffolding → validation
- Automatically delegates to specialist agents when needed
- Invoked by users asking to create presentations
- Example: "Create a 12-slide pitch deck for Series A fundraise"

### 2. **presentation-designer.agent.md** (Subagent)

**Visual design specialist.**

- Recommends color palettes matched to topic/audience
- Defines typography hierarchy and font pairings
- Suggests layout patterns for different content types
- Ensures accessibility standards (WCAG AA)
- Automatically invoked by presentation-builder for design decisions

### 3. **content-strategist.agent.md** (Subagent)

**Information architect and messaging expert.**

- Plans presentation structure and content flow
- Creates detailed slide outlines
- Establishes narrative and information hierarchy
- Ensures balanced, visually varied slide types
- Automatically invoked by presentation-builder for content planning

## Skills Created

### 1. **presentation-builder** Skill

**Complete workflow documentation for creating reveal.js presentations.**

Contents:
- 7-step workflow (plan → scaffold → customize → fill → overflow check → visual review → deliver)
- HTML scaffolding guidance (using create-presentation.js)
- CSS customization with CSS variables
- Content editing patterns (incremental editing)
- Overflow detection and fixing
- Screenshot-based visual validation
- Browser editing and PDF export guidance

File: `.claude/skills/presentation-builder/SKILL.md`

### 2. **presentation-design-system** Skill

**Design patterns, color palettes, and visual consistency strategies.**

Contents:
- 20+ color palettes organized by topic (tech, finance, healthcare, creative, education, startups, sustainability)
- Typography hierarchy and font pairing guidance
- Web-safe fonts vs Google Fonts recommendations
- CSS variable organization and customization
- Component patterns (stat boxes, cards, blockquotes, etc.)
- Accessibility standards and contrast checking
- Color usage best practices (light/dark backgrounds)

File: `.claude/skills/presentation-design-system/SKILL.md`

### 3. **technical-presentations** Skill

**Patterns for code-heavy and technical presentations.**

Contents:
- Code highlighting with line-number targeting
- Architecture diagrams (Mermaid syntax)
- Data visualization with Chart.js
- Process flows and flowcharts
- Comparison tables for technology choices
- Terminal/console output styling
- Layout patterns (code + explanation side-by-side)
- Dark color scheme recommendations
- Accessibility for technical content

File: `.claude/skills/technical-presentations/SKILL.md`

### 4. **business-presentations** Skill

**Patterns for business, sales, and financial presentations.**

Contents:
- Pitch deck structure (10-15 slides with specific topics)
- Quarterly business review (QBR) layouts
- Sales presentation patterns
- Key metrics dashboard templates
- Financial charts (revenue trends, growth)
- Customer case study templates
- Competitive positioning visuals
- Roadmap and timeline slide patterns
- Corporate color scheme recommendations

File: `.claude/skills/business-presentations/SKILL.md`

## Directory Structure

```
.claude/
├── agents/
│   ├── presentation-builder.agent.md
│   ├── presentation-designer.agent.md
│   └── content-strategist.agent.md
├── skills/
│   ├── presentation-builder/
│   │   ├── SKILL.md
│   │   ├── scripts/ (placeholder for utility scripts)
│   │   └── references/ (placeholder for additional docs)
│   ├── presentation-design-system/
│   │   ├── SKILL.md
│   │   ├── assets/ (placeholder for templates)
│   │   └── references/ (placeholder for additional docs)
│   ├── technical-presentations/
│   │   ├── SKILL.md
│   │   └── assets/ (placeholder for templates)
│   └── business-presentations/
│       ├── SKILL.md
│       └── assets/ (placeholder for templates)
├── AGENTS.md (Agent reference and workflow documentation)
└── README.md (Quick start guide)
```

## How to Use

### Getting Started

1. **Ask the presentation-builder agent** to create a presentation:
   ```
   "Create a 12-slide pitch deck for our Series A fundraise"
   ```

2. The agent will:
   - Ask clarifying questions
   - Delegate to content-strategist for outline
   - Delegate to presentation-designer for theme
   - Execute the full scaffolding and content workflow
   - Validate all slides visually
   - Provide browser editing commands

### Key Features

✅ **Full workflow automation** - From planning to final presentation
✅ **Specialized agents** - Each handles their area of expertise
✅ **Design patterns** - 20+ color palettes and layout templates
✅ **Technical content** - Code, diagrams, charts for technical presentations
✅ **Business templates** - Pitch decks, QBR, sales presentations
✅ **Visual validation** - Automatic overflow checking and screenshot review
✅ **Accessible** - WCAG AA compliance built-in

## Next Steps

1. **Try creating a presentation** - Ask presentation-builder for a sample deck
2. **Customize colors** - Use presentation-design-system skill for your brand colors
3. **Explore patterns** - Check technical/business skills for layout ideas
4. **Refine presentations** - Use browser editor for text refinement
5. **Export to PDF** - Generate PDFs from HTML when ready

## File Reference

| File | Purpose |
|------|---------|
| `.claude/agents/presentation-builder.agent.md` | Main orchestrator agent |
| `.claude/agents/presentation-designer.agent.md` | Design specialist subagent |
| `.claude/agents/content-strategist.agent.md` | Content strategist subagent |
| `.claude/AGENTS.md` | Agent reference and workflow |
| `.claude/README.md` | Quick start guide |
| `.claude/skills/presentation-builder/SKILL.md` | Main workflow skill |
| `.claude/skills/presentation-design-system/SKILL.md` | Design system skill |
| `.claude/skills/technical-presentations/SKILL.md` | Technical content skill |
| `.claude/skills/business-presentations/SKILL.md` | Business content skill |

## Architecture

The system follows a **hierarchical agent pattern**:

```
User
  ↓
presentation-builder (orchestrator)
  ├→ Asks presentation-designer (for design decisions)
  ├→ Asks content-strategist (for content planning)
  └→ Executes presentation-builder skill (for implementation)
```

Each agent has:
- **Clear responsibility** - One role, focused purpose
- **Minimal tools** - Only what it needs
- **Tool restrictions** - Research agents use read/search only
- **Keyword-rich description** - For automatic discovery

## Design Principles

1. **Separation of concerns** - Each agent specializes in one area
2. **Automatic delegation** - Main agent coordinates specialists
3. **Incremental workflow** - Step-by-step process with validation
4. **Template-based** - Skills provide patterns, not rigid solutions
5. **Accessibility-first** - WCAG standards built into every skill
6. **Flexibility** - Users can customize colors, fonts, layouts

---

**You're ready to create presentations!** Start by asking presentation-builder to create your first deck.
