# Z.AI MASTER PROMPT — MyPets Digital Library — Launch in <24h

## Context

You are working on the existing production project:

- Frontend: `nexflowx-hub/mypets-frontend`
- Backend: `nexflowx-hub/mypets-backend`
- Canonical editorial/data repository: `nexflowx-hub/mypets-data`
- Main public domain: `mypets.lat`
- Future secondary brand/domain: `facepets.org`

The immediate priority is the **MyPets Digital Library** connected to the campaign:

> **1 eBook = 1 kg de ração**
>
> Current base unit: **R$ 12,90 confirmed = 1 selected guide/eBook + MyPets commitment of 1 kg of feed.**

The existing campaign/payment flow already exists and MUST NOT be broken.

The current site already has:
- `/ajudar/ebooks`
- `/ebooks/[slug]`
- `/ebooks/colecao`
- receipt validation
- reward keys
- campaign tracking
- payment confirmation rules
- print button
- MyPets visual system
- Next.js App Router
- React 19
- Next 16
- Tailwind
- `react-markdown`
- Radix components
- existing SEO/robots/sitemap infrastructure

The data repository already contains the expanded launch guides, metadata, source registries, media registries, release manifests and frontend handoff documentation.

Do not redesign the business logic from scratch. **Evolve the existing application.**

---

# 1. Mission

Transform the current basic web eBook delivery into a premium **MyPets Digital Library**, visually rich and optimized for mobile, tablet and desktop.

It must feel like a modern digital book / magazine / learning reader rather than:
- a donation receipt;
- a plain Markdown page;
- a generic blog;
- a dashboard;
- or an old-fashioned PDF viewer.

The reader must combine:

- long-form editorial reading;
- page/chapter navigation;
- photographs;
- image galleries;
- comparison tables;
- cards;
- checklists;
- warnings;
- tips;
- embedded official videos;
- breed profile cards;
- source/reference panels;
- reading progress;
- resume reading;
- print/PDF output.

The same canonical content must support:
1. web reading;
2. public previews;
3. entitled premium reading;
4. print/PDF;
5. future SEO derivatives;
6. future safe FacePets conversational retrieval.

---

# 2. Absolute non-negotiable constraints

## Payment / entitlement

Do NOT break:
- `/ajudar/ebooks`
- `validateEbookReceipt`
- existing reward keys
- current payment confirmation
- current `receipt` access
- current tracking
- current campaign unit rules

Do not count:
- QR generated;
- checkout opened;
- payment started;

as a confirmed kg.

Only confirmed backend financial success unlocks entitlement.

## Historical slug compatibility

At minimum preserve:

```
filhote-primeiros-30-dias -> primeiros-30-dias
rotina-alimentacao -> alimentacao-bem-estar
```

Build a generic alias resolver so future aliases do not require route rewrites.

## Premium content leakage

Public pages must **never ship the full entitled content inside hidden DOM, JSON props, RSC payload or client bundle**.

A preview route receives only preview content.

An entitled reader receives full content only after validated access.

## Security

Do not execute arbitrary Markdown HTML.

Never render arbitrary:
- iframe;
- script;
- object;
- embed;
- raw HTML events.

All video/media embeds must resolve from the approved `media/registry.yaml`.

Allowlist domains and types.

## SEO

Index:
- `/biblioteca`
- `/biblioteca/[slug]`
- selected future public `/guias/...`
- breed public pages if enabled

Noindex:
- receipt URLs
- full entitled reader
- `/minha-biblioteca`
- account/private pages
- print entitlement endpoints

## Accessibility

Do not sacrifice accessibility for a fake “page turning” effect.

The primary mode is semantic HTML reading.

A visual “book mode” is optional enhancement and must never block:
- text selection;
- keyboard use;
- screen readers;
- print;
- mobile reading.

---

# 3. Canonical content architecture

Canonical repository:

`nexflowx-hub/mypets-data`

Source tree:

```
library/
  index.json
  manifest.yaml
  pt-BR/
    <guide-directory>/
      meta.yaml
      preview.md
      guide.md
      sources.yaml

media/
  registry.yaml

sources/
  registry.yaml

releases/
  <release-id>/
    manifest.yaml
```

The frontend must not manually rewrite these guides.

Implement an ingestion adapter.

---

# 4. Content ingestion strategy

## Fast launch implementation

Create a build-time sync script inside `mypets-frontend`.

