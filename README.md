# Agentic Coding @ Mor — Training Deck

Self-contained HTML training deck cho toàn bộ developer Mor về quy trình **Agentic Coding** — spec-driven, TDD-first, human-gate.

🎬 **Live deck:** https://mor-nhatlq.github.io/AI-Process-Presentation/

## Files

| File | Purpose |
|---|---|
| `index.html` | Single-file slide deck (Reveal.js + Mermaid v11 + base64 assets). Deploy GitHub Pages |
| `speaker-notes.md` | Companion presenter doc — talking points + Q&A buffer cho 14 slides |

## Present locally

```bash
open index.html
```

Hoặc serve qua HTTP để speaker view (`S` key) hoạt động:

```bash
python3 -m http.server 8000
# → http://localhost:8000/
```

## Keyboard shortcuts

| Key | Action |
|---|---|
| `→` `←` `Space` | Next / Prev slide |
| `F` | Fullscreen |
| `S` | Speaker view (notes + timer) |
| `Esc` / `O` | Slide overview |
| `B` / `.` | Black screen pause |
| `?` | Help |

## Content overview

14 slides covering:

1. Title hero
2. 3 nguyên tắc cốt lõi (Spec-first · Human-gate · TDD)
3. Quy trình chung — Workflow Requirement → Workflow Code
4. Vai trò trong team (4 personas)
5. Workflow Requirement diagram
6. Workflow Requirement skill map
7. Human Review Gate (NOT-OK loop + 2 cơ chế chặn)
8. Workflow Code diagram
9. Workflow Code skill map
10. TDD cycle (Red → Green → Refactor → Regression)
11. Toolkit · 4 plugin (`spec` · `superpowers` · `deep-review` · `docs-hero`)
12. Use case phổ biến — decision tree
13. Anti-pattern · Tối kị không được làm
14. Adoption roadmap (Pilot → Training → Adapting → Rollout)

## Tech stack

- [Reveal.js v5](https://revealjs.com/) — slide framework
- [Mermaid v11](https://mermaid.js.org/) — diagrams (3 inline)
- [Prism.js](https://prismjs.com/) — code syntax highlight
- 2 workflow PNG embedded base64 (resized 1920px)
- MOR brand: blue `#1E40AF` · orange `#F97316` · gold `#F59E0B`

Single-file HTML — toàn bộ inline (CSS/JS/images base64 + CDN abs URLs).

## Plugin source

Companion plugins repo: [`mor-duongmh/claude-plugins`](https://github.com/mor-duongmh/claude-plugins) — `spec`, `superpowers`, `deep-review`, `docs-hero`.
