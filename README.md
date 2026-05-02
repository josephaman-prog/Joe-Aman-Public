# Japan Vacation Test

Astro site for publishing Paper-generated visual boards to Cloudflare Pages.

Live site:
https://japan-vacation-test.pages.dev/

## Workflow

Use this flow when turning a Paper board into a hosted page.

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

4. Choose the default homepage behavior.
   - The current homepage redirects to `/japan-vacation-2026/`.
   - Update `public/_redirects` when a different board should become the default page.

5. Verify locally.

   ```sh
   npm install
   npm run build
   npm run dev
   ```

6. Commit and push to GitHub.

   ```sh
   git add .
   git commit -m "Add new Paper visual"
   git push
   ```

7. Cloudflare Pages redeploys from `main`.
   - Framework preset: Astro
   - Build command: `npm run build`
   - Build output directory: `dist`
   - Root directory: blank

## Current Routes

- `/` redirects to `/japan-vacation-2026/`
- `/japan-vacation-2026/` displays the Japan Vacation 2026 board

## Customizing Pages

Basic layout, typography, responsive behavior, and animation can live directly in `.astro` files with HTML, CSS, and small scripts.

For richer behavior, use Astro islands:

- Add vanilla JavaScript for simple click behavior, toggles, modals, filters, or scroll effects.
- Add a framework integration like React when a section needs complex state, reusable UI controls, or animation libraries.
- Keep Paper-derived visuals as presentational Astro components, then layer interactivity around them.

Good candidates for Astro-side enhancements:

- Clickable itinerary cards
- Expand/collapse day details
- Image lightboxes
- Route-map hotspots
- Smooth entrance animations
- Mobile-specific controls
- Data-driven rendering from a JSON itinerary file

## Node

Cloudflare Pages uses the Node version in `.node-version`.
