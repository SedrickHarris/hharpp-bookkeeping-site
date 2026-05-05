# Claude Code Prompt — Hharpp Homepage

## Your task
Read `content.json` in this directory. Build `index.html` — a complete,
production-ready homepage for Hharpp Business Services. Every word of
copy, every testimonial, every FAQ answer, every service description, and
every schema value comes from `content.json`. Do not invent anything.
Do not use placeholder text. Do not skip any section.

---

## Before you write a single line of HTML

1. Read `content.json` completely
2. Confirm you have loaded: company info, all 7 services, all 4 testimonials,
   all 6 FAQs with voice_answer AND full_answer, all quiz questions and all
   7 result states, the lead magnet content, and all SEO fields
3. Only then begin writing `index.html`

---

## File specification

**Output file:** `index.html`
**Format:** Single self-contained HTML file
- All CSS in one `<style>` block inside `<head>` — no external stylesheets
- All JavaScript in one `<script>` block immediately before `</body>` — no external scripts
- Google Fonts loaded via `@import url(...)` inside the `<style>` block
- All 5 schema blocks as separate `<script type="application/ld+json">` tags in `<head>`
- No broken `<img>` tags — use styled `<div>` elements for image placeholders
- All internal links use the `url` fields from `content.json` — no `#` placeholder hrefs
  except the lead magnet form action (which should be `action="#"`)

---

## Design system — implement exactly

```css
/* Font import */
@import url('https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,400;0,600;1,400;1,600&family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap');

/* CSS custom properties */
:root {
  --gold:         #B8960C;
  --gold-lt:      #FFF8E0;
  --gold-dk:      #8A6500;
  --gold-border:  #D4A017;
  --navy:         #1B3A5C;
  --navy-lt:      #E8EFF6;
  --warm-white:   #F7F4EF;
  --white:        #FFFFFF;
  --charcoal:     #2C2C2C;
  --mid-grey:     #6B6B6B;
  --font-serif:   'Lora', Georgia, serif;
  --font-sans:    'Plus Jakarta Sans', system-ui, sans-serif;
}
```

**Typography rules:**
- H1: font-family var(--font-serif), font-weight 600, font-size clamp(32px, 5vw, 42px), color var(--navy), line-height 1.15
- H2: font-family var(--font-serif), font-weight 600, font-size 28px, color var(--navy), line-height 1.2
- H3: font-family var(--font-serif), font-weight 400, font-size 20px, color var(--navy), line-height 1.3
- Pull quote: font-family var(--font-serif), font-style italic, font-size 18px, color var(--gold)
- Body: font-family var(--font-sans), font-weight 400, font-size 16px, color var(--charcoal), line-height 1.7
- Small body: font-family var(--font-sans), font-size 14px, color var(--mid-grey), line-height 1.6
- Eyebrow: font-family var(--font-sans), font-weight 600, font-size 11px, text-transform uppercase, letter-spacing 0.1em, color var(--gold-dk)
- Button: font-family var(--font-sans), font-weight 600, font-size 13px

**Component rules:**
- Primary button: background var(--navy), color #fff, padding 11px 24px, border-radius 6px, border none, cursor pointer, transition background 0.15s
- Primary button hover: background #0F2238
- Gold CTA button: background var(--gold), color #fff, same padding and radius
- Secondary link: color var(--gold), text-decoration none, border-bottom 1.5px solid var(--gold), padding-bottom 1px
- Card: background #fff, border 0.5px solid rgba(0,0,0,0.1), border-radius 12px, padding 24px
- Testimonial card: white bg, left border 3px solid var(--gold), border-radius 0 12px 12px 0, padding 20px 24px
- Gold pill/chip: background var(--gold-lt), color var(--gold-dk), border 0.5px solid var(--gold-border), border-radius 99px, padding 4px 14px, font-size 12px, font-family var(--font-sans), font-weight 500
- Navy pill: background var(--navy-lt), color var(--navy), border 0.5px solid rgba(27,58,92,0.3), border-radius 99px, padding 3px 10px, font-size 11px

---

## Page sections — build all 12 in this exact order

