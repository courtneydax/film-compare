# Film Compare

An HTML tool for comparing photos side-by-side.

## Usage

Open `index.html` directly in a browser — no server, no build step, no external dependencies. Works fully offline via `file://`.

1. **Choose Folder** loads every image in a folder. If it has subfolders, check **Include subfolders** first (in the header) to pull images from them too — otherwise only top-level images load.
2. Each image appears as a card with an editable label (defaults to filename) and a **★** button to mark it the **reference** image — the reference pins to the front of the grid and gets a highlighted border.
3. Click any thumbnail to enter **compare mode**.

## Compare mode

- Two-plus-panel layout: the **reference stays locked** on the left; the **Compare: 1/2/3** dropdown in the header controls how many other images sit alongside it.
- Drag to pan, scroll to zoom — pan/zoom is synced across all visible panels so you can hold the same crop (e.g. to check grain) while flipping between stocks.
- **Prev/Next buttons, the slider, or ←/→ arrow keys** step the visible window through the non-reference images.
- **Click any non-reference slot** to open a picker modal and manually assign a specific image to that slot. A pinned slot shows a 📌 badge; click the badge to release it. **Pinned slots are skipped by Prev/Next/the slider** — stepping only cycles the remaining unpinned slots, so you can lock a couple of images in place and still step through the rest.
- Esc closes compare mode (or the picker modal, if that's open).

## Files

- `index.html` — the main app (HTML/CSS/JS)
- `help.html` — film stock reference page, linked from the header. Contains, top to bottom:
  - Reference table — per-stock type/ISO/ratio, signature look, best-for use case, suggested short T2I prompt
  - Showcase prompts — one full scene prompt per stock, each scene deliberately chosen to expose that stock's signature trait (e.g. point-source lights at night for Cinestill's halation, complementary orange/green landscape for Velvia's saturation)
  - T2I / I2I prompt template note (same trait descriptor, different lead-in verb)
  - Model notes — T2I: Chroma, Grok Imagine, Seedream, Qwen Image, Krea 2 Turbo, Z-Image Turbo. I2I: FireRed, Qwen-Image-Edit, Grok, Seedream v5. Based on vendor docs/community reports, not hands-on tested in this tool.
- `examples/` — example generated images for the showcase prompts in `help.html`, referenced directly by the showcase cards.

## Notes

- No persistence — reloading the page clears everything; it's meant for one comparison session at a time.
- Nothing is uploaded anywhere — images are read locally via the browser's File System APIs and never leave the page.
