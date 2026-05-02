# Enemy -- v2.0

Enemy 1 (Tempest of Violence) + Enemy 2 (Missing in Action)
Anachronia, deutsche v2.0

- **Compilation:** S. Kaufmann (2026)
- **WHDLoad-Slaves:** Wepl ([whdload.de](https://www.whdload.de))
- **System:** CD32 mit 1,5 MB FastRAM

## Features

- **BoxArt-Boot-Logo:** Beim Einlegen der CD erscheint zunaechst ein
  4-Sekunden-Splash mit dem Spiele-Cover, bevor die Auswahl kommt.
- **Boot-Menue mit Joypad und Tastatur:** Direkt nach dem Logo wird
  gewaehlt zwischen *Enemy 1 (Tempest of Violence)* und
  *Enemy 2 (Missing in Action)*. Erste gedrueckte Taste oder
  Joypad-Richtung startet sofort -- keine Bestaetigung mit ENTER noetig.
  - Enemy 1: Pfeil-Links / `1` / Joystick-Links / Roter Feuerknopf
  - Enemy 2: Pfeil-Rechts / `2` / Joystick-Rechts / Blauer CD32-Knopf
- **Alle Level von Anfang an freigeschaltet:** Beide Spiele starten in
  Level 1, aber ueber das Hauptmenue kann jeder Level direkt angewaehlt
  werden -- 34 Level in Enemy 1 (von „Feind" bis „Zorn"), 29 Level in
  Enemy 2. Kein muehsames Passwort-Eintippen, keine versteckten Codes.
- **Eigenes Auswahl-Menue:** Selbst gebautes 68k-Tool, das ohne externe
  Library auskommt und sowohl Tastatur (per RAW-Console) als auch
  Joypad (per `lowlevel.library/ReadJoyPort`) gleichzeitig pollt.
- **Sauberer Start ohne WHDLoad-Splash:** Der ueblicherweise sichtbare
  WHDLoad-Credit-Screen ist unterdrueckt; stattdessen kurz ein
  *„Loading Game, please wait..."* in der Boot-CLI, dann startet
  unmittelbar das gewaehlte Spiel.
- **Quit zurueck zur CD-Auswahl:** F10 im Spiel beendet WHDLoad und
  bringt zurueck zum Boot-Menue, ohne Reboot.

## Credits

Vielen Dank an **Anachronia** fuer beide Enemy-Spiele und an **Wepl**
fuer die WHDLoad-Slaves -- ohne diese Arbeit gaebe es weder die
ungetruebte Spielbarkeit auf modernen Konfigurationen noch diese
CD-Variante.
