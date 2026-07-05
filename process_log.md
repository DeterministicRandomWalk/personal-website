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
- Added a privacy checklist to `AGENTS.md` requiring a sensitive-string scan before commits, pushes, or deployments.
- Checked official Astro and Cloudflare documentation for Cloudflare Pages deployment settings.
  - Production branch: `main`
  - Build command: `npm run build`
  - Build output directory: `dist`
  - Cloudflare Pages v3 build image uses Node.js 22 by default for new projects.
- Decision: connect the GitHub repository through the Cloudflare dashboard rather than adding Cloudflare-specific runtime code, because the current site is static Astro output and does not need the Cloudflare adapter.
- First Cloudflare Pages deployment attempt cloned the repository and successfully ran `npm run build`.
- Deployment failed during asset validation because Cloudflare looked for an output directory named `npm run build`.
  - Diagnosis: the Cloudflare build output directory field was configured incorrectly.
  - Required fix: set Build command to `npm run build` and Build output directory / Build directory to `dist`.
- Cloudflare Pages deployment succeeded after correcting the build output directory.
- Cloudflare assigned the default production URL `personal-website-c80.pages.dev`.
- Decision needed: either rename the Cloudflare Pages project for a nicer free `pages.dev` subdomain or attach a custom domain.
- Decision: rename the Cloudflare Pages project to target the free production URL `deterministic-random-walk.pages.dev`.
- Renaming the Cloudflare Pages project display name did not change the assigned `pages.dev` hostname.
- Checked Cloudflare's known-issues documentation and found that `*.pages.dev` subdomains cannot be changed after project creation.
- Decision: because this Pages project is brand new and has no custom domain, the clean fix is to delete and recreate the Cloudflare Pages project with project name `deterministic-random-walk` during initial setup.
- Deleted the original Cloudflare Pages project and recreated it with project name `deterministic-random-walk`.
- New production URL: `https://deterministic-random-walk.pages.dev`.
- Verified the new URL returns HTTP 200.
- Updated `astro.config.mjs` `site` value to the new production URL so generated sitemap/canonical metadata use the correct domain.
- Added the first real series article as linked Chinese and English blog posts.
  - Chinese: `/blog/why-this-series-exists-zh/`
  - English: `/blog/why-this-series-exists-en/`
- Added optional blog post language metadata so translated posts can render with the correct HTML `lang` attribute.
- Removed the large placeholder hero image from the bilingual series introduction posts.
- Replaced the outdated series outline with the updated main-series and bonus-essay tables in both Chinese and English.
- Added subtle responsive table styling to blog posts.
- Verified locally that the bilingual posts no longer render hero images and each contains the updated main-series and bonus-essay tables.
- Pushed the article update to GitHub.
- Production still served the previous article version after waiting, so an empty commit was pushed to trigger Cloudflare Pages.
- Production still served the previous version after the trigger commit.
  - Next action: check Cloudflare Pages Deployments for the latest commit and retry/deploy from the dashboard if automatic deployments are paused, missing, queued, or failed.
- Added the provided series illustration as `src/assets/series-00-pipeline-illustration.png`.
- Reintroduced images for the bilingual Part 0 posts using the provided illustration.
- Adjusted blog post and blog index image rendering to preserve natural aspect ratios and keep article images modest rather than full-width banners.
- Removed the starter `Hello, world` blog post.
- Rewrote the About page to introduce the site as a personal blog focused on the intersection of asset management and production-grade AI systems for investment workflows.
- Refined blog article design for a cleaner, less colorful reading experience:
  - Title and date now lead the article before any image.
  - Article images are smaller illustrations rather than banner-like hero images.
  - Markdown tables have visible frames, cell borders, and horizontal scrolling on small screens.
  - Blockquotes are quieter callout blocks.
  - Chinese posts use a Chinese-first font stack.
- Simplified the blog index from large image cards to a compact reading list.
- Updated `AGENTS.md` privacy requirements to require blog-content scans for company names, person names, product/vendor names, and other identifying details before publication.
- Added a note to the About page that the blog first took shape in March 2026 and has been kept updated.
- Sanitized existing Part 0 posts to remove named model/research/person references from the published blog text.
- Added Part 1 as linked Chinese and English posts.
  - Chinese: `/blog/impossible-task-zh/`
  - English: `/blog/impossible-task-en/`
- Anonymized Part 1 content before publication by replacing named companies, vendors, product names, model names, and tool/framework names with generic descriptions.
- Removed named vendor fonts from the Chinese article font stack so generated CSS stays aligned with the no-company-name publishing rule.
- Swapped series illustrations:
  - Part 0 now uses `src/assets/series-00-introduction-illustration.png`.
  - Part 1 now uses the previous pig/chicks illustration as `src/assets/series-01-impossible-task-illustration.png`.
