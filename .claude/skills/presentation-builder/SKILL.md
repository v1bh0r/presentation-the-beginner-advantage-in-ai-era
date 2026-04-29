---
name: presentation-builder
description: "Create professional reveal.js presentations from concept to deployment. Use when building presentations, generating HTML/CSS, scaffolding slides, checking overflow, reviewing visuals, exporting to PDF, or polishing presentations for delivery."
---

# Presentation Builder Skill

Complete workflow for creating reveal.js presentations using natural language planning, automated scaffolding, incremental content filling, validation, and visual review.

## When to Use

- Create a new presentation from scratch
- Generate HTML + CSS reveal.js files
- Fill in slide content incrementally
- Check for content overflow across slides
- Review screenshots and validate visual quality
- Export presentations to PDF
- Edit presentations with browser-based editor
- Refine presentation themes and styling

## What You Create

A reveal.js presentation consists of:
1. **presentation.html** - Slides with content, loads reveal.js from CDN
2. **styles.css** - Custom theme with colors, typography, and component styles
3. **Optional**: scripts/ folder for helper utilities, assets/ for images/resources

No build step required — open HTML in a browser to present. Can export to PDF.

## Complete Workflow

### Step 1: Plan Presentation Structure

**Input from user:**
- Topic/content for presentation
- Intended audience and purpose
- Desired number of slides (or section breakdown)
- Any branding/style preferences

**Your analysis:**
- Determine total slide count
- Identify section dividers (centered title slides for transitions)
- Plan vertical slide stacks for drill-down content (when needed)
- Note any special requirements (charts, code, images, technical content)

**Output:** Slide structure plan (e.g., "intro (1 slide), content section (4 slides), section break (1), data viz (3 slides), closing (1)")

### Step 2: Generate HTML Scaffold

Use [create-presentation.js](./scripts/create-presentation.js) to generate the initial HTML structure.

**Finding the script:** The script is at `.claude/skills/presentation-builder/scripts/create-presentation.js`

**Run scaffold generation:**

```bash
node ./.claude/skills/presentation-builder/scripts/create-presentation.js \
  --structure 1,1,1,d,3,d,1 \
  --title "My Presentation Title" \
  --output presentation.html \
  --styles styles.css
```

**Structure format (comma-separated):**
- `1` = single horizontal slide
- `N` (where N > 1) = vertical stack of N slides
- `d` = section divider slide (centered, minimal content)

**Examples:**
```bash
# 10 horizontal slides
node ./.claude/skills/presentation-builder/scripts/create-presentation.js \
  --slides 10 \
  --output presentation.html

# Mixed: intro, 2 content, divider, 3-stack, divider, closing
node ./.claude/skills/presentation-builder/scripts/create-presentation.js \
  --structure 1,1,1,d,3,d,1 \
  --title "Q4 Review" \
  --output presentation.html
```

**Output:**
- `presentation.html` - Scaffold with placeholder slides
- `styles.css` - Base theme with CSS variables
- Each slide has unique `id` (e.g., `slide-1`, `slide-2`) for targeting

### Step 3: Customize CSS Theme

Edit `styles.css` to define colors, typography, and component styles.

**CSS Variable Strategy:**
The base styles.css includes variables at `:root` for easy customization:

```css
:root {
  /* Background */
  --background-color: #ffffff;  /* Change for dark themes */
  
  /* Typography - ALWAYS use pt for font sizes */
  --heading-font: "Source Sans Pro", Helvetica, sans-serif;
  --body-font: "Source Sans Pro", Helvetica, sans-serif;
  --base-font-size: 32px;  /* Only px here - reveal.js base */
  --text-size: 16pt;       /* Base body text size */
  --h1-size: 48pt;
  --h2-size: 36pt;
  --h3-size: 24pt;
  
  /* Colors - customize per presentation */
  --primary-color: #2196F3;
  --secondary-color: #ff9800;
  --text-color: #222;
  --muted-color: #666;
}
```

**Key rules:**
- Use `pt` (points) for all font sizes EXCEPT `--base-font-size` (which is `px`)
- Base text size is intentionally small (16pt) to fit more content
- Use utility classes (.text-lg, .text-xl, .text-2xl, etc.) to scale text on light-content slides
- Define custom component styles below `:root` (blockquotes, stat boxes, cards, etc.)

