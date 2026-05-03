# CLAUDE.md — Asli Simsek Portfolio

## Project purpose

Personal PMM portfolio for Asli Simsek, built on the Angie Astro template. Goal: land senior PMM roles in B2B tech across Europe. Primary ICP is VP Marketing, Head of PMM, or hiring manager at a B2B SaaS or enterprise tech company. Secondary ICP is a recruiter screening candidates for those teams.

The site is a single-page scroll with anchor navigation. It is live at:
**https://prismatic-sorbet-59d9a3.netlify.app**

GitHub repo: `asliiasim/my-portfolio`
Local project path: `~/Desktop/"Vibe Coding - AI Agents"/angie-portfolio`

---

## Tech stack

- **Astro 5.5.3** — static site generator, component-based
- **Tailwind CSS v4** — via `@tailwindcss/vite` plugin (NOT `@astrojs/tailwind`, which is incompatible with Astro 5+)
- **GSAP** — used only in `Tools.astro` for ticker animation
- **Netlify** — auto-deploys on every push to `main`
- **GitHub** — `asliiasim/my-portfolio`, credentials cached via macOS Keychain

Run locally:
```bash
cd ~/Desktop/"Vibe Coding - AI Agents"/angie-portfolio
npm run dev        # starts on localhost:4321 (or next available port)
npm run build      # build check before pushing
```

Push to live:
```bash
git add .
git commit -m "describe what changed"
git push origin main
# Netlify deploys automatically in ~30 seconds
```

---

## File structure

```
src/
  pages/
    index.astro           # Page composition — imports and orders all components
  components/
    Header.astro          # Nav: logo, Work / About / Contact anchor links
    Hero.astro            # Above the fold: headline, subline, headshot, CTAs
    Tools.astro           # Two-row GSAP ticker: Companies & Partners / Media & Publisher Partners
    Service.astro         # Stats bar (156 MQLs, 85+, £1M+) + 4 competency cards
    Works.astro           # 4 portfolio cards in 2x2 grid (id="work")
    CaseStudies.astro     # Full case studies: CRA and Events (cases 1 and 2)
    SelectedProjects.astro # Shorter entries: B2B SaaS, PHD, Sales Enablement, GEO/AEO (cases 3-6)
    About.astro           # Bio, languages, "About This Portfolio" build proof (id="about")
    ToolsGrid.astro       # 4 grouped tool lists (no animation)
    Reviews.astro         # Oliver Happy pull-quote + "Impact by the numbers" evidence block
    CallToAction.astro    # Contact CTA (id="contact")
    Footer.astro          # Logo, nav links, social icons, copyright
  assets/
    headshot.png          # Asli's headshot — used in Hero
    case-vitrifi.svg      # Dark placeholder SVG: "65% email open rate"
    case-phd.svg          # Dark placeholder SVG: "+15% ROI improvement"
    [+ Angie template SVGs — do not modify]
  layouts/
    Layout.astro          # HTML shell, title, meta tags, SEO, FAQ schema, Person schema
  sample.ts               # author.name, author.nickname, linkedin, email — imported by Header/Footer
  styles/
    global.css            # Tailwind v4 import + Google Fonts
```

Page order in `index.astro`:
Header → Hero → Tools → Service → Works → CaseStudies → SelectedProjects → About → ToolsGrid → Reviews → CallToAction → Footer

---

## Design constraints — CRITICAL

**Do not change any of the following from the Angie template:**
- Colour palette (`--main-bg: #FEFFF0`, `--yellow: #FFDC58`, `--blue: #BAE6FF`, black)
- Fonts (Space Grotesk via Google Fonts)
- Spacing scale, border widths, shadow styles
- Any decorative SVG assets (logo-star, pink-star, red-star, arrow, string, idea, etc.)
- GSAP animation logic in Tools.astro
- The `Bars.astro` component
- The `Button.astro` component

**Only modify:** text content, image sources, links, section structure where specified.

---

## Content rules — CRITICAL

### Confidentiality
- **Never name Vitrifi** anywhere on the page. Use "B2B SaaS Telecoms Scale-up" or "B2B SaaS telecoms scale-up"
- **Named SMEs:** Do not use full names. Use job titles and seniority only. Example: "Canonical's Robotics Product Manager" not "Gabriel Aguiar Noury"
- **Battlecard content:** Reference as artifact type only. Do not reproduce verbatim
- **Screenshots not approved for external use:** Do not reference or display any internal GTM spreadsheet screenshots, Marketo brief screenshots, or any image not explicitly approved
- **Inference Snaps:** Do not mention as a case study — went live after December 2025 departure
- **Embedded World 2026:** Asli planned the GTM and briefed the team before leaving. Correct framing: "planned before leaving; delivered by successor team." Do NOT link to the Avnet/Advantech/Witekio webinar post as if Asli executed it

### Writing conventions
- No em dashes (—) or en dashes (–) in visible copy. Use periods, commas, or "to" for date ranges
- Short paragraphs: 1-3 sentences max per paragraph in case studies and bios
- No bullet points in narrative sections — use short separate paragraphs
- Dates written as "Oct 2025 to Present" not "Oct 2025–Present"
- Do not fabricate testimonial names or quotes
- Do not add stats, companies, or deliverables not verified in the session

