---
name: spotshare-programmatic-seo
description: When building SEO-driven city or location pages for SpotShare at scale. Use when generating new city pages, expanding to new markets, templating location content, or planning SpotShare's pSEO strategy. Applies SpotShare-specific rules on top of standard programmatic SEO principles — tone, data sourcing, CTA framing, stat handling, and what content belongs on these pages.
metadata:
  version: 1.0.0
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

**Educate first, pitch second.**
- Pages should read as useful guides for HOA boards and property managers — not as SpotShare marketing copy
- SpotShare can be mentioned by name, but should not be the hero of the page
- When explaining how the solution works, describe the *model* (shared resident parking) as a concept. SpotShare is one platform built for this use case — not the only way to solve it
- Reserve explicit SpotShare CTAs for the CTA section and one mention in the FAQ

**Avoid:**
- "SpotShare is the best solution for..."
- "X buildings have already solved this with SpotShare"
- Benefit cards that are all SpotShare-specific features

**Use instead:**
- Conceptual explanation of the shared parking model
- SpotShare mentioned once in body content as an example platform
- CTA section for direct SpotShare pitch

### CTA Section

**Lead with the building, not the stat.**
- Good: "Want to see how it works for your building?"
- Good: "We can walk you through whether this is a fit."
- Bad: "[N] buildings have already solved this with SpotShare."
- Bad: "Is your building on the list?"

The second CTA button should link to `/how-it-works` or `/demo`, not to a buildings directory (which implies a numbered list).

### Stat Bar

**Do not include a stat bar** unless every stat in it is sourced market data (parking rates, policy dates, etc.) with no SpotShare-specific metrics. If in doubt, leave it out.

### Section 3 (How Buildings Solve It)

This section must explain the *shared parking model as a concept* — not as a SpotShare product walkthrough.

Required structure:
1. Why the model works (the underlying logic of idle assigned spots)
2. How it works in practice (a concrete scenario, not feature bullets)
3. SpotShare mentioned once as one platform option
4. Optional testimonial placeholder (mark clearly as placeholder)

Do not include benefit cards with checkmarks (✅) that list SpotShare-specific features. These read as product marketing and undercut the editorial tone.

### FAQ Rules

- "What is SpotShare?" can be included — it's a legitimate search query
- The answer must not include a building count or city count
- Describe SpotShare by what it does, not by its scale
- "How do HOA buildings manage guest parking without adding spaces?" should describe the model generically before naming SpotShare

### Meta Description

Do not include building counts or "X buildings are already solving this" framing. Focus on the market problem and what the page helps readers understand.

---

## Page Template: City Location Page

### URL Structure
`spotshare.io/cities/[city-slug]`

### Title Pattern
`Guest Parking in Downtown [City] Condos ([Year] Guide) | SpotShare`

### Meta Description Pattern
`[City] parking rates [stat] — [trend]. Here's what HOA boards and property managers need to know about the guest parking problem, and how buildings across downtown [City] are addressing it.`

### Required Sections

| # | Section | Purpose |
|---|---------|---------|
| 1 | What It Costs Your Guests to Park Right Now | Market data table — parking rates, event pricing, projections |
| 2 | Why Newer Buildings Have Less Guest Parking | Policy/regulatory context — parking minimums, TPA rules |
| 3 | How Buildings Are Solving It Without Adding Spaces | Conceptual explanation of shared parking model |
| 4 | FAQ | 4–6 questions covering local context + SpotShare |
| CTA | Want to See How It Works for Your Building? | Direct CTA — demo or how-it-works link |

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
| `top_keywords_found` | On-page language — use exact phrases residents/PMs used |
| `content_gap` | FAQ — answer the question that isn't being answered anywhere online |
| `seo_page_opportunity` | Go/no-go signal — only build the page if this is `yes` or `maybe` |
| `market_moment` | Optional callout box if a policy or development story is active |

**All market stats still require source notes.** The frontmatter fields provide framing
signals — they do not replace sourced data. If a field says `high` for parking cost,
still pull the actual dollar figures from the briefing narrative below the frontmatter.

**Go/no-go rule:** If `seo_page_opportunity` is `no`, flag it and do not generate the
page. Confirm with the user before proceeding.

### Schema Markup

Always include:
- `BreadcrumbList`
- `FAQPage` with at least 3 questions

---

## SpotShare Playbook Selection

SpotShare's primary pSEO pattern is **Locations** (`[service] in [city]`), but pages should feel like editorial guides, not thin location directories.

Layer in:
- **Glossary**: "What is shared resident parking?" — zero-click content that builds topical authority
- **Personas**: Property managers vs. HOA boards vs. residents — different pain points, same page
- **Curation** (future): "Best practices for condo guest parking management in [city]"

Avoid pure directory pages until there's sufficient building data to make them genuinely useful.

---

## Quality Checks (SpotShare-Specific)

In addition to standard pSEO pre-launch checklist:

- [ ] No building count stats anywhere on the page
- [ ] No stat bar with SpotShare-specific metrics
- [ ] Section 3 explains the model conceptually, not as a product feature list
- [ ] SpotShare mentioned no more than 3 times in body content (FAQ + Section 3 + one other)
- [ ] CTA headline does not reference a building count
- [ ] All market data has a source note
- [ ] FAQ "What is SpotShare?" answer omits any count of buildings or cities
- [ ] Testimonial clearly marked as placeholder if not yet filled

---

## Research → Page Workflow

1. Run `spotshare-city-research` skill — saves structured `.md` to `research/[city-slug]-data.md`
2. Read YAML frontmatter from `research/[city-slug]-data.md`
3. Check `seo_page_opportunity` — if `no`, stop and flag. If `yes` or `maybe`, proceed.
4. Pull signal fields from frontmatter for framing and tone
5. Pull exact dollar figures and sourced stats from the briefing narrative section
6. Generate page using template, combining both layers
7. Tone-check against SpotShare rules before outputting final HTML
8. Output to `seo-output/[city-slug]-page.html`
9. Update city index (see below)

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
