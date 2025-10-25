# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

CanadaPrep is a static bilingual (English/French) website deployed via GitHub Pages. The site is in early development with placeholder content.

## Architecture

### Directory Structure

- `gh-pages/` - Contains all website source files that are deployed to GitHub Pages
  - Root level: English HTML pages (index.html, support.html, privacy.html)
  - `fr/` subdirectory: French translations of all pages
  - `styles.css` - Shared stylesheet used by both English and French pages

### Bilingual Architecture

The site uses a directory-based localization approach:
- English pages are at the root of `gh-pages/`
- French pages mirror the structure inside `gh-pages/fr/`
- French pages reference the stylesheet using relative path: `../styles.css`
- Language navigation is present on all pages with links to switch between English/French versions

### Page Structure

All pages follow a consistent template:
- Header with language navigation
- Main content area (currently placeholder comments)
- Footer with navigation links to Support and Privacy Policy pages

## Deployment

Deployment is automated via GitHub Actions workflow `.github/workflows/deploy-gh-pages.yml`:
- Triggers on pushes to `main` branch when files in `gh-pages/` change
- Can also be triggered manually via workflow_dispatch
- Deploys the `gh-pages/` directory to GitHub Pages

To trigger deployment:
```bash
git add gh-pages/
git commit -m "Update site content"
git push origin main
```

## Development

### Local Development

Since this is a static HTML site, you can preview it locally using any HTTP server:

```bash
# Using Python 3
cd gh-pages
python3 -m http.server 8000

# Using Node.js (if you have npx installed)
cd gh-pages
npx serve

# Then open http://localhost:8000 in your browser
```

### Adding New Pages

When adding new pages:
1. Create the English version in `gh-pages/`
2. Create the French version in `gh-pages/fr/`
3. Ensure both versions have proper language navigation
4. Update footer navigation on existing pages if needed
5. French pages must use `<html lang="fr">` and reference `../styles.css`
