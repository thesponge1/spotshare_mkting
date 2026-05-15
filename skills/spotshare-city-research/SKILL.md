---
name: spotshare-city-research
version: 2.0
description: >
  Run social + web research for SpotShare — a guest parking infrastructure system for luxury
  condos and HOA buildings — for any city. Use this skill whenever the user names a city and
  wants a SpotShare briefing, market research, or parking intelligence for that city. Also
  triggers when the user says "run research for [city]", "what's happening in [city]",
  "next city", "run the next city", "San Diego brief", or any similar phrase referencing a
  city in the context of SpotShare. The skill runs 9 targeted research queries via the
  last30days engine, filters findings into Tier 0 / Tier 1 / Tier 2 / Exclude buckets, and
  saves a structured city intelligence record + briefing narrative to the city research
  folder. Output includes competitor intelligence, a language bank, and social content
  angles in addition to market and SEO signals. Always use this skill when SpotShare + a
  city name appear together in any form.
---

# SpotShare City Research Skill v2

## What This Skill Does

Given a city name, run targeted social + web research to find conversations, complaints,
competitor moves, and content opportunities relevant to SpotShare. Filter findings by
signal quality. Save a structured city intelligence record and briefing narrative to the
city research folder. This output feeds the programmatic SEO skill, future Notion
dashboard, sales copy, and social content directly.

---

## Step 0: Confirm Inputs

You need:
1. **City name** — extract from the user's message. If missing, ask for it.

Do not proceed without the city name.

---

## Step 0b: Sync API Keys

Before running the engine, ensure the last30days engine can read the project API keys.

Run this Bash command:

```bash
cp /Users/alissas/Development/spotshare_mkting/.env \
   /Users/alissas/Development/spotshare_mkting/.claude/last30days.env
```

This copies `.env` → `.claude/last30days.env`, which is the path the engine reads.
Do this silently — no need to mention it to the user unless the copy fails.
If the copy fails, warn the user and do not proceed: the engine will fall back to
web-only search and social data will be missing.

---

## Step 1: Build the Research Queries

For the given city, run the `last30days` engine with ALL of the following queries.

### Always-On Queries (run for every city)

| # | Query | Why |
|---|-------|-----|
| 1 | `"guest parking" condo HOA` | Core pain point — PM/CAM language |
| 2 | `"visitor parking" condo OR HOA OR "property manager"` | Alternate terminology |
| 3 | `"community association manager" OR CAM parking` | Customer-specific voice |
| 4 | `"HOA parking" amenities OR software OR app` | Solution-aware conversations |
| 5 | `"HOA guest parking software"` | Buying-intent query — surfaces competitors + roundup content |
| 6 | `"property manager parking solutions"` | PM-voice solution conversations — surfaces competitors + positioning language |
| 7 | `"best HOA parking app" OR "parking software condo" OR "visitor parking management"` | Purchase-intent signal — catches software evaluation conversations |

### City-Specific Queries (swap city each run)

| # | Query | Why |
|---|-------|-----|
| 8 | `"guest parking" OR "visitor parking" [CITY]` | Local pain points + content opportunity |
| 9 | `"how" OR "where" OR "best" "guest parking" OR "visitor parking" [CITY] condo luxury` | Search-intent signal — flags whether a city SEO page is worth building |

Replace `[CITY]` with the city name provided.

**Query yield note:** After running, record how many on-target results each query returned.
Flag any query that returns fewer than 3 on-target results as "thin." This gets reported
in the Step 8 confirmation.

---

## Step 2: Engine Flags

Use these flags on every invocation:

```
--emit=compact
--auto-resolve
--days=30
--subreddits=HOA,PropertyManagement,CondoLiving,RealEstate,fuckHOA,BADHOA
--x-handle=CAIsocial
--x-related=FirstService,Yardi,RealPage,Parkade,ReliantParking,ParkVault,ParqEx
--search=reddit,x,youtube,tiktok,grounding
--web-backend=brave
--save-dir=~/spotshare-research/cities/[CITY]/
--save-suffix="$(date +%Y-%m-%d)"
--store
```

**Subreddit whitelist** — only these 6. Never pull from: r/BestofRedditorUpdates,
r/AITAH, r/EntitledPeople, r/mildlyinfuriating, r/neighborsfromhell. These are noise.

**Source health:** After running, note which sources were unavailable (X/Twitter auth,
Reddit rate limits, YouTube signal quality). Report this in the Step 8 confirmation as
run confidence level.

---

## Step 3: Relevance Filter

After the engine returns results, filter ALL findings before writing the briefing.

### INCLUDE — Tier 0 (Educational Content Angles)

Parking-helpful content that is NOT SpotShare-specific. SpotShare is not the obvious
solution here — this is genuinely useful information for property managers about parking
in their city. Full write-up. Output goes in its own section in the briefing.

