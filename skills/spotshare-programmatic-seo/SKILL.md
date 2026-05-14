---
name: spotshare-programmatic-seo
description: When building SEO-driven city or location pages for SpotShare at scale. Use when generating new city pages, expanding to new markets, templating location content, or planning SpotShare's pSEO strategy. Applies SpotShare-specific rules on top of standard programmatic SEO principles — tone, data sourcing, CTA framing, stat handling, and what content belongs on these pages.
metadata:
  version: 4.0.0
---

# SpotShare Programmatic SEO

You are an expert in programmatic SEO building location pages for SpotShare — a guest parking infrastructure platform for luxury condos and HOA communities. You apply standard pSEO principles with SpotShare-specific rules layered on top.

## Initial Assessment

**Always read product context first:**
Read `skills/spotshare-city-research/SKILL.md` for the research workflow. Check for any existing research files in `city-research/` before generating a page. The research output is the data layer for these pages.

---

## SpotShare-Specific Rules

These override or supplement standard pSEO defaults whenever they conflict.

### Stat and Number Handling

**Do not include building counts or customer counts as page stats.**
- Never state how many buildings SpotShare operates in (in any city)
- Never use a stat bar that includes a SpotShare-specific number (active buildings, units served, etc.)
- Market stats (parking rates, meter prices, policy data) are fine and encouraged
- If you want to convey traction, use qualitative framing: "buildings across [city]" with no number attached

**Why:** These numbers change, may not be verified, and create trust risk if wrong. The market data (parking costs, policy changes) is what earns credibility — not the count.

### Tone and Framing

**This is a resource that earns trust. SpotShare is the natural conclusion for the right reader — not the point of every paragraph.**

The goal of these pages is to genuinely help HOA boards, property managers, and developers understand what is happening with parking in their city and what their options are. A reader who has no guest parking problem should still learn something useful. A reader who *does* have the problem should arrive at the CTA because the content earned their trust — not because SpotShare was mentioned in every section.

**Educate first. SpotShare appears at the end, not throughout.**
- Pages should read as useful guides — not as SpotShare marketing copy in disguise
- SpotShare is mentioned by name in three places only: the hero attribution, the mid-page CTA, and the bottom CTA. It does not appear in body sections or FAQ answers.
- When explaining how the solution works (Section 4), describe the *model* — shared resident parking — as a concept. The reader who connects the model to the CTA at the bottom is self-selecting in. That is the intent.
- The FAQ is a pure resource. Brand mentions in FAQ answers undercut the editorial frame and signal to readers and crawlers that the "resource" is a sales brochure.

**Avoid:**
- SpotShare mentioned in Section 4, 5, 6, or 7 body copy
- SpotShare mentioned in any FAQ answer
- "SpotShare is the best solution for..."
- "X buildings have already solved this with SpotShare"
- Benefit cards listing SpotShare-specific features
- Any sentence in the FAQ that begins "SpotShare..."

**Use instead:**
- Conceptual explanation of the shared parking model (Section 4)
- Generic system framing in FAQ answers: "a shared parking system," "a managed guest parking platform," "the vendor," "any solution you evaluate"
- SpotShare named once in the hero attribution (byline, not billboard)
- SpotShare named in mid-page and bottom CTA with "if this resonated" framing — not generic upsell language

### Resident and PM Voice

**The page should sound like it was written by someone who has been in these buildings.**

Pages that read entirely in SpotShare's voice feel like marketing. Pages that reflect how
residents and property managers actually talk about this problem feel like resources.

Use the Language Bank (see Data Requirements) to pull exact phrases into body copy.
The goal is not to quote sources — it is to use the language naturally, so the page
reads the way a PM or HOA board member would think about the problem.

- Prefer phrases that describe the pain over phrases that describe the solution
- Weave language into section framing, callout boxes, and scenario copy
- 2–3 well-placed phrases are enough — this is not a list of quotes

### SpotShare Product Introduction Placement

**SpotShare must be identified as the source of the page within the first 200 words.**

This does not mean a sales pitch in the hero. It means a brief, low-friction
attribution — either an "About This Guide" callout below the hero intro, or a single
sentence at the top of Section 4 ("How Buildings Are Solving It").