### 1. `<head>`
Populate every field from `content.json` seo object:
- `<meta charset="UTF-8">`
- `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
- `<title>` from seo.title
- `<meta name="description">` from seo.meta_description
- `<link rel="canonical">` from seo.canonical
- `<meta name="robots" content="index, follow, max-snippet:-1, max-image-preview:large, max-video-preview:-1">`
- `<meta name="author" content="Heather Potvin, CPB">`
- Geo tags: geo.region, geo.placename, geo.position, ICBM — from seo object
- Open Graph: og:title, og:description, og:type (website), og:url, og:image, og:site_name, og:locale (en_US)
- Twitter card: twitter:card (summary_large_image), twitter:title, twitter:description, twitter:image
- Google Fonts `@import` inside `<style>` block
- All CSS inside `<style>` block
- All 5 schema blocks (see SCHEMA section below)

### 2. NAV
- `<nav>` element, sticky (position sticky, top 0, z-index 100, background white, border-bottom 0.5px solid rgba(0,0,0,0.08), backdrop-filter blur(8px))
- Inner container: max-width 1200px, margin 0 auto, padding 0 24px, display flex, align-items center, justify-content space-between, height 64px
- Logo: `<a href="/">` containing "Hharpp" in font-serif, font-weight 600, font-size 22px, color var(--navy), text-decoration none
- Nav links (hide on mobile < 768px): Services → #services | Construction → #construction | About → /about/ | FAQ → /faq/ | Contact → /contact/ — font-sans 14px 500 charcoal, text-decoration none, opacity 0.8, hover opacity 1
- CTA button: "Book a free consultation" → /contact/ — gold CTA button style, font-size 13px, padding 9px 18px
- Trust micro-line: `<div>` below the main nav bar, text-align center, font-size 11px, color var(--mid-grey), padding 6px, background var(--warm-white), border-bottom 0.5px solid rgba(0,0,0,0.05) — content: "Serving Nevada & California · 100% Virtual · Est. 2009"

### 3. SECTION A — HERO
- `<section>` id="hero", background var(--warm-white), padding 80px 24px 72px
- Inner: max-width 800px, margin 0 auto, text-align center
- Eyebrow: "Virtual Bookkeeping · Boulder City, NV · Serving Nevada & California"
- H1: "Virtual Bookkeeping & Payroll Services for Small Business"
- Subheading: `<p class="hero-speakable">` — Lora italic, font-size 22px, color var(--gold), margin 20px 0 — "Making sense out of chaos — 100% online, 100% personal."
- Body: "Hharpp Business Services is your outsourced CFO — providing virtual bookkeeping, payroll, QuickBooks setup, and cash flow management for small businesses across Nevada and California. We work entirely online so your books stay clean no matter where you're located. Relationship-first. No call centers. No cookie-cutter packages."
- CTA row: primary button "Book your free consultation" → /contact/ | secondary link "See our services →" → #services — display flex, gap 16px, justify-content center, margin-top 32px, flex-wrap wrap
- Credentials strip: `<div>` — "Certified Public Bookkeeper (CPB) · QuickBooks Certified Advanced Pro-Advisor · SHRM Member · AIPB Member · Est. 2009" — font-sans 11px, color var(--mid-grey), margin-top 28px, letter-spacing 0.02em
- Trust stats: 4-column flex row — for each stat a `<div>` with the number in font-serif font-weight 700 font-size 32px color var(--navy) and label in font-sans 12px color var(--mid-grey) — data: "16+" Years in business | "30+" Years experience | "NV & CA" States served | "100%" Virtual delivery — add border-right 0.5px solid rgba(0,0,0,0.1) between items, gap 0, padding 0 32px on each item, centered text, margin-top 40px, padding-top 32px, border-top 0.5px solid rgba(0,0,0,0.08)

### 4. SECTION B — QUIZ WIDGET
- `<section>` id="quiz", background var(--warm-white), padding 0 24px 64px
- Center a `<div class="quiz-container">` max-width 560px, margin 0 auto
- Border: 0.5px solid rgba(184,150,12,0.3), border-radius 14px, background white, overflow hidden
- Quiz header: background var(--gold-lt), padding 16px 24px, border-bottom 0.5px solid rgba(184,150,12,0.2)
  - Eyebrow: "Quick service finder"
  - Title: font-serif 600 16px navy "What does your business need most right now?"
- Progress bar: 3 dots (divs), height 3px, flex row, gap 4px, padding 12px 24px 0
  - Active dot: background var(--navy)
  - Done dot: background var(--gold)
  - Inactive dot: background rgba(0,0,0,0.1)
- 3 question panels (only one visible at a time via display:none/block):
  Each panel: padding 20px 24px
  - Question label: "Question N of 3" font-sans 11px mid-grey
  - Question text: font-serif 600 17px navy, margin 6px 0 18px
  - Options: vertical stack of buttons, each with a radio circle (16px, border 1.5px), label (font-sans 13px 500 charcoal), sub-label (font-sans 11px mid-grey), border 0.5px, border-radius 8px, padding 11px 14px, cursor pointer, width 100%, text-align left — hover: border-color var(--gold), background var(--gold-lt) — selected: border-color var(--navy), background var(--navy-lt)
  - Use EXACT question text, option labels, and option sub-labels from content.json quiz.questions
- Navigation row: display flex, justify-content space-between, padding 4px 24px 20px
  - Back button: transparent, no border, font-sans 12px mid-grey (hidden on step 1)
  - Next button: primary button style but opacity 0.4 when no selection made, opacity 1 when option selected — text "Next →" on steps 1-2, "See my match →" on step 3
- Result panel (hidden until step 3 complete): padding 24px
  - Eyebrow: "Your Hharpp match"
  - Result title: font-serif 600 18px navy (populated by JS from content.json quiz.results)
  - Result body: font-sans 14px mid-grey line-height 1.6 (populated by JS)
  - Service chips: navy pills row (populated by JS)
  - CTA: gold button "Book your free consultation" → /contact/ | "Learn more" underline link → #services
  - Restart: small outline button "Start over" — transparent, border 0.5px solid rgba(0,0,0,0.2), font-sans 11px mid-grey, margin-top 12px, display block, margin 12px auto 0

**Quiz JavaScript routing logic** (implement exactly):
```
function getResult(q1, q2, q3) {
  if (q2 === 'construction') return 'construction';
  if (q1 === 'behind' || q1 === 'messy') return 'catchup';
  if (q1 === 'starting') return 'newbiz';
  if (q3 === 'payroll') return 'payroll';
  if (q3 === 'cashflow') return 'cashflow';
  if (q3 === 'quickbooks') return 'quickbooks';
  return 'fullservice';
}
```
All result data (title, body, services array) comes from the RESULTS object
which must be hardcoded from content.json quiz.results — all 7 states.

### 5. SECTION C — SERVICES GRID
- `<section>` id="services", background white, padding 80px 24px
- Inner: max-width 1200px, margin 0 auto
- Eyebrow + H2 + intro paragraph (from content.json)
- 7 service cards in CSS grid: grid-template-columns repeat(auto-fill, minmax(300px, 1fr)), gap 20px, margin-top 40px
- Each card (from content.json services array):
  - H3: service name (font-serif 400 20px navy)
  - Body: service description (font-sans 14px mid-grey line-height 1.6)
  - Link: "→ Learn more" → service.url (gold secondary link style)
- Card hover: border-color var(--gold-border), transition 0.15s

### 6. SECTION D — CONSTRUCTION CALLOUT
- `<section>` id="construction", background var(--navy), padding 80px 24px
- Inner: max-width 1000px, margin 0 auto
- Eyebrow (gold): construction.eyebrow from content.json
- H2 (white, font-serif 600 32px): construction.h2
- Two paragraphs (white 85% opacity, font-sans 16px line-height 1.7): construction.para1 and construction.para2
- 2-column unordered list of construction.services — white 85% opacity, font-sans 14px, gold bullet dots (2px • character or CSS ::before)
- CTA button: "Learn about construction accounting →" → /construction-accounting/ — transparent background, border 1.5px solid var(--gold), color var(--gold), padding 11px 24px, border-radius 6px, font-sans 600 13px, hover background rgba(184,150,12,0.1), margin-top 32px, display inline-block

### 7. SECTION E — WHY HHARPP
- `<section>` id="why", background var(--warm-white), padding 80px 24px
- Eyebrow + H2 from spec
- 2×2 grid of differentiator cards (from content.json differentiators array):
  - Card: white bg, left border 3px solid var(--gold), border-radius 0 10px 10px 0, padding 24px, box-shadow none
  - Card title: font-sans 600 15px var(--navy), margin-bottom 8px
  - Card body: font-sans 14px mid-grey line-height 1.6
- Grid: grid-template-columns 1fr 1fr on desktop, 1fr on mobile

### 8. SECTION F — TESTIMONIALS
- `<section>` id="testimonials", background var(--navy-lt), padding 80px 24px
- Eyebrow + H2 from spec
- 2×2 grid of testimonial cards (from content.json testimonials array):
  - Quote: `<blockquote>` font-serif italic 17px gold line-height 1.5, before content: open-quote character in gold
  - Attribution: font-sans 13px mid-grey margin-top 12px — "— author.author, author.company"
  - Card: white bg, border-left 3px solid var(--gold), border-radius 0 12px 12px 0, padding 24px 28px
- Social proof strip below grid: font-sans 12px mid-grey text-align center margin-top 32px — company.social_proof from content.json

### 9. SECTION G — FAQ
- `<section>` id="faq", background white, padding 80px 24px
- Eyebrow + H2 from spec
- 6 FAQ accordions (from content.json faqs array):
  Each accordion:
  - `<div class="faq-item">` with border-bottom 0.5px solid rgba(0,0,0,0.08)
  - Button trigger: display flex, justify-content space-between, align-items center, width 100%, background none, border none, padding 20px 0, cursor pointer, text-align left
    - Question text: font-sans 600 15px charcoal (left)
    - Icon: "+" when closed, "−" when open, font-sans 20px gold (right)
  - Answer panel: hidden by default, max-height 0, overflow hidden, transition max-height 0.3s ease
    When open: max-height 500px
    - Voice answer sentence: `<p class="faq-speakable-N">` (N = 1-6) — font-sans 15px navy font-weight 500, margin-bottom 12px — use faq.voice_answer
    - Full answer: `<p>` font-sans 14px mid-grey line-height 1.7 — use faq.full_answer
    - Padding: 0 0 20px 0
  - Only one accordion open at a time (JS: close others when opening one)
- "See all FAQs and resources →" gold secondary link → /faq/, margin-top 32px, display block, text-align center

### 10. SECTION H — SERVICE AREA
- `<section>` id="service-area", background var(--warm-white), padding 64px 24px
- Eyebrow + H2 from spec
- Body paragraph about Boulder City base + virtual nationwide reach
- Chips row: flex wrap gap 8px margin-top 24px — each chip a gold pill from content.json service_area_chips

### 11. SECTION I — ABOUT PREVIEW
- `<section>` id="about-preview", background white, padding 80px 24px
- 2-column layout on desktop (1-col on mobile): grid-template-columns 380px 1fr, gap 56px, align-items center
- LEFT: photo placeholder `<div>` — width 100%, aspect-ratio 4/5, background var(--navy-lt), border 2px solid var(--gold-border), border-radius 12px, display flex, align-items center, justify-content center — inner text: "[HEATHER HEADSHOT]" font-sans 13px mid-grey
- RIGHT:
  - Eyebrow + H2 from spec
  - Bio paragraph from content.json heather_bio
  - Credentials chips: flex wrap gap 8px margin-top 20px — gold pills from content.json credentials array (use credential.name only, shorten to: CPB · CMA (retired) · MBA · QuickBooks Advanced Pro-Advisor · SHRM · AIPB)
  - Link "Read Heather's full story →" → /about/ — gold secondary link, display block, margin-top 20px

### 12. SECTION J — LEAD MAGNET
- `<section>` id="lead-magnet", background var(--gold-lt), padding 64px 24px, border-top 0.5px solid rgba(184,150,12,0.2), border-bottom 0.5px solid rgba(184,150,12,0.2)
- 2-column grid on desktop (1-col on mobile): max-width 900px margin 0 auto, gap 48px, align-items center
- LEFT column:
  - Eyebrow (gold): lead_magnet.eyebrow
  - H2 (navy, font-serif 600 24px): lead_magnet.h2
  - Description: lead_magnet.description font-sans 14px mid-grey margin 12px 0 16px
  - 3 bullet points from lead_magnet.bullets — each with a gold checkmark (✓) before the text, font-sans 13px charcoal, line-height 1.8
- RIGHT column:
  - White card (border-radius 12px, padding 28px, background white, border 0.5px solid rgba(184,150,12,0.2)):
    - Label: "Get the free checklist" font-sans 600 14px navy, margin-bottom 16px
    - Name input: width 100%, margin-bottom 12px, font-sans 14px, padding 10px 14px, border 0.5px solid rgba(0,0,0,0.15), border-radius 6px
    - Email input: same styles
    - Submit button: gold CTA button full width — "Send me the checklist"
    - Note below: font-sans 11px mid-grey text-align center margin-top 10px — "No spam. Unsubscribe anytime."
  - `<form action="#" method="post">` — connect to email platform before launch

### 13. SECTION K — CTA BAND
- `<section>` id="cta", background var(--navy), padding 80px 24px, text-align center
- H2: font-serif italic 600 30px white line-height 1.25 — "Ready to make sense of your finances?"
- Subtext: font-sans 15px rgba(255,255,255,0.8) max-width 520px margin 16px auto 32px line-height 1.6 — "Your first consultation is free and completely without obligation. We'll learn about your business, review where your books stand, and tell you honestly whether Hharpp is the right fit for you."
- Gold CTA button: "Book your free consultation" → /contact/
- Contact line: font-sans 13px rgba(255,255,255,0.6) margin-top 20px — "Or call us at (702) 342-8844 · services@hharpp.com · Mon–Thu 8:30 AM–4:00 PM MT"

### 14. FOOTER
- `<footer>` background var(--navy), padding 56px 24px 32px
- Inner: max-width 1200px margin 0 auto
- 4-column grid (2-col on tablet, 1-col on mobile), gap 32px:
  COL 1:
    - "Hharpp Business Services" font-serif 600 18px white
    - "Making sense out of chaos." font-serif italic 14px gold, margin 6px 0 12px
    - Address/contact: font-sans 12px rgba(255,255,255,0.55) line-height 1.8 — "Boulder City, NV" / "services@hharpp.com" / "(702) 342-8844"
  COL 2 — Services:
    - Label: "Services" font-sans 600 12px rgba(255,255,255,0.4) uppercase letter-spacing 0.08em, margin-bottom 12px
    - Links from content.json services array — each service.name → service.url, font-sans 13px rgba(255,255,255,0.7), display block, margin-bottom 8px, text-decoration none, hover rgba(255,255,255,1)
  COL 3 — Company:
    - Label: "Company" same style
    - Links: About Heather → /about/ | FAQ / Resources → /faq/ | Contact Us → /contact/ | Book a Consultation → /contact/ | Privacy Policy → /privacy-policy/ | Terms of Service → /terms/
  COL 4 — Service Area:
    - Label: "Service area"
    - List of areas from content.json service_area_chips — font-sans 12px rgba(255,255,255,0.55), display block, line-height 1.9
- Bottom bar: border-top 0.5px solid rgba(255,255,255,0.12), margin-top 40px, padding-top 24px, display flex, justify-content space-between, align-items center, flex-wrap wrap, gap 8px
  - Left: "© 2026 Hharpp Business Services Inc · All rights reserved" font-sans 11px rgba(255,255,255,0.4)
  - Right: "Certified Public Bookkeeper · QuickBooks Advanced Pro-Advisor · Boulder City, Nevada" font-sans 11px rgba(255,255,255,0.4)

---

## Schema — 5 blocks, all in `<head>`

### Block 1 — LocalBusiness + AccountingService
```json
{
  "@context": "https://schema.org",
  "@type": ["LocalBusiness", "AccountingService"],
  "@id": "https://hharpp.com/#organization",
  "name": "Hharpp Business Services",
  "legalName": "Hharpp Business Services Inc",
  "description": "Hharpp Business Services provides virtual bookkeeping, payroll, QuickBooks setup and training, cash flow management, business consulting, and HR services for small businesses across Nevada and California. Specializing in construction accounting and job costing. Serving clients 100% online since 2009.",
  "url": "https://hharpp.com",
  "telephone": "+1-702-342-8844",
  "email": "services@hharpp.com",
  "foundingDate": "2009",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "1010 Industrial Road #166 Canary Way",
    "addressLocality": "Boulder City",
    "addressRegion": "NV",
    "postalCode": "89005",
    "addressCountry": "US"
  },
  "geo": { "@type": "GeoCoordinates", "latitude": 35.9788, "longitude": -114.8328 },
  "openingHoursSpecification": [{ "@type": "OpeningHoursSpecification", "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday"], "opens": "08:30", "closes": "16:00" }],
  "areaServed": [
    { "@type": "State", "name": "Nevada" },
    { "@type": "State", "name": "California" },
    { "@type": "AdministrativeArea", "name": "United States" }
  ],
  "serviceType": ["Bookkeeping","Payroll Services","QuickBooks Setup and Training","Cash Flow Management","Business Consulting","HR Services","Construction Accounting","Cloud Accounting","Virtual CFO Services"],
  "priceRange": "$$",
  "sameAs": [
    "https://www.alignable.com/henderson-nv/hharpp-accounting-services",
    "https://proadvisor.intuit.com/app/accountant/search?searchId=heather-potvin",
    "https://members.ghdcc.com/members/member/hharpp-business-services-inc-117",
    "https://www.bbb.org/us/ca/rancho-cucamonga/profile/accountant/hharpp-accounting-services-1126-89075592"
  ],
  "aggregateRating": { "@type": "AggregateRating", "ratingValue": "5", "reviewCount": "16", "bestRating": "5" }
}
```

### Block 2 — Person (Heather Potvin)
```json
{
  "@context": "https://schema.org",
  "@type": "Person",
  "@id": "https://hharpp.com/#heather-potvin",
  "name": "Heather Potvin",
  "jobTitle": "President, CFO, Certified Public Bookkeeper",
  "description": "Heather Potvin is the founder and President of Hharpp Business Services. A Certified Public Bookkeeper (CPB), retired Certified Management Accountant (CMA), and QuickBooks Certified Advanced Pro-Advisor with over 30 years of experience specializing in construction accounting and virtual CFO services for small businesses.",
  "url": "https://hharpp.com/about/",
  "worksFor": { "@id": "https://hharpp.com/#organization" },
  "hasCredential": [
    { "@type": "EducationalOccupationalCredential", "name": "Certified Public Bookkeeper (CPB)", "recognizedBy": { "@type": "Organization", "name": "American Institute of Professional Bookkeepers" }},
    { "@type": "EducationalOccupationalCredential", "name": "Certified Management Accountant (CMA)" },
    { "@type": "EducationalOccupationalCredential", "name": "QuickBooks Certified Advanced Pro-Advisor", "recognizedBy": { "@type": "Organization", "name": "Intuit" }},
    { "@type": "EducationalOccupationalCredential", "name": "Master of Business Administration (MBA)" }
  ],
  "memberOf": [
    { "@type": "Organization", "name": "Society for Human Resource Management (SHRM)" },
    { "@type": "Organization", "name": "American Institute of Professional Bookkeepers (AIPB)" }
  ],
  "sameAs": [
    "https://www.linkedin.com/company/hharpp-accounting-services",
    "https://www.alignable.com/henderson-nv/hharpp-accounting-services",
    "https://proadvisor.intuit.com/app/accountant/search?searchId=heather-potvin"
  ]
}
```

### Block 3 — WebSite + SearchAction
```json
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "@id": "https://hharpp.com/#website",
  "name": "Hharpp Business Services",
  "url": "https://hharpp.com",
  "publisher": { "@id": "https://hharpp.com/#organization" },
  "potentialAction": {
    "@type": "SearchAction",
    "target": { "@type": "EntryPoint", "urlTemplate": "https://hharpp.com/?s={search_term_string}" },
    "query-input": "required name=search_term_string"
  }
}
```

### Block 4 — WebPage + Speakable
```json
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "@id": "https://hharpp.com/#webpage",
  "name": "Virtual Bookkeeping & Payroll Services | Hharpp — Boulder City, NV",
  "url": "https://hharpp.com/",
  "speakable": {
    "@type": "SpeakableSpecification",
    "cssSelector": [".hero-speakable",".faq-speakable-1",".faq-speakable-2",".faq-speakable-3",".faq-speakable-4",".faq-speakable-5",".faq-speakable-6"]
  },
  "isPartOf": { "@id": "https://hharpp.com/#website" },
  "about": { "@id": "https://hharpp.com/#organization" },
  "author": { "@id": "https://hharpp.com/#heather-potvin" }
}
```

### Block 5 — FAQPage
All 6 questions and answers from content.json faqs array — use faq.question as "name" and faq.full_answer as "text" in acceptedAnswer.

---

## Responsive breakpoints

```css
/* Mobile first base styles for all elements above */

