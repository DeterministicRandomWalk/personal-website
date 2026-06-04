# Personal Website

Astro personal website and blog for `DeterministicRandomWalk`.

## Local Development

This project currently requires Node.js `>=22.12.0`, matching Astro's current engine requirement.

Install or select a compatible Node.js version, then run:

```sh
npm install
npm run dev
```

## Commands

| Command | Action |
| :-- | :-- |
| `npm run dev` | Start the local development server. |
| `npm run build` | Build the production site into `dist/`. |
| `npm run preview` | Preview the production build locally. |
| `npm run astro -- --help` | Show Astro CLI help. |

## Blog Posts

Blog posts live in `src/content/blog/` as Markdown or MDX files.

Each post should include frontmatter like:

```md
---
title: 'Post title'
description: 'Short description for previews and SEO.'
pubDate: 'Jun 04 2026'
heroImage: '../../assets/blog-placeholder-1.jpg'
---
```

## Deployment Plan

Target hosting: Cloudflare Pages.

Expected Cloudflare build settings:

| Setting | Value |
| :-- | :-- |
| Framework preset | Astro |
| Build command | `npm run build` |
| Build output directory | `dist` |
| Node version | `22.12.0` or newer |

The final production `site` URL in `astro.config.mjs` should be updated after the Cloudflare Pages URL or custom domain is known.