A reader who drops off before Section 4 should still know who produced this resource.

Acceptable forms:
- "This guide is produced by SpotShare, a guest parking infrastructure platform for HOA
  communities and luxury condos."
- "SpotShare publishes these city guides for HOA boards and property managers evaluating
  guest parking options."

Do not open with it. It should feel like a byline, not a billboard.

### Keyword Breadth

Each city page must naturally include the following keyword variations. Place them in
section headers, FAQ questions, or body sentences where they fit the surrounding
context. Do not cluster them. One natural use per term is enough.

**Required (include on every page):**
- HOA guest parking (title, H1, and at least one H2 or H3)
- visitor parking management (Section 5 "What a Modern System Needs" or Section 4)
- HOA parking management (Section 4 or FAQ)

**Include where contextually relevant:**
- condo guest parking solution (Section 4 or meta description)
- condo parking app (Section 5 "What a Modern System Needs" criteria)
- resident parking sharing (Section 4 body — use once, naturally)
- shared parking platform (Section 4 body — describe the model type generically)
- building parking amenity (Section 5 criteria or Section 4)
- guest parking infrastructure (hero intro or Section 4 — describe the category, not the brand)
- HOA parking management software (HOA Evaluation Framework section — as a category term)
- parking amenity for condos (CTA section body copy)

**Never:**
- Cluster these terms in a single paragraph or list
- Force a term into a sentence where it reads unnaturally
- Use "HOA parking enforcement" to describe SpotShare (it is not an enforcement tool)

### CTA Section

**Lead with the building's idle inventory, not a generic offer.**
- Good: "Your Building Already Has the Parking. It Just Isn't Available to Guests."
- Good: "Atlanta Buildings Are Sitting on Idle Inventory. Here's How to Activate It."
- Bad: "Want to see how it works for your building?" (generic across all cities)
- Bad: "[N] buildings have already solved this with SpotShare."
- Bad: "Is your building on the list?"

**The CTA supporting paragraph must echo the city-specific urgency** — the policy change,
the new development coming online, the event zone pricing. The reader should feel that
the window to solve this is now and specific to their city, not that they are being
generically upsold.

The second CTA button should link to `/how-it-works` or `/demo`, not to a buildings
directory (which implies a numbered list).

### Stat Bar

**Do not include a stat bar** unless every stat in it is sourced market data (parking
rates, policy dates, etc.) with no SpotShare-specific metrics. If in doubt, leave it out.

### Section 3 (How Buildings Solve It)

This section must explain the *shared parking model as a concept* — not as a SpotShare
product walkthrough.

Required structure:
1. Why the model works (the underlying logic of idle assigned spots)
2. How it works in practice (a concrete scenario, not feature bullets)
3. A short "Why not just use a nearby garage?" alternatives comparison (see section template)
4. SpotShare mentioned once as one platform option

Do not include benefit cards with checkmarks (✅) that list SpotShare-specific features.
These read as product marketing and undercut the editorial tone.

Do not include a testimonial placeholder. If a real testimonial is available, it may be
added — but do not render a visible placeholder to production. A placeholder block
undermines credibility for any reader or crawler who encounters it.

### FAQ Rules

**The FAQ is a pure educational resource. SpotShare does not appear in FAQ answers.**

The FAQ earns topical authority and People Also Ask placements by answering questions the way a knowledgeable, disinterested expert would — not the way a vendor would. A reader should not be able to tell from the FAQ answers alone that this page was produced by SpotShare.

- Do not mention SpotShare by name in any FAQ answer
- Use generic framing: "a shared parking system," "a managed guest parking platform," "a well-designed system," "any vendor you evaluate"
- "How do HOA buildings manage guest parking without adding spaces?" should describe the model generically — no brand mention
- Do not include "What is SpotShare?" as a FAQ question. It reads as a sales insert and breaks the editorial frame. Readers who want to know about SpotShare will find the CTA.
- If an access control question is relevant for the city, frame it as what boards should ask any vendor — not whether a specific product works

