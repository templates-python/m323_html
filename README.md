# m323_html

Interaktive Erklär-Animationen zum Modul **323 – Funktional Programmieren**.

Jede Datei ist ein eigenständiges HTML-Dokument ohne externe Abhängigkeiten (kein CDN, keine
Build-Kette). Ausgeliefert wird über GitHub Pages, eingebunden wird im
[BZZ-Modulwiki](https://wiki.bzz.ch/modul/m323/start) per `iframe`.

## Inhalt

| Datei | Learning Unit | Thema |
|---|---|---|
| `index.html` | – | Übersicht aller Animationen |
| `lu02/pure-vs-unpure.html` | LU02b | Determinismus: gleiche Eingabe, gleiches Ergebnis? Mit und ohne globalen Zustand |
| `lu02/byvalue-byreference.html` | LU02d | By Value / By Reference: Speichermodell beim Funktionsaufruf, `int` vs. `list` |
| `lu02/objekte-und-standardwerte.html` | LU02e | Objekte by reference, `frozen=True`, geteilter mutable Standardwert |

## GitHub Pages aktivieren

Einmalig unter **Settings → Pages**: Source = `Deploy from a branch`, Branch = `main`, Ordner = `/ (root)`.

Danach sind die Dateien erreichbar unter:

```
https://templates-python.github.io/m323_html/
https://templates-python.github.io/m323_html/lu02/byvalue-byreference.html
```

Die Datei `.nojekyll` verhindert, dass Jekyll die Auslieferung verändert.

## Einbindung ins Wiki

Auf der Theorieseite (`modul:m323:learningunits:lu02:byvaluebyreference`) mit dem
bereits installierten [`iframe`-Plugin](https://www.dokuwiki.org/plugin:iframe):

```
{{url>https://templates-python.github.io/m323_html/lu02/byvalue-byreference.html 100%,760px noborder|Animation: By Value und By Reference}}
```

Die Höhe (`760px`) ist bewusst fix – der iframe kann seine Höhe nicht selbst an den Inhalt
anpassen. Bei schmalen Fenstern klappt das Layout einspaltig um und braucht mehr Platz.

**Nicht** per `confightmlok` direkt in die Wikiseite einbetten: Die CSS-Klassen der Animation
(`.panel`, `.main`, `.tabs`) kollidieren mit dem Bootstrap3-Template. Der iframe kapselt das.

## Konventionen für neue Animationen

* Ein Ordner pro Learning Unit (`lu02/`, `lu03/`, …), Dateiname beschreibt das Thema.
* Vollständig standalone: CSS und JS inline, keine externen Requests.
* Theme-aware: helle Palette auf `:root`, Dark Mode über `@media (prefers-color-scheme: dark)`.
* **Kein Autoplay.** Steuerung über «Weiter»/«Zurück», zusätzlich Pfeiltasten – Lernende sollen
  das Tempo bestimmen und Schritte vergleichen können.
* Jeder Schritt hat einen erklärenden Satz; der didaktisch entscheidende Schritt wird
  explizit als solcher markiert.
* Neue Datei in `index.html` und in der Tabelle oben ergänzen.
* **Alle gezeigten Ausgaben gegen echtes Python prüfen**, bevor die Animation veröffentlicht wird –
  eine Animation, die etwas anderes behauptet als der Interpreter, richtet mehr Schaden an als Nutzen.

Die Schritt-Engine (CSS + JS) ist in jeder Datei dupliziert, damit jede Animation für sich allein
lauffähig bleibt. Ab der dritten Animation lohnt es sich, sie nach `assets/` auszulagern.

## Lizenz

CC BY-NC-SA 4.0 – Kevin Maurizi
