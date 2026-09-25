# Frontend Handoff — MyPets Digital Library v1

## Goal

Upgrade the existing eBook reward flow into a real digital library without breaking the existing payment/receipt entitlement system.

Existing production concepts to preserve:
- campaign route: `/ajudar/ebooks`
- successful payment receipt validation
- reward keys/entitlements
- existing reward slugs where already issued
- collection after payment

## Canonical content

Repository: `nexflowx-hub/mypets-data`

Source tree:
- `library/manifest.yaml`
- `library/pt-BR/<guide>/meta.yaml`
- `library/pt-BR/<guide>/guide.md`
- `library/pt-BR/<guide>/sources.yaml`
- `media/registry.yaml`

### Compatibility aliases

Do not invalidate historical/current payment reward keys.

Map:
- `filhote-primeiros-30-dias` -> canonical `primeiros-30-dias`
- `rotina-alimentacao` -> canonical `alimentacao-bem-estar`
- other current slugs remain equivalent

The entitlement layer must resolve aliases before content lookup.

## Recommended ingestion

### v1 fastest safe approach

At build/deploy time, sync the pinned content release into the frontend build artifact.

Do not rely on client-side GitHub requests.

Suggested environment:
- `MYPETS_CONTENT_REF=<commit-sha-or-release-tag>`
- optional server-side token only if the data repo becomes private

Build step:
1. fetch/copy approved release files;
2. validate required metadata;
3. generate a local content index;
4. fail build if manifest points to missing content.

Production pages then read local build content.

### Why pin a ref?

A content commit must not silently change what a deployed reader shows. A frontend deployment points to a specific content release/commit.

## Routes

### Public library

`/biblioteca`

Show:
- collection title
- five guide cards
- cover
- useful promise
- reading time
- chapter/section count
- preview CTA
- campaign CTA

### Public title page

`/biblioteca/[slug]`

Show:
- cover/hero
- description
- table of contents
- practical assets (plan/checklists/trackers)
- selected preview excerpt from `preview_sections`
- source-quality note
- CTA: participate / unlock

This page is indexable.

### Entitled reader

Preserve or redirect existing:
- `/ebooks/[slug]?receipt=...`

Preferred canonical reader URL:
- `/biblioteca/[slug]/ler?receipt=...`

Old URL should redirect while preserving receipt.

### Collection

Existing `/ebooks/colecao` can become/redirect to:
- `/minha-biblioteca?receipt=...`

## Reader UX

Desktop:
- left collapsible TOC
- center reading column
- right optional progress/source panel

Mobile:
- clean reading column
- sticky compact progress bar
- TOC drawer
- next/previous section controls

Required:
- reading progress
- section anchor navigation
- resume position
- chapter completion
- printable/download option when entitled
- media embeds from allowlisted registry
- source/reference drawer
- related guide CTA
- campaign impact reminder without interrupting reading

## Markdown renderer

The frontend already includes `react-markdown`.

Support:
- headings
- lists
- tables
- blockquotes/callouts
- task checklists
- explicit anchors
- approved YouTube embeds referenced by media id

Sanitize raw HTML. Only allow the minimal anchor syntax needed by canonical content or replace anchors during ingestion.

Do not render arbitrary iframe/html from Markdown.

## Progress storage

v1:
- localStorage fallback for anonymous receipt-based sessions

Production:
- backend/Supabase record keyed to authenticated user or entitlement:
  - guide_id
  - release_id
  - last_section
  - percent
  - completed_sections
  - checklist_state
  - updated_at

Do not put payment secrets or privileged keys in browser storage.

## Content security

The current data repository is public. If the business requirement is that full reward content must not be discoverable outside entitlement, change the repository to private before launch or publish only public/preview material there and sync private full releases through a protected pipeline.

Even with a private repo, entitlement must still be enforced in the app.

## SEO

Index:
- `/biblioteca`
- title/preview pages
- curated public derivatives under `/guias/...`

Noindex:
- receipt URLs
- entitled reader
- collection/account pages

## Media

Videos:
- render embeds only from allowlisted registry/domain
- lazy load
- privacy-enhanced YouTube mode if practical

Creative Commons images:
- ingest licensed copy to controlled storage
- store attribution alongside asset
- render credit where license requires it

## Definition of done

- all five guides resolve from canonical content
- current payment reward keys still work
- public library and title preview exist
- entitled reader renders long-form content correctly
- TOC/anchors work on mobile and desktop
- references/media work
- PDF/print output is readable
- no full premium guide leaks into public page source through a hidden component
- sitemap/canonical/noindex rules are correct
