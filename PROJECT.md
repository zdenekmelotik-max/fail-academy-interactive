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

---

## Shrnutí

Jednostránková webová aplikace (single HTML) převádí materiály kurzu FAIL do **100% profesionálního UI**: videa, koncepty, příběhy, úkoly a kvízy. Sdílí se odkazem — progress se **nesleduje**.

Google Drive odkaz na `.html` často otevře text místo appky; proto běží na **GitHub Pages**.

---

## Pro koho

- Autor (vlastní opakování kurzu)
- 2 kolegové (stejný odkaz, bez přihlášení a bez společného progressu)

---

## Co appka obsahuje

- 10 modulů programu FAIL
- YouTube videa embednutá přímo v UI (+ bonus sessions)
- Koncepty, tipy, příběhy, slovníčky jako karty
- Procvičení: úkoly + kvízy (výsledek se neukládá)
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
dist/fail-academy-interactive.html
        │
        ├──► GitHub Pages (sdílený odkaz)
        └──► Drive kopie (záloha, ne pro sdílení odkazem)
```

| Vrstva | Technologie |
|--------|-------------|
| Publish | Static HTML + CSS + JS (jeden soubor) |
| Hosting | GitHub Pages |
| Dev (volitelné) | Vite + React v `fail-learning-app` |
| Data | Extrakce z `ai-future-leaders-akademie.html` + course.json |

---

## Jak spustit lokálně (vývoj)

```bash
cd ~/Projects/fail-learning-app
npm install
npm run import-content          # obnoví course.json z Drive
node scripts/build-shareable-html.mjs
open dist/fail-academy-interactive.html
# nebo
npx --yes serve dist -p 8765
```

Volitelně React MVP: `npm run dev` → http://localhost:5173

---

## Jak aktualizovat a znovu nasadit

1. Upravte materiály na Google Drive (nebo HTML přehled).
2. `npm run import-content`
3. `node scripts/build-shareable-html.mjs`
4. Zkopírujte `dist/fail-academy-interactive.html` → `dist/deploy/index.html`
5. V `dist/deploy`: `git add -A && git commit -m "…" && git push`
6. GitHub Actions nasadí Pages (~1 min).

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
