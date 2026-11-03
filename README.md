# DailyMate AI

A simple and professional student productivity assistant built with
**Next.js 16 + TypeScript + Tailwind CSS 4 + shadcn/ui**.

## Features

1. **Dashboard** — overview of today's progress, upcoming deadlines and study sessions
2. **Daily Tasks** — add / edit / delete / complete tasks with priority, date and time
3. **Assignment Deadline Tracker** — track courses, deadlines and submission status
4. **Study Planner** — weekly grid for scheduling focused study sessions
5. **Writing Helper** — outline, summarize, expand, rewrite and brainstorm on-device

All data is stored in **browser localStorage** — no backend or account needed.
The design uses a modern **blue and white** theme and is fully mobile responsive.

## Getting started

### Prerequisites

- Node.js 18+ (or [Bun](https://bun.sh) for faster installs)

### Install and run

```bash
# Install dependencies
npm install        # or: bun install

# Start the dev server
npm run dev        # or: bun run dev
```

Then open <http://localhost:3000> in your browser.

### Build for production

```bash
npm run build
npm run start
```

## Project structure

```
src/
  app/
    globals.css           # Blue & white theme (light + dark)
    layout.tsx            # Root layout with metadata
    page.tsx              # Main page (renders DailyMateApp)
  components/
    dailymate/
      daily-mate-app.tsx  # App shell: header, nav, footer
      dashboard.tsx       # Dashboard view
      daily-tasks.tsx     # Daily tasks view (CRUD)
      assignments.tsx     # Assignment tracker view (CRUD)
      study-planner.tsx   # Weekly study planner (CRUD)
      writing-helper.tsx  # Writing helper (5 on-device modes)
    ui/                   # shadcn/ui component library
  hooks/
    use-toast.ts          # Toast hook
    use-mobile.ts         # Mobile detection hook
  lib/
    storage.ts            # useLocalStorage hook + date helpers
    types.ts              # Shared TypeScript types
    utils.ts              # General utilities (cn)
    db.ts                 # Prisma client (unused, kept for reference)
```

## Tech notes

- **No database required** — everything lives in the browser via localStorage.
  `prisma/` and `src/lib/db.ts` are scaffolded but unused by this app.
- **SSR-safe localStorage** — implemented with `useSyncExternalStore`
  (the React 19 idiomatic pattern), so there are no hydration mismatches.
- **Cross-tab sync** — open the app in two tabs and changes propagate
  automatically via `storage` events.
- **Lint clean** — `npm run lint` passes with zero errors or warnings.

## Customization

- **Colors**: edit CSS variables in `src/app/globals.css` (`:root` and `.dark`).
- **Navigation items**: edit the `NAV` array in
  `src/components/dailymate/daily-mate-app.tsx`.
- **Writing helper logic**: the on-device text heuristics live at the bottom of
  `src/components/dailymate/writing-helper.tsx` and can be extended freely.
"# daliy-meta-ai" 
