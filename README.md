# codernoteswebsite

Static marketing site for [codernotes](https://github.com/Tijani127/codernotes).
No build step, no framework, no dependencies — plain HTML, CSS and one SVG.

```
index.html          the whole page
assets/style.css    all styling, custom properties for the palette
assets/mark.svg     the logo, matching the geometry in src/brand.cpp
assets/app-dark.png screenshot, Midnight theme
assets/app-light.png screenshot, Daylight theme
.nojekyll           stops GitHub Pages from running Jekyll over the files
```

## Local preview

There is nothing to install. Open `index.html`, or serve the folder:

```sh
python -m http.server 8000
```

## Deploying to GitHub Pages

Any static host works. Two ways with GitHub:

**A. Its own repository** (the site gets `https://<user>.github.io/<repo>/`)

```sh
cd codernoteswebsite
git init -b main
git add .
git commit -m "Marketing site"
git remote add origin https://github.com/<user>/<repo>.git
git push -u origin main
```

Then in the repo: **Settings → Pages → Source: Deploy from a branch → `main` / `/ (root)`**.

**B. Inside the codernotes repository**

```sh
# from a clone of codernotes
cp -r ../codernoteswebsite/. docs/
git add docs
git commit -m "Add marketing site"
git push
```

Then **Settings → Pages → Source: Deploy from a branch → `main` / `/docs`**.

## Changing things

- **Version numbers and download links** — the `v0.1.0` string and the three
  `releases/download/...` URLs appear in the hero eyebrow and the download
  cards. Update them together when a new tag ships.
- **Colours** — everything is a custom property at the top of `assets/style.css`.
  They were taken from the app's own Midnight palette so the site and the app
  match.
- **Language list** — the chips in the `#run` section are hand-maintained and
  currently match `src/runner.cpp`. There are 19.
- **Screenshots** — regenerate from the app and copy them over:

  ```sh
  codernotes --size 1600 900 --screenshot assets/app-dark.png
  ```

  Set the theme first by writing `midnight` or `daylight` into
  `notes/theme.txt`.
