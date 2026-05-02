---
name: spotshare-city-research
description: >
  Run social + web research for SpotShare — a guest parking infrastructure system for luxury
  condos and HOA buildings — for any city. Use this skill whenever the user names a city and
  wants a SpotShare briefing, market research, or parking intelligence for that city. Also
  triggers when the user says "run research for [city]", "what's happening in [city]",
  "next city", "run the next city", "San Diego brief", or any similar phrase referencing a
  city in the context of SpotShare. The skill runs 5 targeted research queries via the
  last30days engine, filters findings into Tier 1 / Tier 2 / Exclude buckets, and sends a
  formatted briefing email via Gmail. Always use this skill when SpotShare + a city name
  appear together in any form.
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
2. **Recipient email** — ask if not already known from conversation history.
3. **Gmail connected** — required to send the briefing at the end.

Do not proceed without the city name.

---
## Step 1: Build the Research Queries

For the given city, run the `last30days` engine with the following queries.
All 5 queries must include the city name. No national-only queries.

| # | Query | Why |
|---|-------|-----|
| 1 | `property manager OR CAM "luxury condo" [CITY]` | Find buyers talking about their buildings |
| 2 | `"community association manager" [CITY] amenities OR technology` | CAMs discussing building upgrades |
| 3 | `HOA board [CITY] downtown amenity OR app OR resident complaint` | Boards evaluating solutions |
| 4 | `"property management" [CITY] condo resident experience` | PMs talking about what residents want |
| 5 | `[CITY] luxury condo "guest parking" OR "visitor parking"` | One parking query, city-locked |

Replace `[CITY]` with the city name provided in every query.

---

## Step 2: Engine Flags

Use these flags on every invocation:

```
--emit=compact
--auto-resolve
--days=30
--x-handle=CAIsocial
--subreddits=HOA,PropertyManagement,CondoLiving,RealEstate
--x-related=FirstService,Yardi,RealPage,Parkade,[CITY_PM_COMPANIES]
--search=reddit,x,youtube,tiktok,grounding
--web-backend=brave
```

Replace `[CITY_PM_COMPANIES]` with 2-3 major property management companies 
known to operate luxury condo buildings in [CITY]. Research these before running 
if not already known. Example: for San Diego → BraeRock, ACCU, Action Property Management.

**Subreddit note:** r/fuckHOA and r/BADHOA removed — these pull resident 
venting, not property manager signal. The four remaining subreddits skew 
toward PMs and CAMs.

**Optional save flags:**
```
--save-dir=~/spotshare-research/cities/[CITY]/
--save-suffix="$(date +%Y-%m-%d)"
--store
```

---

## Step 3: Relevance Filter

After the engine returns results, filter ALL findings before writing the briefing.

### INCLUDE — Tier 1 (Email-Worthy)

High signal. Full write-up. Must be within 30 days (prefer 72 hours for breaking stories).

- Property managers / CAMs in [CITY] discussing building operations, amenities, or resident complaints
- CAMs or HOA boards in [CITY] actively evaluating apps, software, or technology for their building
- Luxury condo buildings in [CITY] with documented guest parking problems
- Competitor mentions (Parkade, ParqEx, Community Boss, SpotHero) in the context of [CITY] buildings
- News or local press about [CITY] condo/HOA amenity decisions or parking policy
- A CAM/PM creator or account based in [CITY] discovered on TikTok or YouTube

### INCLUDE — Tier 2 (Also on Our Radar)

Lower signal. One-liner in the footer only, with a note on usefulness.

- PM/CAM TikTok or YouTube creators discovered in any market → creator watch list
- HOA board or resident language around amenity frustration → social content hooks
- Viral condo living content (not parking-specific) → reactive content opportunity
- CAM vs property manager identity discussions → customer culture understanding
- National competitor activity (Parkade, ParqEx, etc.) not tied to a specific city → competitive intel

### EXCLUDE — Always Drop

- Personal neighbor disputes of any kind
- Car vandalism / damage stories
- Event parking tips (concerts, stadiums, airports)
- Generic "how to find parking downtown" content
- Content older than 30 days
- Anything from r/BestofRedditorUpdates, r/AITAH, r/EntitledPeople, r/mildlyinfuriating
- NFL / sports / entertainment parking
- Resident venting with no property manager or board angle
- Anything not connected to luxury multi-unit residential, HOAs, or property management professionals

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

TIER 1 — ACT ON THESE

[For each Tier 1 finding:]

[Platform] · [Subreddit or Account or Source]
[1-3 sentence summary. Plain language. Quote key phrases residents/PMs used.]
Opportunity: [One sentence — content, outreach, or pitch angle.]
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

- To: recipient email (ask if not known)
- Subject: SpotShare City Brief: [CITY] — [TODAY'S DATE]
- Body: formatted briefing from Step 5

After sending, confirm:
"Sent. [X] Tier 1 findings, [Y] Tier 2 for [CITY]. Ready to run the next city whenever — just drop the name."

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
