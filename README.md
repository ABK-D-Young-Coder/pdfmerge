# PDF Merge

A lightweight browser-only PDF merge tool that combines multiple PDF files locally in the browser. It runs inside a Web Worker, keeps all processing on-device, and downloads the merged result as a PDF without requiring any backend or build tools.

## Privacy guarantee

Files are never uploaded to a server. The app reads PDFs in the browser, merges them locally with `pdf-lib`, and keeps the generated result in memory until you download it. Nothing leaves your device during the merge process.

## Deploy on GitHub Pages

1. Create a new GitHub repository or use an existing one.
2. Add a file named `index.html` at the repository root.
3. Commit and push the file to the default branch.
4. Open the repository in GitHub.
5. Go to `Settings` → `Pages`.
6. Under `Build and deployment`, set:
   - Source: `Deploy from a branch`
   - Branch: `main` (or the branch you use)
   - Folder: `/ (root)`
7. Save the settings.
8. After GitHub Pages finishes publishing, the app will be available at:
   `https://<username>.github.io/<repo>/`

## Browser support notes

This app is designed to work in modern desktop and mobile browsers, including:
- Chrome
- Edge
- Firefox
- Safari
- iOS Safari
- Mobile Chrome on Android

The code uses standard browser APIs, Web Workers, Blob URLs, and `pdf-lib`. Some browser-specific download behavior is handled with a persistent download link to make the flow work reliably on mobile Safari.

## How it works

- `pdf-lib` loads from jsDelivr and is used to create a new PDF document, copy pages from each input PDF, and save the merged output.
- Merging runs in a Web Worker so the browser UI stays responsive while large files are processed.
- The worker is created from an inline Blob URL inside the single `index.html` file, so no separate worker file is needed.
- If the worker fails, stalls, or never responds, the app automatically falls back to a main-thread merge after a 20-second watchdog timer.
- The merged file is exposed as a Blob URL, and a persistent download link is displayed so the user can click to save the result. A hidden anchor also attempts a direct auto-download when possible.

## Files included

- `index.html` — complete application
- `README.md` — project documentation
- `LICENSE` — MIT license

## Notes

This project is intentionally static and dependency-free apart from the CDN-hosted `pdf-lib` script. It is built to run as a GitHub Pages site with no build step, bundler, or server-side code.
