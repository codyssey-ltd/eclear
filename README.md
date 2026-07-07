# eclear — Rich Text Sanitizer & Markdown Converter | Browser-Based HTML Cleaner

[![Browser support](https://img.shields.io/badge/browsers-Chrome%20Firefox%20Safari%20Edge-blue)](https://github.com/codyssey-ltd/eclear)
[![License: MIT](https://img.shields.io/badge/license-MIT-green)](https://github.com/codyssey-ltd/eclear/blob/main/LICENSE)
[![No server](https://img.shields.io/badge/architecture-100%25%20client--side-success)](#privacy)

> **Paste. Copy. Done.** — Clean rich text from dark themes, Word, Google Docs, and web pages in one keystroke.

**Repo:** [github.com/codyssey-ltd/eclear](https://github.com/codyssey-ltd/eclear)

## What is eclear?

**eclear** is a free, open-source **rich text sanitizer** that runs entirely in your browser. Paste messy content from Microsoft Word, Google Docs, VS Code, dark-themed editors, or any web page — eclear strips dark themes, inline styles, and junk markup, then copies clean rich text back to your clipboard in one keystroke.

**No installs. No accounts. No server. No tracking.** Just open the file and paste.

## Key Features

- 🎨 **Dark theme stripper** — removes hardcoded dark colors and backgrounds from copied text
- 📝 **Markdown to HTML converter** — paste markdown, get formatted rich text
- 📊 **Mermaid diagram renderer** — converts Mermaid.js flowcharts to PNG images for pasting anywhere
- 🧹 **HTML cleaner** — strips Word/Google Docs junk (`mso-*` styles, namespace tags, conditional comments)
- 🔒 **100% client-side** — no data leaves your browser, fully private
- 📋 **One-keystroke copy** — `Ctrl+C` copies cleaned HTML + plain text to clipboard
- 🔄 **Copy as Markdown** — `Ctrl+Shift+M` converts rendered HTML back to Markdown
- 📁 **Drag-and-drop files** — drop `.txt`, `.md`, `.html` files to process them
- 📐 **Responsive editor** — adjustable width with arrow keys
- 🔍 **Word count** — live word and character count in status bar

## Quick Start

1. **Download** [`html/index.html`](https://github.com/codyssey-ltd/eclear/blob/main/html/index.html) from this repo
2. **Open** it in any modern browser (Chrome, Firefox, Safari, Edge)
3. **Paste** — `Ctrl+V` or right-click → Paste
4. **Copy** — `Ctrl+C` — cleaned rich text is on your clipboard
5. **Paste** into Gmail, Outlook, BookStack, Slack, or anywhere

That's it. Three steps: **paste, copy, paste.**

## Use Cases

### Dark Theme → Email

Copied text from a dark editor (VS Code, Obsidian) into Gmail or Outlook and got unreadable dark-on-dark text? Paste into eclear → `Ctrl+C` → paste clean, light-theme text with formatting intact.

### Word / Google Docs Cleanup

Pasting from Word brings thousands of lines of Microsoft-specific XML and inline styles. eclear strips all `mso-*` styles, namespace tags, and conditional comments — paste clean HTML anywhere.

### Markdown → Rich Text

Have markdown (`**bold**`, `# headings`, `- lists`, `| tables |`) and need it as formatted rich text? Paste the markdown → eclear detects and converts it → `Ctrl+C` → paste into any rich text editor.

### Mermaid Diagrams → BookStack

BookStack doesn't render Mermaid diagrams natively. Copy your Mermaid source → paste into eclear (diagram renders to PNG) → `Ctrl+C` → paste into BookStack — the image is auto-uploaded. Works with flowcharts, sequence diagrams, Gantt charts, pie charts, and more.

### Web Page Content Extraction

Copied an article from a website and got tracking pixels, script tags, and site-specific styling? eclear removes all scripts, styles, and disallowed tags — paste only the content you want.

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+V` | Paste content into eclear |
| `Ctrl+C` | Copy cleaned content as rich text (HTML) |
| `Ctrl+Shift+M` | Copy cleaned content as Markdown |
| `Ctrl+Enter` | Re-clean current content and copy |
| `←` / `→` | Decrease / increase editor width |
| `?` | Show keyboard shortcut help |
| `Esc` | Close help / error overlay |

All shortcuts also have **clickable buttons** in the top bar for mouse users.

## What Gets Cleaned

**Stripped:**
- All inline styles except `text-align`
- `<script>`, `<style>`, `<meta>`, `<link>`, `<iframe>`, `<object>`, `<embed>`, `<svg>` tags
- Word/Google Docs namespace tags (`o:p`, `v:shape`, etc.)
- HTML comments and conditional comments
- Tracking pixels and hidden elements
- `javascript:` URLs and unsafe attributes

**Preserved:**
- Text formatting: bold, italic, underline, strikethrough, mark, sub, sup
- Headings (H1–H6)
- Lists (ordered, unordered, definition)
- Tables with full structure (thead, tbody, tr, td, th, caption)
- Links and images (including data URIs)
- Blockquotes, code blocks, preformatted text
- Paragraphs and line breaks

## Privacy

eclear is **100% client-side**. No server, no API calls, no data storage, no tracking. Everything runs in your browser via DOM manipulation. Your pasted content never leaves your device.

The only external dependency is the [Mermaid.js](https://mermaid.js.org/) library loaded from a CDN for diagram rendering. If the CDN is unavailable, mermaid blocks fall back to code blocks — all other features work fully offline.

## Browser Support

| Browser | Minimum Version |
|---------|----------------|
| Chrome | 76+ |
| Firefox | 90+ |
| Safari | 13.1+ |
| Edge | 79+ |

## Tech Stack

- **Vanilla JavaScript** — no frameworks, no build step
- **HTML5** — `contenteditable`, Clipboard API, Drag and Drop API
- **CSS3** — CSS variables, flexbox, animations
- **Mermaid.js v11** — diagram rendering (CDN-loaded, optional)
- **Playwright** — end-to-end test suite (42 tests)

## File Structure

```
eclear/
├── html/
│   └── index.html      # The entire application — HTML, CSS, and JS in one file
├── tests/
│   ├── e2e_features.mjs       # Feature test suite (34 tests)
│   ├── e2e_mermaid_errors.mjs # Mermaid error handling tests (8 tests)
│   └── mixed_content_test.txt # Comprehensive test content
└── README.md
```

## Development

```bash
# Run tests
cd eclear
python3 -m http.server 8765 --directory html
node tests/e2e_features.mjs
node tests/e2e_mermaid_errors.mjs

# Or just open html/index.html in your browser — no build needed
```

## FAQ

**Is eclear free?** Yes, open-source under MIT license.

**Does eclear store my data?** No. Everything runs in your browser. Nothing is sent to any server.

**Does eclear work offline?** Yes, except Mermaid diagram rendering which loads Mermaid.js from a CDN. All other features work fully offline.

**Can I use eclear with Gmail?** Yes — copy from eclear and paste directly into Gmail's compose window. The cleaned HTML is preserved.

**Can I use eclear with BookStack?** Yes — eclear was built with BookStack in mind. Mermaid diagrams are rendered to PNG images that BookStack auto-uploads on paste.

## License

MIT — see [LICENSE](LICENSE) file.
