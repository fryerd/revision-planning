# Survey Dashboard Workflow: Raw Data → Live Site

A replicable process for transforming survey responses into interactive data dashboards.

**Based on**: Seneca Independent Study Survey (January 2026, 1,305 responses)
**Output**: Single-file HTML dashboard deployed via GitHub Pages
**Time**: ~1 session for foundation + iterations for polish

---

## Table of Contents

1. [Phase 1: Data Structuring & Themeing](#phase-1-data-structuring--themeing)
2. [Phase 2: Narrative Architecture](#phase-2-narrative-architecture)
3. [Phase 3: Technical Foundation](#phase-3-technical-foundation)
4. [Phase 4: Visual Identity](#phase-4-visual-identity-theme-override-pattern)
5. [Phase 5: Content Refinement](#phase-5-content-refinement-the-deep-read)
6. [Phase 6: Deployment](#phase-6-deployment)
7. [Phase 7: UX Polish](#phase-7-ux-polish-post-launch-iteration)
8. [Key Decisions & Rationale](#key-decisions--why)
9. [Replication Checklist](#replication-checklist-for-next-survey)

---

## Phase 1: Data Structuring & Themeing

**Goal**: Convert raw responses into analyzable segments

### 1. Segment your respondents
Create meaningful groups based on usage patterns or key variables.

**Example structure**:
```javascript
const SEGMENTS = [
  {label: 'Mix of both', count: 469, color: '#4ecf86'},
  {label: 'Only homework', count: 268, color: '#6366f1'},
  {label: 'Mostly homework', count: 227, color: '#f5b5a0'},
  // ...
];
```

### 2. Theme open-ended responses
Use keyword analysis to extract recurring patterns.

**Process**:
- Group transcripts by segment
- Extract recurring barriers, preferences, pain points
- Build non-mutually-exclusive theme arrays (one response can match multiple themes)

**Example structure**:
```javascript
const BARRIERS_OH = [
  {label: 'Time / Competing homework', count: 32, pct: 21, color: 'var(--rose)'},
  {label: 'Boredom / Lack of engagement', count: 25, pct: 16, color: 'var(--rose)'},
  // ...
];
```

### 3. Tag representative quotes
For each theme, pull 3-5 direct quotes with metadata.

**Example structure**:
```javascript
const QUOTES_OH = [
  {
    s: "Seneca is a lovely app for revision but it is way too similar…",
    f: "Seneca is a lovely app for revision but it is way too similar to a student sitting and getting information then answering some questions on it. It would be better if the revision were in forms of interactive games or quests which would motivate students.",
    y: "Year 9"
  },
  // ...
];
```

**Fields**:
- `s`: Short preview (first ~60 chars)
- `f`: Full quote text
- `y`: Demographic/context (e.g., "Year 10", "Teacher", "Parent")

### 4. Extract quantitative patterns
Capture multi-select responses, ratings, distributions.

**Example structure**:
```javascript
const STUDY_INTENT = [
  {label: 'Know what to study before opening', count: 430, pct: 57, color: 'var(--teal)'},
  {label: 'Use Seneca to help decide', count: 198, pct: 26, color: 'var(--amber)'},
  {label: "Don't know — just open Seneca", count: 128, pct: 17, color: 'var(--rose)'},
];
```

---

## Phase 2: Narrative Architecture

**Goal**: Design the story the data tells

### 1. Map the user journey through sections

**Recommended flow**:
1. **Broad**: Who are these people? (Demographics, segments)
2. **Context**: How do they currently behave? (Usage patterns)
3. **Problems**: What's broken? (Barriers, gaps, competitors)
4. **Evidence**: What do they say? (Sentiment, quotes)
5. **Insights**: What does it mean? (Deeper findings)
6. **Solutions**: What should we do? (Prioritized recommendations)

**Our flow**:
- Overview (segments, year groups)
- Barriers (what stops them?)
- Competitors (what do they use instead?)
- How They Study (navigation patterns)
- Likes & Dislikes (sentiment)
- Deeper Findings (non-obvious insights)
- Priorities (ranked recommendations)

### 2. Choose visualization types per data shape

| Data Type | Visualization | Use Case |
|-----------|---------------|----------|
| Proportions of whole | Donut chart | Segment distribution |
| Frequencies/rankings | Horizontal bars | Barrier themes, features mentioned |
| Qualitative evidence | Expandable quote cards | Student voices |
| Rating scales | Stacked horizontal bar | Ease ratings (1-5) |
| Key insights | Icon cards with evidence | Non-obvious findings |
| Recommendations | Ranked cards with badges | Prioritized action items |

### 3. Write insight boxes for non-obvious patterns

Place interpretive summaries **before** the detailed data they explain.

**Example**:
```html
<div class="insight">
  <div class="insight-icon">💡</div>
  <p><strong>Key insight:</strong> Students aren't choosing one competitor — they're assembling revision portfolios. <strong>Cognito</strong> for video, <strong>Quizlet</strong> for self-made flashcards, <strong>PMT</strong> for past papers. Seneca is losing to an <strong>ecosystem</strong>, not a single app.</p>
</div>
```

---

## Phase 3: Technical Foundation

**Goal**: Build the single-file HTML structure

### 1. Set up HTML skeleton

**Key sections**:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Survey Dashboard</title>
  <style>/* All CSS inline */</style>
</head>
<body>
  <!-- Sticky nav with anchor links -->
  <nav>...</nav>

  <!-- Hero with key stats -->
  <header class="hero">...</header>

  <!-- Sections with semantic IDs -->
  <section id="overview">...</section>
  <section id="barriers">...</section>
  <!-- ... -->

  <footer>...</footer>

  <!-- All data + rendering -->
  <script>/* All JS inline */</script>
</body>
</html>
```

### 2. Build the CSS system

**Foundation**:
```css
:root {
  --bg: #f0f3fa;
  --card: #ffffff;
  --t1: #1e2736; /* Primary text */
  --t2: #6b7a8d; /* Secondary text */
  --amber: #f5a623;
  --teal: #4ecf86;
  --rose: #f25c5c;
  /* ... */
}
```

**Component classes**:
- `.card` - Base card container
- `.bar` - Bar chart row
- `.quote-card` - Expandable quote
- `.finding-card` - Insight card with icon
- `.priority-card` - Recommendation card with badge

**Layout grids**:
```css
.grid-2 {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
}

.grid-barriers {
  display: grid;
  grid-template-columns: 1.3fr 1fr;
  gap: 24px;
}
```

**Animation states**:
```css
.reveal {
  opacity: 0;
  transform: translateY(18px);
  transition: opacity .6s ease, transform .6s ease;
}
.reveal.vis {
  opacity: 1;
  transform: translateY(0);
}
```

### 3. Write data arrays

All data lives as `const` arrays at top of `<script>`:

```javascript
const SEGMENTS = [...];
const YEAR_GROUPS = [...];
const BARRIERS_OH = [...];
const QUOTES_OH = [...];
// ...
```

**No external JSON** — everything inline for single-file portability.

### 4. Build render functions

**Pattern**:
```javascript
function renderBars(containerId, data) {
  document.getElementById(containerId).innerHTML = data.map((d, i) => `
    <div class="bar" style="transition-delay:${i*0.07}s">
      <div class="bar-hd">
        <span class="bar-lbl">${d.label}</span>
        <span class="bar-val">${d.count} · ${d.pct}%</span>
      </div>
      <div class="bar-track">
        <div class="bar-fill" data-w="${d.pct}" style="background:${d.color}"></div>
      </div>
    </div>
  `).join('');
}
```

**Key functions**:
- `renderBars(id, data)` — Bar chart
- `renderQuotes(id, arr)` — Quote cards
- `renderDonut()` — SVG donut chart
- `renderFindings()` — Insight cards
- `renderPriorities()` — Recommendation cards

### 5. Add interactivity

**Scroll-triggered reveals**:
```javascript
new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) e.target.classList.add('vis');
  });
}, {threshold: 0.12}).observe && document.querySelectorAll('.reveal').forEach(el => {
  new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) e.target.classList.add('vis');
    });
  }, {threshold: 0.12}).observe(el);
});
```

**Tab switching**:
```javascript
document.querySelectorAll('.tab-btn').forEach(btn => {
  btn.onclick = () => {
    // Remove active from all tabs/panels
    document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
    document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));

    // Add active to clicked tab and its panel
    btn.classList.add('active');
    document.getElementById('panel-' + btn.dataset.tab).classList.add('active');
  };
});
```

**Quote expand/collapse**:
```javascript
function renderQuotes(id, arr) {
  document.getElementById(id).innerHTML = arr.map(q => `
    <div class="quote-card" onclick="this.classList.toggle('open')">
      <div class="qmark">"</div>
      <p class="q-short">${q.s}</p>
      <p class="q-full">${q.f}</p>
      <div class="q-foot">
        <span class="q-yr">${q.y}</span>
        <span class="q-more">tap to expand</span>
      </div>
    </div>
  `).join('');
}
```

### 6. Handle dynamic content gotcha ⚠️

**Problem**: Statically-placed `.reveal` elements get observed on page load, but dynamically-injected `.reveal` elements (from `innerHTML`) are never observed.

**Solution**: Add a second observer call **after** render functions run:

```javascript
(function() {
  renderFindings();
  renderPriorities();

  // Re-observe dynamically-rendered reveal cards
  document.querySelectorAll('#findingsGrid .reveal, #priorityCards .reveal').forEach(el => {
    new IntersectionObserver(entries => {
      entries.forEach(e => {
        if (e.isIntersecting) e.target.classList.add('vis');
      });
    }, {threshold: 0.12}).observe(el);
  });

  // ... rest of init
})();
```

---

## Phase 4: Visual Identity (Theme Override Pattern)

**Goal**: Apply consistent branding without rewriting the entire stylesheet

### 1. Start with a base theme
Write initial CSS with hardcoded colors (dark or light).

### 2. If you need to pivot themes

**Step 1**: Define CSS variables for semantic colors
```css
:root {
  --bg: #f0f3fa;
  --card: #ffffff;
  --t1: #1e2736; /* Primary text */
  --t2: #6b7a8d; /* Secondary text */
  --border: rgba(30,39,54,0.1);
  /* Brand colors */
  --amber: #f5a623;
  --teal: #4ecf86;
  --rose: #f25c5c;
  --blue: #5b9bd5;
}
```

**Step 2**: Replace hardcoded values with variables where you want theme control
```css
/* Before */
.card {
  background: #ffffff;
  border: 1px solid rgba(30,39,54,0.1);
}