/* Tablet */
@media (min-width: 768px) {
  /* nav links visible */
  /* 2-col grids where specified */
  /* quiz max-width centered */
}

/* Desktop */
@media (min-width: 1280px) {
  /* 3-col service grid */
  /* 4-col footer grid */
  /* about section 2-col */
  /* trust stats horizontal */
}
```

---

## JavaScript — implement all behaviors

### Sticky nav scroll effect
On scroll > 10px: nav background becomes white with box-shadow 0 1px 12px rgba(0,0,0,0.08)
On scroll ≤ 10px: nav background white, no shadow

### FAQ accordions
- All panels closed by default
- Click question button: if panel is closed, open it (max-height 500px) and change icon to "−"
- If another panel is open, close it first
- Click open panel: close it, change icon back to "+"
- Smooth CSS transition on max-height

### Quiz widget
State object: `{ step: 1, answers: { q1: null, q2: null, q3: null } }`

selectOption(questionId, value):
- Store answer in state.answers
- Remove 'selected' class from all options in question
- Add 'selected' class to clicked option
- Enable next button (remove disabled/opacity)

nextStep():
- If no answer for current step: return (do nothing)
- If step < 3: hide current question panel, show next, update progress dots, show back button, reset next button state
- If step === 3: showResult()

prevStep():
- If step === 1: return
- Hide current, show previous, update progress dots, hide back button if step becomes 1, re-enable next button

showResult():
- Calculate result key using getResult() function above
- Look up result data from RESULTS object (hardcoded from content.json quiz.results — all 7 states)
- Populate: result title, result body, service chips (create pill elements dynamically)
- Hide question panels and nav row
- Show result panel
- Set all progress dots to 'done' state

restartQuiz():
- Reset state to { step: 1, answers: { q1: null, q2: null, q3: null } }
- Clear all 'selected' classes from all options
- Show question 1 panel, hide panels 2 and 3
- Hide result panel
- Show nav row
- Hide back button
- Reset all progress dots
- Disable next button

RESULTS object must contain all 7 keys: construction, catchup, newbiz, payroll, cashflow, quickbooks, fullservice — populated from content.json quiz.results

### Smooth scroll
All anchor links (href starting with #): addEventListener click, preventDefault, scrollIntoView behavior smooth

---

## Verification checklist — before saving the file

- [ ] All 6 FAQ questions match content.json faqs[].question exactly
- [ ] All 4 testimonials match content.json testimonials[] — quotes verbatim
- [ ] All 7 service names and descriptions match content.json services[]
- [ ] All 7 quiz result states are present in the RESULTS JS object
- [ ] Quiz routing function matches the routing_logic in content.json exactly
- [ ] Phone number (702) 342-8844 appears in: nav CTA, footer, CTA band
- [ ] Email services@hharpp.com appears in: footer, CTA band, meta description
- [ ] Address "Boulder City, NV" appears in: title, eyebrow, footer, schema
- [ ] All 5 schema blocks present in <head>
- [ ] .hero-speakable class on hero subheading paragraph
- [ ] .faq-speakable-1 through .faq-speakable-6 on voice_answer sentences
- [ ] No broken <img> tags — only styled div placeholders
- [ ] All internal links point to real paths, not #
- [ ] Lead magnet form action="#" (not empty)
- [ ] CSS custom properties defined in :root
- [ ] Google Fonts @import present in <style>
- [ ] File is valid HTML5 — opens without console errors in a browser

