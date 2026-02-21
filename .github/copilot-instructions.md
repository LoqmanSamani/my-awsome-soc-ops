# Soc Ops — Workspace Instructions

## Development Checklist (mandatory before every commit)

- [ ] `npm run lint` — passes clean
- [ ] `npm run build` — TypeScript compiles, Vite builds
- [ ] `npm run test` — all Vitest tests pass

## Stack

- React 19, TypeScript 5.9, Vite 7
- Tailwind CSS v4 (CSS-first: `@import "tailwindcss"` + `@theme` in `src/index.css`, no config file)
- Vitest 4 + jsdom + @testing-library/react
- Node 22+

## Architecture

```
src/
  App.tsx                  — Root: routes between start → game → bingo modal
  hooks/useBingoGame.ts    — Game state machine + localStorage persistence
  components/              — StartScreen, GameScreen, BingoBoard, BingoSquare, BingoModal
  data/questions.ts        — 24 icebreaker prompts + FREE_SPACE constant
  utils/bingoLogic.ts      — Pure functions: generateBoard, toggleSquare, checkBingo
  utils/bingoLogic.test.ts — Unit tests for all game logic
  types/index.ts           — BingoSquareData, BingoLine, GameState
```

## Conventions

- Functional components with hooks; no class components
- Types in `src/types/index.ts`; import with `import type`
- Game logic is pure (no React) in `utils/bingoLogic.ts` — test here first
- Tailwind v4: use `@theme` for design tokens, native opacity (`bg-black/50`), no legacy utilities
- ESLint: recommended TS rules + react-hooks + react-refresh
- Deploys to GitHub Pages via Actions on push to `main`