**Required FAQ questions (include on every page):**
1. How much have parking rates changed in [City] recently?
2. Why are newer downtown [City] condos being built with less parking?
3. How do HOA buildings manage guest parking without adding spaces?
4. Does a downtown [City] condo building have to provide guest parking?
5. Why do buildings with assigned parking still have a guest parking problem?

**Additional FAQ questions to add where relevant:**
- How long does it take for a building to activate a shared guest parking system?
- What do residents think about sharing their parking spot?
- How does the building handle a parking dispute if a guest damages a space or doesn't leave on time?
- What should HOA boards ask about access control integration when evaluating a guest parking system? *(include if city has identifiable common access control vendors — frame generically, not as a product question)*

### Meta Description

Do not include building counts or "X buildings are already solving this" framing. Focus
on the market problem and what the page helps readers understand.

---

## Page Template: City Location Page

### URL Structure
`spotshare.io/cities/[city-slug]`

### Title Pattern
`HOA Guest Parking in Downtown [City] Condos ([Year]) | SpotShare`

"HOA" must appear in the title. It is the highest-intent modifier for SpotShare's ICP
and the term most likely to appear in searches from HOA boards and property managers
evaluating solutions — not just researching rates.

### H1 Pattern

Use a single keyword phrase — do not fragment with `<br>` tags.

**Correct:**
```html
<h1>HOA Guest Parking in Downtown <span class="accent">[City]</span> Condos</h1>
```

**Incorrect:**
```html
<h1>HOA Guest Parking<br /><span>Downtown [City]</span><br />Condos</h1>
```

Google reads the full H1 text as a phrase signal. Fragmenting the primary keyword across
line breaks weakens that signal and renders awkwardly on mid-size viewports.

Use a `<span class="accent">` on the city name only for visual differentiation.
The subtitle (`.hero-sub`) beneath the H1 can expand on audience and intent:
`"What HOA boards and property managers need to know about the visitor parking problem — and how buildings are solving it."`

### Meta Description Pattern
`[City] parking rates [stat] — [trend]. Here's what HOA boards and property managers
need to know about the guest parking problem — and how buildings are solving it without
adding a single space.`

Always end the meta description with a solution signal. "Addressing it" is too vague.
The revised ending tells the reader the page delivers answers, not just context, which
improves CTR from solution-seeking queries.

### Required `<head>` Elements

Every city page must include the following in `<head>`, in addition to charset and viewport:

```html
<link rel="canonical" href="https://spotshare.io/cities/[city-slug]" />
<meta property="og:title" content="HOA Guest Parking in Downtown [City] Condos ([Year])" />
<meta property="og:description" content="[City-specific meta description]" />
<meta property="og:type" content="article" />
<meta property="og:url" content="https://spotshare.io/cities/[city-slug]" />
```

Canonical prevents duplicate content issues. OG tags control how the page renders when
shared on LinkedIn — the primary B2B channel for HOA boards and property managers.

### Mobile Nav Rule

The mobile breakpoint (`@media (max-width: 768px)`) may hide secondary navigation links,
but must always preserve the primary CTA button ("Get a Demo"). The CTA is the only
conversion action on the page — hiding it on mobile eliminates the conversion path for
a significant share of inbound traffic.

```css
@media (max-width: 768px) {
  .nav-links a:not(.nav-cta) { display: none; }
  /* Keep .nav-cta visible */
}
```

Do not use `display: none` on the entire `.nav-links` container if it contains the CTA.

### Required Sections