Suggested structure:

```
scripts/
  sync-mypets-content.ts

src/
  content-generated/
    library-index.json
    media-registry.json
    source-registry.json
    guides/
      ...
```

Environment:

```
MYPETS_CONTENT_REPO=nexflowx-hub/mypets-data
MYPETS_CONTENT_REF=<PINNED_COMMIT_SHA_OR_TAG>
MYPETS_CONTENT_LOCALE=pt-BR
```

If a GitHub token becomes necessary, it must remain server/build only.

Never expose it as `NEXT_PUBLIC_*`.

## Sync validation

Fail the build if:

- manifest references missing guide;
- meta is missing;
- guide.md is missing;
- preview.md is missing;
- referenced media id does not exist;
- referenced source id does not exist;
- duplicate canonical slugs exist;
- legacy alias collides with another canonical slug;
- invalid URL/domain exists in media registry;
- required title/id/version fields are absent.

Generate a compact normalized JSON index.

---

# 5. Normalized TypeScript model

Create strong types with Zod validation.

Example conceptual model:

```ts
type LibraryGuide = {
  id: string;
  slug: string;
  legacySlugs: string[];
  title: string;
  subtitle: string;
  description: string;
  locale: string;
  version: string;
  status: string;
  readingMinutes: number;
  tags: string[];
  audience: string[];
  topics: string[];
  image?: string;
  access: "public" | "entitled";
  medicalRisk: "none" | "low" | "medium" | "high";
  childSafe: boolean;
  aiUse: "allowed" | "restricted" | "blocked";
  previewMarkdown: string;
  fullMarkdown?: string;
  sourceIds: string[];
};
```

Media model should support at minimum:

```ts
type LibraryMedia =
 | {
    id: string;
    type: "image";
    src: string;
    alt: string;
    caption?: string;
    credit?: string;
    license?: string;
    sourceUrl?: string;
   }
 | {
    id: string;
    type: "video-embed";
    provider: "youtube";
    embedUrl: string;
    title: string;
    publisher: string;
    sourcePage?: string;
   };
```

Do not embed remote objects directly without normalization.

---

# 6. Public routes to build

## /biblioteca

Purpose:
Premium catalog homepage.

Hero:
- “Biblioteca MyPets”
- collection positioning
- campaign relationship
- number of available guides
- visual shelf/collection
- button to campaign
- optional search

Sections:
1. featured guides
2. categories
3. “comece por aqui”
4. “mais lidos” only when real analytics exist — never invent
5. breed atlas entry point
6. how access works
7. quality/research note
8. campaign relationship

Cards should display:
- cover/photo
- title
- subtitle
- category
- reading time
- practical assets
- locked/unlocked state when known

Design language:
premium editorial, clean, warm, credible.

Do not make it look like a Shopify product grid.

## /biblioteca/[slug]

Public guide landing/preview.

Must contain:
- editorial hero;
- cover/media;
- title;
- subtitle;
- reading time;
- contents/table of contents;
- what the reader will learn;
- practical assets included;
- selected preview;
- references/research quality summary;
- related guides;
- campaign CTA.

CTA:
**“Garantir 1 kg e desbloquear este guia — R$ 12,90”**

Do not ship full guide.

## /biblioteca/[slug]/preview

Optional dedicated preview route.

Use only `preview.md`.

## /biblioteca/racas

Build this as a first-class “Atlas de Raças”.

Features:
- search;
- filters;
- alphabetical index;
- groups;
- size;
- energy;
- maintenance;
- apartment compatibility;
- heat sensitivity;
- child/family context;
- image cards.

Do not present filters as deterministic truth.

Use wording:
- tendency
- typical profile
- points to investigate

Every page must remind that individual variation matters.

## /biblioteca/racas/[breed-slug]

Breed detail.

Design:
- large real photo
- summary matrix
- origin/function
- energy
- exercise
- grooming
- training
- sociability context
- vocalization
- environment
- heat/cold
- health/welfare points
- “before choosing”
- “questions to ask”
- references
- related breeds

This page may later be generated from structured breed data.

---

# 7. Entitled routes

## /minha-biblioteca

Validate access.

Show all entitled guides.

Each card:
- progress
- last opened
- continue button
- print/download
- version
- completed checkmark

Receipt-based users without account:
- support current receipt query
- local progress fallback