**Typography guidance:**
- Font sizes in points are predictable across browsers (familiar from PowerPoint/Keynote)
- Consistency across slides prevents jarring size changes
- Use `.text-lg` through `.text-4xl` utilities when slides have less content

**Color palette strategy:**
- Pick 5 colors: dominant (primary), secondary, accent, text, background
- Ensure contrast for readability (WCAG AA at minimum)
- Test light text on dark backgrounds and vice versa

### Step 4: Fill in HTML Content

**IMPORTANT:** Use incremental editing — fill slides one or a few at a time. Do NOT rewrite the entire HTML file at once.

The scaffold generates unique placeholder text per slide (e.g., `Slide 2 Title Here`), so each section is targetable with the Edit tool.

**Standard slide structure:**

```html
<section id="unique-slide-id">
  <h2>Slide Title</h2>
  <div class="content">
    <!-- Main content here -->
  </div>
</section>
```

**Multi-column layouts** — use inline CSS Grid (no utility classes):

```html
<!-- Two equal columns -->
<div style="display: grid; grid-template-columns: repeat(2, 1fr); gap: 30px;">
  <div>
    <h3>Column 1 Title</h3>
    <p>Content here</p>
  </div>
  <div>
    <h3>Column 2 Title</h3>
    <p>Content here</p>
  </div>
</div>

<!-- Three columns -->
<div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 25px;">
  <div>Col 1</div>
  <div>Col 2</div>
  <div>Col 3</div>
</div>

<!-- Unequal: narrow sidebar + wide content -->
<div style="display: grid; grid-template-columns: 1fr 2fr; gap: 30px;">
  <div>Sidebar</div>
  <div>Main content</div>
</div>
```

**Important patterns:**
- Every `<section>` must have unique `id` for stable identification
- Use `class="section-divider"` for centered section title slides
- Wrap main content in `<div class="content">` — it's a flexbox container for spacing
- Use `<div class="footnote">` for source attribution at bottom
- **Never put text directly in `<span>` or `<div>` — they won't inherit base styles!**
- Use `<p>`, `<li>`, `<h1>`–`<h6>` for all visible text (they inherit font size, color, line-height)

**Inline styles are OK for:**
- Layout containers (grid, flex with specific ratios)
- One-off positioning needs

**Create CSS classes for:**
- Visual patterns that repeat 3+ times (stat boxes, cards, timeline steps)
- Component styling (blockquotes, callout boxes, badges)

### Step 5: Check for Content Overflow

Run the overflow checker to catch content that extends beyond slide boundaries:

```bash
cd <presentation-directory>
node ./.claude/skills/presentation-builder/scripts/check-overflow.js presentation.html
```

**Output:** Reports slides with:
- **Vertical overflow**: Content taller than slide height
- **Horizontal overflow**: Content wider than slide width

**Fix overflow:**
1. Reduce content (shorten text, fewer bullet points)
2. Adjust font sizes on specific slides (.text-lg/.text-sm)
3. Modify column ratios in grid layouts
4. Use vertical slide stacks for related content

Re-run overflow checker after fixes to confirm.

### Step 6: Visual Review with Screenshots

The overflow script catches layout issues, but visual problems need human review:

1. **Color inheritance in containers** - Text inside styled containers may inherit wrong color
2. **Icon rendering** - Font Awesome icons may not load (empty squares)
3. **Text wrapping** - Text may wrap unexpectedly in columns
4. **List styling** - Bullets may not contrast well on all backgrounds
5. **Complex layouts** - Nested grids occasionally slip through overflow detection

**Capture screenshots of all slides:**

```bash
cd <presentation-directory>
npx decktape reveal "presentation.html?export" output.pdf \
  --screenshots \
  --screenshots-directory "screenshots/$(date +%Y%m%d_%H%M%S)"
```

The `?export` query parameter disables chart animations for cleaner PDF rendering.

Creates timestamped folder (e.g., `screenshots/20241210_143052/`) for version comparison.

**Review every screenshot:**
- Check text readability on all backgrounds
- Verify color contrast meets WCAG standards
- Look for unexpected text wrapping or overflow
- Confirm icons render correctly
- Review section dividers and transitions
- Validate visual hierarchy (titles > headings > body text)

**Capture specific slides after fixes:**

