# Schießbuch – App-Version (Klickdummy)

Statische Web-App. Kein Server nötig, keine Datenbank – die Einträge werden im Speicher des
jeweiligen Geräts abgelegt und bleiben dort erhalten. Andere Geräte sehen sie nicht.

## Dateien

- `index.html` – die App
- `manifest.webmanifest` – Name, Farben, Icons für die Installation
- `sw.js` – Service Worker, macht die App offline lauffähig
- `apple-touch-icon.png`, `icon-192.png`, `icon-512.png`, `icon-512-maskable.png` – App-Icons

## Variante A: Render.com (mit GitHub)

1. Auf github.com ein neues Repository anlegen, z. B. `schiessbuch`.
2. Die Dateien aus diesem Ordner hochladen (Add file → Upload files), commit.
3. Auf render.com: New → **Static Site** → GitHub verbinden → Repository auswählen.
4. Einstellungen: **Build Command** leer lassen, **Publish Directory** `.` eintragen.
5. Create Static Site. Nach ein bis zwei Minuten läuft die App unter
   `https://<name>.onrender.com` – Render liefert HTTPS mit, das braucht der Service Worker.

Jeder spätere Push nach GitHub wird automatisch neu veröffentlicht.

## Variante B: GitHub Pages (ohne Render)

1. Repository wie oben anlegen und Dateien hochladen.
2. Settings → Pages → Source: **Deploy from a branch**, Branch `main`, Ordner `/ (root)`, Save.
3. Nach kurzer Zeit erreichbar unter `https://<benutzername>.github.io/schiessbuch/`.

## Auf dem iPhone installieren

1. Die Adresse in **Safari** öffnen (nicht in Chrome oder Brave – nur Safari kann installieren).
2. Teilen-Symbol → **Zum Home-Bildschirm**.
3. Name bestätigen. Das Vereinslogo liegt jetzt als Icon auf dem Home-Bildschirm und startet
   die App im Vollbild ohne Safari-Leiste. Nach dem ersten Start funktioniert sie auch offline.

## Etwas ändern

`index.html` bearbeiten, hochladen – fertig. Wenn eine Änderung auf dem iPhone nicht ankommt,
in `sw.js` die Zeile `var CACHE = "schiessbuch-v1";` auf `-v2` hochzählen; dann lädt die
installierte App die neue Fassung.
