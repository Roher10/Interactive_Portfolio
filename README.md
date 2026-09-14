# Roberto Hernandez Hoffmann — Portfolio

A kinetic, single-page portfolio: an interactive Three.js hexagonal
"brain-globe" hero that detonates on scroll into skill clusters (GSAP +
ScrollTrigger), velocity-driven kinetic type, and a fully mobile-animated
build. **Zero build step** — it's one static `index.html` with Three.js,
GSAP, and ScrollTrigger inlined directly into the file, plus the résumé PDF
served alongside it.

## Run it locally

No install, no build. Any static file server works, e.g.:

```bash
npx serve .
# or
python -m http.server 8000
```

Then open the printed local URL.

## Deploy: GitHub → Vercel

### 1. Push to GitHub

From this folder:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

(Create the empty repo on GitHub first — either on github.com via "New
repository", or with the GitHub CLI: `gh repo create <repo-name> --public
--source=. --remote=origin --push`.)

### 2. Import into Vercel

1. Go to [vercel.com/new](https://vercel.com/new) and sign in with GitHub.
2. Select this repository.
3. Framework preset: **Other** (Vercel auto-detects this correctly since
   there's no `package.json` — no build command, no output directory to set).
4. Click **Deploy**.

That's it — Vercel serves `index.html` and the PDF as static files. Every
push to `main` auto-deploys.

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire site — markup, CSS, and JS (Three.js, GSAP, ScrollTrigger inlined) |
| `Roberto_Hernandez_Hoffmann_Resume.pdf` | Downloadable résumé, linked from the nav and mobile drawer |
| `vercel.json` | Clean URLs + cache headers |
| `.gitignore` | Standard OS/editor noise |

## Notes

- All Résumé data is transcribed directly from the source PDF — no
  placeholder content.
- The page is self-contained by design (no CDN dependencies, no external
  requests besides Google Fonts), so it will keep working even if a
  dependency's CDN ever goes away.
- Respects `prefers-reduced-motion` and adapts the deconstruct/scroll
  choreography for narrow (mobile) viewports.
