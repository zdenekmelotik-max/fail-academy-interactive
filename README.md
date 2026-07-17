# FAIL Academy Interactive

Interaktivní webový trénink programu **Future AI Leader (FAIL)** — 10 modulů, videa, PDF prezentace, prompty, kvízy a úkoly v profesionálním UI.

## Živý odkaz (pro kolegy)

**https://zdenekmelotik-max.github.io/fail-academy-interactive/**

## Co umí

- Embedovaná YouTube videa + bonus sessions
- PDF prezentace s listováním **Předchozí / Další** (PDF.js)
- Prompty s kopírováním
- Úkoly a kvízy (správné odpovědi zeleně)
- Bez přihlášení a bez sledování progressu

## Rychlý start (vývoj)

```bash
cd ~/Projects/fail-learning-app
npm install
npm run import-content
node scripts/build-shareable-html.mjs
open dist/fail-academy-interactive.html
# nebo sloužit celý deploy adresář:
npx --yes serve dist/deploy -p 8765
```

## Nasazení

```bash
node scripts/build-shareable-html.mjs
cd dist/deploy
git add -A && git commit -m "update content" && git push
```

Po nasazení doporučen hard refresh (Cmd+Shift+R).

## Dokumentace

- [Projektová dokumentace](docs/PROJECT.md) — účel, architektura, PDF pravidla, nasazení
- [Notion draft](docs/NOTION-PROJECT.md) — text ke vložení do Notion → Projekty

## Repozitáře

| Repo | Účel |
|------|------|
| Tento projekt (`fail-learning-app`) | Zdroj, skripty, React MVP |
| [fail-academy-interactive](https://github.com/zdenekmelotik-max/fail-academy-interactive) | Publikovaný static site (GitHub Pages) |

## Poznámka ke Google Disku

Soubor `.html` na Drive je záloha. **Sdílejte GitHub Pages odkaz** — Drive často otevře HTML jako text.
