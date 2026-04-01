# EA at UCLA: SEO & Website Optimization Guide

**Prepared for Steven Veld | Spring 2026**

---

## Part 1: Diagnosing the Current Site

### What's Working

Your current site (eaucla.org) has genuine strengths worth preserving:

- **Visual design is solid.** Clean layout, good use of the rotating text hero, professional card-based program display. This is already ahead of most university EA groups.
- **Program structure is well-presented.** The Frontiers Fellowship, Career Pathways, and Career Accelerator are clearly differentiated with time commitments and CTAs.
- **Events section is timely.** You're actually keeping it updated with real upcoming events, which many groups fail at.
- **Alumni section exists.** Kuhan's story is compelling. This is a strong differentiator.

### What Needs Work

Based on your advisor's notes and the site audit, here are the core problems:

**1. SEO is essentially nonexistent.**
- The site title is "Effective Altruism at UCLA | Evidence & Reason" — the subtitle is wasted space. Nobody searches "evidence and reason."
- There's only one indexable page in Google's main results for `site:eaucla.org`. The old Squarespace pages (syllabus-longtermism, ea-orgs, etc.) are still indexed but the new Vite site likely has minimal meta tags.
- No structured data, no Open Graph tags, no sitemap.xml (or if there is one, it's not working well).
- LinkedIn shows only 7 followers. Instagram presence unclear.

**2. The CTAs are buried and generic.**
- "Join Newsletter" and "Join Discord" are the only two actions in the nav. Both are low-commitment but also low-conversion — a new visitor doesn't know why they should join either.
- There's no "Book a 1-on-1" option anywhere on the site.
- There's no lightweight "let us know you exist" form.
- The mailing list signup goes to a generic Mailchimp page, not an embedded form.

**3. The site doesn't capture search intent from non-EA people.**
- A UCLA student googling "UCLA clubs for social impact" or "high-impact careers UCLA" or "AI safety UCLA" will never find you.
- You're only discoverable by people who already know the phrase "effective altruism."

**4. Community page has placeholder content.**
- Multiple "Alumni Name" and "Mentor Name" placeholders are still live. This actively hurts credibility.

---

## Part 2: SEO Strategy

### 2A. Keyword Strategy

Your advisor's core insight is right: you need to rank for terms that people *actually search*, not just "effective altruism UCLA." Here's a concrete keyword map.

#### Tier 1: Brand Keywords (You should own these)
These are searches from people who already know you exist.

| Keyword | Monthly Volume (est.) | Current Ranking |
|---------|----------------------|-----------------|
| EA UCLA | Low | Likely #1 |
| Effective altruism UCLA | Low | Likely #1 |
| EA at UCLA | Low | Likely #1 |

**Action:** Make sure your title tag, H1, and meta description all contain "Effective Altruism at UCLA" or "EA at UCLA."

#### Tier 2: Discovery Keywords (How new members find you)
These are searches from UCLA students who don't know EA exists but are interested in adjacent things.

| Keyword | Why It Matters |
|---------|---------------|
| UCLA clubs for social impact | Direct funnel for mission-aligned students |
| high impact careers UCLA | Matches your Career Accelerator positioning |
| AI safety UCLA | You're one of the only groups doing this at UCLA |
| UCLA student organizations giving / charity | Captures the "effective giving" angle |
| UCLA philosophy clubs | Some overlap with EA's philosophical foundations |
| UCLA career fellowships | Matches Frontiers Fellowship and Career Pathways |
| how to do good UCLA | Long-tail, but captures the EA pitch exactly |
| UCLA clubs for global health | Captures cause-area interest |
| UCLA biosecurity | Niche but high-intent |
| best UCLA clubs to join | Competitive but worth having content for |

**Action:** Create dedicated landing pages or content sections that naturally incorporate these terms. More on this below.

#### Tier 3: Broader Interest Keywords (Content marketing)
These aren't UCLA-specific but can drive traffic from students researching topics you cover.

| Keyword | Content Type |
|---------|-------------|
| what is effective altruism | Explainer page (you have /ea.html — optimize it) |
| AI safety careers | Blog post or resource page |
| effective giving guide college students | Blog post |
| longtermism explained | Content page |
| high impact career paths | Resource page (you have /jobs — optimize it) |
| 80000 hours career guide summary | Blog content |

### 2B. On-Page SEO — Technical Fixes

These are changes to make in your Vite codebase (the GitHub repo).

#### Title Tags
Every page needs a unique, keyword-rich title tag under 60 characters.

| Page | Current Title | Recommended Title |
|------|--------------|-------------------|
| Home | Effective Altruism at UCLA \| Evidence & Reason | Effective Altruism at UCLA — High-Impact Careers & Fellowships |
| Community | About Us \| Effective Altruism at UCLA | Meet the Team — EA at UCLA |
| EA explainer | (unknown) | What Is Effective Altruism? — EA at UCLA |
| Jobs | Career Opportunities \| Explore Impactful Careers Today | AI Safety & High-Impact Careers — EA at UCLA |

#### Meta Descriptions
Write compelling 150-160 character descriptions for every page. These show up in Google results and are your "ad copy."

**Home page example:**
```
UCLA's community for students tackling the world's most pressing problems. Join our fellowships, career programs, and 1-on-1 advising. Free to join.
```

**EA explainer example:**
```
What is effective altruism? Learn how UCLA students use evidence and reason to find the highest-impact ways to improve the world.
```

#### Open Graph & Social Meta Tags
Add these to every page's `<head>` for proper social sharing:

```html
<meta property="og:title" content="Effective Altruism at UCLA" />
<meta property="og:description" content="UCLA's community for high-impact careers and evidence-based giving." />
<meta property="og:image" content="https://www.eaucla.org/assets/og-image.png" />
<meta property="og:url" content="https://www.eaucla.org/" />
<meta property="og:type" content="website" />
<meta name="twitter:card" content="summary_large_image" />
```

Create a dedicated OG image (1200x630px) with your logo, a clean background, and the text "Effective Altruism at UCLA."

#### Sitemap & Robots.txt
If you don't already have these:

**robots.txt** (at root):
```
User-agent: *
Allow: /
Sitemap: https://www.eaucla.org/sitemap.xml
```

**sitemap.xml**: Generate one listing every public page with `<lastmod>` dates. Vite has plugins for this (e.g., `vite-plugin-sitemap`).

#### Structured Data (JSON-LD)
Add this to your homepage to help Google understand what you are:

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Effective Altruism at UCLA",
  "alternateName": "EA at UCLA",
  "url": "https://www.eaucla.org",
  "logo": "https://www.eaucla.org/assets/EAAUCLAlogo.png",
  "description": "A student community at UCLA focused on using evidence and reason to do the most good.",
  "parentOrganization": {
    "@type": "CollegeOrUniversity",
    "name": "University of California, Los Angeles"
  },
  "sameAs": [
    "https://discord.com/invite/BqRrBmBtPq",
    "https://www.linkedin.com/company/effective-altruism-at-ucla",
    "https://www.instagram.com/eaucla/",
    "https://forum.effectivealtruism.org/"
  ]
}
```

Add `Event` structured data for each upcoming event too — this can get you into Google's event search results.

#### Page Speed & Technical
- Run Google PageSpeed Insights on eaucla.org and fix any flagged issues.
- Ensure all images have `alt` text (descriptive, keyword-relevant where natural).
- Make sure the site is fully mobile-responsive (it likely is with Vite, but verify).
- Ensure all old Squarespace URLs either redirect to new equivalents or return proper 404s. Right now Google is indexing orphaned pages like `/syllabus-longtermism` and `/ea-orgs` from the old site.

### 2C. Off-Page SEO & Link Building

For a student org, "link building" mostly means getting listed in the right places.

#### Must-Have Listings
- **UCLA Student Organizations directory** — make sure your listing is complete with website URL, description, and correct contact info.
- **EA Hub / effectivealtruism.org group directory** — verify your listing is up to date.
- **EA Forum** — post your annual review, fellowship results, or any research. Each post links back to your site.
- **80,000 Hours community page** — check if you can get listed.

#### LinkedIn
Your LinkedIn page has 7 followers. This is a missed opportunity because LinkedIn pages rank well in Google.

- Update the LinkedIn company page with full description, logo, cover image, and website link.
- Post quarterly updates (fellowship launches, event recaps, alumni highlights).
- Have board members list "EA at UCLA" as an experience on their personal profiles.
- The description should contain keywords: "effective altruism," "high-impact careers," "AI safety," "UCLA student organization," "evidence-based giving."

#### Instagram
If you don't have an active Instagram, start one. 85% of college students use Instagram. Post:
- Event announcements with location/time
- Fellowship application reminders
- Quick "EA concept of the week" carousels
- Photos from events and retreats
- Alumni spotlight stories

Bio should include: website link, "UCLA's community for high-impact careers" or similar, and a Linktree or equivalent with all your CTAs.

#### Google Business Profile
This is unconventional for a student org, but if you have a regular meeting location, you *can* create a Google Business Profile. This gets you into local search results and Google Maps. Worth exploring — your advisor specifically mentioned this approach (the UToronto example).

---

## Part 3: Website Redesign Recommendations

### 3A. Homepage Hero — Immediate CTAs

Your advisor's key recommendation: the homepage should immediately present a clear range of actions a visitor can take. Right now the hero has "Explore Programs" and "See Events." These are fine but they're both passive — they send people deeper into the site rather than converting them.

**Redesigned CTA Section (below the hero fold):**

Replace or supplement the current hero buttons with a 3-column CTA block:

#### CTA 1: "Come to Our Next Event"
- Show the next upcoming event with date, time, and location
- One-click RSVP button
- Auto-updates (pull from your events data)
- This is for the casual browser: low commitment, come check us out

#### CTA 2: "Book a 1-on-1"
- Show 2-3 organizer photos (good ones — your advisor stressed this) with first names
- "Chat with us about EA, careers, or getting involved"
- Links to a Calendly or similar scheduling tool
- This is for the curious-but-hesitant: personal connection before commitment

**Who to feature:** Pick 2-3 people who are genuinely good at 1-on-1 conversations — warm, non-judgmental, good at meeting people where they are. This probably means you, Will, and maybe one other board member. Get professional-looking headshots (good lighting, clean background, friendly expression). The current team photos vary in quality.

#### CTA 3: "Stay in the Loop"
- Embedded 3-field form: Name, Email, "How familiar are you with EA?" (dropdown: "Just learning" / "Somewhat familiar" / "Very familiar")
- This replaces the external Mailchimp link
- The familiarity question is gold for segmentation — you can send different follow-up content to newcomers vs. people who already know the movement

**Why this matters:** Right now, a new visitor has to click through to a separate Mailchimp page to sign up for anything. Every extra click loses people. An embedded form on the homepage captures interest in the moment.

### 3B. Programs Section — Keep, But Add Context

The current programs section is well-structured. Minor improvements:

- **Add "No prior EA knowledge required"** prominently to the Frontiers Fellowship card. This is your top-of-funnel program and new visitors need to know they're welcome.
- **Add expected time commitment more visually** — the current "7 Weeks / 2 hrs/wk reading / 1 hr/wk discussion" is good but could be a small visual timeline or progress indicator.
- **Career Pathways says "List of professional guests coming soon!"** — either add the list or remove the placeholder. Placeholders signal "we haven't finished this."

### 3C. Social Proof Section

Add a new section between Programs and Events:

**"Where EA at UCLA Members End Up"**

This is a condensed version of your alumni page, but on the homepage. Show 3-4 real alumni with:
- Photo
- Name
- Current role (e.g., "AI Safety Researcher at [Org]" or "Policy Fellow at GovAI")
- One sentence on their EA at UCLA involvement

You already have Kuhan's story and Felipe Calero Forero's background. Fill out the rest with real people — the current "Alumni Name" placeholders need to go immediately. If you don't have enough alumni stories yet, reach out to former members this quarter and collect them. Even 2-3 real stories are better than 5 placeholders.

### 3D. Content Pages for SEO

Create these pages to capture the discovery keywords from Part 2:

#### /what-is-ea (or optimize existing /ea.html)
- Title: "What Is Effective Altruism? | EA at UCLA"
- 800-1200 words explaining EA in accessible language
- Link to introductory resources (Doing Good Better, 80K Hours, etc.)
- CTA at bottom: "Want to learn more? Join our Frontiers Fellowship"

#### /careers (optimize existing /jobs)
- Title: "High-Impact Career Paths | EA at UCLA"
- Organize by cause area: AI safety, global health, biosecurity, policy, etc.
- For each: what the field is, what roles exist, how to get started, UCLA-specific resources
- Link to Career Accelerator and Career Pathways
- This page can rank for "high impact careers UCLA," "AI safety careers," etc.

#### /blog or /writing (optimize existing section)
- Publish the writing your community produces (you mention an AI Frontiers piece on opt-in surveillance)
- Each post should have its own URL, proper title tag, and meta description
- Even 1-2 quality posts per quarter helps SEO — Google rewards fresh content

#### /for-new-members
- A dedicated onboarding page: "New to EA? Start Here"
- Brief explainer, link to fellowship, link to book a 1-on-1, link to next event
- This is your landing page for Instagram bio links, flyer QR codes, etc.

### 3E. Things to Fix Immediately

These are quick wins that don't require a redesign:

1. **Remove all placeholder content.** The "Alumni Name," "Mentor Name" entries on /community.html actively damage credibility. Either fill them with real people or remove them entirely.

2. **Fix the community page header.** "We're looking for promising candidates to expand our board! Board applications will open during week 2." — if it's past week 2, update or remove this.

3. **Add a favicon.** Check if you have one — small thing, but it signals polish.

4. **Add footer links.** Your footer only has Email and EA Forum. Add: Instagram, LinkedIn, Discord, and your UCLA student org page.

5. **Old Squarespace URLs.** Set up redirects for any old URLs that are still being indexed (longtermism syllabus, ea-orgs, etc.) to point to equivalent pages on the new site, or to the homepage if no equivalent exists.

---

## Part 4: Social Media & Online Presence Checklist

### Platforms to Maintain

| Platform | Priority | Current Status | Action |
|----------|----------|---------------|--------|
| Website (eaucla.org) | Critical | Active, needs SEO work | Implement this guide |
| Discord | High | Active | Keep — this is your community hub |
| Instagram | High | Unclear | Create or revive; post 2-3x/week during quarter |
| LinkedIn (org page) | Medium | 7 followers, sparse | Update fully, post monthly |
| Newsletter (Mailchimp) | Medium | Active | Embed form on homepage |
| EA Forum | Medium | Occasional | Post fellowship results, annual reviews |
| YouTube/TikTok | Low (for now) | None | Only if you have capacity; short-form video of events could work |

### Instagram Content Calendar (Example Quarter)

**Week 1:** "Welcome back! Here's what EA at UCLA is doing this quarter" carousel
**Week 2:** General meeting announcement + registration link
**Week 3:** "What is effective altruism?" carousel (3-5 slides, accessible language)
**Week 4:** Fellowship spotlight — what the Frontiers Fellowship covers
**Week 5:** Career Pathways guest speaker announcement
**Week 6:** Midquarter photo dump from events
**Week 7:** "EA concept of the week" — ITN framework, expected value, etc.
**Week 8:** Alumni spotlight story
**Week 9:** Fellowship application reminder (for next quarter)
**Week 10:** Quarter recap + "apply for board" CTA

### Cross-Linking Strategy

Every platform should link to every other platform, and all should link back to the website:
- Instagram bio → Linktree with: Website, Discord, Newsletter signup, Next event RSVP
- LinkedIn → Website in description
- Discord → Pinned message with website and Instagram
- Website → All platforms in footer and header
- Newsletter → Links to latest blog post, next event, Instagram

---

## Part 5: Implementation Priority

If you're doing this with limited bandwidth (which you are, as a student org), here's the order:

### This Week
1. Remove all placeholder content from /community.html
2. Update meta titles and descriptions on all pages
3. Add Open Graph tags to all pages
4. Embed the mailing list form on the homepage (even a simple 3-field version)

### This Month
5. Create or update Instagram account with consistent branding
6. Update LinkedIn company page fully
7. Add structured data (JSON-LD) to homepage
8. Create sitemap.xml and robots.txt
9. Set up redirects for old Squarespace URLs
10. Add "Book a 1-on-1" CTA with Calendly links

### This Quarter
11. Create /for-new-members landing page
12. Optimize /ea.html for "what is effective altruism" keyword
13. Optimize /jobs for career-related keywords
14. Publish 1-2 blog posts with proper SEO
15. Collect and publish real alumni stories (replace placeholders)
16. Redesign homepage hero section with 3-CTA block

### Ongoing
- Post 2-3x/week on Instagram during active quarters
- Post monthly on LinkedIn
- Update events section as events change
- Publish at least 1 piece of writing per quarter
- Run Google Search Console monthly to check indexing and search queries

---

## Part 6: Measuring Success

### Set Up Google Search Console
If you haven't already, verify eaucla.org in Google Search Console. This is free and tells you:
- Which search queries bring people to your site
- Which pages are indexed
- Any crawl errors or issues

### Set Up Google Analytics (GA4)
Track:
- Total sessions per month
- Top landing pages
- Referral sources (where traffic comes from)
- Newsletter signup conversions

### Benchmarks to Aim For
After implementing this guide, reasonable 6-month targets:

| Metric | Current (est.) | Target |
|--------|---------------|--------|
| Monthly organic sessions | < 100 | 300-500 |
| Pages indexed in Google | ~5-10 | 15-20 |
| Instagram followers | 0 or low | 200+ |
| LinkedIn followers | 7 | 50+ |
| Newsletter signups/quarter | Unknown | 30-50 new |
| 1-on-1 bookings/quarter | 0 (no system) | 10-20 |

---

## Appendix: Quick Reference for Vite/HTML Implementation

### Meta Tag Template (add to each page's `<head>`)
```html
<!-- Primary Meta -->
<title>[Page Title] — EA at UCLA</title>
<meta name="description" content="[150-160 char description]" />

