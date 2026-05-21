# San Diego Page — AEO Action Plan
**Goal:** Make `seo-output/san-diego-page.html` show up as a cited source in ChatGPT answers and Google AI Overviews.

---

## What AEO Actually Means for This Page

When someone asks ChatGPT or Google AI Overviews something like *"why do downtown San Diego condos have a guest parking problem?"* or *"how do HOA boards manage guest parking?"* — the AI pulls from pages it has already indexed and trusts. For our page to get cited, it needs to be:

1. Easy for AI to extract specific answers from
2. Structured so AI understands what type of content it is
3. Credible-looking with clear authorship and sourcing
4. Fast and technically sound

Most of what's below is adding invisible code (called "structured data" or "schema") to the HTML that tells AI systems exactly what the page is about. Think of it like labeling boxes clearly for a warehouse robot — the content is already there, we just need better labels.

---

## Priority 1 — Highest Impact (Do These First)

### 1. Add FAQ Schema to the FAQ Section
**What it is:** A hidden tag in the HTML that tells Google and AI crawlers "this section is a list of questions and answers."

**Why it matters:** This is the single biggest AEO win on this page. The FAQ section already has 9 strong questions with detailed answers. Right now, AI systems have to guess that this is a Q&A section. Adding FAQ schema removes the guesswork and puts us in the running for AI Overview snippets directly.

**What needs to change:** Each question and answer in the FAQ section needs to be wrapped in structured data code (added once in the `<head>` of the file — nothing visible changes on the page).

---

### 2. Add Article Schema (Author + Publish Date)
**What it is:** Hidden code that tells AI: "This is an article, written by SpotShare, published on [date], last updated on [date]."

**Why it matters:** ChatGPT and AI Overviews strongly prefer sourcing content that has a clear author and a recent date. Right now our page has no author, no publish date, and no last-updated date anywhere — which makes AI systems treat it as anonymous, undated content. That's a credibility hit.

**What needs to change:**
- Add a publish date and "last updated" date visibly somewhere on the page (even small, like below the hero)
- Add hidden Article schema code naming SpotShare as the author/publisher
- Add SpotShare's website URL as the publisher

---

### 3. Make the Sources into Actual Links
**What it is:** Turn the plain-text source citations at the bottom of each section into real clickable links.

**Why it matters:** AI systems (especially Perplexity and ChatGPT with browsing) follow links to verify claims. Right now our sources read like a bibliography but have no working links — which means AI cannot validate the data we're citing. Linked citations signal that our facts are real and checkable, which increases the chance we get cited ourselves.

**What needs to change:** Each source note in the page needs its URLs turned into actual `<a href>` links. We already have the source text — we just need to add the working URLs.

---

### 4. Add an Organization Schema for SpotShare
**What it is:** Hidden code that formally identifies SpotShare as a company — including our website URL, description, and what we do.

**Why it matters:** AI systems build a "knowledge graph" of companies and sources they trust. Without this, SpotShare is just a name in text. With it, AI systems can connect our page to SpotShare as a known entity — which is how you eventually start showing up in answers like "companies that offer HOA parking management."

**What needs to change:** One block of hidden code added to the `<head>` of the file. No visible changes.

---

## Priority 2 — Strong Supporting Wins

### 5. Use Proper Semantic HTML Tags
**What it is:** Changing some of the page's invisible structure tags from generic `<div>` to more descriptive ones like `<main>`, `<article>`, and `<nav>`.

**Why it matters:** AI crawlers use these tags to understand what part of a page is the main content vs. navigation vs. sidebar. Right now the entire page body is wrapped in generic `<div>` containers. Using `<article>` and `<main>` tags signals "this is the core content, prioritize it."

**What needs to change:**
- Wrap the main content area in `<main>` tags
- Wrap the article body in `<article>` tags
- The nav and footer are already correct

---

### 6. Add a HowTo Schema for the Implementation Timeline Table
**What it is:** Hidden code that labels the "How Long Does It Take?" table as a step-by-step process.

