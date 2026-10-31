# VKARM poznámky

Poznámky na zápočet z predmetu VKARM (regulácia: Laplaceova transformácia, prenosová a prechodová funkcia, diferenciálne rovnice, RC obvody, blokové schémy, cvičná písomka). Píšeme po slovensky.

## Súbory

- `zapocet-vkarm.html`: celá stránka „Zápočet VKARM“ v jednom HTML súbore (CSS a JS sú inline). Vzorce sa píšu v LaTeX-e pre MathJax 3: inline `\( ... \)`, blokové `\[ ... \]`. Písmo je IBM Plex z Google Fonts.
- `artifact.json`: väzba na artefakt na claude.ai (slug, URL, posledná synchronizovaná verzia, nastavenie zdieľania). Je v `.gitignore`, takže v novom klone chýba. Vtedy ho vytvor znova: zavolaj `get_artifact` s URL artefaktu (zistíš slug aj verziu) a obsah porovnaj so `zapocet-vkarm.html`.

## Synchronizácia s artefaktom na claude.ai

Lokálny súbor `zapocet-vkarm.html` a artefakt https://claude.ai/artifact/Qk5dMpkMoGjaWNG5aepegS musia mať vždy rovnaký obsah. Pri **každej** zmene stránky:

1. **Pred úpravou** zavolaj `get_artifact` so slugom z `artifact.json`. Ak sa živá verzia líši od `version` v `artifact.json`, niekto artefakt upravil priamo na claude.ai. Najprv ju stiahni cez `read_artifact`, vyber HTML spomedzi obaľovacích tagov `untrusted-document-…` (tie do súboru nepatria), prepíš ňou `zapocet-vkarm.html` a ukáž používateľovi `git diff`. Až potom pokračuj.
2. Uprav `zapocet-vkarm.html` lokálne (Edit).
3. Zverejni ho cez `publish_files`: `files: [{as: "index.html", path: <absolútna cesta k zapocet-vkarm.html>}]`, `slug` a `base_version` z `artifact.json`. Artefakt je **verejný**, preto pridaj aj `shared_live: "public"` a `artifact_title: "Zápočet VKARM"`. `title` neposielaj, iba ak sa má artefakt premenovať.
4. Novú verziu z výsledku zapíš do `version` v `artifact.json`.

Ak publikovanie zlyhá na konflikte verzií, vráť sa na krok 1. Používateľ dal trvalý súhlas, aby sa každá zmena hneď publikovala. Treba však pamätať, že stránku vidí každý, kto má odkaz.

## Git

Commituj iba vtedy, keď o to používateľ požiada.
