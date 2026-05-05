# Hharpp Bookkeeping Services Page — Claude Code Project Brief

## Task
Read `content.json` completely. Read `PROMPT.md` completely. Build `bookkeeping.html`.

## Output file
`bookkeeping.html` — production-ready, self-contained HTML file.

## Non-negotiable constraints
- Single file. Everything inline — all CSS in one `<style>` block in `<head>`, all JS in one `<script>` block before `</body>`.
- Google Fonts via `@import url(...)` inside the `<style>` block. No external CSS files.
- All 8 schema blocks as separate `<script type="application/ld+json">` tags in `<head>`.
- No broken `<img>` tags — styled `<div>` placeholders only for any images not yet available.
- No `#` placeholder hrefs on internal links. Every link must point to its real path.
- No placeholder copy. Every word comes from `content.json`. No invented content.
- Responsive: works at 375px (mobile), 768px (tablet), 1280px+ (desktop).
- WCAG AA color contrast on all text.
- Run the 20-point verification checklist in PROMPT.md before saving the file.
