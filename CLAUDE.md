# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Tech Stack

This is a React Router v7 application with TypeScript, deployed on Cloudflare Pages/Workers:
- **Framework**: React Router v7 with SSR
- **Runtime**: Cloudflare Workers
- **Styling**: TailwindCSS v4 with shadcn/ui components
- **Tooling**: Biome for linting/formatting, Lefthook for git hooks

## Development Commands

```bash
# Start development server with HMR
npm run dev

# Build for production
npm run build

# Preview production build locally
npm run preview

# Type checking (includes Cloudflare types generation)
npm run typecheck

# Linting and formatting
npm run lint        # Lint with auto-fix
npm run format      # Format code
npm run check       # Run both lint and format

# Deployment
npm run deploy      # Build and deploy to Cloudflare
```

## Architecture

- **Entry Points**: 
  - `app/entry.server.tsx` - Server-side rendering entry
  - `workers/app.ts` - Cloudflare Worker entry
- **Routes**: File-based routing in `app/routes/`
- **Components**: UI components go in `app/components/` (shadcn/ui ready)
- **Utilities**: Shared utilities in `app/lib/`

## Cloudflare Integration

- Uses `@cloudflare/vite-plugin` for Cloudflare Workers compatibility
- Wrangler config in `wrangler.jsonc`
- Types generated automatically via `cf-typegen` script
- Environment variables configured in `wrangler.jsonc` vars section

## Code Style

- **Linter**: Biome with recommended rules
- **Format**: 2-space indentation, single quotes for JS/TS
- **Git Hooks**: Pre-commit hook runs Biome check on staged files
- **Ignored**: CSS files excluded from Biome, some generated files ignored

## shadcn/ui Setup

- Style: "new-york" variant
- Components path: `@/components/ui`
- Utils path: `@/lib/utils`
- CSS variables enabled with zinc base color
- Lucide icons library