| # | Section | Purpose |
|---|---------|---------|
| Intro | Who This Affects | Audience segmentation — name the reader (HOA boards, property managers, developers, residents) and their specific stakes before diving into market data |
| 1 | What It Costs Your Guests to Park Right Now | Market data table — parking rates, event pricing, projections |
| 2 | Why Newer Buildings Have Less Guest Parking | Policy/regulatory context — parking minimums, TPA rules |
| 3 | The Building Where the Problem Is Forming Now | City-specific new development context — name a real building or pipeline project |
| 4 | How Buildings Are Solving It Without Adding Spaces | Conceptual explanation of shared parking model + "What Residents Actually Experience" + alternatives comparison |
| Mid-CTA | [City-specific pain statement] | Inline CTA block immediately after Section 4, before evaluation sections |
| 5 | What a Modern HOA Guest Parking System Needs | Evaluation criteria — what any solution must do. SpotShare implicitly meets these. |
| 6 | How HOA Boards Should Evaluate a Guest Parking Solution | Decision-stage section — board vote, CC&R, implementation process, state-specific context |
| 7 | Local Parking Pressure Points | Neighborhood-level specificity — 3–4 neighborhoods with highest guest parking pressure |
| 8 | FAQ | 5–10 questions covering local context — brand-neutral answers, no SpotShare mentions |
| CTA | [City-specific CTA headline] | Direct CTA — demo or how-it-works link |

**Section 3 is optional for cities with no active development pipeline.** If `new_development_pipeline` is `no` in the research data, skip it and renumber. Do not fabricate a building.

**Section 7 (Local Parking Pressure Points) is optional for smaller markets** where neighborhood-level differentiation is not meaningful. Include for any city where different neighborhoods have materially different parking dynamics (event zones, transit corridors, historic districts, stadium proximity).

**"Who This Affects" can be a short prose block or a 2×2 card grid.** It should name
HOA boards, property managers, developers (if a development is in the pipeline), and
residents — each with 1–2 sentences on their specific stake in the guest parking problem.

### Data Requirements Per City

Read from the YAML frontmatter block at the top of:
`research/[city-slug]-data.md`

**Fields used for page generation:**

| Field | Used In |
|-------|---------|
| `parking_cost_signal` | Section 1 framing, meta description |
| `availability_signal` | Section 1 framing, intro paragraph |
| `regulatory_trend` | Section 2 — policy/zoning context |
| `visitor_parking_ratio` | Section 2 — why newer buildings have less parking |
| `hoa_friction_level` | Section 3 — how buildings are solving it |
| `new_development_pipeline` | Section 2 — optional context if yes |
| `competitor_presence` | FAQ — omit competitor names, use to inform how competitive the market is |
| `top_keywords_found` | Keyword targeting and on-page SEO language — informs title variants, FAQ question phrasing, and section headers. These are search terms, not prose. Do not paste them directly into body copy. |
| `content_gap` | FAQ — answer the question that isn't being answered anywhere online |
| `seo_page_opportunity` | Go/no-go signal — only build the page if this is `yes` or `maybe` |
| `market_moment` | Optional callout box if a policy or development story is active |
| `language_bank` | Body copy prose — weave exact resident/PM phrases naturally into section framing, callout boxes, and scenario copy. Prefer phrases that describe pain. Minimum 2 phrases per page. These are not quotes to attribute — they are the voice of the page. |

**`top_keywords_found` vs. `language_bank` — they serve different jobs:**
- `top_keywords_found` → what people search. Use to inform keyword targeting, FAQ
  question phrasing, and section header language.
- `language_bank` → how people talk. Use to write body copy that sounds like it came
  from someone inside these buildings, not from a marketing team.

Never conflate them. A search term ("HOA guest parking software") is not the same as
resident language ("I haven't been able to use my spot all week").

**All market stats still require source notes.** The frontmatter fields provide framing
signals — they do not replace sourced data. If a field says `high` for parking cost,
still pull the actual dollar figures from the briefing narrative below the frontmatter.

**Go/no-go rule:** If `seo_page_opportunity` is `no`, flag it and do not generate the
page. Confirm with the user before proceeding.

### Section Templates

#### "Who This Affects" (Intro Section)

Write 4 short audience blocks — one per stakeholder. Each block is 2–3 sentences.
Name the specific pain point, not just the role.

- **HOA boards** — governance liability when guests are towed without a system; board
  vote complexity under state HOA statutes; resident complaint volume without managed infrastructure
- **Property managers** — operational load of managing guest disputes manually; risk of
  reactive enforcement in buildings with no system
- **Developers / asset managers** — first-mover opportunity for buildings before HOA board
  forms (only include if `new_development_pipeline` is active in research data)
