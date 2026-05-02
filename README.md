# KATDL

AI consulting and software engineering for health sciences. Built with [Hugo](https://gohugo.io/).

## Development

Prerequisites: [Hugo Extended](https://gohugo.io/installation/) (v0.145.0+)

```bash
hugo server
```

The site will be available at `http://localhost:1313/` with live reload.

## Build

```bash
hugo --gc --minify
```

Output goes to `./public/`.

## Deployment

Pushes to `main` trigger a GitHub Actions workflow that builds and deploys to GitHub Pages at [katdl.com](https://katdl.com).
