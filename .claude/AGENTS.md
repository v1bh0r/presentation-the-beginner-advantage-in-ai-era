---
description: "Presentation creation agents for orchestrating and specializing slide building. Use presentation-builder as the main entry point for creating presentations, delegating to presentation-designer for theming and content-strategist for structure."
---

# Presentation Agents

Three specialized agents for presentation creation, each with focused responsibilities:

## presentation-builder

**Role**: Main orchestrator for creating presentations

**Invoked by**: Users asking to create presentations, build slides, design decks

**Responsibilities**:

- Understand user requirements and clarify presentation goals
- Delegate design decisions to presentation-designer
- Coordinate content structure with content-strategist
- Execute full reveal.js workflow (scaffolding, content, validation)
- Validate output (overflow checks, screenshot review)
- Guide final refinements

**Tools**: `read`, `edit`, `search`, `execute` (full workflow capability)

**User-invocable**: Yes

**Subagents**: presentation-designer, content-strategist

## presentation-designer

**Role**: Visual design specialist

**Invoked by**: presentation-builder when design decisions are needed

**Responsibilities**:

- Select appropriate color palettes based on topic and audience
- Define typography hierarchy and font choices
- Recommend layout patterns for different content types
- Ensure visual consistency and accessibility standards
- Align designs with brand identity

**Tools**: `read`, `search` (research-only, no execution)

**User-invocable**: No (subagent only)

## content-strategist

**Role**: Information architect and messaging expert

**Invoked by**: presentation-builder when content structure is needed

**Responsibilities**:

- Analyze presentation goals, audience, and key messages
- Create detailed slide outlines with content strategy
- Establish narrative flow and information hierarchy
- Balance slide types for visual variety
- Craft compelling messaging and messaging strategy

**Tools**: `read`, `search` (research-only, no execution)

**User-invocable**: No (subagent only)

---

## How to Use These Agents

### Primary Workflow

1. **User asks presentation-builder** to create a presentation
   - "Create a pitch deck for our Series A fundraise"
   - "Build a 10-slide presentation about our Q3 results"

2. **presentation-builder analyzes** the request and asks clarifying questions

3. **presentation-builder delegates to content-strategist** for outline and structure

4. **presentation-builder delegates to presentation-designer** for color palette and theme

5. **presentation-builder executes** the full workflow:
   - Uses presentation-builder skill to scaffold HTML
   - Fills in content using provided outline
   - Runs overflow checks
   - Reviews screenshots
   - Iterates on issues

6. **presentation-builder delivers** the finished presentation with editing commands

### When to Invoke Directly

- **presentation-builder**: Always the entry point for presentation creation
- **presentation-designer**: Only when you want specialized design advice (not typical user path)
- **content-strategist**: Only when you want specialized content structure advice (not typical user path)

### Examples

**Start a presentation:**
> "Create a 15-slide pitch deck about our AI automation platform. We're targeting Series A investors."

**Design consultation:**
> "(Request to presentation-designer) What color palette would work for a healthcare technology presentation targeting hospital administrators?"

**Content planning:**
> "(Request to content-strategist) Help me structure a quarterly business review presentation for 50 employees."

---

## Agent Selection Decision Tree

```text
User asks about presentations?
├─ YES: Route to presentation-builder
│  ├─ Needs full presentation generation?
│  │  └─ YES: Execute presentation-builder workflow
│  │  └─ NO: Ask clarifying questions
│  └─ Needs specialized design advice?
│     └─ DELEGATE to presentation-designer
│  └─ Needs content structure advice?
│     └─ DELEGATE to content-strategist
└─ NO: Use different agent/workflow
```
