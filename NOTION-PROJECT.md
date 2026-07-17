# FAIL Academy Interactive

> Kompletní projektová karta pro Notion → **Projekty**  
> Aktualizace: 17. 7. 2026

---

## Status
**Live** — sdílený odkaz funguje

## Odkazy
- **Appka:** https://zdenekmelotik-max.github.io/fail-academy-interactive/
- **GitHub (publish / Pages):** https://github.com/zdenekmelotik-max/fail-academy-interactive
- **Lokální zdroj:** `~/Projects/fail-learning-app`
- **Dokumentace:** `docs/PROJECT.md` (v lokálním repo i v publish repo)

## Účel
Interaktivní učení kurzu **Future AI Leader (FAIL)** pro mě + 2 kolegy. Materiály z Google Drive (`treninky/FAIL Attachments`) převedené do profesionálního UI. Bez přihlášení, bez sledování progressu.

## Proč ne Google Drive odkaz
Drive často zobrazí HTML jako text. Proto běží na **GitHub Pages**.

---

## Co je hotové (MVP)

### Navigace & UI
- 10 modulů + úvod „jak web používat“
- Responzivní menu (desktop sidebar / mobil Menu)
- Předchozí / další modul, Zpět na přehled
- Žádný raw markdown jako hlavní obsah

### Videa
- YouTube embed u modulů + bonus sessions

### Prezentace (PDF) — 2026-07-17
- Vestavěný **PDF.js** prohlížeč v stránce
- Tlačítka **Předchozí / Další** + počítadlo slidů
- **Celá obrazovka** (nový tab) + **Stáhnout PDF**
- Lazy load: PDF se načte až po otevření modulu
- Absolutní URL (oprava 404 bez trailing slash)
- Start na slidu 1, zoom podle šířky okna

### Prompty
- Karty s textem promptu + **Kopírovat**

### Procvičení
- Úkoly jako checklist tipů
- Kvízy: po odeslání správné **zeleně ✓**, špatné **červeně ✗**
- Výsledek se neukládá

---

## Stack
| Vrstva | Technologie |
|--------|-------------|
| Publish | Static HTML + CSS + JS |
| PDF | Mozilla PDF.js |
| Hosting | GitHub Pages |
| Build | `scripts/build-shareable-html.mjs` |
| Data | Drive FAIL Attachments + `course.json` |

Publish repo obsahuje: `index.html`, `materials/modul-N/`, `pdfjs/`.

---

## Jak aktualizovat appku
1. Upravit materiály na Google Drive
2. V `fail-learning-app`: `npm run import-content`
3. `node scripts/build-shareable-html.mjs`
4. V `dist/deploy`: `git add -A && git commit -m "…" && git push`
5. Po nasazení: hard refresh (Cmd+Shift+R)

---

## Sdílení s kolegy
Poslat jen: https://zdenekmelotik-max.github.io/fail-academy-interactive/

---

## Záměrně není
- Progress / společné skóre
- Login / Google Auth
- Firebase / backend
- Raw markdown jako hlavní UX

## Fáze 2 (backlog)
- Auth / privátní přístup
- Lepší ručně kurátorované kvízy
- Fulltext search napříč moduly
- Automatický Drive → build sync

---

## Vlastnictví
- GitHub: `zdenekmelotik-max`
- Materiály: Google Drive `zdenek.melotik@gmail.com` → treninky/FAIL Attachments
