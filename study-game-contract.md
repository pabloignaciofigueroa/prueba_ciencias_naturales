# Study Game Contract

## Purpose

`STUDY_GAME_CONFIG` is the public contract for future standalone HTML study pages.

It must be expressive enough to represent:

- the soft `map + memory + listen` family style page
- the intense `select + combo + stage energy` hunter style page

It must remain framework-free and work in plain HTML, CSS, and JS.

## Top-level shape

```js
const STUDY_GAME_CONFIG = {
  meta: {},
  theme: {},
  flow: {},
  progression: {},
  feedback: {},
  mechanics: [],
  assets: {},
  mapNodes: [],
  helpers: [],
  futureContent: {}
};
```

## Required sections

### `meta`

Purpose: identity and mission wrapper.

```js
meta: {
  title: "Mission title",
  subject: "ciencias_naturales",
  fantasyWrapper: "Short mission fantasy",
  playerRole: "Explorer",
  subtitle: "Short supporting line"
}
```

Required fields:

- `title`
- `subject`
- `fantasyWrapper`
- `playerRole`

Optional fields:

- `subtitle`
- `goalLabel`
- `difficultyLabel`

### `theme`

Purpose: visual and emotional skin.

```js
theme: {
  skinId: "soft-map",
  tone: "soft", // "soft" or "intense"
  fonts: {
    display: "'Chewy', cursive",
    body: "'Baloo 2', sans-serif"
  },
  tokens: {
    bgDeep: "#10233b",
    bgMid: "#173a63",
    accentA: "#ffd86f",
    accentB: "#ff78c5",
    accentC: "#79f1ff",
    textMain: "#fffafc"
  },
  backgroundStrategy: "gradient-and-glow",
  panelStyle: "glass",
  celebrationIntensity: "soft",
  audioHooks: {
    bgm: [],
    sfx: {}
  }
}
```

Rules:

- `skinId` is page-specific
- `tone` drives copy intensity and celebration behavior
- `tokens` must be page-scoped, not global across all pages
- `audioHooks` may be empty, but the object should exist when audio is planned

### `flow`

Purpose: declare which screens are active.

```js
flow: {
  activeScreens: ["landing", "briefing", "map", "game", "victory"],
  startScreen: "landing",
  preGameScreen: "map",
  allowReplay: true
}
```

Supported screen ids:

- `landing`
- `briefing`
- `select`
- `map`
- `game`
- `victory`

Rules:

- `landing`, `game`, and `victory` are mandatory in v1
- `briefing`, `select`, and `map` are optional
- only one pre-game branch should be primary at a time

### `progression`

Purpose: state, scoring, and persistence.

```js
progression: {
  roundLength: 8,
  scorePerCorrect: 10,
  starStep: 1,
  comboEnabled: false,
  starsEnabled: true,
  progressStyle: "bar",
  storage: {
    namespace: "science-soft-map-v1",
    keys: {
      score: "score",
      stars: "stars",
      lastScreen: "lastScreen"
    }
  }
}
```

Rules:

- storage must be page-scoped through `storage.namespace`
- do not reuse one global key across different study pages
- `comboEnabled` and `starsEnabled` may coexist, but at least one progress signal should be visible

### `feedback`

Purpose: emotional response and end-of-round language.

```js
feedback: {
  praiseLines: ["Great rescue!", "Nice match!"],
  retryLines: ["Almost there.", "Try another clue."],
  victory: {
    title: "Mission complete",
    summary: "You restored the science path."
  }
}
```

Required:

- `praiseLines`
- `retryLines`
- `victory.title`
- `victory.summary`

### `mechanics`

Purpose: ordered deck of playable interactions.

Each item represents one round or one playable unit.

```js
mechanics: [
  {
    id: "m1",
    mechanicId: "photo-word",
    prompt: "Who uses the sense of sight?",
    subtitle: "Choose the best match.",
    options: [
      { id: "a", label: "Eyes" },
      { id: "b", label: "Ears" },
      { id: "c", label: "Nose" }
    ],
    answer: "a",
    rewardHook: "stars"
  }
]
```

Required per item:

- `id`
- `mechanicId`
- `prompt`
- `options` for choice mechanics
- `answer`

Optional per item:

- `subtitle`
- `image`
- `audio`
- `helperText`
- `pairs`
- `steps`
- `rewardHook`