```bash
npx decktape reveal "presentation.html?export" output.pdf \
  --screenshots \
  --screenshots-directory "screenshots/$(date +%Y%m%d_%H%M%S)" \
  --slides 2,5,7-9
```

### Step 7: Iterate on Issues

Fix any problems found during screenshot review:

1. **Color issues** - Update CSS variables or add color rules to specific containers
2. **Overflow** - Reduce content or adjust font sizes
3. **Contrast** - Change text color, background color, or font weight
4. **Layout** - Adjust grid columns, gaps, padding, or text alignment
5. **Typography** - Use text utility classes (.text-lg, .text-xl) for visual balance

After each fix, re-run overflow checker and re-capture screenshots of affected slides.

### Step 8: Browser Editing (Optional)

After generating the presentation, users can edit text directly in the browser:

```bash
node ./.claude/skills/presentation-builder/scripts/edit-html.js presentation/presentation.html
```

Opens a local server where they can:
- Click any text to edit inline
- Press Escape to deselect
- Click Save to write changes back to the file
- Press Ctrl+C to stop the server

Perfect for wordsmithing, fixing typos, or tweaking copy.

### Step 9: Export to PDF (Optional)

Generate PDF from the HTML presentation:

```bash
cd <presentation-directory>
npx decktape reveal "presentation.html" output.pdf
```

The PDF preserves colors, layouts, and transitions (within PDF limitations).

## Design Principles

### Content Organization

- **Diverse presentation** - Vary layouts across slides (columns, stacks, cards, text blocks)
- **Scannable content** - Short bullet points, one main idea per slide
- **Visual balance** - When slides have less content, scale text larger (use .text-xl, .text-2xl)
- **Consistency** - Repeat design patterns, spacing, and typography across slides

### Typography

- **ALWAYS use `pt` for font sizes** - Never em, rem, or px (except --base-font-size)
- **Base text intentionally small** - 16pt to fit more content
- **Scale up on light slides** - Use .text-lg, .text-xl, .text-2xl utilities
- **Clear hierarchy** - h1 > h2 > h3 > body, visual weight through color and size

### Color Strategy

- **Analyze the topic** - Choose colors that match the presentation subject
- **Avoid autopilot** - Don't default to blue for business, green for sustainability, etc.
- **Build a palette** - 3-5 colors: dominant + supporting + accent
- **Test contrast** - Verify readability on all background colors
- **Consider cultural context** - Colors have different meanings in different regions

### Slide Layouts

Vary your layouts to maintain visual interest:

1. **Title/intro** - Centered, large text, topic-focused
2. **Content** - Left-aligned, 1-2 columns, bullet points or numbered list
3. **Section divider** - Centered title, minimal content (use `class="section-divider"`)
4. **Stat/callout** - Large number or quote, emphasis on data
5. **Visual** - Image-forward with minimal text overlay
6. **2-column** - Comparison, side-by-side concepts, image + text
7. **3-column** - Multiple items, feature list, process steps
8. **Closing** - Summary, key takeaway, call-to-action

## Key Requirements

✅ **CRITICAL: Review screenshots of EVERY slide** — Do not skip slides
✅ Use web-safe fonts (Arial, Helvetica, Georgia, Verdana) or Google Fonts via @import
✅ Ensure strong contrast between text and background (WCAG AA minimum)
✅ Use consistent spacing, padding, and alignment across slides
✅ All visible text in proper elements (`<p>`, `<li>`, `<h1>`–`<h6>`)
✅ Inline styles for one-off layouts, CSS classes for repeated patterns
✅ Run overflow checker — catch content overflow before visual review
✅ Provide browser editing command to user when complete

## References

- [Chart.js Integration](./references/charts.md) - Data visualization with Chart.js
- [Advanced Features](./references/advanced-features.md) - Fragments, speaker notes, animations
- [Base Styles Reference](./references/base-styles.md) - CSS variables, typography, component styles

## Next Steps for Users

After presentation generation, suggest:

1. **Text refinement** - Use browser editor for wordsmithing
2. **Visual customization** - Modify CSS variables for different color schemes
3. **PDF export** - Generate PDF for sharing or archival
4. **Presenter mode** - Use reveal.js presenter mode (press 'S' during presentation)
5. **Version control** - Commit presentation.html and styles.css to git
