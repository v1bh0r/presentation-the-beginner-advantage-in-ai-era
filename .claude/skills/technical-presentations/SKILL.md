---
name: technical-presentations
description: "Design technical presentations with code, diagrams, and architecture. Use for software architecture, coding tutorials, data visualization, flow diagrams, API documentation, and technical deep-dives."
---

# Technical Presentations Skill

Patterns and best practices for technical presentations including code highlighting, architecture diagrams, data visualization, and flow documentation.

## When to Use

- Software architecture presentations
- Coding tutorials and training
- API documentation and technical deep-dives
- Algorithm explanations with visualizations
- System design presentations
- Data flow and process diagrams
- Technical conference talks
- Engineering team updates

## Content Patterns

### Code Snippets

**Displaying code in slides:**

```html
<section id="code-slide">
  <h2>Code Example</h2>
  <div style="display: grid; grid-template-columns: 1fr; gap: 20px;">
    <pre style="width: 100%; margin: 0;"><code class="language-javascript" data-line-numbers="1-5|6-10">
// Initialize API connection
const client = new ApiClient({
  endpoint: 'https://api.example.com',
  timeout: 5000
});

// Fetch data
const data = await client.get('/users');
console.log('Users:', data);
    </code></pre>
  </div>
</section>
```

**Code highlighting best practices:**
- Keep code snippets focused (5-15 lines maximum)
- Highlight key lines with `data-line-numbers="1-5|6-10"` (line number ranges)
- Use monospace fonts (Monaco, Courier New, Consolas)
- Ensure contrast between code background and text
- Comment code for clarity in presentation context
- Show only the most relevant parts (omit boilerplate)

**Language support:**
Reveal.js supports syntax highlighting via Highlight.js:
- javascript, python, java, cpp, rust, go, typescript, sql, html, css, bash, yaml, json, and more

### Architecture Diagrams

**Using Mermaid for diagrams:**

```html
<section id="architecture">
  <h2>System Architecture</h2>
  <div style="display: flex; justify-content: center; align-items: center; height: 100%;">
    <pre class="mermaid">
      graph LR
        Client["Client<br/>Web Browser"]
        API["API Server<br/>Node.js + Express"]
        DB["Database<br/>PostgreSQL"]
        Cache["Cache<br/>Redis"]
        
        Client -->|HTTP| API
        API -->|Query| DB
        API -->|Get/Set| Cache
        DB -->|Updates| Cache
    </pre>
  </div>
</section>
```

**Mermaid diagram types ideal for technical presentations:**
- **Flowchart** - Process flows, decision trees, algorithms
- **Sequence Diagram** - Interactions between components, timing
- **State Diagram** - State machines, finite state automata
- **Class Diagram** - Object-oriented design, inheritance hierarchies
- **Entity Relationship** - Database schemas, data models
- **Git Graph** - Version control branching strategy
- **Timeline** - Project milestones, release schedule

### Data Visualization

**Charts for metrics and trends:**

```html
<section style="display: flex; flex-direction: column; height: 100%;">
  <h2>Performance Metrics</h2>
  <div style="flex: 1; position: relative; min-height: 0;">
    <canvas data-chart="line">
    <!--
    {
      "data": {
        "labels": ["Jan", "Feb", "Mar", "Apr", "May", "Jun"],
        "datasets": [
          {
            "label": "Response Time (ms)",
            "data": [120, 115, 110, 105, 100, 95],
            "borderColor": "#2196F3",
            "fill": false,
            "tension": 0.4
          },
          {
            "label": "Error Rate (%)",
            "data": [2.5, 2.2, 1.8, 1.5, 1.2, 0.8],
            "borderColor": "#FF6B6B",
            "fill": false,
            "tension": 0.4
          }
        ]
      },
      "options": {
        "maintainAspectRatio": false,
        "responsive": true
      }
    }
    -->
    </canvas>
  </div>
</section>
```

**Chart types:**
- **Line** - Trends over time, performance metrics
- **Bar** - Comparisons, rankings, benchmarks
- **Pie** - Distribution, percentages
- **Scatter** - Correlations, outliers

### Flow Diagrams

**Visualize processes and workflows:**

```html
<section id="process-flow">
  <h2>Request Processing Pipeline</h2>
  <div style="display: grid; grid-template-columns: repeat(5, 1fr); gap: 15px; align-items: center;">
    <div style="background: #2196F3; color: white; padding: 15px; border-radius: 8px; text-align: center;">
      <strong>Request</strong>
    </div>
    <div style="text-align: center; font-size: 20pt;">→</div>
    <div style="background: #4CAF50; color: white; padding: 15px; border-radius: 8px; text-align: center;">
      <strong>Validate</strong>
    </div>
    <div style="text-align: center; font-size: 20pt;">→</div>
    <div style="background: #FF9800; color: white; padding: 15px; border-radius: 8px; text-align: center;">
      <strong>Process</strong>
    </div>
  </div>
  <div style="display: grid; grid-template-columns: repeat(5, 1fr); gap: 15px; align-items: center; margin-top: 20px;">
    <div style="grid-column: 5;">
      <div style="background: #9C27B0; color: white; padding: 15px; border-radius: 8px; text-align: center;">
        <strong>Response</strong>
      </div>
    </div>
    <div style="grid-column: 5; text-align: center; font-size: 20pt; margin-top: 20px;">↑</div>
  </div>
</section>
```

### Comparison Tables