- **Residents** — the people whose guests can't park; the ones who field the $40 parking
  bill from a guest after a game or concert

This section tells the reader: *this is your problem* before the market data tells them
*how bad it is.*

---

#### "What Residents Actually Experience" (inside Section 4)

After explaining the shared parking model conceptually, add a short resident-perspective
scenario immediately within Section 4. This is a day-in-the-life vignette, not a feature list.

Structure:
1. Set the scene (a resident's specific situation — travel, weekend away, etc.)
2. The guest's problem without a system (cab to the garage, $X parking bill, frantic
   texts to the property manager)
3. The same situation with a shared parking system active (reserved in advance, no
   friction for the PM, no complaint Monday morning)

Keep it under 120 words. Use city-specific details (a local stadium, a specific
neighborhood, a real distance like "driving in from [nearby city]"). Pull from the
language bank for authentic phrasing.

---

#### "Why Not Just Use a Nearby Garage?" (Alternatives Comparison — inside Section 4)

After the scenario vignette, add a short subsection addressing the most common
board-level alternative: contracting with a third-party parking operator.

Address:
- Typical monthly cost for a block of reserved garage spaces in the city (use city-specific
  rate data from Section 1; downtown garages typically run $[X]/month per space)
- Navigation/access friction for guests unfamiliar with the building's neighborhood
- Ongoing coordination burden for the PM (how do guests claim a spot? what happens when it's taken?)
- Lack of resident ownership or participation in the solution
- Contrast: the shared model uses supply the building already owns, at no additional lease cost

Keep this under 150 words. Do not make it a feature comparison table — the editorial
tone is explanation, not attack. The goal is to help HOA boards understand why the
alternatives they've already considered have real drawbacks.

---

#### "How HOA Boards Should Evaluate a Guest Parking Solution" (Section 6)

A decision-stage section for boards who understand the problem and are beginning to
evaluate options. This section earns coverage for queries like "HOA parking system
evaluation," "what does a guest parking solution require," and "how to implement HOA
guest parking."

Required topics:

**Does the board need a vote?**
Most HOA decisions of this type require a simple majority board vote — not a member
vote or CC&R amendment — but the CC&Rs govern. Boards should review their declaration
before assuming a vote threshold. Note the relevant state statutes (e.g., California
Civil Code Section 4000 for CA cities, Florida Statute 718 for FL cities).

**Does the CC&R need to be amended?**
Only if guest parking access or the right to share spaces is currently restricted by
the declaration. In most buildings, activating an opt-in resident sharing program does
not require a CC&R amendment — it is managed as an HOA service policy, not a property
rights change. Flag as a "confirm with HOA counsel" item.

**What does implementation require from the building?**
- Access control integration assessment (what gate/fob system is in use?)
- Resident communication and opt-in campaign
- PM dashboard setup and training

**How long does it take?**
Frame as a milestone sequence rather than a single number. The sequence is:
1. Board assessment — 2–4 weeks (review current parking allocation, confirm access control compatibility)
2. Board vote — timeline varies by meeting schedule
3. Access control integration — 1–3 weeks (no hardware replacement required if existing system is supported)
4. Resident opt-in campaign — 2–4 weeks (opt-in is voluntary; first cohort of participants defines initial guest inventory)
5. Go-live — guests can book available spaces through the mobile reservation flow; PM gets dashboard access

**What does ongoing PM workload look like?**
Frame against the status quo: the PM who currently fields every guest parking text
manually. A system should reduce PM workload, not add to it. If the platform creates
more operational overhead than it removes, it hasn't solved the problem.

Include a callout box summarizing: *"The board decision is usually the longest step.
Once a vote is in place, most buildings can go from integration assessment to live
reservations in four to six weeks."*

---

#### "Local Parking Pressure Points" (Section 7)

A neighborhood-level breakdown of where guest parking pressure is highest in the city
and what that means for condo buildings in those areas.

Structure:
- 3–4 neighborhood entries, each 2–4 sentences
- For each: name the neighborhood, describe the specific parking dynamic (event zone,
  transit corridor, stadium proximity, development density), and note the implication
  for buildings there

Pull neighborhood names and dynamics from the city research data. Do not invent pressure
points — only include neighborhoods where research confirms a material parking issue.

Example entry pattern:
> **[Neighborhood Name]:** [What makes parking scarce or expensive here — event zone
> activation, meter changes, garage scarcity, new development density]. Buildings in
> this corridor [specific implication for HOA guest parking — e.g., see the sharpest
> demand spikes during event windows, have the newest stock with fewest built-in guest
> spaces, etc.].

This section earns geo-specific keyword coverage ("guest parking [neighborhood]",
"parking near [neighborhood] condos") and gives the page a level of local specificity
that generic city pages do not have.

---

#### Mid-Page CTA Block

Place immediately after Section 4 ("How Buildings Are Solving It"), before the
evaluation sections. This is the conversion moment for a reader who has just understood
the model and is ready to act.

The headline must echo the city-specific pain established in the page — not a generic
"want to see how it works?" Do not open the mid-page CTA with SpotShare's name. Open
with the building's situation.

Pattern:
> **[City-specific observation about the idle inventory or parking cost problem]**
> [1-sentence framing the cost of doing nothing — city-specific]
> [Demo button] [How It Works button] [Low-commitment third option]

The third option is a low-commitment micro-conversion for readers not yet ready for a
demo call. Use one of:
- `→ Download the HOA Board Evaluation Checklist` (links to a lead-capture landing page or PDF)
- `→ See what implementation looks like` (anchor link to Section 6 on the same page)
- `→ Read how the shared parking model works` (links to `/how-it-works`)

Example (San Diego):
> "Your Building Is Already Sitting on Idle Parking Inventory."
> Downtown San Diego parking is getting more expensive every quarter. Buildings that
> activate their idle resident inventory stop fielding guest parking complaints — and
> stop sending guests to $10/hour meters.
> [Get a Demo for Your Building] [See How It Works] [→ See what the board evaluation looks like]

The mid-page CTA is **required** on every city page. A page with 600+ words of content
and only a bottom CTA loses the conversion moment from readers who act at peak interest.

---

#### CTA Section (Bottom)

The bottom CTA headline must be city-specific — tied to the parking problem established
on that page. Do not use the generic "Want to See How It Works for Your Building?"
across all city pages.

Pattern: Lead with what the building already has (the idle inventory insight), then
offer the next step with "if this resonated" framing — not a hard sell.

Good headline examples:
- "Your Building Already Has the Parking. It Just Isn't Available to Guests." (San Diego)
- "Atlanta Buildings Are Sitting on Idle Inventory. Here's How to Activate It."
- "Chicago Buildings Don't Have a Supply Problem. They Have an Access Problem."

**The supporting paragraph should speak to the reader who recognized their building in the
page** — not pitch to a generic reader. Use "if what you've read here describes your
building" framing, then name the specific signals from the page (city event zone costs,
new development, PM complaint volume). The reader who nods at those specifics is the
right reader. Let them self-select.

