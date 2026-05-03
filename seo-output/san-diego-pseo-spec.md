# Programmatic SEO: SpotShare City Pages
## San Diego — Full Spec

---

## Strategy Overview

**Playbook:** Locations
**Pattern:** `[guest/visitor parking] + [city] + condo/HOA`
**Confirmed demand:** A third-party blog (92101urbanliving.com) is already ranking for "guest parking downtown San Diego condo" — on SpotShare's behalf. This page reclaims that SERP with first-party content.
**Scale:** 30 city pages (using the city rotation list), expandable
**Goal:** Become the definitive parking knowledge hub for luxury condo communities — topical authority first, product second.

---

## URL Structure

```
spotshare.io/cities/                     ← hub page (lists all cities)
spotshare.io/cities/san-diego/           ← San Diego (build this first)
spotshare.io/cities/chicago/
spotshare.io/cities/miami/
...
```

Use subfolders, not subdomains. Keeps all domain authority consolidated.

The `/cities/` hub page ranks for broad queries ("HOA guest parking software"). Each city spoke ranks for city-specific queries.

---

## Data Schema

Each city page renders from a structured data file. The dev builds one Next.js template; each city gets one JSON entry.

**San Diego entry:**

```json
{
  "city": "San Diego",
  "slug": "san-diego",
  "state": "CA",
  "headline": "Guest Parking in Downtown San Diego Condos",
  "subheadline": "What property managers and HOA boards need to know in 2026",
  "pain_summary": "Most downtown San Diego condo complexes provide zero assigned guest parking. Residents are left sending guests to meters that now cost $2.50/hour — with event pricing hitting $10/hour in the Gaslamp, East Village, and Marina District.",
  "local_stat_1": "Street meter rates doubled to $2.50/hr in 2025",
  "local_stat_2": "Event pricing: $10/hr across ~200 blocks during Padres games and concerts",
  "local_stat_3": "Rates projected to reach $3.00–3.50/hr by late 2026",
  "regulatory_context": "San Diego eliminated minimum parking requirements in Transit Priority Areas in 2022. A new amendment to the municipal parking code took effect March 11, 2026. New condos in TPAs are legally permitted to be built with fewer total spaces. Guest parking ratios in newer buildings are shrinking by design.",
  "buildings_on_platform": 15,
  "neighborhoods": ["East Village", "Gaslamp Quarter", "Marina District", "Little Italy", "Cortez Hill"],
  "cta_hook": "Is your building on the list?",
  "meta_title": "Guest Parking in Downtown San Diego Condos (2026 Guide)",
  "meta_description": "Downtown SD parking rates hit $2.50/hr in 2025 — projected to reach $3.50 by 2026. Here's what HOA boards and property managers need to know, and how 15 downtown buildings are already solving it."
}
```

---

## San Diego Page Spec

**URL:** `spotshare.io/cities/san-diego/`

**Title tag:** `Guest Parking in Downtown San Diego Condos (2026 Guide) | SpotShare`

**Meta description:** `Downtown SD parking rates hit $2.50/hr in 2025 — projected to reach $3.50 by 2026. Here's what HOA boards and property managers need to know about guest parking, and how 15 downtown buildings are solving it.`

---

### Page Sections

---

**H1:** Guest Parking in Downtown San Diego Condos

**Intro paragraph:**
> Most downtown San Diego condo buildings have no assigned guest parking. Every resident who wants to host someone sends them to street meters that now cost $2.50/hour — or worse, a garage during a Padres game at $10/hour. It's the complaint HOA boards hear most, and it's getting worse, not better.

---

**H2: What It Costs Your Guests to Park Right Now**

| Parking Type | Current Rate | Notes |
|---|---|---|
| Street meters (standard) | $2.50/hr | Doubled in 2025 |
| Event pricing (East Village, Gaslamp, Marina) | $10/hr | Active during Padres games + concerts |
| Balboa Park daily | $16/day | As of early 2026 |
| Projected street rate by late 2026 | $3.00–3.50/hr | Dynamic pricing rolling out |

*Source: rethinkdowntown.com — Downtown San Diego Parking Costs 2025*

*Note: This section makes the page worth bookmarking. A property manager can share this table directly with residents.*

---

**H2: Why Newer San Diego Buildings Have Less Guest Parking**

> San Diego eliminated minimum parking requirements for commercial properties in Transit Priority Areas in 2022. A new amendment to the municipal parking code took effect March 11, 2026. The city's goal is explicit: reduce parking supply to encourage transit use.
>
> For HOA boards, this means newer buildings in TPAs are legally permitted — and often built — with fewer total spaces than older buildings. The guest parking ratio you're working with now may be better than what's available in the next building your residents consider.

