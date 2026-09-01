# Mayled — LED Display Platform

**Full-stack web platform for an LED display manufacturer** — a bilingual marketing site, a database-driven admin CMS, and an interactive **3-step configurator** where a customer places a virtual LED screen onto a real façade photo and gets an instant price estimate.

🔗 **Live:** [mayled.com.tr](https://mayled.com.tr) · Production, used by a real business · 🇹🇷 / 🇬🇧

> This is a **showcase repository** — it presents the product, architecture, and my role. The source code is kept private because this is a live commercial project. A live demo is available at the link above.

![Configurator](docs/configurator.jpg)
<sub>The signature feature: pick a screen type & size, drag/resize a virtual LED screen onto a façade photo, and get an instant price range + quote.</sub>

---

## What it does

Mayled sells LED displays. The platform turns a static brochure site into a self-serve sales tool:

- **Interactive configurator** — a guided 3-step flow (screen type & dimensions → visual placement on a real façade photo with a draggable/resizable overlay → instant price range + lead capture). Built with a pure CSS + DOM overlay so it stays light on cheap shared hosting.
- **Admin CMS** — the owner manages *everything* from a panel: products, references/case studies, trusted-client logos, software downloads, FAQ, homepage content, and per-module on/off toggles. No developer needed for day-to-day content.
- **Bilingual (TR/EN)** with fully localized URLs (`/urunler` ↔ `/products`).
- **Lead pipeline** — configurator and contact forms create leads, with email notifications.
- **Fully responsive** — verified across every iPhone width (320–430px) and large-font/zoom settings.

## Highlights

- 🎛️ **Real-time visual configurator** — DOM/CSS overlay, aspect-ratio lock, ruler & technical view, "ask an expert" hand-off.
- 🗄️ **Everything is CMS-driven** — a key-value settings store + typed tables mean the whole site (copy, images, sections) is editable from the panel; changes revalidate the live pages on save.
- 🔒 **Secure by design** — secrets never touch the repo; auth via Auth.js v5 (bcrypt + JWT).
- ⚡ **Tuned for cheap shared hosting** — self-hosted fonts (no third-party fetch at build), browser-side image compression on upload, ISR caching, and a deploy pipeline hardened against the host's constraints.

## Tech stack

| Layer | Technologies |
|---|---|
| **Framework** | Next.js 15 (App Router, standalone), React 19, TypeScript |
| **Styling** | Tailwind CSS, self-hosted fonts |
| **Data** | MySQL, Drizzle ORM (mysql2) |
| **Auth** | Auth.js v5 (Credentials + bcrypt, JWT sessions) |
| **State / Forms** | Zustand, React Hook Form, Zod |
| **i18n** | next-intl (TR/EN, localized pathnames) |
| **Email** | Resend + Nodemailer + React Email |
| **Testing** | Playwright (e2e), Vitest |
| **Deploy** | Hostinger (CloudLinux / Passenger), GitHub → auto build & deploy |

## Architecture notes

- **Server Components + Server Actions** for data flow; the public site is statically generated with ISR and revalidated on admin edits.
- **Config-as-data**: a `site_settings` key-value store lets non-technical users edit content that would normally be hard-coded.
- **Resilient deploys** on constrained shared hosting: runtime env loading that's independent of the deploy directory depth, self-hosted fonts to remove a build-time network dependency, and canonical-URL auth config.

## Screenshots

| Home | Products | Case studies |
|---|---|---|
| ![Home](docs/home.jpg) | ![Products](docs/products.jpg) | ![References](docs/references.jpg) |

**Responsive (iPhone):**

| Home | Configurator | Contact |
|---|---|---|
| <img src="docs/mobile-home.jpg" width="240"> | <img src="docs/mobile-configurator.jpg" width="240"> | <img src="docs/mobile-contact.jpg" width="240"> |

## My role

Solo **full-stack** developer — design, frontend, backend, database schema, authentication, internationalization, the admin CMS, and the interactive configurator; plus the deployment pipeline and production troubleshooting on shared hosting. **~25,000 lines of TypeScript across ~240 files.**

---

<sub>Built with Next.js · TypeScript · MySQL · Deployed on Hostinger · © Mayled</sub>
