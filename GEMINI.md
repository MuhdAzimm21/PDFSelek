# Project Overview

This project, "PDFSelek," is a purely client-side web application for performing PDF manipulations. It is designed as a Multi-Page Application (MPA), where each of the three core features is a self-contained single-page app within its own HTML file.

**Core Features:**
*   **Merge:** Combines multiple PDF files into one. (`merge.html`)
*   **Split:** Extracts selected pages from a single PDF. (`split.html`)
*   **Split & Merge:** Allows selecting and combining pages from multiple PDF files. (`split-and-merge.html`)

**Technologies & Architecture:**
*   **Frontend:** The application is built with plain HTML, CSS, and JavaScript, using Bootstrap 5 for styling.
*   **PDF Processing:** All PDF processing happens in the user's browser, powered by two key libraries loaded from a CDN:
    *   **`pdf.js`**: Used to render previews of PDF pages onto HTML `<canvas>` elements.
    *   **`pdf-lib`**: Used for the core PDF manipulation logic (creating, copying, and saving documents).
*   **Architecture:** The key architectural characteristic is that all JavaScript logic for a feature is embedded directly within its corresponding HTML file in `<script>` tags. The `script.js` file is not used for any core functionality. This has resulted in significant code duplication across the feature pages.

---

# Building and Running

This is a static web project with no build process.

**Running Locally:**
1.  Serve the project directory using a local web server. A simple one can be started with Python:
    ```bash
    python -m http.server
    ```
2.  Open your web browser and navigate to `http://localhost:8000` (or the appropriate port).

You can also open the `index.html` file directly in a web browser, but using a local server is recommended to avoid potential issues with file access security policies in some browsers.

**Deployment:**
The project is set up for continuous deployment to GitHub Pages. The `.github/workflows/static.yml` file defines a GitHub Action that deploys the entire repository as a static site whenever changes are pushed to the `main` branch.

---

# Development Conventions

*   **File Structure:** Each major feature (merge, split) resides entirely within its own HTML file (e.g., `merge.html`). This file contains the page structure, UI, and all the necessary inline JavaScript logic.
*   **JavaScript:** Follow the established pattern of placing all feature-specific JavaScript inside a `<script>` tag at the bottom of the relevant HTML file. Do not add shared logic to `script.js`, as it is not part of the core application.
*   **Dependencies:** External libraries like Bootstrap, `pdf.js`, and `pdf-lib` are included via CDN links in the HTML files. There is no `package.json` or other package manager.
*   **Styling:** All CSS is located in `style.css`. The file is organized with comments that delineate styles for global elements and specific feature pages.
*   **Code Duplication:** Be aware that the current architecture leads to duplicated code (e.g., drag-and-drop file handling, PDF preview rendering). When adding or modifying functionality, it may be necessary to apply similar changes to multiple HTML files.
