# Z.AI Implementation Brief — MyPets Digital Library

Work on `nexflowx-hub/mypets-frontend`. Canonical editorial data is in `nexflowx-hub/mypets-data`.

## Mission

Transform the existing 1 eBook = 1 kg reward experience into a premium, mobile-first MyPets Digital Library while preserving current payment and receipt entitlement behavior.

Do not rewrite the editorial content. Consume the canonical content release.

## Non-negotiable constraints

1. Do not break `/ajudar/ebooks`.
2. Preserve existing `validateEbookReceipt` behavior and reward-key compatibility.
3. Keep old issued slugs working:
   - filhote-primeiros-30-dias -> primeiros-30-dias
   - rotina-alimentacao -> alimentacao-bem-estar
4. Public pages must never contain the entire entitled guide hidden in DOM/source.
5. Receipt/reader pages must be noindex.
6. No arbitrary HTML/iframe execution from Markdown.
7. Use source/media allowlists.
8. Keep MyPets visual language, but increase perceived quality substantially.

## Build

Implement:
- /biblioteca
- /biblioteca/[slug]
- /biblioteca/[slug]/ler
- /minha-biblioteca
- redirect compatibility from current /ebooks routes

Build a content adapter that reads a pinned mypets-data release/ref and exposes:
- collection metadata
- guide metadata
- preview fragments
- entitled full Markdown
- source list
- approved media

Use existing React/Next stack. `react-markdown` is already installed.

## Visual direction

The reader should feel closer to a premium reading product than a donation receipt:
- generous typography
- narrow readable measure
- progress line
- sticky TOC on desktop
- drawer TOC on mobile
- elegant callouts
- strong table styling
- task/checklist styling
- illustration/video panels
- clear source drawer
- cover/collection cards with premium editorial feel

Avoid dashboard clutter.

## Conversion

The reading experience is primary.

Use only a discreet end-of-section/end-of-guide conversion:
"Este guia colocou 1 kg em movimento. Quer escolher outro guia e ajudar com +1 kg?"

Do not interrupt chapters with repeated payment CTAs.

## Quality gates

Run:
- lint
- typecheck
- build
- manual mobile reader QA
- entitlement test with valid/invalid receipt
- slug alias test
- noindex/canonical check
- content-source sanitization test

Document all assumptions in a PR.