Authenticated users:
- prepare integration for backend/Supabase progress

## /biblioteca/[slug]/ler

Canonical entitled reader.

Support:

```
/biblioteca/[slug]/ler?receipt=...
/biblioteca/[slug]/ler#section
```

Old:
`/ebooks/[slug]?receipt=...`

should redirect preserving receipt and alias.

Old:
`/ebooks/colecao?receipt=...`

should redirect to:
`/minha-biblioteca?receipt=...`

Keep old routes functional through redirects or compatibility wrappers.

---

# 8. Reader layout — desktop

Target experience:
Kindle + modern editorial magazine + lightweight learning platform.

Three conceptual columns:

### Left
Collapsible table of contents:
- section number
- section title
- completed indicator
- current section

### Center
Main reading column:
- max readable width approximately 700–780 px
- generous line height
- strong type hierarchy
- rich media
- semantic components

### Right
Optional contextual panel:
- reading progress
- bookmarks
- references
- “neste capítulo”
- related content

On medium widths, hide right panel first.

---

# 9. Reader layout — mobile

Mobile is critical.

Use:
- full-width clean reading area
- compact sticky top bar
- progress bar
- chapter title
- TOC drawer
- previous / next chapter
- bottom safe-area padding

Avoid:
- tiny multi-column text;
- forced page dimensions;
- horizontal overflow;
- hover-only controls.

Tables:
- responsive cards when necessary;
- horizontal scroll only when unavoidable.

---

# 10. Book / page-turn mode

The user wants an optional experience resembling a digital book.

Implement an optional button:

**“Modo livro”**

This is a presentation layer, not the data model.

Possible behavior:
- page-sized cards on desktop/tablet;
- smooth horizontal navigation;
- subtle page-turn or slide animation;
- keyboard arrows;
- swipe.

Do NOT:
- convert text to canvas;
- render each page as an image;
- use an inaccessible PDF iframe as primary reader;
- break responsive typography.

On mobile, default to continuous reader.

If the book mode becomes unstable or delays launch, ship it as progressive enhancement after the core reader.

---

# 11. Rich editorial block system

Canonical Markdown uses semantic callout conventions.

Build a parser/renderer for:

```
[!IMPORTANT]
[!WARNING]
[!TIP]
[!NOTE]
[!MEDIA]
```

Also support future rich directives, but do not require rewriting current content.

Render components:

### KeyPoint
Visually strong summary.

### Warning
Safety/red-flag block.

### VetBoundary
“General information, not diagnosis.”

### Tip
Practical quick action.

### Checklist
Interactive in web.
Printable checkbox in PDF.

### Table
Responsive.

### Figure
Image + caption + attribution.

### Gallery
2–6 responsive images.

### Video
Allowlisted embed.

### BreedCard
Structured summary.

### ComparisonMatrix
Energy / grooming / size etc.

### DoToday
Action box.

### Quiz/Reflection
Optional non-graded interactive question.

### SourceNote
Reference link.

---

# 12. Markdown rules

Support:
- h1–h4
- paragraph
- strong/emphasis
- ordered/unordered list
- task list
- table
- blockquote
- inline links
- horizontal rule
- anchors
- callouts

External links:
- `target="_blank"`
- `rel="noopener noreferrer"`

Do not accept arbitrary iframe.

A `[!MEDIA]` directive must identify a media registry id and render through the registry.

---

# 13. Media registry rendering

Read `media/registry.yaml`.

### Images

For managed/local images:
- Next/Image
- responsive sizes
- lazy loading except hero
- alt
- caption
- credit/attribution if needed

For Creative Commons:
- preserve author
- source
- license
- attribution

Prefer ingesting an approved copy into controlled storage/static assets rather than indefinite hotlinking.

### Video

Use official YouTube embeds only through allowlist.

Prefer privacy-enhanced embed host where feasible.

Lazy load:
- show thumbnail/card first
- load iframe after interaction or near viewport

Always show:
- title
- publisher
- “conteúdo externo” indication if useful
- accessible iframe title

---

# 14. Visual media density

Long guides must not become walls of text.

Target:
- one visual/editorial interruption every ~2–4 reading screens where meaningful;
- one strong table/checklist every few sections;
- images should teach or orient, not merely decorate.

For breed pages:
- at least one strong real photograph;
- ideally gallery of 2–4 licensed/approved photos over time.

For training:
- video demonstrations;
- step cards;
- progression diagrams.