- Adjusted article heading hierarchy so `h3` subsection headings render smaller than `h2` section headings.
- Added Part 2 as linked Chinese and English posts.
  - Chinese: `/blog/seven-layers-zh/`
  - English: `/blog/seven-layers-en/`
- Added the provided Part 2 illustration as `src/assets/series-02-seven-layers-illustration.png`.
- Linked Part 1 forward to Part 2.
- Anonymized Part 2 content before publication by replacing named organizations, roles, model/product names, frameworks, and specific vendors with generic descriptions.
- Updated the Part 2 token-cost estimate in both Chinese and English to reflect URL plus surrounding paragraph context, changing the rough per-URL estimate from 200 tokens to 2000 tokens.
- Updated the Part 2 per-company URL scale in both Chinese and English from 1000 to 10000 reviewed URLs, and adjusted the token-cost estimate to 20 million tokens per company before multiplying by portfolio scale.
- Added Part 3A as linked Chinese and English posts.
  - Chinese: `/blog/llm-shines-agents-destroy-zh/`
  - English: `/blog/llm-shines-agents-destroy-en/`
- Added the provided Part 3A illustration as `src/assets/series-03a-llm-shines-illustration.jpeg`.
- Linked Part 2 forward to Part 3A.
- Anonymized Part 3A content before publication by replacing named people, organizations, products, browser frameworks, and specific vendor examples with generic descriptions.
- Generalized the homepage platform/deployment wording so the public site does not display hosting-provider names unnecessarily.
- Stripped EXIF metadata from the Part 3A illustration before publication to remove device model, software version, and capture timestamp.
- Added Part 3B as linked Chinese and English posts.
  - Chinese: `/blog/agents-destroy-orchestration-zh/`
  - English: `/blog/agents-destroy-orchestration-en/`
- Added the provided Part 3B illustration as `src/assets/series-03b-agents-destroy-illustration.jpeg`.
- Stripped EXIF metadata from the Part 3B illustration before publication.
- Linked Part 3A forward to Part 3B.
- Anonymized Part 3B content before publication by replacing named organizations, cloud vendors, model names, browser frameworks, parsing libraries, operating systems, and company examples with generic descriptions while retaining public technical standards such as `robots.txt`.
- Reworked the homepage introduction around the "deterministic random walk" metaphor:
  - Life, markets, and human systems move through randomness.
  - Investment modernization with AI needs probabilistic judgment combined with deterministic engineering.
  - The homepage now links directly to Blog and About without repeating the large site title.
- Added the provided homepage artwork as `src/assets/home-deterministic-random-walk-art.png`.
- Stripped metadata/profile information from the homepage artwork before publication and described the image without publishing family-identifying details.
- Added visible RSS links to the main navigation, footer, and homepage while keeping the existing RSS metadata in `BaseHead`.
- Revised the homepage introduction to use a more professional positioning statement around markets, investment process, probabilistic models, and deterministic engineering.
- Removed the About page hero image and the short conversational opening so the page stays text-focused.
- Added a homepage featured-series block linking to Part 0 through Part 3B in both English and Chinese.
- Reworked the blog index into separate English Series and 中文系列 sections so translated posts are grouped instead of interleaved.
- Added an internal interpersonal publication review that preserves sharp criticism of systems and technical claims while requiring real colleague anecdotes to be vague, non-identifiable, carefully paraphrased, and manually approved.
- Removed a specific internal-team reference from the future Part 11 description in both Chinese and English.
- Removed external source links from all published bilingual posts to reduce cross-platform identity correlation risk.
- Re-edited the English series as an independent public edition: preserved the technical arguments and failure mechanisms while generalizing exact project scale, organizational context, timelines, internal incidents, colleague anecdotes, and operational constants that could identify a workplace or team.
- Added a permanent publishing rule requiring every future English post to be independently edited as a technically substantive, de-identified public edition rather than a direct translation.
- Added Part 4 as linked Chinese and independently edited English posts.
  - Chinese: `/blog/honest-comparison-zh/`
  - English: `/blog/honest-comparison-en/`
