# Portfolio — Toni Silván

> Personal portfolio website built with **Next.js**.  
> Showcases my profile, skills, and **in‑depth case studies** of selected projects:
> Spring Boot API, Gateway Guard, AI Mini‑App, and a UX/Data Visualization Dashboard.

---

## Status

Stable foundation; content and case studies evolving.

---

## Why this exists

Recruiters and engineers should be able to:
- Understand **who I am** in 30 seconds.
- Skim **selected projects** and see concrete outcomes, code, and architecture.
- Contact me easily, and verify my history (GitHub/LinkedIn/Medium).

---

## Tech Stack

- **Framework**: Next.js (App Router, Server Components)
- **Language**: TypeScript
- **Styling**: Tailwind CSS + shadcn/ui (accessible headless primitives)
- **Content**: MDX via Contentlayer (case studies & blog posts)
- **Animations**: Framer Motion
- **SEO**: Dynamic metadata per route, sitemap, robots.txt, OG image generation
- **Analytics**: Plausible (or Umami) — privacy‑friendly
- **Testing**: Vitest + React Testing Library; Playwright for e2e
- **CI/CD**: GitHub Actions; **Deployment** on Vercel

> Optional integrations (behind feature flags / env):  
> Upstash Redis (likes/counters), Resend or EmailJS (contact form).

---

## Architecture (high‑level)

Browser
│
├── Next.js (App Router, RSC, Edge/Node runtimes)
│ ├─ Pages: Home / Projects / Project [slug] / About / Contact / CV
│ ├─ MDX content (Contentlayer) → Case studies, blog posts
│ ├─ API routes (optional): /api/contact → Resend/EmailJS
│ └─ OG image generation (dynamic)
│
├── Analytics (Plausible/Umami)
└── Optional KV (Upstash) for simple counters/likes

yaml
Copy
Edit

---

## Project Structure

portfolio/
├─ app/ # Next.js App Router
│ ├─ (site)/ # Route group for main site
│ │ ├─ page.tsx # Home
│ │ ├─ about/page.tsx
│ │ ├─ projects/page.tsx
│ │ ├─ projects/[slug]/page.tsx # MDX-driven case study
│ │ ├─ contact/page.tsx
│ │ └─ cv/page.tsx
│ └─ api/
│ └─ contact/route.ts # optional (Resend/EmailJS)
├─ components/ # UI components (shadcn/ui, custom)
├─ content/ # MDX content
│ ├─ projects/ # Case studies (.mdx)
│ └─ blog/ # Blog posts (.mdx, optional)
├─ lib/ # utils (seo, content, formatting)
├─ public/ # static assets
├─ styles/ # globals.css, tailwind
├─ contentlayer.config.ts
├─ next.config.mjs
├─ package.json
└─ tsconfig.json

yaml
Copy
Edit

---

## Case Studies (content model)

Each project is an MDX file under `content/projects/*.mdx` with front‑matter like:

