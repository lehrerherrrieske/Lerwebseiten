# Lernportal

![GitHub Pages](https://img.shields.io/badge/hosted%20on-GitHub%20Pages-222?logo=github)
![Technik](https://img.shields.io/badge/Technik-HTML%20%7C%20CSS%20%7C%20JavaScript-B25A38)
![Keine Abhängigkeiten](https://img.shields.io/badge/Abh%C3%A4ngigkeiten-keine-1C7168)

Interaktive Lernseiten für den Unterricht am Gymnasium – zum Nacharbeiten, Üben und Wiederholen.
Das Portal bündelt alle Seiten an einem Ort und führt in drei Schritten zum passenden Material:
**Fach wählen → Klassenstufe wählen → Lernseite öffnen.**

**Zum Portal:** https://lehrerherrrieske.github.io/Lerwebseiten/

---

## Inhalt

- [Für Schülerinnen und Schüler](#für-schülerinnen-und-schüler)
- [Fächer und Klassenstufen](#fächer-und-klassenstufen)
- [Was die Lernseiten bieten](#was-die-lernseiten-bieten)
- [Aufbau des Repositorys](#aufbau-des-repositorys)
- [Neue Lernseite eintragen](#neue-lernseite-eintragen)
- [Neues Fach hinzufügen](#neues-fach-hinzufügen)
- [Lokal ansehen und veröffentlichen](#lokal-ansehen-und-veröffentlichen)
- [Technik](#technik)

---

## Für Schülerinnen und Schüler

1. Öffne das Portal über den Link oben.
2. Wähle dein Fach und anschließend deine Klassenstufe.
3. Die Lernseiten sind nach Lernbereichen sortiert. Ein Klick öffnet die Seite direkt im Browser.

Es ist keine Anmeldung und keine Installation nötig. Die Seiten funktionieren am Computer, Tablet und Smartphone.
Seiten mit dem Hinweis **„In Arbeit“** werden gerade noch erstellt und sind bald verfügbar.

---

## Fächer und Klassenstufen

| Fach       | Klassenstufen                    |
|------------|----------------------------------|
| Physik     | 6 – 10, 11 und 12 (GK und LK)    |
| Informatik | 7 – 10, 11 und 12 (GK und LK)    |
| Biologie   | 5 – 10, 11 und 12 (GK und LK)    |
| Englisch   | 5 – 10, 11 und 12 (GK und LK)    |

Die Inhalte orientieren sich am sächsischen Lehrplan für das Gymnasium und wachsen laufend mit dem Unterricht.

---

## Was die Lernseiten bieten

Jede Lernseite ist eine eigenständige HTML-Datei und folgt einem einheitlichen Aufbau:

- **Phasen-Navigation** – die Stunde ist in übersichtliche Abschnitte gegliedert
- **Interaktive Übungen** – Quiz, Lückentexte, Zuordnungen, Sortieraufgaben, Memory, Lernkarten, Kreuzworträtsel u. a.
- **Gestufte Hilfen** – zu jeder Aufgabe lassen sich Tipps und später eine Musterlösung aufrufen
- **Heftereintrag** – die wichtigsten Ergebnisse können direkt übernommen werden
- **Einheitliches Design** – ruhiges, warmes Farbschema, gut lesbar auch am Beamer

---

## Aufbau des Repositorys

```
/
├── index.html                  Startseite des Portals
├── README.md
├── Physik/
│   ├── Klasse_6/
│   ├── Klasse_7/
│   ├── ...
│   ├── Klasse_11_GK/
│   ├── Klasse_11_LK/
│   ├── Klasse_12_GK/
│   └── Klasse_12_LK/
├── Informatik/
│   └── Klasse_7/ ... Klasse_12_LK/
├── Biologie/
│   └── Klasse_5/ ... Klasse_12_LK/
└── Englisch/
    └── Klasse_5/ ... Klasse_12_LK/
```

Die Lernseiten liegen im Ordner ihres Fachs und ihrer Klassenstufe.
Dateinamen folgen dem Schema `K<Klasse> - LB<Nr> - <Thema>.html`, zum Beispiel
`K8 - LB2 - Ohmsches_Gesetz.html`.

Leere Ordner enthalten eine Platzhalterdatei `.gitkeep`, damit Git sie mit hochlädt.
Sobald eine Lernseite im Ordner liegt, kann sie entfernt werden.

---

## Neue Lernseite eintragen

1. Die HTML-Datei in den passenden Ordner legen, z. B. `Physik/Klasse_8/`.
2. In der `index.html` im Array `SEITEN` eine Zeile ergänzen:

```js
{ fach:"physik", klasse:"8", lb:"LB2 - Elektrizitätslehre",
  titel:"Stromstärke, Spannung, Widerstand",
  datei:"K8 - LB2 - Stromstaerke_Spannung_Widerstand.html", neu:true },
```

| Feld     | Bedeutung                                                                 |
|----------|---------------------------------------------------------------------------|
| `fach`   | ID des Fachs aus `FAECHER`, z. B. `"physik"`, `"biologie"`                 |
| `klasse` | ID der Klassenstufe aus `KLASSEN`, z. B. `"7"`, `"11GK"`, `"12LK"`         |
| `lb`     | Lernbereich – dient als Gruppenüberschrift                                |
| `titel`  | Anzeigename der Seite                                                     |
| `datei`  | nur der Dateiname, der Ordner wird automatisch ergänzt                    |
| `neu`    | optional – zeigt das Kennzeichen „Neu“                                    |
| `wip`    | optional – Seite erscheint ausgegraut mit dem Hinweis „In Arbeit“         |

Klassenstufen ohne Einträge zeigen automatisch einen Platzhaltertext.

---

## Neues Fach hinzufügen

Fächer werden zentral in der `index.html` gepflegt. Zwei Schritte genügen:

**1. Fach in der Liste `FAECHER` ergänzen**

```js
{ id:"chemie", name:"Chemie", icon:"…", farbe:"#8A6A1F" },
```

`id` wird kleingeschrieben und ohne Umlaute angegeben, `icon` ist ein beliebiges Symbol für die Fachkarte. Aus `farbe` berechnet die Seite
automatisch alle hellen und dunklen Farbvarianten.

**2. Klassenstufen in `KLASSEN` anlegen**

```js
chemie: [
  {id:"7",    label:"7",              ordner:"Chemie/Klasse_7"},
  {id:"11GK", label:"11", sub:"GK",   ordner:"Chemie/Klasse_11_GK"},
  // ...
],
```

Fachkarte, Farbgebung und Untertitel der Startseite entstehen danach von selbst.

---

## Lokal ansehen und veröffentlichen

**Lokal:** Repository klonen und `index.html` im Browser öffnen – ein Server ist nicht nötig.

```bash
git clone https://github.com/lehrerherrrieske/Lerwebseiten.git
```

**Änderungen veröffentlichen:** Im Hauptverzeichnis des Repositorys ausführen:

```bash
git add -A
git commit -m "Neue Lernseite: ..."
git push
```

GitHub Pages aktualisiert die Seite anschließend innerhalb weniger Minuten.

---

## Technik

- Reines HTML, CSS und JavaScript – keine Frameworks, kein Build-Schritt
- Jede Lernseite ist eine einzelne, in sich geschlossene Datei
- Responsives Layout für Desktop, Tablet und Smartphone
- Gehostet über GitHub Pages

---

## Über das Projekt

Erstellt von Herrn Rieske für den Unterricht in Physik und Informatik, erweitert um Biologie und Englisch.
Die Materialien wurden mit Unterstützung von KI entwickelt und im Unterricht erprobt.
