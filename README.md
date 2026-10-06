# PDF Merge

A privacy-first PDF merging tool built as a single static file for GitHub Pages. It lets you upload, reorder, sort, and merge multiple PDF documents directly in your browser with no upload, no backend, and no installation.

## What it does

- Merges two or more PDF files locally in the browser
- Supports drag-and-drop, click-to-select, and paste-from-clipboard workflows
- Reorders files by drag, move buttons, or sort options
- Detects duplicates by file name and size
- Saves the final merged file with a custom output name
- Works in a dark or light theme and is mobile-friendly

## Privacy guarantee

Files are never uploaded to a server. All PDF reading, page merging, and file generation happen locally in the browser. The app uses `pdf-lib` and a Web Worker so the UI remains responsive while processing is happening on the user’s device only.

## Deploy on GitHub Pages

1. Upload the repository files to GitHub.
2. Open the repository in GitHub.
3. Go to `Settings` → `Pages`.
4. Under `Build and deployment`, select:
   - Source: `Deploy from a branch`
   - Branch: `main`
   - Folder: `/ (root)`
5. Save.
6. GitHub will publish the site at:
   `https://<username>.github.io/<repo>/`

## Browser support notes

The app is designed for modern desktop and mobile browsers, including:
- Chrome
- Edge
- Firefox
- Safari
- iOS Safari
- Android Chrome

The project includes a download fallback for mobile browsers so the final merged PDF remains easy to save even when automatic downloads are restricted.

## How it works

- `pdf-lib` is loaded from jsDelivr.
- A single `index.html` file contains the full landing page and merging app.
- The merge job runs in a Web Worker so the UI stays responsive.
- If the worker fails or stalls, the app falls back to a main-thread merge automatically.
- The final PDF is converted to a Blob and downloaded through a persistent anchor for compatibility with mobile Safari.

## Extra features included

- Landing page with product-style overview and sections
- Secure local workflow messaging
- Duplicate detection and skipped-file notices
- Theme persistence with localStorage
- Output filename persistence with localStorage
- Drag-to-reorder file list
- Mobile-friendly layout and controls

## Files included

- `index.html` — complete landing page and PDF merge tool
- `README.md` — project documentation
- `LICENSE` — MIT license