For body language:
- illustrated/photo examples;
- “give space” visual callouts.

For nutrition:
- safe original diagrams;
- link/embed approved authoritative media where possible.

---

# 15. Image fallback strategy

If a content item lacks a ready licensed image:

1. use existing MyPets photography if semantically relevant;
2. use approved CC/public-domain registry;
3. use an original MyPets illustration generated/commissioned for that concept;
4. only then use neutral visual placeholder.

Never fabricate a photograph and present it as a real documented animal.

For breed representation, label generated art as illustration if ever used.

---

# 16. Reading progress

v1:
- localStorage keyed by:
  - release id
  - guide id
  - receipt hash/session id

Persist:
- last section
- percent
- completed sections
- checklist states
- bookmarks

Do not store payment secrets.

Production-compatible interface:

```ts
interface ReadingProgressStore {
 get(...)
 save(...)
}
```

Provide:
- local adapter now
- API/Supabase adapter seam later

---

# 17. Entitlement resolver

Create one resolver:

```ts
resolveGuideAccess({
 slug,
 receipt,
 user
})
```

Flow:
1. resolve canonical slug;
2. validate guide exists;
3. validate receipt/server entitlement;
4. map historical reward key aliases;
5. return allowed/denied;
6. never trust client boolean.

Keep this server-side.

---

# 18. Campaign integration

Reader should not become a payment funnel every screen.

Use discreet reminders:

At end of chapter:
> “Você está a ler um guia da campanha 1 eBook = 1 kg.”

At end of guide:
> “Este guia ajudou a colocar 1 kg em movimento. Quer escolher outro guia e garantir +1 kg?”

CTA:
- go back to `/ajudar/ebooks`
- preserve UTM content identifying reader and guide

Do not interrupt paragraphs with repeated sales boxes.

---

# 19. Public library conversion flow

Public guide page:
1. quality
2. usefulness
3. preview
4. contents
5. trust/research
6. campaign mechanism
7. CTA

Primary CTA:
**Desbloquear com 1 kg — R$ 12,90**

Secondary:
**Ver outros guias**

Do not call the content a “free bonus” in the main positioning.
It is a useful digital reward/product attached to the support.

---

# 20. Print / PDF

The user must be able to:
- print;
- save as PDF;
- eventually download a generated master PDF.

### Immediate launch

Implement excellent print CSS:
- hide nav/buttons/video controls;
- show video title + source URL text instead of iframe;
- expand collapsed sections;
- avoid clipped tables;
- page break before major chapters where appropriate;
- prevent orphan headings;
- black text on white;
- preserve figures;
- include title/release/source note.

Button:
**“Imprimir / Guardar em PDF”**

### Future server PDF

Keep an interface for:
- Playwright/Chromium render
or
- dedicated PDF generation pipeline.

The canonical prose must remain the same.

---

# 21. Search and filters

Implement client-side catalog search on normalized metadata.

Search fields:
- title
- subtitle
- tags
- topics

Filters:
- filhotes
- treino
- comportamento
- alimentação
- cuidados
- raças
- família
- apartamento
- rotina

Do not overengineer full-text search for launch.

---

# 22. Breed atlas architecture

Do not bury all future breeds in one monolithic Markdown file forever.

For launch:
- current guide remains readable;
- additionally prepare structured breed dataset.

Suggested:

```
library/pt-BR/breeds/
  index.yaml
  labrador-retriever.yaml
  golden-retriever.yaml
  ...
```

Schema:

```yaml
id:
slug:
name:
fci_group:
origin:
size:
energy:
exercise:
trainability:
grooming:
vocalization:
apartment:
heat_sensitivity:
children_context:
other_dogs_context:
small_animals_context:
alone_time_context:
health_welfare_notes:
history_function:
ideal_for:
think_twice_if:
questions_before_choice:
media_ids:
source_ids:
last_reviewed:
```

Never assign a deterministic “compatibility score”.

Use qualitative labels:
- baixa
- moderada
- alta

with explanatory text.

---

# 23. Guide metadata UI

Show useful facts, not fake marketing metrics.

Allowed:
- reading time estimate
- chapter count
- number of checklists actually present
- videos actually present
- tables actually present
- last reviewed date
- version

Do not invent:
- “10.000 leitores”
- “98% recomendado”
- bestseller badges
- fake ratings

---

