# Enemy – v2.1

Enemy 1 (Tempest of Violence) + Enemy 2 (Missing in Action)
Anachronia, **deutsche v2.0 + englische v2.0** auf einer CD

- **Enemy:** [Anachronia.ch](https://www.anachronia.ch) (Besten Dank an André Wüthrich)
- **WHDLoad-Slaves:** Wepl ([whdload.de](https://www.whdload.de))
- **Compilation:** S. Kaufmann (2026)
- **System:** CD32 mit 1,5 MB FastRAM

## Features

- **BoxArt-Boot-Logo** vor der Auswahl
- **4-Wege-Auswahl-Menü** (Tastatur: `1`/`2`/`3`/`4` oder Pfeile/Pad-Buttons)
  - `1` → Enemy 1 (DE)
  - `2` → Enemy 2 (DE)
  - `3` → Enemy 1 (EN) — *neu in v2.1*
  - `4` → Enemy 2 (EN) — *neu in v2.1*
- **Alle vier Spielversionen auf einer CD** – DE + EN, Enemy 1 + Enemy 2
- **Alle Level freigeschaltet**, Spielstart immer in Level 1
- **Sauberer Start** ohne WHDLoad-Splash

## Changelog

### v2.1
- Englische Versionen von Enemy 1 und Enemy 2 ergänzt (Tasten `3` + `4`)
- Menü auf 4-Wege-Dispatch erweitert via Sentinel-Files `T:E3` / `T:E4`,
  weil AmigaDOS-`IF` selbst `$RC` überschreibt und damit kein
  `IF FAIL/ERROR/WARN`-Cascading erlaubt
- Build-Toolchain-Bugs in `build_cd32_iso.py` behoben:
  - `-allow-lowercase` aus den xorriso-Flags entfernt (CD32-CDFS erwartet
    ISO-9660-Uppercase, sonst findet WHDLoad das Binary nicht)
  - `strip_trailing_dots()` iteriert jetzt über alle Sektoren eines
    Directory-Records (vorher nur erster Sektor → bei mehr-sektor-Dirs
    wurden `WHDLOAD.;1` / `WHDLOADCD32.;1` nicht gestrippt)
- EN-Daten-Vorbereitung: Disk A **und** Disk B müssen für alle Subfolder
  (`bobs`/`bp`/`fx`/`msx`/`sek`/`txt`) gemerged werden, plus HD-Install-Marker
  (`astart.txt`, `ainstall.txt`, `CloseWB`, `Type` + HD-Style-Startup-Sequence)
  damit das Spiel nicht nach „Enemy Disk A" fragt

### v2.0.2
- Auswahl-Menü neu gestaltet: Box-Layout mit zentriertem Titel,
  Anachronia (www.anachronia.ch) als Quelle ergänzt, JoyDebug-Eintrag
  entfernt
- Versionsanzeige im CLI-Menü auf v2.0.2 aktualisiert

### v2.0.1
- Fix: Enemy-2-Auswahl im Menü (Echo überschrieb Return-Code zwischen
  `Menu` und `IF WARN`, dadurch wurde immer Enemy 1 geladen)

### v2.0
- Initial Release

## Credits

Dank an **Anachronia** für beide Enemy-Spiele und an **Wepl** für die
WHDLoad-Slaves.
