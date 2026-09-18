# Project page

Plain static site — no build step, no framework. `index.html` + `static/css/style.css`.

## Preview locally

```
cd website && python -m http.server 8000
```
then open http://localhost:8000.

## Host on GitHub Pages

Option A (separate repo, cleanest): create a repo, e.g. `<user>/wireless-anc`, copy the contents of `website/` to its
root, push, then Settings → Pages → Deploy from branch `main` / root. URL: `https://<user>.github.io/wireless-anc/`.

Option B (this repo): Settings → Pages → Deploy from branch `main`, folder `/website`
(GitHub only offers `/` or `/docs`, so either rename this folder to `docs/` or push it to a `gh-pages` branch).

## Adding audio samples

- Put clips in `static/audio/sim/` and `static/audio/real/` (WAV keeps the HF content honest; a 5 s clip at 16 kHz is
  ~160 KB, so no need for MP3). Keep the same peak gain for every row in a table so loudness differences are real.
- Spectrogram PNGs go in `static/images/spec/{sim,real}/` (~260 px wide at display; 800 px source is plenty).
- Copy the `<div class="sample"> … </div>` block in `index.html` once per scene and fill in the paths and dB numbers.
  Rows to keep: No ANC · Direct filter prediction · Ours · Causal upper bound. The `ours` row class gives the highlight.
- `preload="none"` on `<audio>` keeps the page from downloading every clip on load.

## TODO before submission

- Author links, venue line, arXiv/PDF and code button URLs (search `TODO` in `index.html`).
- BibTeX entry.
- Scene descriptions and reduction numbers per sample.