**Side-by-side technology comparisons:**

```html
<section id="comparison">
  <h2>Database Comparison</h2>
  <div style="font-size: 14pt;">
    <table style="width: 100%; border-collapse: collapse;">
      <tr style="background: #2196F3; color: white;">
        <th style="padding: 10px; border: 1px solid #ddd;">Feature</th>
        <th style="padding: 10px; border: 1px solid #ddd;">PostgreSQL</th>
        <th style="padding: 10px; border: 1px solid #ddd;">MongoDB</th>
        <th style="padding: 10px; border: 1px solid #ddd;">Redis</th>
      </tr>
      <tr>
        <td style="padding: 10px; border: 1px solid #ddd;"><strong>Type</strong></td>
        <td style="padding: 10px; border: 1px solid #ddd;">Relational</td>
        <td style="padding: 10px; border: 1px solid #ddd;">Document</td>
        <td style="padding: 10px; border: 1px solid #ddd;">In-Memory</td>
      </tr>
      <tr style="background: #f5f5f5;">
        <td style="padding: 10px; border: 1px solid #ddd;"><strong>Query Speed</strong></td>
        <td style="padding: 10px; border: 1px solid #ddd;">Fast</td>
        <td style="padding: 10px; border: 1px solid #ddd;">Very Fast</td>
        <td style="padding: 10px; border: 1px solid #ddd;">Fastest</td>
      </tr>
      <tr>
        <td style="padding: 10px; border: 1px solid #ddd;"><strong>ACID</strong></td>
        <td style="padding: 10px; border: 1px solid #ddd;">✅ Yes</td>
        <td style="padding: 10px; border: 1px solid #ddd;">Partial</td>
        <td style="padding: 10px; border: 1px solid #ddd;">No</td>
      </tr>
    </table>
  </div>
</section>
```

### Terminal/Console Output

**Show command-line interactions:**

```html
<section id="terminal">
  <h2>Running Tests</h2>
  <pre style="background: #1e1e1e; color: #00FF00; padding: 20px; border-radius: 8px; text-align: left; font-size: 13pt;">
$ npm test

 PASS  tests/api.test.js
  ✓ GET /users returns 200 (45ms)
  ✓ POST /users creates user (123ms)
  ✓ DELETE /users/:id removes user (67ms)

 PASS  tests/db.test.js
  ✓ Connection established (12ms)
  ✓ Query returns correct data (34ms)

Tests:       5 passed, 5 total
Time:        1.234 s
  </pre>
</section>
```

## Color Scheme Recommendations

**For technical presentations:**

- **Dark theme** - Reduces eye strain for code-heavy slides
  ```css
  --background-color: #1e1e2e;
  --text-color: #e0e0e0;
  --primary-color: #00d4ff;    /* Cyan for highlights */
  --secondary-color: #00ff88;  /* Lime for success */
  --accent-color: #ff6b6b;     /* Red for warnings/errors */
  ```

- **Light theme** - Professional for client presentations
  ```css
  --background-color: #ffffff;
  --text-color: #222;
  --primary-color: #0066ff;    /* Electric blue */
  --secondary-color: #00aa66;  /* Tech green */
  --accent-color: #ff4455;     /* Alert red */
  ```

## Layout Patterns

### Code + Explanation (Side-by-side)

```html
<section>
  <h2>Example Implementation</h2>
  <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 30px;">
    <div>
      <h4>Code</h4>
      <pre><code class="language-python">
def fibonacci(n):
  if n <= 1:
    return n
  return (fibonacci(n-1) + 
          fibonacci(n-2))
      </code></pre>
    </div>
    <div>
      <h4>Explanation</h4>
      <ul style="font-size: 14pt;">
        <li>Base case: n ≤ 1 returns n</li>
        <li>Recursive case: sum previous two</li>
        <li>Time: O(2^n) exponential</li>
        <li>Space: O(n) call stack depth</li>
      </ul>
    </div>
  </div>
</section>
```

### Diagram + Notes (Side-by-side)

```html
<section>
  <h2>Authentication Flow</h2>
  <div style="display: grid; grid-template-columns: 2fr 1fr; gap: 30px;">
    <div>
      <!-- Mermaid diagram here -->
    </div>
    <div>
      <h4>Key Points</h4>
      <ul style="font-size: 14pt;">
        <li>JWT tokens issued on login</li>
        <li>Tokens stored in localStorage</li>
        <li>Include in Authorization header</li>
        <li>Server validates signature</li>
      </ul>
    </div>
  </div>
</section>
```

## Technical Best Practices

1. **Keep code snippets focused** - Maximum 15 lines per slide
2. **Highlight key lines** - Use `data-line-numbers` to emphasize important parts
3. **Use consistent color schemes** - Dark backgrounds for code, light text
4. **Provide explanatory text** - Don't assume viewers understand code without context
5. **Test all diagrams** - Render Mermaid diagrams before presenting
6. **Avoid live coding** - Pre-write examples to minimize errors during presentation
7. **Include speaker notes** - Explain complex concepts in presenter mode
8. **Use monospace fonts** - For code and technical terms (Monaco, Courier, Consolas)

## Accessibility for Technical Content

- Ensure code blocks have sufficient contrast (light text on dark background)
- Provide transcripts for terminal/output examples
- Include text descriptions of diagrams in speaker notes
- Use semantic HTML for tables (proper `<th>`, `<td>` tags)
- Test color-blind safe color palettes for charts
