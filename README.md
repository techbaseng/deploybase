# Deploybase — AI Deployment Directory

A directory site listing every deployed Claude Project (custom AI system) built and run by Babatunde Awoyemi / Techbase Consultant Services — a one line summary of what each one does, who it serves, and a direct link out to that project's own live site, where the full write-up and the exact instructions/knowledge files live.

Live structure, once hosted on GitHub Pages:

```
/                          → hub (index.html) — the registry grid
/assets/css/style.css      → design system for the hub
/assets/js/main.js         → renders the hub grid from the PROJECTS array
/assets/data/projects.js   → the registry data — edit this to add/remove/reorder cards
```

Every project, including live tools, is its own separate repo now — nothing is nested inside `deploybase` itself. (Earlier versions of this repo held the Educator AI Toolkit under `/toolkit/`; it has since been split into two standalone tool sites, `exam-revision-generator` and `lesson-note-generator`, each its own repo, same as every `AGENT.0N` entry.)

Every card on the hub links straight to that project's own repo/site (e.g. `https://babatundeawo.github.io/classpulse-national/`) rather than to an internal detail page here. Deploybase itself only ever holds the summary card, never the full description — that lives on the project's own site, alongside its exact custom instructions and knowledge files, copyable directly from the page.

The registry data is a plain `.js` file (not `.json`) loaded with a normal `<script>` tag, on purpose — that means the site renders correctly even when opened directly as a local file (double-clicking `index.html`), not just when served over http/GitHub Pages. `fetch()`-ing a local JSON file is blocked by the browser in that case, which is why an earlier version of this site showed an empty grid when opened locally.

## Adding a new project later

1. **Build the project its own site.** Give it its own repo (`babatundeawo.github.io/<slug>/` once GitHub Pages is enabled), with a distinct colour palette and typography direction — no two project sites should look like reskins of each other. Include a "Get this project" section with the exact custom instructions and knowledge file(s), copyable from the page.
2. **Add a card entry.** Open `assets/data/projects.js` and add one object to the `PROJECTS` array with `id`, `status` (`"active"` or `"tool"`), `name`, `role`, `summary`, `stack`, `href` pointing at the new site's live URL, and `"external": true`. The hub grid picks it up automatically — no HTML edit needed on `index.html`.
3. **Status labels.** `"active"` (`AGENT.0N`) is a Claude Project write-up — a case study of an AI system Babatunde runs. `"tool"` (`TOOL.0N`) is a live, self-serve tool meant for someone else to pick up and use directly, like the Exam & Revision Generator or the Weekly Lesson Note Generator.

## Linking rules

Per the standing portfolio-wide convention, this site's footer only ever links to three places: the personal portfolio (babatundeawo.github.io), the personal GitHub profile, and the Techbase org profile. It doesn't cross-link to any sibling project repo, and neither does any individual project site — each of those follows the same three-link footer rule independently.

## Hosting

Static site, no build step. Enable GitHub Pages on this repo (root or `/docs`, depending on where it's pushed) and it's live. Each of the 9 linked projects is its own separate repo with GitHub Pages enabled the same way.
