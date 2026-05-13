# Presidential Assassination Attempts Explorer

A searchable historical archive of U.S. presidential assassination attempts, plots, and security incidents, built for researchers, students, journalists, and history readers.

It uses React 19, TypeScript, TanStack Start, TanStack Router, Vite, Tailwind CSS, Leaflet, Recharts, and an OpenAI-backed chat assistant to turn a structured dataset into an editorial web experience.

Use it to filter events, compare eras, inspect locations on a map, and read confidence-labeled records from 1835 to the present.

This is a dataset-driven web app with SEO-friendly routes, an interactive timeline, charts, person profiles, and AI-assisted historical Q&A.

## Live Demo
- Production: https://assassination.aisuretech.com

<!-- Use absolute production URLs for README images (https://...), not relative paths. -->
![Presidential Assassination Attempts Explorer preview](https://assassination.aisuretech.com/og-image.png)

## Why This Project Is Discoverable on GitHub
- Uses high-intent search terms such as U.S. presidential history, assassination attempts, political violence, and historical archive.
- Ships with indexable routes for events, timeline, map, insights, people, FAQ, and AI chat.
- Includes structured metadata, canonical URLs, Open Graph tags, Twitter cards, and an XML sitemap for SEO.
- Combines a clearly scoped historical dataset with modern React, TanStack Start, and TypeScript tooling.

## Table of Contents
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Environment Variables](#environment-variables)
- [Architecture](#architecture)
- [Learning Modules](#learning-modules)
- [Deployment](#deployment)
- [SEO and Performance](#seo-and-performance)
- [Screenshots](#screenshots)
- [Use Cases](#use-cases)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [FAQ](#faq)
- [Suggested GitHub Topics](#suggested-github-topics)
- [Links](#links)
- [License](#license)

## Features

### For Learners
- Search a curated archive of presidential assassination attempts, plots, threats, and related incidents from 1835 to the present.
- Explore a chronological timeline that groups events by era and highlights outcome status.
- Browse an interactive map to see where incidents occurred and how they cluster geographically.
- Ask Dr. Claire Whitmore natural-language questions about the archive, comparisons, and historical context.

### For Developers
- Build on a TanStack Start route-based architecture with shared data helpers in `src/lib`.
- Filter the archive by role, outcome, method, era, confidence, and keyword search using URL-backed state.
- Stream AI chat responses from a single server endpoint at `POST /api/chat` with OpenAI.
- Benefit from SEO metadata, JSON-LD on key pages, and a sitemap-friendly information architecture.

## Tech Stack
- Frontend: TanStack Start, React 19, TypeScript, TanStack Router, Tailwind CSS v4, Lucide React, Recharts, Leaflet, React Markdown.
- Runtime/Platform: Bun, Vite, Nitro, Vercel-ready deployment, with Cloudflare-compatible server entry support.
- Analytics and Monitoring: Google Analytics 4 via `gtag`, plus server-side error logging for the AI route.
- Testing: ESLint, TypeScript, and production build validation with `bun run build`.
- PWA: Web app manifest in `public/manifest.json` with standalone app icons and install metadata.

## Quick Start

### Prerequisites
- Bun 1.x
- An OpenAI API key for the chat endpoint if you want to use `/chat` locally

### Install and Run
```bash
bun install
bun run dev
```

Open the local Vite URL shown in the terminal, usually http://localhost:5173

### Build and Validate
```bash
bun run build
bun run lint
```

## Project Structure
```text
.
|-- docs/
|   |-- assets-checklist.md
|   |-- claire.md
|   |-- image-generation-checklist.md
|   |-- README.md
|-- public/
|   |-- manifest.json
|   |-- og-image.png
|   |-- screenshots/
|-- src/
|   |-- components/
|   |   |-- site/
|   |   |-- ui/
|   |-- data/
|   |-- lib/
|   |-- routes/
|   |-- types/
|-- bun.lockb
|-- package.json
|-- tsconfig.json
|-- vercel.json
|-- vite.config.ts
|-- wrangler.jsonc
```

## Environment Variables
Create a .env file in the project root:

```env
OPENAI_API_KEY=your_openai_api_key
OPENAI_MODEL=gpt-4o-mini
```

## Architecture
The app is organized as a route-first TanStack Start site with shared dataset helpers, static public assets, and one streaming AI endpoint.

1. Route modules in `src/routes` render the homepage, explorer, timeline, map, insights, people pages, and legal pages.
2. Shared data loaders in `src/lib` read the JSON datasets and expose filtering, lookup, statistics, and AI summary helpers.
3. The Explore, Timeline, Map, and Insights pages present the archive in different formats while reusing the same records.
4. The `/api/chat` server route validates messages, injects dataset context, and streams OpenAI completions as SSE.
5. SEO metadata, canonical URLs, OG images, JSON-LD, and sitemap routes make the site easy to share and index.

```text
Browser
  -> TanStack Start route
  -> shared dataset helpers in src/lib
  -> event/person JSON data in src/data
  -> UI components in src/components
  -> optional POST /api/chat
  -> OpenAI streaming response
```

## Learning Modules
- Event discovery and keyword search across a historically scoped archive.
- Timeline reading and era-based pattern recognition.
- Geographic analysis with map-based incident placement.
- AI-assisted historical Q&A grounded in curated dataset summaries.

## Deployment
Recommended deployment target: Vercel

```bash
bun install
NITRO_PRESET=vercel bun run build
vercel deploy
```

Production URL:
- https://assassination.aisuretech.com

## SEO and Performance
- Route-level titles, descriptions, canonical links, and Open Graph tags support search and social sharing.
- The root layout includes Twitter metadata, structured social previews, and Google Analytics 4.
- An XML sitemap and sitemap page help search engines discover the archive.
- Dataset-driven pages keep content readable, indexable, and easy to crawl.
- The map view is lazy-loaded so the main experience stays lighter on first paint.
- Static assets in `public/` keep images and icons fast to serve and cache.

## Screenshots
<!-- Use absolute production URLs for all screenshot images (https://...), not ./assets paths. -->

| Feature | Preview |
|--------|--------|
| Home hero | ![](https://assassination.aisuretech.com/home-hero.jpg) |
| Dr. Claire Whitmore | ![](https://assassination.aisuretech.com/claire-hero.jpg) |

## Use Cases
- Academic research into U.S. presidential security and political violence.
- Classroom teaching for modern American history, media studies, and civic education.
- Journalistic background research for timelines, context, and source cross-checking.
- Product and UX reference for route-based archives, maps, charts, and AI-assisted search.

## Roadmap
- [ ] Expand source annotations for lower-confidence entries.
- [ ] Add export options for filtered event lists.
- [ ] Add side-by-side comparison tools for two events or people.
- [ ] Add richer context panels for map, timeline, and people pages.

## Contributing
Contributions are welcome.

1. Fork the repository
2. Create a feature branch: git checkout -b feature/your-feature
3. Commit your changes
4. Push to your branch
5. Open a pull request

## FAQ

### What kind of project is this?
It is a data-driven historical archive of U.S. presidential assassination attempts, plots, threats, and related security incidents. The site is designed for research, teaching, and public reference, not entertainment.

### Is the archive complete?
No. It is a curated dataset with documented coverage from 1835 to the present, but it is not a claim to capture every possible rumor, allegation, or obscure historical mention.

### Do I need an OpenAI key to use the site?
No for browsing, search, and reading the archive. Yes if you want the `/chat` endpoint to work locally, because the AI assistant depends on `OPENAI_API_KEY`.

### Is there a general backend API?
Not really. The app has one custom application endpoint at `POST /api/chat`, plus sitemap generation. The rest of the site is route-driven front end and shared data helpers.

## Suggested GitHub Topics
Add these in repository settings for discoverability:
- us-history
- historical-archive
- tanstack-start
- react
- typescript
- vite
- leaflet
- openai

## Links
- GitHub Organization: https://github.com/aisuretech/
- Website: https://assassination.aisuretech.com
- Contact: info@AISureTech.com

## License
Proprietary
