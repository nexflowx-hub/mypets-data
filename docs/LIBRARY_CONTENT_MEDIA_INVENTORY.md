# MyPets Digital Library — Content & Media Inventory

**Snapshot:** 2026-09-25  
**Branch:** `feat/digital-library-v1`  
**Status:** editorial launch build / active QA

## Executive snapshot

- **13 canonical guides**
- **61,275 words** across the guide corpus
- **58 explicit `[!MEDIA]` placements** already wired into guide Markdown
- **73 approved media records**
  - **63 image records**
  - **10 official video embeds**
- **47 structured breed profiles**
- **47 / 47 breed profiles linked to specific real photographs**
- **103 planned visual/editorial interventions** in the guide-level media pack, combining approved media with original MyPets diagrams, trackers, timelines and interactive/printable components

> Word count is a build-time editorial measure, not a promise of fixed PDF pages. Web/PDF page count changes substantially with photography, tables, diagrams and responsive layout.

## Guide inventory

| # | Guide | Words | Headings / content blocks | Linked media placements | Tables / table rows | Checklist items | Visual pack target |
|---|---|---:|---:|---:|---:|---:|---:|
| 01 | Cuidados Essenciais com o Seu Cão | 5,234 | 104 | 3 | 0 | 28 | 7 |
| 02 | Os Primeiros 30 Dias com um Filhote | 5,168 | 129 | 3 | 14 | 13 | 7 |
| 03 | Treino Gentil: 7 Comandos para o Dia a Dia | 5,111 | 143 | 6 | 4 | 0 | 9 |
| 04 | Guia das Raças: Escolha pelo Estilo de Vida | 6,221 | 146 | 16 | 27 | 11 | 20+ |
| 05 | Rotina de Alimentação e Bem-Estar | 5,065 | 102 | 3 | 18 | 28 | 6 |
| 06 | Linguagem Corporal Canina | 4,974 | 119 | 4 | 10 | 10 | 8 |
| 07 | Passeios sem Stress | 4,307 | 106 | 6 | 19 | 17 | 8 |
| 08 | Ficar Sozinho em Casa | 4,181 | 116 | 2 | 9 | 36 | 6 |
| 09 | Cão em Apartamento | 4,130 | 134 | 4 | 5 | 33 | 7 |
| 10 | Higiene, Banho e Saúde Oral | 4,268 | 155 | 2 | 18 | 16 | 6 |
| 11 | Adotei um Cão Adulto: E Agora? | 4,200 | 124 | 3 | 6 | 12 | 6 |
| 12 | Cães e Crianças | 4,411 | 136 | 3 | 0 | 32 | 6 |
| 13 | 50 Ideias de Enriquecimento para Cães | 4,005 | 154 | 3 | 20 | 16 | 7 |

## What “visual pack target” means

The target is not just a count of photographs. It combines:

- real/approved photography;
- official video embeds;
- image galleries;
- original diagrams;
- timelines;
- traffic-light graphics;
- weekly/day plans;
- comparison matrices;
- trackers;
- printable cards;
- interactive reader components.

The canonical visual-production map lives in:

`media/guide-media-pack.yaml`

The approved third-party/MyPets asset registry lives in:

`media/registry.yaml`

## Media system

### Approved video embeds

Current registry includes official/authoritative video material for:
- body condition scoring;
- muscle condition assessment;
- force-free sit training;
- reward-based training lesson;
- recall;
- leave-it;
- loose-lead walking;
- dig-box enrichment;
- food enrichment;
- child/dog education.

Videos are embedded from official publishers rather than downloaded/rehosted.

### Real photography

The registry contains:
- MyPets-owned campaign/editorial photography;
- Creative Commons photography;
- CC0/public-domain photography;
- attribution and source metadata when required.

### Breed atlas photography

Current structured atlas:
- **47 breed profiles**
- **47 profiles linked to real photographs**
- **0 profiles without a dedicated breed-specific photograph in the launch dataset**

The launch atlas now has a dedicated real-photography reference for every structured breed profile. Attribution/license QA and asset ingestion into controlled storage remain release tasks.

## Guide-specific media direction

### Guide 01 — Cuidados Essenciais
Real lifestyle photography plus:
- daily-rhythm timeline;
- home-safety map;
- red-flag traffic light;
- annual care calendar.

### Guide 02 — Primeiros 30 Dias
Puppy/crate/walk/rest photography plus:
- first 72 hours timeline;
- socialization traffic light;
- 30-day roadmap;
- toilet-training loop.

### Guide 03 — Treino Gentil
Highest video density:
- clicker training image;
- clicker object image;
- sit video;
- recall video;
- leave-it video;
- loose-lead video;
- learning loop;
- 3D difficulty matrix;
- 21-day plan.

### Guide 04 — Raças
Visual flagship:
- breed photography;
- structured breed cards;
- lifestyle matrix;
- cost wheel;
- decision tree;
- dedicated atlas UI using `library/pt-BR/breeds/index.json`.

### Guide 05 — Alimentação
WSAVA videos plus:
- label-reading diagram;
- transition process;
- body-observation visual;
- 30-day nutrition tracker.

### Guide 06 — Linguagem Corporal
Real body-language examples plus:
- play bow;
- turning away;
- calming signals;
- dogs playing;
- whole-body annotation;
- traffic-light language;
- before/during/recovery process;
- printable child card.

### Guide 07 — Passeios sem Stress
Walking photos + training videos plus:
- route A/B/C cards;
- loose-lead loop;
- trigger-distance diagram;
- 14-day plan.

### Guide 08 — Ficar Sozinho
Rest/crate imagery plus:
- seconds-to-minutes staircase;
- camera observation board;
- separation hierarchy;
- 14-day plan.

### Guide 09 — Cão em Apartamento
Home/walk/enrichment media plus:
- apartment functional-zone map;
- noise trigger map;
- weekly enrichment planner.

### Guide 10 — Higiene e Saúde Oral
Grooming photography plus:
- tolerance body map;
- toothbrushing steps;
- 10-day cooperative-care plan;
- alert/warning grid.

### Guide 11 — Adotei um Cão Adulto
Rest, walk and distance/body-language photography plus:
- first 72h timeline;
- 30-day roadmap;
- adaptation tracker.

### Guide 12 — Cães e Crianças
Education video + body-language photography plus:
- five-rules child poster;
- dog traffic light;
- safe-space diagram;
- printable activity pages.

### Guide 13 — Enriquecimento
Official enrichment videos + play photography plus:
- enrichment wheel;
- difficulty slider;
- weekly planner;
- safety card;
- 30-day challenge / activity-card system.

## Editorial status

### Flagship-depth
Guides 01–05 are above ~5k words and function as the primary launch anchors.

### Near-flagship / substantial
Guides 06–13 are now approximately 4k–5k words each and have been expanded with practical exercises, scenarios, trackers and visual hooks.

### Remaining launch QA
Before a content release is tagged:
- veterinary/factual review;
- language consistency pass;
- verify every external media source/license;
- confirm all media IDs resolve;
- responsive reader QA;
- print/PDF QA;
- entitlement QA;
- final release ref/checksum.

## Production principle

The library should feel **visual and playful without becoming superficial**.

A typical reading sequence should alternate:

`story/explanation → visual → practical scenario → checklist/table → video/figure → action → recap`

rather than presenting uninterrupted walls of text.