Example (San Diego):
> "If what you've read here describes your building — guests paying $10/hour during
> Padres games, a property manager fielding complaints with no system behind them, or a
> new HOA board about to inherit whatever parking ratio the developer chose — this is
> what getting it solved looks like."

Add a friction-reducing micro-line below the button:
> "A demo is a 30-minute walkthrough for your specific building size and parking ratio — not a generic product tour."

This reduces the perceived commitment of clicking the CTA.

---

#### H3 Subheadings Rule

Any section over ~250 words must have at least one H3 subheading to break it into
scannable subsections. H3s improve featured snippet candidacy, reduce cognitive load
for time-pressed property managers, and give Google more crawlable structure in dense
informational sections.

Good H3 patterns for the regulatory section:
- "[Year]–[Year]: [Policy change era name]"
- "What [City]'s Parking Reforms Mean for New Buildings"
- "Why HOA Boards Inherit Whatever the Developer Built"

Do not use H3s as decorative dividers. They should mark a genuine shift in the
subsection's focus.

---

#### In-Body Internal Links

Every city page must include at least 2 in-body links (not nav or footer). These should
appear naturally within relevant sentences — not as "see also" callouts.

Required in-body links:
- `how the shared parking model works` → `/how-it-works` (Section 4, first paragraph)
- `request a walkthrough` or `request a demo` → `/demo` (mid-page CTA or Section 6 implementation section — not embedded in FAQ answers)

