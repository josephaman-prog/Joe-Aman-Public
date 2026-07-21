# Joe Aman — Public Pages

Astro site for publishing Paper-generated visual boards and other public
pages to Cloudflare Pages.

Live site:
https://joe-aman-public.pages.dev/

## Workflow

Use this flow when turning a Paper board (or any one-off page) into a hosted
page.

1. Export or inspect the Paper board.
   - Prefer real HTML/CSS when the board should stay responsive, selectable, or interactive.
   - Use a static image export when exact visual fidelity matters more than responsive behavior.

2. Add the page in `src/pages/`.
   - Example: `src/pages/japan-vacation-2026.astro`
   - The file path controls the URL. `src/pages/example.astro` becomes `/example/`.

3. Put static assets in `public/`.
   - Local images go in `public/assets/`.
   - Reference them with root-relative URLs like `/assets/example.webp`.
   - Paper-hosted image URLs can be used for tests, but local assets are more durable for long-term hosting.

4. Add the page to the homepage list.
   - `src/pages/index.astro` is a landing page linking every published page — add a card for the new page.

5. Verify locally.

   ```sh
   npm install
   npm run build
   npm run dev
   ```

6. Commit and push to GitHub.

   ```sh
   git add .
   git commit -m "Add new page"
   git push
   ```

7. Cloudflare Pages redeploys from `main`.
   - Framework preset: Astro
   - Build command: `npm run build`
   - Build output directory: `dist`
   - Root directory: blank

## Current Routes

- `/` — landing page listing all published pages
- `/japan-vacation-2026/` — Japan Vacation 2026 board
- `/i-love-melisa-lim/` — I Love Melisa Lim heart

## Customizing Pages

Basic layout, typography, responsive behavior, and animation can live directly in `.astro` files with HTML, CSS, and small scripts.

For richer behavior, use Astro islands:

- Add vanilla JavaScript for simple click behavior, toggles, modals, filters, or scroll effects.
- Add a framework integration like React when a section needs complex state, reusable UI controls, or animation libraries.
- Keep Paper-derived visuals as presentational Astro components, then layer interactivity around them.

## Node

Cloudflare Pages uses the Node version in `.node-version`.