Supported initial mechanic ids:

- `photo-word`
- `word-photo`
- `true-false`
- `memory`
- `listen`
- `sequence`
- `cantinela`
- `train`
- `fingersum`
- `plusjump`

## Mechanic data rules

### Generic choice mechanics

Use this shape for:

- `photo-word`
- `word-photo`
- `listen`
- `cantinela`
- `train`
- `fingersum`
- `plusjump`

```js
{
  mechanicId: "cantinela",
  prompt: "Pick the healthy snack.",
  options: [
    { id: "fruit", label: "Fruit" },
    { id: "chips", label: "Chips" },
    { id: "candy", label: "Candy" }
  ],
  answer: "fruit"
}
```

### `true-false`

```js
{
  mechanicId: "true-false",
  prompt: "The nose helps us smell.",
  answer: true
}
```

### `memory`

```js
{
  mechanicId: "memory",
  prompt: "Find the matching pairs.",
  pairs: [
    { id: "sight", left: "Vista", right: "Eyes" },
    { id: "hearing", left: "Oido", right: "Ears" }
  ]
}
```

### `sequence`

```js
{
  mechanicId: "sequence",
  prompt: "Rebuild the order.",
  steps: ["Observe", "Compare", "Classify"],
  answer: ["Observe", "Compare", "Classify"]
}
```

## `assets`

Purpose: non-text resources and fallbacks.

```js
assets: {
  stickers: [],
  portraits: [],
  backgrounds: [],
  audio: {
    bgm: [],
    sfx: {}
  },
  fallbacks: {
    avatarText: "OK"
  }
}
```

Rules:

- do not hardcode page assets inside engine logic
- keep paths relative to the standalone HTML when possible

## Optional sections

### `mapNodes`

Use when `map` is active.

```js
mapNodes: [
  { id: "node-1", label: "Sentidos", x: 18, y: 40, status: "active" },
  { id: "node-2", label: "Cuidado", x: 44, y: 25, status: "locked" }
]
```

### `helpers`

Use when `select` or `briefing` is active.

```js
helpers: [
  { id: "hero-1", name: "Mira", role: "Signal guide" },
  { id: "hero-2", name: "Rumi", role: "Stage spark" }
]
```

### `futureContent`

Use to preserve content not implemented in starter v1.

```js
futureContent: {
  openMissions: [],
  drawMissions: []
}
```

This is where `open_text` prompts from `base_preguntas_ciencias_naturales.json` should live for now.

## Adapter rules for `base_preguntas_ciencias_naturales.json`

### Direct v1 adapter

```js
{
  id: raw.id,
  mechanicId: pickMechanicFromPrompt(raw),
  prompt: raw.enunciado,
  options: raw.opciones.map((label, index) => ({ id: `${raw.id}-${index}`, label })),
  answer: findAnswerId(raw),
  tags: {
    tema: raw.tema,
    origenCard: raw.origen_card,
    origenTitulo: raw.origen_titulo
  }
}
```

### Suggested mapping defaults

- two-option `V/F` prompts -> `true-false`
- two-option care prompts -> `true-false` or `cantinela`
- short multiple choice prompts -> `cantinela`
- prompts with matching body part / label logic -> `photo-word` or `word-photo`
- process or ordered prompts -> `sequence`
- open text prompts -> `futureContent.openMissions`

## Two concrete config directions

### Soft family style

- `flow.activeScreens`: `landing`, `briefing`, `map`, `game`, `victory`
- `theme.tone`: `soft`
- `progression.comboEnabled`: `false`
- `progression.starsEnabled`: `true`
- mechanics focus: `photo-word`, `true-false`, `memory`, `listen`

### Intense hunter style

- `flow.activeScreens`: `landing`, `select`, `game`, `victory`
- `theme.tone`: `intense`
- `progression.comboEnabled`: `true`
- `progression.starsEnabled`: `true`
- mechanics focus: `sequence`, `cantinela`, `train`, `plusjump`

## Acceptance criteria

The contract is valid when:

- the same top-level shape can represent both source pages
- the starter can run a soft `map` variant and an intense `select/combo` variant
- page persistence remains scoped by page namespace
- new pages can be created by changing content, fantasy, assets, mechanics, and intensity without changing engine structure