```md
---
title: "Gateway Guard — Security & Orchestration with Spring Cloud Gateway"
slug: "gateway-guard"
date: "2025-08-25"
summary: "Production-ready filters, runtime config, observability, and an admin UI."
role: "Technical Lead / IC"
tech: ["Spring Boot", "Spring Cloud Gateway", "Redis", "Next.js", "Docker"]
repoUrl: "https://github.com/tonisilvan/gateway-guard"
demoUrl: "https://guard.toni.dev"
impact:
  - "Reduced incident rate by X% after deploying rate limiting & JWT claims checks"
  - "Sub-50ms p95 across N requests via caching & circuit breakers"
---

## Context & Problem
Brief context...

## My Role
What I owned…

## Architecture
Explain components, include a diagram image if needed.

## Key Technical Challenges → Solutions
1) …
2) …

## Results
Measured outcomes, performance, reliability, costs.

## Links
- Repo
- Live demo
The list page (/projects) is auto‑generated from Contentlayer; each [slug] renders its MDX.

Getting Started
Prerequisites
Node.js LTS (≥ 20)

npm (or pnpm/yarn)

Installation
bash
Copy
Edit
git clone https://github.com/tonisilvan/portfolio.git
cd portfolio
npm install
Environment
Create .env.local:

dotenv
Copy
Edit
# required
NEXT_PUBLIC_SITE_URL=https://your-domain.tld

# analytics (choose one)
NEXT_PUBLIC_PLAUSIBLE_DOMAIN=your-domain.tld
# or
NEXT_PUBLIC_UMAMI_WEBSITE_ID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

# contact (optional)
RESEND_API_KEY=your_resend_key
EMAILJS_PUBLIC_KEY=your_emailjs_public
EMAILJS_SERVICE_ID=service_xxx
EMAILJS_TEMPLATE_ID=template_xxx

# kv (optional)
UPSTASH_REDIS_REST_URL=https://eu1-x.upstash.io/...
UPSTASH_REDIS_REST_TOKEN=xxxx
You can deploy without any optional keys; the site will just hide those features.

Run locally
bash
Copy
Edit
npm run dev
# open http://localhost:3000
Production build
bash
Copy
Edit
npm run build
npm run start
Scripts
dev — Start dev server

build — Production build

start — Run production server locally

lint — ESLint

typecheck — TypeScript type checks

test — Unit/integration tests (Vitest + RTL)

test:e2e — End‑to‑end tests (Playwright)

format — Prettier

Quality Gates
ESLint with recommended + react + ts + jsx‑a11y rules

Prettier for formatting

Type safety: strict TypeScript

Testing:

Vitest: component + lib tests

RTL: user‑level component tests

Playwright: critical user flows (home → projects → case study → contact)

CI (GitHub Actions):

Install, lint, typecheck, unit tests

Build

(optional) run Playwright on PRs

SEO & Performance
Per‑route metadata and canonical URLs

Open Graph image generation for projects

robots.txt and sitemap.xml

Image optimization; font loading strategy

Lighthouse targets: PWA (optional), Performance ≥ 90, A11y ≥ 95, SEO ≥ 95

Accessibility (A11y) Checklist
Color contrast validated

Keyboard navigation (focus rings, skip links)

Landmarks and proper headings

Forms with labels/aria‑describedby

Motion‑reduced fallbacks (prefers-reduced-motion)

Deployment
This project is designed for Vercel:

Push to main → auto‑build and deploy

Configure environment variables in Vercel

Set NEXT_PUBLIC_SITE_URL to your production URL

Add a custom domain and enable Edge cache if desired

Can also be hosted on other platforms; adjust next.config.mjs as needed.

Project Index (linked from the portfolio)
Spring Boot API — Secure API with JWT, DB, and external integrations.

Repo: https://github.com/tonisilvan/spring-boot-api (public)

Gateway Guard — Security & orchestration with Spring Cloud Gateway.

Repo: https://github.com/tonisilvan/gateway-guard (public)

AI Mini‑App — Small experimental AI app (prompting, guardrails, costs).

Repo: https://github.com/tonisilvan/ai-miniapp (public)

UX Dashboard — Interactive data visualization with filters and states.

Repo: https://github.com/tonisilvan/ux-dashboard (public)

Each project has its own README + diagrams; the portfolio hosts the case study.

Contributing
This is a personal site; issues and PRs are welcome for small improvements.
For substantial changes, please open an issue first.

Roadmap
 Publish first two full case studies (Spring API, Gateway Guard)

 Add dynamic OG images per project

 Wire contact API (Resend) with spam protection

 Add optional “like/counter” via Upstash Redis

 Publish blog section (optional)

 e2e tests for contact flow

FAQ
Why Contentlayer + MDX?
Reliable typed content, fast dev experience, and flexible rendering (code blocks, diagrams, components).

Why shadcn/ui?
Accessible, composable primitives that fit Tailwind without heavy CSS overrides.

Why not put project code inside this repo?
Separation of concerns: the portfolio stays fast and focused on storytelling; each project evolves independently.

License
MIT © Toni Silván
