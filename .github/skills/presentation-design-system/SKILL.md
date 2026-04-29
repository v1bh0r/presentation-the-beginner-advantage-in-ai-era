---
name: presentation-design-system
description: "Design presentation themes and create cohesive visual systems. Use for color palettes, typography guidance, design system decisions, brand alignment, CSS customization, and visual consistency strategies."
---

# Presentation Design System Skill

Comprehensive guidance for designing professional, cohesive presentation themes that match your content and audience.

## When to Use

- Select appropriate color palettes for your topic
- Define typography hierarchy and font choices
- Create consistent visual components (boxes, cards, callouts)
- Align presentations with brand guidelines
- Establish design systems for multi-presentation projects
- Customize CSS variables for different color schemes
- Ensure accessibility and readability standards
- Review design decisions for visual consistency

## Design Principles

### Color Palette Selection

**Choose colors strategically:**

1. **Analyze the topic** - What mood, industry, or energy does the presentation convey?
2. **Consider audience** - What color associations matter to your audience?
3. **Avoid autopilot** - Don't default to blue for finance, green for sustainability
4. **Think beyond clichés** - A healthcare presentation can use warm earth tones
5. **Build a palette** - Select 3-5 colors that work together
   - **Dominant** (60%) - Primary color for headers, backgrounds
   - **Supporting** (30%) - Secondary color for accents, borders
   - **Accent** (10%) - Highlight color for calls-to-action
   - **Text** - Ensure contrast on dominant background
   - **Background** - Usually white/light or dark gray/black

