# Presentation Creator Setup

This workspace includes a complete agent and skill system for creating professional reveal.js presentations.

## Quick Start

### Creating a Presentation

Ask the **presentation-builder** agent to create a presentation. Examples:

- "Create a 12-slide pitch deck for our Series A fundraise"
- "Build a quarterly business review presentation with our Q3 metrics"
- "Generate a technical deep-dive on our microservices architecture"

The presentation-builder will:

1. Understand your requirements
2. Delegate design strategy to presentation-designer
3. Delegate content structure to content-strategist
4. Generate HTML/CSS scaffolding
5. Fill in content incrementally
6. Check for overflow issues
7. Review all slides visually
8. Deliver browser-editing commands

## Available Agents

### presentation-builder

Main orchestrator for creating presentations. Handles the full workflow from planning to delivery. Automatically delegates to specialist subagents as needed.

### presentation-designer

Specializes in visual design, color palettes, typography, and visual systems. Automatically invoked by presentation-builder when design decisions are needed.

### content-strategist

Specializes in information architecture, messaging strategy, and content structure. Automatically invoked by presentation-builder when content planning is needed.

## Available Skills

### presentation-builder skill

Complete workflow for creating reveal.js presentations:

- HTML scaffolding with create-presentation.js script
- CSS customization templates
- Incremental content editing patterns
- Overflow checking
- Screenshot validation
- Browser-based editing guide

### presentation-design-system skill

Design patterns, color palettes, typography guidance, and visual consistency strategies:

- 20+ color palette options (by topic)
- Typography hierarchy and font pairing
- Component styling patterns (boxes, cards, callouts)
- Accessibility standards (WCAG AA)
- CSS variables reference

### technical-presentations skill

Patterns for technical content:

- Code highlighting and line-number targeting
- Architecture diagrams (Mermaid)
- Data visualization (Chart.js)
- Process flows and flowcharts
- Comparison tables
- Terminal/console output styling

### business-presentations skill

Patterns for business presentations:

- Pitch deck structure (10-15 slides)
- Quarterly business review layouts
- Sales presentation patterns
- Key metrics dashboards
- Financial charts
- Customer case study templates
- Competitive positioning visuals
- Roadmap/timeline slides

## Folder Structure

```
.claude/
├── agents/
│   ├── presentation-builder.agent.md     # Main orchestrator agent
│   ├── presentation-designer.agent.md    # Design specialist subagent
│   └── content-strategist.agent.md       # Content strategist subagent
├── skills/
│   ├── presentation-builder/
│   │   ├── SKILL.md                      # Main workflow documentation
│   │   ├── scripts/
│   │   │   ├── create-presentation.js    # Scaffold generation
│   │   │   ├── check-overflow.js         # Overflow validation
│   │   │   └── edit-html.js              # Browser-based editor
│   │   └── references/
│   ├── presentation-design-system/
│   │   ├── SKILL.md                      # Design guidance
│   │   ├── assets/
│   │   │   ├── color-palettes.md
│   │   │   └── typography-guide.md
│   │   └── references/
│   ├── technical-presentations/
│   │   ├── SKILL.md                      # Technical patterns
│   │   └── assets/
│   ├── business-presentations/
│   │   ├── SKILL.md                      # Business patterns
│   │   └── assets/
│   └── ...
└── AGENTS.md                             # Agent reference and workflow
```

## Example Workflows

### Workflow 1: Create a Pitch Deck

1. **User**: "Create a 12-slide Series A pitch deck for our AI automation platform"
2. **presentation-builder**: Asks clarifying questions
   - Target investors/audience?
   - Key differentiators?
   - Current traction/metrics?
3. **content-strategist**: Creates slide outline
   - Problem, Solution, Market, Traction, Team, Ask structure
4. **presentation-designer**: Recommends color palette
   - Tech startup colors (electric blue + teal)
5. **presentation-builder**: Executes
   - Scaffolds 12-slide HTML
   - Fills content based on outline
   - Runs overflow checks
   - Reviews all screenshots
6. **Output**: presentation.html ready to present

### Workflow 2: Technical Presentation

