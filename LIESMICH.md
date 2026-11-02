# Latein Vokabeln – eigenständige Web-App

Läuft komplett ohne Claude.ai, auch offline. Alle Daten bleiben auf dem iPad.

## Dateien
| Datei | Zweck |
|---|---|
| index.html | Die App |
| vokabeln.json | Deine Vokabeln (wird beim Start automatisch eingelesen) |
| sw.js | Offline-Modus |
| manifest.webmanifest, icon-*.png | Symbol und App-Darstellung auf dem Home-Bildschirm |

## Hosten
Den ganzen Ordner auf einen Webserver mit **HTTPS** legen (ohne HTTPS kein Offline-Modus).
- **Eigener Server:** Ordner ins Webroot kopieren, z. B. `/var/www/latein/`.
- **GitHub Pages:** Repo anlegen, Dateien hochladen, unter Settings → Pages den Branch `main` aktivieren.

## Auf dem iPad installieren
Seite in Safari öffnen → Teilen → „Zum Home-Bildschirm“. Danach immer über das Symbol starten.

## Speichern
- Automatisch nach jeder Antwort und jeder Lektion, lokal auf dem iPad.
- **Fortschritt exportieren** (Tab „Neu“) erzeugt `latein-fortschritt-JJJJ-MM-TT.json`. Über „In Dateien sichern“ ablegen, z. B. in iCloud Drive.
- **Fortschritt importieren** lädt so eine Datei wieder (ersetzt den aktuellen Stand).
- Die App erinnert dich, wenn die letzte Sicherung älter als 7 Tage ist.

## Vokabeln aktualisieren
Entweder `vokabeln.json` auf dem Server austauschen (wird beim nächsten Start übernommen) oder in der App „Vokabeldatei laden“ wählen. Der Lernfortschritt bleibt erhalten, neue Wörter kommen ans Ende des Lernpfads.

Format:
```json
{
  "version": 1,
  "words": [
    { "id": "w001", "la": "amicus, amici m.", "de": "Freund", "level": 1, "info": "Nomen, o-Deklination, maskulin" }
  ]
}
```
`level`: 1 = Leicht, 2 = Mittel, 3 = Schwer. Die Reihenfolge innerhalb eines Moduls bestimmt die Lektionen (je 10 Wörter).

Eine einfache Textdatei geht auch (landet im gewählten Modul), eine Vokabel pro Zeile: `amicus, amici m. = Freund`
