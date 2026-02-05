# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static single-page site for Portrait Lounge (portraitloungelive.com), a live portrait experience business for events based in Lake Forest, CA (Orange County area). No framework or build system, pure HTML/CSS/JavaScript in a single `index.html` file with an `images/` directory.

## Development

No build step. To preview locally:

```bash
python -m http.server
# or
npx http-server
```

No test suite or linting is configured.

## Architecture

Everything lives in `index.html`:

- **Head**: meta/SEO tags, OpenGraph, Schema.org structured data (LocalBusiness, Service, FAQPage, BreadcrumbList, WebSite), Google Fonts (Montserrat), custom font (Perandory Semi Condensed)
- **`<style>` block**: CSS variables for dark/gold theming, component styles organized by section, animations, responsive breakpoints (768px mobile, 1024px tablet)
- **Body HTML**: fixed navbar, hero, brand intro, how it works, services cards, portfolio grid, marquee, testimonials, FAQ accordion, contact form, footer
- **`<script>` block**: navbar scroll behavior, mobile menu toggle, Intersection Observer fade-ins, smooth scroll, testimonial carousel, FAQ accordion, form submission

## Key Integration

The contact form POSTs to a Zapier webhook (placeholder URL, needs to be configured). It sends name, email, phone, event date, event type, venue, message, referral source, timestamp, and source URL.

## Hosting

This site will be hosted on Coolify as a static site. Pushing to `main` deploys to production.

## Git Policy

Never push to git without explicit user approval. Always ask before running `git push`.

## Secrets & Environment Variables

Never put sensitive keys, API secrets, or environment variables directly in the website code. If a key needs to be added, tell the user to contact Omer to have it added as an environment variable in Coolify.

## SEO

After creating any new page (blog post, landing page, etc.), always run the `seo-audit` skill to review and improve its SEO before considering the task complete.

## Writing Style

Never use em dashes in any content. Use commas, periods, semicolons, or rewrite the sentence instead.

## Image Optimization

Whenever images are added to the project, always optimize them before they go live. Resize to a max width of 1600px, compress to reduce file size, and convert to JPG at reasonable quality. Use `sips` (macOS built-in) or `imagemagick` if available. Never serve unoptimized camera files directly on the site.

## CSS Theming

Colors and fonts are controlled via CSS custom properties defined at the top of the style block. The site uses a dark theme:

- `--black: #0a0a0a` (primary background)
- `--dark: #111111` (alternate dark background)
- `--dark-surface: #1a1a1a` (card/section backgrounds)
- `--gold: #c9a84c` (primary accent, CTAs, highlights)
- `--gold-dark: #b8952a` (secondary gold)
- `--gold-light: #d4b96a` (hover states)
- `--cream: #f5f0e8` (primary text on dark)
- `--white: #ffffff` / `--off-white: #fafafa`

Fonts:
- **Perandory Semi Condensed** (custom, `/fonts/PerandorySemiCondensed.otf`): All headings (h1, h2, h3)
- **Montserrat** (Google Fonts, weights 200-600): Body text, buttons, labels

## Contact Info

- **Owner**: Guramrit Singh Malhotra
- **Phone**: 949-312-8300
- **Email**: guramrit.art@gmail.com
- **Instagram**: @portraitlounge.live
- **Location**: Lake Forest, CA 92630 (serves Orange County, Los Angeles, and beyond)

## Blog

Fully static blog (Phase 2, not yet built). Each post will be a standalone HTML file in `blog/`. No markdown rendering or fetch calls.

- **Listing page**: `blog.html` (future)
- **Post files**: `blog/[slug].html`
- **Images**: `images/blog-{slug}/`
- All links use relative paths so navigation works locally and on the server
- Every blog post must include a contact form and FAQ section after the article content

---

## FTWP Brand & Marketing Framework

This site follows the Full Time Wedding Pro (FTWP) Phase 1 methodology by Peyton Helm. All website copy, structure, and strategy should align with these principles.

### Core Philosophy

**What We Sell (Not deliverables)**
- The experience, the memory, the keepsake
- NOT hours of coverage, number of photos, or technical specs
- This is priceless, which opens the gateway to premium pricing

**Brand vs Commodity**
- A website showing photos + contact form = commodity/shop
- A brand emotionally connects, inspires, educates, and guides ideal clients
- Goal: Transform from commodity photo booth alternative to premium portrait experience brand

### Website Golden Rule

> Your website is your storefront. The goal is to emotionally connect with, inspire, educate, and empower ONLY your most perfect ideal client, and effortlessly guide them to your contact form through simplicity, trust, empathy, and confidence.

Every word, image, and video must serve this purpose.

### Website Structure (80% of Results)

**Predetermined Paths**
- Guide visitors through intentional paths that all lead to the contact form
- Every section: ONE title, content, ONE call to action to ONE predetermined location

**Critical Rules**
- Contact form on EVERY page and blog post
- Never send people off your site until after they inquire
- Never have dead-end pages
- Create context switches (change background colors between sections = dopamine spikes)
- Must have a blog (SEO, education, personal connection)
- Create a Thank You page (critical for ad tracking)

**The Grunt Test (Hero Section Must Show)**
- Who you are
- What you do
- Who you serve
- Where you are
- Button to contact

### Copywriting (80% of Results)

**SB7 Framework (StoryBrand)**
1. Character (the event host/bride/organizer) has a problem
2. Meets a guide (Portrait Lounge)
3. Guide gives a plan
4. Calls them to action
5. Happy ending

**Copy Guidelines**
- Website should read at 3rd grade level
- Use clear CTAs: "Book Your Event" not "Learn More"
- Every word should emotionally connect with ideal client or make brand memorable

### Pricing Strategy

**What to Show**
- Starting rate (recommended): Qualifies leads without turning them away
- Always link to services/packages above every contact form

**Package Structure (3 collections)**
- Top Tier (Bespoke): Price anchor, everything offered, starting at $3,500
- Middle Tier (Signature): What you want to sell, $2,200
- Bottom Tier (Digital): Minimum, $1,200

**Psychology of Numbers**
- Price anchoring: Highest collection FIRST (top or left)
- No hourly language. Charge for the RESULT, not the process

### Contact Form Structure

**Long forms preferred (qualify leads, save time)**

**Required Fields**
- Full name, Email, Phone number
- Event date, Event type, Venue/location
- "Where did you hear about us?" (critical for ad tracking)
- "Tell me more" open text

### Tracking & Analytics (Non-Negotiable)

**FullStory (Free)**
- Screen records visitor behavior
- 10,000 sessions/month free

**Google Analytics**
- Engagement rate, bounce rate, page load times