1. **User**: "Build a 10-slide presentation about our microservices migration"
2. **presentation-builder**: Understands technical depth required
3. **content-strategist**: Creates structure
   - Problem, Architecture, Benefits, Implementation, Timeline
4. **presentation-designer**: Recommends dark theme
   - Better for code-heavy slides
5. **presentation-builder**: Executes
   - Creates technical slides with architecture diagrams
   - Includes code examples where relevant
   - Uses technical-presentations skill patterns
6. **Output**: Presentation with code, diagrams, and technical visuals

### Workflow 3: Quarterly Business Review

1. **User**: "Build a 20-slide QBR for our executive team"
2. **presentation-builder**: Gathers requirements
3. **content-strategist**: Creates dashboard layout
   - Metrics → Department updates → Forecasts
4. **presentation-designer**: Corporate color scheme
5. **presentation-builder**: Executes
   - Uses business-presentations skill for metric boxes
   - Includes charts for trends
   - Consistent dashboard layouts
6. **Output**: QBR presentation with data visualization

## Creating Presentations Manually

If you prefer more direct control, you can:

1. **Use the scaffold script** directly:
   ```bash
   node ./.claude/skills/presentation-builder/scripts/create-presentation.js \
     --slides 10 --output presentation.html
   ```

2. **Edit content incrementally** using the Edit tool
3. **Check for overflow** with the provided script
4. **Review screenshots** to validate visual quality
5. **Export to PDF** when ready

See [presentation-builder SKILL.md](./.claude/skills/presentation-builder/SKILL.md) for full details.

## Dependencies

Required for scripts (should be already installed):
- Node.js
- Puppeteer (for overflow checking)
- DeckTape (for PDF export and screenshots)
- Cheerio (for Chart.js validation)

Install if needed:
```bash
npm install puppeteer decktape cheerio
```

## Tips & Best Practices

✅ **Always review screenshots of EVERY slide** before declaring a presentation complete
✅ **Use consistent typography** — base text at 16pt, scale up on light slides with utility classes
✅ **Test colors for contrast** — ensure WCAG AA standards (4.5:1 for normal text, 3:1 for large text)
✅ **Vary slide layouts** — don't repeat the same pattern consecutively
✅ **Put text in proper elements** — use `<p>`, `<li>`, `<h1>`–`<h6>`, never bare text in `<div>`
✅ **Use CSS classes for repeated components** — stat boxes, cards, timelines (not inline styles)
✅ **Run overflow checks** — catch layout issues before visual review

## Troubleshooting

**Presentation looks wrong in browser:**
1. Check CSS variables are properly set
2. Verify text elements have proper CSS classes
3. Run screenshot validation
4. Check for color contrast issues

**Content overflowing slides:**
1. Run overflow checker: `node ./.claude/skills/presentation-builder/scripts/check-overflow.js presentation.html`
2. Reduce content or adjust font sizes
3. Modify column layouts if using multi-column
4. Re-run checks after fixes

**Images not showing:**
1. Check image paths are relative and correct
2. Verify images exist in expected directory
3. Check file permissions

**Charts not rendering:**
1. Verify Chart.js data format is valid JSON
2. Check `maintainAspectRatio: false` is set
3. Review flexbox container setup
4. See technical-presentations skill for chart patterns

## References

- [Reveal.js Documentation](https://revealjs.com/)
- [Agent Reference](./.claude/AGENTS.md)
- [Presentation Builder Skill](./.claude/skills/presentation-builder/SKILL.md)
- [Design System Skill](./.claude/skills/presentation-design-system/SKILL.md)
- [Technical Presentations Skill](./.claude/skills/technical-presentations/SKILL.md)
- [Business Presentations Skill](./.claude/skills/business-presentations/SKILL.md)

## Next Steps

1. **Try creating a presentation** — Ask presentation-builder to create a sample deck
2. **Customize colors** — Review presentation-design-system skill for palette options
3. **Learn patterns** — Explore technical and business presentation skills for layout ideas
4. **Export presentations** — Use DeckTape to generate PDFs from HTML files
