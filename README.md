# MyPets Data

Canonical content repository for the MyPets / FacePets ecosystem.

## Priority: MyPets Digital Library

This repository stores versioned editorial content, source ledgers, release metadata and reusable media metadata for the MyPets Digital Library.

### Responsibilities

- long-form guide content in Markdown/MDX-compatible Markdown
- structured guide metadata
- source and copyright/license ledgers
- media/embed registry
- release manifests and changelogs
- AI-safety/retrieval metadata for future FacePets conversational experiences

### Does not store

- customer payment data
- user entitlements or reading progress
- secrets
- private customer data
- downloadable production PDFs as the primary delivery mechanism
- third-party copyrighted media copied without an appropriate license

Runtime state belongs in the MyPets backend/Supabase. Final downloadable assets belong in private object storage and are released by entitlement/signed URL.

## Editorial rule

Research widely; publish original MyPets prose.

"Free to read" is not automatically "free to copy." Third-party text, images, charts and video are reused only when the license or embedding terms support the intended use. Otherwise they are linked/cited and the factual substance is rewritten in original language.

## Initial collection

1. Cuidados Essenciais com o Seu Cão
2. Os Primeiros 30 Dias com um Filhote
3. Treino Gentil: 7 Comandos para o Dia a Dia
4. Guia das Raças: Escolha pelo Estilo de Vida
5. Rotina de Alimentação e Bem-Estar

See `docs/CONTENT_STANDARD.md` and `docs/ARCHITECTURE.md`.
