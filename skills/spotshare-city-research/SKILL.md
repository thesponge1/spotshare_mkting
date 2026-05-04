---
name: spotshare-city-research
description: >
  Run social + web research for SpotShare — a guest parking infrastructure system for luxury
  condos and HOA buildings — for any city. Use this skill whenever the user names a city and
  wants a SpotShare briefing, market research, or parking intelligence for that city. Also
  triggers when the user says "run research for [city]", "what's happening in [city]",
  "next city", "run the next city", "San Diego brief", or any similar phrase referencing a
  city in the context of SpotShare. The skill runs 6 targeted research queries via the
  last30days engine, filters findings into Tier 0 / Tier 1 / Tier 2 / Exclude buckets, and
  sends a formatted briefing email via Gmail. Always use this skill when SpotShare + a city
  name appear together in any form.
---

# SpotShare City Research Skill

## What This Skill Does

Given a city name, run targeted social + web research to find conversations, complaints,
and content opportunities relevant to SpotShare. Filter findings by signal quality. Send a
formatted briefing email via Gmail.

---

## Step 0: Confirm Inputs

You need:
1. **City name** — extract from the user's message. If missing, ask for it.
2. **Recipient email** — always `hello@spotshare.com`. No need to ask.
3. **Gmail connected** — required to send the briefing at the end.

Do not proceed without the city name.

---

## Step 1: Build the Research Queries

For the given city, run the `last30days` engine with the following queries.

### Always-On Queries (run for every city)

| # | Query | Why |
|---|-------|-----|
| 1 | `"guest parking" condo HOA` | Core pain point — PM/CAM language |
| 2 | `"visitor parking" condo OR HOA OR "property manager"` | Alternate terminology |
| 3 | `"community association manager" OR CAM parking` | Customer-specific voice |
| 4 | `"HOA parking" amenities OR software OR app` | Solution-aware conversations |

### City-Specific Queries (swap city each run)

| # | Query | Why |
|---|-------|-----|
| 5 | `"guest parking" OR "visitor parking" [CITY]` | Local pain points + content opportunity |
| 6 | `"how" OR "where" OR "best" "guest parking" OR "visitor parking" [CITY] condo luxury` | Search-intent signal — people already Googling for an answer that doesn't exist yet; flags whether a city SEO page is worth building |

Replace `[CITY]` with the city name provided.

---

## Step 2: Engine Flags

Use these flags on every invocation:

```
--emit=compact
--auto-resolve
--days=30
--subreddits=HOA,PropertyManagement,CondoLiving,RealEstate,fuckHOA,BADHOA
--x-handle=CAIsocial
--x-related=FirstService,Yardi,RealPage,Parkade
--search=reddit,x,youtube,tiktok,grounding
--web-backend=brave
```

**Subreddit whitelist** — only these 6. Never pull from: r/BestofRedditorUpdates,
r/AITAH, r/EntitledPeople, r/mildlyinfuriating, r/neighborsfromhell. These are noise.

**Optional save flags:**
```
--save-dir=~/spotshare-research/cities/[CITY]/
--save-suffix="$(date +%Y-%m-%d)"
--store
```

---

## Step 3: Relevance Filter

After the engine returns results, filter ALL findings before writing the briefing.

### INCLUDE — Tier 0 (Educational Content Angles)

Parking-helpful content that is NOT SpotShare-specific. SpotShare is not the obvious
solution here — this is genuinely useful information for property managers about parking
in their city. Full write-up. Output goes in its own section in the email.

Flag anything that is:
- City parking policy changes (meter pricing, parking minimums, zoning updates)
- New condo/HOA development pipeline stories with parking ratio implications
- Parking cost data relevant to residents or guests in that city
- HOA or condo parking law updates (state or local)
- Industry stats or reports about urban parking scarcity
- Any data a property manager would find useful even if SpotShare didn't exist

Output format for each Tier 0 finding:
[Source]
[1-3 sentence summary of the useful information. Neutral tone — no SpotShare pitch.]
Content angle: [One sentence on what a helpful, non-salesy article or page about this would cover.]

### INCLUDE — Tier 1 (SpotShare-Specific, Act On These)

High signal. Full write-up. Must be within 30 days (prefer 72 hours for breaking stories).

- Property managers / CAMs discussing parking problems for their buildings
- Buildings actively looking for guest parking apps, software, or amenity solutions
- HOA boards discussing new building technology or amenities
- City-specific guest parking scarcity threads (content opportunity)
- Parking ticket complaints in downtown condos (content opportunity)
- Competitor mentions: Parkade, ParqEx, Community Boss / Parking Boss, SpotHero
- Industry org content (CAI) about parking or amenities
- News articles about city parking policy changes or condo parking drama
- **Questions phrased as "how do I / where do I / what's the best" about [CITY] guest parking — flag as SEO PAGE OPPORTUNITY**

