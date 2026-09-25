# Z.AI Implementation Brief — MyPets Digital Library

## Goal

Build the first production-quality web reader for the MyPets Digital Library inside `nexflowx-hub/mypets-frontend`, consuming canonical content from `nexflowx-hub/mypets-data`.

Do not rewrite editorial content in the frontend. Content is owned by the data repository.

## Required routes

Public:
- `/biblioteca`
- `/biblioteca/[slug]`
- `/biblioteca/[slug]/preview`

Entitled:
- `/minha-biblioteca`
- `/biblioteca/[slug]/ler`

## Catalogue UX

Each card:
- cover/image placeholder
- title
- concise subtitle
- reading time
- practical assets badge
- locked/unlocked state
- campaign badge: 1 eBook = 1 kg
- CTA

Do not invent social proof or impact numbers.

## Guide landing

Show:
- cover
- title/subtitle
- who it is for
- expected reading time
- full table of contents
- practical assets included
- a meaningful free preview
- unlock CTA integrated with the existing eBook/ração flow
- related guides

## Reader UX

Mobile-first.

Desktop:
- left table of contents
- central reading column
- optional right rail for progress/notes/CTA

Mobile:
- sticky compact progress header
- TOC drawer
- readable typography
- no horizontal overflow

Functions:
- progress %
- chapter completion
- resume last position
- checklist state
- bookmarks/favorites
- previous/next chapter
- references section
- print/download action when entitled
- discreet related-guide CTA

## Content ingestion

Preferred v1:
- sync/copy content at build time from mypets-data, or
- use a controlled GitHub raw endpoint/build pipeline.

The reader should not fetch GitHub on every public request in production.

Create a content adapter interface so storage can later move to object storage/CMS without changing page components.

Parse:
- collection.yaml
- each meta.yaml
- guide.md
- sources.yaml

Support standard Markdown now and an MDX-compatible extension later.

## Security

Never trust client state for entitlement.
Unlocked guide content must be authorized server-side.

Do not expose:
- private storage paths
- service role secrets
- payment API secrets

## Database/API

Prepare DTOs for:
- library catalogue
- entitlement status
- reading progress
- checklist state
- bookmark state
- download grant

Use current MyPets backend seams and existing payment completion state.

## Visual direction

Premium editorial product, not blog.

- generous whitespace
- strong typography
- warm MyPets brand system
- high-quality cover art
- clear callout cards
- subtle progress feedback
- illustrations/photos as editorial support
- excellent mobile experience

## PDF

Do not make a separately authored PDF.
Provide a print/PDF stylesheet or server-side renderer based on canonical content.

The downloadable production PDF can later be generated and stored privately with release/version checksum.

## SEO

Catalogue and preview pages are indexable.
Entitled full-reader pages should not expose premium full text to search engines.

Support future public derivatives of selected chapters using canonical metadata and internal links.

## Analytics

Track at minimum:
- LIBRARY_VIEW
- GUIDE_VIEW
- GUIDE_PREVIEW_STARTED
- GUIDE_UNLOCK_CTA
- GUIDE_OPENED
- CHAPTER_COMPLETED
- GUIDE_COMPLETED
- PDF_DOWNLOAD
- RELATED_GUIDE_CTA

Do not treat page view as donation conversion.

## Acceptance criteria

- production build passes
- no invented content/impact
- all five draft guides visible in catalogue
- one guide can be read end-to-end in preview/dev entitlement mode
- responsive at common phone widths
- keyboard accessible navigation
- no horizontal scroll in tables
- source references render correctly
- locked state cannot be bypassed by URL alone
