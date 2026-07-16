# FAIL Academy Interactive

> Projektová karta pro Notion → **Projekty**

## Status
Live

## Odkazy
- Appka: https://zdenekmelotik-max.github.io/fail-academy-interactive/
- GitHub (publish): https://github.com/zdenekmelotik-max/fail-academy-interactive
- Lokální zdroj: `~/Projects/fail-learning-app`
- Dokumentace: viz `docs/PROJECT.md` v lokálním projektu / GitHub

## Účel
Interaktivní učení kurzu Future AI Leader (FAIL) pro mě a 2 kolegy. Materiály z Google Drive převedené do 100% UI (videa, karty, úkoly, kvízy). Bez sledování progressu.

## Proč ne Google Drive odkaz
Drive často zobrazí HTML jako text. Proto běží na GitHub Pages.

## Obsah
- 10 modulů FAIL
- YouTube embed + bonus sessions
- Koncepty, příběhy, tipy, slovníčky
- Úkoly + kvízy (neukládá se)
- Responzivní navigace (Menu, Zpět, předchozí/další)

## Stack
Single HTML · CSS · JS · GitHub Pages  
Zdroj dat: `treninky/FAIL Attachments` na Google Drive  
Build: `scripts/build-shareable-html.mjs`

## Jak aktualizovat
1. Upravit materiály na Drive
2. `npm run import-content`
3. `node scripts/build-shareable-html.mjs`
4. Push `dist/deploy` do `fail-academy-interactive`

## Záměrně není
- Progress / login / Firebase
- Raw markdown jako hlavní obsah

## Fáze 2
Auth, lepší kvízy, search, automatický sync