# 24. Reference/source panel

At the end of each guide:
- “Fontes e revisão”
- list publishers
- optional links
- last source review date

Do not turn every sentence into academic citation clutter.

For higher-risk medical/nutrition sections:
- surface source notes more prominently.

---

# 25. Content risk handling

The library is educational.

Render a reusable boundary component when metadata indicates medical content.

General red flags may be shown.

Never convert general editorial content into:
- diagnosis;
- medication prescribing;
- individual dosage;
- personalized vaccine schedule;
- therapeutic diet prescription.

---

# 26. Design direction

The existing brand uses:
- petrol/dark green
- emerald accents
- cream backgrounds
- coral in other MyPets contexts

For library:
- retain brand;
- reduce conversion-page visual noise;
- increase editorial sophistication.

Reference mood:
- premium nature magazine
- modern digital reading app
- calm animal-welfare editorial

Use:
- large photography
- generous white/cream space
- elegant cards
- subtle shadows
- rounded surfaces consistent with MyPets
- strong readable typography

Avoid:
- excessive gradients
- neon
- gamification confetti
- cartoonish pet icons everywhere
- dense admin look

---

# 27. Reader typography

Body:
- comfortable serif OR highly readable editorial sans depending on existing font availability
- 17–19 px desktop equivalent
- 16–18 px mobile
- line height around 1.65–1.8

Headings:
- strong display hierarchy

Reading measure:
- avoid 1000px text lines

Add user controls only if simple:
- font size A-/A+
- light/dark
- reader/book mode

Do not delay launch for advanced personalization.

---

# 28. Dark mode

If the application already supports theme:
- make reader work in dark mode;
- ensure media/callout contrast.

Print always light.

---

# 29. Performance

Targets:
- no huge JS bundle for reader;
- server render core content;
- lazy video;
- optimized images;
- avoid loading all guide bodies on catalog page;
- preview page receives only preview;
- code split optional book mode.

Aim for excellent Core Web Vitals.

---

# 30. SEO

For `/biblioteca/[slug]` generate:
- title
- description
- canonical
- OpenGraph
- image
- breadcrumbs structured data where appropriate

Library:
- CollectionPage or ItemList structured data if useful and correct

Guide preview:
- Article/CreativeWork only if semantically accurate.

Do not mark entitled content as freely accessible.

Breed pages:
- indexable when complete and useful
- unique description
- source-backed
- internal links to relevant guides

---

# 31. Sitemap

Update sitemap with:
- `/biblioteca`
- public guide title pages
- approved breed pages

Exclude:
- reader
- receipt
- private library
- print private URLs

---

# 32. Analytics events

Preserve current campaign events.

Add reader events with non-sensitive payload:

- LIBRARY_VIEW
- GUIDE_PREVIEW_VIEW
- GUIDE_UNLOCK_CLICK
- GUIDE_OPEN
- GUIDE_SECTION_VIEW
- GUIDE_COMPLETE
- GUIDE_PRINT
- GUIDE_VIDEO_PLAY
- GUIDE_RELATED_CLICK

Do not fire “complete” based only on loading the page.

---

# 33. Error states

Handle:
- invalid slug
- invalid receipt
- receipt valid but guide not entitled
- missing synced content
- media unavailable
- failed video
- old alias
- content release mismatch

Errors should not expose internals.

Provide recovery CTA.

---

# 34. Existing campaign page changes

Do not radically rebuild `/ajudar/ebooks` before launch.

Make targeted improvements:

1. Replace static assumption of five books with content index.
2. Show new guide count automatically.
3. Link each card to public library preview.
4. Keep funnel selection limited to campaign-configured reward SKUs.
5. If new guides are not yet connected to backend reward keys, they may appear as “em breve” or free/public library items but MUST NOT be selectable as paid reward until entitlement mapping exists.

Never create a frontend-only paid SKU.

---

# 35. Backend contract

Do not invent payment behavior.

For library progress, create interfaces but use local storage if backend endpoint is not ready.

For expanded paid catalog, document required backend change:
- reward key
- product selection
- receipt entitlement
- campaign analytics

No frontend-only entitlement.

---

# 36. Compatibility with FacePets

Do not build the FacePets AI now.

Prepare content retrieval compatibility.

The content model already includes:
- ai_use
- medical_risk
- child_safe
- persona_use
- source confidence/review dates

