# Workspace Hub — Print, Notes & Layout Tools

A pure client-side suite of printable document and visual layout tools with zero build steps. Launch any tool directly from the minimalist hub (`index.html`).

---

## 📁 Repository Structure

```text
clever-borg/
├── index.html          # Minimalist hub page with direct cards to all 3 tools
├── notes.html          # A4 Markdown PDF Generator (single-file binary-search pagination engine)
├── images.html         # PrintStudio — Interactive HTML5 canvas image print layout studio
├── legacy/             # Classic multi-file 2-in-1 A4 Markdown PDF generator
│   ├── index.html      # Legacy app entry point
│   ├── app.js          # Linear node-splitting & DOM measurement pagination engine
│   ├── style.css       # Screen preview & @media print styles
│   └── sample.md       # Default study guide markdown sample
└── README.md           # Project documentation
```

---

## 🛠️ Included Tools

### 1. Notes (`notes.html`) — A4 Markdown PDF
A self-contained, single-file Markdown-to-A4 pagination engine designed for high-density cheat sheets and revision notes:
- **Multi-Column A4 Layouts**: Choose between `1-in-1 (Portrait)`, `2-in-1 (Landscape)`, or `3-in-1 (Landscape)` logical pages per physical A4 sheet.
- **Binary-Search Node Splitting ($O(\log N)$)**: Uses an off-screen `#measurer` container and `binarySplit()` to split overflowing paragraphs (by word), `<pre><code>` blocks (by line), `<blockquote>` blocks, and `<table>` rows (automatically preserving `<thead>` headers across column breaks).
- **Zero Inner Scrollbars**: Enforces strict containment on screen and in print.
- **Rich Content Support**:
  - **Math**: Inline (`$...$`) and display (`$$...$$`) LaTeX via KaTeX.
  - **Code Highlighting**: Syntax highlighting via Highlight.js (`github.min.css`).
  - **Diagrams**: Mermaid.js (`mermaid`) block rendering into SVG.
  - **Extended Markdown**: GitHub-style alerts (`[!NOTE]`, `[!TIP]`, `[!IMPORTANT]`, `[!WARNING]`, `[!CAUTION]`), `==highlights==`, `~subscript~`, `^superscript^`, footnotes (`[^1]`), and emoji shortcodes.
- **Controls**: Font size (`6px`–`18px` in `0.5px` steps), toggleable page numbers (`Page #`), orphan heading prevention (`No Orphans`), zoom controls (`-`, `+`, `Fit`, `Ctrl + Wheel`), and native `window.print()` PDF export.

### 2. Images (`images.html`) — PrintStudio
An interactive HTML5 `<canvas>` (`#studioCanvas`) print layout studio for arranging, cropping, and exporting multi-image sheets:
- **Canvas Aspect Ratios & Sizes**: `A4 Portrait`, `A4 Landscape`, `3:4`, `4:3`, `16:9`, `9:16`, and `1:1`.
- **Print DPI Presets**: `Eco (72 DPI)`, `Low (150 DPI)`, `Medium (300 DPI)`, and `High (600 DPI)` with live pixel dimension readouts.
- **Interactive Manipulation**: Drag-and-drop image import, on-demand sample image loader, snap grids (`2×2`, `4×4`), layer ordering, rotation, aspect-ratio locking, and interactive canvas pan/zoom.
- **Export Formats**: Direct client-side export to **Printable PDF** (via `jsPDF`), **Lossless PNG**, or **High-quality JPEG**.

### 3. Legacy (`legacy/index.html`) — Classic 2-in-1 A4 Markdown PDF
The original multi-file (`index.html`, `app.js`, `style.css`, `sample.md`) implementation of the A4 Markdown PDF generator:
- Includes additional preprocessors for Markdown definition lists (`: definition`) and abbreviations (`*[ABBR]: Full Text`).
- Automatically fetches `sample.md` when served over HTTP/HTTPS.

---

## 🚀 Usage

1. **Direct Browser Open**: Open `index.html`, `notes.html`, or `images.html` directly in any modern browser.
2. **Local Development Server** (required only if you want `legacy/index.html` to auto-fetch `legacy/sample.md`):
   ```bash
   npx serve .
   # or
   npx wrangler pages dev .
   ```