Flag anything that is:
- City parking policy changes (meter pricing, parking minimums, zoning updates)
- New condo/HOA development pipeline stories with parking ratio implications
- Parking cost data relevant to residents or guests in that city
- HOA or condo parking law updates (state or local)
- Industry stats or reports about urban parking scarcity
- Any data a property manager would find useful even if SpotShare didn't exist

Output format for each Tier 0 finding:
```
**[Source]**
[1-3 sentence summary of the useful information. Neutral tone — no SpotShare pitch.]
Content angle: [One sentence on what a helpful, non-salesy article or page about this would cover.]
```

### INCLUDE — Tier 1 (SpotShare-Specific, Act On These)

High signal. Full write-up. Must be within 30 days (prefer 72 hours for breaking stories).

- Property managers / CAMs discussing parking problems for their buildings
- Buildings actively looking for guest parking apps, software, or amenity solutions
- HOA boards discussing new building technology or amenities
- Competitor mentions: Parkade, ParqEx, Community Boss / Parking Boss, SpotHero,
  Reliant Parking, ParkVault, Fresh222, ParkM, ButterflyMX, or any new name surfaced
- Software evaluation conversations: roundup articles, "best of" lists, comparison pages
- Industry org content (CAI) about parking or amenities
- City-specific guest parking scarcity threads (content opportunity)
- Parking ticket complaints in downtown condos (content opportunity)
- News articles about city parking policy changes or condo parking drama
- **Questions phrased as "how do I / where do I / what's the best" about [CITY] guest
  parking — flag as SEO PAGE OPPORTUNITY**

Output format for each Tier 1 finding:
```
**[Platform] · [Subreddit or Account or Source]**
[1-3 sentence summary. Plain language. Pull exact phrases residents/PMs used in quotes.]
Opportunity: [One sentence — content, outreach, pitch, or counter-narrative angle.
If SEO PAGE OPPORTUNITY, say so explicitly. If competitor finding, note SpotShare's
differentiation angle.]
[Link if available]
```

### INCLUDE — Tier 2 (Also on Our Radar)

Lower signal. One-liner in the briefing footer only, with a note on usefulness.

- Resident rants about parking disputes → social content language
- HOA drama about parking rules → meme/social hooks
- CAM vs property manager identity discussions → customer culture
- Viral parking stories → reactive content hooks
- PM/CAM TikTok creators discovered → creator watch list
- New competitor domains surfaced but not yet assessed → flag for monitoring

### EXCLUDE — Always Drop

- Personal "someone parked in my spot" disputes (unless viral — then Tier 2)
- Car vandalism / damage stories
- Event parking tips (concerts, stadiums, airports)
- Generic "how to find parking downtown" content
- Content older than 30 days
- Anything from r/BestofRedditorUpdates, r/AITAH, r/EntitledPeople, r/mildlyinfuriating
- NFL / sports / entertainment parking
- Anything unrelated to multi-unit residential, HOAs, or property management
- Off-topic fallback results from auto-resolve scoring (flag these in source warnings)

### PR OPPORTUNITY FLAG

If any finding is a trending story or viral moment with a short shelf life, flag it
separately at the TOP of the briefing before all other sections. One paragraph: what the
story is, why SpotShare can insert itself, how time-sensitive it is.

---

## Step 4: Terminology Check

| Use | Avoid |
|-----|-------|
| CAM / Community Association Manager | Apartment manager |
| Property Manager | Landlord |
| HOA board / condo board | — |
| Resident / homeowner | Tenant (implies rental) |
| Guest parking / visitor parking | — |

---

## Step 5: Compose the City Intelligence Record

This is the structured data block. It lives at the TOP of the saved file and is what the
programmatic SEO skill and future dashboard will read from. Fill every field from research
findings. Use "unknown" only if genuinely no signal exists — do not guess.

```
---
city: [CITY]
run_date: [YYYY-MM-DD]
city_slug: [city-name-lowercase-hyphenated]

# PARKING PRESSURE SIGNALS
parking_cost_signal: [low / moderate / high / critical] — [one-line evidence]
availability_signal: [low / moderate / high / critical] — [one-line evidence]
regulatory_trend: [improving / stable / worsening] — [one-line evidence]
hoa_friction_level: [low / moderate / high] — [one-line evidence]
new_development_pipeline: [yes / no / unknown] — [one-line evidence if yes]
visitor_parking_ratio: [adequate / low / near-zero / unknown] — [one-line evidence]

# SPOTSHARE MARKET SIGNALS
market_readiness: [tier-1 / tier-2 / tier-3]
seo_page_opportunity: [yes / no / maybe] — [reason]
competitor_presence: [none / light / active] — [names if active]
market_moment: [one-line description of any development, policy, or PR moment worth acting on now — or "none"]
outreach_angle: [one sentence on the strongest angle for a cold outreach email to a PM in this city right now]

# CONTENT SIGNALS
tier0_count: [n]
tier1_count: [n]
tier2_count: [n]
pr_opportunity: [yes / no]
top_keywords_found: [comma-separated list of phrases residents/PMs actually used verbatim]
content_gap: [one sentence — what is being searched but not answered anywhere online]

# RUN HEALTH
queries_run: [n of 9]
thin_queries: [comma-separated query numbers that returned <3 on-target results, or "none"]
sources_unavailable: [comma-separated list of unavailable sources, or "none"]
run_confidence: [high / medium / low] — [one-line reason if medium or low]
---
```