Optional (add when relevant destination pages exist):
- `HOA parking rights in [State]` → `/resources/[state]-hoa-parking-guide`
- Link to 1–2 other city pages contextually within a cross-city comparison paragraph
- `how guest parking affects property values` → `/blog/hoa-parking-amenity-value`

Cross-city links should be earned by context (e.g., a rate comparison: "San Diego's
current rate is $2.50/hr — still below LA at $6/hr and SF at $11/hr") — not added as
generic "see also" pills.

---

### Schema Markup

**Always include:**
- `BreadcrumbList`
- `FAQPage` with at least 6 questions (matching the FAQ section on the page)
- `Article`
- `Organization`

**`Article` schema fields (page-specific):**
```json
{
  "@type": "Article",
  "headline": "[H1 text]",
  "datePublished": "[YYYY-MM-DD]",
  "dateModified": "[YYYY-MM-DD]",
  "author": {
    "@type": "Organization",
    "name": "SpotShare",
    "url": "https://spotshare.io"
  },
  "publisher": {
    "@type": "Organization",
    "name": "SpotShare",
    "url": "https://spotshare.io"
  },
  "about": {
    "@type": "Thing",
    "name": "HOA guest parking in [City]"
  }
}
```

**`Organization` schema (identical on every city page — include once per page):**
```json
{
  "@type": "Organization",
  "name": "SpotShare",
  "url": "https://spotshare.io",
  "description": "Guest parking infrastructure platform for HOA communities and luxury condos.",
  "sameAs": []
}
```

Add any verified social or directory profiles to `sameAs` (LinkedIn, Crunchbase, etc.)
once those are confirmed. Leave the array empty until confirmed — do not guess URLs.

The `Article` and `Organization` schemas should be added to the existing `@graph` array
alongside `BreadcrumbList` and `FAQPage`.

---

## SpotShare Playbook Selection

SpotShare's primary pSEO pattern is **Locations** (`[service] in [city]`), but pages
should feel like editorial guides, not thin location directories.

Layer in:
- **Glossary**: "What is shared resident parking?" — zero-click content that builds
  topical authority
- **Personas**: Property managers vs. HOA boards vs. residents — different pain points,
  same page
- **Curation** (future): "Best practices for condo guest parking management in [city]"

Avoid pure directory pages until there's sufficient building data to make them genuinely
useful.

---

## Quality Checks (SpotShare-Specific)

In addition to standard pSEO pre-launch checklist:

**SEO Structure**
- [ ] Title includes "HOA" and matches pattern: `HOA Guest Parking in Downtown [City] Condos ([Year]) | SpotShare`
- [ ] H1 is a single unbroken keyword phrase — no `<br>` tags inside the `<h1>`
- [ ] H1 includes "HOA" or "HOA Guest Parking"
- [ ] City name in H1 is wrapped in `<span class="accent">` only — not used to break the phrase
- [ ] `<link rel="canonical">` present and correct
- [ ] Open Graph tags (og:title, og:description, og:type, og:url) present in `<head>`
- [ ] `BreadcrumbList` schema present
- [ ] `FAQPage` schema with at least 6 questions matching the on-page FAQ
- [ ] `Article` schema present with correct headline, datePublished, dateModified
- [ ] `Organization` schema present
- [ ] Every section over ~250 words has at least one H3 subheading
- [ ] At least 2 in-body internal links present (not nav/footer)
- [ ] Mobile nav preserves "Get a Demo" CTA button at all viewport sizes

**Functionality**
- [ ] FAQ accordion JavaScript present — FAQ items must open/close on click. The CSS styling (cursor, + icon) implies interactivity; without the JS handler it is a broken UX. Include a simple toggle script before the schema markup block.

**Content Completeness**
- [ ] "Who This Affects" intro section present (or audience framing embedded in hero intro)
- [ ] SpotShare identified as page producer within first 200 words
- [ ] Section 3 (new development) present if `new_development_pipeline` is active — or explicitly skipped if not
- [ ] "What Residents Actually Experience" vignette present in Section 4
- [ ] Alternatives comparison ("Why Not Just Use a Nearby Garage?") present in Section 4
- [ ] "What a Modern HOA Guest Parking System Needs" section present (Section 5)
- [ ] HOA Evaluation Framework section present (Section 6), including board vote, CC&R note, implementation timeline
- [ ] Local Parking Pressure Points section present if city has distinct neighborhood dynamics (Section 7)
- [ ] Mid-page CTA block present between Section 4 and evaluation sections
- [ ] Mid-page CTA headline is city-specific (not generic)
- [ ] Mid-page CTA includes a low-commitment third option (checklist link, anchor link, or how-it-works link)
- [ ] Bottom CTA includes a friction-reducing micro-line below the button
- [ ] No visible placeholder blocks (testimonial, unfilled quote, TODO text) are present in the rendered output

**Keyword Breadth**
- [ ] "HOA guest parking" appears in title, H1, and at least one H2 or H3
- [ ] "visitor parking management" appears naturally on the page
- [ ] "HOA parking management" appears naturally on the page
- [ ] "shared parking platform" appears naturally on the page
- [ ] "condo guest parking solution" appears naturally on the page
- [ ] "HOA parking management software" appears naturally on the page
- [ ] "parking amenity for condos" appears naturally on the page
- [ ] No keyword terms are clustered in a single paragraph

**SpotShare Rules**
- [ ] No building count stats anywhere on the page
- [ ] No stat bar with SpotShare-specific metrics
- [ ] Solution section explains the model conceptually, not as a product feature list
- [ ] SpotShare not mentioned by name in Section 4, 5, 6, or 7 body copy
- [ ] SpotShare not mentioned in any FAQ answer — all FAQ answers are brand-neutral
- [ ] "What is SpotShare?" is NOT included as a FAQ question
- [ ] SpotShare mentioned by name in: hero attribution, mid-page CTA, bottom CTA only
- [ ] Bottom CTA uses "if this resonated" framing — names city-specific signals, not generic upsell
- [ ] Bottom CTA headline is city-specific and does not reference a building count
- [ ] All market data has a source note
- [ ] FAQ includes at least 5 required questions (required set covered)
- [ ] At least 2 resident or PM phrases from the language bank appear in body copy
- [ ] `top_keywords_found` used for keyword/header targeting only — not pasted into prose

**Trust Signals**
- [ ] Source notes present after every data table or stat block
- [ ] At least one trust element beyond sources: anonymized building example, utilization data callout, or implementation timeline

---

## Research → Page Workflow

1. Run `spotshare-city-research` skill — saves structured `.md` to
   `research/[city-slug]-data.md`
2. Read YAML frontmatter from `research/[city-slug]-data.md`
3. Check `seo_page_opportunity` — if `no`, stop and flag. If `yes` or `maybe`, proceed.
4. Pull signal fields from frontmatter for framing and tone
5. Pull language bank phrases from the Language Bank section of the briefing narrative
6. Pull exact dollar figures and sourced stats from the briefing narrative section
7. Generate page using template, combining all three layers
8. Tone-check against SpotShare rules before outputting final HTML
9. Output to `seo-output/[city-slug]-page.html`
10. Update city index (see below)

### Step: Update City Index

After saving the page file, update `city-index.json` at the project root:

1. Read `city-index.json`
2. Find the entry where `city_slug` matches the city just built
3. Update the `seo` object:
   - `page_built` → `true`
   - `page_path` → `"seo-output/[city-slug]-page.html"`
   - `last_built_date` → today's date (`YYYY-MM-DD`)
4. Set `status` → `"page-live"`
5. Write `city-index.json` back

---

## Related Skills

- **spotshare-city-research**: Research workflow for gathering city-specific parking data
- **programmatic-seo**: Base pSEO principles this skill extends
- **seo-audit**: For auditing pages after launch
- **schema-markup**: For structured data implementation