### INCLUDE — Tier 2 (Also on Our Radar)

Lower signal. One-liner in the footer only, with a note on usefulness.

- Resident rants about parking disputes → social content language
- HOA drama about parking rules → meme/social hooks
- CAM vs property manager identity discussions → customer culture
- Viral parking stories → reactive content hooks
- PM/CAM TikTok creators discovered → creator watch list

### EXCLUDE — Always Drop

- Personal "someone parked in my spot" disputes
- Car vandalism / damage stories
- Event parking tips (concerts, stadiums, airports)
- Generic "how to find parking downtown" content
- Content older than 30 days
- Anything from r/BestofRedditorUpdates, r/AITAH, r/EntitledPeople, r/mildlyinfuriating
- NFL / sports / entertainment parking
- Anything unrelated to multi-unit residential, HOAs, or property management

### PR OPPORTUNITY FLAG

If any finding is a trending story or viral moment with a short shelf life, flag it
separately at the top of the email. One paragraph: what the story is, why SpotShare can
insert itself, how time-sensitive it is.

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

## Step 5: Compose the Briefing Email

**Subject:** SpotShare City Brief: [CITY] — [TODAY'S DATE]

**Body:**

Hey —

Here's what's moving in [CITY] this week for SpotShare.

---

[IF PR OPPORTUNITY EXISTS:]
PR OPPORTUNITY
[One paragraph. What the story is. Why SpotShare can insert itself. How time-sensitive.]

---

EDUCATIONAL CONTENT ANGLES — [CITY]

These are parking facts and local context worth publishing about — no SpotShare pitch needed.
A property manager in [CITY] would find this useful on its own.

[For each Tier 0 finding:]

[Source]
[1-3 sentence summary. Neutral, helpful tone.]
Content angle: [One sentence on what the article or page would cover.]

---

TIER 1 — ACT ON THESE

[For each Tier 1 finding:]

[Platform] · [Subreddit or Account or Source]
[1-3 sentence summary. Plain language. Quote key phrases residents/PMs used.]
Opportunity: [One sentence — content, outreach, or pitch angle. If flagged SEO PAGE OPPORTUNITY, say so explicitly.]
[Link if available]

---

ALSO ON OUR RADAR

[Tier 2 one-liners with usefulness note]

---

[If no Tier 1:]
No Tier 1 findings for [CITY] this cycle.

That's it for [CITY].

---

## Step 6: Send via Gmail

Use the Gmail MCP to send the briefing.

- To: hello@spotshare.com
- Subject: SpotShare City Brief: [CITY] — [TODAY'S DATE]
- Body: formatted briefing from Step 5

After sending, confirm:
"Sent. [X] Tier 0 content angles, [Y] Tier 1 findings, [Z] Tier 2 for [CITY]. Ready to run the next city whenever — just drop the name."

---

## City Rotation Reference

If the user says "next city" or "what's next," use this 30-day rotation:

| Day | City |
|-----|------|
| 1 | San Diego |
| 2 | Atlanta |
| 3 | Chicago |
| 4 | Seattle / Bellevue |
| 5 | St. Petersburg, FL |
| 6 | New York City |
| 7 | Miami |
| 8 | San Francisco |
| 9 | Los Angeles |
| 10 | Boston |
| 11 | Washington DC |
| 12 | Denver |
| 13 | Austin |
| 14 | Portland |
| 15 | Philadelphia |
| 16 | Houston |
| 17 | Dallas |
| 18 | Minneapolis |
| 19 | Nashville |
| 20 | Charlotte |
| 21 | Tampa |
| 22 | Fort Lauderdale |
| 23 | Honolulu |
| 24 | Las Vegas |
| 25 | Phoenix / Scottsdale |
| 26 | Baltimore |
| 27 | Raleigh / Durham |
| 28 | Salt Lake City |
| 29 | New Orleans |
| 30 | Pittsburgh |

---

## ICP Reminder

When in doubt: Would a property manager at a 400-unit luxury condo in a dense urban area care about this?

Our customers:
- Manage 300-600 unit buildings
- Dense, walkable, downtown urban areas
- Resident-owned assigned parking (every spot reserved — that is why guest parking is scarce)
- Report to HOA boards who vote on new amenities
- Want to look like heroes for solving chronic complaints

---

## Competitor Watch List

Flag any content mentioning these by name:

| Competitor | Why |
|------------|-----|
| Parkade | Direct competitor — has a SpotShare comparison page |
| ParqEx | Parking enforcement + guest parking, more enterprise |
| Community Boss / Parking Boss | Simpler, HOA-focused |
| SpotHero | Consumer marketplace — brand confusion risk |