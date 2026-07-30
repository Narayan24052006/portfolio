# Portfolio — Chinmai Sri Narayana Kothamasu

A single-file, no-build-step 3D portfolio. Everything (HTML, CSS, JS) lives in
`index.html`. The only other file is your résumé PDF under `assets/`.

The hero has a small interactive 3D "signal network" (built with Three.js,
loaded from a CDN) — nodes connected to their nearest neighbours with pulses
travelling along the edges, and a gentle tilt on mouse move. It's a nod to the
signal/edge-AI work in the Projects section rather than a generic decoration.

## Run it locally

No install, no build. Because the script uses ES module imports, open it
through a local server rather than double-clicking the file:

```bash
# any of these work
python3 -m http.server 8000
# or
npx serve .
```

Then visit `http://localhost:8000`.

## Deploy it (pick one — all free)

**Vercel**
1. Push this folder to a GitHub repo.
2. Go to vercel.com → "Add New Project" → import the repo.
3. Framework preset: "Other". No build command needed. Deploy.

**Netlify**
1. Go to app.netlify.com → "Add new site" → "Deploy manually".
2. Drag this whole folder into the upload area. Done — you get a live URL instantly.

**GitHub Pages**
1. Push this folder to a GitHub repo (root, or a `/docs` folder).
2. Repo → Settings → Pages → set source to that branch/folder.
3. Your site is live at `https://<username>.github.io/<repo>/`.

Once deployed, put the URL on your resume and LinkedIn — and update the
`og:url` meta tag in `index.html` for nicer link previews.

## Customize

Everything is in `index.html`, organized top to bottom in the same order as
the page. A few things worth knowing:

- **Résumé button**: points to `assets/resume.pdf`. Replace that file with
  a newer version whenever you update your resume — the link doesn't need
  to change.
- **Project cards**: each `<article class="project-card">` in the Projects
  section is self-contained. To add a project, copy one block and edit the
  tags, title, description, and stack line. If you add public repos for
  these projects, consider linking each card title to its repo.
- **Colors / type**: all defined once as CSS custom properties at the top of
  `<style>` (search for `:root`). Change `--amber` to re-theme the whole
  accent color in one place.
- **3D node count / behavior**: search for `const COUNT = 64` in the script
  to adjust density, or `PULSE_COUNT` to change how many signal pulses
  animate at once.

## Notes on what was intentionally left out

- **Phone number** isn't displayed on the page, to avoid it being scraped by
  bots once the site is public. Email and LinkedIn are the contact paths
  instead. If you'd rather show it, add a line under the contact links in
  the `<footer id="contact">` section.
- **Reduced motion**: the 3D animation and scroll reveals both respect
  `prefers-reduced-motion`, so the page stays fully usable (and calmer) for
  anyone with that OS setting on.
