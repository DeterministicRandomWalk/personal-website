# Process Log

## 2026-06-03

- Confirmed the project goal: build a personal blog website using Astro and Cloudflare Pages.
- Confirmed a dedicated personal GitHub/Cloudflare identity will be used for this project.
- Checked the local JavaScript toolchain.
- Found that the current Astro scaffolder requires Node.js `>=22.12.0`.
- Tried to install a newer Node.js version with Homebrew, but the install failed while installing a dependency.
- Decision: use an available newer Node.js runtime for local scaffolding and builds until the system Node.js version is upgraded.

## 2026-06-04

- Scaffolded an Astro blog project with the official blog template.
- Decision: moved the generated Astro project files into the workspace root so the repository root can also be the Cloudflare Pages project root.
- Personalized the scaffold:
  - Set the site title to `Deterministic Random Walk`.
  - Replaced starter homepage copy with personal-blog copy.
  - Replaced the placeholder about page with a short profile page.
  - Replaced Astro starter social links with the public GitHub profile.
  - Removed sample starter blog posts and added `hello-world.md` as the first post.
- Replaced the generated Astro starter README with project-specific development and Cloudflare deployment notes.
- Verified the site with `npm run build`.
  - Result: success.
  - Generated pages: `/`, `/about/`, `/blog/`, `/blog/hello-world/`, `/rss.xml`, and sitemap output.
- Started the local Astro dev server and performed a browser smoke test.
  - Homepage rendered the personalized title, navigation, and intro copy.
  - Blog index rendered the `Hello, world` post.
  - `/blog/hello-world/` rendered the first post content.
  - `/about/` rendered the profile content.
- Initialized a local git repository in the project root.
- Confirmed `.gitignore` excludes generated/dependency folders:
  - `dist/`
  - `.astro/`
  - `node_modules/`
- Decision: configured this repository only, not global git settings, to use the dedicated website GitHub identity.
- Set the initial branch name to `main`.
- Created the GitHub repository for the project under the dedicated personal GitHub account.
- Added the GitHub remote and pushed local `main`.
- Decision: use SSH for pushes after adding this machine's public key to the dedicated GitHub account.
- Verified SSH authentication identifies the dedicated GitHub account.
- User noticed that public repo files exposed a local machine path containing the real macOS username.
- Decision: sanitize public files and git history to avoid publishing real names, local paths, private account details, and machine-specific runtime paths.
- Removed direct email links from the public site for now to reduce account correlation and spam exposure.
