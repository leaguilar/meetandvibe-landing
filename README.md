# meet&vibe

The published website for **meetandvibe.com**, served by GitHub Pages from the `main` branch.

This repository holds only the built site. Its source, with the build scripts and tests, lives in the `site/` folder of the meetandvibe repository. `CNAME` sets the custom domain and `.nojekyll` makes GitHub Pages serve the files as they are.

## Publish an update

1. In the meetandvibe repository, run `npm ci` and `npm run build` inside `site/`.
2. Here, delete everything except `CNAME`, `.nojekyll`, `.gitignore` and this README.
3. Copy the contents of `site/dist/` into this folder.
4. Commit and push to `main`. GitHub Pages publishes within a few minutes.

## Preview locally

```sh
python3 -m http.server 4173 --bind 0.0.0.0
```
