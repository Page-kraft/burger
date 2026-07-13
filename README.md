# BunBun Burger

Entpackte, bearbeitbare Version der Website aus `BunBun Burger.html` (eine
selbst-entpackende „Bundle"-Datei). Der eingebettete, komprimierte Payload wurde
in echte Dateien zerlegt.

## Struktur

- `index.html` — das eigentliche Seiten-Template (React-App auf Basis eines
  Custom-Component-Frameworks). Ganz oben ist eine `window.__resources`-Map
  eingefügt, über die die Skripte die Assets per ID auflösen.
- `assets/` — 206 Assets: die ~180 Frames der scroll-gesteuerten Burger-Animation,
  Zutaten-Fotos, Fonts (woff2), React + ReactDOM und die App-Skripte.

## Lokal ansehen

```bash
cd bunbun-burger
python3 -m http.server 4178
# dann http://localhost:4178/index.html öffnen
```

Muss über einen Server (http://) laufen, nicht per Doppelklick (file://),
weil die App JS-Module und Fonts lädt.

## Auf GitHub + Vercel veröffentlichen

Das ist eine reine statische Seite — **kein Build-Schritt nötig**.

**1. Zu GitHub pushen** (Repo vorher auf github.com anlegen, leer, ohne README):

```bash
cd bunbun-burger
git remote add origin https://github.com/<DEIN-USER>/bunbun-burger.git
git push -u origin main
```

**2. Auf Vercel deployen:**

- [vercel.com/new](https://vercel.com/new) öffnen → das GitHub-Repo importieren
- **Framework Preset:** „Other" (Vercel erkennt die statische Seite automatisch)
- **Build Command:** leer lassen · **Output Directory:** leer lassen (Root)
- „Deploy" klicken

Vercel serviert `index.html` direkt aus dem Repo-Root. Jeder weitere
`git push` löst automatisch ein neues Deployment aus.

## Hinweise

- Die Produkt-Karten (The Classic, The Smoke, …) und einige Sektionen zeigen
  `<image-slot>`-Platzhalter mit Text wie „Foto: The Classic". Das ist **so im
  Original** — dort waren nie echte Fotos hinterlegt. Eigene Bilder können in
  `index.html` an den `image-slot`-Elementen ergänzt werden.