*Source: sandiego.gov — Parking Reform program page*

*Content angle: positions proactive guest parking management as a forward-looking amenity decision, not just a complaint-response.*

---

**H2: How Downtown San Diego Buildings Are Solving It**
*(SpotShare's first appearance on the page)*

> 15 buildings in downtown San Diego are currently using SpotShare to share resident-owned parking spots with guests. Instead of sending visitors to $2.50/hr meters, residents make their assigned spot available when they're not using it — and the building gains a functional guest parking amenity without building a single new space.

- [ ] Insert the 15 building names (or a neighborhood-level map if names can't be published)
- [ ] Pull 1–2 resident or property manager quotes
- Keep this section factual and proof-based, not salesy

---

**H2: Frequently Asked Questions**
*(FAQPage schema goes here — see Schema section below)*

| Question | Answer direction |
|---|---|
| Does my downtown San Diego condo have to provide guest parking? | No — and fewer new buildings will. Explain the TPA reform. |
| How much does visitor parking cost in downtown San Diego? | $2.50/hr standard, $10/hr during events, going up. |
| What neighborhoods in San Diego have the worst guest parking? | East Village, Gaslamp, Marina District. |
| How do HOA buildings manage guest parking without assigned spots? | Explain the shared-spot model. |
| What is SpotShare? | One paragraph, factual. |

---

**CTA (bottom of page):**

> Is your building in downtown San Diego? Check if you're on the list — or bring SpotShare to your HOA board.

Buttons: `[See participating buildings]` `[Get a demo for your building]`

---

## Schema Markup

Add this to `<Head>` on the San Diego page (and templated for every city page):

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://spotshare.io"},
        {"@type": "ListItem", "position": 2, "name": "Cities", "item": "https://spotshare.io/cities"},
        {"@type": "ListItem", "position": 3, "name": "San Diego", "item": "https://spotshare.io/cities/san-diego"}
      ]
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {
          "@type": "Question",
          "name": "Does my downtown San Diego condo have to provide guest parking?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "No. Most downtown San Diego condos have no assigned guest parking. San Diego's 2022 parking reform eliminated minimum parking requirements in Transit Priority Areas, meaning newer buildings are permitted to be built with fewer spaces."
          }
        },
        {
          "@type": "Question",
          "name": "How much does visitor parking cost in downtown San Diego?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "Street meters in downtown San Diego cost $2.50/hour as of 2025, doubled from prior rates. During Padres games and concerts in East Village, Gaslamp, and Marina District, event pricing reaches $10/hour. Rates are projected to reach $3.00–3.50/hour by late 2026."
          }
        },
        {
          "@type": "Question",
          "name": "What neighborhoods in San Diego have the worst guest parking availability?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "East Village, the Gaslamp Quarter, and the Marina District have the highest concentration of downtown condos with no dedicated guest parking, combined with the highest street parking costs and event-driven pricing spikes."
          }
        }
      ]
    }
  ]
}
```

---

## Internal Linking Plan

| Link from | Link to | Anchor text |
|---|---|---|
| `/cities/` hub | `/cities/san-diego/` | "San Diego" |
| `/cities/san-diego/` | `/cities/` | "See all cities" |
| `/cities/san-diego/` | `/blog/parkade-vs-spotshare/` (when built) | "how SpotShare compares to Parkade" |
| `/cities/san-diego/` | `/blog/hoa-guest-parking-software/` (when built) | "best HOA guest parking software" |
| San Diego page | XML sitemap | Add on publish |

No orphan pages — every city page must be reachable from the `/cities/` hub before it's indexed.

---

## Dev Handoff Checklist

- [ ] Build `/cities/[slug]/` Next.js dynamic route
- [ ] Create city data file (JSON or MDX) with the schema fields above
- [ ] Add San Diego as first entry
- [ ] Implement FAQPage + BreadcrumbList schema in `<Head>`
- [ ] Build `/cities/` hub page with links to all city pages
- [ ] Add city pages to XML sitemap
- [ ] Verify page speed / Core Web Vitals before indexing

---

## Next Steps (Content)

1. **Write full San Diego page copy** — ready to brief whenever
2. **Build the `/cities/` hub page** — needed before spokes go live
3. **Parkade comparison page** (`/blog/parkade-vs-spotshare/`) — flagged as most time-sensitive item from research; Parkade has a live page targeting SpotShare by name right now
4. **"Best HOA guest parking software" roundup post** — SimplyPermits is ranking for this and SpotShare doesn't appear

---

*Source data: research/sandiego-data.md*
*Generated: 2026-05-03*
