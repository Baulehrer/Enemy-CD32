# Enemy – v2.2.1

Enemy 1 (Tempest of Violence) + Enemy 2 (Missing in Action)
Anachronia, **deutsche v2.0 + englische v2.0** auf einer CD

- **Enemy:** [Anachronia.ch](https://www.anachronia.ch) (Besten Dank an André Wüthrich)
- **WHDLoad-Slaves:** Wepl ([whdload.de](https://www.whdload.de))
- **Compilation:** S. Kaufmann (2026)
- **System:** CD32 mit 1,5 MB FastRAM

## Features

- **BoxArt-Boot-Logo** vor der Auswahl
- **4-Wege-Auswahl-Menü** mit Cursor-Navigation
  - `[*]` markiert den aktiven Eintrag
  - `TAB` / `BACKSPACE` bewegt den Cursor (Wrap an beiden Enden)
  - `SPACE` / `ENTER` startet den markierten Eintrag
  - `1` / `2` / `3` / `4` startet direkt
  - Joypad: D-Pad navigiert, Color-Button (RED/BLUE/GREEN/YELLOW) startet
- **Vier Spielversionen auf einer CD** – DE + EN, Enemy 1 + Enemy 2
- **Alle Level freigeschaltet**, Spielstart immer in Level 1
- **Sauberer Start** ohne WHDLoad-Splash

## Changelog

### v2.2.1
- **Joypad funktioniert** — drei Bugs in `menu.asm` gefixt:
  - `JP_TYPE_MOUSE`-Konstante stand auf `$10000000`. Das ist tatsächlich
    `JP_TYPE_GAMECTLR` (CD32-Pad). Mein Mouse-Skip hat damit den echten
    Pad als „Maus" verworfen und übersprungen. Korrekt: `MOUSE=$20000000`,
    `GAMECTLR=$10000000`
  - `JPB_BUTTON_GREEN`/`YELLOW`/`PLAY` waren auf den falschen Bit-
    Positionen (15/16/12). Verifiziert via `tools/joydebug/joydebug.asm`:
    GREEN=3, YELLOW=4, PLAY=5
  - Manche USB-Pads liefern in FS-UAE ein non-kanonisches Bit-Mapping:
    Directions in den unteren 4 Bits (UP=3, DOWN=2, LEFT=1, RIGHT=0),
    Buttons in Bits 20-23. Der Poll testet jetzt beide Layouts. GREEN
    (Bit 3) wurde aus dem Fire-Mask entfernt, weil es auf diesen Pads
    mit UP kollidiert
- Diagnose-Overlay (`LL:`/`P1:`) aus dem Boot-Menü entfernt — diente nur
  zur Joypad-Bit-Identifikation

### v2.2
- Boot-Menü auf Cursor-Navigation umgestellt (`[*]`-Marker, ANSI-Position-
  Sequenzen für In-Place-Redraw)
- `TAB` / `BACKSPACE` als robuste Tastatur-Navigation — funktioniert auch
  in FS-UAE, das mit `joystick_port_1_mode = cd32 gamepad` die PC-
  Pfeiltasten an den Pad-Emulator weiterreicht und damit aus dem
  Amiga-Keyboard-Stream nimmt
- `SPACE` / `ENTER` bestätigen, `1`-`4` weiterhin Direktstart
- Joypad: D-Pad steuert Cursor, alle vier Color-Buttons starten
- Port-0-Polling entfernt (Trackpad/Maus-Klicks in FS-UAE wurden sonst
  als „Confirm" interpretiert und starteten zufällig Spiele)
- Joypad-Idle-Snapshot wird jetzt vor den Bit-Tests fortgeschrieben —
  gehaltener D-Pad-Druck triggert nicht mehr jeden 50ms-Tick neu

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