<!-- Open Graph -->
<meta property="og:type" content="website" />
<meta property="og:url" content="https://www.eaucla.org/[page]" />
<meta property="og:title" content="[Page Title] — EA at UCLA" />
<meta property="og:description" content="[Same or similar to meta description]" />
<meta property="og:image" content="https://www.eaucla.org/assets/og-image.png" />

<!-- Twitter -->
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:title" content="[Page Title] — EA at UCLA" />
<meta name="twitter:description" content="[Description]" />
<meta name="twitter:image" content="https://www.eaucla.org/assets/og-image.png" />
```

### Structured Data Template (homepage)
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Effective Altruism at UCLA",
  "alternateName": "EA at UCLA",
  "url": "https://www.eaucla.org",
  "logo": "https://www.eaucla.org/assets/EAAUCLAlogo.png",
  "description": "A student community at UCLA using evidence and reason to find the best ways to improve the world.",
  "parentOrganization": {
    "@type": "CollegeOrUniversity",
    "name": "University of California, Los Angeles"
  }
}
</script>
```

### Event Structured Data Template
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Event",
  "name": "Spring General Meeting",
  "startDate": "2026-04-08T18:00:00-07:00",
  "location": {
    "@type": "Place",
    "name": "Powell Library Rm B, UCLA",
    "address": "Los Angeles, CA 90095"
  },
  "organizer": {
    "@type": "Organization",
    "name": "Effective Altruism at UCLA",
    "url": "https://www.eaucla.org"
  },
  "description": "Introduction to Effective Altruism and overview of spring quarter initiatives.",
  "eventAttendanceMode": "https://schema.org/OfflineEventAttendanceMode"
}
</script>
```

### Image Alt Text Examples
```html
<!-- Bad -->
<img src="logo.png" alt="logo" />

<!-- Good -->
<img src="logo.png" alt="Effective Altruism at UCLA logo" />

<!-- Bad -->
<img src="StevenVeld.png" alt="photo" />

<!-- Good -->
<img src="StevenVeld.png" alt="Steven Veld, Co-President of EA at UCLA" />
```