- Added the provided Part 4 illustration as `src/assets/series-04-honest-comparison-illustration.jpeg` and removed its embedded device and capture metadata.
- Reframed Part 4's numerical comparison as an explicit order-of-magnitude model rather than publishing internal billing claims, exact workplace scale, identifiable incidents, named organizations, products, companies, or people.
- Restored the Chinese Part 4 close to the author's original full-detail version after manual review. Kept its illustrative figures and named public tools, while generalizing only the cloud provider and the country/industry identity of one parameter-loop incident.
- Constrained article tables to their content width so detailed comparison tables scroll internally instead of widening the page on mobile.
- Recalibrated the English privacy policy after the previous pass removed too much detail.
  - English posts now preserve the author's structure, narrative, technical figures, public examples, and sentence-level argument.
  - Privacy edits are limited to traceable identifiers and phrases, including workplace or department names, identifiable colleague details or quotations, country-and-industry incident combinations, private vendors or clients, and cloud-provider names.
- Restored English Parts 0 through 3B close to their original detailed versions while keeping external source links removed and retaining only narrow anonymization edits.
- Rebuilt English Part 4 as a full-detail version of the article rather than a shortened public abstract.
  - Preserved the cost tables, scale estimates, reliability calculation, public tool examples, and engineering details.
  - Kept the cloud provider unnamed and described the parameter-loop incident only as occurring on a large enterprise website.
- Fixed the article container box sizing so long, table-heavy posts remain within the mobile viewport while their tables and code blocks scroll internally.
- Adjusted the mobile navigation to use a compact two-row layout, preventing the site title and four internal links from overflowing narrow screens.

## 2026-06-11

- Verified the research claims for Part 5A against current primary sources from METR, Anthropic, and the cited arXiv paper.
- Corrected the METR figures to the May 2026 v1.1 estimates and added METR's stated benchmark-scope and uncertainty caveats.
- Preserved the article's central reliability-cliff argument while making clear that time horizon does not directly equal hours of a real engineer's job replaced.
- Added Part 5A as linked Chinese and English posts.
  - Chinese: `/blog/research-data-zh/`
  - English: `/blog/research-data-en/`
- Kept the English version close to the Chinese article's structure, detail, examples, and tone.
- Reused the already sanitized homepage artwork for Part 5A rather than creating a duplicate image file.
- Linked Part 4 forward to Part 5A and added Part 5A to the homepage and bilingual blog ordering.
- Verified the Part 5B research and framework claims against the cited primary papers, official talks/posts, and survey results.
- Corrected four details before publication review:
  - SWE-CI reports two Claude Opus models above a 0.50 zero-regression rate, not one.
  - The Stack Overflow 84% figure means respondents who use or plan to use AI tools.
  - Tobi Lütke helped popularize `context engineering`; the term was not attributed to him as its originator.
  - The METR reference remains aligned with Part 5A's corrected approximately 12-hour estimate.
- Added Part 5B as linked Chinese and English drafts.
  - Chinese: `/blog/research-frameworks-zh/`
  - English: `/blog/research-frameworks-en/`
- Preserved the Chinese article's structure, examples, technical detail, and tone in the English version.
- Generalized two potentially traceable incident details: the named jurisdiction comparison and the industry-specific website with session parameters.
- Added and sanitized the supplied Part 5B illustration as `src/assets/series-05b-research-frameworks-illustration.jpg`.
- Linked Part 5A forward to Part 5B and added Part 5B to the homepage and bilingual blog ordering.

## 2026-06-18

- Verified Part 6's current company, workforce, and macro-scenario claims against company announcements, regulatory filings, primary research, and clearly labeled analyst estimates.
- Kept distinct evidence categories separate in the article:
  - confirmed workforce actions,
  - company-stated AI rationale,
  - simultaneous AI investment without a direct replacement claim,
  - analyst or media inference.
- Updated the Oracle section so the 20,000–30,000 figure is presented as an unconfirmed analyst/media estimate rather than a confirmed company total.
- Removed the outdated Meta planning-language example rather than publishing a claim that had changed by June 2026.
- Added Part 6 as linked Chinese and English drafts.
  - Chinese: `/blog/leverage-gap-zh/`
  - English: `/blog/leverage-gap-en/`
- Preserved the article's argument, organizational examples, technical details, scale figures, and junior-career discussion in the English version.
- Narrowly anonymized the internal automation-tool anecdote by removing the tool nickname, meeting duration, license cost, department structure, and ending detail while preserving the substantive comparison.
- Added and sanitized the supplied Part 6 illustration as `src/assets/series-06-leverage-gap-illustration.jpg`.
- Linked Part 5B forward to Part 6 and added Part 6 to the homepage and bilingual blog ordering.
- Restored the Chinese Part 6 close to the author's supplied draft and rebuilt the English edition as a close translation.
- Completed factual, privacy, re-identification, interpersonal, and rendered-page review before publication.
- Added an `Authorial preservation` rule to `AGENTS.md` so future bilingual posts retain the approved Chinese text and receive only local factual or privacy edits.

