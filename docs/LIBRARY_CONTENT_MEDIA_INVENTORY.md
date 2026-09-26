# MyPets Digital Library — Content & Media Inventory

**Snapshot:** 2026-09-25  
**Branch:** `feat/digital-library-v1`  
**Status:** editorial launch build / active QA

## Executive snapshot

- **13 canonical guides**
- **64,208 words** across the guide corpus
- **58 explicit `[!MEDIA]` placements** already present in guide Markdown
- **103 exact planned in-guide visual/editorial placements** in the canonical master map
- **91 approved media records**
  - **81 image records**
  - **10 official video embeds**
- **64 structured breed profiles**
- **64 / 64 breed profiles linked to a real-photography reference**
- **17 new Atlas 64 profiles** include richer FCI group/origin/editorial fields
- all covers are specified to use the **official round MyPets logo/medallion**
- print/PDF worksheets may use the same round mark as a low-opacity watermark

Canonical production files:
- `media/media-placement-master.json`
- `docs/MEDIA_PLACEMENT_MASTER_MAP.md`
- `media/guide-media-pack.yaml`
- `media/registry.yaml`
- `library/pt-BR/breeds/index.json`
- `docs/ATLAS_64_PRODUCTION_MAP.md`
- `docs/COVER_BRAND_SYSTEM.md`

> Word count is an editorial measure, not a fixed PDF-page promise. Photography, tables, interactive blocks and responsive layout change pagination substantially.

## Guide inventory

| # | Guide | Words | Content headings/blocks | Explicit media markers | Table rows | Checklist items | Exact visual target |
|---:|---|---:|---:|---:|---:|---:|---:|
| 01 | Cuidados Essenciais com o Seu Cão | 5,234 | 104 | 3 | 0 | 28 | 7 |
| 02 | Os Primeiros 30 Dias com um Filhote | 5,168 | 129 | 3 | 14 | 13 | 7 |
| 03 | Treino Gentil: 7 Comandos para o Dia a Dia | 5,111 | 143 | 6 | 4 | 0 | 9 |
| 04 | Guia das Raças: Escolha pelo Estilo de Vida | **9,154** | 215 | 16 | 27 | 11 | 20 |
| 05 | Rotina de Alimentação e Bem-Estar | 5,065 | 102 | 3 | 18 | 28 | 6 |
| 06 | Linguagem Corporal Canina | 4,974 | 119 | 4 | 10 | 10 | 8 |
| 07 | Passeios sem Stress | 4,307 | 106 | 6 | 19 | 17 | 8 |
| 08 | Ficar Sozinho em Casa | 4,181 | 116 | 2 | 9 | 36 | 6 |
| 09 | Cão em Apartamento | 4,130 | 134 | 4 | 5 | 33 | 7 |
| 10 | Higiene, Banho e Saúde Oral | 4,268 | 155 | 2 | 18 | 16 | 6 |
| 11 | Adotei um Cão Adulto: E Agora? | 4,200 | 124 | 3 | 6 | 12 | 6 |
| 12 | Cães e Crianças | 4,411 | 136 | 3 | 0 | 32 | 6 |
| 13 | 50 Ideias de Enriquecimento para Cães | 4,005 | 154 | 3 | 20 | 16 | 7 |

## MEDIA PLACEMENT MASTER MAP

The canonical master map contains exactly **103 placements**.

Each placement records:
- guide id;
- exact section heading/anchor;
- before/after position;
- media or original-visual id;
- visual type;
- PT-BR alt text;
- editorial caption;
- video “watch for” prompts where useful.

QA performed on 2026-09-25:
- **103/103 section anchors resolved**
- **all referenced media ids resolved**
- **all original visual ids resolved**
- **all cover hero ids resolved**
- **canonical round MyPets brand mark resolved**
- **64/64 breed photo ids resolved**

## Cover system

Canonical logo asset:
- media id: `mypets-round-logo`
- frontend source: `src/lib/brand.ts#BRAND.logoUrl`

Cover treatment:
- bottom-right round editorial seal;
- safe margin around 4%;
- avoid dog faces/eyes and important focal points;
- web opacity around 0.82;
- print/PDF optional watermark around 0.12–0.18;
- never rebuild/retype the logo.

## Atlas MyPets 64

The structured atlas now contains **64 breeds**.

The additional 17 profiles are:
1. Welsh Corgi Pembroke
2. Welsh Corgi Cardigan
3. American Staffordshire Terrier
4. Staffordshire Bull Terrier
5. Newfoundland / Terra-Nova
6. Flat-Coated Retriever
7. Cão de Água Português
8. Havanese / Bichon Havanês
9. Pekingese
10. Japanese Spitz
11. Basenji
12. Shiba Inu
13. Chow Chow
14. Alaskan Malamute
15. English Setter
16. Irish Red Setter / Setter Irlandês
17. Dálmata

Every one of the 64 profiles has:
- dedicated real-photo reference;
- photo alt text;
- photo caption;
- size;
- energy;
- grooming;
- trainability;
- vocalization;
- apartment context;
- heat context;
- family context;
- alone-time context.

The 17 new profiles additionally include:
- FCI group;
- country/origin context;
- functional history;
- editorial summary;
- “combina melhor com”;
- “pense duas vezes se”;
- welfare notes;
- dedicated breed-specific FCI source id.

## Media system

### Images
The registry currently contains **81 image records** spanning:
- MyPets-owned brand/editorial assets;
- 64 breed-photo references;
- body-language photography;
- puppy/crate/walking imagery;
- grooming/rest/training imagery;
- the official MyPets round logo.

### Videos
Current **10 official video embeds** cover:
- body condition;
- muscle condition;
- force-free sit;
- reward-based training;
- recall;
- leave-it;
- loose-lead walking;
- dig-box enrichment;
- food enrichment;
- children/dog education.

External video remains embed-only.

## Original MyPets visual system

The 103-placement map uses original components such as:
- traffic lights;
- timelines;
- roadmaps;
- process loops;
- day/week challenges;
- room maps;
- body maps;
- distance diagrams;
- comparison matrices;
- decision trees;
- trackers;
- child cards;
- printable checklists.

All original diagrams should be:
- semantic HTML/SVG;
- keyboard/screen-reader compatible where interactive;
- printable without JavaScript;
- branded subtly with the round MyPets mark when exported as standalone material.

## Remaining release QA

Before tagging production:
- veterinary/factual review;
- PT-BR language consistency pass;
- media license/attribution spot-check;
- ingest reusable external photography into controlled storage where appropriate;
- responsive reader QA;
- print/PDF QA;
- entitlement QA;
- pin final content commit/release;
- compute final checksums.

## Production principle

The desired reading rhythm is:

`explanation → visual → scenario → action/checklist → video/table → recap`

The goal is **lúdico, visual e memorável sem banalizar saúde, segurança ou comportamento**.