### Employer framing
- Asli left Canonical in December 2025. Role was Oct 2025 to December 2025 (~3 months)
- Work planned but executed after departure should note "planned before leaving"
- Work delivered (whitepapers, webinar, SPS campaign, CES) is fully claimable
- The infotainment demo was built with Rightware and subsequently reused by Canonical at MWC 2026 — this is a positive proof point, not a risk

---

## Portfolio positioning

**USP:** Research-first PMM. Asli conducts primary buyer research (85+ structured interviews) before building positioning — this is the differentiator vs. other senior PMMs.

**Hero label:** RESEARCH-FIRST PMM

**ICP decision trigger (what gets a hiring manager to contact her):**
1. Live, verifiable case study evidence with real metrics and public links
2. Depth of enablement work (battlecards, DBR decks, partner portals) showing operational range
3. Technical fluency (GEO/AEO tooling, built this site, programmatic media automation)
4. Research-first approach demonstrating rigour unusual at this level

---

## Social proof rules

**Oliver Happy testimonial:** Verified LinkedIn recommendation, July 2025. Link to his LinkedIn: https://www.linkedin.com/in/oliverhappy/. Do not use a photo — pull-quote format only.

**"Impact by the numbers" evidence block:** 4 verifiable proof points replacing placeholder testimonials. Do not add placeholder cards or [Name TBC] slots.

**When new testimonials arrive:** Add them above Oliver's quote in the same pull-quote style. Attribution format: "Name, Title, Company" with a LinkedIn verification link if available. Anonymised peer quotes format: "Colleague, [Team], [Company]."

**References note:** "Additional references available on request" — keep this line. Asli is gathering references after an APM interview (week of 5 May 2026) and will add them then.

---

## SEO and AEO/GEO

Meta tags, Open Graph, Twitter Card, Person schema, and FAQ schema are all in `src/layouts/Layout.astro`.

**If you update the live URL (e.g. after adding a custom domain):** Update the `url` field in the Person schema JSON-LD in Layout.astro.

**FAQ schema covers:** research-first PMM definition, GEO/AEO definition, GTM measurement, sales enablement. Update these if the portfolio's positioning shifts.

**Target keywords:** "PMM portfolio", "product marketing manager B2B SaaS", "research-first PMM", "GTM strategy portfolio", "sales enablement portfolio"

---

## Artefacts & Links Memory Bank

All verified LinkedIn posts and public assets from Asli's Canonical tenure. Use these for portfolio updates, testimonial requests, and future case study evidence.

### CRA Whitepaper Campaign — Video Content (LinkedIn)
| Link | Description | Reactions | Portfolio use |
|------|-------------|-----------|---------------|
| https://www.linkedin.com/feed/update/urn:li:activity:7437780959732801537/ | Video V1: whitepaper launch (Yocto vs Ubuntu Core) | 42 | Add to CRA Live Links |
| https://www.linkedin.com/feed/update/urn:li:activity:7405250165994962945/ | Video V2: whitepaper launch | 51 | Add to CRA Live Links |
| https://www.linkedin.com/feed/update/urn:li:activity:7437046409050361857/ | Yocto vs Ubuntu Core content post | 75 | Supporting evidence |
| https://www.linkedin.com/feed/update/urn:li:activity:7437404452648669184/ | Real-time OS content post | — | Supporting evidence |
| https://www.linkedin.com/feed/update/urn:li:activity:7401234371053142018/ | Securing Ubuntu webinar promotion | — | Supporting evidence |

### CES 2026 (January 6 to 9, Las Vegas, Booth #10562)
| Link | Description | Reactions | Portfolio use |
|------|-------------|-----------|---------------|
| https://www.linkedin.com/feed/update/urn:li:activity:7414666128901328896/ | CES 2026 main recap post | 114 | Add to Events Live Links |
| https://www.linkedin.com/feed/update/urn:li:activity:7414261971434295296/ | CES 2026 second post | — | Supporting evidence |
| https://www.linkedin.com/feed/update/urn:li:activity:7414093406936981505/ | NVIDIA Rubin partnership announcement | 257 | Add to Events Live Links — strongest social proof |
| https://www.linkedin.com/feed/update/urn:li:activity:7402789896454635520/ | Infotainment development preview | — | Supporting evidence |

### SPS 2025 (November 25 to 27, Nuremberg, Booth #122 Hall 6)
| Link | Description | Reactions | Portfolio use |
|------|-------------|-----------|---------------|
| https://www.linkedin.com/feed/update/urn:li:activity:7401302086484652033/ | SPS 2025 event activation | 61 | Add to Events Live Links |

### MWC 2026 (infotainment reuse — positive proof point)
| Link | Description | Reactions | Portfolio use |
|------|-------------|-----------|---------------|
| https://www.linkedin.com/feed/update/urn:li:activity:7435011281646084098/ | MWC 2026: Canonical reuses infotainment demo (built with Rightware during Asli's tenure) | 69 | Add to Events Live Links — frame as "work outlasted the tenure" |
| https://www.linkedin.com/feed/update/urn:li:activity:7420023503443353601/ | Anbox Cloud automotive post | — | Supporting evidence |