/* After */
.card {
  background: var(--card);
  border: 1px solid var(--border);
}
```

**Step 3**: Create theme override block at **end** of stylesheet
```css
/* ============================================================
   LIGHT THEME OVERRIDES
   ============================================================ */
nav {
  background: #fff;
  box-shadow: 0 1px 4px rgba(30,39,54,0.06);
}

.card {
  box-shadow: 0 2px 8px rgba(30,39,54,0.05);
}

/* Override specific hardcoded values */
.stat-card:hover {
  box-shadow: 0 6px 24px rgba(30,39,54,0.1);
}
```

**Why this works**: CSS source order — later rules override earlier ones with same specificity.

### 3. Font & brand choices

**Web fonts**:
```css
@import url('https://fonts.googleapis.com/css2?family=Mulish:wght@300;400;500;600;700;800&display=swap');

body {
  font-family: 'Mulish', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}
```

**Brand colors in hero**:
```css
.hero-tag {
  color: #5b6abf;
  background: rgba(91,106,191,0.08);
  border-color: rgba(91,106,191,0.2);
}
```

---

## Phase 5: Content Refinement (The Deep Read)

**Goal**: Surface insights that keyword analysis alone cannot find

### 1. Read every transcript yourself

**Why**:
- Keyword analysis gives themes (frequency)
- Full transcript reading surfaces insights that don't keyword-match
- Examples we discovered:
  - "Homework brand poisoning" (perception problem)
  - "Lazy = overwhelmed" (misdiagnosed motivation)
  - "Paywall = equity argument" (principled objection, not price sensitivity)

### 2. Write "Deeper Findings"

**Structure**:
```javascript
const FINDINGS = [
  {
    icon: '🎥',
    sev: 'high', // Controls top border color
    title: 'Video is the single biggest content gap',
    desc: 'Cognito (18 mentions) dominates the competitor list specifically because of video. YouTube (9) is cited for the same reason. 27 students, all citing the same missing feature. Seneca has no video. This is not a minor gap.',
    quote: "I can see what is happening rather than just reading. The topic layout is simpler than Seneca and it stays in my long-term memory better because of the video lessons.",
    qy: "Year 11"
  },
  // ...
];
```

**Guidelines**:
- Icon: Choose emoji that represents the insight
- Title: 5-10 words, punchy, actionable
- Description: 2-3 sentences, evidence + interpretation
- Quote: Most representative student voice
- Aim for 8-10 findings

### 3. Draft "Priorities"

**Structure**:
```javascript
const PRIORITIES = [
  {
    num: '01',
    badge: 'High', // or 'Medium', 'Low'
    bc: 'high',    // CSS class for badge color
    border: 'var(--rose)', // Left border color
    title: 'Fix the empty state / homepage',
    desc: 'When no homework is set, the homepage shows just a leaderboard. No recommendations, no "what to do next." Students forget the platform can do revision at all. This is the most concrete single product fix in the data.',
    ev: [
      'Students say "Seneca is usually empty"',
      'No recommendations when homework is done',
      'Clearest single product fix identified',
      'Directly causes revision drop-off'
    ],
    q: "I just never really thought about it… when I have no homework, Seneca is usually empty. There's just nothing to do.",
    qy: "Year 10"
  },
  // ...
];
```

**How to rank**:
- Combine: barrier frequency + competitive gaps + sentiment + student quotes
- Consider: impact (how many users affected) × severity (how much it hurts)
- Badge severity: High (top 3), Medium (next 4), Low (nice-to-haves)

### 4. Replace placeholder text with final versions

Once finalized, use Edit tool to swap entire arrays:

```javascript
// Replace old FINDINGS array with new reordered version
const FINDINGS = [
  // All 10 findings in new priority order
];
```

---

## Phase 6: Deployment

**Goal**: Ship to a live URL

### 1. Initialize git repo
```bash
cd /path/to/project
git init
git add .
git commit -m "Initial commit: survey dashboard"
```

### 2. Create GitHub repository
```bash
gh repo create your-repo-name --public --source=. --remote=origin --push
```

Or via web UI: GitHub.com → New Repository

### 3. Use branch workflow to avoid breaking existing content

**Why**: If your repo already has files (e.g., other prototypes), pushing to `main` directly could overwrite them.

```bash
# Create feature branch
git checkout -b dashboard-name

