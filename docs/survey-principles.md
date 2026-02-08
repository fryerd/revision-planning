# Survey Principles & Theory

Key theories, frameworks, and best practices for each phase of survey-to-dashboard projects.

**Purpose**: Reference guide for qualitative research, data visualization, interaction design, and content strategy. Use this alongside `survey-workflow.md` for comprehensive methodology.

---

## Table of Contents

1. [Survey Design & Question Crafting](#1-survey-design--question-crafting)
2. [Data Analysis & Themeing](#2-data-analysis--themeing)
3. [Information Architecture & Narrative Design](#3-information-architecture--narrative-design)
4. [Data Visualization Design](#4-data-visualization-design)
5. [Interaction & Animation Design](#5-interaction--animation-design)
6. [Content Writing & Evidence Presentation](#6-content-writing--evidence-presentation)
7. [Visual Hierarchy & Micro-interactions](#7-visual-hierarchy--micro-interactions)
8. [Cross-Cutting Principles](#cross-cutting-principles-all-phases)
9. [Recommended Reading](#recommended-reading-by-phase)

---

## 1. Survey Design & Question Crafting

### **The Mom Test** (Rob Fitzpatrick)
**Principle**: Ask about past behavior, not hypothetical futures

**Why it matters**: People are terrible at predicting what they'll do. They're accurate about what they did.

**Application**:
- ✅ Good: "What did you do last time you needed to revise?"
- ❌ Bad: "Would you use a revision planner if we built one?"

**Our use**:
- "What stops you from revising independently?" (actual barriers)
- Not "What features would you want?" (speculation)

---

### **Jobs to be Done** (Clayton Christensen)
**Principle**: People "hire" products to make progress in their lives. Understand the job, not the product features.

**Why it matters**: Users don't want a drill, they want a hole. They don't want features, they want to achieve a goal.

**Application**:
- Ask: "When you need to revise, what do you use and why?"
- Not: "Do you like Seneca's quiz feature?"

**Our use**:
Discovered students "hire" different tools for different jobs:
- Cognito for video explanations
- Quizlet for self-made flashcards
- PMT for past papers
- Seneca for content recap

They're building portfolios, not choosing one tool.

---

### **Cognitive Load Theory** (Sweller)
**Principle**: Working memory has limited capacity (~7±2 items). Minimize extraneous cognitive load.

**Why it matters**: Complex surveys exhaust respondents. They satisfice (pick "neutral") or drop out.

**Application**:
- Keep surveys short (<10 minutes)
- One question per concept
- Avoid nested conditionals ("If yes, then skip to Q12...")
- Use conversational flow (AI follow-ups) instead of long multi-part questions

**Our use**:
Open-ended questions with AI follow-up (conversational) instead of 50 Likert scale items.

---

### **Anchoring Bias Avoidance** (Kahneman & Tversky)
**Principle**: First information encountered sets a mental anchor that skews subsequent judgments.

**Why it matters**: Asking "Do you find Seneca boring?" before "What do you dislike?" primes them to say "boring."

**Application**:
- Randomize question order where possible
- Start neutral, move to specific
- Don't lead with negative framing

**Our use**:
Started with neutral "How do you use Seneca?" before "What stops you from using it more?"

---

### **Open-Ended Last Rule** (Qualitative Research Methods)
**Principle**: Closed questions prime responses; open questions reveal unknown unknowns.

**Why it matters**: You can't multiple-choice your way to "THE AMELIA AI... COSTS MONEY" (all-caps fury). You need open text.

**Application**:
- Use closed questions (multi-select, scale) for structure and quantification
- End with "Anything else?" for discovery
- The most valuable insights come from unstructured text

**Our use**:
Got "THE AMELIA AI THAT WOULD BE VERY HELPFUL TO USE, COSTS MONEY" in Year 7 open response. No pre-designed question would surface that intensity.

---

## 2. Data Analysis & Themeing

### **Grounded Theory** (Glaser & Strauss)
**Principle**: Theory emerges from data, not imposed beforehand. Let patterns surface organically.

**Why it matters**: If you start with "I bet paywall is the issue," you'll only see paywall evidence. You'll miss "homework brand poisoning."

**Application**:
- Read transcripts without a hypothesis
- Code recurring phrases
- Group codes into themes
- Don't force data into pre-existing categories

**Our use**:
"Homework brand association is poisonous" wasn't a hypothesis. It emerged from 50+ students saying "I see it as homework" across segments.

---

### **Thematic Analysis Framework** (Braun & Clarke)
**Principle**: 6-phase systematic approach to finding patterns in qualitative data.

**Phases**:
1. Familiarization (read all transcripts)
2. Coding (tag recurring phrases, concepts)
3. Theme generation (group codes into broader patterns)
4. Review themes (check they fit data)
5. Define themes (name them clearly)
6. Report (write findings)

**Application**:
- Don't skip familiarization — read everything at least once
- Use consistent coding (tag "can't find content," "sidebar confusing," "too many clicks")
- Iterate on theme names until they're clear to someone who hasn't seen the data

**Our use**:
- Coded: "can't find content," "sidebar confusing," "too many clicks"
- Theme: "Navigation barriers"
- Reviewed: Does this fit all 24 mentions? Yes.

---

### **Frequency vs. Salience** (Qualitative priority assessment)
**Principle**: Most-mentioned ≠ most important. Intensity, emotion, and reproducibility matter.

**Why it matters**: 10 synonym errors (low count) but every one is specific, reproducible, and furious = high priority.

**Application**:
- Track both count (how many?) and intensity (how much do they care?)
- Look for: specificity, emotion, reproducibility
- Weight "frustration per mention"

**Our use**:
Synonym marking errors: only 10 mentions, but...
- Every single one was specific ("biology, stem cells, 'rejection isn't possible'")
- Every single one was frustrated
- We tagged it: "Highest frustration-per-mention in the dataset"

---

### **Triangulation** (Denzin)
**Principle**: Cross-validate findings with multiple data sources or methods.

**Why it matters**: One quote is an anecdote. Barrier theme + competitive mention + sentiment quote = pattern.

**Application**:
- Look for convergence across:
  - Open-ended barrier responses
  - Competitor mentions
  - Likes/dislikes sentiment
  - Demographic patterns (Year 7 vs Year 11)

**Our use**:
Video gap confirmed by:
- Cognito mentioned 18 times (competitor data)
- YouTube mentioned 9 times (competitor data)
- "I can see what is happening rather than reading" (quote)
- No video content = #1 content gap (barrier data)

All point to same insight: video is the biggest content gap.

---

### **Theoretical Saturation** (Grounded Theory)
**Principle**: Stop coding when new data adds no new themes.

**Why it matters**: You don't need to code all 1,305 responses if responses 200–250 repeat themes from 1–199.

**Application**:
- Code in batches (first 50, next 50, etc.)
- Track when you stop finding new themes
- Saturation usually hits at 200–500 responses for homogeneous populations

**Our use**:
We had 1,305 responses. Saturation likely hit around 400–500 per segment. Remaining responses confirmed patterns, didn't add new ones.

---

## 3. Information Architecture & Narrative Design

### **Inverted Pyramid** (Journalism)
**Principle**: Most important information first, details later.

**Why it matters**: Users scan. If they only read the first section, they should get the headline.

**Application**:
- Hero stats: "61% already use Seneca for independent study"
- Overview section before methodology footnotes
- Each section: headline stat → details → evidence

**Our use**:
- Hero: 61%, #1 barrier, 3.84/5 ease rating
- Footer: Methodology details (sample size, AI disclaimer, edge cases)

---

### **Pyramid Principle** (Barbara Minto)
**Principle**: Start with the answer, then support it. (SCQA: Situation-Complication-Question-Answer)

**Why it matters**: Executives and stakeholders want the "so what?" first, evidence second.

**Application**:
- Finding title = Answer ("Video is the biggest content gap")
- Finding description = Support ("Cognito 18×, YouTube 9×, 27 students cite video")
- Quote = Illustration ("I can see what is happening rather than reading")

**Our use**:
Every finding/priority follows this structure:
1. **Title** (Answer): "Synonym marking errors are dealbreakers"
2. **Description** (Support): "10 specific reports, every one reproducible, corrupts core mechanism"
3. **Quote** (Illustration): "In biology i typed 'rejection isnt possible'... it corrected me with the same answer"

---

### **Progressive Disclosure** (UX principle)
**Principle**: Show only what's needed now; reveal complexity on demand.

**Why it matters**: Reduces cognitive load. Users can go deeper if interested, but aren't overwhelmed upfront.

**Application**:
- Quote short preview → click for full quote
- Collapsible cards for dense data (14 subjects, ease breakdown)
- Tabs for segmented data (OH vs MH barriers)

**Our use**:
- Quotes show first 60 chars, expand on click
- Section 4 cards (Subjects, Ease) collapsed by default with gradient fade
- Tabs separate Only Homework vs Mostly Homework barrier data

---

### **Miller's Law** (7±2 items in working memory)
**Principle**: Humans can hold ~7 chunks of information at once.

**Why it matters**: Lists of 20 items are unreadable. Group into 5–10 max.

**Application**:
- Limit categories per section (5–10 bars, not 25)
- If you have 20 items, group into themes or show top 10 + "Other"

**Our use**:
- Barriers: 11 themes (acceptable — push the limit)
- Competitors: Top 19 (truncated from 47 total mentions)
- Findings: 10 insights
- Priorities: 9 recommendations

All stay near Miller's sweet spot.

---

### **Narrative Arc** (Story structure)
**Principle**: Setup → Rising tension → Climax → Resolution

**Why it matters**: Data is boring. Stories are memorable.

**Application**:
- Setup: Who are these students? (Overview)
- Rising tension: What's broken? (Barriers, Competitors)
- Climax: Why is it broken? (Findings)
- Resolution: What should we do? (Priorities)

**Our use**:
1. **Overview**: 61% use it, here's who they are
2. **Barriers**: Time/homework is #1, navigation is #3
3. **Competitors**: They're building portfolios (Cognito, Quizlet, PMT)
4. **Findings** (climax): "Homework brand is poisonous," "Empty state kills conversion"
5. **Priorities** (resolution): Fix empty state, build planner, add video

---

## 4. Data Visualization Design

### **Tufte's Data-Ink Ratio**
**Principle**: Maximize information per unit of ink. Remove chartjunk.

**Definition**:
```
Data-ink ratio = (ink used for data) / (total ink)
```

**Why it matters**: Every pixel that doesn't encode data is distraction.

**Remove**:
- 3D effects on bars
- Decorative gradients
- Grid lines (unless essential)
- Background patterns
- Heavy borders

**Our use**:
- Minimal bar charts: label, value, track, fill. No axes, no grid, no background.
- Donut chart: just slices + legend. No center decorations.
- Card borders: 1px solid, not heavy drop shadows

---

### **Cleveland & McGill's Perceptual Hierarchy**
**Principle**: We perceive some visual encodings more accurately than others.

**Ranking** (most to least accurate):
1. **Position on common scale** (scatter plot, dot plot)
2. **Length** (bar chart)
3. **Angle** (pie chart)
4. **Area** (bubble chart)
5. **Color saturation** (heatmap)
6. **Color hue** (rainbow encoding)

**Application**:
- Use bar charts for comparison (length is accurate)
- Avoid pie charts for precise comparison (angle is imprecise)
- Only use donut/pie for proportions of a whole

**Our use**:
- Bar charts for frequencies (barrier themes, competitor mentions)
- Donut only for segment distribution (proportions of 1,305)
- Color for category, not for magnitude (rose = barriers, teal = likes)

---

### **Gestalt Principles** (Proximity, Similarity, Closure)
**Principle**: We group things that are near, look alike, or form a pattern.

**Laws**:
- **Proximity**: Things close together are perceived as a group
- **Similarity**: Things that look alike are perceived as related
- **Closure**: We complete incomplete shapes mentally

**Application**:
- Group related bars close together (barrier themes)
- Use same color for same category (all barriers rose-colored)
- Use whitespace to separate unrelated sections

**Our use**:
- Barrier themes grouped by segment (OH vs MH) with shared rose color
- Whitespace between sections signals topic change
- Quote cards in same grid share styling → perceived as set

---

### **Semantic Color Encoding**
**Principle**: Red = danger/stop, green = success/go, blue = neutral/info (cultural conventions).

**Why it matters**: Color carries meaning. Use it intentionally, not decoratively.

**Application**:
- Red/rose for problems, barriers, dislikes
- Green/teal for successes, likes, positive outcomes
- Amber/yellow for warnings, cautions
- Blue for neutral data

**Our use**:
- Rose: barriers, dislikes, high-priority findings
- Teal: likes, positive sentiment
- Amber: medium-priority items, warnings (paywall)
- Blue: neutral data (subjects, methods)

---

### **Shneiderman's Mantra** (Overview, Zoom, Filter, Details-on-demand)
**Principle**: Visual information seeking mantra for interactive systems.

**Steps**:
1. **Overview**: Show the whole dataset
2. **Zoom**: Let users focus on areas of interest
3. **Filter**: Let users remove uninteresting items
4. **Details-on-demand**: Reveal full data on hover/click

**Application**:
- Show all segments in donut (overview)
- Hover for exact percentages (zoom)
- Tabs filter by segment (filter)
- Quote cards expand for full text (details-on-demand)

**Our use**:
- Bar charts show all themes (overview)
- Tooltips add exact counts on hover (details)
- Quote short preview → click for full (details-on-demand)
- Tabs separate OH vs MH data (filter)

---

## 5. Interaction & Animation Design

### **Fitts's Law** (Target size & distance)
**Formula**:
```
Time = a + b × log₂(Distance/Size + 1)
```

**Principle**: Time to click a target increases with distance and decreases with size.

**Application**:
- Make clickable things big (min 44×44px touch targets)
- Put related actions close together
- Don't make users hunt for buttons

**Our use**:
- Quote cards are full-width (easy to hit anywhere)
- Nav links have 22px gap (not cramped)
- Collapsible cards: entire card is clickable (not just a tiny arrow)

---

### **Hick's Law** (Choice paralysis)
**Formula**:
```
Time = a + b × log₂(n + 1)
```
where n = number of choices

**Principle**: Decision time increases logarithmically with number of choices.

**Application**:
- Limit simultaneous choices
- Use progressive disclosure (tabs, accordions)
- Don't show 10 filters at once

**Our use**:
- Tabs (OH vs MH) instead of dropdown "select segment" — only 2 visible choices
- Collapsible cards hide complexity until user chooses to expand

---

### **Affordances & Signifiers** (Don Norman)
**Definitions**:
- **Affordance**: What an object can do (a button can be clicked)
- **Signifier**: Clue that an affordance exists (button looks clickable)

**Principle**: Design should signal what actions are possible.

**Application**:
- Buttons look clickable (raised, shadowed, hover state)
- Links are underlined or colored
- Cursor changes to pointer on clickable elements

**Our use**:
- Quote cards: `cursor: pointer`, "tap to expand" text, hover border change
- Collapsible cards: gradient fade signals "there's more below"
- Tab buttons: distinct active state (white background, shadow)

---

### **Immediate Feedback Principle**
**Principle**: System responds instantly (<100ms) to user action.

**Why it matters**: Delays >100ms feel sluggish. Users wonder "did it work?"

**Application**:
- Hover → highlight (instant)
- Click → expand (instant)
- No loading spinners for local interactions

**Our use**:
- Bar fill animates on scroll-in (triggered by IntersectionObserver)
- Quote expands instantly on click (CSS class toggle, no JS delay)
- Donut slice highlights on hover (CSS `:hover`, GPU-accelerated)

---

### **Progressive Enhancement**
**Principle**: Core content works without CSS/JS; enhancements layer on top.

**Why it matters**: If JS fails (3% of users), content should still be readable.

**Application**:
- HTML structure is semantic and readable
- CSS adds layout and polish
- JS adds interactivity (animations, expand/collapse)

**Our use**:
- All data rendered via JS, but could be static HTML
- `.reveal` animations add polish, but content is readable without `.vis` class
- Quote cards work with or without JS (CSS `:hover` for visual feedback)

---

## 6. Content Writing & Evidence Presentation

### **Show, Don't Tell** (Writing principle)
**Principle**: Evidence > assertion. Let reader draw conclusion.

**Why it matters**: "Students are frustrated" is weak. "THE AMELIA AI... COSTS MONEY" (all-caps) shows fury.

**Application**:
- Don't say "users find it confusing"
- Show the quote: "Everything is crammed into the left side... features aren't listed in one area"

**Our use**:
- Every finding has a direct student quote
- Findings lead with observable evidence: "18 mentions," "10 specific reports," "Year 7 students capitalised their entire complaint"

---

### **Toulmin's Argumentation Model** (Claim-Data-Warrant)
**Structure**:
- **Claim**: What you assert
- **Data**: Evidence supporting claim
- **Warrant**: Why the data supports the claim

**Example**:
- **Claim**: Synonym errors are dealbreakers
- **Data**: 10 students reported false negatives, one gave reproducible biology example
- **Warrant**: In an active-recall platform, being marked wrong when right teaches the wrong lesson

**Our use**:
Every finding follows this:
- **Title** = Claim
- **Quote** = Data
- **Description** = Warrant

---

### **Quantitative Anchoring for Qualitative Claims**
**Principle**: Numbers make patterns credible; quotes make them human.

**Why it matters**: "Some students mentioned video" is vague. "18 students cited Cognito for video" is specific.

**Application**:
- Lead with count ("18 mentions, 10 reports, 75 students")
- Follow with representative quote
- Combine: frequency + intensity

**Our use**:
- "Cognito (18 mentions) dominates the competitor list specifically because of video"
- Then: "I can see what is happening rather than just reading"

---

### **Signal vs. Noise** (Nate Silver)
**Principle**: Separate true patterns (signal) from random variance (noise).

**Why it matters**: One student saying "slow loading" might be their WiFi. Ten students saying "synonym errors" is a pattern.

**Application**:
- Set a threshold: 3+ mentions = theme
- Don't report one-offs unless they're severe
- Weight by: frequency × intensity × reproducibility

**Our use**:
- 10 synonym errors (signal)
- 1 student mentioned slow loading (noise — excluded)
- "Homework brand poisoning": 50+ mentions across segments (strong signal)

---

### **Cognitive Empathy** (Writing for audience mental model)
**Principle**: Write in the reader's language, not yours.

**Why it matters**: "Null homepage render" means nothing. "Empty state" is clear.

**Application**:
- Use user vocabulary, not internal jargon
- Define technical terms on first use
- Test: Would a stakeholder understand this?

**Our use**:
- "Empty state" (not "null homepage render")
- "Homework brand" (not "usage pattern segmentation bias")
- "Lazy students are overwhelmed" (use their word "lazy," then reframe)

---

## 7. Visual Hierarchy & Micro-interactions

### **F-Pattern & Z-Pattern** (Eye-tracking research, Nielsen Norman Group)
**Patterns**:
- **F-Pattern**: Text-heavy pages (users scan top, then down left side)
- **Z-Pattern**: Visual-heavy pages (users scan top-left → top-right → bottom-left → bottom-right)

**Application**:
- Put key info top-left (F-pattern start)
- Place CTAs on right side of Z
- Don't bury important content bottom-left

**Our use**:
- Section titles top-left (F-pattern anchor)
- Hero stats use Z-pattern (left stat → center → right stat)
- Nav links top-right (Z-pattern terminus)

---

### **Doherty Threshold** (400ms response time)
**Principle**: Users feel in control if system responds <400ms.

**Why it matters**:
- <100ms: Instant
- 100–300ms: Slight delay, but acceptable
- 300–1000ms: Sluggish
- >1000ms: Mental context switch

**Application**:
- Interactions <400ms (clicks, hovers)
- Animations 200–400ms (stylistic polish)
- Avoid 1s+ transitions (feel broken)

**Our use**:
- Click → expand: instant (CSS class toggle)
- Bar fills: 1.1s (stylistic, not blocking interaction)
- Hover → highlight: instant (GPU-accelerated)

---

### **Aesthetic-Usability Effect**
**Principle**: Beautiful designs are perceived as more usable (even if they're not).

**Why it matters**: Users trust polished interfaces. They forgive minor usability issues if it looks professional.

**Application**:
- Polish shadows, border-radius, transitions
- Consistent spacing (8px grid)
- Smooth animations (cubic-bezier easing)

**Our use**:
- Card shadows: `0 2px 8px rgba(30,39,54,0.05)`
- Border-radius: 16px (cards), 8px (buttons)
- Smooth scroll snap (sections catch gently)

---

### **Serial Position Effect** (Primacy & Recency)
**Principle**: We remember first and last items best.

**Application**:
- Put most critical findings at #1 and #10 (bookends)
- Put weakest items in middle (#5–7)

**Our use**:
Findings order:
- #1: Homework brand poisoning (biggest perception barrier)
- #10: Infinite retries (undermines core mechanic)
- Middle: Portfolio thinking, Amelia paywall, etc.

---

### **Contrast & Accessibility** (WCAG Guidelines)
**Standards**:
- **AA**: 4.5:1 contrast for body text, 3:1 for large text (18pt+)
- **AAA**: 7:1 for body, 4.5:1 for large

**Why it matters**: Low contrast excludes users with low vision, older users, mobile users in sunlight.

**Application**:
- Test text/background combinations
- Don't rely on color alone (use icons, labels)
- Provide alternatives (text labels + color + icon)

**Our use**:
- Semantic color (rose = barriers) but also text labels ("Barriers")
- Icons (🎥 video, 📭 empty state) so colorblind users get signal
- High contrast text: `--t1: #1e2736` on `--bg: #f0f3fa`

---

## Cross-Cutting Principles (All Phases)

### **Occam's Razor**
**Principle**: Don't add complexity without evidence it's needed.

**Our use**:
- Didn't add filters, date pickers, multi-level navigation
- One scrollable page was enough
- Single HTML file (no build system, no dependencies)

---

### **Pareto Principle (80/20)**
**Principle**: 80% of insight comes from 20% of the data.

**Our use**:
- Focused on top barriers (time/homework, navigation)
- Focused on top competitor (Cognito)
- Didn't list all 47 tools mentioned once

---

### **Recognition Over Recall** (Nielsen's Heuristics)
**Principle**: Show options, don't make users remember them.

**Our use**:
- Nav is sticky (always visible)
- Sections are labeled (no mystery meat navigation)
- Quotes show year badge (don't make user remember "who said this?")

---

### **Redundancy of Cues**
**Principle**: Multiple signals for same information (color + icon + text).

**Why it matters**: Accessibility, clarity, redundancy if one channel fails.

**Our use**:
Priority badges use:
- Color (rose/amber/blue)
- Text (High/Medium/Low)
- Border color
- Number (01, 02, 03...)

---

### **Iterative Refinement** (Agile/Lean)
**Principle**: Ship, learn, improve.

**Our use**:
- Deployed v1 with dark theme
- Pivoted to light theme based on feedback
- Added collapsible cards after seeing density issues
- All post-launch, based on real usage

---

## Recommended Reading by Phase

### **Survey Design**
- *The Mom Test* — Rob Fitzpatrick
- *Competing Against Luck* — Clayton Christensen (Jobs to be Done)
- *Thinking, Fast and Slow* — Daniel Kahneman (Biases)

### **Analysis**
- *Constructing Grounded Theory* — Kathy Charmaz
- *Qualitative Data Analysis* — Miles & Huberman
- *Thematic Analysis* — Braun & Clarke (paper)

### **Information Architecture**
- *The Pyramid Principle* — Barbara Minto
- *Information Architecture* — Rosenfeld & Morville
- *Made to Stick* — Chip & Dan Heath (Story structure)

### **Visualization**
- *The Visual Display of Quantitative Information* — Edward Tufte
- *Show Me the Numbers* — Stephen Few
- *Graphical Perception* — Cleveland & McGill (paper)

### **Interaction Design**
- *Don't Make Me Think* — Steve Krug
- *The Design of Everyday Things* — Don Norman
- *About Face* — Alan Cooper (Interaction design)

### **Writing & Evidence**
- *On Writing Well* — William Zinsser
- *The Elements of Style* — Strunk & White
- *The Uses of Argument* — Stephen Toulmin

### **Visual Design**
- *Refactoring UI* — Adam Wathan & Steve Schoger
- *The Non-Designer's Design Book* — Robin Williams
- *Gestalt Principles* (various papers)

---

## Quick Reference: When to Use What

| Phase | Key Principles to Apply |
|-------|-------------------------|
| **Drafting questions** | Mom Test, Jobs to be Done, Cognitive Load Theory |
| **Themeing responses** | Grounded Theory, Thematic Analysis, Triangulation |
| **Structuring narrative** | Inverted Pyramid, Pyramid Principle, Miller's Law |
| **Choosing visualizations** | Tufte's Data-Ink Ratio, Cleveland & McGill, Semantic Color |
| **Designing interactions** | Fitts's Law, Affordances, Immediate Feedback |
| **Writing findings** | Show Don't Tell, Toulmin Model, Quantitative Anchoring |
| **Polishing UI** | F/Z-Pattern, Aesthetic-Usability, WCAG Contrast |

---

**The strongest dashboards apply principles from all these disciplines**: research rigor + visual clarity + narrative coherence + interaction polish.

---

**Created**: February 2026
**Source**: Seneca Independent Study Survey Dashboard project
**Maintained**: Dan Fryer
