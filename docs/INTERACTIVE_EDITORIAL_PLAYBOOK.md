# MyPets Digital Library — Interactive Editorial Playbook

**Goal:** make long-form content playful, memorable and useful without turning animal-care guidance into gamification noise.

## Core principle

Every interactive element must do at least one of these:
- improve observation;
- help the reader make a safer decision;
- convert theory into an action;
- reduce cognitive load;
- create a useful record;
- make a child/family concept easier to remember.

Do not add badges, points or fake rewards merely to increase engagement.

## Component families

### 1. TrafficLight
Use for:
- body language;
- socialization;
- risk escalation;
- when to observe / pause / seek help.

Web:
- tap a colour to expand examples.

Print:
- three stacked labelled boxes.

### 2. DayPlan / ChallengeGrid
Use for:
- 7-day care plan;
- 14-day walking plan;
- 14-day alone-time plan;
- 21-day training plan;
- 30-day puppy/adoption/enrichment plan.

Web:
- check days;
- save state;
- “continuar hoje”.

Print:
- checkbox calendar.

### 3. ScenarioCards
Use for:
- “o que você faria?”;
- visitor scenarios;
- street encounters;
- children + dog;
- grooming tolerance.

Web:
- reveal recommended response after selection.

Important:
- no scoring that implies diagnosis/competence.

### 4. SwipeCards
Use for:
- enrichment activity deck;
- breed quick facts;
- training micro-exercises;
- household safety audit.

Web:
- swipe/save/favourite.

Print:
- card grid.

### 5. BeforeAfter
Use for:
- body language;
- adoption adjustment;
- nutrition tracking;
- grooming tolerance.

Web:
- compare two states.

Print:
- two-column comparison.

### 6. ObservationTracker
Use for:
- food;
- stool/appetite;
- separation video;
- behaviour contexts;
- walking triggers;
- adoption.

Web:
- simple rows stored in progress state.

Print:
- writable table.

### 7. DecisionTree
Use for:
- breed choice;
- “should I approach?”;
- walk management;
- grooming “continue/pause/stop”.

Never provide medical diagnosis.

### 8. ComparisonMatrix
Use for:
- breed characteristics;
- equipment;
- routine alternatives.

Use qualitative labels and context rather than fake precision.

### 9. HotspotFigure
Use for:
- whole-dog body language;
- grooming body map;
- home safety map.

Web:
- tap hotspot for explanation.

Print:
- numbered labels + legend.

### 10. VideoLesson
Pattern:
1. context text;
2. video;
3. “watch for these 3 things”;
4. one practical exercise.

Avoid dropping a video without instructional framing.

### 11. KidCard
Use in:
- body language;
- dogs + children.

Rules:
- very short text;
- large symbols;
- action verb;
- no frightening imagery.

Examples:
- “Ele se afastou? Deixa.”
- “Está comendo? Dá espaço.”
- “Rosnou? Chama um adulto.”

### 12. MythReality
Use for:
- breed stereotypes;
- nutrition myths;
- training myths.

Pattern:
**Mito** → **O que sabemos** → **O que fazer na prática**

### 13. OneMinuteMission
A tiny action immediately after a section.

Examples:
- photograph your dog's ID tag;
- check harness fit;
- choose the safe-space location;
- write the current food name;
- observe 10 seconds without touching.

### 14. PrintableWorksheet
Required examples:
- emergency contacts;
- puppy 30-day plan;
- training diary;
- breed comparison sheet;
- nutrition diary;
- body-language personal traffic light;
- walk trigger map;
- separation camera log;
- apartment noise map;
- grooming tolerance map;
- adoption diary;
- child safety poster;
- enrichment favourites list.

## Reader rhythm

Avoid more than ~3 consecutive text-only screens where a meaningful interaction/visual can improve understanding.

Recommended sequence:

`explanation → image/figure → scenario → action/checklist → explanation → video/table → recap`

## Microcopy

Use action language:
- “Observe agora”
- “Experimente hoje”
- “Marque quando concluir”
- “Veja o que mudou”
- “Dê espaço”
- “Torne mais fácil”
- “Compare com o seu cão”

Avoid:
- “Você falhou”
- “Cão teimoso”
- “Domine”
- “Prove que é o líder”

## Completion

A reader may mark sections complete.

Completion is personal organization, not a certificate of competence.

Do not issue:
- veterinary certificates;
- trainer certification;
- “qualified tutor” badges.

## Motion

Use subtle motion:
- progress;
- card reveal;
- page swipe;
- hotspot highlight.

Respect `prefers-reduced-motion`.

No animation should delay access to safety information.

## Print parity

Every interactive component requires a print fallback.

Examples:
- slider → labelled scale;
- hotspot → numbered diagram;
- reveal card → question + answer block;
- checklist → empty checkboxes;
- video → thumbnail/title/source;
- swipe deck → card grid.

## Launch priority

Must render on day one:
- traffic lights;
- day plans;
- scenario cards;
- checklists;
- comparison tables;
- media/video lesson;
- trackers.

Can follow:
- hotspots;
- swipe deck;
- book-mode page turn;
- richer saved worksheets.