---

## Step 6: Compose the Briefing Narrative

This is the human-readable section. It lives BELOW the structured record in the same file.

```
# SpotShare City Brief: [CITY] — [TODAY'S DATE]

Here's what's moving in [CITY] this cycle.

---

[IF PR OPPORTUNITY EXISTS:]
## 🚨 PR OPPORTUNITY
[One paragraph. What the story is. Why SpotShare can insert itself. How time-sensitive.]

---

## EDUCATIONAL CONTENT ANGLES — [CITY]

These are parking facts and local context worth publishing — no SpotShare pitch needed.
A property manager in [CITY] would find this useful on its own.

[For each Tier 0 finding:]

**[Source]**
[1-3 sentence summary. Neutral, helpful tone.]
Content angle: [One sentence on what the article or page would cover.]

---

## TIER 1 — ACT ON THESE

[For each Tier 1 finding:]

**[Platform] · [Subreddit or Account or Source]**
[1-3 sentence summary. Plain language. Pull exact phrases in quotes.]
Opportunity: [One sentence — content, outreach, or pitch angle. SEO PAGE OPPORTUNITY
or COMPETITOR COUNTER-NARRATIVE where applicable.]
[Link if available]

---

## COMPETITOR INTELLIGENCE

For every competitor surfaced this cycle — known or new — write a structured entry.
If no competitors surfaced, write: "No new competitor signals this cycle."

**[Competitor Name]**
- What they're doing: [1-2 sentences on their current messaging, product positioning,
  or content activity this cycle.]
- Their language: "[exact quote from their site or content if available]"
- Their angle vs. SpotShare: [One sentence — what problem framing they own.]
- SpotShare's counter: [One sentence — what SpotShare says differently or better.
  Anchor in real building proof points where possible.]
- Watch level: [Tier 1 / Tier 2 / Monitor]

---

## LANGUAGE BANK — [CITY] / [DATE]

Raw phrases pulled verbatim from residents, property managers, and HOA members this
cycle. No analysis — just the quotes, sourced. Use these for sales copy, social hooks,
and outreach emails.

Format:
"[exact phrase]" — [platform / source], [date if known]

Pull a minimum of 5 phrases per run if available. Prefer:
- Phrases that describe the pain (what residents say about parking chaos)
- Phrases that describe the stakes (what PMs say about complaints, time drain)
- Phrases that describe the solution search (what buyers type when evaluating software)
- Unexpected or emotionally charged language that would stop someone mid-scroll

---

## SOCIAL CONTENT ANGLES

For any finding with viral, reactive, or meme potential, write a one-liner entry here.
Do not write copy — just flag the angle, the format, and the platform it fits.

Format:
- **[Hook / angle in plain language]** — Format: [meme / reaction / series / stat drop /
  humor skit / quote card] — Platform: [TikTok / LinkedIn / Instagram] — Source:
  [link or brief description]

If nothing has social potential this cycle, write: "No social angles this cycle."

---

## ALSO ON OUR RADAR

[Tier 2 one-liners with usefulness note]

---

[If no Tier 1:]
No Tier 1 findings for [CITY] this cycle.
```

---

## Step 7: Save the File

Save the complete output (structured record + briefing narrative) as a single `.md` file
inside the project:

```
research/[city-slug]-data.md
```

Example:
```
research/san-diego-data.md
```

The file structure is always:
1. Structured YAML frontmatter block (Step 5)
2. Briefing narrative (Step 6)

This is the source of truth the programmatic SEO skill reads from.

---

## Step 7b: Update City Index

After saving the city file, update `city-index.json` at the project root:

