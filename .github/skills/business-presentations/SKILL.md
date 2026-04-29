---
name: business-presentations
description: "Create business presentations with data, charts, and professional layouts. Use for pitch decks, quarterly reports, sales decks, stakeholder updates, financial presentations, and executive summaries."
---

# Business Presentations Skill

Patterns and strategies for professional business presentations including pitch decks, reports, data visualization, and executive communication.

## When to Use

- Pitch decks (seed funding, Series A, product launches)
- Quarterly business reviews (QBR)
- Sales and marketing presentations
- Financial reports and investor updates
- Executive summaries and briefings
- Board of directors presentations
- Team performance reviews
- Strategic planning presentations
- Client proposals and case studies

## Presentation Types

### Pitch Deck (Funding)

**Typical structure (10-15 slides):**

1. **Title Slide** - Company, founder names, date
2. **Problem** - What problem are you solving? Show pain points
3. **Solution** - Your product/service. Why is it unique?
4. **Market Size** - TAM (Total Addressable Market), growth potential
5. **Business Model** - How do you make money?
6. **Traction** - Customers, revenue, growth metrics
7. **Team** - Founder/executive bios, relevant experience
8. **Competition** - Who are competitors? Your differentiation?
9. **Use of Funds** - How will you spend the investment?
10. **Financial Projections** - Revenue forecast, path to profitability
11. **Vision & Roadmap** - 12-18 month plan
12. **Call to Action** - Investment amount, next steps

**Design strategy:**
- Clean, professional aesthetic (avoid clutter)
- Consistent color palette (typically 2-3 colors max)
- Data-driven visuals (charts, not just text)
- Strong visual hierarchy (titles prominent, supporting text secondary)
- Every slide answers a specific question

### Quarterly Business Review (QBR)

**Typical structure (20-25 slides):**

1. **Cover** - Company, period, date
2. **Executive Summary** - Key metrics, wins, challenges
3. **Financial Overview** - Revenue, expenses, profitability trend
4. **Key Metrics** - Customer count, retention, churn rate
5-8. **Department Updates** - Sales, Marketing, Engineering, Product (1-2 slides each)
9. **Challenges & Risks** - What went wrong? Mitigation strategies
10. **Wins & Celebrations** - Major milestones, team achievements
11. **Forecasts** - Next quarter outlook
12. **Questions** - Final slide

**Design strategy:**
- Use consistent dashboard layouts for metrics
- Include year-over-year (YoY) comparisons
- Highlight variances from plan
- Use consistent color coding (green = good, red = concerning, yellow = watch)

### Sales Deck

**Typical structure (15-20 slides):**

1. **Title** - Product/service, benefit statement
2. **About Your Company** - Credibility, market position
3. **Customer Problem** - Paint the pain
4. **Your Solution** - How you solve it uniquely
5-8. **Product Features & Benefits** - 2-4 core features with customer impact
9. **Customer Success Stories** - Case studies, testimonials
10. **Differentiation** - Why choose you over competitors?
11. **Pricing/Investment** - Cost structure, ROI
12. **Implementation Timeline** - How quickly they can see results
13. **Call to Action** - Next steps, contact info

**Design strategy:**
- Customer-focused language (not technical specs)
- Visual demonstrations of product value
- Include ROI calculations or cost savings
- Case studies with measurable results
- Clear call-to-action on closing slide

## Content Patterns

### Key Metrics Dashboard

**Multi-metric overview slide:**