Future FacePets conversational layer can consume approved segments.

Do not add any generative chat dependency to the launch-critical path.

---

# 37. Implementation folders suggested

```
src/
  app/
    biblioteca/
      page.tsx
      [slug]/
        page.tsx
        ler/
          page.tsx
      racas/
        page.tsx
        [breed]/
          page.tsx
    minha-biblioteca/
      page.tsx

  components/
    library/
      library-card.tsx
      library-hero.tsx
      guide-preview.tsx
      reader-shell.tsx
      reader-toc.tsx
      reader-toolbar.tsx
      reader-progress.tsx
      reader-callout.tsx
      reader-checklist.tsx
      reader-media.tsx
      reader-video.tsx
      reader-table.tsx
      reader-source-panel.tsx
      book-mode.tsx
      breed-card.tsx
      breed-profile.tsx

  lib/
    library/
      index.ts
      schema.ts
      content.ts
      aliases.ts
      entitlement.ts
      markdown.ts
      media.ts
      progress.ts
      print.ts
```

Use existing component system instead of duplicating generic UI primitives.

---

# 38. Launch sequencing

## Phase 1 — must ship
- content sync
- `/biblioteca`
- public guide page
- entitled reader
- current receipt compatibility
- responsive rich markdown
- media registry embeds
- source panel
- print CSS
- redirects
- SEO/noindex
- build/lint/typecheck

## Phase 2 — ship if stable before deadline
- `/minha-biblioteca` progress
- bookmarks/checklists
- search/filter
- breed atlas route
- book mode

## Phase 3 — after campaign launch
- server-generated PDFs
- authenticated cross-device progress
- advanced reader personalization
- richer SEO derivative pages
- FacePets retrieval APIs

Do not block Phase 1 on Phase 3.

---

# 39. Visual QA checklist

Test at:
- 360px
- 390px
- 768px
- 1024px
- 1440px

Check:
- no clipped tables
- no horizontal content overflow
- sticky bars do not cover anchors
- YouTube responsive
- image credits readable
- TOC usable
- print clean
- dark mode contrast
- long headings wrap
- callouts do not break
- lists readable
- focus states visible

---

# 40. Functional QA

Mandatory:

```
bun run lint
bun run typecheck
bun run build
```

Also manually verify:

1. valid receipt unlocks owned guide
2. invalid receipt does not
3. valid receipt cannot open unowned guide
4. legacy slug resolves
5. current /ebooks URL does not break
6. print produces clean pages
7. public preview source does not include complete premium guide
8. noindex works for reader
9. sitemap contains public library
10. videos only load from allowlist
11. missing video fails gracefully
12. mobile TOC closes after navigation
13. progress restores
14. campaign CTA returns correctly

---

# 41. PR strategy

Do the work on a feature branch, not directly on main.

Suggested:
`feat/digital-library-reader-v1`

Make coherent commits:
1. content sync/types
2. public library
3. reader
4. entitlement compatibility
5. media
6. print
7. SEO/QA

PR description must include:
- screenshots
- routes
- assumptions
- tests
- unresolved launch risks

---

# 42. Definition of Done for the 24h launch

The library is launchable when:

- the canonical content release is pinned;
- at least the current 5 paid guides render fully;
- newly enabled reward guides render only after backend mapping;
- library landing is public and high quality;
- preview pages are indexable;
- reader requires entitlement;
- reader works on mobile;
- images/videos/tables/checklists render;
- print/PDF browser output works;
- legacy receipt URLs still work;
- source panel exists;
- full paid content is not leaked publicly;
- lint/typecheck/build succeed;
- campaign payment path still succeeds;
- no invented impact figures or reviews appear.

---

# 43. Final instruction

Act as a senior product engineer and editorial UX designer.

Inspect the existing code before changing it.

Reuse current:
- MyPets branding
- payment access logic
- shared UI components
- analytics conventions
- API helpers

Do not produce a disconnected prototype.

Build the Digital Library **inside the current MyPets production architecture**.

Prioritize reliability and launchability.

When forced to choose between:
- fancy page-turn animation
and
- a reliable accessible reader,

ship the reliable reader first.

When forced to choose between:
- an architectural rewrite
and
- compatibility with the live campaign,

preserve compatibility.

At the end:
1. run checks;
2. document every changed route;
3. list any backend requirement;
4. list any content/media item still missing;
5. leave the project in a deployable state.
