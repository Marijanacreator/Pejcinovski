# Dr Pejčinoski — sajt

## Struktura
- `index.html` — glavna i jedina stranica sajta
- `support.js` — runtime skripta koju `index.html` učitava, mora biti u istom (root) folderu
- `assets/` — slike, ikonice i pomoćna skripta (`image-slot.js`, `icons/`, `uploads/`, `zub.png`)

## Hostovanje na GitHub Pages
1. Sve iz ovog paketa (fajlove i `assets/` folder) ubaci na root nivo repoa — ne u podfolder.
2. Settings → Pages → Deploy from branch → `main` → `/ (root)`.
3. Sačekaj da se build završi, pa otvori `https://tvoj-username.github.io/ime-repoa/`.

Ako i dalje izbaci 404, proveri da je fajl tačno `index.html` (sa ekstenzijom) na root nivou repoa, i da je `assets/` folder uploadovan ceo.