```html
<section id="metrics">
  <h2>Q3 Performance Overview</h2>
  <div style="display: grid; grid-template-columns: repeat(4, 1fr); gap: 20px; margin-top: 30px;">
    <div style="background: #2196F3; color: white; padding: 25px; border-radius: 8px; text-align: center;">
      <div style="font-size: 48pt; font-weight: bold;">$2.4M</div>
      <div style="font-size: 16pt; margin-top: 10px;">Quarterly Revenue</div>
      <div style="font-size: 14pt; margin-top: 5px; color: #e3f2fd;">↑ 23% YoY</div>
    </div>
    <div style="background: #4CAF50; color: white; padding: 25px; border-radius: 8px; text-align: center;">
      <div style="font-size: 48pt; font-weight: bold;">1,247</div>
      <div style="font-size: 16pt; margin-top: 10px;">Active Customers</div>
      <div style="font-size: 14pt; margin-top: 5px; color: #e8f5e9;">↑ 18% QoQ</div>
    </div>
    <div style="background: #FF9800; color: white; padding: 25px; border-radius: 8px; text-align: center;">
      <div style="font-size: 48pt; font-weight: bold;">94.2%</div>
      <div style="font-size: 16pt; margin-top: 10px;">Customer Retention</div>
      <div style="font-size: 14pt; margin-top: 5px; color: #fff3e0;">↑ 2.1% from Q2</div>
    </div>
    <div style="background: #E91E63; color: white; padding: 25px; border-radius: 8px; text-align: center;">
      <div style="font-size: 48pt; font-weight: bold;">$1.92k</div>
      <div style="font-size: 16pt; margin-top: 10px;">Average ARR</div>
      <div style="font-size: 14pt; margin-top: 5px; color: #fce4ec;">↑ 12% YoY</div>
    </div>
  </div>
</section>
```

### Financial Charts

**Revenue trend line chart:**

```html
<section style="display: flex; flex-direction: column; height: 100%;">
  <h2>Revenue Trend (12 Months)</h2>
  <div style="flex: 1; position: relative; min-height: 0;">
    <canvas data-chart="line">
    <!--
    {
      "data": {
        "labels": ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"],
        "datasets": [
          {
            "label": "Actual Revenue",
            "data": [180, 195, 210, 235, 260, 285, 310, 340, 375, 410, 450, 495],
            "borderColor": "#2196F3",
            "backgroundColor": "rgba(33, 150, 243, 0.1)",
            "fill": true,
            "tension": 0.3,
            "pointRadius": 5
          },
          {
            "label": "Forecast",
            "data": [180, 200, 220, 240, 265, 290, 315, 340, 365, 390, 415, 440],
            "borderColor": "#999",
            "borderDash": [5, 5],
            "fill": false,
            "tension": 0.3
          }
        ]
      },
      "options": {
        "maintainAspectRatio": false,
        "responsive": true,
        "plugins": {
          "legend": {
            "display": true,
            "position": "top"
          }
        }
      }
    }
    -->
    </canvas>
  </div>
</section>
```

### Customer Case Study

**Structured case study layout:**

```html
<section>
  <h2>Customer Success: TechCorp</h2>
  <div style="display: grid; grid-template-columns: 2fr 1fr; gap: 30px;">
    <div>
      <h3>Challenge</h3>
      <p style="font-size: 14pt; margin: 10px 0;">
        TechCorp struggled with manual data entry, losing 15% of daily transactions to human error and spending 40 hours/week on data processing.
      </p>
      <h3 style="margin-top: 20px;">Our Solution</h3>
      <p style="font-size: 14pt; margin: 10px 0;">
        Implemented our automation platform to streamline data processing with AI-powered validation.
      </p>
      <h3 style="margin-top: 20px;">Results</h3>
      <ul style="font-size: 14pt;">
        <li><strong>99.7% accuracy</strong> (from 85%)</li>
        <li><strong>4 hours/week</strong> processing time (from 40)</li>
        <li><strong>$250K annual savings</strong> in labor</li>
      </ul>
    </div>
    <div style="background: #f5f5f5; padding: 20px; border-radius: 8px; text-align: center;">
      <h4 style="margin-top: 0;">Investment</h4>
      <div style="font-size: 28pt; font-weight: bold; margin: 20px 0;">$50K/year</div>
      <h4>ROI</h4>
      <div style="font-size: 28pt; font-weight: bold; color: #4CAF50; margin: 20px 0;">500%</div>
      <h4>Payback Period</h4>
      <div style="font-size: 28pt; font-weight: bold; margin: 20px 0;">1.4 months</div>
    </div>
  </div>
</section>
```

### Timeline/Roadmap

**Visual project roadmap:**

