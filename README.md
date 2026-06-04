# Theodor Landell — Portfolio

Tvåspråkig (SV/EN) one-page-portfolio med tre projekt: Träplanksanalys, DartVision och Blackjack.
Ren, ljus Scandinavian-stil. Ingen build krävs — det är ren HTML/CSS/JS.

## Mappstruktur
```
portfolio/
├── index.html              ← hela sidan (HTML + CSS + JS)
└── assets/
    ├── videos/             ← bakgrundsvideor (webboptimerade, ljudlösa)
    ├── img/                ← skärmbilder + stillbilder
    └── cv/                 ← CV på svenska och engelska
```

## Förhandsgranska lokalt
Videorna och bilderna laddas inte om du öppnar `index.html` direkt i en del webbläsare
(de blockerar lokala filer). Kör därför en liten lokal server:

```bash
cd portfolio
python3 -m http.server 8000
```
Öppna sedan **http://localhost:8000** i webbläsaren.

## Publicera (gratis)
Dra och släpp hela `portfolio`-mappen på någon av dessa:
- **Netlify Drop** — https://app.netlify.com/drop
- **Vercel** — `vercel` i mappen, eller dra in på vercel.com
- **GitHub Pages** — lägg filerna i ett repo och slå på Pages

## Anpassa
- **GitHub / LinkedIn:** redan inlagda (github.com/TheodorLandell + din LinkedIn). Byt vid behov i `index.html`.
- **CV:** ersätt filerna i `assets/cv/` (behåll filnamnen) — svensk visas på SV, engelsk på EN.
- **Texter:** all text finns i `I18N`-objektet längst upp i `<script>` i `index.html` (sv + en).
- **Projekt:** all projektinfo finns i `PROJECTS`-arrayen direkt under `I18N`.
- **Videor:** byt filerna i `assets/videos/` (behåll filnamnen). Håll dem små — 720p, ljudlösa.

## Teknik
Fonts: Fraunces (rubriker), Hanken Grotesk (brödtext), JetBrains Mono (etiketter) via Google Fonts.
Inga ramverk, inga beroenden, inget bygg-steg.