1. Read `city-index.json`
2. Find the entry where `city_slug` matches the city just researched
3. Update the `research` object:
   - `last_run_date` → today's date (`YYYY-MM-DD`)
   - `file_path` → the path of the file just saved (relative to project root)
   - `market_readiness` → from frontmatter `market_readiness`
   - `seo_page_opportunity` → from frontmatter `seo_page_opportunity` (strip any
     trailing annotation after `—`)
   - `competitor_presence` → from frontmatter `competitor_presence` (strip any trailing
     annotation after `—`, keep just the signal word: `none` / `light` / `active`)
   - `market_moment` → from frontmatter `market_moment` (primary/first moment, used in
     table display)
   - `market_moments` → array of all distinct market moments identified in the briefing.
     Each is a one-to-two sentence description. Include any PR OPPORTUNITY as the first
     item if present. Include timing triggers and key regulatory/competitor moments.
     Typically 2–4 items.
   - `competitors` → array of competitor objects from Competitor Intelligence, Tier 1,
     Tier 2, and "Also on Radar" sections. Each object:
     `{ "tier": "1" | "2" | "watch", "name": "...", "description": "...",
     "their_angle": "...", "spotshare_counter": "..." }`
     Description: 1–2 sentences on what they're doing and why it matters for SpotShare.
     their_angle and spotshare_counter: pulled directly from Competitor Intelligence section.
   - `tier0_count` → from frontmatter `tier0_count`
   - `tier1_count` → from frontmatter `tier1_count`
   - `run_confidence` → from frontmatter `run_confidence`
4. Recalculate `status`:
   - If `seo.page_built` is true and `last_run_date` is more than 30 days ago →
     `"needs-refresh"`
   - If `seo.page_built` is true → `"page-live"`
   - If research fields are populated but `seo.page_built` is false → `"researched"`
   - If no research → `"not-started"`
5. Write `city-index.json` back

---

## Step 8: Confirm in Chat

After saving, print this confirmation in chat:

```
Done. [CITY] — [YYYY-MM-DD]
Saved to: research/[city-slug]-data.md

Tier 0: [n] content angles
Tier 1: [n] act-on findings
Tier 2: [n] on radar
Competitors surfaced: [n] — [names]
Language bank entries: [n]
Social angles: [n]
Market readiness: [tier]
SEO opportunity: [yes / no / maybe]
Competitor presence: [none / light / active]
Run confidence: [high / medium / low]
[If thin queries:] ⚠️ Thin queries: [query numbers]
[If sources unavailable:] ⚠️ Sources dark: [source names]
[If timing trigger exists:] ⚡ Timing trigger: [one-liner]
[If PR opportunity exists:] 🚨 PR opportunity flagged

Ready for the next city — just drop the name.
```

---

## City Rotation Reference

### Reading the State File

The city rotation is tracked in the `rotation` block of `city-index.json` at the project
root.

On every run, read the file and resolve the current city like this:

1. If the user named a specific city → use that city (manual override). Do NOT advance
   the counter.
2. If the user said "next city" or gave no city → read `rotation.current_index`, look up
   `cities[current_index].city`, use that city.

After a successful run (file saved, confirmation printed), update `city-index.json`:
- Increment `rotation.current_index` by 1. If it exceeds the last index (29), reset to 0.
- Set `rotation.last_run_date` to today's date in `YYYY-MM-DD` format.
- Set `rotation.last_city` to the city that was just run.

### State File Location

./city-index.json

### Rotation Block Shape

```json
{
  "rotation": {
    "current_index": 3,
    "last_run_date": "2026-05-04",
    "last_city": "Chicago"
  },
  "cities": [...]
}
```

Only `rotation.current_index`, `rotation.last_run_date`, and `rotation.last_city` are
ever written back. The `cities` array is read-only — never modify it.

---

## ICP Reminder

When in doubt: Would a property manager at a 400-unit luxury condo in a dense urban area
care about this?

Our customers:
- Manage 300-600 unit buildings
- Dense, walkable, downtown urban areas
- Resident-owned assigned parking (every spot reserved — that is why guest parking is
  scarce)
- Report to HOA boards who vote on new amenities
- Want to look like heroes for solving chronic complaints

---

## Competitor Watch List

Flag any content mentioning these by name. Add new names discovered during runs.

| Competitor | Why | Watch Level |
|------------|-----|-------------|
| Parkade | Direct competitor — has a live SpotShare comparison page | Tier 1 |
| ParqEx / GuestParq | Parking enforcement + guest parking, more enterprise | Tier 1 |
| Community Boss / Parking Boss | Simpler, HOA-focused | Tier 1 |
| Reliant Parking | HOA guest parking control + permit software — confirmed active | Tier 1 |
| ParkVault | TikTok-active, "no more office visits" PM framing | Tier 2 |
| ButterflyMX | Building tech / visitor access — competing for HOA board amenity budget | Monitor |
| SpotHero | Consumer marketplace — brand confusion risk | Monitor |
| Fresh222 | Multifamily/commercial parking management — assess HOA-specific messaging | Monitor |
| ParkM | Multifamily parking management — assess HOA-specific messaging | Monitor |

**When a new competitor surfaces:** add it to this table at the bottom with watch level
"Monitor" until enough signal exists to upgrade. Always write a Competitor Intelligence
entry in the briefing regardless of watch level.
