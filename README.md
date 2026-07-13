# Deploybase — AI Deployment Directory

A directory site listing every deployed Claude Project (custom AI system) built and run by Babatunde Awoyemi / Techbase Consultant Services — what each one does, who it serves, and how a session with it works. One entry links out to a live public tool instead of a description page.

Live structure, once hosted on GitHub Pages:

```
/                          → hub (index.html) — the registry grid
/projects/*.html           → one detail page per AI system
/toolkit/                  → Educator AI Toolkit, a separate live site, kept as-is
/assets/css/style.css      → shared design system for the hub + all detail pages
/assets/js/main.js         → renders the hub grid from the PROJECTS array
/assets/data/projects.js   → the registry data — edit this to add/remove/reorder cards
```

The registry data is a plain `.js` file (not `.json`) loaded with a normal `<script>` tag, on purpose — that means the site renders correctly even when opened directly as a local file (double-clicking `index.html`), not just when served over http/GitHub Pages. `fetch()`-ing a local JSON file is blocked by the browser in that case, which is why an earlier version of this site showed an empty grid when opened locally.

## Adding a new project later

1. **Write the detail page.** Copy any file in `/projects/` as a starting template — the page structure (header, meta grid, numbered content blocks, step list, rule grid, closing CTA band, footer) is reusable. Swap in the new project's content and give it the next `AGENT.0N` id.
2. **Add a card entry.** Open `assets/data/projects.js` and add one object to the `PROJECTS` array with `id`, `status` (`"active"` or `"tool"`), `name`, `role`, `summary`, `stack`, and `href` pointing to the new page. The hub grid picks it up automatically — no HTML edit needed on `index.html`.
3. **Live tools vs. description pages.** If the new project is itself a hosted tool (like the Educator AI Toolkit), drop its site in a subfolder here, set `"status": "tool"` and `"external": true` in its entry, and point `href` at its own `index.html`.

## Linking rules

Per the standing portfolio-wide convention, this site's footer only ever links to three places: the personal portfolio (babatundeawo.github.io), the personal GitHub profile, and the Techbase org profile. It doesn't cross-link to any sibling project repo.

## Hosting

Static site, no build step. Enable GitHub Pages on this repo (root or `/docs`, depending on where it's pushed) and it's live.
