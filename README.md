# Copywriting-Portfolio (Jekyll + Pages CMS, zweisprachig DE/EN)

## Was hier drin ist

- **Jekyll**-Grundgerüst, optisch angelehnt an den minimalistischen Next.js-Blog-Stil
- **jekyll-polyglot** für Mehrsprachigkeit: Deutsch = Hauptsprache (keine URL-Präfix),
  Englisch = `/en/...`
- **Pages CMS**-Konfiguration (`.pages.yml`) mit getrennten Collections für
  DE- und EN-Arbeiten
- **GitHub Actions**-Workflow, der den Build übernimmt (nötig, weil GitHub Pages'
  eigener Build `jekyll-polyglot` nicht unterstützt)

## Ordnerstruktur

```
_works/de/…       Arbeiten auf Deutsch
_works/en/…       Arbeiten auf Englisch (gleicher Dateiname wie das DE-Pendant!)
index.md          Startseite Deutsch      (permalink: /)
index-en.md       Startseite Englisch     (permalink: / → landet automatisch unter /en/)
about.md / about-en.md   Über-mich-Seiten
_layouts/, _includes/    Templates
assets/css/style.css     Styles
.pages.yml               Pages CMS Konfiguration
.github/workflows/deploy.yml   Build & Deploy
```

**Wichtige Regel:** Für jede Arbeit legst du zwei Dateien mit **identischem
Dateinamen** an – eine in `_works/de/`, eine in `_works/en/`. Der Dateiname
bestimmt die URL (`/works/dateiname/`), so bleiben beide Sprachversionen
über den Sprachumschalter verknüpft.

## Einrichtung

### 1. Repository anlegen
Lade diesen Ordner in ein neues GitHub-Repo hoch (per Git oder GitHub-Weboberfläche).

### 2. URL in `_config.yml` anpassen
```yaml
url: "https://DEINUSERNAME.github.io"
baseurl: ""              # oder "/REPO-NAME", falls kein User-Root-Repo
```

### 3. GitHub Pages auf "GitHub Actions" umstellen
Repo → **Settings → Pages → Source** → "GitHub Actions" auswählen
(nicht "Deploy from a branch" – das würde den mitgelieferten Workflow ignorieren).

### 4. Pages CMS verbinden
Auf [pagescms.org](https://app.pagescms.org) einloggen, GitHub-App installieren,
Repository verbinden. Pages CMS liest automatisch die `.pages.yml`.

### 5. Lokal testen (optional)
```bash
bundle install
bundle exec jekyll serve
```
→ `http://localhost:4000` (Deutsch) und `http://localhost:4000/en/` (Englisch)

## Neue Arbeit anlegen

**Über Pages CMS:**
1. Collection "Arbeiten (Deutsch)" → neuer Eintrag → Datei benennen, z. B. `neues-projekt.md`
2. Collection "Works (English)" → neuer Eintrag → **denselben Dateinamen** `neues-projekt.md` verwenden

**Direkt im Repo:**
```
_works/de/neues-projekt.md
_works/en/neues-projekt.md
```

## Grenzen dieses Setups

- Der Sprachumschalter im Header geht davon aus, dass zu jeder Seite eine
  Übersetzung mit identischer URL existiert. Fehlt eine Übersetzung, führt
  der Link auf eine 404-Seite – lege in dem Fall lieber sofort beide
  Sprachversionen an (auch wenn die zweite erstmal nur ein Platzhalter ist).
- Aktuell sind nur zwei Sprachen vorgesehen; die Switcher-Logik in
  `_includes/header.html` müsste für weitere Sprachen erweitert werden.
- Es gibt bewusst keine Kommentarfunktion, Suche o. Ä. – das lässt sich bei
  Bedarf über zusätzliche Jekyll-Plugins/JS ergänzen.