**Why it matters:** Google AI Overviews frequently pull step-by-step processes into direct answer cards. Our implementation timeline (Board Assessment → Board Vote → Integration → Opt-in → Go-live) is exactly the kind of structured process that gets cited. Adding HowTo schema makes it eligible for that format.

**What needs to change:** Hidden code added around the implementation table. No visible changes.

---

### 7. Add an Open Graph Image
**What it is:** A preview image that shows when the page is linked or shared.

**Why it matters:** Perplexity and ChatGPT both show source previews when they cite a page. A page with no preview image looks less credible than one with a clean, branded image. This also helps with LinkedIn and Twitter sharing which drives traffic that builds AI awareness of the page.

**What needs to change:** Create one simple branded image (1200x630px) and add two lines of code to the `<head>` pointing to it.

---

### 8. Add a Speakable Schema to the Key Summary Paragraphs
**What it is:** A tag that tells AI assistants "this paragraph is the best plain-English summary of this topic."

**Why it matters:** This is specifically designed for AI and voice assistants. When an AI reads our page and looks for a quote to pull, speakable schema tells it exactly which sentences to use. Without it, the AI guesses — and might pull a less useful sentence.

**What needs to change:** Tag 2–3 specific paragraphs in the page as the "speakable" summary. The best candidates are the hero intro paragraph and the opening of the "How Buildings Are Solving It" section.

---

## Priority 3 — Content Additions That Help AI

### 9. Add a "What Is SpotShare?" Direct Answer Block
**What it is:** A short, 2–3 sentence plain-English description of SpotShare at the top of the page.

**Why it matters:** AI systems need a direct, quotable definition to cite when someone asks "what is SpotShare?" Right now the page assumes the reader already knows. The hero attribution line ("produced by SpotShare, a guest parking infrastructure platform...") is close but too brief and doesn't stand alone well as a citation.

**What needs to change:** Add a short definition block near the top — ideally right after the hero — that clearly answers: "SpotShare is [what], for [who], that solves [what problem]."

---

### 10. Add a TL;DR Summary Section at the Top
**What it is:** A 3–5 bullet summary of the page's key points, placed near the top of the article.

**Why it matters:** AI Overviews almost always prefer to pull from clearly summarized content near the top of a page rather than extract from long paragraphs buried mid-page. A TL;DR gives AI a ready-made answer block for questions like "what is the guest parking situation in downtown San Diego condos?"

**What needs to change:** Add a short "Key Takeaways" or "TL;DR" box after the hero section, before the first content section. Bullet points only — no paragraphs.

---

### 11. Add a "Last Updated" Line Visibly on the Page
**What it is:** A visible date line like "Last updated: May 2026" near the hero or below the page title.

**Why it matters:** AI systems heavily weight content recency. Our page references 2026 events throughout, but there is no date stamp anywhere visible. AI crawlers may treat the page as undated and deprioritize it for time-sensitive queries. This is a one-line fix with real impact.

**What needs to change:** Add a single "Last updated: [Month Year]" line below the hero sub-headline.

---

## What We Do NOT Need to Change

- The content itself is strong. The depth, specificity, and local data (parking rate doubles, Andia by Bosa, reform timelines) are exactly what AI systems look for in a citable source.
- The FAQ questions are already written in natural language — they match how people actually ask questions to ChatGPT. No rewrites needed.
- The page title and meta description are solid.
- The page structure (H1 → H2 → H3) is correct and does not need changes.

---

## Summary Checklist

| # | Change | Priority | Visible to Users? |
|---|--------|----------|-------------------|
| 1 | Add FAQ schema | High | No |
| 2 | Add Article schema + publish date | High | Date only |
| 3 | Turn source citations into real links | High | Yes |
| 4 | Add Organization schema for SpotShare | High | No |
| 5 | Use semantic HTML tags (main, article) | Medium | No |
| 6 | Add HowTo schema to implementation table | Medium | No |
| 7 | Add Open Graph image | Medium | Preview only |
| 8 | Add Speakable schema to key paragraphs | Medium | No |
| 9 | Add "What Is SpotShare?" definition block | Medium | Yes |
| 10 | Add TL;DR / Key Takeaways box | Medium | Yes |
| 11 | Add "Last Updated" date line | Low | Yes |
