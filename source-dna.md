# Study Game System - Source DNA

## Purpose

This document captures the reusable DNA extracted from:

- `index.html`
- `index hunters moving spectacular.html`
- `base_preguntas_ciencias_naturales.json`

The goal is to preserve what makes the source pages feel like play, not worksheets, while turning that logic into a reusable system for future study pages.

## Source audit snapshot

### Source page A - Family show

- Title: `Olivia's Family English Show`
- Screen spine detected: `landing -> map -> game -> victory`
- Core mechanics detected: `photo-word`, `word-photo`, `true-false`, `memory`, `listen`
- Persistent state: player name, score, stars, last mode
- Signature features: speech synthesis, top banner, map hub, soft feedback, stickers, sparkles, glossy glass panels
- Visual mood: affectionate, bright, low-pressure, candy-pop

### Source page B - Hunter academy

- Title: `Academia HUNTR/X Demon Hunter Math`
- Screen spine detected: `landing -> select -> game -> victory`
- Core mechanics detected: `sequence`, `cantinela`, `train`, `fingersum`, `plusjump`
- Persistent state: player name
- Signature features: hero selection, combo language, stage flash, burst overlays, particle canvas, victory poster
- Visual mood: dramatic, neon, momentum-heavy, concert energy

### Content base already extracted in project

`base_preguntas_ciencias_naturales.json` already contains a reusable question bank with:

- many `multiple_choice` prompts that map well to short game loops
- some `open_text` prompts that should be treated as future creative or free-response missions
- themes such as `cinco_sentidos`, `cuidado_sentidos`, `actividad_fisica`, `alimentacion`, and `repaso_final`

This means the project already has the raw content layer needed for future playable pages.

## Shared DNA to preserve

Both source pages prove the same structural truth:

1. A fantasy wrapper comes before the first exercise
2. Learning is delivered as short turns, not as a long sheet
3. Progress is always visible
4. Feedback is immediate after every move
5. A strong victory moment invites replay

These are the non-negotiable traits of the reusable system.

## Reusable spine

The common reusable spine is:

`landing -> briefing/select/map -> game -> victory`

Rules for the spine:

- `landing` always introduces mission, role, and reward
- `briefing`, `select`, and `map` are optional branch screens
- `game` is the stable shell where mechanics rotate
- `victory` is always explicit, never implied

## What must stay different per page

### Keep from `index.html`

- soft retry language
- cozy, affectionate tone
- map-as-exploration rhythm
- memory and listen loops as delight mechanics
- decorative celebration that feels safe and cute

### Keep from `index hunters moving spectacular.html`

- dramatic hero entry feeling
- companion or avatar selection
- combo and level framing
- strong reactive hit feedback
- concert-like victory energy

The reusable system must unify logic and contracts, not flatten identity.

## Layer model

The system should always separate these layers:

### 1. Content layer

- mission text
- prompts
- options
- answers
- praise and retry lines
- asset references

### 2. Theme layer

- fonts
- color tokens
- background strategy
- panel treatment
- celebration intensity
- optional audio hooks

### 3. Reward layer

- score
- stars
- combo
- progress bar
- toast text
- burst styling
- victory summary

### 4. Mechanics layer

- renderer by `mechanicId`
- input requirements
- answer validation
- reward hook
- retry behavior

### 5. Flow layer

- supported screens
- optional branches before game
- replay and continue behavior

## Mechanics equivalence table

| Source mechanic | Reusable category | Pedagogical job | Required inputs | Immediate feedback | Soft skin tone | Intense skin tone |
| --- | --- | --- | --- | --- | --- | --- |
| `photo-word` | Visual recognition | match image to label | prompt, options, answer, image | highlight + praise | "Nice match" | "Target locked" |
| `word-photo` | Guided target selection | choose correct visual target | prompt, options, answer | correct/wrong on card | "You found it" | "Marked" |
| `true-false` | Fast concept check | validate short statement | prompt, boolean answer | binary feedback | "Good catch" | "Stable / glitch" |
| `memory` | Reveal and reinforce | repeated exposure and matching | pair set | matched tiles + mini reward | sparkles | combo pulse |
| `listen` | Audio cue | connect sound to meaning | prompt audio hook, options, answer | replay + match | "Listen again" | "Follow the signal" |
| `sequence` | Order builder | process or timeline order | steps, correct order | chain validation | "You rebuilt it" | "Sequence restored" |
| `cantinela` | Quick choice | identify smallest / best / correct target | prompt, options, answer | instant tap feedback | "Pick the clue" | "Hit the mark" |
| `train` | Missing piece | fill one step or one number | prompt, options or input, answer | slot completion | "Car connected" | "Rail repaired" |
| `fingersum` | Visual arithmetic | combine quantities | prompt, options, answer | simple score jump | "Count and match" | "Power up" |
| `plusjump` | Step forward logic | next value / delta reasoning | prompt, options, answer | jump reward | "Keep going" | "Boost forward" |

## Mapping from `base_preguntas_ciencias_naturales.json`

### Good v1 fits

- `multiple_choice` with 2 options:
  - `true-false`
  - yes/no pairs
  - healthy/unhealthy
  - good/bad care habits

- `multiple_choice` with 3 to 5 options:
  - `cantinela`
  - `photo-word`
  - `word-photo`
  - `plusjump` style "choose the next or best"

### Good v1 with custom assets

- matching body parts to senses
- food category cards
- health habit recognition
- activity vs not-activity selection

### Better as future v2

- `open_text`
- `CreativeSceneCard` style prompts from earlier extraction notes
- drag/drop classification
- open drawing missions

For v1, open prompts should be stored as optional future missions rather than forced into the starter.

## Rules for future study pages

- Keep the loop structure before changing the theme
- Build around 3 to 5 short mechanics per page
- Use at least one delight mechanic such as `map`, `memory`, or `select`
- Keep mistakes local and recoverable
- Never end a round without a clear victory state

## Practical default for ciencias naturales

For future science pages, the system should default to:

- a mission wrapper
- one light branch screen before gameplay
- mostly `multiple_choice` content from the JSON base
- one soft reinforcement mechanic
- one progress bar plus either stars or combo
- a page-specific localStorage namespace to avoid collisions