# Add your dashboard file
git add seneca-survey.html
git commit -m "Add survey dashboard"

# Push branch
git push -u origin dashboard-name
```

### 4. Merge to main via GitHub API

This preserves existing files in the repo:

```bash
gh api repos/USERNAME/REPO/merges \
  -X POST \
  -f head=dashboard-name \
  -f base=main \
  -f message="Merge dashboard into main"
```

### 5. Enable GitHub Pages

**Via web UI**:
1. Repository → Settings → Pages
2. Source: `main` branch
3. Save

**Result**: Your dashboard is live at:
```
https://USERNAME.github.io/REPO/filename.html
```

**Deployment time**: ~2 minutes after merge

---

## Phase 7: UX Polish (Post-Launch Iteration)

**Goal**: Refine interactions based on real usage

### 1. Scroll behavior

**Scroll snap** (sections "catch" gently):
```css
html {
  scroll-snap-type: y proximity;
  scroll-padding-top: 56px; /* Nav height */
}

header.hero, section, footer {
  scroll-snap-align: start;
}
```

### 2. Animation refinement

**Upgrade fade-only to slide-up**:
```css
/* Before: Fade only */
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

/* After: Slide + fade */
@keyframes panelIn {
  from {
    opacity: 0;
    transform: translateY(12px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.panel.active {
  animation: panelIn 0.38s cubic-bezier(0.4, 0, 0.2, 1);
}
```

### 3. Data ordering

**Sort quotes by demographic** (e.g., year descending):
```javascript
function renderQuotes(id, arr) {
  const sorted = [...arr].sort((a, b) =>
    (parseInt(b.y.replace(/\D/g, '')) || 0) -
    (parseInt(a.y.replace(/\D/g, '')) || 0)
  );

  document.getElementById(id).innerHTML = sorted.map(q => `...`).join('');
}
```

**Reorder findings** by priority (most actionable first).

### 4. Layout improvements

**Unify grid systems**:
```html
<!-- Before: Competitors section had full-width card + quotes below -->
<div class="card">Bars</div>
<div>Quotes</div>

<!-- After: Match barriers two-column layout -->
<div class="grid-barriers">
  <div class="card">Bars</div>
  <div>Quotes</div>
</div>
```

### 5. Collapsible cards for dense content

**HTML**:
```html
<div class="card reveal" data-collapsible>
  <div class="card-title">Subjects they revise for</div>
  <!-- 14 bars of subject data -->
</div>
```

**CSS**:
```css
.card[data-collapsible] {
  max-height: 210px;
  overflow: hidden;
  position: relative;
  cursor: pointer;
  transition: max-height 0.45s cubic-bezier(0.4, 0, 0.2, 1);
}

.card[data-collapsible]::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 50px;
  background: linear-gradient(to top, var(--card), transparent);
  pointer-events: none;
  transition: opacity 0.35s;
}

.card[data-collapsible].expanded {
  max-height: 2000px;
}

.card[data-collapsible].expanded::after {
  opacity: 0;
}
```

**JavaScript**:
```javascript
document.querySelectorAll('.card[data-collapsible]').forEach(card => {
  card.onclick = () => card.classList.toggle('expanded');
});
```

### 6. First-item-open pattern for quotes

```javascript
// After rendering competitor quotes, open the first one by default
const firstCompQuote = document.querySelector('#quotes-comp .quote-card');
if (firstCompQuote) firstCompQuote.classList.add('open');
```

---

## Key Decisions & Why

| Decision | Rationale |
|----------|-----------|
| **Single HTML file** | Portability — can email, host anywhere, no build step, no dependencies |
| **CSS override block** | Pivot themes without rewriting entire stylesheet; change 50 lines instead of 500 |
| **JavaScript render functions** | Data arrays stay clean, HTML generation is DRY, easy to update |
| **IntersectionObserver** | Scroll animations without scroll listeners (better performance) |
| **Quote short/full pattern** | Show preview, expand on click — keeps cards scannable, reduces initial cognitive load |
| **Badge + border color** | Visual hierarchy for priority/severity without reading text |
| **Grid-based layout** | Responsive by default, aligns related content, easier to maintain than floats/flexbox soup |
| **GitHub Pages** | Free hosting, versioned via git, shareable URL, auto-deploys on push to main |

---

## File Size & Performance Notes

**Our final file**:
- ~1,100 lines of code
- ~45KB uncompressed (gzips to ~12KB)
- All data inline — no HTTP requests except font import
- Loads in <200ms on 3G

**Performance optimizations**:
- Animations use `transform` and `opacity` (GPU-accelerated)
- IntersectionObserver triggers animations only when visible (lazy animation)
- Bar fills animate via `width` transition (layout stays stable)
- No images, no external scripts, no analytics bloat

---

## Replication Checklist for Next Survey

- [ ] **Data Structuring**
  - [ ] Theme raw responses into frequency arrays (`BARRIERS`, `LIKES`, `COMPETITORS`, etc.)
  - [ ] Tag 3-5 quotes per theme with demographic metadata
  - [ ] Extract quantitative patterns (ratings, multi-select, distributions)

- [ ] **Narrative Design**
  - [ ] Design section flow (broad → specific → recommendations)
  - [ ] Choose visualization types per data shape
  - [ ] Write insight boxes for non-obvious patterns

- [ ] **Technical Build**
  - [ ] Build HTML skeleton (nav, hero, sections with semantic IDs)
  - [ ] Write CSS system (variables, cards, bars, quotes, grids)
  - [ ] Build render functions (bars, quotes, donut, findings, priorities)
  - [ ] Add interactivity (observers, tabs, tooltips, expand/collapse)
  - [ ] Handle dynamic content reveal gotcha (re-observe after render)

- [ ] **Content**
  - [ ] Read all transcripts, write Deeper Findings (8-10 insights)
  - [ ] Draft Priorities with evidence tags + quotes (8-10 recommendations)
  - [ ] Replace placeholder arrays with final content

- [ ] **Deployment**
  - [ ] Initialize git repo
  - [ ] Create GitHub repository
  - [ ] Push to branch, merge to main via API
  - [ ] Enable GitHub Pages

- [ ] **Polish** (post-launch)
  - [ ] Add scroll snap for section navigation
  - [ ] Refine animations (slide + fade, cubic-bezier easing)
  - [ ] Sort data (quotes by year, findings by priority)
  - [ ] Add collapsible cards for dense sections
  - [ ] Open first quote by default in key sections

---

## Next Steps

1. **Start new survey project**: Read this workflow doc before beginning
2. **Customize for your context**: Adjust sections, visualizations, tone
3. **Reference principles doc**: See `survey-principles.md` for theory behind each phase
4. **Iterate**: Ship v1 fast, polish based on stakeholder feedback

---

**Created**: February 2026
**Source**: Seneca Independent Study Survey Dashboard project
**Maintained**: Dan Fryer
