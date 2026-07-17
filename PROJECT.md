# FAIL Academy — projektová dokumentace

| Pole | Hodnota |
|------|---------|
| **Název** | FAIL Academy Interactive |
| **Účel** | Interaktivní učení programu Future AI Leader (FAIL) pro sebe + 2 kolegy |
| **Status** | Live (sdílený odkaz) |
| **Živá appka** | https://zdenekmelotik-max.github.io/fail-academy-interactive/ |
| **GitHub (publish)** | https://github.com/zdenekmelotik-max/fail-academy-interactive |
| **Lokální zdroj** | `~/Projects/fail-learning-app` |
| **Zdrojové materiály** | Google Drive → `treninky/FAIL Attachments` |
| **Jazyk** | Čeština |
| **Poslední update** | 2026-07-17 — listování PDF prezentací přímo v stránce |

---

## Shrnutí

Jednostránková webová aplikace převádí materiály kurzu FAIL do **profesionálního UI**: videa, prezentace (PDF), prompty, koncepty, úkoly a kvízy. Sdílí se odkazem — progress se **nesleduje**.

Google Drive odkaz na `.html` často otevře text místo appky; proto běží na **GitHub Pages**.

---

## Pro koho

- Autor (vlastní opakování kurzu)
- 2 kolegové (stejný odkaz, bez přihlášení a bez společného progressu)

---

## Co appka obsahuje

- 10 modulů programu FAIL
- YouTube videa embednutá přímo v UI (+ bonus sessions)
- **Prezentace (PDF)** přes vestavěný PDF.js
  - listování **Předchozí / Další** přímo na stránce
  - počítadlo slidů (`N / celkem`)
  - odkaz **Celá obrazovka** + **Stáhnout PDF**
  - načtení až po otevření modulu (lazy load)
- **Prompty** jako karty s tlačítkem Kopírovat
- Koncepty, tipy, příběhy, slovníčky jako karty
- Procvičení: úkoly + kvízy (správné zeleně ✓, špatné červeně ✗; výsledek se neukládá)
- Responzivní navigace: menu, Zpět, předchozí/další modul
- **Žádný raw markdown** jako hlavní obsah

---

## Architektura

```
Google Drive (FAIL Attachments)
        │
        ▼
scripts/import-content.mjs  →  public/data/course.json
scripts/build-shareable-html.mjs
        │
        ▼
dist/deploy/
  ├── index.html          # celá appka
  ├── materials/modul-N/  # PDF + HTML prezentace
  └── pdfjs/              # PDF.js viewer
        │
        ├──► GitHub Pages (sdílený odkaz)
        └──► Drive kopie HTML (záloha, ne pro sdílení odkazem)
```

| Vrstva | Technologie |
|--------|-------------|
| Publish | Static HTML + CSS + JS |
| Prezentace | Mozilla PDF.js (same-origin embed) |
| Hosting | GitHub Pages (`fail-academy-interactive`) |
| Dev (volitelné) | Vite + React v `fail-learning-app` |
| Data | `ai-future-leaders-akademie.html` + course.json + Drive PDF/MD |

### PDF — důležitá pravidla

- Odkazy na viewer jsou **absolutní** (`https://…/pdfjs/web/viewer.html?file=…`). Relativní `pdfjs/…` se na GitHub Pages bez trailing slash rozbije (404).
- Zoom `page-width` se nastaví až po načtení PDF.js (hash `#zoom=…` v URL embedu může načítání rozbít).
- Při otevření modulu se prezentace resetuje na slide 1.

---

## Jak spustit lokálně (vývoj)

```bash
cd ~/Projects/fail-learning-app
npm install
npm run import-content          # obnoví course.json z Drive
node scripts/build-shareable-html.mjs
open dist/fail-academy-interactive.html
# nebo
npx --yes serve dist/deploy -p 8765
```

Volitelně React MVP: `npm run dev` → http://localhost:5173

---

## Jak aktualizovat a znovu nasadit

1. Upravte materiály na Google Drive (nebo HTML přehled).
2. `npm run import-content`
3. `node scripts/build-shareable-html.mjs`  
   (zapíše `dist/deploy/index.html` + zkopíruje materiály)
4. V `dist/deploy` (publish repo):
   ```bash
   git add -A && git commit -m "…" && git push
   ```
5. GitHub Actions / Pages nasadí změnu (~1 min). Po update doporučen **hard refresh** (Cmd+Shift+R).

---

## Sdílení s kolegy

**Použijte:** https://zdenekmelotik-max.github.io/fail-academy-interactive/

**Nepoužívejte** Drive odkaz na HTML soubor jako primární — Drive často zobrazí zdrojový text místo UI.

---

## Co záměrně není

- Sledování progressu / společné skóre
- Přihlášení (Google Auth)
- Firebase / vlastní backend
- AI generátor úkolů (možná fáze 2)

---

## Fáze 2 (nápadník)

- Omezení přístupu (Auth / privátní Pages)
- Lepší kvízy ručně kurátorované
- Vyhledávání napříč moduly
- Notion / Drive sync automatizace

---

## Kontakty / vlastnictví

- GitHub účet: `zdenekmelotik-max`
- Materiály: Google Drive `zdenek.melotik@gmail.com` → treninky
