# MyPets Digital Library — Architecture

## Operating model

- **Google Drive**: editorial workspace, research notes, comments and human review.
- **GitHub (this repository)**: canonical, versioned publishing content.
- **MyPets frontend**: renders the web reader.
- **Backend/Supabase**: entitlements, progress, bookmarks and checklist state.
- **Private object storage**: final PDFs, worksheets and large media.

One canonical content base should feed web, PDF and selected public/SEO derivatives.

## Repository layout

```
content/
  collection.yaml
  pt-BR/
    cuidados-essenciais/
      meta.yaml
      guide.md
      sources.yaml
    primeiro-filhote/
    treino-gentil/
    guia-das-racas/
    alimentacao-bem-estar/
media/
  registry.yaml
docs/
  CONTENT_STANDARD.md
  ARCHITECTURE.md
```

## Publishing flow

RESEARCH -> DRAFT -> TECHNICAL REVIEW -> EDITORIAL QA -> RELEASE CANDIDATE -> PUBLISHED

No published release should be silently replaced. A material change creates a new version and changelog entry.

## Web URLs

Public catalogue:
- /biblioteca
- /biblioteca/[slug]

Entitled reading:
- /minha-biblioteca
- /biblioteca/[slug]/ler

Selected public chapters may be exposed as SEO derivatives, generated from canonical content rather than separately maintained copies.

## Future FacePets use

Content is prepared for controlled retrieval by future conversational experiences. Every guide can be classified by audience, medical-risk level, child-safety and AI-use permission. General education and companionship are allowed where appropriate; diagnosis, medication, individualized treatment and emergency substitution are not.
