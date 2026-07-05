# Copywriting Portfolio (Jekyll, einsprachig, Standard-GitHub-Pages-Build)

## Was sich geändert hat gegenüber der ersten (mehrsprachigen) Version

Keine Mehrsprachigkeit mehr, kein `jekyll-polyglot`, keine eigene GitHub Action.
Die Seite nutzt jetzt GitHub Pages' **eingebauten** Jekyll-Build – der versteht
alle hier verwendeten Plugins (`jekyll-sitemap`, `jekyll-feed`) direkt, ohne
Umwege.

## Aufräumen im bestehenden Repo (wichtig!)

Bevor du die neuen Dateien hochlädst, lösche im Repo:

- `.github/workflows/deploy.yml` und ggf. `.github/workflows/jekyll.yml`
  (der ganze `.github`-Ordner kann weg)
- `_works/de/` und `_works/en/` (werden durch `_works/` ersetzt)
- `index-en.md`, `about-en.md`

Dann in **Settings → Pages → Source**: auf **"Deploy from a branch"**
umstellen (Branch: `main`, Ordner: `/ (root)`). Das ist der native,
eingebaute Build – braucht keine Action mehr.

## Struktur

```
_works/                 Eine Datei pro Arbeit
index.md                Startseite (Hero Post + "More Stories"-Grid)
works.md                Übersicht aller Arbeiten
about.md                Über-mich-Seite
_layouts/, _includes/   Templates
assets/css/style.css    Styles
.pages.yml              Pages CMS Konfiguration
```

## Einrichtung

1. `_config.yml`: `url` und `baseurl` prüfen (aktuell auf
   `https://kwokel.github.io` / `/portfolio` gesetzt)
2. Alte Dateien wie oben beschrieben entfernen, neue hochladen
3. Settings → Pages → Source → "Deploy from a branch" (main / root)
4. Pages CMS liest automatisch die neue `.pages.yml`

## Lokal testen (optional)

```bash
bundle install
bundle exec jekyll serve
```
→ `http://localhost:4000`

## Neue Arbeit anlegen

Über Pages CMS (Collection "Works") oder direkt als neue Datei in
`_works/dein-projekt.md`:

```markdown
---
title: "Titel des Projekts"
date: 2026-07-01
excerpt: "Ein Satz Zusammenfassung."
coverImage: /assets/images/works/dein-bild.jpg
published: true
---
Der eigentliche Text: Gedanken, Strategie, Motivation hinter dem Projekt.
```