6. **Test contrast** - Verify readability with [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
7. **Consider light & dark modes** - Some presentations shown on light backgrounds, others on dark

**Palette Inspiration (by topic):**

**Technology/Innovation:**
- Vibrant blue (#2196F3) + dark gray (#333) + accent teal (#00BCD4)
- Or: Purple (#9C27B0) + dark blue (#1A237E) + neon pink (#E91E63)

**Finance/Business:**
- Deep navy (#003D7A) + gold (#D4AF37) + charcoal (#2C3E50)
- Or: Teal (#0097A7) + slate gray (#455A64) + accent gold (#FFC107)

**Healthcare/Wellness:**
- Warm terracotta (#CD6E45) + sage green (#7CB342) + cream (#F5F5F0)
- Or: Coral (#FF7043) + mint (#4DB6AC) + light gray (#ECEFF1)

**Creative/Design:**
- Bold magenta (#E91E63) + cyan (#00BCD4) + charcoal (#212121)
- Or: Burnt orange (#E65100) + teal (#006064) + cream (#FFFDE7)

**Education:**
- Warm yellow (#FDD835) + navy (#1565C0) + light gray (#F5F5F5)
- Or: Turquoise (#0097A7) + orange (#FF6F00) + white (#FFFFFF)

**Tech Startups:**
- Bright electric blue (#0066FF) + deep purple (#5D00FF) + accent lime (#00FF88)
- Or: Modern slate (#2C3E50) + vibrant teal (#1ABC9C) + accent pink (#E74C3C)

**Sustainability:**
- Forest green (#1B5E20) + earth brown (#5D4037) + sage (#8BC34A) + cream (#FFFDE7)
- Or: Ocean blue (#006064) + leaf green (#33691E) + sand (#BCAAA4)

### Typography Strategy

**Font Selection:**

- **Web-safe fonts** (no Google Fonts needed):
  - Serif: Georgia, Times New Roman
  - Sans-serif: Arial, Helvetica, Verdana, Trebuchet MS
  
- **Google Fonts** (via @import in CSS):
  ```css
  @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700&family=Lato:wght@300;400;600&display=swap');
  
  :root {
    --heading-font: "Playfair Display", Georgia, serif;
    --body-font: "Lato", Helvetica, sans-serif;
  }
  ```

- **Pairing strategy**:
  - Serif + Sans-serif: Classic, works for any topic
  - Sans-serif + Sans-serif (different weights): Modern, clean
  - Display font + Sans-serif: Creative, adds personality

**Font Size Hierarchy:**

```css
--base-font-size: 32px;     /* Reveal.js base (px only) */
--text-size: 16pt;          /* Base body text */
--h1-size: 48pt;            /* Slide title */
--h2-size: 36pt;            /* Major heading */
--h3-size: 24pt;            /* Subheading */
```

**Scaling for content density:**

- **Content-heavy slides** - Keep small (base 16pt) to fit more
- **Content-light slides** - Scale up with utility classes:
  ```css
  .text-lg  { font-size: 18pt; }   /* Slightly larger */
  .text-xl  { font-size: 20pt; }   /* Medium emphasis */
  .text-2xl { font-size: 24pt; }   /* Strong emphasis */
  .text-3xl { font-size: 28pt; }   /* Very large */
  .text-4xl { font-size: 32pt; }   /* Maximum body text */
  ```

**Typography guidance:**
- Always use `pt` (points) for slide text — predictable, familiar from PowerPoint
- Never use `em` or `rem` for slide content (they scale with reveal.js base)
- Consistent hierarchy prevents cognitive load on viewers
- Prioritize readability over style

### Color Usage in Practice

**Text on backgrounds:**

```css
/* Light background (default) */
--background-color: #ffffff;
--text-color: #222;           /* Dark text on light */
--muted-color: #666;          /* Lighter gray for secondary text */

/* Dark background */
--background-color: #1A1A2E;
--text-color: #FAF7F2;        /* Light text on dark */
--muted-color: #BBB;          /* Light gray for secondary text */
```

**Container styling:**

```css
.callout {
  background-color: var(--primary-color);
  color: #ffffff;            /* Ensure light text on colored background */
  padding: 20px;
  border-radius: 8px;
}

.callout strong {
  color: var(--secondary-color);  /* Accent color for emphasis */
}
```

### Component Patterns

**Stat boxes** (repeated element — use a CSS class):

```css
.stat-box {
  text-align: center;
  padding: 20px;
  background: var(--primary-color);
  color: white;
  border-radius: 8px;
}

.stat-box .number {
  font-size: 48pt;
  font-weight: bold;
  display: block;
}

.stat-box .label {
  font-size: 14pt;
  margin-top: 10px;
}
```

**Feature cards** (side-by-side items):

```css
.feature-card {
  padding: 20px;
  background: #f5f5f5;
  border-left: 4px solid var(--primary-color);
}

.feature-card h3 {
  margin: 0 0 10px 0;
}

.feature-card p {
  margin: 0;
  font-size: 14pt;
}
```

**Blockquotes** (standard styling):

```css
.reveal blockquote {
  border-left: 4px solid var(--primary-color);
  padding-left: 20px;
  margin: 20px 0;
  font-style: italic;
  background: none;
  box-shadow: none;
  width: 100%;
}
```

### Accessibility Standards

**WCAG AA Contrast Ratios (minimum):**
- Large text (18pt+): 3:1 contrast ratio
- Normal text: 4.5:1 contrast ratio
- Graphics/UI components: 3:1 contrast ratio

**Quick checks:**
- Can you read white text on your primary color? (3:1 minimum)
- Can you read black text on your secondary color? (4.5:1 minimum)
- Are section dividers visually distinct from content slides?
- Do interactive elements (links, buttons) have sufficient contrast?

**Tools:**
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
- [WAVE Browser Extension](https://wave.webaim.org/extension/)

## CSS Variable Reference

**Base template for customization:**

```css
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@600;700&family=Lato:wght@300;400;600&display=swap');

:root {
  /* ========== BACKGROUND ========== */
  --background-color: #ffffff;      /* Light: #ffffff, Dark: #1a1a2e */
  
  /* ========== TYPOGRAPHY ========== */
  --heading-font: "Playfair Display", Georgia, serif;
  --body-font: "Lato", Helvetica, sans-serif;
  --base-font-size: 32px;           /* Reveal.js base (px only) */
  --text-size: 16pt;                /* Base body */
  --h1-size: 48pt;                  /* Slide title */
  --h2-size: 36pt;                  /* Major heading */
  --h3-size: 24pt;                  /* Subheading */
  
  /* ========== COLORS ========== */
  --primary-color: #2196F3;         /* Dominant color */
  --secondary-color: #ff9800;       /* Supporting color */
  --accent-color: #e91e63;          /* Highlight/CTA */
  --text-color: #222;               /* Primary text */
  --muted-color: #666;              /* Secondary text/muted */
  --border-color: #ddd;             /* Borders, dividers */
  
  /* ========== SPACING ========== */
  --slide-padding: 40px 60px;       /* Slide padding */
  --gutter: 30px;                   /* Gap between columns */
}
```

**Applying to reveal.js:**

```css
.reveal {
  font-family: var(--body-font);
  background-color: var(--background-color);
}

.reveal h1, .reveal h2, .reveal h3 {
  font-family: var(--heading-font);
  color: var(--text-color);
  text-transform: none;
}

.reveal h1 { font-size: var(--h1-size); }
.reveal h2 { font-size: var(--h2-size); }
.reveal h3 { font-size: var(--h3-size); }

.reveal p, .reveal li {
  font-size: var(--text-size);
  color: var(--text-color);
}

.reveal .slides section {
  padding: var(--slide-padding);
  text-align: left;
}
```

## Design Checklist

Before finalizing your theme, verify:

✅ Color palette matches presentation topic and audience
✅ Text contrast meets WCAG AA standards on all backgrounds
✅ Typography hierarchy is clear (h1 > h2 > h3 > body)
✅ Font choices are professional and appropriate
✅ CSS variables are consistently named and organized
✅ Component styles repeat for consistency (not one-off inline styles)
✅ Spacing and padding are consistent across slides
✅ Icons (Font Awesome) load and display correctly
✅ All colors tested on both light and dark content
✅ Mobile/small-screen text remains readable

## References

- [Reveal.js Official Colors/Themes](https://revealjs.com/themes/)
- [Google Fonts Pairing Guide](https://www.typewolf.com/)
- [WCAG Contrast Guidelines](https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum)