```html
<section id="roadmap">
  <h2>12-Month Roadmap</h2>
  <div style="margin-top: 40px;">
    <div style="display: grid; grid-template-columns: repeat(4, 1fr); gap: 20px;">
      <div>
        <h4 style="text-align: center; color: #2196F3; margin: 0 0 10px 0;">Q1 2025</h4>
        <div style="background: #E3F2FD; border-left: 4px solid #2196F3; padding: 15px; border-radius: 4px;">
          <p style="margin: 5px 0; font-size: 14pt;">Mobile app launch</p>
          <p style="margin: 5px 0; font-size: 14pt;">API v2 release</p>
          <p style="margin: 5px 0; font-size: 14pt;">EU expansion</p>
        </div>
      </div>
      <div>
        <h4 style="text-align: center; color: #4CAF50; margin: 0 0 10px 0;">Q2 2025</h4>
        <div style="background: #E8F5E9; border-left: 4px solid #4CAF50; padding: 15px; border-radius: 4px;">
          <p style="margin: 5px 0; font-size: 14pt;">AI-powered features</p>
          <p style="margin: 5px 0; font-size: 14pt;">Enterprise tier</p>
          <p style="margin: 5px 0; font-size: 14pt;">Partner program</p>
        </div>
      </div>
      <div>
        <h4 style="text-align: center; color: #FF9800; margin: 0 0 10px 0;">Q3 2025</h4>
        <div style="background: #FFF3E0; border-left: 4px solid #FF9800; padding: 15px; border-radius: 4px;">
          <p style="margin: 5px 0; font-size: 14pt;">Analytics dashboard</p>
          <p style="margin: 5px 0; font-size: 14pt;">APAC launch</p>
          <p style="margin: 5px 0; font-size: 14pt;">Integrations</p>
        </div>
      </div>
      <div>
        <h4 style="text-align: center; color: #E91E63; margin: 0 0 10px 0;">Q4 2025</h4>
        <div style="background: #FCE4EC; border-left: 4px solid #E91E63; padding: 15px; border-radius: 4px;">
          <p style="margin: 5px 0; font-size: 14pt;">Series B fundraise</p>
          <p style="margin: 5px 0; font-size: 14pt;">IPO roadshow</p>
          <p style="margin: 5px 0; font-size: 14pt;">Global presence</p>
        </div>
      </div>
    </div>
  </div>
</section>
```

## Design Recommendations

**Color palette for business presentations:**

- **Corporate/Professional**: Navy (#1C3144) + Gold (#D4AF37) + Light Gray (#F5F5F5)
- **Tech/Startup**: Electric Blue (#0066FF) + Teal (#00D4D4) + Dark Gray (#2C3E50)
- **Finance**: Deep Blue (#003D7A) + Green (#2ECC71) + White (#FFFFFF)
- **Creative/Agency**: Magenta (#E91E63) + Purple (#9C27B0) + Dark Gray (#212121)
- **Health/Wellness**: Teal (#0097A7) + Coral (#FF6B6B) + Cream (#FFFDE7)

**Typography for business:**

- **Headings**: Professional serif (Georgia, Charter) or modern sans-serif (Helvetica, Arial)
- **Body text**: Clean sans-serif (Helvetica, Verdana, Trebuchet MS)
- **Recommended Google Fonts combo**: Playfair Display (headings) + Lato (body)

**Chart color strategy:**

- Use consistent colors across all charts (same blue for revenue across all slides)
- Status indicators: Green = good/positive, Red = concerning/negative, Yellow = neutral/watch
- Limit palette to 3-5 colors maximum for clarity

## Slide Structure Templates

### Opening Slide
- Company/product name
- Tagline or value proposition
- Date/period
- Presenter name

### Content Slide
- Clear title (what's the point?)
- 3-4 key bullets (not paragraphs)
- Supporting visual (chart, diagram, or image)
- Relevant data point highlighted

### Closing Slide
- Summary of key takeaways (3 bullets)
- Clear call-to-action
- Contact information
- "Questions?" prompt

## Delivery Best Practices

1. **One idea per slide** - Don't overload with information
2. **Data-driven** - Use numbers and charts, not vague claims
3. **Consistent branding** - Color, fonts, and layout across all slides
4. **Visual hierarchy** - Make key metrics and takeaways visually prominent
5. **Speaker notes** - Include talking points in presenter mode
6. **Practice timing** - Aim for 1-2 minutes per slide
7. **Backup slides** - Include 5-10 detailed slides for Q&A
