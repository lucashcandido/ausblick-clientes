# Ausblick – Clientes

Liste der möglichen Kunden von Ausblick: wen wir schon kontaktiert haben, mit **Telefonnummer, Ort und Webadresse**. Aufgebaut wie `work.castcomercial.com`.

- **Liste:** Name, Rubro, Telefon (antippen = anrufen), Ort, Web (antippen = öffnen), Status und letzter Kontakt (Datum, wer, was).
- **Status:** Sin contactar · Contactado · Interesado · Cliente · No interesado. Filter oben, Suche über alle Felder.
- **Kontakte:** Im Kunden „Registrar contacto“ → Datum, Notiz und Name des Geräts werden gespeichert. Der erste Kontakt setzt den Status auf „Contactado“.
- **Doppelte:** Beim Anlegen warnt die App, wenn Name, Telefon oder Web schon existieren.
- **Sort in / Alle:** Importierte Garagen starten unter „Sort in“. Dort pro Eintrag „✓ Existe“ (→ Alle) oder „✕ No existe“ (wird gelöscht, mit Rückgängig). Mit Telefonnummer oder eingetragenem Kontakt gilt ein Eintrag automatisch als existierend; selbst angelegte Kunden kommen direkt zu Alle. Adresse antippen öffnet Google Maps.
- **Kategorien:** pro Kunde beliebig viele (im Kundenfenster an-/abwählen oder neue anlegen), Filter neben der Suche. Eingebaut: „Cocheras / Parking lot / Parkplatz“ (`parking`) und „Peluquerías / Hairdressers / Friseur“ (`hair`), je nach Sprache angezeigt; eigene Kategorien so wie eingegeben. Alle Kunden, die vor dem 29.10.2026 angelegt wurden, haben automatisch „Parkplatz“.
- **„next to it“:** Checkbox unter der Telefonnummer, wenn die Nummer von einem Geschäft neben der Garage stammt; in der Liste als Etikett neben der Nummer. „(next to it)“ am Ende des Namens wird automatisch in die Checkbox umgewandelt.
- **Filter „Con teléfono“**, Liste seitenweise (100 pro Seite), Button „Ver mapa“ wenn in den Notizen ein Kartenlink steht.
- **Export:** Configuración → Exportar lista (CSV, öffnet in Excel).
- **Sprachen:** Español, English, Deutsch. Beim ersten Öffnen nach Gerätesprache (sonst Spanisch), umschaltbar oben im Einrichtungsbildschirm und in der Configuración; die Wahl bleibt pro Gerät gespeichert. Die Daten selbst sind sprachunabhängig.

## Daten und Zugang

- **Daten:** im privaten Repo `ausblick-clientes-data`, eine Datei `clientes.json`. Neuere Änderung gewinnt pro Kunde, Kontakte von zwei Geräten werden zusammengeführt. Offline-Änderungen werden später gespeichert.
- **Token:** Fine-grained Personal Access Token, der **nur** `ausblick-clientes-data` erreicht (Repository permissions → Contents: Read and write).
- **Code:** Wer die App zum ersten Mal mit dem Token einrichtet („Primera vez (token)“), bekommt einen 12-stelligen Code und die Datei `access.json` (Token mit AES-GCM/PBKDF2 aus dem Code verschlüsselt). `access.json` kommt in dieses Repo; alle anderen Geräte brauchen dann nur noch Name + Code. Ohne den Code ist die Datei nutzlos.
- **Token erneuert:** Mit dem neuen Token einmal „Primera vez“ machen und die neue `access.json` hochladen – die anderen Geräte holen sich den neuen Token automatisch, wenn der Code gleich bleibt (Configuración → Cambiar nombre o acceso → Primera vez, gleiches Gerät behält den Code).

## Einrichtung (einmalig)

1. Repo `ausblick-clientes` (öffentlich, für GitHub Pages) und `ausblick-clientes-data` (privat, leer) anlegen.
2. Diese Dateien nach `ausblick-clientes` pushen, Settings → Pages → Branch `main` / root.
3. Token erstellen (siehe oben), App öffnen → „Primera vez (token)“ → `access.json` herunterladen und in `ausblick-clientes` hochladen.
4. Optional eigene Domain (z. B. `clientes.ausblicksistemas.com`) per `CNAME`.

## Datenquellen der importierten Parkplätze

GCBA „Garajes Comerciales“ (CC BY 2.5 AR) und © OpenStreetMap-Mitwirkende (ODbL). Details im Daten-Repo.