## 2026-06-19

- Added Part 7 as linked Chinese and English drafts.
  - Chinese: `/blog/context-accumulation-zh/`
  - English: `/blog/context-accumulation-en/`
- Preserved the supplied Chinese draft's structure, chronology, metaphors, examples, emotional texture, and argument.
- Completed the factual, privacy, interpersonal, and rendered-page review.
- Added and sanitized the supplied Part 7 flower image as `src/assets/series-07-context-accumulation.jpg`.
- Linked Part 6 forward to Part 7 and added Part 7 to the homepage and bilingual blog ordering.

## 2026-06-20

- Added Part 8A as linked Chinese and English drafts.
  - Chinese: `/blog/delegation-problem-zh/`
  - English: `/blog/delegation-problem-en/`
- Preserved the supplied Chinese draft's structure and argument while applying local privacy/factual edits.
- Added and sanitized the supplied Part 8A construction image as `src/assets/series-08a-delegation-problem.jpg`.
- Linked Part 7 forward to Part 8A and added Part 8A to the homepage and bilingual blog ordering.

## 2026-06-21

- Added Part 8B as linked Chinese and English drafts.
  - Chinese: `/blog/autonomy-spectrum-zh/`
  - English: `/blog/autonomy-spectrum-en/`
- Preserved the supplied Chinese draft's layered autonomy framework, tables, examples, and closing argument.
- Added and sanitized the supplied Part 8B illustration as `src/assets/series-08b-autonomy-spectrum.jpg`.
- Linked Part 8A forward to Part 8B and added Part 8B to the homepage and bilingual blog ordering.

## 2026-06-22

- Added Part 9 as linked Chinese and English drafts.
  - Chinese: `/blog/other-extreme-zh/`
  - English: `/blog/other-extreme-en/`
- Preserved the supplied Chinese draft's mirror-argument structure about anti-hype, LeCun, research judgment, and product value.
- Added and sanitized the supplied Part 9 illustration as `src/assets/series-09-other-extreme.jpg`.
- Linked Part 8B forward to Part 9 and added Part 9 to the homepage and bilingual blog ordering.

## 2026-06-23

- Added Part 10 as linked Chinese and English drafts.
  - Chinese: `/blog/two-rooms-zh/`
  - English: `/blog/two-rooms-en/`
- Preserved the supplied Chinese draft's two-room structure, investment-industry analogy, and audience-specific guidance.
- Applied a local privacy edit to avoid implying one identifiable internal collision.
- Added and sanitized the supplied Part 10 illustration as `src/assets/series-10-two-rooms.jpg`.
- Linked Part 9 forward to Part 10 and added Part 10 to the homepage and bilingual blog ordering.

## 2026-06-24

- Added Part 11 as linked Chinese and English drafts.
  - Chinese: `/blog/evidence-zh/`
  - English: `/blog/evidence-en/`
- Preserved the supplied Chinese draft's evidence structure, production-system argument, and series-closing review.
- Kept the local privacy edit that generalizes the specific investment-team type while preserving the timing, person-role, and vendor details requested by the author.
- Added and sanitized the supplied Part 11 illustration as `src/assets/series-11-evidence.jpg`.
- Linked Part 10 forward to Part 11 and added Part 11 to the homepage and bilingual blog ordering.

## 2026-06-25

- Added Bonus A as linked Chinese and English drafts.
  - Chinese: `/blog/rebuttal-zh/`
  - English: `/blog/rebuttal-en/`
- Preserved the supplied Chinese draft's Karpathy-test structure, eight-counterargument sequence, and judgment-vs-balance closing argument.
- Kept the same local privacy generalization for the specific investment-team type used in Part 11.
- Added and sanitized the supplied Bonus A illustration as `src/assets/series-bonus-a-rebuttal.jpg`.
- Linked Part 11 forward to Bonus A and added Bonus A to the homepage and bilingual blog ordering.

## 2026-06-26

- Added Bonus B as linked Chinese and English drafts.
  - Chinese: `/blog/understand-systems-zh/`
  - English: `/blog/understand-systems-en/`
- Preserved the supplied Chinese draft's learning/delegation argument, nine concrete failure examples, and sheepdog closing metaphor.
- Paraphrased near-verbatim colleague remarks in the coding-agent anecdote while preserving the substantive point about AI-coding misunderstanding.
- Added and sanitized the supplied Bonus B illustration as `src/assets/series-bonus-b-understand-systems.jpg`.
- Linked Bonus A to Bonus B and added Bonus B to the homepage and bilingual blog ordering.
