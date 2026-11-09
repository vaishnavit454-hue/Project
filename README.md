[README.md](https://github.com/user-attachments/files/34563428/README.md)
# Margin — Local Knowledge Retrieval for Writers

**Margin** is a zero-backend, distraction-free, local-only knowledge retrieval tool for writers. It runs entirely in the browser using HTML, CSS, and Vanilla JavaScript with zero external dependencies, zero CDNs, and zero third-party APIs. All data is saved directly to your browser's `localStorage` under `collider_clips`.

---

## 🌟 Features

### 1. Distraction-Free Split-Screen Interface
- **Obsidian / Notion-inspired aesthetic**: Built with an off-white background (`#F7FAFC`), dark slate text (`#2D3748`), subtle borders, and system typography.
- **60% Left Canvas**: Borderless writing and drafting area with real-time word count, character count, and reading time estimation.
- **40% Right Collision Board**: Subtly shaded column (`#EDF2F7`) where matched links and quotes surface live as you write.
- **Empty State**: Displays *"Start typing to surface relevant highlights."* when no overlaps are found.

### 2. Local-Only Collision Engine
- **Debounced Trigger**: Automatically fires a collision scan 500ms after you pause typing or paste a draft.
- **Stop-Words Filter**: Hardcoded array of 50+ common English stop words (`the`, `and`, `is`, `in`, `about`, etc.).
- **Heavy Words Extraction**: Strips punctuation and stop-words to isolate high-value conceptual keywords.
- **Overlap Scoring**: Counts how many heavy words from the draft appear in each saved snippet in `localStorage.collider_clips`.
- **Top 3 Cards**: Ranks and displays the top 3 highest-scoring snippets on the Collision Board.
- **Visual Overlap Highlighting**: Uses regex to wrap matching words inside `<mark class="highlight-match">` tags (soft yellow background `#FEF08A`) so you immediately see why a link surfaced.

### 3. Knowledge Storage & Bookmarklet Simulator
- **Data Structure**: Stores an array of clip objects in `localStorage`:
  ```json
  [
    {
      "id": "clip_1710000000000_abc",
      "url": "https://paulgraham.com/words.html",
      "highlighted_text": "Writing doesn't just communicate ideas; it generates them...",
      "date_saved": "2026-11-08T04:47:16.000Z"
    }
  ]
  ```
- **Settings / Test Data Modal**: Accessible from the top bar to manually add URLs and snippets, delete individual clips, or reset to 7 curated sample highlights (Vannevar Bush, Paul Graham, Tiago Forte, Steven Johnson, Andy Matuschak, Joan Didion, William Zinsser).
- **Real Browser Bookmarklet**: One-click copyable bookmarklet to capture highlights from any website directly into Margin while reading.

---

## 🚀 How to Run

Because Margin has zero backend and zero external dependencies:

### Option A: Open directly in your browser
Simply double-click or open the file in Chrome, Safari, Firefox, or Edge:
```bash
open /Users/pihu/.gemini/antigravity/scratch/margin/index.html
```

### Option B: Local HTTP server
If you prefer running via a local web server:
```bash
cd /Users/pihu/.gemini/antigravity/scratch/margin
python3 -m http.server 8080
```
Then visit `http://localhost:8080` in your web browser.

---

## 🧪 Quick Test Walkthrough

1. Open `index.html`.
2. Notice the Collision Board displays the required empty state: *"Start typing to surface relevant highlights."*
3. Click the **"Sample Drafts"** dropdown in the top bar and select **"Vannevar Bush & Memex"** (or paste your own writing).
4. Watch the 500ms debounce trigger: the status changes to *"Colliding..."* and then surfaces cards ranked by overlap score.
5. Notice the soft yellow `<mark>` highlights identifying words like `memex`, `memory`, `thinking`, etc.
6. Click **"Settings / Test Data"** in the top bar to add your own snippets, view existing saved clips, or copy the browser bookmarklet!
