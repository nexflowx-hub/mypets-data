# MyPets Digital Library — Architecture v1

## Canonical model

- **mypets-data (this repo):** canonical published editorial content, source ledgers, media metadata and release manifests.
- **Google Drive:** editorial workspace for research notes, comments, collaborative review and PDF proofing.
- **mypets-frontend:** renderer/reader, SEO pages, preview/paywall UX.
- **mypets-backend + Supabase:** products, contributions, entitlements, reading progress, checklist state and audit events.
- **Private object storage:** final PDFs/worksheets/media downloads delivered via signed URL.

The same canonical content must feed web reading and PDF generation. Do not maintain separate prose copies.

## Content tree

```
library/
  manifest.yaml
  pt-BR/
    01-cuidados-essenciais/
      meta.yaml
      guide.md
      sources.yaml
    02-primeiros-30-dias/
    03-treino-gentil/
    04-guia-das-racas/
    05-alimentacao-bem-estar/
media/
  registry.yaml
sources/
  registry.yaml
releases/
  v1/
docs/
```

## Web routes

Public:
- /biblioteca
- /biblioteca/[slug]
- /biblioteca/[slug]/preview
- /guias/[topic] for selected SEO derivatives

Entitled:
- /minha-biblioteca
- /biblioteca/[slug]/ler
- /biblioteca/[slug]/ler#[section]
- /biblioteca/[slug]/download

## Reader features

- mobile-first responsive typography
- persistent table of contents
- reading progress
- section completion
- checklist state
- bookmarks
- related guides
- references/source panel
- embedded approved videos
- accessible media captions/alt text
- discreet campaign-impact CTA
- PDF download when entitled

## Release discipline

No silent replacement of published content. Every meaningful editorial revision increments a release version and records:
- release date
- source review date
- content checksum
- PDF checksum when generated
- changelog
- reviewer status

## FacePets compatibility

FacePets is not a blocker for MyPets Library v1, but content is tagged for safe future retrieval:
- ai_use
- medical_risk
- child_safe
- persona_use
- last_reviewed
- source_confidence

The future FacePets companion/play layer may use only approved low-risk content and must never imply veterinary diagnosis, treatment or prescribing.