### ctrlX AUTOMATION Week (November 18 to 20)
| Link | Description | Reactions | Portfolio use |
|------|-------------|-----------|---------------|
| https://www.linkedin.com/feed/update/urn:li:ugcPost:7388492753128652800/ | Bosch Rexroth Italia post (ctrlX) | 40 | Supporting evidence |
| https://www.linkedin.com/feed/update/urn:li:activity:7391631618219667456/ | Canonical ctrlX AUTOMATION Week post | 47 | Add to Events Live Links |

### Partner Announcements
| Link | Description | Reactions | Portfolio use |
|------|-------------|-----------|---------------|
| https://www.linkedin.com/feed/update/urn:li:activity:7401568953216679936/ | Qualcomm certification partnership | 163 | Add to Events Live Links |
| https://www.linkedin.com/feed/update/urn:li:activity:7414093406936981505/ | NVIDIA Rubin partnership | 257 | Add to Events Live Links (same as CES entry above) |

### ROSCon Singapore (November 27 to 29)
| Link | Description | Reactions | Portfolio use |
|------|-------------|-----------|---------------|
| https://canonical.com/blog/roscon-2025 | ROSCon 2025 recap (Canonical blog) | — | Already in Events Live Links |
| https://canonical.com/blog/extending-ros-noetic-support-with-esm-enabled-content-snaps | Extending ROS Noetic support with ESM | — | Supporting evidence |

### Planned Before Leaving — Do NOT claim as executed
These were planned by Asli before her December 2025 departure. Execution completed by successor team. Frame as "planned before leaving; delivered by successor team."
| Link | Description | Notes |
|------|-------------|-------|
| https://www.linkedin.com/feed/update/urn:li:activity:7447576757441908736/ | Avnet/Advantech/Witekio webinar (Embedded World 2026) | Do not link as if Asli executed it |
| https://www.linkedin.com/feed/update/urn:li:activity:7437547911405613056/ | Embedded World 2026 | Asli planned GTM; successor team delivered |
| https://ubuntu.com/engage/embedded-world-2026 | Embedded World 2026 landing page | Already in Events links with correct framing |
| https://ubuntu.com/engage/reducing-risk-for-embedded-devices | Avnet/Advantech/Witekio whitepaper | Already in Events links with correct framing |

### Public Blog Posts (fully claimable)
| Link | Description |
|------|-------------|
| https://canonical.com/blog/roscon-2025 | ROSCon 2025 |
| https://canonical.com/blog/canonical-at-ces-2026 | CES 2026 announcement |
| https://canonical.com/blog/future-of-infotainment-canonical-at-ces-2026 | CES 2026 infotainment |
| https://canonical.com/blog/canonical-qualcomm-dragonwing-iq9075 | Qualcomm Dragonwing partnership |

### Ubuntu Engage Assets (whitepapers and webinars)
| Link | Description |
|------|-------------|
| https://ubuntu.com/engage/cra-yocto-core | Yocto or Ubuntu Core? CTO comparison guide |
| https://ubuntu.com/engage/cra-regulations-for-ubuntu | Prepare Your Devices for the EU CRA |
| https://ubuntu.com/engage/securing-ubuntu-devices | Securing Ubuntu Deployments whitepaper |
| https://ubuntu.com/engage/webinar-securing-ubuntu-devices | Key Steps to Secure Ubuntu Deployments (webinar, Dec 11) |
| https://ubuntu.com/pro/devices | Ubuntu Pro for Devices (product page) |

---

## Known outstanding items (as of May 2026)

- [ ] Card images for CRA and Events cases: still using generic Ubuntu CDN images. Replace with screenshots of the actual campaign assets (whitepaper landing page for CRA; ROSCon post image for Events)
- [ ] LinkedIn video posts: add to CRA Live Links section (V1: activity-7437780959732801537 and V2: activity-7405250165994962945)
- [ ] Company logo strip: build a "Worked with" greyscale logo row (Canonical, NVIDIA, Qualcomm, Bosch Rexroth, Omnicom/PHD). Best placement: between ticker and stats/service section
- [ ] Additional testimonials: add after APM interview references are collected (week of 5 May 2026)
- [ ] Custom domain: buy domain, configure in Netlify Domain management, update Person schema URL
- [ ] High-scoring LinkedIn links: add to Events case Live Links (NVIDIA post 257 reactions, Qualcomm post 163 reactions, CES post 114 reactions, MWC infotainment reuse 69 reactions, ctrlX Canonical post 47 reactions)

---

## What NOT to do

- Do not run `npm init` or re-initialise the project
- Do not change `astro.config.mjs`, `tsconfig.json`, or `package.json` without a specific reason
- Do not install `@astrojs/tailwind` — it is incompatible with Astro 5+
- Do not modify decorative SVG files in `src/assets/`
- Do not push without running `npm run build` to check for errors first
- Do not commit sensitive files (tokens, `.env`)
- Do not use `git add -A` — add specific files or `src/` only
